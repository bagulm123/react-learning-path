# Assignment 4: DOM Manipulation - Making Pages Interactive

**By Mahendra Bagul**

The DOM (Document Object Model) is how JavaScript talks to HTML. This is where things get REALLY interactive! 🎨

---

## 📚 What You'll Learn

- ✅ What is the DOM
- ✅ Selecting elements (getElementById, querySelector, querySelectorAll)
- ✅ Creating elements
- ✅ Modifying elements (textContent, innerHTML, style)
- ✅ Adding/removing classes
- ✅ Event listeners
- ✅ Event object and event types
- ✅ Form handling
- ✅ Local Storage
- ✅ Dynamic content rendering

---

## 🎯 Assignment Objectives

Create a **To-Do List App** with full CRUD operations, local storage persistence, and rich interactions.

**Difficulty**: ⭐⭐⭐☆☆  
**Time**: 5-6 hours  
**Prerequisites**: Assignments 1-3 completed

---

## 📋 Requirements

### Must Have
1. ✅ Add, edit, delete tasks
2. ✅ Mark tasks complete/incomplete
3. ✅ Filter tasks (all, active, completed)
4. ✅ Persist data in localStorage
5. ✅ Task counter
6. ✅ Clear completed tasks
7. ✅ Drag and drop (bonus)
8. ✅ Dynamic DOM manipulation
9. ✅ Event listeners
10. ✅ Responsive UI

---

## 🌐 DOM Basics

### What is the DOM?
The DOM is a tree-like representation of your HTML:
```
document
  └── html
      ├── head
      │   └── title
      └── body
          ├── h1
          ├── div
          │   ├── p
          │   └── button
          └── script
```

### Selecting Elements
```javascript
// By ID (returns element or null)
const element = document.getElementById('myId');

// By class (returns NodeList)
const elements = document.getElementsByClassName('myClass');

// By tag (returns NodeList)
const divs = document.getElementsByTagName('div');

// Query selector (returns first match)
const firstBtn = document.querySelector('.btn');

// Query selector all (returns NodeList)
const allBtns = document.querySelectorAll('.btn');
```

---

## 💻 Complete Implementation

### HTML (index.html)
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do List App</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>✅ My To-Do List</h1>
        
        <!-- Add Task Form -->
        <div class="add-task-section">
            <input 
                type="text" 
                id="taskInput" 
                placeholder="What needs to be done?"
                class="task-input"
            >
            <button id="addBtn" class="btn btn-add">Add Task</button>
        </div>
        
        <!-- Filters -->
        <div class="filters">
            <button class="filter-btn active" data-filter="all">
                All (<span id="allCount">0</span>)
            </button>
            <button class="filter-btn" data-filter="active">
                Active (<span id="activeCount">0</span>)
            </button>
            <button class="filter-btn" data-filter="completed">
                Completed (<span id="completedCount">0</span>)
            </button>
        </div>
        
        <!-- Tasks List -->
        <div id="tasksList" class="tasks-list"></div>
        
        <!-- Actions -->
        <div class="actions">
            <button id="clearCompletedBtn" class="btn btn-danger">
                Clear Completed
            </button>
            <button id="clearAllBtn" class="btn btn-danger">
                Clear All
            </button>
        </div>
        
        <!-- DOM Demo Section -->
        <div class="demo-section">
            <h2>DOM Manipulation Demo</h2>
            <button onclick="demoDOM()">Show DOM Methods</button>
            <div id="demoOutput"></div>
        </div>
    </div>
    
    <script src="script.js"></script>
</body>
</html>
```

### JavaScript (script.js)
```javascript
// ===== STATE =====
let tasks = [];
let currentFilter = 'all';
let nextId = 1;

// ===== DOM ELEMENTS =====
const taskInput = document.getElementById('taskInput');
const addBtn = document.getElementById('addBtn');
const tasksList = document.getElementById('tasksList');
const filterBtns = document.querySelectorAll('.filter-btn');
const clearCompletedBtn = document.getElementById('clearCompletedBtn');
const clearAllBtn = document.getElementById('clearAllBtn');

// ===== INITIALIZE =====
function init() {
    loadFromLocalStorage();
    renderTasks();
    updateCounts();
    
    // Event listeners
    addBtn.addEventListener('click', addTask);
    taskInput.addEventListener('keypress', (e) => {
        if (e.key === 'Enter') addTask();
    });
    
    filterBtns.forEach(btn => {
        btn.addEventListener('click', (e) => {
            currentFilter = e.target.dataset.filter;
            
            // Update active button
            filterBtns.forEach(b => b.classList.remove('active'));
            e.target.classList.add('active');
            
            renderTasks();
        });
    });
    
    clearCompletedBtn.addEventListener('click', clearCompleted);
    clearAllBtn.addEventListener('click', clearAll);
    
    console.log('✅ To-Do App initialized!');
}

