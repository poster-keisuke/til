## Get Start
### Go install
goenvを利用して、Goをinstallする方法

#### 1. goenvのインストール
```shell
$ brew install --HEAD gonev
```
※ `--HEAD`をつけないと、Goの最新版がインストールできなかった。

#### 2. pathを通す
bash_profile / zprofileに以下を記載
```
export PATH="${GOPATH}/bin:$PATH"
```
他のページには、設定を色々変えているところがあるが、バージョンごとにディレクトリが変わるのでうまく設定されない。

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
使用するgoのバージョンを設定する
```shell
$ goenv global 1.13.8
```

設定されているか確認
```shell
$ go version 1.13.8
go version go1.13.8 darwin/amd64
```

参考:
- [Golangをgoenvを使ってインストールしてみた
](https://qiita.com/walkers/items/761b2a5e58849176a633)