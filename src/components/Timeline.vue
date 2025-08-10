<template>
  <div class="timeline-card glass-card">
    <ul>
      <li v-for="item in timelineEvents" :key="item.date">
        <div class="date">{{ item.date }}</div>
        <div class="event">{{ item.event }}</div>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const timelineEvents = ref([
  { date: '2025.10', event: 'ICP备案成功' },
  { date: '2025.9', event: '注册域名ziyo.net' },
  { date: '2025.8', event: '完善静态网页' },
  { date: '2025.7', event: '产生设计网页想法' },
]);
</script>

<style scoped>
.timeline-card {
  padding: 1.5rem 1rem 1.5rem 2.5rem; /* 左侧留出更多空间给线条 */
}

ul {
  list-style-type: none;
  padding: 0;
  margin: 0;
  position: relative;
}

/* 绘制时间线的竖线 */
ul::before {
  content: '';
  position: absolute;
  left: -18px;
  top: 5px;
  bottom: 5px;
  width: 2px;
  background: rgba(255, 255, 255, 0.2);
}

li {
  margin-bottom: 1rem;
  position: relative;
}

li:last-child {
  margin-bottom: 0;
}

/* 绘制时间线上的圆点 */
li::before {
  content: '';
  position: absolute;
  left: -23px;
  top: 6px;
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.4);
  border: 2px solid rgba(255, 255, 255, 0.8);
}

.date {
  font-size: 0.8rem;
  color: var(--text-color-light);
  margin-bottom: 0.2rem;
}

.event {
  font-size: 0.9rem;
  font-weight: 500;
}
</style>