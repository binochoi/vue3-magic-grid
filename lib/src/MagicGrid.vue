<script lang="ts" setup>
import MagicGrid from 'magic-grid';
import type { MagicGridProps } from './types';
import { onMounted, ref, nextTick, watch } from 'vue';
const container = ref<HTMLDivElement>();
let containerHeight = ref<number>(0);
let magicGrid: MagicGrid;
const props = defineProps<{
  options?: MagicGridProps,
  count?: number;
}>();
const initMagicGrid = () => {
  magicGrid = new MagicGrid({
    ...props.options,
    container: container.value!,
  });
  let interval: NodeJS.Timeout;
  const init = () => {
    if(magicGrid.ready() === false) {
      return;
    }
    const containerScrollHeight = container.value!.scrollHeight;
    containerHeight.value = containerScrollHeight;
    magicGrid.listen();
    clearInterval(interval);
  }
  interval = setInterval(init, 200);
}
onMounted(initMagicGrid);
watch(() => props.count, () => {
  nextTick(initMagicGrid);
})
</script>
<template>
<div :key="props.count">
  <div ref="container" :style="{ height: `${containerHeight}px` }">
    <slot></slot>
  </div>
</div>
</template>