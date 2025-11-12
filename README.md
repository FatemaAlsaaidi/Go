# Go
## download and install golang in windows 
1.	Download and install go engine  https://go.dev/doc/install
2.	 Pin the extension of go (backage of go ) in visual studio which is as editor
3.	Create go file  .go
4.	To be able to run the golange code, Inside the folder which go files exist :
a.	 should initial go model:
go mod init < name of module>

## run go code
- 	To run the golang code :
a.	Open terminal of folder which the go files exist 
b.	Execute : go run <file name> 
c.	Or click run botton 

## Print text
Import **ftm** backage ==> this backage use to print the text file

```go
package main

import "fmt"

func main() {
	fmt.Println("hello world")
}

```

- When we write a Go program that want to run directly (like an executable), it must be in the main package.
- The Go compiler looks for a package named main and a function named main() inside it — that’s the entry point of program
- "fmt" stands for format — it’s a standard library package in Go that provides functions for formatted I/O (input/output).
- In Go, the function named main() inside the package main is automatically the starting point when you run the program.So when execute:
```terminal
go run main.go
```

## Variables
- The variables are used to store some data at a particular memory address in the system
- declare variables using **var**:
```go
package main

import "fmt"

func main() {

	var name = "fatema"
	fmt.Println(name)
}

```
**Quation** 
- Why in Go we only declare variables with var, not using the data type directly (like in C#)?!
  -- Go is not like C or Java — it was designed to be simpler and more readable by enforcing a consistent, minimal syntax.

		In Go:
		
		The keyword var always introduces a variable.
		
		The type comes after the variable name (not before like C, Java, or C#).
  
-  Simplified declarations with **:=**
```go
name := "Fatema"
age := 25

```

## Constants
- const declares a constant value.
- 
```go
package main

import (
	"fmt"
	"math"
)

const rihal string = "Rihal"
const number int = 5

func main() {
	fmt.Println("hello world")

	var name = "fatema"
	fmt.Println(name)

	fmt.Println(rihal)
	fmt.Println(number)

	const age int = 25
	fmt.Println(age)

	const mark = 99.00
	fmt.Println((mark))

	const n = 500000000
	const d = 3e20 / n
	fmt.Println(d)
	fmt.Println(int64(d))
	fmt.Println(math.Sin(n))

}


```
In Go, when write a constant like:
```go
const x = 5
```

it’s called an untyped constant — it doesn’t yet have a fixed type like int, float64, etc.
Go decides its type later, based on how you use it.

This gives Go flexibility — the same constant can be used as an int, float64, or even complex128 if needed.

**Example**
```go
const a = 5   // untyped constant

var x int = a       // a becomes int
var y float64 = a   // a becomes float64
```

Works fine because a can adapt its type automatically.

But if you force a type too early

If you define the constant with an explicit type, like:

```go
const n int = 500000000
```


now n is strictly an integer — it can’t automatically change type anymore.

So if you later use n in an expression that expects a float, you’ll get an error.

**Example**
```go
import "math"

const n int = 500000000

func main() {
    fmt.Println(math.Sin(n)) //  ERROR
}

```
**Error message**
```go
cannot use n (constant 500000000 of type int) as float64 value in argument to math.Sin
```

**Why?**
- Because the function math.Sin() needs a float64, but n is an int.
- Go doesn’t automatically convert between numeric types.
**Note**
- const means immutabl; const l = 3 defines a constant, and constants in Go cannot be changed after declaration.

## Pointer
- pointer value is the address of a variable.  A pointer is thus the location at which a value is stored.
**why we need pointer?!**
  - with a pointer, we can read or update the value of a variable indirectly, without using or even knowing the name of the variable, if indeed it has a name.
**Memory Representation variables vs pointers**
Variable: The memory allocated for a variable directly holds its value.
Pointer: The memory allocated for a pointer holds an address, which in turn points to another memory location where the actual value is stored.

**How Pointers Work in Memory**
1. You create the variable which store the value.
```go
var x = 42
```
2. The system allocates a block of memory to store its value (value of variable)

```go
the system will allocate memory to store 42 and x will refer to that location.
```
note: The variable name refers to this memory location

3. A pointer variable p stores the memory address of variable x, not the value 42 itself.

**Pointer aliasing**
- Pointer aliasing is useful because it allows us to access a variable without using its name

**Pointer in function**
- Using pointers in Golang functions can serve various purposes, including modifying the original value passed to the function, preventing unnecessary copying of large data structures, and optimizing performance.

```go
package main

import (
	"fmt"
)

type Rectangle struct {
	Width, Height float64
}

func resizeRectangle(r *Rectangle, width, height float64) {
	r.Height = height
	r.Width = width
}

func main() {

	rec := Rectangle{Width: 5, Height: 6}

	fmt.Println("Before resize: ", rec)

	resizeRectangle(&rec, 10, 12)

	fmt.Println("After resize: ", rec)

}


```

1. Struct Definition (Rectangle):
- Rectangle has Width and Height fields.
2. Function Definition (resizeRectangle):
- resizeRectangle takes a pointer to a Rectangle (*Rectangle) and modifies its fields.
3. Passing the Pointer (&rect):
- In main, &rect passes the address of rect to resizeRectangle.
- The function updates rect directly.

## For
```go
package main

import (
	"fmt"
)

func main() {

	//print even number
	for i := 0; i <= 3; i++ {
		if i%2 == 0 {
			fmt.Println(i)
		}

	}
	// print odd number
	for i := 0; i <= 3; i++ {
		if i%2 == 0 {
			continue
		}
		fmt.Println(i)

	}
}

```
## If/Else
``` go
package main

import (
	"fmt"
)

func main() {
	var num int
	fmt.Print("Enter your grade:")
	fmt.Scan(&num)

	if num >= 90 && num <= 100 {
		fmt.Print("A")
	} else if num >= 80 && num <= 89 {
		fmt.Print("B")
	} else if num >= 60 && num <= 79 {
		fmt.Print("C")
	} else if num >= 50 && num <= 59 {
		fmt.Print("D")
	} else if num >= 0 && num < 50 {
		fmt.Print("F")
	} else {
		fmt.Print("Invalid number of grade")
	}
}

```
## Switch
```go
package main

import (
	"fmt"
)

func main() {
	var choice string
	fmt.Println("Enter the number of process")
	fmt.Scan(&choice)

	switch choice {
	case "1":
		fmt.Println("Welcome with first process")
		break
	case "2":
		fmt.Println("Welcome with second process")
		break
	default:
		fmt.Println("Invalid number")
		break
	}

}


```
## Arrays

```go
package main

import "fmt"

func main() {
	// find pair with given sum in array sum = 10

	var sum = 10
	var hold1 = 0
	var hold2 = 0

	b := [6]int{8, 7, 2, 5, 3, 1}
	var A [2]int

	for i := 0; i <= len(b); i++ {
		hold1 = b[i]
		for j := 0; j <= len(b); j++ {
			hold2 = b[j]
			if hold2 == hold1 {
				continue
			} else {
				if hold1+hold2 == sum {
					A[0] = hold1
					A[1] = hold2
					fmt.Println(A[0])
					fmt.Println(A[1])
					fmt.Print("Enter to press")
					return
				} else {
					continue
				}
			}
		}

	}

}

```