// ===== ADD TASK =====
function addTask() {
    const text = taskInput.value.trim();
    
    if (!text) {
        alert('Please enter a task!');
        return;
    }
    
    const task = {
        id: nextId++,
        text: text,
        completed: false,
        createdAt: new Date().toISOString()
    };
    
    tasks.push(task);
    taskInput.value = '';
    
    saveToLocalStorage();
    renderTasks();
    updateCounts();
    
    console.log('Added task:', task);
}

// ===== RENDER TASKS =====
function renderTasks() {
    // Filter tasks
    let filteredTasks = tasks;
    
    if (currentFilter === 'active') {
        filteredTasks = tasks.filter(t => !t.completed);
    } else if (currentFilter === 'completed') {
        filteredTasks = tasks.filter(t => t.completed);
    }
    
    // Clear container
    tasksList.innerHTML = '';
    
    if (filteredTasks.length === 0) {
        const emptyMsg = document.createElement('p');
        emptyMsg.className = 'empty-message';
        emptyMsg.textContent = 'No tasks yet. Add one above! 🎯';
        tasksList.appendChild(emptyMsg);
        return;
    }
    
    // Render each task
    filteredTasks.forEach(task => {
        const taskElement = createTaskElement(task);
        tasksList.appendChild(taskElement);
    });
}

// ===== CREATE TASK ELEMENT =====
function createTaskElement(task) {
    // Create container
    const div = document.createElement('div');
    div.className = 'task-item';
    if (task.completed) {
        div.classList.add('completed');
    }
    div.dataset.id = task.id;
    
    // Checkbox
    const checkbox = document.createElement('input');
    checkbox.type = 'checkbox';
    checkbox.checked = task.completed;
    checkbox.className = 'task-checkbox';
    checkbox.addEventListener('change', () => toggleTask(task.id));
    
    // Text
    const text = document.createElement('span');
    text.className = 'task-text';
    text.textContent = task.text;
    text.addEventListener('dblclick', () => editTask(task.id));
    
    // Edit input (hidden)
    const editInput = document.createElement('input');
    editInput.type = 'text';
    editInput.className = 'task-edit-input';
    editInput.value = task.text;
    editInput.style.display = 'none';
    editInput.addEventListener('blur', () => saveEdit(task.id, editInput));
    editInput.addEventListener('keypress', (e) => {
        if (e.key === 'Enter') editInput.blur();
    });
    
    // Delete button
    const deleteBtn = document.createElement('button');
    deleteBtn.className = 'delete-btn';
    deleteBtn.textContent = '×';
    deleteBtn.addEventListener('click', () => deleteTask(task.id));
    
    // Assemble
    div.appendChild(checkbox);
    div.appendChild(text);
    div.appendChild(editInput);
    div.appendChild(deleteBtn);
    
    return div;
}

// ===== TOGGLE TASK =====
function toggleTask(id) {
    const task = tasks.find(t => t.id === id);
    if (task) {
        task.completed = !task.completed;
        saveToLocalStorage();
        renderTasks();
        updateCounts();
    }
}

// ===== EDIT TASK =====
function editTask(id) {
    const taskElement = document.querySelector(`[data-id="${id}"]`);
    const text = taskElement.querySelector('.task-text');
    const input = taskElement.querySelector('.task-edit-input');
    
    text.style.display = 'none';
    input.style.display = 'block';
    input.focus();
    input.select();
}

// ===== SAVE EDIT =====
function saveEdit(id, input) {
    const newText = input.value.trim();
    
    if (!newText) {
        renderTasks();
        return;
    }
    
    const task = tasks.find(t => t.id === id);
    if (task) {
        task.text = newText;
        saveToLocalStorage();
        renderTasks();
    }
}

// ===== DELETE TASK =====
function deleteTask(id) {
    tasks = tasks.filter(t => t.id !== id);
    saveToLocalStorage();
    renderTasks();
    updateCounts();
}

// ===== CLEAR COMPLETED =====
function clearCompleted() {
    if (confirm('Clear all completed tasks?')) {
        tasks = tasks.filter(t => !t.completed);
        saveToLocalStorage();
        renderTasks();
        updateCounts();
    }
}

// ===== CLEAR ALL =====
function clearAll() {
    if (confirm('Clear ALL tasks?')) {
        tasks = [];
        saveToLocalStorage();
        renderTasks();
        updateCounts();
    }
}

// ===== UPDATE COUNTS =====
function updateCounts() {
    const all = tasks.length;
    const active = tasks.filter(t => !t.completed).length;
    const completed = tasks.filter(t => t.completed).length;
    
    document.getElementById('allCount').textContent = all;
    document.getElementById('activeCount').textContent = active;
    document.getElementById('completedCount').textContent = completed;
}

