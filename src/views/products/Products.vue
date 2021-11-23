<template>
  <div>
    <div class="pt-3 pb-2 mb-3 border-bottom">
      <v-btn href="/products/create" variant="contained" color="primary">追加</v-btn>
    </div>
    <v-simple-table>
      <template v-slot:default>
        <thead>
        <tr>
          <th class="text-left">#</th>
          <th class="text-left">画像</th>
          <th class="text-left">タイトル</th>
          <th class="text-left">説明</th>
          <th class="text-left">価格</th>
          <th class="text-left">操作</th>
        </tr>
        </thead>
        <tbody>
        <tr
            v-for="product in products.slice((page -1) * perPage, page * perPage)"
            :key="product.id"
        >
          <td>{{ product.id }}</td>
          <td>
            <v-img :src="product.image" max-height="80" max-width="120"/>
          </td>
          <td>{{ product.title }}</td>
          <td>{{ product.description }}</td>
          <td>{{ product.price }}</td>
          <td>
            <v-btn-toggle>
            <v-btn color="primary" :href="`/products/${product.id}/edit`">編集</v-btn>
            <v-btn color="error" @click="del(product.id)">削除</v-btn>
            </v-btn-toggle>
          </td>
        </tr>
        </tbody>
      </template>
    </v-simple-table>
    <div class="text-center">
      <v-pagination
          v-model="page"
          total-visible="7"
          :length="lastPage"
      ></v-pagination>
    </div>
  </div>
</template>

<script lang="ts">
import axios from "axios";
import Vue from 'vue';

export default Vue.extend({
  name: "Products",
  data() {
    return {
      products: [],
      page: 1,
      perPage: 10,
      lastPage: 0,
    }
  },
  async mounted() {
    const {data} = await axios.get('products')

    this.products = data
    this.lastPage = Math.ceil(data.length / this.perPage)
  },
  methods: {
    async del(id: number) {
      if(confirm('削除してよろしいですか？')) {
        await axios.delete(`products/${id}`)

        this.products = this.products.filter((p: any) => p.id !== id)
      }
    }
  }
})
</script>
