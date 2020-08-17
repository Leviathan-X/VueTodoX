<template>
  <form>
      <input v-model="newTodo.title" placeholder="Todo title">
      <input v-model="newTodo.project" placeholder="Todo project">
      <button type="button" v-on:click="sendNewTodo">Submit</button>
  </form>
</template>

<script>
export default {
    data: function () {
        return {
            newTodo: {
                title: "",
                project: "",
                done: false
            }
        }
    }, 
    methods: {
        sendNewTodo: function() {
            this.$emit('create-todo', this.newTodo); // this.$emit('create-todo', {...this.newTodo}); - works, but not needed in this case    
            this.newTodo = { // This creates a new object reference in memory
                title: "",
                project: "",
                done: false
            }
        }
    }
}
</script>

<style>
</style>