// ===== LOCAL STORAGE =====
function saveToLocalStorage() {
    localStorage.setItem('tasks', JSON.stringify(tasks));
    localStorage.setItem('nextId', nextId.toString());
}

function loadFromLocalStorage() {
    const saved = localStorage.getItem('tasks');
    if (saved) {
        tasks = JSON.parse(saved);
    }
    
    const savedId = localStorage.getItem('nextId');
    if (savedId) {
        nextId = parseInt(savedId);
    }
}

// ===== DOM DEMO =====
function demoDOM() {
    const output = document.getElementById('demoOutput');
    
    // Clear previous content
    output.innerHTML = '';
    
    // Create demo section
    const demoDiv = document.createElement('div');
    demoDiv.className = 'dom-demo';
    
    // Add heading
    const heading = document.createElement('h3');
    heading.textContent = 'DOM Manipulation Examples';
    heading.style.color = '#667eea';
    demoDiv.appendChild(heading);
    
    // Example 1: Creating elements
    const example1 = document.createElement('div');
    example1.className = 'example-box';
    example1.innerHTML = `
        <h4>1. Creating Elements</h4>
        <pre>const div = document.createElement('div');
div.className = 'my-class';
div.textContent = 'Hello!';
document.body.appendChild(div);</pre>
    `;
    demoDiv.appendChild(example1);
    
    // Example 2: Selecting elements
    const example2 = document.createElement('div');
    example2.className = 'example-box';
    example2.innerHTML = `
        <h4>2. Selecting Elements</h4>
        <pre>// By ID
const el = document.getElementById('myId');

// By class (querySelector)
const el = document.querySelector('.myClass');

// All elements
const els = document.querySelectorAll('.myClass');</pre>
    `;
    demoDiv.appendChild(example2);
    
    // Example 3: Modifying elements
    const example3 = document.createElement('div');
    example3.className = 'example-box';
    example3.innerHTML = `
        <h4>3. Modifying Elements</h4>
        <pre>// Change text
el.textContent = 'New text';

// Change HTML
el.innerHTML = '&lt;strong&gt;Bold&lt;/strong&gt;';

// Change style
el.style.color = 'red';
el.style.fontSize = '20px';

// Add class
el.classList.add('active');

// Remove class
el.classList.remove('inactive');

// Toggle class
el.classList.toggle('active');</pre>
    `;
    demoDiv.appendChild(example3);
    
    // Example 4: Event listeners
    const example4 = document.createElement('div');
    example4.className = 'example-box';
    example4.innerHTML = `
        <h4>4. Event Listeners</h4>
        <pre>// Click event
btn.addEventListener('click', () => {
    console.log('Clicked!');
});

// Input event
input.addEventListener('input', (e) => {
    console.log(e.target.value);
});

// Form submit
form.addEventListener('submit', (e) => {
    e.preventDefault();
    // Handle form
});</pre>
    `;
    demoDiv.appendChild(example4);
    
    // Example 5: LocalStorage
    const example5 = document.createElement('div');
    example5.className = 'example-box';
    example5.innerHTML = `
        <h4>5. LocalStorage</h4>
        <pre>// Save
localStorage.setItem('key', 'value');

// Save object
localStorage.setItem('user', JSON.stringify(obj));

// Get
const value = localStorage.getItem('key');

// Get object
const obj = JSON.parse(localStorage.getItem('user'));

// Remove
localStorage.removeItem('key');

// Clear all
localStorage.clear();</pre>
    `;
    demoDiv.appendChild(example5);
    
    // Add interactive button
    const interactiveBtn = document.createElement('button');
    interactiveBtn.textContent = 'Click Me! (Interactive Demo)';
    interactiveBtn.className = 'btn btn-add';
    interactiveBtn.style.marginTop = '1rem';
    interactiveBtn.addEventListener('click', () => {
        interactiveBtn.textContent = 'You clicked me! 🎉';
        interactiveBtn.style.background = '#28a745';
        setTimeout(() => {
            interactiveBtn.textContent = 'Click Me Again!';
            interactiveBtn.style.background = '';
        }, 2000);
    });
    demoDiv.appendChild(interactiveBtn);
    
    output.appendChild(demoDiv);
}

// ===== START APP =====
init();
```

### CSS (styles.css)
```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    padding: 2rem;
    min-height: 100vh;
}

.container {
    max-width: 700px;
    margin: 0 auto;
}

h1 {
    color: white;
    text-align: center;
    margin-bottom: 2rem;
    font-size: 2.5rem;
}

.add-task-section {
    display: flex;
    gap: 1rem;
    margin-bottom: 1.5rem;
}

.task-input {
    flex: 1;
    padding: 1rem;
    border: none;
    border-radius: 10px;
    font-size: 1rem;
    box-shadow: 0 5px 15px rgba(0,0,0,0.1);
}

