<template>
  <div id="app">
    <Header />
    <div class="container">
      <AddTodo v-bind:todos="todos" v-on:add-todo="addTodo" />

      <div v-if="todos.length > 0">
        <TodoList v-bind:todos="todos" v-on:del-todo="delTodo" />
      </div>
      <div v-else><NoList /></div>
    </div>
  </div>
</template>

<script>
import Header from "./components/layout/AppHeader.vue";
import TodoList from "./components/TodoList.vue";
import AddTodo from "./components/AddTodo.vue";
import NoList from "./components/NoList.vue";
export default {
  name: "App",
  components: {
    Header,
    TodoList,
    AddTodo,
    NoList,
  },
  methods: {
    delTodo(id) {
      console.log(id);
      this.todos = this.todos.filter((el) => {
        return el.id !== id;
      });
      localStorage.setItem("todo", JSON.stringify(this.todos));
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
      localStorage.setItem("todo", JSON.stringify(this.todos));
    },
  },
  data(){
return{
  todos:[]
}
  },
  mounted() {
    if (localStorage.getItem("todo") !== "undefined") {
      console.log("--------------------");
      this.todos=JSON.parse(localStorage.getItem("todo"));

    } else {
      console.log("............................");
      let todos = [];
      localStorage.setItem("todo", JSON.stringify(todos));
       this.todos=JSON.parse(localStorage.getItem("todo"));
    }
  },
  // computed(){
  //   alltodos=localStorage.getItem
  // },
  created() {
    console.log(this.todos);
  },
  watch: {
    todos() {
      console.log("watch me change");
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  background-color: #708582;
}
</style>
