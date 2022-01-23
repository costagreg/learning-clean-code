# Functions

**Functions are the first line of organization in any program**

How can we make a function communicate its intent? It has to be **Small**!!

## Blocks and Indenting

This implies that the blocks within *if* statements, *else* statementsm *while* statements, and so on should be one line long. Probably that line should be a function call. Not only does this keep the enclosing function small, but it also adds documentary value because the function called within the block can have a nicely description name.

## Do One Thing

**FUNCTIONS SHOULD DO ONE THING. THEY SHOULD DO IT WELL, THEY SHOULD DO IT ONLY.**

So another way to know that a function is doing more than one thing is if you can exstract another function another function from it with a name that is not merely a restatement of its implementation.

## One Level Of Abstraction per Function

In order to make sure our functions are doing "one thing", we need to make sure that the statements within our function are all at the same level of abstraction.

e.g. high level: `.getHtml()`, Intermediate: `String pagePathName = PathParser.render(pagePath)`, low level: `.append("\n")`

**Mixing levels of abstraction within a functionis always confusing. Readers may not be able to tell whether a particular expression is an essential concept or a detail**

## Reading Code from Top to Bottom: The Stepdown Rule

The rule tells us that the code in our class should be readable from top to bottom, descending one level of abstraction per function. It implies that the function ordering is no longer random. A caller function should always reside above the callee function.

## Use Descriptive Names

> You know you are working on clean code when each routine turns out to be pretty much what you expected

Half of the battle to achieving that principle is choosing good names for small functions that do one thing.

**Don't be afraid to make a name long. A long descriptive name is better than a short enigmatic name. A long descriptive name is better than a long descriptive comment.**

## Function Arguments

The ideal number of arguments for a function is zero (niladic). Next come one (monadic), followed closely by two (dyadic). Three arguments (triadic) should be avoided where possible. More than three (polyadic) requires very special justification - and then shouldn't be used anyway.

Output arguments are harder to understand than input arguments. When we read a function, we are used to the idea of information going **in** to the function through arguments and **out** through the return value. We don't usually expect information to be going out though the arguments. So output arguments often cause us to do a dauble-take.

One input argument is the next best thing to no arguments.

## Common Monadic Forms

There are two very coomon reasons to pass a single argument into a function. You may be asking a question about that argument, as in `boolean fileExists("MyFile")`. Or you may be operating on that argument, transforming it into something else and returning it. 

## Flag Arguments

Flag arguments are ugly, Passing a boolean into a function is a truly terrible pracice. It immediately complicates the signature of the method, loudly proclaiming that this funciton does more than one thing. It does one thing if the flag is true and another if the flag is false.
For example if you a methoda call `render(boolean isSuite)` you may want to create two separate function `renderForSuite()` and `renderForSingleTest()`.

## Dyadic (two arguments function)

A function with two arguments is harder to understand thant a monadic function. For example, `writeField(name)` is easier to understand than `writeField(output-Stream, name)`
There are times, of course, where two arguments are appropriate.For example, `Point p = new Point(0,0);` is perfectly reasonable. Cartesian points naturally take two arguments. The two arguments in this case are ordered components of a single value! Whereas `output-Stream` and `name` have neither a natural cohesion, nor a natural ordering.

Even obvious dyadic functions like `assertEquals(expected, actual)` are problematic. How many times have you the actual where the expected shuld be? The two arguments have no natural ordering.
Dyads aren't evil, and you will certainy have to write them. However, you should be aware that they cme at a cost and should take advantage of what mechanisms may be available to you to convert them into monads. For example, you might make the `writeFild` method a member of `outputStream` so that you can say `outputStream.writeField(name)`. Or you might make the `outputStream` a member variable of the current class so that you don't have to pass it. Or you might exstract a new class like `FieldWriter` that takes the `outputStream` in its constructos and has a `write` method.

## Arguments Objects

When a function seems to need more thant two or three arguments, it is likely that some of those arguments ought to be wrapped into a class of their own. 
E.g

`Circle makeCircle(double x, double y, double radius)`
`Circle makeCircle(Point center, double radius)`

## Verbs and Keywords

In the cosa of a monad(one argument), the function and argument should form a very nice verb/noun pair.

