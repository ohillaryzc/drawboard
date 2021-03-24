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
    @width-change="widthChange"
    @change="toolChange"
  />
  <!-- 画板 -->
  <main-board
    :color="color"
    :line-width="lineWidth"
    :action="action"
  />
</template>

<script setup>
import { ref } from 'vue';
import ColorSelect from './components/color-select.vue';
import ToolSelect from './components/tool-select.vue';
import MainBoard from './components/main-board.vue';

const color = ref('');
const colorChange = (value) => {
  color.value = value;
};

const action = ref('pencil');
const toolChange = (value) => {
  action.value = value;
};

const lineWidth = ref(1);
const widthChange = (value) => {
  lineWidth.value = value;
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
  ::-webkit-scrollbar {
    width: 0; /* 滚动条的宽度 */
    height: 0; /* 滚动条的高度 */
  }
</style>
