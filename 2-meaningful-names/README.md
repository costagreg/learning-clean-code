# Meaningful Names
Name are everywhere in the code so we better name veriables, class and function well.

## Use Intention-Revealing Names
Names should reval intent(pupose).

The name of a variable, function, or class, should answer all the big questions. It should tell you why it exists, what it does, and how it is used.
If a name require a comment, then the name does not reveal its intent.

```
int d; // elapsed time in days
```

The name `d` revals nothing

We should choose a name that specifies what is being used:

```
int elapsedTimeInDays;
int daysSinceCreation;
int daysSinceModification;
int fileAgeInDays;
```

Example bad code which is hard to understand:

```
public List<int[]> getThem(){
  List<int[]> list1 = new ArrayList<int[]>();
  for (int[] x : theList)
    if (x[0] == 4)
      list1.add(x);
  return list1;
}
```

The code above is not implicity at all. What kinds of things are in `theList`? What is 4? etc.

Better version of the code:

```
public List<int[]> getFlaggedCells(){
  List<int[]> flaggedCells = new ArrayList<int[]>();
  for (int[] cell : gameBoard)
    if(cell[STATUS_VALUE] == FLAGGED)
      flaggedCells.add(cell);
  return flaggedCells;
}
```

## Avoid Disinformation

Programmers must avoid leaving false clues that obscure the meaning of code. We should avoid words whose entrenched meanings vary from our intended meaning.

For example don't refer to a grouping of accounts as an `accountList` unless it's actually a `List`. The `List` means something specific to programmers. If it's not a list use `accountGroup`, `bunchOfAccounts` or just plan `accounts`

Beware of using names which vary in small ways.

## Make Meaningful Distinctions

Programmers create problems for themselves when they write code solely to satisfy a compiler or interpreter.

Because you can't use the same name to refer to two different things in the same scope, it's not sufficient to change the name adding number or noise words. If a name must be different, then they also mean something different.

An example of disinformation:

```
public static void copyChars(char a1[], char a2[]){
  for (int i = 0; i < a1.length; i++) {
    a2[i] = a1[i]
  }
}
```

This function reads much better when `source` and `destination` are used as arguments.

Noise words are another meaningless distinction. If for example you have a `Product` class and you create another called `ProductInfo` or `ProductData`, you have made the name different without making them anything different. Info and Data are indistinct noise words like a, an, and the.

**Noise words are redundat**

If in a codebase you see

```
getActiveAccount()
getActiveAccounts()
getActiveAccountInfo()
```

How are the programmers in this project supposed to know which of these function to call?

**Distinguish names in such a way that the reader knows what the differences offer**

## Use Pronouncable Names
Words are pronuncable. **If you can't pronunce a name you can't discuss it without sounding like an idiot.**

Bad code:
```
class DtaRcrd102 {
  private Date genymdhms;
  private Date modymdhms;
  private final String pszqint = "102";
  /* ... */
}
```

Good code:
```
class Customer{
  private Date generationTimestamp;
  private Date modificationTimestamp;
  private final String recordId = "102";
}
```

## Class Names
Classes and objects should have noun or noun phrase name. A class name should not be a verb.

## Method Names
Methods should have verb or verb phrase names like `postPayment`, `deletePage` or `save`.

## Don't Be Cute
Choose clarity over entertainment value.
Will they know what the function name `HolyHandGranade` is supposed to do?

## Pick One Word per Concept
Pick one word for one abstract concept and stick with it. For instance, it's confusing to have `fetch`, `retrive`, and `get` as equivalent methods of different classes.
Likewise, it's confusing to have a `controller` and a `manager` and a `driver` in the same code base.

## Don't Pun
Avoid using the same word for two purposes. Using the same term for two different ideas is essentially a pun.

If you follow the "the one word per concept" rule, you could end up with many classes that have, for example, an `add` method. As long as the parameter lists and return values of the varius `add` methos are sementically equivalent, all is well.

Let's say we have many classes where `add` will create a new value by adding or cancatenating 2 existng values. Now let's say we are writing a new class that has a method that puts its single parameter into a collection. Should we call this method `add`? It might seem consisten because we have so many other `add` methods, but in this case, the semantics are different, so we should use a name like `inster` or `append` instead.

## Use Solution Domain Names.
Remember that people who read your code will be programmer. So go ahead and use computer science terms, algoritm names etc.
                                                                                         
es should reval intent.## Add Meaningful Context
You need to place names in context for your reader by enclosing them in well-named classes, functions, or namespaces. When all else fails, then prefixing the name may be necessary as last resort.

What if you say the `state` variable being used alone in a method? Would you automatically infer that it was part of an address?

## Don't Add Gratuitous Context
It's a bad idea to prefix every class with the name of the application. It's not wise because we will make our life harder to search classes in our IDE.
Same concept for variables and functions.

**Shorter names are generally better than longer ones, so long as they are clear. Add no more context to a name than is necessary**


