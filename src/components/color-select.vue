<template>
  <div class="color-select-box" :style="{ marginTop: `-${32 * items.length}px` }">
    <div
      v-for="(item, index) in items"
      :key="index"
      :style="{ backgroundColor: item }"
      class="color-select-item"
      @click="itemClick(item)"
    >
    </div>
  </div>
</template>

<script setup>
import { ref, defineEmit } from 'vue';
const emits = defineEmit(['change']);
const items = ref([]);
items.value = ['#409EFF', '#67C23A', '#E6A23C', '#F56C6C', '#909399'];

const value = ref('');
const itemClick = (item) => {
  value.value = item;
  emits('change', item);
};
</script>

<style scoped>
  .color-select-box {
    position: fixed;
    top: 50%;
    left: 20px;
  }
  .color-select-item {
    margin: 8px 0;
    width: 30px;
    height: 30px;
    border: 4px solid #fff;
    background-color: red;
    border-radius: 50%;
    box-shadow: 0 0 16px 4px rgba(0, 0, 0, .1);
    box-sizing: border-box;
    cursor: pointer;
  }
</style>
