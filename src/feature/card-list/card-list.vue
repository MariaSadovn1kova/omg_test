<script lang="ts" setup>
import { ref } from 'vue';
import { useVirtualList } from '@vueuse/core';

import { Card } from '@/widgets';

const randomCardArray = Array.from({ length: Math.floor(Math.random() * 15) + 120 }, () => Math.floor(Math.random() * 11) + 10);
const { list, containerProps, wrapperProps } = useVirtualList(
  randomCardArray,
  {
    itemHeight: 200,
  },
)
</script>

<template>
  <div 
    class="card-list"
    v-bind="containerProps"
  >
    <div v-bind="wrapperProps">
      <Card 
        v-for="item in list" 
        :key="item.index"
        :numCount="item.data"
        class="card-list__item"
      />
    </div>
  </div>
</template>

<style scoped lang="postcss">
  @import './card-list.pcss';
</style>