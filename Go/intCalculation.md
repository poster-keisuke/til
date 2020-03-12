## Go で int 同士で割り算すると、int で返ってくる

```go

package main

import (
    "fmt"
)

fmt.Printf("%t\n", 10 / 3) // 3

```

`10/3 = 3.333333` のハズだが、int 同士だと 3 が返り値になる。
そのため、小数点も含めた返り値にしたい場合は、`float64`に変換が必要

```go

package main

import (
    "fmt"
)

fmt.Printf("%t\n", 10 / 3.0) // 3.333333....
fmt.Printf("%t\n", float64(10) / 3) // 3.333333....
fmt.Printf("%t\n", 10 / float64(3)) // 3.333333....
```

参考:

- [Go: int 同士の割り算は、int が戻り値なので注意](https://qiita.com/suin/items/d45cf4cea90cc51d01bd)
