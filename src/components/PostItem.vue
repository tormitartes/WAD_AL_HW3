<template>
  <article class="post">
    <div class="post-meta">
      <span>👤 {{ post.author }}</span>
      <span>{{ formattedDate }}</span>
    </div>
    <img v-if="post.image" :src="post.image" :alt="post.imageAlt" class="post-image" />
    <p class="post-text">{{ post.text }}</p>
  </article>
</template>

<script>
export default {
  name: 'PostItem',
  props: {
    post: {
      type: Object,
      required: true,
    },
  },
  computed: {
    formattedDate() {
      return new Date(this.post.createdAt).toLocaleDateString('en-US', {
        year: 'numeric',
        month: 'short',
        day: 'numeric',
        timeZone: 'UTC',
      })
    },
  },
}
</script>

<style scoped>
.post {
  background-color: #e0e0e0;
  border-radius: 10px;
  padding: 10px;
  margin-bottom: 15px;
}

.post-meta {
  display: flex;
  justify-content: space-between;
  font-size: 13px;
}

.post-image {
  width: 100%;
  border-radius: 6px;
  margin-top: 8px;
}

.post-text {
  margin: 8px 0 0;
}
</style>