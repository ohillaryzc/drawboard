<template>
  <!-- 颜色选择 -->
  <color-select
    :index="0"
    text="message"
    :arr="[0, 1, 2]"
    @change="colorChange"
  >
  </color-select>
  <!-- 工具选择 -->
  <tool-select
    :color="color"
  />
  <!-- 画板 -->
</template>

<script setup>
import { ref } from 'vue';
import ColorSelect from './components/color-select.vue';
import ToolSelect from './components/tool-select.vue';

const color = ref('');
const colorChange = (value) => {
  color.value = value;
};
</script>

<style>
  * {
    margin: 0;
    padding: 0;
  }
  html, body {
    height: 100%;
  }
</style>
