<template>
  <div class="graph-container glass-card">
    <div class="graph">
      <div
        v-for="(level, index) in squareLevels"
        :key="index"
        class="day"
        :style="{ backgroundColor: getBackgroundColor(index) }"
        title="点击改变颜色"
        
        @click="changeSquareColor(index)"
        
        @dragstart.prevent
      ></div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const totalSquares = 53 * 7; 

// --- 1. 新的颜色数组 ---
const colors = [
  '#e0e0e0',   // 等级 0: 浅色
  '#90ee90',   // 等级 1: 浅绿色
  '#006400',   // 等级 2: 深绿色
  '#00ced1',   // 等级 3: 青色 (DarkTurquoise)
  '#1e90ff',   // 等级 4: 蓝色 (DodgerBlue)
];

// --- 2. 实现初始颜色随机 ---
const createInitialLevels = () => {
  const levels = [];
  for (let i = 0; i < totalSquares; i++) {
    // 为每个方块生成一个 0 到 (colors.length - 1) 之间的随机整数
    const randomLevel = Math.floor(Math.random() * colors.length);
    levels.push(randomLevel);
  }
  return levels;
};

// 使用函数生成初始的、随机的等级数组
const squareLevels = ref(createInitialLevels());

// --- 3. 交互改回点击 ---

// 根据方块自身的等级获取背景色
const getBackgroundColor = (index) => {
  const level = squareLevels.value[index];
  return colors[level];
};

// 点击时，切换指定方块的颜色等级
const changeSquareColor = (index) => {
  const currentLevel = squareLevels.value[index];
  // 逻辑不变：让当前方块的等级 +1，并在所有颜色中循环
  const newLevel = (currentLevel + 1) % colors.length;
  squareLevels.value[index] = newLevel;
};

</script>

<style scoped>
.graph-container {
  padding: 1rem;
}
.graph {
  display: grid;
  grid-template-columns: repeat(53, 1fr); 
  grid-template-rows: repeat(7, auto);
  gap: 3px;
}
.day {
  aspect-ratio: 1 / 1; 
  border-radius: 3px;
  transition: transform 0.1s ease-in-out;
  cursor: pointer; 
  user-select: none;
}
.day:hover {
    transform: scale(1.2);
}
</style>