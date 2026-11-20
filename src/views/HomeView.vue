<template>
  <main class="main-page">
    <PostItem v-for="post in posts" :key="post.id" :post-id="post.id" />
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
}
</script>

<style scoped>
.main-page {
  max-width: 500px;
  margin: 0 auto;
  padding: 20px 10px;
}
</style>