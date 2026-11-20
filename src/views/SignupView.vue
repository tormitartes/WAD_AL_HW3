<template>
  <main class="signup-page">
    <form class="signup-form" @submit.prevent>
      <div class="form-row">
        <label for="email">Email</label>
        <input id="email" type="email" placeholder="Email" v-model="email" />
      </div>
      <div class="form-row">
        <label for="password">Password</label>
        <input id="password" type="password" placeholder="Password" v-model="password" />
      </div>
      <button type="submit">Signup</button>
    </form>
  </main>
</template>

<script>
export default {
  name: 'SignupView',
  data() {
    return {
      email: '',
      password: '',
    }
  },
}
</script>

<style scoped>
.signup-page {
  max-width: 500px;
  margin: 0 auto;
  padding: 40px 10px;
}

.signup-form {
  background-color: #e0e0e0;
  border-radius: 10px;
  padding: 20px;
  text-align: center;
}

.form-row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 15px;
}

.form-row input {
  width: 70%;
  padding: 6px;
}

button {
  padding: 6px 20px;
  cursor: pointer;
}
</style>