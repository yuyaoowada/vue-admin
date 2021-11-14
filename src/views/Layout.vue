<template>
  <v-app>
    <Nav/>
    <div class="container-fluid">
      <div class="row">
        <Menu/>

        <main class="col-md-9 ms-sm-auto col-lg-10 px-md-4">
          <div class="table-responsive">
            <table class="table table-striped table-sm">
              <thead>
              <tr>
                <th>#</th>
                <th>Header</th>
                <th>Header</th>
                <th>Header</th>
                <th>Header</th>
              </tr>
              </thead>
              <tbody>
              <tr>
                <td>1,001</td>
                <td>Lorem</td>
                <td>ipsum</td>
                <td>dolor</td>
                <td>sit</td>
              </tr>
              </tbody>
            </table>
          </div>
        </main>
      </div>
    </div>
  </v-app>
</template>

<script>
import Nav from "@/components/Nav.vue";
import Menu from "@/components/Menu.vue";
export default {
  name: "Layout",
  components: {Menu, Nav},
}
</script>

<style scoped>

</style>
