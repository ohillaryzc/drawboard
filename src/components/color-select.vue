<template>
  <div class="color-select-box" :style="{ marginTop: `-${32 * items.length}px` }">
    <div
      v-for="(item, index) in items"
      :key="index"
      :style="{ backgroundColor: item.value }"
      class="color-select-item"
      @click="itemClick(item)"
    >
    </div>
  </div>
</template>

<script setup>
  import { ref } from 'vue';
  const items = ref([]);
  items.value = [
    {
      color: 'red',
      value: 'red',
    },
    {
      color: 'green',
      value: 'green',
    },
    {
      color: 'blue',
      value: 'blue',
    },
  ];

  const value = ref('');
  const itemClick = (item) => {
    value.value = item.value;
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
    box-shadow: 0 0 16px 4px rgba(0, 0, 0, .3);
    box-sizing: border-box;
    cursor: pointer;
  }
</style>
