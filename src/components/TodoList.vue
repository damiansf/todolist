<template>
  <div>
    <h2>In Progress</h2>
    <Todo v-on:delete-todo="deleteTodo($event)" v-on:complete-todo="toggleTodo($event, true)" v-for="todo in todos.filter(todo => {return todo.done === false})" :key="todo.id" v-bind:todo="todo"/>
    <h2>Completed</h2>
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
