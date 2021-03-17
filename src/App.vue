<template>
  <!-- 颜色选择 -->
  <color-select />
  <!-- 工具选择 -->
  <tool-select />
  <!-- 画板 -->
</template>

<script setup>
import ColorSelect from './components/color-select.vue';
import ToolSelect from './components/tool-select.vue';
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
