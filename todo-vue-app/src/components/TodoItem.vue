<template>
  <div>
      <fieldset v-if="editing === true">
        <form>
          <legend>{{ todoItem.title }}</legend>
          <input autfocus v-model="todoItem.title" v-bind:placeholder="todoItem.title">
          <input v-model="todoItem.project" v-bind:placeholder="todoItem.project">
          <br />
          <button v-on:click="$emit('edit-todo', this.todoItem)">Edit</button>
          <!--<button v-on:click="editTodo()">Edit</button>-->
          <br />
          <button v-on:click="editingMode()">Cancel</button>
        </form>
      </fieldset>
      <fieldset v-else>
            <legend>{{ todoItem.title }}</legend>
            <p>{{ todoItem.project }}</p>
            <div v-if="todoItem.done === true">
                <button>Completed</button>
            </div>
            <div v-else>
                <button>Pending</button>
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
        editing : false
      }
    },
    methods: {
      editingMode: function () {
        if (this.editing === false) this.editing = true;
        else this.editing = false;
      }
    }
}
</script>

<style>

</style>