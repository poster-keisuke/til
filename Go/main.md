## Get Start

### Go install

goenv を利用して、Go を install する方法

#### 1. goenv のインストール

```shell
$ brew install --HEAD gonev
```

※ `--HEAD`をつけないと、Go の最新版がインストールできなかった。

#### 2. path を通す

bash_profile / zshrc or zshenv に以下を記載

```
export GOENV_ROOT="$HOME/.goenv"
export PATH="$GOENV_ROOT/bin:$PATH"
eval "$(goenv init -)"
export PATH="$GOROOT/bin:$PATH"
export PATH="$PATH:$GOPATH/bin"
```

#### 3. 指定バージョンのインストール

インストールできるバージョンの確認

```
$ goenv install -l
Available versions:
  1.2.2
  :
  1.7.4
```

指定したバージョンをインストール

```shell
$ goenv install 1.13.8
```

#### 4. 設定

使用する go のバージョンを設定する

```shell
$ goenv global/local 1.13.8
```

設定されているか確認

```shell
$ go version 1.13.8
go version go1.13.8 darwin/amd64
```

参考:

- [Golang を goenv を使ってインストールしてみた
  ](https://qiita.com/walkers/items/761b2a5e58849176a633)
- [goenv/Installation](https://github.com/syndbg/goenv/blob/master/INSTALL.md)

### Hello World

```go
// hello.go
package main

import "fmt"

func main() {
  fmt.Printf("Hello World\n")
}
```

```shell
$ go build hello.go
$ ./hello // Hello World
```

参考:

- [Getting Started
  ](https://golang.org/doc/install)

### Q&A

#### Q: vscode 上で、GOPATH 及び GOROOT が読み込めない

エラー文

```
Failed to run "go env" to find GOPATH as the "go" binary cannot be found in either GOROOT(undefined) or ...
```

#### A: ターミナルから GOPATH を引き継いだ状態で開き直す。

```shell
$ code .
```

GOPATH や GOROOT の環境情報を取得できる。

また、再起動することで tools の再コンパイルが走る。（走らない場合もある。）

参考:
[VSCode で go tools のコマンドがみつからない。
](https://qiita.com/tomlaw/items/df47acd61b70db3762e6)
