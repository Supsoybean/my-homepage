<template>
  <a :href="link" class="card-link" target="_blank" rel="noopener noreferrer">
    <div class="card glass-card">
      
      <div class="card-icon">
        <svg v-if="iconSymbolId" class="icon" aria-hidden="true">
          <use :xlink:href="`#${iconSymbolId}`"></use>
        </svg>

        <i v-else class="iconfont" :class="iconClass"></i>
      </div>

      <div class="card-content">
        <h3>{{ title }}</h3>
        <p>{{ description }}</p>
      </div>

    </div>
  </a>
</template>

<script setup>
// defineProps 用来声明这个组件可以从父组件接收哪些数据
defineProps({
  title: String,        // 卡片标题
  description: String,  // 卡片描述
  link: String,         // 卡片点击后跳转的链接
  iconClass: String,    // 单色字体图标的 CSS 类名
  iconSymbolId: String, // 彩色 SVG 图标的 Symbol ID
});
</script>

<style scoped>
/* 卡片链接的基础样式 */
.card-link {
  text-decoration: none; /* 去掉链接下划线 */
  color: inherit; /* 继承父元素的文字颜色 */
}
/* 卡片主体：弹性布局，让图标和文字横向排列 */
.card {
  display: flex;
  align-items: center; /* 垂直居中对齐 */
  gap: 1rem; /* 图标和文字之间的间距 */
  transition: all 0.3s ease; /* 让所有变化的属性都有0.3秒的过渡动画 */
}
/* 卡片鼠标悬浮时的效果 */
.card:hover {
  transform: translateY(-5px); /* 向上移动5像素 */
  background: rgba(255, 255, 255, 0.25); /* 改变背景色 */
  border-color: rgba(255, 255, 255, 0.4); /* 改变边框颜色 */
}
/* 左侧图标容器的样式 */
.card-icon {
  background-color: rgba(0, 0, 0, 0.15);
  padding: 0.8rem;
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 56px; /* 固定宽度 */
  height: 56px; /* 固定高度 */
  box-sizing: border-box; /* 让 padding 不会撑大盒子尺寸 */
}

/* 单色字体图标的大小 */
.card-icon .iconfont {
  font-size: 28px;
  color: var(--text-color);
}

/* 彩色 SVG 图标的大小 */
.card-icon .icon {
  width: 32px;
  height: 32px;
}

/* 右侧文字内容的标题样式 */
.card-content h3 {
  font-size: 1.1rem;
  margin: 0 0 0.2rem 0; /* 标题和描述之间增加一点小间距 */
}
/* 右侧文字内容的描述样式 */
.card-content p {
  font-size: 0.9rem;
  color: var(--text-color-light);
  margin: 0;
}
</style>