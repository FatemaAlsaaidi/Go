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
