<template>
  <div id="app">
    <div class="container">
      <h1>To-do List Manager</h1>
      <AddTodo />
      <FilterTodos />
      <Todos />
      <h6 style="margin-top: 100px">
        Powered by: Vue 3 | Vuex 4 | Axios | Ruby on Rails 6 | SQLite 3
      </h6>
    </div>
  </div>
</template>

<script>
import Todos from "./components/Todos.vue";
import AddTodo from "./components/AddTodo.vue";
import FilterTodos from "./components/FilterTodos.vue";

export default {
  name: "App",
  components: {
    Todos,
    AddTodo,
    FilterTodos,
  },
};
</script>
