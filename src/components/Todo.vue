<template>
  <div>
    <span>{{todo.title}}</span>
    <img src="../assets/checkmark.png" v-show="!todo.done" v-on:click="completeTodo(todo)">
    <img src="../assets/restore.png" v-show="todo.done" v-on:click="restoreTodo(todo)">
    <img src="../assets/trashcan.png" v-on:click="deleteTodo(todo)">
  </div>
</template>

<script>
export default {
  name: 'Todo',
  props: ['todo'],
  methods: {
    deleteTodo(todo) {
      this.$emit('delete-todo', todo)
    },
    completeTodo(todo) {
      this.$emit('complete-todo', todo)
    },
    restoreTodo(todo) {
      this.$emit('restore-todo', todo)
    }
  }
}
</script>

<style scoped>
img {
  width: 20px;
  height: 20px;
  cursor: pointer;
}
span {
  padding-right: 10px;
  font-size: 20px;
}
</style>
