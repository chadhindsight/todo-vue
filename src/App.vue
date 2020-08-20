<template>
  <Todos v-bind:todos="todos" />
</template>

<script>
import Todos from "./components/Todos";

export default {
  name: "App",
  components: {
    Todos,
  },
  // A function that returns an object
  data() {
    return {
      todos: [
        {
          id: 2,
          title: "Make dinner",
          completed: false,
        },
        {
          id: 34,
          title: "Buy groceries",
          completed: false,
        },
        {
          id: 21,
          title: "Pay Cable bill",
          completed: false,
        },
      ],
    };
  },
};
</script>

<style>
</style>
