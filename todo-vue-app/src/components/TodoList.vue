<template>
    <ul id="todos">
        <li v-for="todo in todosArray" :key="todo.title">
            <TodoItem v-bind:todoItem="todo" v-on:delete-todo="deleteTodo" v-on:edit-todo="sendEditedTodo"/>
        </li>
    </ul>
</template>

<script>
import TodoItem from './TodoItem.vue'

export default {
    name: 'TodoList',
    props: /*['todoArray'],*/ {
        todosArray: Array
        }, 
    components: {
        TodoItem
    }, 
    methods: {
        deleteTodo(todoItem) {
            const todoIndex = this.todosArray.indexOf(todoItem);
            this.todosArray.splice(todoIndex, 1);
        },
        sendEditedTodo(todoItem, editedTodo) {
            todoItem.title = editedTodo.title;
            todoItem.project = editedTodo.project;
            todoItem.done = editedTodo.done;
            this.$emit('send-edited-todo', todoItem);
        }
    }
}
</script>

<style scoped>
</style>