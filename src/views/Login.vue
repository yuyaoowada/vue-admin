<template>
  <main class="form-signin">
    <form @submit.prevent="submit">
      <h1 class="h3 mb-3 fw-normal">サインインする</h1>

      <input v-model="email" type="email" class="form-control" placeholder="メールアドレス">
      <input v-model="password" type="password" class="form-control" placeholder="パスワード">

      <button class="w-100 btn btn-lg btn-primary" type="submit">サインイン</button>
    </form>
  </main>
</template>

<script>
import axios from "axios";

export default {
  name: "Login",
  data() {
    return {
      email: '',
      password: '',
    }
  },
  methods: {
    async submit() {
      await axios.post('login', {
        email:this.email,
        password: this.password,
      })

      await this.$router.push('/')
    }
  }
}
</script>

<style scoped>
html,
body {
  height: 100%;
}

body {
  display: flex;
  align-items: center;
  padding-top: 40px;
  padding-bottom: 40px;
  background-color: #f5f5f5;
}

.form-signin {
  width: 100%;
  max-width: 330px;
  padding: 15px;
  margin: auto;
}
.form-signin .form-control {
  position: relative;
  box-sizing: border-box;
  height: auto;
  padding: 10px;
  font-size: 16px;
}
.form-signin .form-control:focus {
  z-index: 2;
}
.form-signin input[type="email"] {
  margin-bottom: -1px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.form-signin input[type="password"] {
  margin-bottom: 10px;
  border-top-left-radius: 0;
  border-top-right-radius: 0;
}
</style>
