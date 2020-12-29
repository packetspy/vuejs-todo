<template>
  <div class="container">
    <div class="columns is-centered">
      <div class="column is-half">
        <h1>Todo's</h1>
      </div>
    </div>
    <div class="columns is-centered">
      <div class="column is-half">
        <div class="field is-grouped">
          <p class="control is-expanded">
            <input type="text" class="input is-hovered" placeholder="The job most important todo" v-model="newTodoText" v-on:keyup.enter="addTodo()" />
          </p>
          <p class="control">
            <a href="" v-on:click="addTodo()" onclick="return false;" title="Add a new item" class="button is-primary">+</a>
          </p>
        </div>
      </div>
    </div>
    <div class="columns is-centered">
      <div class="column is-half">
        <ul tag="ul" name="list-animation">
          <li v-for="todo in todoItems" v-bind:key="todo.id" class="todo-item todo-item-animated">
            <label class="checkbox todo-check">
              <input type="checkbox" v-model="todo.isDone" v-on:click="move(todo.id)" />
              <span class="checkmark"></span>
            </label>

            <span class="todo-text" v-bind:class="{ completed: todo.isDone }">{{
              todo.Text
            }}</span>
            <a href="" v-on:click="removeTodo(todo)" onclick="return false;" title="Remove this item">x</a>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
let itemIndex = 0

function GetFreeItemIndex() {
  itemIndex++
  return itemIndex
}

let todoData = [
  { Id: GetFreeItemIndex(), Text: "Important Task", isDone: false },
  { Id: GetFreeItemIndex(), Text: "Study VueJs", isDone: false },
  { Id: GetFreeItemIndex(), Text: "English Motherfucker, you need", isDone: false }
]

export default {
  name: "Todo",
  data: function () {
    return { todoItems: todoData, newTodoText: "" }
  },

  methods: {
    addTodo: function () {
      if (this.newTodoText.trim() === "" || this.newTodoText === null || !this.newTodoText) return

      this.todoItems.push({ Text: this.newTodoText, isDone: false })
      this.newTodoText = ""
    },
    removeTodo: function (todo) {
      this.todoItems.splice(this.todoItems.indexOf(todo), 1)
    },
    moveTodo: function (todo) {
      console.log(todo)
      return
    }
  }
}

//Todo ... meia boca
// https://medium.com/better-programming/how-to-build-your-first-vue-js-application-469ed1ec4fde
// https://github.com/FrancescoBonizzi/VueJs-Experiments/blob/master/Todo%20list%20application/app.js

// instant search
// https://medium.com/better-programming/instant-search-with-vue-js-and-axios-5b78a3a59f01
</script>

<style>
</style>