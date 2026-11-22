<template>
  <main class="main-page">
    <PostItem v-for="post in posts" :key="post.id" :post-id="post.id" />

    <div class="reset-container">
      <button class="reset-button" @click="resetLikes">
        Reset Likes
      </button>
    </div>
  </main>
</template>

<script>
import PostItem from '../components/PostItem.vue'

export default {
  name: 'HomeView',
  components: {
    PostItem,
  },
  computed: {
    posts() {
      return this.$store.state.posts
    },
  },

  methods: {
    resetLikes() {
      this.$store.commit('resetLikes')
    },
  },
}
</script>

<style scoped>
.main-page {
  max-width: 500px;
  margin: 0 auto;
  padding: 20px 10px;
}

.reset-container {
  display: flex;
  justify-content: center;
  margin-top: 25px;
  margin-bottom: 20px;
}

.reset-button {
  background-color: #dc3545;
  color: white;
  border: none;
  border-radius: 8px;
  padding: 12px 24px;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  transition: background-color 0.2s ease;
}

.reset-button:hover {
  background-color: #b02a37;
}

.reset-button:active {
  transform: scale(0.98);
}

.reset-button:focus-visible {
  outline: 3px solid #ff9aa5;
  outline-offset: 3px;
}
</style>