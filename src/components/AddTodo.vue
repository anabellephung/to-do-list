<template>
  <div>
    <h3>Add To-do Item</h3>
    <div class="add">
      <form @submit="onSubmit">
        <input type="text" v-model="title" placeholder="Add To-do item..." />
        <input type="submit" value="Submit" />
      </form>
    </div>
  </div>
</template>

<script>
import { mapActions } from "vuex";
export default {
  name: "AddTodo",
  data() {
    return {
      title: "",
    };
  },
  methods: {
    ...mapActions(["addTodo"]),
    onSubmit(e) {
      e.preventDefault();
      this.addTodo(this.title);
      this.title = "";
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
}
input[type="text"] {
  flex: 10;
  padding: 10px;
  border: 1px solid #fff;
  box-shadow: 0 3px 10px rgba(0, 0, 0, 0.2);
  outline: 0;
}
input[type="text"]:hover,
input[type="text"]:focus {
  border: 1px solid #911291;
}
input[type="submit"] {
  flex: 2;
  background: #911291;
  color: #fff;
  border: 1px solid #911291;
  cursor: pointer;
  transition: background 0.2s ease-in-out;
}
input[type="submit"]:hover,
input[type="submit"]:focus {
  background: #750e75;
}
</style>
