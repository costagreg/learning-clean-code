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


