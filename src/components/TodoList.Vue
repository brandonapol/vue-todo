<template>
    <div class="data">
        <form>
            <input v-model="newTodo" placeholder="Add a new todo item">
            <button v-on:click.prevent="addTodo(newTodo, todos)">Add</button>
        </form>
        <ul v-if="todos">
            <li v-for="todo in todos" :key="todo.id">
                <div class="left">
                    <span v-if="todo.completed"><i class="fas fa-check-circle check"></i></span>
                    <span v-if="!todo.completed"><i class="fas fa-times-circle cross"></i></span>
                    {{ todo.text }}
                </div>
                <div class="right">
                    <button @click="markTodoAsComplete(todo, todos)">Complete</button>
                    <button @click="deleteTodo(todo, todos)">Delete</button>
                </div>
            </li>
        </ul>
        <button v-if="todos.length" @click="completeAll(todos)">Mark All as Complete</button>
        <button v-if="todos.length" @click="deleteAll(todos)">Clear List</button>
    </div>
</template>
  
<script>
    const addTodo = (newTodo, todos) => {
        if (newTodo) {
            todos.push({
            id: todos.length + 1,
            text: newTodo,
            completed: false
            })
            newTodo = ''
        }
    }

    export default {
        data() {
        return {
            todos: [],
            newTodo: ''
        }
        },
        methods: {
            addTodo,
            markTodoAsComplete(todo, todos) {
                const todoIndex = todos.indexOf(todo)
                todos[todoIndex].completed = !todos[todoIndex].completed
            },
            deleteTodo(todo, todos) {
                const todoIndex = todos.indexOf(todo)
                todos.pop(todoIndex)
            },
            completeAll(todos) {
                let i = 0;
                while (i < todos.length) {
                    todos[i].completed = true;
                    i += 1
                }
            },
            deleteAll(todos) {
                let i = 0;
                while (i <= todos.length + 1) {
                    todos.pop()
                    i += 1
                }
            },
        }
    }
</script>

<style scoped>
.cross {
    color: red
}

.check {
    color: green
}

form {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}

ul {
    list-style-type: none
}

button {
    color: white;
    background-color: rgb(68, 82, 82);
    padding: 5px;
    margin: 3px;
    border-radius: 5px;
    border: none;
}

input {
    padding: 5px;
    margin: 3px;
    border-radius: 5px;
    border: none;
    width: 100%;
}

li {
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    padding: 5px;
    margin: 3px;
    /* margin-left: -40px; */
}

ul {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding-inline-start: 0px;
}

.left {
    width: 50%;
    display: flex;
    flex-direction: row;
    justify-content: start;
    align-items: center;
}

.right {
    width: 50%;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}

span {
    margin-right: 3px;
}

</style>