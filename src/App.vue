<template>
  <div id="app">
    <TodoList :todoList=initialTodos />
  </div>
</template>

<script>
import TodoList from "./components/TodoList";

export default {
  name: "App",
  components: {
    TodoList,
  },
  data() {
    return {
      initialTodos: [
        { title: "Todo A", project: "Project A", done: false },
        { title: "Todo B", project: "Project B", done: true },
        { title: "Todo C", project: "Project C", done: false },
      ],
    };
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
  margin-top: 60px;
}
</style>
