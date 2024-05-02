<script lang="ts" setup>
interface IProps {
  num: number;
}
const props = defineProps<IProps>();
</script>

<template>
  <div class="num-card">
    <span class="num-card__content">{{ num }}</span>
  </div>
</template>

<style scoped lang="postcss">
  @import './num-card.pcss';
</style>