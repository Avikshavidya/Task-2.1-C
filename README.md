# Task-2.1-C
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Todo App</title>
    <style>
        /* Add your CSS styles here */
        /* Example styles */
        .todo-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 8px;
            border: 1px solid #ccc;
            margin: 8px 0;
        }
        .completed {
            text-decoration: line-through;
        }
    </style>
</head>
<body>
    <div id="app">
        <h1>Todo App</h1>
        <div>
            <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Add a new task">
            <button @click="addTodo">Add</button>
        </div>
        <div>
            <div v-for="(todo, index) in todos" :key="index" class="todo-item" :class="{ 'completed': todo.completed }">
                {{ todo.text }}
                <button @click="deleteTodo(index)">Delete</button>
                <button @click="toggleComplete(index)">{{ todo.completed ? 'Mark Incomplete' : 'Mark Complete' }}</button>
            </div>
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/vue@3.2.11/dist/vue.esm-browser.js"></script>
    <script>
        const app = Vue.createApp({
            data() {
                return {
                    newTodo: '',
                    todos: []
                };
            },
            methods: {
                addTodo() {
                    if (this.newTodo.trim() !== '') {
                        this.todos.push({ text: this.newTodo, completed: false });
                        this.newTodo = '';
                    }
                },
                deleteTodo(index) {
                    this.todos.splice(index, 1);
                },
                toggleComplete(index) {
                    this.todos[index].completed = !this.todos[index].completed;
                }
            }
        });

        app.mount('#app');
    </script>
</body>
</html>
