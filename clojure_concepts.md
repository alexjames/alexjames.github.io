# Functional programming concepts

### Pure functions
Pure functions are functions that have no side-effects. They will always return the same result if they are provided the same 
arguments. They have no 'state'. They can't cause any changes that are observable outside of it. For example, they can't 
mutate an external object or write to a file.

Pure functions are basically re-entrant in nature, making them safe to use for concurrent programming.

### Functional composition
f1(f2())

One of the main objectives of OOP is to stop unwanted modification of private data. With immutable data structures, this is not a concern anymore. More over, methods are tightly coupled with objects in OOP, reducing their re-usability. This is another advantage of functional programming.

### Map/Reduce sandwhich
Maps are like iterating through a list and applying a function to it. Reduce cummulatively acts on a collection
to get a final result.

![alt text](http://api.ning.com/files/-3i3rVffQH2bautHoYhtuyn-BhEFBMR3TNXJzACS9ATLysgH7VID6G3-DRqv65rcjsIwZ7riHJZ9rtS9XGWzIc326dpaeNvF/bor55.PNG)

[Source: http://www.datasciencecentral.com/forum/topics/what-is-map-reduce]