For example, `write(name)` is very evocative. Whatever this "name" thing is, it is being "written". An even better name might be `writeField(name)`, which tells us that the "name" thing is a "field".
This last is an example of the ***keyword*** form of a function name. Using this form we encode the names of the arguments into the function name. For example, ***assertEquals*** might be better written as ***assertExpectEqualsActual(expected, actual)***. This strongly mitigates the problem of having to remember the ordering of the arguments.

## Have No Side Effects
Side effects are lies. Your function promises to done thing, but it also does other ***hidden*** things. That's wrong.

```
public class UserValidator {
 private Cryptographer cryptographer;

 public boolean checkPassword(String userName, String password) {
  User user = UserGateway.findByName(userName);
  if (user != User.NULL) {
    String codedPhrase = user.getPhraseEncodedByPassword();
    String phrase = cryptographer.decrypt(codePhrase, password);
    if ("Valid Password".equals(phrase)){
      Session.initialise();
      return true;
    }
  }
  return false;
 }
}
```

The side effect is the call to ``Session.initialise()``. The ``checkPassword`` function, by its name, says that it checks the password. The name does not imply that it initializes the session.

Better separate this logic in 2 functions. Remember the rule ***Do One thing***,or if you must have a temporal coupling change name of the function like ***checkPasswordAndInitializeSession***.

### Output Arguments

What do you think about this function?

```
appendFooter(s);
```

Does this function append `s` as the footer to something? Or does it append some footer to `s`? Is `s` an input or an output?

```
public void appendFooter(StringBuffer report)
```

If you read the signature can clarify the issue, but anything that forces you to check the function signature is equivalan to a double-take. It's a cognitive break and it should be avoided.

In general output arguments should be avoided. If your function must change the state of something, have it change the state of its owning object.

### Command Query Separation

**Functions should either do something or answer something, but not both.**
Either your function should change the state of an object, or it should retunr some information about that object. Doing both often leads to confusion.

```
public boolean set(String attribute, String value);
```

This function sets the value of a named attribute and returns true if it's successful and false is not such attribute exists.

```
if (set("username", "unclebob"))...
```

What does it mean? Is it asking whether the "username" attribute was previusly set to "unclebob"? Or is it asking whether the "username" attribute was previusly set to "unclebob"? Is ``set`` a verb or an adjective?

Better solution to separate the command from the query

```
if (attributeExists("username")) {
  setAttribute("username", "unclebob");
}
```

### Prefer Exceptions to Returning Error Codes

Returning error code is a subtle violation of ***command query separation***. It promotes commands being used as expressions in the predicates of ***if*** statment.

```
if(deletePage(page) == E_OK) {
  ...
}
```

When you return an error code, you create the problem that the caller must deal with the error immediately

```
if (deletePage(page) == E_OK){
  if(registr.deleteReference(page.name) == E_OK){

  } else {
    // handle error in here
  }
} else {
  // handle error
}
```

if you use exceptions instead of returned error codes, the the error processing code can be separated from the happy path code and can be simplfied.

```
try{
  // Happy path
  deletePage(page);
  registry.deleteReference(page.name);
  ...
}
catch (Exepction e){
  // Unhappy path
}
```

### Extract Try/Catch Blocks

Try/Cat confuse the structure of the code and mix error processing with normal processing. So it is better to extract the bodies of the try and catch blocks out into functions of their own.

```
public void delete(Page page){
  try {
    deletePageAndAllReferences(page);
  }
  catch (Exception e) {
    logError(e)
  }
}
```

THis nice separation make the code easier to understand and modify.

### Error Handling Is One Thing

***Function should do one thing. Error handling is one thing***

Thus a function that handles errors should do nothing else. No code before Try and after catch/finally blocks.

### Don't Repeat Yourself

The duplication is a problem because it bloats the code and will require four-fold modification should the algorithm ever have to change. it also a four-fold opportunity for an error of omission.

**Duplication may be the roor of all evil in software**

### How DO You Write Functions Like This?

**Writing software is like any other kind of writing**: when you write a paper or an article, you get your thoughts down first, then you massage it until it read well.
Make sure to always cover each line with unit tests before refactoring.

Writing code following all there rules since the start it's impossible. But you need to iterate till they are all applied.
