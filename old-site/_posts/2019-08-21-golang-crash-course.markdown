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
var length1, length2 int = 12, 4 // declaring multiple vars at once
var phrase = "Blah"
isCorrect := false // Shorthand declaration, datatype inferred
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
### Arrays/Slices
Declaring an array of strings of size 5.
```
var listArr [4]string // declare an array
listArr[0] = "Alex"   // indexing starts from 0
listArr[3] = "Jacob"  // last element index in an array of size 4
```
```
colors := []string{"red", "blue"}    // declare and initialize array
fmt.Println(colors)                  // print entire array
```

Slices are subsets of arrays that can be sepecified with the format:
```
Array[start index (included):last index (excluded)]
```

```
// array of colors of size 4
colors := []string{"red", "blue", "green", "yellow"}
fmt.Println(colors)           // [red blue green yellow]
fmt.Println(colors[2:])       // [green yellow]
fmt.Println(colors[:1])       // [red]
fmt.Println(colors[2:4])      // [green yellow]
```

## Conditionals
If statement
```
country := "india"

// if-statement
if country == "england" {
	fmt.Println("Zip")
} else if country == "canada" {
	fmt.Println("Zap")
} else {
	fmt.Println("Zup")
}
```
Switch statement
```
country := "india"

// switch on variable name, no need of break statements like C
switch country {
case "england":
	fmt.Println("Zip")
case "canada":
	fmt.Println("Zap")
default:
	fmt.Println("Zup")
}
```
### Loops
There is only a for-loop in golang.

Basic `for` loop.
```
for i := 0; i < 10; i++ {
	fmt.Println(i)
}
```

`while` loop using a `for`.
```
i := 0
for i < 10 {
	fmt.Println(i)
	i++
}
```

`do`-`while` loop.
```
i := 0
for {
	fmt.Println(i)
	i++
	if i == 10 {
		break
	}
}
```
