<template>
  <div>
    <h1>In Progress</h1>
    <Todo v-on:delete-todo="deleteTodo($event)" v-on:complete-todo="toggleTodo($event, true)" v-for="todo in todos.filter(todo => {return todo.done === false})" :key="todo.id" v-bind:todo="todo"/>
    <h1>Completed</h1>
    <Todo v-on:delete-todo="deleteTodo($event)" v-on:restore-todo="toggleTodo($event, false)" v-for="todo in todos.filter(todo => {return todo.done === true})" :key="todo.id" v-bind:todo="todo"/>
  </div>
</template>

<script>

import Todo from './Todo.vue'

export default {
  name: 'TodoList',
  components: {
   Todo,
  },
  props: ['todos'],
  methods: {
    deleteTodo(todo) {
      let todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    },
    toggleTodo(todo, state) {
      let todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].done = state;
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
