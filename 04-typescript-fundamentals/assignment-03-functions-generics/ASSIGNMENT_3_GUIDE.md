# Assignment 3: Functions & Generics - Reusable Type-Safe Code

**By Mahendra Bagul**

Generics let you write reusable code that works with any type while maintaining type safety. This is crucial for libraries and React! 🎯

---

## 📚 What You'll Learn

- ✅ Function type annotations
- ✅ Generic functions
- ✅ Generic interfaces
- ✅ Generic classes
- ✅ Generic constraints
- ✅ Multiple type parameters
- ✅ Default generic parameters
- ✅ Generic utility functions
- ✅ Practical use cases
- ✅ Building a type-safe data structures library

---

## 🎯 Assignment Objectives

Create a **Generic Data Structures Library** with Stack, Queue, and utility functions.

**Difficulty**: ⭐⭐⭐⭐☆  
**Time**: 6-7 hours  
**Prerequisites**: TypeScript Assignments 1-2 completed

---

## 📋 Requirements

### Must Have
1. ✅ Generic Stack class
2. ✅ Generic Queue class
3. ✅ Generic utility functions
4. ✅ Constrained generics
5. ✅ Multiple type parameters
6. ✅ Generic interfaces
7. ✅ Default type parameters
8. ✅ Interactive UI
9. ✅ Type safety demonstrated
10. ✅ Real-world examples

---

## 💻 Complete Implementation

### src/dataStructures.ts
```typescript
// ===== GENERIC STACK =====
class Stack<T> {
    private items: T[] = [];
    
    push(item: T): void {
        this.items.push(item);
    }
    
    pop(): T | undefined {
        return this.items.pop();
    }
    
    peek(): T | undefined {
        return this.items[this.items.length - 1];
    }
    
    isEmpty(): boolean {
        return this.items.length === 0;
    }
    
    size(): number {
        return this.items.length;
    }
    
    clear(): void {
        this.items = [];
    }
    
    toArray(): T[] {
        return [...this.items];
    }
}

// ===== GENERIC QUEUE =====
class Queue<T> {
    private items: T[] = [];
    
    enqueue(item: T): void {
        this.items.push(item);
    }
    
    dequeue(): T | undefined {
        return this.items.shift();
    }
    
    front(): T | undefined {
        return this.items[0];
    }
    
    isEmpty(): boolean {
        return this.items.length === 0;
    }
    
    size(): number {
        return this.items.length;
    }
    
    clear(): void {
        this.items = [];
    }
    
    toArray(): T[] {
        return [...this.items];
    }
}

// ===== GENERIC PAIR =====
class Pair<K, V> {
    constructor(public key: K, public value: V) {}
    
    toString(): string {
        return `{${this.key}: ${this.value}}`;
    }
}

// ===== GENERIC FUNCTIONS =====

// Simple generic function
function identity<T>(arg: T): T {
    return arg;
}

// Generic with array
function getFirst<T>(arr: T[]): T | undefined {
    return arr[0];
}

// Generic with multiple type parameters
function pair<K, V>(key: K, value: V): Pair<K, V> {
    return new Pair(key, value);
}

// Generic with constraints
interface HasLength {
    length: number;
}

function logLength<T extends HasLength>(arg: T): T {
    console.log(`Length: ${arg.length}`);
    return arg;
}

// Generic that returns a property
function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
    return obj[key];
}

// Generic filter function
function filter<T>(array: T[], predicate: (item: T) => boolean): T[] {
    return array.filter(predicate);
}

// Generic map function
function map<T, U>(array: T[], transform: (item: T) => U): U[] {
    return array.map(transform);
}

// Generic reduce function
function reduce<T, U>(
    array: T[],
    reducer: (acc: U, item: T) => U,
    initial: U
): U {
    return array.reduce(reducer, initial);
}

// ===== GENERIC INTERFACES =====

interface Repository<T> {
    getById(id: number): T | undefined;
    getAll(): T[];
    add(item: T): void;
    update(id: number, item: T): boolean;
    delete(id: number): boolean;
}

// ===== GENERIC REPOSITORY CLASS =====
class InMemoryRepository<T extends { id: number }> implements Repository<T> {
    private items: T[] = [];
    
    getById(id: number): T | undefined {
        return this.items.find(item => item.id === id);
    }
    
    getAll(): T[] {
        return [...this.items];
    }
    
    add(item: T): void {
        this.items.push(item);
    }
    
    update(id: number, updated: T): boolean {
        const index = this.items.findIndex(item => item.id === id);
        if (index === -1) return false;
        
        this.items[index] = updated;
        return true;
    }
    
    delete(id: number): boolean {
        const index = this.items.findIndex(item => item.id === id);
        if (index === -1) return false;
        
        this.items.splice(index, 1);
        return true;
    }
}

// Export everything
export {
    Stack,
    Queue,
    Pair,
    identity,
    getFirst,
    pair,
    logLength,
    getProperty,
    filter,
    map,
    reduce,
    InMemoryRepository,
    type Repository
};
```

