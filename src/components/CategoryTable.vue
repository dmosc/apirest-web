<template>
  <table>
    <thead>
    <tr>
      <th colspan="2">Categorías</th>
    </tr>
    </thead>
    <tbody>
    <tr v-for="category in categories" :key="category.id_category">
      <td>{{ category.id_category }}</td>
      <td>{{ category.name }}</td>
    </tr>
    </tbody>
  </table>
</template>

<script>
import {backendClient} from "@/services/backend";

export default {
  name: "CategoryTable",
  data() {
    return {
      categories: []
    };
  },
  async created() {
    const {data} = await backendClient.get("/categories");
    console.log(data);
    this.categories = data;
  }
}
</script>

<style scoped>
td {
  border: 1px solid #bbb;
}

tr {
  width: 200%;
  padding: 2px 10px;
}

thead {
  background-color: #333;
  color: #fff;
}

table {
  width: 100%;
}
</style>