<template>
  <div class="test-view">
    <div class="test-header">
      <h3>效果实验室</h3>
      <button @click="$emit('back-to-home')">返回主页</button>
    </div>

    <div class="grid-showcase">
      <h4>效果一：点击变色（随机初始色）</h4>
      <ClickToColorGrid />
    </div>

    <div class="grid-showcase">
      <h4>效果二：鼠标拖动划过变色</h4>
      <DragToColorGrid />
    </div>

    <div class="grid-showcase">
      <h4>效果三：方块自动随机变色</h4>
      <AutoColorChangeGrid />
    </div>

  </div>
</template>

<script setup>
import ClickToColorGrid from './ClickToColorGrid.vue';
import DragToColorGrid from './DragToColorGrid.vue';
import AutoColorChangeGrid from './AutoColorChangeGrid.vue';

defineEmits(['back-to-home']);
</script>

<style scoped>
.test-view {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}
.test-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: var(--text-color);
}
.test-header h3 {
  margin: 0;
  font-size: 1.8rem;
}
.test-header button {
  background-color: rgba(255, 255, 255, 0.25);
  border: 1px solid rgba(255, 255, 255, 0.3);
  color: var(--text-color);
  padding: 0.5rem 1rem;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.2s;
  font-weight: 500;
}
.test-header button:hover {
  background-color: rgba(255, 255, 255, 0.35);
}
.grid-showcase {
  padding: 1.5rem;
  border-radius: 15px;
  background-color: rgba(255, 255, 255, 0.15);
  border: 1px solid rgba(255, 255, 255, 0.2);
}

/* ▼▼▼ 在这里修改 ▼▼▼ */
.grid-showcase h4 {
  margin-top: 0;
  margin-bottom: 1rem;
  font-weight: 700;
  /* 保持文字为浅色，与整体风格统一 */
  color: #e0e7ff; 
  /* 新增：添加一层淡淡的黑色文字阴影来增加对比度 */
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.7); 
}
</style>