### src/app.ts
```typescript
import {
    Stack,
    Queue,
    Pair,
    identity,
    getFirst,
    filter,
    map,
    InMemoryRepository
} from './dataStructures';

// ===== TYPE DEFINITIONS =====
interface Task {
    id: number;
    title: string;
    priority: number;
}

// ===== INSTANCES =====
const numberStack = new Stack<number>();
const stringQueue = new Queue<string>();
const taskRepo = new InMemoryRepository<Task>();

let nextTaskId = 1;

// ===== STACK OPERATIONS =====
(window as any).pushToStack = (): void => {
    const input = document.getElementById('stackInput') as HTMLInputElement;
    const value = parseInt(input.value);
    
    if (isNaN(value)) {
        showMessage("Enter a valid number!", "error");
        return;
    }
    
    numberStack.push(value);
    input.value = '';
    updateStackDisplay();
    showMessage(`Pushed ${value} to stack`, "success");
};

(window as any).popFromStack = (): void => {
    const value = numberStack.pop();
    
    if (value === undefined) {
        showMessage("Stack is empty!", "error");
        return;
    }
    
    updateStackDisplay();
    showMessage(`Popped ${value} from stack`, "success");
};

(window as any).peekStack = (): void => {
    const value = numberStack.peek();
    
    if (value === undefined) {
        showMessage("Stack is empty!", "error");
        return;
    }
    
    showMessage(`Top of stack: ${value}`, "info");
};

function updateStackDisplay(): void {
    const display = document.getElementById('stackDisplay') as HTMLDivElement;
    const items = numberStack.toArray();
    
    if (items.length === 0) {
        display.innerHTML = '<div class="empty">Stack is empty</div>';
        return;
    }
    
    display.innerHTML = items
        .reverse()
        .map(item => `<div class="stack-item">${item}</div>`)
        .join('');
}

// ===== QUEUE OPERATIONS =====
(window as any).enqueueToQueue = (): void => {
    const input = document.getElementById('queueInput') as HTMLInputElement;
    const value = input.value.trim();
    
    if (!value) {
        showMessage("Enter a value!", "error");
        return;
    }
    
    stringQueue.enqueue(value);
    input.value = '';
    updateQueueDisplay();
    showMessage(`Enqueued "${value}" to queue`, "success");
};

(window as any).dequeueFromQueue = (): void => {
    const value = stringQueue.dequeue();
    
    if (value === undefined) {
        showMessage("Queue is empty!", "error");
        return;
    }
    
    updateQueueDisplay();
    showMessage(`Dequeued "${value}" from queue`, "success");
};

function updateQueueDisplay(): void {
    const display = document.getElementById('queueDisplay') as HTMLDivElement;
    const items = stringQueue.toArray();
    
    if (items.length === 0) {
        display.innerHTML = '<div class="empty">Queue is empty</div>';
        return;
    }
    
    display.innerHTML = items
        .map(item => `<div class="queue-item">${item}</div>`)
        .join('');
}

// ===== GENERIC FUNCTIONS DEMO =====
(window as any).demoGenericFunctions = (): void => {
    const output = document.getElementById('genericOutput') as HTMLDivElement;
    
    // Identity function
    const num = identity(42);
    const str = identity("hello");
    
    // Get first
    const numbers = [1, 2, 3, 4, 5];
    const first = getFirst(numbers);
    
    // Filter
    const evens = filter(numbers, n => n % 2 === 0);
    
    // Map
    const doubled = map(numbers, n => n * 2);
    
    output.innerHTML = `
        <div class="demo-box">
            <h4>Identity Function</h4>
            <pre>const num = identity(42);       // number
