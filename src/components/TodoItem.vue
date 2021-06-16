<template>
  <div>
    <div class="todo-item">
      <h2 v-bind:class="{ completed: todo.completed }">
        <span class="mark-todo"
          ><Input v-on:change="markTodo" type="checkbox"
        /></span>
        {{ todo.title }}
      </h2>
      <p class="del-btn" @click="$emit('del-todo', todo.id)">X</p>
    </div>
  </div>
</template>
<script>
export default {
  name: "TodoItem",
  props: {
    todo: Object,
  },
  methods: {
    markTodo() {
      this.todo.completed = !this.todo.completed;
    },
    delTodo(id){
        console.log(id);
    }
  },
};
</script>
<style scoped>
.completed {
  text-decoration: line-through;
}
.todo-item {
  background-color: rgb(255, 223, 205);
  border-bottom: black solid 2px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.2em;
}
.mark-todo {
  margin-left: 0.5em;
}
.date {
  color: rgba(110, 110, 110, 0.308);
  margin: 0.1em 0 0.3em 2em;
}
.del-btn {
  color: white;
  background-color: red;
  width: 24px;
  height: 24px;
  border-radius: 50%;
  padding: 0.6em 0.8em;
  margin-right: 0.9em;
  font-size: 10px;
}
</style>