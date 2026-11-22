<template>
  <article class="post">
    <div class="post-meta">
      <span>👤 {{ post.author }}</span>
      <span>{{ formattedDate }}</span>
    </div>
    <img v-if="post.image" :src="post.image" :alt="post.imageAlt" class="post-image" />
    <p class="post-text">{{ post.text }}</p>
    <button @click="likePost">
      👍 {{post.likes}}
    </button>
  </article>
</template>

<script>
export default {
  name: 'PostItem',
  props: {
    postId: {
      type: Number,
      required: true,
    },
  },
  computed: {
    post() {
      return this.$store.state.posts.find((p) => p.id === this.postId)
    },
    formattedDate() {
      return new Date(this.post.createdAt).toLocaleDateString('en-US', {
        year: 'numeric',
        month: 'short',
        day: 'numeric',
        timeZone: 'UTC',
      })
    },
  },
  methods: {
    likePost() {
      this.$store.commit('incrementLikes', this.postId)
    },
  },
}
</script>

<style scoped>
.post {
  background-color: #e0e0e0;
  border-radius: 10px;
  padding: 15px 20px;
  margin-bottom: 15px;
}

.post-meta {
  display: flex;
  justify-content: space-between;
  font-size: 14px;
  margin-bottom: 4px;

}

.post-image {
  display: block;
  width: 100%;
  border-radius: 8px;
  margin-top: 10px;
  max-height: 600px;
}

.post-text {
  margin: 12px 0 0;
}
button {
  align-items: center;
  margin-top: 15px;
  padding: 5px 15px;
  background-color: #b2abab;
  font-size: 14px;
  border-radius: 100px;
  border-color: transparent;
  cursor: pointer;
}
button:hover {
  background-color: #a3a0a0;
}
</style>