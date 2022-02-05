# Comments

> Don't comment bad code - rewrite it

The proper use of comments is to compensae for our failure to express ourself in code. Note that I used to word failure. Comments are always failures. We must have them because we cannot always figure out how to express ourself without them but their use is not a cause for celebration.

Why am I so down to on comments? Because they lie. The older a comment is, and the farther away it is from the code it describes, the more likely it is to be just plain wrong. The reason is simple. Programmers can't realistically mainten them.

Innacurate comments are far worse that no comments at all. They delude and mislead. They set expecations that will never be fulfilled.

Truth can only be found in one place: the code. Only the code can truly tell you what it does. It is the only source of truly accurate information.

## Comments Do Not Make Up for Bad code

One of the more common motivations for writing comments is bad code. We write a module and we know it is confusing and disorganized. We know it's a mess. So say to ourselves, "Ooh, I d better comment that!" NO! You d better clean it!"

## Good Comments

### Warning of COnsequences

Sometimes it is useful to wanr other programmers about certain consequences.

### ToDO Comments

It is sometimes reasonable to leave "To do" notes in the form of //TODO comments.

### Amplification 

A comment may be used to amplify the importance of something that may otherwise seem incsequential.

## Bad Comments

Most comments fall into this category.

### Mumbling

Plopping in a comment just because you feel you should or because the process requires it, is a hack.
Any comment that forces you to look in another module for the meaning of that comment has failed to communicate to you an dis not worth the bits it consumes.

### Redundat Comments

Comments that describe line by line each line don't serve any porpouse. 

### Misleading Comments

Comments that describe somethins that's not clear enough or it's not true or not precise.

### Don't use a Comment When You Can Use a Function or a Variable

```
// does the module from the global list <mod> depend on the subsytem we are part of?
if (smodule.getDependSubsystems().contains(subSysMod.getSubSystem()))
```

Can be refactored to

```
ArrayList moduleDepndees = smodule.getDependSubsystems();
String ourSubSystem = subSysMod.getSubSystem();
if (moduleDependees.contains(ourSubSystem))
```

### Commented-Out Code

Others who see that commented-out code won't have the courage to delete it. They will think it is there for a reason and is too important to delete.
We have good source code control systems now, commenting code shouldn't be necessary.

### Nonlocal Information

If you must write a comment, then make sure it describes the code it appears near. Don't offer systemwide information in the context of a local comment.


