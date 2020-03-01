## スプレッド演算子

ドット(...)を利用して、変数の中身を展開できる。

```js
const obj1 = { a: 1, b: 2 };
const obj2 = { ...obj1, c: 3 };
console.log(obj2); // {a:1, b:2, c:3}
```

```js
let obj1 = { a: 1, b: 2 };
let obj2 = Object.assign({}, obj1, { c: 3 });
console.log(obj2); // {a:1, b:2, c:3}
```
