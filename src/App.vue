<template>
  <Header />
  <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  <AddTodo v-on:add-todo="addTodo" />
</template>

<script>
import axios from "axios";
import Todos from "./components/Todos";
import Header from "./components/layouts/Header";
import AddTodo from "./components/AddTodo.vue";

export default {
  name: "App",
  components: {
    Todos,
    Header,
    AddTodo,
  },
  // A function that returns an object
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    async deleteTodo(id) {
      try {
        await axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`);
        this.todos = this.todos.filter((todo) => todo.id !== id);
      } catch (err) {
        console.log(err);
      }
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
    },
  },
  // works similar to componentDidMount
  async created() {
    try {
      let res = await axios.get(
        "https://jsonplaceholder.typicode.com/todos?_limit=7"
      );
      this.todos = res.data;
      console.log(res.data);
    } catch (err) {
      console.log(err);
    }
  },
};
</script>

<style>
</style>
