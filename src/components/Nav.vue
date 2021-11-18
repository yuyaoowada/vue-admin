<template>
  <header class="navbar navbar-dark sticky-top bg-dark flex-md-nowrap p-0 shadow">
    <a class="navbar-brand col-md-3 col-lg-2 me-0 px-3" href="#">会社名</a>
    <nav class="my-2 my-md-0 mr-md-3">
      <router-link to="/profile" class="p-2 text--white text-decoration-none"> {{user.firstName}} {{user.lastName}}
      </router-link>
      <a href="#" class="p-2 text--white text-decoration-none" @click="logout">サインアウト</a>
    </nav>
  </header>
</template>

<script>
import axios from "axios";

export default {
  name: "Nav",
  props: ['user'],
  methods: {
    async logout(){
      await axios.post('logout')

      await this.$router.push('/login')
    }
  }
}
</script>
