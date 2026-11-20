<template>
  <header class="header">
    <nav class="nav">
      <router-link to="/">Home</router-link>
      <router-link to="/signup">Signup</router-link>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'AppHeader',
}
</script>

<style scoped>
.header {
  background-color: #2c3e50;
  padding: 15px;
}

.nav {
  display: flex;
  justify-content: center;
  gap: 25px;
}

.nav a {
  color: white;
  text-decoration: none;
  font-weight: bold;
}

.nav a:hover,
.nav a.router-link-exact-active {
  text-decoration: underline;
}
</style>