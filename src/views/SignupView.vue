<template>
  <main class="signup-page">
    <form class="signup-form" @submit.prevent="onSubmit">
      <div class="form-row">
        <label for="email">Email</label>
        <input id="email" type="email" placeholder="Email" v-model="email" />
      </div>
      <div class="form-row">
        <label for="password">Password</label>
        <input id="password" type="password" placeholder="Password" v-model="password" />
      </div>
      <button type="submit">Signup</button>

      <!-- shown when Signup rules are failed -->
      
      <div v-if="submitted && failedRules.length" class="error-box">
        <p>The password is not valid -</p>
        <ul>
          <li v-for="rule in failedRules" :key="rule.label">{{ rule.label }}</li>
        </ul>
      </div>

      <p v-if="submitted && !failedRules.length" class="success-box">
        The password is valid.
      </p>
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
      submitted: false,
      // each rule
      rules: [
        {
          label: 'The password should be at least 8 characters and less than 15 characters',
          test: (p) => p.length >= 8 && p.length < 15,
        },
        {
          label: 'Includes at least one uppercase alphabet character',
          test: (p) => /\p{Lu}/u.test(p),
        },
        {
          label: 'Includes at least two lowercase alphabet characters',
          test: (p) => (p.match(/\p{Ll}/gu) || []).length >= 2,
        },
        {
          label: 'Includes at least one numeric value',
          test: (p) => /[0-9]/.test(p),
        },
        {
          label: 'It should start with an uppercase letter',
          test: (p) => /^\p{Lu}/u.test(p),
        },
        {
          label: 'It should include the character "_"',
          test: (p) => p.includes('_'),
        },
      ],
    }
  },
  computed: {
    // the rules that the current password does not satisfy
    failedRules() {
      return this.rules.filter((rule) => !rule.test(this.password))
    },
  },
  methods: {
    onSubmit() {
      this.submitted = true
    },
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

.error-box {
  margin-top: 15px;
  padding: 8px 12px;
  text-align: left;
  background-color: #d9c5c5;
  border: 2px solid #bf5353;
  border-radius: 8px;
  color: #a7241f;
  font-size: 14px;
}

.error-box p {
  font-weight: bold;
}

.error-box ul {
  margin: 0;
  padding-left: 20px;
}

.success-box {
  margin: 15px;
  padding: 8px 12px;
  text-align: center;
  background-color: #d7e7d0;
  border: 2px solid #5bbf5b;
  border-radius: 8px;
  color: #2b5b25;
  font-size: 14px;
}
</style>
