<template>
  <div>
    <h3>アカウント情報</h3>
    <form @submit.prevent="infoSubmit">
      <div class="mb-3">
        <v-text-field label="名" v-model="user.first_name"/>
      </div>
      <div class="mb-3">
        <v-textarea label="姓" v-model="user.last_name"/>
      </div>
      <div class="mb-3">
        <v-text-field label="メール" v-model="user.email"/>
      </div>
      <v-btn color="primary" type="submit">
        保存
      </v-btn>
    </form>

    <h3 class="mt-4">パスワード変更</h3>
    <form @submit.prevent="passwordSubmit">
      <div class="mb-3">
        <v-text-field label="パスワード" v-model="password"/>
      </div>
      <div class="mb-3">
        <v-textarea label="パスワード確認" v-model="password_confirm"/>
      </div>
      <v-btn color="primary" type="submit">
        保存
      </v-btn>
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Profile",
  data() {
    return {
      password: '',
      password_confirm: '',
    }
  },
  methods: {
    async infoSubmit() {
      const {data} = await axios.put('users/info', {
        first_name: this.user.first_name,
        last_name: this.user.last_name,
        email: this.user.email,
      })

      await this.$store.dispatch('setUser', data)
    },
    async passwordSubmit() {
      await axios.put('users/password', {
        password: this.password,
        password_confirm: this.password_confirm,
      })
    },
  },
  computed: {
    user() {
      return this.$store.state.user
    }
  }
}
</script>
