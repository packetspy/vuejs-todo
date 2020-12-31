<template>
  <div class="container">
    <p>Completed Tasks: {{todoList.filter(todo => {return todo.done === true}).length}}</p>
    <p>Pending Tasks: {{todoList.filter(todo => {return todo.done === false}).length}}</p>

    <div class="ui card">
      <div class="content">
        <div class="header">
          Abbreviated Header
        </div>

      </div>
      <div class="ui bottom attached two buttons">
        <div role="button" class="ui button teal">
          Action 1
        </div>
        <div role="button" class="ui button">
          Action 2
        </div>
      </div>
    </div>

    <sui-card class="centered" v-for="todo in todoList" v-bind:key="todo.id">
      <sui-card-content>
        <sui-card-header>
          {{todo.title}}
        </sui-card-header>
        <sui-card-meta>2 days ago</sui-card-meta>
      </sui-card-content>
      <sui-card-content>
        <p>{{todo.project}}</p>
      </sui-card-content>
      <sui-card-content extra v-show="todo.done">
        <span class="teal">
          <sui-icon name="edit" /> Edit
        </span>
        <span slot="right" class="teal">
          <sui-icon name="check" /> Completed
        </span>
      </sui-card-content>

      <sui-button attached="bottom" v-show="!todo.done">
        <sui-icon name="check" /> Complete
      </sui-button>
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