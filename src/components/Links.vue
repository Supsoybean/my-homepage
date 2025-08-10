<template>
  <div class="links-container">
    <a href="#" class="link-icon" title="GitHub">
      <i class="iconfont icon-github-fill"></i>
    </a>
    <a href="#" class="link-icon" title="个人博客">
      <i class="iconfont icon-boke"></i>
    </a>
    <a href="#" class="link-icon" title="邮箱">
      <i class="iconfont icon-youxiang"></i>
    </a>
    <a href="#" class="link-icon" title="Bilibili">
      <i class="iconfont icon-bilibili"></i>
    </a>
  </div>
</template>

<script setup>
</script>

<style scoped>
.links-container {
  display: flex;
  gap: 1rem;
  padding: 0.8rem 1.5rem;
  background: var(--card-bg-color);
  border-radius: 50px;
  backdrop-filter: blur(10px);
  border: 1px solid var(--card-border-color);
  width: fit-content;
}

.link-icon {
  color: var(--text-color);
  transition: all 0.2s ease;
  text-decoration: none;
}

.link-icon:hover {
  transform: scale(1.2);
  color: #fff; /* 鼠标悬浮时，图标颜色变白 */
}

/* 设置图标大小 */
.link-icon .iconfont {
  font-size: 24px;
}
</style>