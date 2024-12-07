## データクラスの設計

以下のようなデータクラスを実装してしまうと、このMoneyクラスを利用して処理を行う実装がバラバラに作られてしまうため（低凝集）、
処理が重複してしまう、修正漏れが発生する、初期化の際に不正値が混入するなどの技術的負債を生みやすくなってしまう。

* 重複コード: 必要なロジックがMoneyクラスに集まっておらず、処理が重複、分散してしまう。
* 修正漏れ: 重複コードが有ることにより、修正時に漏れが起こりやすい。
* 可読性: Moneyクラスを扱う処理が分散していることで、全体像が把握しづらくなる。

```java
class Money {
  int amount;
  Currency currency;
}
```

これを防ぐために、データクラスに加えてロジックを含めるようにする。

### 初期化時に不正値の混入を防ぐ

Moneyクラスを初期化するためのコンストラクタをMoneyクラスに持たせます。
また、このとき初期化時のバリデーションを行うことができる。

```java
class Money {
  int amount;
  Currency currency;

  Money(int amount, Currency currency) {
    if (amount < 0) {
      throw new IllegalArgumentException("金額は0以上を入力して下さい。");
    }
    if (currency == null) {
      throw new IllegalArgumentException("通貨単位を必ず指定してください。");
    }
    this.amount = amount;
    this.currency = currency;
  }
}
```

### 処理が重複してしまう、修正漏れが発生する

Moneyクラスを利用する際に、よく利用されるようなメソッドを実装することによって、
重複した実装を避け、修正漏れを抑えることができる。

```java
class Money {
  int amount;
  Currency currency;

  void add(int other) {
    amount += other;
  }
}
```

### 再代入を防ぐ

以下のように、final修飾子を利用することで、利用側で予期せぬ再代入を防ぐことができる。
これにより、このMoneyクラスのプロパティを外部から変更できないようする。

```java
class Money {
  final int amount;
  final Currency currency;

  // ...
}
```

イミュータブルにすることによって、値を変更できなくなってしまうが、
その場合はメソッド内で新しいMoneyクラスを返すようにすればよい。

その際に、引数も同様にイミュータブルにすることにすることによって、より強固にすることができる。

```java
class Money {
  final int amount;
  final Currency currency;

  Money add(final int other) {
    return New Money(amount + other, currency);
  }
}
```

### 引数のプリミティブ型を避ける

引数がプリミティブ型であれば、Moneyクラスのaddメソッドを通貨以外でも渡せてしまう。

```java
int moneyCount = 3;
money.add(moneyCount);
```

そのため、引数をMoney型にすることによってこうした引数へ渡す型も制限することで事故が起こりにくくすることができる。

```java
class Money {
  final int amount;
  final Currency currency;

  void add(Money other) {
    if (!currency.equals(other.currency)) {
      throw new IllegalArgumentException("通貨単位が異なります。");
    }

    return new Money(amount+other.amount, currency);
  }
}
```

### 最終成果

* 重複コード: 必要なロジックがMoneyクラスに集まっておらず、処理が重複、分散してしまう。
* 修正漏れ: 重複コードが有ることにより、修正時に漏れが起こりやすい。
* 可読性: Moneyクラスを扱う処理が分散していることで、全体像が把握しづらくなる。

上記課題を解消し、更に強固な実装を行うことができた。
それにより以下のような効果も生まれる。

* 初期化時のバリデーション: 初期化される値に不正値が含まれることがなくなる。
* 副作用: 初期化や、利用する関数で意図しない副作用を生むコードを防ぐことができる。
* 値の渡し間違い: 誤って意図しないプリミティブな引数を渡してしまい、意図しない挙動を生むことが少なくなる。

これにより、高凝集でありカプセル化された実装にすることができる。

```java
class Money {
  final int amount;
  final Currency currency;

  Money(final int amount, final Currency currency) {
    if (amount < 0) {
      throw new IllegalArgumentException("金額は0以上を入力して下さい。");
    }
    if (currency == null) {
      throw new IllegalArgumentException("通貨単位を必ず指定してください。");
    }
    this.amount = amount;
    this.currency = currency;
  }

  void add(Money other) {
    if (!currency.equals(other.currency)) {
      throw new IllegalArgumentException("通貨単位が異なります。");
    }

    return new Money(amount+other.amount, currency);
  }
}
```
