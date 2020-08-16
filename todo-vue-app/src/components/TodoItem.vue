<template>
  <div>
      <fieldset v-if="editing === true">
        <form>
          <legend>{{ todoItem.title }}</legend>
          <input autfocus v-model="editedTodo.title" v-bind:placeholder="todoItem.title">
          <input v-model="editedTodo.project" v-bind:placeholder="todoItem.project">
          <br />
          <button type="button" v-on:click="$emit('edit-todo', todoItem, editedTodo), editingMode()">Edit</button>
          <br />
          <button v-on:click="editingMode()">Cancel</button>
        </form>
      </fieldset>
      <fieldset v-else>
            <legend>{{ todoItem.title }}</legend>
            <p>{{ todoItem.project }}</p>
            <div v-if="todoItem.done === true">
                <button type="button" v-on:click="editDone(), $emit('edit-todo', todoItem, editedTodo)">Completed</button>
            </div>
            <div v-else>
                <button type="button" v-on:click="editDone(), $emit('edit-todo', todoItem, editedTodo)">Pending</button>
            </div>
            <button v-on:click="editingMode()">Edit</button>
            <button v-on:click="$emit('delete-todo', todoItem)">Delete</button>
      </fieldset>
    <br /><br />
  </div>
</template>

<script>
export default {
    name: 'TodoItem',
    props: {
        todoItem: Object
        },
    data: function () {
      return {
        editing : false,
        editedTodo: { ...this.todoItem }
      }
    },
    methods: {
      editingMode: function () {
        if (this.editing === false) this.editing = true;
        else this.editing = false;
      },
      editDone() {
        if (this.editedTodo.done === true) this.editedTodo.done = false;
        else this.editedTodo.done = true;
      }
    }
}
</script>

<style>
</style>