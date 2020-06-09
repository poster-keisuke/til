## VSCode での環境設定

- vscode 用の[プラグイン](https://github.com/Microsoft/vscode-go)をインストール
- settings.json を編集

以下参考

```
"go.useLanguageServer": true,
"go.languageServerExperimentalFeatures": {
    "format": false,
    "autoComplete": true,
    "rename": true,
    "goToDefinition": true,
    "hover": true,
    "signatureHelp": true,
    "goToTypeDefinition": true,
    "goToImplementation": true,
    "documentSymbols": true,
    "workspaceSymbols": true,
    "findReferences": true
}
```

- vscode のコマンドパレットから`go: Install/Update Tools`を実行し、`go-langserver`をインストール
