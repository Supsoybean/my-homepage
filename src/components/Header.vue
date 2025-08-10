<template>
  <header class="header glass-card">
    <div class="title-group">
      <img src="/avatar.png" alt="Avatar" class="avatar">
      <div class="info">
        <h1>Hello I'm <span class="name">SupSoybean</span></h1>
        <div class="subtitle">
          <span class="tag">Self-taught Developer</span>
          <p class="quote">Success is not final, failure is not fatal: it is the courage to continue that counts.</p>
        </div>
      </div>
    </div>
    
    <WoodenFish 
      :merit-count="meritCount"
      :on-increment-merit="onIncrementMerit"
    />
  </header>
</template>

<script setup>
import WoodenFish from './WoodenFish.vue';

// 接收来自 App.vue 的数据和方法
defineProps({
  meritCount: Number,
  onIncrementMerit: Function,
});
</script>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 1.5rem;
  gap: 1.5rem;
}
.title-group {
  display: flex;
  align-items: center;
  gap: 1.5rem;
}
.avatar {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  border: 3px solid rgba(255, 255, 255, 0.5);
}
.info h1 {
  font-size: 2rem;
  font-weight: bold;
  margin: 0 0 0.5rem 0;
}
.name {
  background: linear-gradient(45deg, #42d392, #647eff);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}
.subtitle {
  display: flex;
  align-items: center;
  gap: 0.8rem;
}
.tag {
  background-color: rgba(0, 0, 0, 0.2);
  padding: 0.3rem 0.8rem;
  border-radius: 20px;
  font-size: 0.8rem;
  flex-shrink: 0;
}
.quote {
  margin: 0;
  color: var(--text-color-light);
  font-size: 0.9rem;
}
</style>