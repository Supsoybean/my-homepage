<template>
  <div class="graph-container glass-card">
    <div class="graph">
      <div
        v-for="level in squareLevels"
        :key="level.id"
        class="day"
        :style="{ backgroundColor: level.color }"
      ></div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const totalSquares = 53 * 7;
const colors = ['#e0e0e0', '#ff4d4d', '#ffa64d', '#ffff4d', '#4dff4d', '#4d4dff', '#a64dff'];
const squareLevels = ref(
  Array.from({ length: totalSquares }, (_, i) => ({ id: i, color: colors[0] }))
);

// 1. 修改变色速度 (单位：毫秒)
//    这个数值越小，整体动画看起来就越快。
//    例如：50 -> 很快, 200 -> 慢速
const CHANGE_INTERVAL_MS = 100; // 当前是每 100 毫秒变动一次

// 2. 修改同时变色的方块数量
//    这个数值代表了每次变动时，有多少个方块会同时改变颜色。
const SQUARES_PER_TICK = 1; // 当前是每次只改变 1 个方块

let intervalId = null;

onMounted(() => {
  // 定时器会使用你上面设置的 CHANGE_INTERVAL_MS 变量作为速度
  intervalId = setInterval(() => {
    // for 循环会根据你上面设置的 SQUARES_PER_TICK 变量来决定执行次数
    for (let i = 0; i < SQUARES_PER_TICK; i++) {
      const randomIndex = Math.floor(Math.random() * totalSquares);
      const randomColorIndex = Math.floor(Math.random() * colors.length);
      squareLevels.value[randomIndex].color = colors[randomColorIndex];
    }
  }, CHANGE_INTERVAL_MS);
});

onUnmounted(() => {
  if (intervalId) {
    clearInterval(intervalId);
  }
});
</script>

<style scoped>
.graph-container {
  padding: 1rem;
  border-radius: 10px;
}
.graph{display:grid;grid-template-columns:repeat(53,1fr);grid-template-rows:repeat(7,auto);gap:3px;}
.day{aspect-ratio:1/1;border-radius:3px;transition: background-color 0.2s ease;}
</style>