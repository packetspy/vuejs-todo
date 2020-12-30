<template>
  <div>
    <sui-card class="card centered" v-for="todo in todoList" v-bind:key="todo.id">
      <sui-card-content>
        <sui-card-header>
          {{todo.title}}
        </sui-card-header>
      </sui-card-content>
      <sui-card-content>
        <p>{{todo.project}}</p>
      </sui-card-content>
      <sui-card-content extra>
        <sui-button>Done</sui-button>
      </sui-card-content>
    </sui-card>
  </div>
</template>

<script>
export default {
  props: ["todoList"],
};

// console.log(this.todos);
// console.log(this.initialTodos);
</script>

<style>
</style>