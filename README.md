# a-tour-of-go

Information of this README.MD file, getting from documentation of go.dev.
All of the apps and descriptions in Playground are included in this document. It allows you to access all of this from a
single file, and then practice with that content.

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
