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
### Functions
The basic format for a function is:
```
func function_name(parameter1 type, parameter2 type...) <return_type> {
	// function body
}
```

```
func add(num1 int, num2 int) int {
	return num1 + num2
}
// Also, you can have multiple parameters of the same type like this: func add(num1, num2 int) int {...}

func main() {
	fmt.Println(add(3, 6))
}
```
Functions can return multiple values. You could also name the return values and use them like local variables.
```
func getID() (string, int, string) {
	return "Alex", 99999999, "Valid"
}
...
var name, id, validity = getID()


func doSomething() (retval int, errcode int) {
	retval = 4
	errcode = 0
	return
}
```

### Default Values
```
| Type | Value |
| ---- | ----- |
| number | 0 |
| booleans | true/false |
| string | "" |
| interfaces | nil |

ref types = slice | pointer | map | channel | function
```

### Pointers
```
x := 1
p = &x
*p = 2

p := new(int)   <---- could be allocated on the stack
```
