## Name: Praveena M
## Reg NO: 212223040153

## Ex03 To-Do List using JavaScript
## Date:
## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM
STEP 1
Build the HTML structure (index.html).

STEP 2
Style the App (style.css).

STEP 3
Plan the features the To-Do App should have.

STEP 4
Create a To-do application using Javascript.

STEP 5
Add functionalities.

STEP 6
Test the App.

STEP 7
Open the HTML file in a browser to check layout and functionality.

STEP 8
Fix styling issues and refine content placement.

STEP 9
Deploy the website.

STEP 10
Upload to GitHub Pages for free hosting.

## PROGRAM
## HTML
```

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Todo App</title>
  <link rel="stylesheet" href="todo.css"> <!-- Linking todo.css -->
</head>
<body>

<h1>To-do App</h1>

<input id="todo-input" placeholder="Add a new todo...">
<button id="add-btn">Add</button>

<ul id="todo-list"></ul>

<button id="clear-completed-btn">Clear Completed</button>

<script src="todo.js"></script> <!-- Linking todo.js -->
</body>
</html>



```
## STYLE.CSS
```
body {
    display: flex;
    flex-direction: column; /* <-- Stack vertically */
    align-items: center; /* Center horizontally */
    justify-content: flex-start; /* Start from top */
    min-height: 100vh;
    background: linear-gradient(to right, #72e084, #c68ce1);
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 20px;
  }
  
  h1 {
    margin-bottom: 20px;
  }
  
  #todo-input {
    padding: 10px;
    border-radius: 8px;
    border: 1px solid #ccc;
    margin-bottom: 10px;
    width: 300px;
  }
  
  #add-btn {
    padding: 10px 20px;
    margin-bottom: 20px;
    background-color: green;
    color: white;
    border: none;
    border-radius: 8px;
    cursor: pointer;
  }
  
  #add-btn:hover {
    background-color: darkgreen;
  }
  
  #todo-list {
    list-style: none;
    padding: 0;
    width: 320px;
    margin-bottom: 20px;
  }
  
  #todo-list li {
    background: white;
    margin-bottom: 10px;
    padding: 10px;
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  
  #clear-completed-btn {
    padding: 10px 20px;
    background-color: crimson;
    color: white;
    border: none;
    border-radius: 8px;
    cursor: pointer;
  }
  
  #clear-completed-btn:hover {
    background-color: darkred;
  }
  




```

## Js
```
const todoInput = document.getElementById('todo-input');
const addBtn = document.getElementById('add-btn');
const todoList = document.getElementById('todo-list');
const clearCompletedBtn = document.getElementById('clear-completed-btn');

let todos = JSON.parse(localStorage.getItem('todos')) || [];

function saveTodos() {
  localStorage.setItem('todos', JSON.stringify(todos));
}

function renderTodos() {
  todoList.innerHTML = '';
  todos.forEach((todo, index) => {
    const li = document.createElement('li');
    li.className = `todo-item ${todo.completed ? 'completed' : ''}`;

    const span = document.createElement('span');
    span.textContent = todo.text;

    const actions = document.createElement('div');
    actions.className = 'actions';

    const completeBtn = document.createElement('button');
    completeBtn.innerHTML = todo.completed ? '✅' : '☑️';
    completeBtn.addEventListener('click', () => toggleComplete(index));

    const editBtn = document.createElement('button');
    editBtn.innerHTML = '✏️';
    editBtn.addEventListener('click', () => editTodo(index));

    const deleteBtn = document.createElement('button');
    deleteBtn.innerHTML = '🗑️';
    deleteBtn.addEventListener('click', () => deleteTodo(index));

    actions.appendChild(completeBtn);
    actions.appendChild(editBtn);
    actions.appendChild(deleteBtn);

    li.appendChild(span);
    li.appendChild(actions);

    todoList.appendChild(li);
  });
}

function addTodo() {
  const text = todoInput.value.trim();
  if (text !== '') {
    todos.push({ text, completed: false });
    saveTodos();
    renderTodos();
    todoInput.value = '';
  }
}

function toggleComplete(index) {
  todos[index].completed = !todos[index].completed;
  saveTodos();
  renderTodos();
}

function editTodo(index) {
  const newText = prompt('Edit your todo:', todos[index].text);
  if (newText !== null && newText.trim() !== '') {
    todos[index].text = newText.trim();
    saveTodos();
    renderTodos();
  }
}

function deleteTodo(index) {
  todos.splice(index, 1);
  saveTodos();
  renderTodos();
}

function clearCompleted() {
  todos = todos.filter(todo => !todo.completed);
  saveTodos();
  renderTodos();
}

addBtn.addEventListener('click', addTodo);
clearCompletedBtn.addEventListener('click', clearCompleted);

todoInput.addEventListener('keypress', function(event) {
  if (event.key === 'Enter') {
    addTodo();
  }
});

renderTodos();







```
## OUTPUT
![image](https://github.com/user-attachments/assets/d21dcc8e-4ea9-4e84-925a-143db11ee8e3)



## RESULT
The program for creating To-do list using JavaScript is executed successfully.
