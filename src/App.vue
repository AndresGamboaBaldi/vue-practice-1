<template>
  <div id="app">
    <div id="app-header"></div>
    <router-view />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
table {
  margin: 0 auto;
  width: 100%;
  border: 1px solid black;
}
td {
  margin: 0 auto;
  border: 1px solid black;
}
th {
  background-color: seashell;
  height: 50px;
}
span {
  font-size: 71px;
  color: gold;
}
label {
  font-size: 30px;
  color: navy;
}
tr:nth-child(even) {
  background-color: #f2f2f2;
}
</style>
