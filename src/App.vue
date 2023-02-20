<template>
  <div id="app">
    <h1>TODO List</h1>
    <!-- <TodoList1 class="container"></TodoList1> -->
    <TodoList2 class="container"></TodoList2>
  </div>
</template>

<script>
// import TodoList1 from "@/views/TodoList1.vue";
import TodoList2 from "@/views/TodoList2.vue";

export default {
  name: "App",
  components: {
    // TodoList1,
    TodoList2,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto;
  width: 80%;
  min-width: 600px;
  box-sizing: border-box;
}
.container {
  margin-top: 100px;
}
ul,
li {
  list-style: none;
  margin: 0;
  padding: 0;
}
input,
button {
  vertical-align: middle;
  outline: 0 none;
}
</style>
