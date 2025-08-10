<template>
  <div class="info-card-content">
    <div class="location-info glass-card">
      <div class="info-item">
        <svg class="icon" aria-hidden="true">
        <use xlink:href="#icon-diqiu"></use> 
      </svg>
        <span>HangZhou, China</span>
      </div>
      <div class="info-item">
        <svg class="icon" aria-hidden="true">
        <use xlink:href="#icon-fangzi"></use>
      </svg>
        <span>A plain ordinary place</span>
      </div>
    </div>
    <div class="tags-container glass-card">
      <div class="tags">
        <span class="tag">Vue.js</span>
        <span class="tag">Python</span>
        <span class="tag">大三</span>
        <span class="tag">技术小白</span>
        <span class="tag">佛系青年</span>
        <span class="tag">代码洁癖</span>
        <span class="tag">旅行</span>
        <span class="tag">Minecraft</span>
      </div>
    </div>
  </div>
</template>

<style scoped>
.info-card-content {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.location-info {
  padding: 1rem;
  display: flex;
  flex-direction: column;
  gap: 0.8rem;
}

.info-item {
  display: flex;
  align-items: center;
  gap: 0.8rem;
  font-size: 0.9rem;
  color: var(--text-color-light);
}

.info-item .iconfont {
  font-size: 18px;
  color: var(--text-color);
}

.tags-container {
  padding: 1rem;
}

.tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.tag {
  background-color: rgba(0, 0, 0, 0.2);
  padding: 0.2rem 0.6rem;
  border-radius: 5px;
  font-size: 0.8rem;
}

.icon {
  width: 1.1em;
  height: 1.1em;

  vertical-align: -0.2em; 
  
  fill: currentColor;
  overflow: hidden;
}
</style>