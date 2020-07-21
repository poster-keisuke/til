## margin-top / margin-bottom 問題

margin を使って、要素感の余白のとり方。
基本的には、margin-top を利用する。

隣接セレクタを利用することで、margin-bottom を利用せずに
対応することが可能

```html
<html>
  <body>
    <div class="parent1">
      <div class="child">
        子どもA
      </div>
      <div class="child">
        子どもB
      </div>
    </div>
    <div class="parent2">
      <div class="child">
        子どもC
      </div>
      <div class="child">
        子どもD
      </div>
      <div class="child">
        子どもE
      </div>
    </div>
  </body>
</html>
```

```css
.parent1 {
  background-color: red;
  padding: 20px 20px;
  margin: 20px 0;
}

.parent2 {
  background-color: blue;
  padding: 20px 20px;
}

.child + .child {
  margin-top: 30px;
}

.child {
  color: white;
}
```

https://jsfiddle.net/horaj1wL/20/

また、左右の余白は margin-left
border は top or left で指定する。

極論右,下でも構わないが、意図として伝わりやすい + どちらかに統一するのが良い。

参考: [フロントエンドのプロ直伝！ CSS 余白設定の三原則（＋線の引き方）](https://qiita.com/yama-t/items/da7740769cfc0f8446a0#1-%E5%9F%BA%E6%9C%AC%E7%9A%84%E3%81%ABmargin-top%E3%82%92%E4%BD%BF%E3%81%86)
