<template>
  <v-simple-table>
    <template v-slot:default>
      <thead>
      <tr>
        <th class="text-left">#</th>
        <th class="text-left">コード</th>
        <th class="text-left">カウント</th>
        <th class="text-left">収益</th>
      </tr>
      </thead>
      <tbody>
      <tr
          v-for="link in links"
          :key="link.id"
      >
        <td>{{ link.id }}</td>
        <td>{{ link.code }} {{ link }}</td>
        <td>{{ link.orders.length }}</td>
        <td>{{link.orders.reduce((s, o) => s + o.total, 0)}}</td>
      </tr>
      </tbody>
    </template>
  </v-simple-table>
</template>

<script>
import axios from "axios";

export default {
  name: "Links",
  data() {
    return {
      links:[],
    }
  },
  async mounted() {
    const {data} = await axios.get(`users/${this.$route.params.id}/links`)

    this.links = data
  }
}
</script>
