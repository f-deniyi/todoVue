<template>
  <div>
    <div v-bind:key="todo.id" v-for="todo in todos">
      <TodoItem v-bind:todo="todo" v-on:del-todo='deleteTodo'  />
    </div>
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";
export default {
  name: "TodoList",
  props: {
    todos: Array,
  },
  components: {
    TodoItem,
  },
  methods:{
    deleteTodo(id){
      this.$emit('del-todo',id)
    }
  }
 
};
</script>
<style scoped>
.todo-item {
  background-color: rgb(255, 223, 205);
  border-bottom: black solid 2px;
}
.mark-todo {
  margin-left: 0.5em;
}
</style>