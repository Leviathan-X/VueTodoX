<template>
    <ul id="todos">
        <li v-for="todo in listOfTodos" :key="todo.title">
            <TodoItem v-bind:todo="todo"/>
        </li>
    </ul>
</template>

<script>
import TodoItem from './TodoItem.vue'

export default {
    name: 'TodoList',
    props: /*['todos'],*/ {
        listOfTodos: Array
        }, 
    components: {
        TodoItem
    }
}
</script>

<style scoped>
</style>