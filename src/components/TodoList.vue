<template>
  <div class="theming-container ui container">
    <div class="ui huge header">Todo's</div>
    <div class="ui card centered">
      <div class="content">
        <div class="description">
          <div class="ui right action input"><input type="text" v-model="newTodo" placeholder="Some thing todo">
            <div class="ui teal button" v-on:click="addTodo"><i class="add icon"></i>
              Add
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="ui card centered" v-for="(todo, index) in todoList" v-bind:key="todo.id" v-bind:item="todo" v-bind:index="index">
      <div class="content">
        <div class="header">

          <h2 is="sui-header" icon text-align="left">
            <sui-header-content>{{todo.title}}</sui-header-content>
          </h2>

        </div>
        <div class="meta">2 days ago</div>
        <div class="description">{{todo.project}}</div>
      </div>
      <div class="ui bottom attached three buttons">
        <div role="button" class="ui button">
          <sui-icon name="edit" link />
        </div>
        <div role="button" class="ui button red" v-show="!todo.done">
          <sui-icon name="help" link />
        </div>
        <div role="button" class="ui button teal" v-show="todo.done">
          <sui-icon name="check" link />
        </div>
        <div role="button" class="ui button orange" v-on:click="removeTodo(todo)">
          <sui-icon name="trash" />
        </div>
      </div>
    </div>

    <a is="sui-label" color="teal">
      Completed: {{todoList.filter(todo => {return todo.done === true}).length}}
    </a>
    <a is="sui-label" color="red">
      Pending: {{todoList.filter(todo => {return todo.done === false}).length}}
    </a>

  </div>
</template>

<script>
export default {
  props: ["todoList"],
  data: function () {
    return { newTodo: "", isEditing: false };
  },
  methods: {
    showForm() {
      this.isEditing = true;
    },
    hideForm() {
      this.isEditing = false;
    },
    addTodo: function () {
      if (!this.newTodo.trim()) return;
      this.todoList.push({
        title: this.newTodo.trim(),
        project: this.newTodo.trim(),
        done: false,
      });
    },
    removeTodo: function (todo) {
      this.todoList.splice(this.todoList.indexOf(todo), 1);
      //this.$emit("remove-todo", todo);
    },
  },
};

// console.log(this.todos);
// console.log(this.initialTodos);
</script>

<style>
</style>