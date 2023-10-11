# Magic Grid for Vue3
[magic-grid](https://github.com/e-oj/Magic-Grid) wrapper for Vue 3
extended from 

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

# Warn
## Dynamic list
magic-grid doesnt support dynamic list.
so this library refresh all DOM whenever changed count.
therefore not recommend built-in animate option. Use DIY animation or transition instead.