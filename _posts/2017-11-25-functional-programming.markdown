---
layout: default
title:  "Functional Programming"
date:   2017-11-25 12:50:00
categories: cs
---

# Functional programming concepts

A short summary of functional programming concepts and how they contrast with other programming paradigms.

### Pure functions
Pure functions are functions that have no side-effects. They will always return the same result if they are provided the same 
arguments. They have no 'state'. They can't cause any changes that are observable outside of it. For example, they can't 
mutate an external object or write to a file.

Pure functions are basically re-entrant by nature, making them safe to use for concurrent programming.

### Functional composition
```
f1(f2())
```

One of the main objectives of OOP is to stop unwanted modification of private data. With immutable data structures, this is not a concern anymore. Moreover, methods are tightly coupled with objects in OOP, reducing their re-usability. This is another advantage of functional programming.

### Map/Reduce "sandwhich"
The `map` operation is like iterating through a list and applying a function to it. `reduce` cumulatively acts on a collection
to get a final result. This image provides a good analogy for both. Here, your mapping function slices the ingredients and the
reduce function combines all of them into a tasty sandwhich.
Many flavors of FP don't provide explicit loop-like control flow statements. Instead, you rely on recursion and map-reduces to 
achieve the same result. This takes a "while" to get used to. Pun intended.

![alt text](http://api.ning.com/files/-3i3rVffQH2bautHoYhtuyn-BhEFBMR3TNXJzACS9ATLysgH7VID6G3-DRqv65rcjsIwZ7riHJZ9rtS9XGWzIc326dpaeNvF/bor55.PNG)

[Source: http://www.datasciencecentral.com/forum/topics/what-is-map-reduce]

### Stateless
Why stateless is good? Because if you have no state,
 * it's easier to debug code, you don't have to keep track of hundreds of variables in your head.
 * you'll have no race-conditions. This is awesome for concurrency.
 * servers are easier to replace with low system downtime.

