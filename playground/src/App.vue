<script setup lang="ts">
import { MagicGrid } from 'vue3-magic-grid'
import { ref } from 'vue';

const count = ref(2);
setInterval(() => {
  count.value += 1;
}, 1000);
</script>

<template>
<div :style="{
  width: '1200px'
}">
  <MagicGrid :options="{
    gutter: 30,
    static: true,
    useMin: true,
  }"
  :count="count * 5">
    <div class="item" v-for="_, idx in count * 5" :key="idx">1</div>
  </MagicGrid>
</div>
</template>

<style scoped>
.item {
  width: 280px;
  height: 500px;
  background-color: antiquewhite;
  color: black;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 8px;
}
.item:nth-child(even) {
  height: 400px;
}
.item:nth-child(odd) {
  height: 700px;
}
</style>
