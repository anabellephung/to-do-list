<template>
  <div>
    <h3>To-do Items</h3>
    <div class="legend">
      <span>Double-click to mark as complete.</span>
      <div>
        <span
          style="margin-right: 20px; display: inline-flex; align-items: center"
        >
          <span class="incomplete-box"></span> = Incomplete
        </span>
        <span style="display: inline-flex; align-items: center">
          <span class="complete-box"></span> = Complete
        </span>
      </div>
    </div>
    <div class="todos">
      <div
        v-for="todo in allTodos"
        :key="todo.id"
        @dblclick="onDoubleClick(todo)"
        v-bind:class="{ 'is-complete': todo.completed }"
        class="todo"
      >
        {{ todo.title }}
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="24"
          height="24"
          viewBox="0 0 24 24"
          @click="deleteTodo(todo.id)"
          fill="#fff"
          class="trash-icon"
        >
          <path
            d="M3 6v18h18v-18h-18zm5 14c0 .552-.448 1-1 1s-1-.448-1-1v-10c0-.552.448-1 1-1s1 .448 1 1v10zm5 0c0 .552-.448 1-1 1s-1-.448-1-1v-10c0-.552.448-1 1-1s1 .448 1 1v10zm5 0c0 .552-.448 1-1 1s-1-.448-1-1v-10c0-.552.448-1 1-1s1 .448 1 1v10zm4-18v2h-20v-2h5.711c.9 0 1.631-1.099 1.631-2h5.315c0 .901.73 2 1.631 2h5.712z"
          />
        </svg>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";
export default {
  // Import our getters and actions
  name: "Todos",
  methods: {
    ...mapActions(["fetchTodos", "deleteTodo", "updateTodo"]),
    onDoubleClick(currentTodo) {
      const updatedTodo = {
        id: currentTodo.id,
        title: currentTodo.title,
        completed: !currentTodo.completed,
      };
      this.updateTodo(updatedTodo);
    },
  },
  computed: {
    ...mapGetters(["allTodos"]),
  },
  created() {
    this.fetchTodos();
  },
};
</script>

<style scoped>
.todos {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 1rem;
}
.todo {
  background: #911291;
  padding: 1rem;
  border-radius: 0.25rem;
  text-align: center;
  position: relative;
  cursor: pointer;
  box-shadow: 0 3px 10px rgba(0, 0, 0, 0.2);
}
.trash-icon {
  width: 15px;
  position: absolute;
  bottom: 2.5px;
  right: 5px;
  cursor: pointer;
}
.legend {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  margin-bottom: 1rem;
}
.complete-box {
  display: inline-block;
  width: 15px;
  height: 15px;
  margin-right: 5px;
  background: #91129187;
  border: 1px solid #fff;
  border-radius: 0.25rem;
}
.incomplete-box {
  display: inline-block;
  width: 15px;
  height: 15px;
  margin-right: 5px;
  background: #911291;
  border: 1px solid #fff;
  border-radius: 0.25rem;
}
.is-complete {
  background: #91129187;
  color: #fff;
}
@media (max-width: 500px) {
  .todos {
    grid-template-columns: 1fr;
  }
}
</style>
