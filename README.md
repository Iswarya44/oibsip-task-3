<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do Web App</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <h1>To-Do List</h1>
    <div id="app">
        <input type="text" id="newTask" placeholder="Add a new task...">
        <button onclick="addTask()">Add Task</button>
        <div id="pendingTasks">
            <h2>Pending Tasks</h2>
            <ul id="pendingList"></ul>
        </div>
        <div id="completedTasks">
            <h2>Completed Tasks</h2>
            <ul id="completedList"></ul>
        </div>
    </div>
    <script src="script.js"></script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    text-align: center;
}

h1, h2 {
    color: #333;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    margin: 5px 0;
    display: flex;
    justify-content: space-between;
}

button {
    margin-top: 10px;
}
function addTask() {
    const taskInput = document.getElementById('newTask');
    const taskText = taskInput.value.trim();
    if (taskText !== '') {
        const listItem = document.createElement('li');
        listItem.innerHTML = `
            ${taskText} 
            <button onclick="completeTask(this)">Complete</button>
            <button onclick="deleteTask(this)">Delete</button>
        `;
        document.getElementById('pendingList').appendChild(listItem);
        taskInput.value = '';
    }
}

function completeTask(button) {
    const listItem = button.parentElement;
    document.getElementById('completedList').appendChild(listItem);
    button.parentNode.removeChild(button);
}

function deleteTask(button) {
    const listItem = button.parentElement;
    listItem.parentNode.removeChild(listItem);
}
