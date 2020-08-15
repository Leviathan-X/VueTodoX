<template>
  <form>
      <input v-model="newTodo.title" placeholder="Todo title">
      <input v-model="newTodo.project" placeholder="Todo project">
      <button type="button" v-on:click="$emit('create-todo', newTodo)">Submit</button>
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
}
</script>

<style>
</style>