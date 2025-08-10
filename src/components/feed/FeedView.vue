<template>
  <div class="feed-view">
    <div class="feed-header">
      <h3>我的动态</h3>
      <button @click="$emit('back-to-home')">返回主页</button>
    </div>
    <div class="feed-list">
      <FeedItem v-for="post in posts" :key="post.id" :post="post" />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import FeedItem from './FeedItem.vue';
import { feedData } from '@/data/feedData.js'; // 引入模拟数据

const posts = ref(feedData);

// 定义组件可以发出的事件
defineEmits(['back-to-home']);
</script>

<style scoped>
.feed-view {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}
.feed-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: var(--text-color);
}
.feed-header h3 {
  margin: 0;
  font-size: 1.8rem;
}
/* ▼▼▼ 在这里修改 ▼▼▼ */
.feed-header button {
  /* 将背景色的透明度从 0.1 提高到 0.25 */
  background-color: rgba(255, 255, 255, 0.25);
  border: 1px solid rgba(255, 255, 255, 0.3);
  color: var(--text-color);
  padding: 0.5rem 1rem;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.2s;
  font-weight: 500; /* 可以适当加粗字体 */
}
.feed-header button:hover {
  /* 悬浮时的背景色也相应加深 */
  background-color: rgba(255, 255, 255, 0.35);
}
</style>