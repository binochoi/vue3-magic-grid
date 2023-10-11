# Magic Grid for Vue3
extended from [magic-grid](https://github.com/e-oj/Magic-Grid)

```bash
npm i --save vue3-magic-grid
```

```html
<script setup>
import { MagicGrid } from 'vue3-magic-grid'
</script>
<template>
  <MagicGrid
    :options="{
      animate: true,
      gutter: 30,
      static: true,
      useMin: true,
    }"
    :count="count">
    <Row
      v-for="row in list"
      v-bind="row"
    />
  </MagicGrid>
</template>
```