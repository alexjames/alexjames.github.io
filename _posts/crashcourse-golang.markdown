---
layout: default
title:  "Crash Course: golang"
date:   2017-01-14 12:50:00
categories: cs
---
Golang is a compiled langauge. The runtime is embedded into the finally produced binary file.

### Hello World Example
```
package main

import (
	"fmt"
)

func main() {
	fmt.Println("Hello World!")
}
```
### Main Data Types
```
string
bool
int
int int8 int16 int32 int64
uint uint8 uint16 uint32 uint64
byte (uint8)
rune (int32)
float32 float64
complex32 complex64
```
### Variable Declaration Examples
```
var name string = "Alex"
var age int = 30
var length1, length2 int = 12, 4 // declaring multiple vars
var phrase = "Blah"
isCorrect := false // Shorthand, datatype inferred
fmt.Println(name, age)
```
