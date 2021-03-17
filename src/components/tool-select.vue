<template>
  <div class="tool-select-box">
    <div
      v-for="(item, index) in tools"
      :key="index"
      :class="['tool-select-item', index === active ? 'active' : '']"
      @click="changeTool(index)"
    >
      <img :src="item.icon" alt="" width="30">
    </div>
  </div>
</template>

<script setup>
  import { ref } from 'vue';
  import pencil from '/src/assets/icon-pencil.png?url';
  import eraser from '/src/assets/icon-eraser.png?url';
  import save from '/src/assets/icon-save.png?url';
  const tools = ref([]);
  tools.value = [
    {
      icon: pencil,
      title: '画笔',
    },
    {
      icon: eraser,
      title: '橡皮擦',
    },
    {
      icon: save,
      title: '保存',
    },
  ];
  const active = ref(0);
  const changeTool = (index) => {
    active.value = index;
  };
</script>

<style scoped>
  .tool-select-box {
    position: fixed;
    top: 20px;
    left: 50%;
    margin-left: -108px;
    display: flex;
    justify-content: center;
  }
  .tool-select-item {
    margin: 0 16px;
    width: 50px;
    height: 50px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    box-shadow: 0 0 24px 4px rgba(0, 0, 0, .2);
    box-sizing: border-box;
    cursor: pointer;
  }
  .tool-select-item.active {
    border: 1px solid #007fff;
  }
</style>
