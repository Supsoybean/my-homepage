<template>
  <div class="section">
    <h2>Site</h2>
    <div class="card-grid">
      <div v-for="site in sites" :key="site.title" @click="handleCardClick(site, $event)">
        <Card
          :title="site.title"
          :description="site.description"
          :link="site.link"
          :iconClass="site.icon"
        />
      </div>
    </div>
  </div>
</template>

<script setup>
// 从 Vue 中导入 ref, 用于创建响应式的数据数组
import { ref } from 'vue';
// 导入可复用的 Card 子组件
import Card from '../Card.vue';

// 定义本组件可以向父组件 (App.vue) 发出的所有通知（事件）
const emit = defineEmits(['change-view']);

// 使用 ref 创建一个响应式的数组，用来存储所有卡片的数据
// 如何修改：在这里修改或添加对象，就可以改变页面上显示的卡片内容
const sites = ref([
  { id: 'blog', title: '博客', description: '记录学习生活', icon: 'icon-bi' },
  { id: 'docs', title: '文稿站', description: '记录学习笔记', link: 'https://github.com/Supsoybean/Learning-Notes', icon: 'icon-shiyongwendang' },
  { id: 'test', title: '测试', description: '一些小测试', link: '#', icon: 'icon-wrench' },
  { id: 'about', title: '关于', description: '关于本站', link: '#', icon: 'icon-yonghu' },
]);

// 定义处理卡片点击事件的函数
const handleCardClick = (site, event) => {
  // 判断被点击的卡片的 id 是否为 'blog' 或 'test'
  if (site.id === 'blog' || site.id === 'test') {
    // 如果是，则阻止 <a> 标签的默认跳转行为
    event.preventDefault(); 
    // 然后，向父组件 App.vue 发出名为 'change-view' 的通知，并附带上卡片的 id
    emit('change-view', site.id);
  }
  // 如果不是 'blog' 或 'test'，则不执行任何特殊操作，浏览器会默认执行 <a> 标签的跳转
};
</script>

<style scoped>
/* "Site" 标题的样式 */
.section h2 {
  margin-bottom: 1rem;
  font-size: 1.5rem;
}
/* 卡片网格容器的样式 */
.card-grid {
  display: grid; /* 使用网格布局 */
  /* 定义网格列：自动填充，每列最小220px，最大占满可用空间 (1fr) */
  grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
  gap: 1rem; /* 定义网格项之间的间距 */
}
/* 为每个卡片的直接父级 div 添加手型光标，提示用户可以点击 */
.card-grid > div {
  cursor: pointer;
}
</style>