<template>
  <div class="section">
    <h2>Project</h2>
    <div class="card-grid">
      <Card
        v-for="project in projects"
        :key="project.title"
        :title="project.title"
        :description="project.description"
        :link="project.link"
        
        :iconClass="project.iconClass"
        :iconSymbolId="project.iconSymbolId"
      />
    </div>
  </div>
</template>

<script setup>
// 从 Vue 中导入 ref, 用于创建响应式的数据数组
import { ref } from 'vue';
// 导入可复用的 Card 子组件
import Card from '../Card.vue';

// 使用 ref 创建一个响应式的数组，用来存储所有项目卡片的数据
// 如何修改：在这里修改或添加对象，就可以改变页面上显示的“Project”卡片
const projects = ref([
  { 
    title: '个人主页', 
    description: '记录·思考·分享', 
    link: 'https://github.com/Supsoybean/my-homepage', 
    // 这个卡片使用 iconClass 属性，会显示单色的字体图标
    iconClass: 'icon-zhuye' 
  },
  { 
    title: 'MC MapArt', 
    description: '生成MC像素画', 
    link: 'https://github.com/Supsoybean/Minecraft_MapArt/tree/main', 
    // 这个卡片使用 iconSymbolId 属性，会显示彩色的 SVG 图标
    iconSymbolId: 'icon-minecraft'
  },
]);
</script>

<style scoped>
/* "Project" 标题的样式 */
.section h2 {
  margin-bottom: 1rem;
  font-size: 1.5rem;
}
/* 卡片网格容器的样式 */
.card-grid {
  display: grid;
  /* 定义网格列：自动填充，每列最小220px，最大占满可用空间 (1fr) */
  grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
  gap: 1rem; /* 定义网格项之间的间距 */
}
</style>