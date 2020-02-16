## Form

### Input がキーボードに隠れてしまう問題

`KeyboardAvoidingView` を使うと、フォーム入力時にポジションを変えることができる。

```javascript
import { KeyboardAvoidingView } from "react-native";

<KeyboardAvoidingView style={styles.container} behavior="padding" enabled>
  ... your UI ...
</KeyboardAvoidingView>;
```

`behavior`option を変えることで、アニメーションを変えることが可能。
複数のフォームを使う場合は、position を使うと要素が画面外に飛び出さずに済む。

参考:

- [KeyboardAvoidingView](https://facebook.github.io/react-native/docs/keyboardavoidingview#behavior)
- [【React Native】TextInput がキーボードに隠れてしまう問題の解決法について](https://qiita.com/YutamaKotaro/items/d66377eb0ce8d8da55f5)
