# Objects and Data Structures

There is a reason that we keep our variables private. We don't want anyone else to depend on them. We want to keep the freedom to change their type or implementation on a whim or an impulse.
Why, then, do so many programmers automatically add gettesr and setters to their objects. expsoing their private variables as if they were public?

## Data Abstractions

Hiding implementation is not just a matter of putting a layer of functions  between the variables. Hiding implementation is about abstractions! A class does not simply push its variables out through getter and setters. Rather it exposes abstract interfaces that allow its users to manipulate the assense of the data, without having to know its implemntations.

### Concrete Vehicle
```
public interface Vehicle {
  double getFuelTankCapacityInGallons();
  double getGallonsOfGasoline();
}
```

### Abstract Vehicle
```
public interface Vehicle {
  double getPercentFuelRemaining();
}
```

In both of the above cases the second option is preferable. We do not want to expose the details of our data. Rather we want to express our data in abstract terms.  This is not merely accomplished by using interfaces and/or getters and setters. Serius thought needs to be put into the best way to represent the data that an object contains. 


## Difference between Data structures and objects
Objects hide their data behind abstractions and expose functions that operate on that data.
Data structure expose their data have no meaningul functions.


