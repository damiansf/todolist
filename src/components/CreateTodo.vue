<template>
  <div>
    <input v-model="title" placeholder="Add Todo" v-on:keyup.enter="create">
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
