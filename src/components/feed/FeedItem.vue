<template>
  <div class="feed-item glass-card">
    <div class="item-header">
      <img :src="post.avatar" alt="avatar" class="avatar">
      <div class="author-info">
        <span class="author-name">{{ post.author }}</span>
        <span class="timestamp">{{ post.timestamp }}</span>
      </div>
    </div>
    <div class="item-content">
      <p v-if="post.content">{{ post.content }}</p>
      
      <div v-if="post.type === 'share_post' && post.shared" class="shared-content">
        <a :href="post.shared.link" target="_blank" rel="noopener noreferrer">
          <h4>{{ post.shared.title }}</h4>
          <p>{{ post.shared.description }}</p>
        </a>
      </div>
      
      <div v-if="post.images && post.images.length > 0" class="image-grid">
        <img v-for="(img, index) in post.images" :key="index" :src="img" alt="post image">
      </div>
    </div>
    </div>
</template>

<script setup>
defineProps({
  post: {
    type: Object,
    required: true
  }
});
</script>

<style scoped>
.feed-item {
  padding: 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
.item-header {
  display: flex;
  align-items: center;
  gap: 0.8rem;
}
.avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
}
.author-info {
  display: flex;
  flex-direction: column;
}
.author-name {
  font-weight: bold;
  font-size: 1rem;
  color: var(--text-color);
}
.timestamp {
  font-size: 0.8rem;
  color: var(--text-color-light);
}
.item-content p {
  margin: 0;
  line-height: 1.6;
  white-space: pre-wrap;
}
.shared-content {
  background-color: rgba(0, 0, 0, 0.2);
  padding: 1rem;
  border-radius: 8px;
  margin-top: 1rem;
  transition: background-color 0.2s;
}
.shared-content:hover {
  background-color: rgba(0, 0, 0, 0.3);
}
.shared-content a {
  text-decoration: none;
  color: inherit;
}
.shared-content h4 {
  margin: 0 0 0.5rem 0;
}
.shared-content p {
  font-size: 0.9rem;
  color: var(--text-color-light);
  margin: 0;
}
.image-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
  gap: 0.5rem;
  margin-top: 1rem;
}
.image-grid img {
  width: 100%;
  height: 150px;
  object-fit: cover;
  border-radius: 8px;
}
/* ▼▼▼ .item-footer 相关的 CSS 已整个移除 ▼▼▼ */
</style>