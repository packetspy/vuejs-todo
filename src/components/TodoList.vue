<template>
  <div>
    <sui-card class="card" v-for="todo in todoList" v-bind:key="todo.id">
      <sui-card-content>
        <sui-card-header>
          {{todo.title}}
        </sui-card-header>
      </sui-card-content>
      <sui-card-content>
      </sui-card-content>
    </sui-card>

    1 - {{todoList}}

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