#

## Switch

https://go-tour-jp.appspot.com/flowcontrol/9

PHP などの他の言語のように、明示的に`brake`を記述する必要はない。

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
        // freebsd, openbsd,
        // plan9, windows...
        fmt.Printf("%s.", os)
    }
}

// Go runs on Linux.
```

## Defer

https://go-tour-jp.appspot.com/flowcontrol/12

defer へ渡した関数は、呼び出し元の関数の終わり（return)まで呼び出されない。
つまり、遅延呼び出しが可能。(ちなみに、評価はされる。)

```go
package main

import "fmt"

func main() {
    defer fmt.Println("world")

    fmt.Println("hello")
}

// hello world
```

### Stack Defer

https://go-tour-jp.appspot.com/flowcontrol/13

複数の Defer が stack された場合、最後に stack に入ったものから取り出される
(いわゆる Last-in-First-out)

```go
package main

import "fmt"

func main() {
    fmt.Println("counting")

    for i := 0; i < 10; i++ {
        defer fmt.Println(i)
  }

  fmt.Println("done")
}
```
