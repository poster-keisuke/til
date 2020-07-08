# Packages, variables, and functions

## exported names

https://go-tour-jp.appspot.com/basics/3

最初の文字が大文字の場合は、外部パッケージから参照できる公開された名前
小文字の場合は、外部パッケージから参照できない(export されていない)名前になる。

```go
package main
​
import (
    "fmt"
    "math"
)

func main() {
    fmt.Println(math.Pi)
}

// 3.141592653589793
```

この場合、`math.pi` では関数を実行できない。

## multiple results

https://go-tour-jp.appspot.com/basics/6

function の返り値を複数設定できる。
この場合、x,y は string でないとコンパイルできない。

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

## Variables

https://go-tour-jp.appspot.com/basics/8
https://go-tour-jp.appspot.com/basics/9

js と違い、var は変数の定義に利用する。
定義の際に、型も定義する必要がある。

下記の場合、
`var c, python, java`のように、型を定義しないとコンパイルできない。

また、定義の際に初期値を与えることも可能

```go
package main

import "fmt"

var c, python, java bool
var o, k int = 1, 2

func main() {
    var i int
    fmt.Println(i, o, k, c, python, java)
}

// 0 1 2 false false false
```

### Short variable declarations

https://go-tour-jp.appspot.com/basics/10

関数の内部では、 `:=`を用いることで、暗黙的な型宣言ができる。（動的型付け的）
ただし、関数の外部では利用できない。

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

### Constants

https://go-tour-jp.appspot.com/basics/15

定数の定義も可能。
ただし、文字(character)、文字列（string）、bool、数値（numeric）のみが利用できる。
また、`:=` での定義はできない。

```go
package main

import "fmt"

const Pi = 3.14

func main() {
    const World = "世界"
    fmt.Println("Hello", World)
    fmt.Println("Happy", Pi, "Day")

    const Truth = true
    fmt.Println("Go rules?", Truth)
}

// Hello 世界
// Happy 3.14 Day
// Go rules? true
```

## Zero Value

https://go-tour-jp.appspot.com/basics/12

変数に初期値を与えずに定義すると、zero value が与えられる。

型によって、値が変わる。

- 数値(int/float): `0`
- bool: `false`
- string: `""（空文字）`

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

// 0 0 false ""
```
