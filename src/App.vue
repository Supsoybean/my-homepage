<template>
  <div id="homepage">
    <Header 
      :merit-count="meritCount"           
      :on-increment-merit="incrementMerit" 
    />

    <main class="main-content">
      <div class="left-panel">
        <InfoCard />
        <Timeline />
      </div>

      <div v-if="currentView === 'home'" class="right-panel">
        <Links />
        <ContributionGraph />
        <SiteSection @change-view="changeView" />
        <ProjectSection />
      </div>

      <FeedView v-else-if="currentView === 'blog'" @back-to-home="changeView('home')" />
      
      <TestView v-else-if="currentView === 'test'" @back-to-home="changeView('home')" />

    </main>
  </div>
</template>

<script setup>
// 从 Vue 中导入 ref, 用于创建响应式变量
import { ref } from 'vue';

// 导入所有需要用到的子组件
import Header from './components/Header.vue';
import InfoCard from './components/InfoCard.vue';
import Links from './components/Links.vue';
import ContributionGraph from './components/ContributionGraph.vue';
import SiteSection from './components/sections/SiteSection.vue';
import ProjectSection from './components/sections/ProjectSection.vue';
import Timeline from './components/Timeline.vue';
import FeedView from './components/feed/FeedView.vue';
import TestView from './components/test-grids/TestView.vue';

// 定义功德数的状态，存在 App.vue 中以保持持久
const meritCount = ref(0);
// 定义增加功德数的方法
const incrementMerit = () => {
  meritCount.value++;
};

// 定义控制当前视图的响应式变量，默认为 'home'
const currentView = ref('home');
// 定义切换视图的通用方法
const changeView = (viewName) => {
  currentView.value = viewName;
};
</script>

<style scoped>
/* 页面主容器：垂直弹性布局 */
#homepage {
  display: flex;
  flex-direction: column;
  gap: 2rem;
  width: 100%;
}
/* 主内容区：两栏网格布局 */
.main-content {
  display: grid;
  grid-template-columns: 240px 1fr; /* 左栏固定240px，右栏占满剩余空间 */
  gap: 2rem;
  width: 100%;
}
/* 左右两栏的通用布局：内部组件垂直排列 */
.left-panel, .right-panel {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}
/* 响应式布局：当屏幕宽度小于768px时 */
@media (max-width: 768px) {
  .main-content {
    grid-template-columns: 1fr; /* 变为单栏布局 */
  }
}
</style>