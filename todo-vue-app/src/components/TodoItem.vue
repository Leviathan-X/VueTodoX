<template>
  <div>
      <fieldset v-if="editing === true">
        <form>
          <input autfocus v-bind:placeholder="todoItem.title">
          <input v-bind:placeholder="todoItem.project">
          <br />
          <button v-on:click="editingInput()">Close X</button>
        </form>
      </fieldset>
      <fieldset v-else>
            <legend>{{ todoItem.title }}</legend>
            <p>{{ todoItem.project }}</p>
            <div v-if="todoItem.done === true">
                <button>Completed</button>
            </div>
            <div v-else>
                <button>Complete</button>
            </div>
            <button v-on:click="editingInput()">Edit</button>
            <button>Delete</button>
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
      editingInput: function () {
        if (this.editing === false) this.editing = true;
        else this.editing = false;
      }
    }
}
</script>

<style>

</style>