<template>
  <main class="form-signin">
    <form @submit.prevent="submit">
      <h1 class="h3 mb-3 fw-normal">登録</h1>

      <input v-model="firstName" class="form-control" placeholder="名">
      <input v-model="lastName" class="form-control" placeholder="姓">
      <input v-model="email" type="email" class="form-control" placeholder="メールアドレス">
      <input v-model="password" type="password" class="form-control" placeholder="パスワード">
      <input v-model="passwordConfirm" type="password" class="form-control" placeholder="パスワード確認">

      <button class="w-100 btn btn-lg btn-primary" type="submit">登録</button>
    </form>
  </main>
</template>

<script>
import axios from "axios";

export default {
  name: "Register",
  data() {
    return {
      firstName: '',
      lastName:'',
      email: '',
      password: '',
      passwordConfirm: '',
    }
  },
  methods: {
    async submit() {
      await axios.post('register', {
        first_name: this.firstName,
        last_name: this.lastName,
        email: this.email,
        password: this.password,
        password_confirm: this.passwordConfirm
      })

      await this.$router.push('/login')
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
