<template>
  <div>
      <fieldset v-if="editing === true">
        <form>
          <input autfocus v-model="title" v-bind:placeholder="todo.title">
          <input v-model="project" v-bind:placeholder="todo.project">
          <button v-on:click="editingInput()">Close X</button>
        </form>
      </fieldset>
      <fieldset v-else>
            <legend>{{ todo.title }}</legend>
            <p>{{ todo.project }}</p>
            <div v-if="todo.done === true">
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
        todo: Object
        },
    data: function () {
      return {
        editing : false
      }
    },
    methods: {
      editingInput: function () {
        if (this.editing === false) this.editing = true;
        else this.editing === false;
      }
    }
}
</script>

<style>

</style>