<template>
  <div id="main-board"></div>
</template>

<script setup>
import { onMounted, defineProps } from 'vue';

const props = defineProps({
  color: String,
  lineWidth: Number,
  action: String,
});

const winW = document.body.clientWidth;
const winH = document.body.clientHeight;

const canvas = document.createElement('canvas');
canvas.width = winW;
canvas.height = winH;
canvas.onmousedown = (e) => {
  drawLineStart();
  let startX = e.layerX;
  let startY = e.layerY;
  canvas.onmousemove = (e) => {
    const moveX = e.layerX;
    const moveY = e.layerY;
    drawLine(startX, moveX, startY, moveY);
    startX = moveX;
    startY = moveY;
  };
  document.onmouseup = () => {
    if (canvas.onmousemove) {
      drawLineEnd();
      canvas.onmousemove = null;
    }
  };
};
const ctx = canvas.getContext('2d');
const drawLineStart = () => {
  ctx.beginPath();
  ctx.strokeStyle = props.color;
  ctx.lineWidth = props.lineWidth;
  ctx.lineCap = 'round';
  ctx.lineJoin = 'round';
};
const drawLine = (x1, x2, y1, y2) => {
  ctx.moveTo(x1, y1);
  ctx.lineTo(x2, y2);
  ctx.stroke();
};
const drawLineEnd = () => {
  ctx.closePath();
};
onMounted(() => {
  document.getElementById('main-board').appendChild(canvas);
});
</script>

<style scoped>

</style>
