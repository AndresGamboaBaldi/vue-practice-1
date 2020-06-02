<template>
  <div>
    <span>Inventario Bibliotecario</span>
    <br />
    <label> Seleccione una Categoria: </label>
    <select v-model="selectedCategory">
      <option>Books</option>
      <option>Magazines</option>
      <option>Newspapers</option>
      <option>Others</option>
      <option>All</option>
    </select>
    <input v-model="selectedName" placeholder="Escriba el nombre a buscar" />
    <table id="table" style="table">
      <thead>
        <tr>
          <th>Code</th>
          <th>Name</th>
          <th>Description</th>
          <th>Category</th>
        </tr>
      </thead>
      <tbody>
        <tr :key="item.code" v-for="item in filteredList">
          <td>{{ item.code }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.description }}</td>
          <td>{{ item.category }}</td>
        </tr>
      </tbody>
    </table>
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
