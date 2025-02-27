# a-tour-of-go

Information of this README.MD file, getting from documentation of go.dev.
All of the apps and descriptions in Playground are included in this document. It allows you to access all of this from a single file, and then practice with that content.

This documentation has 2 chapters. You can follow chapters and then can you try yourself on hands-on exercises.

1. All of the information in https://go.dev/tour/list
2. All hands-on exercises at https://gobyexample.com/

![gopher catch the bus](./asset/icon/gopher-catch-the-bus.png 'gopher catch the bus')

#### Welcome

###### Hello, 世界

Welcome to a tour of the [Go Programming language](https://go.dev/).
The tour id divided into a list of modules that you can access by clicking on [A Tour of Go](https://go.dev/tour/welcome/1) on the top left of the page.
You can also view the table of contents at any time by clicking on the [menu](https://go.dev/tour/welcome/1) ıb the top right of the page.
Throughout the tour you will find a series of slides and exercises for you to complete.
You can navigate through them using

- "previous" or `PageUp` to go to the previous page,
- "next" or `PageDown` to go to the next page.

The tour is interactive. Click the [Run](https://go.dev/tour/welcome/1) button now (or press `Shift` + `Enter`) to compile and run the program on a remote server. The result is displayed below the code.
These example programs demonstrate different aspects of Go. The programs in the tour are meant to be starting points for your own experimentation.
Edit the program and run it again.
When you click on [Format](https://go.dev/tour/welcome/1) (shortcut:`Ctrl` + `Enter`), the text in the editor is formatted using the (gofmt)[https://pkg.go.dev/cmd/gofmt] tool. You can switch syntax highlighting on and off by clicking on the syntax button.
When you're ready to move on, click the [right arrow](https://go.dev/tour/welcome/1) below or type the `PageDown` key.

```go
package main

import "fmt"

func main() {
  fmt.Println("Hello, 世界")
}
```

`reference:` [Go Documentation](https://go.dev/tour/welcome/1)
`exercise:`

###### Go Local

The tour is available in other languages:

- [Brazilian Portuguese — Português do Brasil](https://go-tour-br.appspot.com/tour/welcome/1)
- [Catalan — Català](https://go-tour-ca.appspot.com/welcome/1)
- [Simplified Chinese — 中文（简体](https://tour.go-zh.org/welcome/1)
- [Czech — Česky](https://go-tour-cz.appspot.com/welcome/1)
- [Indonesian — Bahasa Indonesia](https://go-tour-id2.appspot.com/welcome/1)
- [Japanese — 日本語](https://go-tour-jp.appspot.com/welcome/1)
- [Korean — 한국어](https://go-tour-ko.appspot.com)
- [Polish — Polski](https://go-tour-pl1.appspot.com/welcome/1)
- [Thai — ภาษาไทย](https://go-tour-th.appspot.com/tour/welcome/1)
- [Ukrainian — Українською](https://go-tour-ua-translation.lm.r.appspot.com/welcome/1)

Click the [next](https://go.dev/tour/welcome/2) button or `PageDown` to continue.

###### Go Offline (optional)

This tour is also available as a standart-alone program that you can use without access to the internet. It builds and runs the code samples on your own machine.

To run the tour locally, you'll need the first [install go](https://go.dev/doc/install) and then run:

```shell
go install golang.org/x/website/tour@latest
```

This will place a `tour` binary in your [GOPATH](https://pkg.go.dev/cmd/go#hdr-GOPATH_and_Modules)'s `bin/` directory. When you run the tour program, it will open a web browser displaying your local version of the tour.

Of course, you can continue to take the tour through this web site.

###### The Go Playground

This tour is built atop the [Go Playground](https://go.dev/play/), a web service that runs on [golang.org](https://go.dev/)'s servers.

The service receives a Go program, compiles, links and runs the program inside a sandbox, then return the output.

There are limitations to the programs that can be run in the playground:

> In the playground the time begins at 2009-11-10 23:00:00 UTC (determining the significance of this date is an exercise for the reader). This makes it easier to cache programs by giving them deterministic output.
> There are also limits on execution time and on CPU and memory usage, and the program cannot access external network hosts.

The playground uses the latest stable release of Go.

Read "[Inside the Go Playground](https://go.dev/blog/playground)" to learn more.

#### Basics

##### Packages, Variables, and Functions

The starting point, learn all basics of the language.

Declaring variables, calling functions, and all the things you need to know before moving to the next lessons.

###### Packages

Every Go program is made up of packages.

Programs start running in package `main`.

This program is using the packages with import paths `fmt` and `math/rand`.

By convention, the package name is the same as the last element of the import path. For instance, the `math/rand` package
comprises files that begin with the statement `package rand`.

```go
package main

import (
	"fmt"
	"math/rand"
)

func main() {
	fmt.Println("My favorite number is", rand.Intn(100))
}
```

![Go packages](./Basics/assets/packages.png 'Go packages')

###### Imports

This code groups the imports into a parenthesized, "factored" import statement.

You can also write multiple imports statements, like:

```go
import "fmt"
import "math"
```

But it is good style to use the factored import statement.

```go
package main

import (
	"fmt"
	"math"
)

func main() {
	fmt.Printf("Now you have %g problems.\n", math.Sqrt(7))
}
```

![Go imports](./Basics/assets/imports.png 'Go imports')

###### Exported Names

In go, a name is exported if it begins with a capital letter. For example `Pizza` is an exported name, as is `Pi`, which
is exported from the `math` package.

`pizza` and `pi` do not start with a capital letter, so they are not exported.

When importing a package, you can refer only to its exported names. Any "unexported" names are not accessible from outside
the package.

Run the code. Notice the error message.

To fix the error, rename `math.pi` to `math.Pi` and try it again.

```go
package main

import (
	"fmt"
	"math"
)

func main() {
	// fmt.Println(math.pi)
	fmt.Println(math.Pi)
}
```

![Go exported names](./Basics/assets/exported-names.png 'Go exported names')

###### Functions

A function can take zero or more arguments.

In this example, `add` takes two parameters of type `int`.

Notice that the type comes after the variable name.

(For more about why types look the way they do, see the [article on Go's declaration syntax](https://go.dev/blog/declaration-syntax)).

```go
package main

import "fmt"

func add(x int, y int) int {
	return x + y
}

func main() {
	fmt.Println(add(42, 13))
}
```

![Go functions](./Basics/assets/exported-names.png 'Go functions')

###### Functions Continued

When two or more consecutive named function parameters share a type, you can omit the type from all but the last.

In this example, we shortened

```go
x int, y int
```

to

```go
x, y int
```

```go
package main

import "fmt"

func add(x, y int) int {
	return x + y
}

func main() {
	fmt.Println(add(42, 13))
}
```

![Go functions continued](./Basics/assets/functions-continued.png 'Go functions continued')

###### Multiple Results

A function can return any number of results.

The `swap` returns two strings.

```go
package main

import "fmt"

func swap(x, y string) (string, string) {
	return y, x
}

func main() {
	a, b := swap("hello", "world")
	fmt.Println(a, b)
}
```

![Go multiple results](./Basics/assets/multiple-results.png 'Go multiple results')

###### Named Return Values

Go's return values may be named. If so, they are treated as variables defined at the top of the function. These names
should be used to documents the meaning of the return values.

A `return` statement without arguments returns the named return values. This is known as a "naked" return.

Naked return statements should be used only in short functions, as with the example shown here. They can harm readability
in longer functions.

```go
package main

import "fmt"

func split(sum int) (y, x int) {
	x = sum * 4 / 9
	y = sum - x
	return
}

func main() {
	fmt.Println(split(17))
}
```

![Go named return values](./Basics/assets/named-return-values.png 'Go named return values')

###### Variables

The `var` statement declares a list of variables; as in function argument lists, the type is last.

A `var` statement can be a package or function level. We see both in this example.

```go
package main

import "fmt"

var c, python, java bool

func main() {
	var i int

	fmt.Println(i, c, python, java)
}
```

![Go variables](./Basics/assets/named-return-values.png 'Go variables')

###### Variables With Initializers

A var declaration can include initializers, one per variable.

If an initializer is present, the tpye can be omitted; the variable will take the type of the initializer.

```go
package main

import "fmt"

var i, j int = 1, 2

func main() {
	var c, python, java = true, false, "no!"

	fmt.Println(i, j, c, python, java)
}
```

![Go variables with initializer](./Basics/assets/variables-with-initializer.png 'Go variables with initializer')

###### Short Variable Declarations

Inside a function, the `:=` short assignment statement can be used in place of a `var` declaration with implicit type.

Outside a function, every statement begins with a keyword(`var`, `func`, and so on) and so the `:=` construct is not
available.

```go
package main

import "fmt"

func main() {
	var i, j int = 1, 2
	k := 3
	c, python, java := true, false, "no!"

	fmt.Println(i, j, k, c, python, java)
}
```

![Go short variable declarations](./Basics/assets/short-variable-declarations.png 'Go short variable declarations')

###### Basic Types

Go's basic type are

- bool
- string
- int int8 int16 int32 int64
- uint uint8 uint16 uint32 uint64 uintptr
- byte // alias for uint8
- rune // alias for int32 // represent a Unicode code point
- float32 float64
- complex64 complex128

The example shows variables of several types, and also that variable declarations my be _factored_ into blocks, as with
import statements.

The `int`, `uint`, and `uintptr` types are usually 32 bits wide on 32-bit systems and 64 bits wide on 64-bit system.
When you need an integer value you should use `int` unless you have specific reason to use a sized or usigned integer
type.

```go
package main

import (
	"fmt"
	"math/cmplx"
)

var (
	ToBe   bool       = false
	MaxInt uint64     = 1<<64 - 1
	x      complex128 = cmplx.Sqrt(-5 + 12i)
)

func main() {
	fmt.Printf("Type: %T Value: %v\n", ToBe, ToBe)
	fmt.Printf("Type: %T Value: %v\n", MaxInt, MaxInt)
	fmt.Printf("Type: %T Value: %v\n", x, x)
}
```

![Go basic types](./Basics/assets/basic-types.png 'Go basic types')

###### Zero Values

Variables declared without an explicit initial value are given their zero value.

The zero value is:

- `0` for numeric types
- `false` for the boolean type, and
- `''` (the empty string) for string

```go
package main

import "fmt"

func main() {
	var i int
	var f float64
	var b bool
	var s string

	fmt.Printf("%v %v %v %q\n", i, f, b, s)
}
```

![Go zero values](./Basics/assets/zero-values.png 'Go zero values')

###### Type Conversions

The expression `T(v)` converts the `v` to the type `T` .

Some numeric conversions:

```
var i int = 42
var f float64 = float64(i)
var u uint = uint(f)
```

Or, put more simply:

```
i := 42
f := float64(i)
u := uint(f)
```

Unlike in C, in Go assignment between items of different type requires an explicit conversion. Try removing the
`float64` or `uint` conversions in the example and see what happens.

```go
package main

import (
	"fmt"
	"math"
)

func main() {
	var x, y int = 3, 4
	var f = math.Sqrt(float64(x*x + y*y))
	var z = uint(f)

	fmt.Println(x, y, z)
}
```

![Go type conversions](./Basics/assets/type-conversions.png 'Go type conversions')

###### Type Inference

When declaring a variable without specifying an explicit type (either by using the `:=` syntax or `var =` expression
syntax), the variable's type is inferred from the value on the right hand side.

When the right hand side of the declaration is typed, the new variable is of that same type:

```
var i int
j := i // j is an int
```

But when the right hand side contains an untyped numeric constant, the new variable may be an `int`, `float64`, or
`complex128` depending on the precision of the constant:

```
i := 42 // int
f := 3.142 // float64
g := 0.867 + 0.5i // complex128
```

Try changing the initial value of `v` in the example code and observe how its type is affected.

```go
package main

import "fmt"

func main() {
	v := 12.9949492i // change me!

	fmt.Printf("v is of type %T\n", v)
}
```

![Go type inference](./Basics/assets/type-inference.png 'Go type inference')

###### Constants

Constants are declared like variables, but with the `const` keyword.

Constants can be character, string, boolean, or numeric values.

Constants cannot be declared using `:=` syntax.

```go
package main

import "fmt"

const Pi = 3.14

func main() {
	const World = "世界"

	fmt.Println("Hello", World)
	fmt.Println("Happy", Pi, "Day")

	const Truth = true
	// Truth = false

	fmt.Println("Go rules?", Truth)

	const BigNum = 2i

	fmt.Println("number:", BigNum)
}
```

![Go constants](./Basics/assets/constants.png 'Go constants')

###### Numeric Constants

Numeric constants are high-precision values.

An untyped constant takes the type needed by its context.

Try printing `needInt(Big)` too.

(An `int` can store at maximum a 64-bit integer, and sometimes less.)

```go
package main

import "fmt"

const (
	// Create a huge number by shifting a 1 bit left 100 places.
	// In other words, the binary number that is 1 followed by 100 zeroes.
	Big = 1 << 100
	// Shift it right again 99 places, so we end up with 1<<1, or 2.
	Small = Big >> 99
)

func needIn(x int) int { return x*10 + 1 }
func needFloat(x float64) float64 {
	return x * 0.1
}

func main() {
	fmt.Println(needIn((Small)))
	fmt.Println(needFloat(Small))
	fmt.Println(needFloat(Big))
}
```

![Go numeric constants](./Basics/assets/numeric-constants.png 'Go numeric constants')

###### Congratulations!

You finished this lesson!

You can go back to the list of [modules](https://go.dev/tour/list) to find what to learn next, or continue with the [next lesson](https://go.dev/tour/flowcontrol/1).

##### Packages, Variables, and Functions

###### For

Go has only one looping construct, the `for` loop.

The basic `for` loop has three components separated by semicolons:

- the init statement: executed before the first iteration
- the condition expression: evaluated before every iteration
- the post statement: executed at the end of every iteration

The init statement will often be a short variable declaration, and the variables declared there are visible only in the
scope of the `for` statement.

The loop will stop iterating once the boolean condition evaluates to `false`.

_note: Unlike other languages like C, Java, or JavaScript there are no parentheses surrounding the three components of the `for` statement and the braces `{}` are always required._

```go
package main

import "fmt"

func main() {
	sum := 0
	for i := 0; i < 10; i++ {
		sum += i
	}
	fmt.Println(sum)
}
```

![Go for loop](./Basics/assets/for.png 'Go for loop')

###### For Continued

The init and post statements are optional.

```go
package main

import "fmt"

func main() {
	sum := 1
	for sum < 1000 {
		sum += sum
	}
	fmt.Println(sum)
}
```

![Go for continued](./Basics/assets/for-continued.png 'Go for continued')

###### For is Go's "while"

At that point you can drop the semicolons: C's `while` is spelled `for` in Go.

```go
package main

import "fmt"

func main() {
	sum := 1
	for sum < 1000 {
		sum += sum
	}
	fmt.Println(sum)
}
```

![Go for is Go while](./Basics/assets/for-is-go-while.png 'Go for is Go while')

###### Forever

If you omit the loop condition it loops forever, so an infinite loop is compactly expressed.

```go
package main

func main() {
	for {
	}
}
```

![Go forever](./Basics/assets/forever.png 'Go forever')

###### If

Go's `if` statements are like it's `for` loops; the expression need not be surrounded by parentheses `()` but the braces
`{}` are required.

```go
package main

import (
	"fmt"
	"math"
)

func sqrt(x float64) string {
	if x < 0 {
		return sqrt(-x) + "i"
	}
	return fmt.Sprint(math.Sqrt(x))
}

func main() {
	fmt.Println(sqrt(2), sqrt(-4))
}
```

![Go if statement](./Basics/assets/if.png 'Go if statement')

###### If With a Short Statement

Like `for`, the `if` statement can start with a short statement to execute before the condition.

Variables declared by the statement are only in scope until the end of the `if`.

_(Try using `v` in the last `return` statement.)_

```go
package main

import (
	"fmt"
	"math"
)

func pow(x, n, lim float64) float64 {
	if v := math.Pow(x, n); v < lim {
		return v
	}
	return lim
}

func main() {
	fmt.Println(
		pow(3, 2, 10),
		pow(3, 3, 20),
	)
}
```

![Go if with short statement](./Basics/assets/if-with-short-statement.png 'Go if with short statement')

```go
package main

import (
	"fmt"
	"math"
)

func pow(x, n, lim float64) float64 {
	if v := math.Pow(x, n); v < lim {
		return v
	}
	return v // Try using `v` in the last `return` statement.
}

func main() {
	fmt.Println(
		pow(3, 2, 10),
		pow(3, 3, 20),
	)
}
```

![Go if with short statement](./Basics/assets/if-with-short-statement-2.png 'Go if with short statement')

###### If and Else

Variables declared inside an `if` short statement are also available inside any of the `else` blocks.

_(Both calls to `pow` return their results before the call to `fmt.Println` in `main` begins.)_

```go
package main

import (
	"fmt"
	"math"
)

func pow(x, n, lim float64) float64 {
	if v := math.Pow(x, n); v < lim {
		return v
	} else {
		fmt.Printf("%g >= %g\n", v, lim)
	}
	// can't use v here, through
	return lim
}

func main() {
	fmt.Println(
		pow(3, 2, 10),
		pow(3, 3, 20),
	)
}
```

![Go if and else](./Basics/assets/if-and-else.png 'Go if and else')

###### Exercise: Loops and Functions

As a way to play with functions and loops, let's implement a square root function: given a number x, we want to find the
number z for which z² is most nearly x.

Computers typically compute the square root of x using a loop. Starting with some guess z, we can adjust z based on how
close z² is to x, producing a better guess:

```go
z -= (z * z - x) / (2 * x)
```

Repeating this adjustment makes the guess better and better until we reach an answer that is as close to the actual
square root as can be.

Implement this in the `func Sqrt` provided. A decent starting guess for z is 1, no matter what the input. To begin with,
repeat at calculation 10 times and print each z along the way. See how close you get to the answer for various values
of x (1, 2, 3, ...) and how quickly the guess improves.

`Hint: To declare and initialize a floating point value, give it floating point syntax or use a conversion:`

```go
z := 1.0
z := float64(1)
```

Next, change the loop condition to stop once the value has stopped changing (or only changes by a very small amount).
See if that's more or fewer than 10 iterations. Try other initial guesses for z, like x, or x/2. How close are your
function's results to the [math. Sqrt](https://pkg.go.dev/math#Sqrt) in the standard library?

_**Note:** If you are interested in the details of the algorithm, the z² − x above is how far away z² is from where it
needs to be (x), and the division by 2z is the derivative of z² is changing. This general approach is called
[Newton's method.](https://en.wikipedia.org/wiki/Newton%27s_method) It works well for many functions but especially
well for square root._

```go
package main

import (
	"fmt"
	"math"
)

func Sqrt(x float64) float64 {
	z := 1.0
	sqrtNumb := math.Sqrt(x)

	for i := 0; i < 10; i++ {
		l := float64(i)
		z -= (z*z - l) / (2 * z)
		diff := float64(0)

		if z > sqrtNumb {
			diff = z - sqrtNumb
		} else {
			diff = sqrtNumb - z
		}

		fmt.Printf("z is: %g\n", z)
		fmt.Printf("diff:  %g\n", diff)
	}

	return z
}

func main() {
	fmt.Println(Sqrt(2))
}
```

![Go loops and functions](./Basics/assets/loops-and-func.png 'Go loops and functions')

###### Switch

A `switch` statement is a shorter way to write a sequence of `if - else` statements. It runs the first case whose value
is equal to the condition expression.

Go's switch is like the one in C, C++, Java, JavaScript, and PHP, except Go only runs the selected case, not all the
cases that follow. In effect, the `break` statement that is needed at the end of each case in those languages is
provided automatically in Go. Another important difference is that Go's switch cases need not be constants, and the
values involved need not be integers.

```go
package main

import (
	"fmt"
	"runtime"
)

func main() {
	fmt.Print("Go runs on ")

	switch os := runtime.GOOS; os {
	case "darwin":
		fmt.Println("OS X.")
	case "linux":
		fmt.Println("Linux.")
	default:
		fmt.Printf("%s.", os)
	}
}
```

![Go switch](./Basics/assets/switch.png 'Go switch')

###### Switch Evaluation Order

Switch cases evaluate cases from top to bottom, stopping when a case succeeds.

For example,

```go
switch i {
	case 0:
	case f():
}
```

does not call `f` if `i == 0`.)

_**Note:** Time in the Go playground always appears to start at 2009-11-10 23:00:00 UTC, a value whose significance is
left as an exercise for the reader._

```go
package main

import (
	"fmt"
	"time"
)

func main() {
	fmt.Println("When's Saturday?")

	today := time.Now().Weekday()

	switch time.Saturday {
	case today + 0:
		fmt.Println("Today.")
	case today + 1:
		fmt.Println("Tomorrow.")
	case today + 2:
		fmt.Println("In two days.")
	default:
		fmt.Println("Too far away.")
	}
}
```

![Go evaluation order](./Basics/assets/switch-evaluation-order.png 'Go switch evaluation order')

###### Switch With No Condition

Switch without a condition is the same as `switch true`.

This constructs can be a clean way to write long if-then-else chains.

```go
package main

import (
	"fmt"
	"time"
)

func main() {
	t := time.Now()

	switch {
	case t.Hour() < 12:
		fmt.Println("Good morning!")
	case t.Hour() < 17:
		fmt.Println("Good afternoon!")
	default:
		fmt.Println("Good evening!")
	}
}
```

![Go switch with no condition](./Basics/assets/switch-with-no-condition.png 'Go switch with no condition')

###### Defer

A defer statement defers the execution of a function until the surrounding function returns.

The deferred call's arguments are evaluated immediately, but the function call is not executed until the surrounding
function returns.

```go
package main

import "fmt"

func main() {
	defer fmt.Println("world")

	fmt.Println("hello")
}
```

![Go defer](./Basics/assets/defer.png 'Go defer')

###### Stacking Defers

Deferred function calls are pushed onto a stack. When a function returns, its deferred calls are executed in
last-in-first-out order.

To learn more about defer statements read this [blog post](https://go.dev/blog/defer-panic-and-recover)

```go
package main

import "fmt"

func main() {
	fmt.Println("counting...")

	for i := 0; i < 10; i++ {
		defer fmt.Println(i)
	}

	fmt.Println("done")
}
```

![Go stacking defers](./Basics/assets/stacking-defers.png 'Go stacking defers')

###### Congratulations!

You finished this lesson!

You can go back to the list of [modules](https://go.dev/tour/list) to find what to learn next, or continue with the [next lesson](https://go.dev/tour/moretypes/1).
