<template>
  <div class="graph-container glass-card">
    <div class="graph">
      <div
        v-for="(level, index) in squareLevels"
        :key="index"
        class="day"
        :style="{ backgroundColor: colors[level] }"
        @mouseenter="changeSquareColor(index)"
        @dragstart.prevent
      ></div>
    </div>
  </div>
</template>

<script setup>
// ... script 部分保持不变 ...
import { ref } from 'vue';
const totalSquares = 53 * 7;
const colors = ['#e0e0e0', '#ff4d4d', '#ffa64d', '#ffff4d', '#4dff4d', '#4d4dff', '#a64dff'];
const squareLevels = ref(new Array(totalSquares).fill(0));
const changeSquareColor = (index) => {
  squareLevels.value[index] = (squareLevels.value[index] + 1) % colors.length;
};
</script>

<style scoped>
/* ▼▼▼ 修改：移除这里的 background-color，让 glass-card 生效 ▼▼▼ */
.graph-container {
  padding: 1rem;
  border-radius: 10px;
  /* background-color: rgba(0, 0, 0, 0.2); <-- 删除这一行 */
}
/* ... .graph 和 .day 的样式保持不变 ... */
.graph{display:grid;grid-template-columns:repeat(53,1fr);grid-template-rows:repeat(7,auto);gap:3px;}
.day{aspect-ratio:1/1;border-radius:3px;transition:transform .1s ease-in-out;cursor:pointer;user-select:none;}
.day:hover{transform:scale(1.2);}
</style>