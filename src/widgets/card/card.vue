<script lang="ts" setup>
import { ref } from 'vue';
import { useVirtualList } from '@vueuse/core'

import { NumCard } from '@/widgets';

interface IProps {
  numCount: number;
}
const props = defineProps<IProps>();

const randomNumsArray = ref(Array.from({ length: props.numCount }, () => Math.floor(Math.random() * 11) + 10));

const { list, containerProps, wrapperProps } = useVirtualList(
  randomNumsArray,
  {
    itemWidth: 50,
  },
)

setInterval(() => {
  randomNumsArray.value = Array.from({ length: props.numCount }, () => Math.floor(Math.random() * 11) + 10);
}, 1000);

</script>

<template>
  <div 
    class="card"
    v-bind="containerProps"
  >
    <div v-bind="wrapperProps">
      <NumCard
        v-for="item in list" 
        :key="item.index" 
        :num="item.data"
      />
    </div>
  </div>
</template>

<style scoped lang="postcss">
  @import './card.pcss';
</style>