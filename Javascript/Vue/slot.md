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