.btn {
    padding: 1rem 2rem;
    border: none;
    border-radius: 10px;
    font-size: 1rem;
    cursor: pointer;
    transition: all 0.3s;
    font-weight: 600;
}

.btn-add {
    background-color: #28a745;
    color: white;
}

.btn-add:hover {
    background-color: #218838;
    transform: translateY(-2px);
}

.btn-danger {
    background-color: #dc3545;
    color: white;
}

.btn-danger:hover {
    background-color: #c82333;
}

.filters {
    display: flex;
    gap: 0.5rem;
    margin-bottom: 1.5rem;
}

.filter-btn {
    flex: 1;
    background: white;
    color: #667eea;
    padding: 0.75rem;
    border: 2px solid #667eea;
    border-radius: 10px;
    cursor: pointer;
    transition: all 0.3s;
    font-weight: 600;
}

.filter-btn:hover {
    background: #667eea;
    color: white;
}

.filter-btn.active {
    background: #667eea;
    color: white;
}

.tasks-list {
    background: white;
    border-radius: 15px;
    padding: 1.5rem;
    min-height: 200px;
    margin-bottom: 1.5rem;
    box-shadow: 0 10px 30px rgba(0,0,0,0.2);
}

.task-item {
    display: flex;
    align-items: center;
    gap: 1rem;
    padding: 1rem;
    border-bottom: 1px solid #eee;
    transition: all 0.3s;
}

.task-item:hover {
    background: #f8f9fa;
}

.task-item.completed {
    opacity: 0.6;
}

.task-checkbox {
    width: 20px;
    height: 20px;
    cursor: pointer;
}

.task-text {
    flex: 1;
    font-size: 1rem;
    color: #2c3e50;
}

.task-item.completed .task-text {
    text-decoration: line-through;
}

.task-edit-input {
    flex: 1;
    padding: 0.5rem;
    border: 2px solid #667eea;
    border-radius: 5px;
    font-size: 1rem;
}

.delete-btn {
    background: #dc3545;
    color: white;
    border: none;
    width: 30px;
    height: 30px;
    border-radius: 50%;
    cursor: pointer;
    font-size: 1.5rem;
    line-height: 1;
    transition: all 0.3s;
}

.delete-btn:hover {
    background: #c82333;
    transform: scale(1.1);
}

.empty-message {
    text-align: center;
    color: #999;
    padding: 2rem;
    font-size: 1.1rem;
}

.actions {
    display: flex;
    gap: 1rem;
}

.demo-section {
    background: white;
    padding: 2rem;
    border-radius: 15px;
    margin-top: 2rem;
    box-shadow: 0 10px 30px rgba(0,0,0,0.2);
}

.demo-section h2 {
    color: #2c3e50;
    margin-bottom: 1rem;
}

.dom-demo {
    margin-top: 1rem;
}

.example-box {
    background: #f8f9fa;
    padding: 1.5rem;
    border-radius: 10px;
    margin-bottom: 1rem;
    border: 2px solid #e9ecef;
}

.example-box h4 {
    color: #667eea;
    margin-bottom: 0.75rem;
}

.example-box pre {
    background: #2c3e50;
    color: #fff;
    padding: 1rem;
    border-radius: 5px;
    overflow-x: auto;
    font-size: 0.9rem;
}

@media (max-width: 768px) {
    .add-task-section {
        flex-direction: column;
    }
    
    .filters {
        flex-direction: column;
    }
    
    .actions {
        flex-direction: column;
    }
}
```

---

## 📖 Key Concepts

### Event Object
```javascript
element.addEventListener('click', (event) => {
    event.preventDefault();  // Prevent default behavior
    event.stopPropagation(); // Stop event bubbling
    
    console.log(event.target);      // Element that triggered event
    console.log(event.type);        // 'click'
    console.log(event.clientX);     // Mouse X position
});
```

### LocalStorage
```javascript
// Save string
localStorage.setItem('name', 'John');

// Save object
const user = {name: 'John', age: 25};
localStorage.setItem('user', JSON.stringify(user));

// Get
const name = localStorage.getItem('name');
const user = JSON.parse(localStorage.getItem('user'));

// Remove
localStorage.removeItem('name');

// Clear all
localStorage.clear();
```

---

## ✅ Self-Assessment

- [ ] Can add tasks
- [ ] Can edit tasks (double-click)
- [ ] Can delete tasks
- [ ] Can toggle completion
- [ ] Filters work (all, active, completed)
- [ ] LocalStorage persistence works
- [ ] Clear completed works
- [ ] Counters update correctly
- [ ] DOM demo shows examples
- [ ] UI is responsive

---

**Next**: [Assignment 5: Event Handling](../assignment-05-event-handling/ASSIGNMENT_5_GUIDE.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

