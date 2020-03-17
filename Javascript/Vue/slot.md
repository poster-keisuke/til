## Slot の使い方

Slot を使うと、コンポーネントに対して動的な値を渡すことが可能。

```js
//Form.vue
<template>
  <BaseButton>Submit</BaseButton>
</template>

// BaseButton.vue
<template>
  <div>
    <button><slot></slot></button>
  </div>
</template>

// 以下のようなHTMLがレンダリングされる。
<template>
  <div>
    <button>Submit</button>
  </div>
</template>
```

### 親の props や、computed も渡すことが可能。

```js
//Form.vue
<template>
  <BaseButton>Purchase for ${{ total }}</BaseButton>
</template>

// BaseButton.vue
<template>
  <div>
    <button><slot></slot></button>
    // Purchase for $12.99
  </div>
</template>
```

### 複数の slot を渡すとき

以下のように、slot 側には`name`を呼び出し側には、`slot`を定義し、マッピングする。

```js
// MediaBox.vue
<slot name="heading"></slot>
<slot name="paragraph"></slot>

// Parent.vue
<template>
  <MediaBox>
    <h2 slot="heading">Poster-keisuke</h2>
    <p slot="paragraph">I'm here</p>
  </MediaBox>
</template>
```

一つだけ定義されていれば、もう片方が定義されていなくても呼び出しが可能。

```js
// MediaBox.vue
<slot name="heading"></slot>
<slot></slot>

// Parent.vue
<template>
  <MediaBox>
    <h2 slot="heading">Poster-keisuke</h2>
    <p>I'm here</p>
  </MediaBox>
</template>
```