const str = identity("hello");  // string

Type is preserved!
num → ${num} (${typeof num})
str → "${str}" (${typeof str})</pre>
            
            <h4>Array Functions</h4>
            <pre>const numbers = ${JSON.stringify(numbers)}

getFirst(numbers) → ${first}
filter(numbers, n => n % 2 === 0) → ${JSON.stringify(evens)}
map(numbers, n => n * 2) → ${JSON.stringify(doubled)}</pre>
        </div>
    `;
};

// ===== TASK REPOSITORY DEMO =====
(window as any).addTask = (): void => {
    const input = document.getElementById('taskInput') as HTMLInputElement;
    const priorityInput = document.getElementById('taskPriority') as HTMLInputElement;
    
    const title = input.value.trim();
    const priority = parseInt(priorityInput.value) || 1;
    
    if (!title) {
        showMessage("Enter a task title!", "error");
        return;
    }
    
    const task: Task = {
        id: nextTaskId++,
        title,
        priority
    };
    
    taskRepo.add(task);
    input.value = '';
    priorityInput.value = '1';
    updateTasksDisplay();
    showMessage("Task added!", "success");
};

(window as any).deleteTask = (id: number): void => {
    taskRepo.delete(id);
    updateTasksDisplay();
    showMessage("Task deleted!", "success");
};

function updateTasksDisplay(): void {
    const display = document.getElementById('tasksDisplay') as HTMLDivElement;
    const tasks = taskRepo.getAll();
    
    if (tasks.length === 0) {
        display.innerHTML = '<div class="empty">No tasks</div>';
        return;
    }
    
    display.innerHTML = tasks
        .sort((a, b) => b.priority - a.priority)
        .map(task => `
            <div class="task-item">
                <span class="task-title">${task.title}</span>
                <span class="task-priority">Priority: ${task.priority}</span>
                <button onclick="deleteTask(${task.id})" class="delete-btn">×</button>
            </div>
        `)
        .join('');
}

// ===== GENERICS EXPLANATION =====
(window as any).showGenericsExplanation = (): void => {
    const output = document.getElementById('explanationOutput') as HTMLDivElement;
    
    output.innerHTML = `
        <div class="explanation-box">
            <h3>What are Generics?</h3>
            <p>Generics let you write code that works with any type while maintaining type safety.</p>
            
            <h4>Without Generics (Bad)</h4>
            <pre>function getFirstAny(arr: any[]): any {
    return arr[0];  // Lost type information!
}

const num = getFirstAny([1, 2, 3]);  // num is 'any' 😢</pre>
            
            <h4>With Generics (Good)</h4>
            <pre>function getFirst<T>(arr: T[]): T {
    return arr[0];  // Type preserved!
}

const num = getFirst([1, 2, 3]);  // num is 'number' ✅
const str = getFirst(['a', 'b']);  // str is 'string' ✅</pre>
            
            <h4>Generic Classes</h4>
            <pre>class Stack<T> {
    private items: T[] = [];
    
    push(item: T): void {
        this.items.push(item);
    }
    
    pop(): T | undefined {
        return this.items.pop();
    }
}

const numberStack = new Stack<number>();
numberStack.push(42);  // ✅
// numberStack.push("hello");  // ❌ Error!

