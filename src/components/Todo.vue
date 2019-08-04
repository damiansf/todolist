<template>
  <div>
    <h2>{{todo.title}}</h2>
    <button v-on:click="deleteTodo(todo)">Delete</button>
    <button v-show="!todo.done" v-on:click="completeTodo(todo)">Complete</button>
    <button v-show="todo.done" v-on:click="restoreTodo(todo)">Restore</button>
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
