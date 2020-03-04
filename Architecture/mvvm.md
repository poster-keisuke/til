## MVVMパターンとは
Model/View/ViewModleからなるデザインパターンの一つ

Vue.jsで採用されている

- Model ビジネスロジック
- View 表示部分
- ViewModel modelをviewに変換する役割

`Modle -> ViewModle <-> View` の形で、ViewはViewModleの値をバインディングして表示する。

### 参照は一方向
- ModleはViewModleを知らない
- ViewModleはViewを知らない

### 関連用語と使い分け
- Decorator
  - 単一モデルクラスに対応
- Presenter
  - 複数モデルクラスにまたがる
  - 永続化されたモデルと一致しない
- ViewModel
  - Decorator/Presenterの上位概念
  - ビューに関連するロジックをまとめるレイヤーのこと

### 参考
- [Decorator と Presenter を使い分けて、 Rails を ViewModel ですっきりさせよう
](https://tech.kitchhike.com/entry/2018/02/28/221159)