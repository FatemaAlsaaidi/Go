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
