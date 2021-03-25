<template>
    <input v-model="inputValue">
    <button v-on:click="handleClick">ToDoを追加</button>
    
    <ul>
        <li 
            v-for="todo in todoItems" 
            v-bind:key="todo.id"
            v-on:click="todo.done = !todo.done">
            <span v-if="todo.done">✅</span>
            {{ todo.text }}
        </li>
    </ul>
</template>
<script>
export default {
    data() {
        return {
            inputValue: '',
            todoItems: [
                { id: 1, text: 'Go out to sea', done: false },
                { id: 2, text: 'Invite the first member', done: false },
            ],
        }
    },
    methods: {
        handleClick() {
            this.todoItems.push({
                id: this.todoItems.length + 1,
                text: this.inputValue
            })
            this.inputValue = ''
        }
    }
}
</script>