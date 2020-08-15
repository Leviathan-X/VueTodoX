<template>
  <div class="Todo">
    <h1>{{ msg }}</h1>
    <br />
    <TodoList v-bind:todosArray="hardcodedTodos"/>
    <CreateTodo v-bind:create-todo="createTodo"/>
    <br /><br />
  </div>
</template>

<script>
import TodoList from './TodoList.vue'
import CreateTodo from './CreateTodo.vue'

export default {
  name: 'Todo',
  props: {
    msg: String
  },
  components: {
    TodoList,
    CreateTodo
  }, 
  data: function () {
    return {
      hardcodedTodos: [{
       title: 'Todo A',
       project: 'Project A',
       done: false,
     }, {
       title: 'Todo B',
       project: 'Project B',
       done: true,
     }, {
       title: 'Todo C',
       project: 'Project C',
       done: false,
     }, {
       title: 'Todo D',
       project: 'Project D',
       done: false,
     }]
    }
  },
   methods: {
    createTodo (newTodo) {
      this.hardcodedTodos.push(newTodo);
    }
  } 
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
