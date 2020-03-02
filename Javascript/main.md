### npm ci

#### npm install

- package.jsonとpackage-lock.jsonの療法を見て、依存関係の解決と依存パッケージのnode_modulesへのインストール
- package-lock.jsonファイルの更新

#### npm ci

- package-loc.jsonから依存関係をインストールする
- node_modulesフォルダの中身があっても、一旦削除

`package.json` の依存関係の解決を行わない。
`package-lock.json` と依存バージョン指定が食い違っていると、エラーになる。

依存関係の更新をせずに、整合性チェックと依存パッケージのダウンロードのみを行う。
そのため、nmp installより高速に動作する。
