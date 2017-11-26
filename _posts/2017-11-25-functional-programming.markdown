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

Pure functions are basically re-entrant in nature, making them safe to use for concurrent programming.

### Functional composition
f1(f2())

One of the main objectives of OOP is to stop unwanted modification of private data. With immutable data structures, this is not a concern anymore. More over, methods are tightly coupled with objects in OOP, reducing their re-usability. This is another advantage of functional programming.

### Map/Reduce "sandwhich"
The "map" operation is like iterating through a list and applying a function to it. Reduce cummulatively acts on a collection
to get a final result. This image provides a good analogy for both of them. Many flavours of FP don't provide explicit loop-like control
flow statements. Instead, you rely on recursion and map-reduces to achieve the same result. This take a "while" to get used to. Pun intended.

![alt text](http://api.ning.com/files/-3i3rVffQH2bautHoYhtuyn-BhEFBMR3TNXJzACS9ATLysgH7VID6G3-DRqv65rcjsIwZ7riHJZ9rtS9XGWzIc326dpaeNvF/bor55.PNG)

[Source: http://www.datasciencecentral.com/forum/topics/what-is-map-reduce]

### Stateless
Why stateless is good? Because if you have no state,
 * servers are easier to replace with low system downtime.
 * you'll have lesser chances of race-conditions.