const stringStack = new Stack<string>();
stringStack.push("hello");  // ✅</pre>
            
            <h4>Constraints</h4>
            <pre>interface HasLength {
    length: number;
}

function logLength<T extends HasLength>(arg: T): T {
    console.log(arg.length);  // ✅ Safe!
    return arg;
}

logLength("hello");  // ✅ String has length
logLength([1, 2, 3]);  // ✅ Array has length
// logLength(123);  // ❌ Error! Number doesn't have length</pre>
        </div>
    `;
};

// ===== MESSAGE =====
function showMessage(message: string, type: "success" | "error" | "info"): void {
    const notification = document.createElement('div');
    notification.className = `notification ${type}`;
    notification.textContent = message;
    
    document.body.appendChild(notification);
    
    setTimeout(() => notification.classList.add('show'), 100);
    
    setTimeout(() => {
        notification.classList.remove('show');
        setTimeout(() => notification.remove(), 300);
    }, 3000);
}

console.log("✅ Generics demo loaded!");
```

### src/index.html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TypeScript Generics</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>🎯 TypeScript Generics</h1>
        
        <!-- Stack Demo -->
        <section class="demo-section">
            <h2>Generic Stack&lt;number&gt;</h2>
            <div class="controls">
                <input type="number" id="stackInput" placeholder="Enter number">
                <button onclick="pushToStack()">Push</button>
                <button onclick="popFromStack()">Pop</button>
                <button onclick="peekStack()">Peek</button>
            </div>
            <div id="stackDisplay" class="stack-display"></div>
        </section>
        
        <!-- Queue Demo -->
        <section class="demo-section">
            <h2>Generic Queue&lt;string&gt;</h2>
            <div class="controls">
                <input type="text" id="queueInput" placeholder="Enter string">
                <button onclick="enqueueToQueue()">Enqueue</button>
                <button onclick="dequeueFromQueue()">Dequeue</button>
            </div>
            <div id="queueDisplay" class="queue-display"></div>
        </section>
        
        <!-- Generic Functions -->
        <section class="demo-section">
            <h2>Generic Functions</h2>
            <button onclick="demoGenericFunctions()">Show Examples</button>
            <div id="genericOutput" class="output"></div>
        </section>
        
        <!-- Repository Pattern -->
        <section class="demo-section">
            <h2>Generic Repository&lt;Task&gt;</h2>
            <div class="controls">
                <input type="text" id="taskInput" placeholder="Task title">
                <input type="number" id="taskPriority" placeholder="Priority (1-5)" min="1" max="5" value="1">
                <button onclick="addTask()">Add Task</button>
            </div>
            <div id="tasksDisplay" class="tasks-display"></div>
        </section>
        
        <!-- Explanation -->
        <section class="demo-section">
            <h2>Understanding Generics</h2>
            <button onclick="showGenericsExplanation()">Show Explanation</button>
            <div id="explanationOutput" class="output"></div>
        </section>
    </div>
    
    <script type="module" src="../dist/app.js"></script>
</body>
</html>
```

---

## 📖 Key Concepts

### Generic Constraints
```typescript
// Only accept types with length property
function logLength<T extends { length: number }>(arg: T): T {
    console.log(arg.length);
    return arg;
}
```

### Multiple Type Parameters
```typescript
function pair<K, V>(key: K, value: V): [K, V] {
    return [key, value];
}

const p1 = pair("name", "John");  // [string, string]
const p2 = pair(1, true);          // [number, boolean]
```

---

## ✅ Self-Assessment

- [ ] Generic Stack implemented
- [ ] Generic Queue implemented
- [ ] Generic functions created
- [ ] Constraints used correctly
- [ ] Multiple type parameters
- [ ] Generic interfaces defined
- [ ] Repository pattern works
- [ ] UI interactive
- [ ] Type safety maintained
- [ ] Examples comprehensive

---

**Next**: [Assignment 4: Classes & OOP](../assignment-04-classes-oop/ASSIGNMENT_4_GUIDE.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

