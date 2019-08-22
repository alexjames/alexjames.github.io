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
```
You can have multiple parameters of the same datatype.
```
func add(num1, num2 int) int {...}
```

```
func main() {
	fmt.Println(add(3, 6))
}
```

Functions can return multiple values.
```
func getID() (string, int, string) {
	return "Alex", 99999999, "Valid"
}
...
var name, id, validity = getID()
```

You could also name the return values and use them like local variables.
```
func doSomething() (retval int, errcode int) {
	retval = 4
	errcode = 0
	return
}
```