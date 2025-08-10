<template>
  <div class="wooden-fish-container">
    
    <div class="fish-wrapper">
      <img
        src="/assets/muyu.png"
        alt="Large Wooden Fish"
        class="fish-img large"
        :class="{ knocking: isKnocking }" @click="knock"                      />
      <div v-if="showPlusOne" class="plus-one-animation">功德 +1</div>
    </div>

    <div class="merit-counter">功德: {{ meritCount }}</div>
  </div>
</template>

<script setup>
// 导入 ref, 用于创建控制动画的响应式状态
import { ref } from 'vue';

// 声明组件可以接收的来自父组件 (App.vue -> Header.vue) 的数据和方法
const props = defineProps({
  meritCount: Number,       // 当前的功德总数
  onIncrementMerit: Function, // 增加功德数的方法
});

// 定义两个本地的响应式状态，用于触发 CSS 动画
const isKnocking = ref(false);  // 控制木鱼敲击动画
const showPlusOne = ref(false); // 控制“功德+1”文字的出现

// 点击木鱼时执行的核心函数
const knock = () => {
  // 1. 调用从父组件传来的方法，让 App.vue 中的功德总数 +1
  props.onIncrementMerit();
  
  // 2. 立即将动画状态设为 true，触发动画效果
  isKnocking.value = true;
  showPlusOne.value = true;
  
  // 3. 使用 setTimeout 在动画结束后，将状态重置为 false，以便下次点击
  setTimeout(() => {
    isKnocking.value = false;
  }, 150); // 150毫秒后重置敲击动画，应与 CSS 动画时长一致
  
  setTimeout(() => {
    showPlusOne.value = false;
  }, 800); // 800毫秒后隐藏“功德+1”文字，应与 CSS 动画时长一致
};
</script>

<style scoped>
/* 整个组件的容器：弹性布局，让木鱼和功德计数横向排列 */
.wooden-fish-container {
  display: flex;
  align-items: center;
  gap: 1.5rem;
}

/* 木鱼图片和 "+1" 动画的包裹容器 */
.fish-wrapper {
  position: relative; /* 为 "+1" 动画提供绝对定位的参考点 */
}

/* 木鱼的尺寸 */
.large {
  width: 120px;
  height: 120px;
}

/* 木鱼图片的基础样式 */
.fish-img {
  cursor: pointer; /* 鼠标悬浮时显示手型光标 */
  transition: transform 0.1s ease;
  filter: drop-shadow(0 4px 8px rgba(0, 0, 0, 0.2)); /* 添加阴影增加立体感 */
}

/* 鼠标按下时的交互效果 */
.fish-img:active {
  transform: scale(0.95);
}

/* "knocking" 类被添加时，播放名为 knock-animation 的动画 */
.fish-img.knocking {
  animation: knock-animation 0.15s ease-in-out;
}

/* 定义敲击动画的关键帧 */
@keyframes knock-animation {
  0% { transform: scale(1); }
  50% { transform: scale(0.9); }
  100% { transform: scale(1); }
}

/* 功德计数器的样式 */
.merit-counter {
  font-size: 1.1rem;
  font-weight: bold;
  color: var(--text-color);
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.5);
}

/* “功德+1” 动画文字的样式 */
.plus-one-animation {
  position: absolute; /* 绝对定位于 fish-wrapper 内 */
  top: 0; /* 从木鱼图片的顶部开始 */
  left: 50%; /* 水平居中 */
  font-size: 1.1rem;
  font-weight: bold;
  color: #f9d423;
  text-shadow: 0 1px 3px rgba(0, 0, 0, 0.7);
  animation: plus-one-fade-up 0.8s ease-out forwards;
  pointer-events: none;
  /* 初始时水平居中，并稍微向上偏移一点，以免挡住木鱼 */
  transform: translate(-50%, -20%); 
  white-space: nowrap;
}

/* 定义“功德+1”向上飘散消失的动画关键帧 */
@keyframes plus-one-fade-up {
  from {
    opacity: 1;
    transform: translate(-50%, -10%);
  }
  to {
    opacity: 0;
    transform: translate(-50%, -100%);
  }
}
</style>