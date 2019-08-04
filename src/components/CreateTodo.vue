<template>
  <div>
    <input v-model="title" placeholder="Add Todo" v-on:keyup.enter="create" class="todo-input">
  </div>
</template>

<script>

export default {
  name: 'CreateTodo',
  data() {
    return {
      title: '',
    };
  },
  methods: {
    create() {
      let title = this.title;
      let id = this.$uuid.v1();
      if(this.title.length > 0) {
        this.$emit('create-todo', {
          title: title,
          done: false,
          id: id,
        })
        this.title = ''
      }
    }
  }
}
</script>

<style scoped>
.todo-input {
    border: none;
    border-bottom: 1px solid #000000;
    background: rgba(0, 0, 0, 0.003);
    position: relative;
    width: 40%;
    margin: 0;
    font-size: 24px;
    color: inherit;
    outline: none;
}
</style>
