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
            <input id="newTodoInput" placeholder="Add a new task">
            <button onclick="addTodo()">Add</button>
        </div>
        <div id="todoList"></div>
    </div>

    <script>
        const todos = [];

        function renderTodos() {
            const todoList = document.getElementById("todoList");
            todoList.innerHTML = "";

            todos.forEach((todo, index) => {
                const todoItem = document.createElement("div");
                todoItem.classList.add("todo-item");
                if (todo.completed) {
                    todoItem.classList.add("completed");
                }

                const textElement = document.createElement("span");
                textElement.textContent = todo.text;

                const deleteButton = document.createElement("button");
                deleteButton.textContent = "Delete";
                deleteButton.onclick = () => deleteTodo(index);

                const toggleButton = document.createElement("button");
                toggleButton.textContent = todo.completed ? "Mark Incomplete" : "Mark Complete";
                toggleButton.onclick = () => toggleComplete(index);

                todoItem.appendChild(textElement);
                todoItem.appendChild(deleteButton);
                todoItem.appendChild(toggleButton);

                todoList.appendChild(todoItem);
            });
        }

        function addTodo() {
            const newTodoInput = document.getElementById("newTodoInput");
            const newTodoText = newTodoInput.value.trim();
            if (newTodoText !== '') {
                todos.push({ text: newTodoText, completed: false });
                newTodoInput.value = '';
                renderTodos();
            }
        }

        function deleteTodo(index) {
            todos.splice(index, 1);
            renderTodos();
        }

        function toggleComplete(index) {
            todos[index].completed = !todos[index].completed;
            renderTodos();
        }

        renderTodos();
    </script>
</body>
</html>
