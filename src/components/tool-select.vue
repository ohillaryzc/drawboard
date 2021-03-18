<template>
  <div class="tool-select-box">
    <div
      v-for="(item, index) in tools"
      :key="index"
      :class="['tool-select-item', index === active ? 'active' : '']"
      :title="item.title"
      @click="changeTool(index)"
    >
      <img :src="item.icon" alt="" width="30">
    </div>
    <div class="tool-select-item line-width-control">
      <div class="line-width" :style="{ height: `${width}px`, backgroundColor: color || '#000' }"></div>
      <div class="progress-box">
        <div class="arrow-border"></div>
        <div class="progress-line">
          <div class="active-line" :style="{ width: `${len}px` }"></div>
          <div
            class="progress-round"
            :style="{ left: `${len - 5}px` }"
            @mousedown="startMove"
          >
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
  import { ref, defineProps } from 'vue';
  import pencil from '/src/assets/icon-pencil.png?url';
  import eraser from '/src/assets/icon-eraser.png?url';
  import save from '/src/assets/icon-save.png?url';

  defineProps({
    color: String,
  });
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

  const width = ref(1);
  const len = ref(10);
  const startMove = (e) => {
    const startX = e.clientX;
    const startValue = len.value;
    document.onmousemove = (e) => {
      e.preventDefault();
      const value = e.clientX - startX + startValue;
      if (value > 10 && value <= 100) {
        len.value = value;
        width.value = value / 10;
      }
    };
  };
  document.onmouseup = () => {
    if (document.onmousemove) {
      document.onmousemove = null;
    }
  };
</script>

<style scoped lang="less">
  .tool-select-box {
    position: fixed;
    top: 20px;
    left: 50%;
    margin-left: -164px;
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
    box-shadow: 0 0 28px 4px rgba(0, 0, 0, .1);
    box-sizing: border-box;
    cursor: pointer;
  }
  .tool-select-item.active {
    border: 1px solid #007fff;
  }
  .line-width-control {
    position: relative;
  }
  .line-width {
    width: 40px;
    height: 10px;
    border-radius: 5px;
    background-color: #000;
    transform: rotate(-45deg);
  }
  .progress-box {
    position: absolute;
    top: 5px;
    left: 66px;
    width: 120px;
    height: 40px;
    background-color: #fff;
    box-shadow: 0 0 5px 0 #eee;
    border-radius: 4px;
    .arrow-border {
      position: absolute;
      top: 14px;
      left: -8px;
      width: 8px;
      height: 12px;
      border-top: 6px solid rgba(0, 0, 0, 0);
      border-bottom: 6px solid rgba(0, 0, 0, 0);
      border-right: 8px solid #eee;
      box-sizing: border-box;
    }
    .progress-line {
      position: relative;
      top: 17px;
      left: 10px;
      width: 100px;
      height: 6px;
      box-sizing: border-box;
      background-color: #999999;
      border-radius: 3px;
      .active-line {
        position: absolute;
        left: 0;
        top: 0;
        bottom: 0;
        width: 10px;
        background-color: #91d5ff;
        border-radius: 3px;
      }
      .progress-round {
        position: absolute;
        left: 5px;
        top: -2px;
        width: 10px;
        height: 10px;
        background-color: #eee;
        border-radius: 50%;
      }
    }
  }
</style>
