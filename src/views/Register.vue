<template>
  <main class="form-signin">
    <form>
      <h1 class="h3 mb-3 fw-normal">サインインする</h1>
      <label class="visually-hidden">メールアドレス</label>
      <input type="email" class="form-control" placeholder="メールアドレス" required autofocus>
      <label class="visually-hidden">パスワード</label>
      <input type="password" class="form-control" placeholder="パスワード" required>
      <button class="w-100 btn btn-lg btn-primary" type="submit">サインイン</button>
    </form>
  </main>
</template>

<script>
export default {
  name: "Register"
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
