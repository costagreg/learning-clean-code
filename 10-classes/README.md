# Classes

## Classes Should Be Small!

Classes should be small. How small? We need to count the number of `responsabilities`.

If we cannot derive a concise name for a class, then it's likely too large. The more ambiguos the class nam, the more likely it has too many responsabilities.

We should also be able to write a brief description of the class in about 25 words, without using the words 'if', 'and', 'or' or 'but'.

## The Single Responsability Principle

```
The Single Responsability Principle (SRP) states that a class or module should have one, and only one, reason to change.
```

A system with many small classes has no more moving parts than a system with few large classes. There is just as much to learn in the system with a few large classes. So the question is: Do you want your tool organized into toolboxes with many small drawers each containing well-defined and well-labeled components? Or do you want few drawers that you just toss everything into?

## Cohesion

Classes should have a smallnumber of instance variables. Each of the methods of a class should maniulate one or more of those variables. In general the more variables a method manipulates the more ***cohesive*** that method is to its class. **A class in which each variable is used by each method maximally cohesive**

When cohesion is high, it means that the methods and variables of the class are co-dependent and hang together as logical whole.

if a set of instance varialbes are used just by few methos in the class, it almost always means that there is at least one other class trying to get out of the larger class. If you saparate them the two class will be more cohesive.

## Mantaining Cohesion Results in Many Small Classes

If there are a few functions that want to share cartain variables, doesn't that make them a class in their own right? Of course it does. ***when classes lose cohesion, split them***

Breaking a large function into many smallare functions often gives us the opportunity to split several smaller classes out as well. This gives our program a much beter organization and a more transparent structure.


