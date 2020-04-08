## docker-compose 実行後アプリケーションがすぐに exited with code 0 を返す

### 原因

コンテナ起動時にコマンドを実行してプロセスが終了してしまっていた。

### 対応

`tty: true`を付与する。

```yml
services:
  app:
    build: .
    container_name: 'python3'
    tty: true
```

こうすることで、コンテナがすぐに終了してしまうのを防ぐことができる。

https://kossy-web-engineer.hatenablog.com/entry/2020/01/05/112620
