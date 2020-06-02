<template>
  <div>
    <span>Inventario Bibliotecario</span>
    <br />
    <select v-model="selectedCategory">
      <option>Books</option>
      <option>Magazines</option>
      <option>Newspapers</option>
      <option>Others</option>
      <option>All</option>
    </select>
    <br />
    <input v-model="selectedName" placeholder="Escriba el nombre" />
    <br />
    <div :key="item.code" v-for="item in filteredList">
      <span>{{ item.code }}</span>
      <span>{{ item.name }}</span>
      <span>{{ item.description }}</span>
      <span>{{ item.category }}</span>
      <br />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import * as data from "../data.json";
export default {
  name: "Home",
  components: {},
  data() {
    return {
      selectedName: "",
      selectedCategory: "All",
      filteredlist: "",
      list: data.obj
    };
  },
  computed: {
    filteredList() {
      const categoryList =
        this.selectedCategory === "All" || this.selectedCategory === ""
          ? this.list
          : this.list.filter(item => item.category === this.selectedCategory);
      return this.selectedName === ""
        ? categoryList
        : categoryList.filter(item =>
            item.name.toLowerCase().includes(this.selectedName.toLowerCase())
          );
    }
  }
};
</script>
