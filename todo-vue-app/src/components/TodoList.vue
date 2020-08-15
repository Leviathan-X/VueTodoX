<template>
    <ul id="todos">
        <li v-for="todo in todosArray" :key="todo.title">
            <TodoItem v-bind:todoItem="todo" v-on:delete-todo="deleteTodo"/>
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
        }
    }
}
</script>

<style scoped>
</style>