<template>
  <div>
    <form @submit="addTodo">
      <input placeholder="Add Todo..." v-model="title" name="title" />
      <button type="submit">Add</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      title: "",
    };
  },
  props: {
    todos: Array,
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      if (this.title === "") {
        return {};
      } else {
        const id = this.todos.length;
        const newTodo = {
          id,
          title: this.title,
          completed: false,
        };
        this.$emit("add-todo", newTodo);
        this.title = "";
      }
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
  width: 100%;
}
form input {
  width: 80%;
  padding: 0.7em;
}
form button {
  width: 20%;
}
</style>