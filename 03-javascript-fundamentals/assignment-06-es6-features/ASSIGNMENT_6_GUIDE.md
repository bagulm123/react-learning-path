# Assignment 6: ES6+ Features - Modern JavaScript

**By Mahendra Bagul**

ES6 (ECMAScript 2015) revolutionized JavaScript! These modern features make code cleaner, shorter, and more powerful. This is what you'll use in React! 🚀

---

## 📚 What You'll Learn

- ✅ Let & const
- ✅ Arrow functions
- ✅ Template literals
- ✅ Destructuring (arrays & objects)
- ✅ Spread & rest operators
- ✅ Default parameters
- ✅ Classes
- ✅ Modules (import/export)
- ✅ Promises & async/await
- ✅ Array methods (map, filter, reduce, find, some, every)

---

## 🎯 Assignment Objectives

Create a **Modern JavaScript Features Showcase** with interactive examples of all ES6+ features.

**Difficulty**: ⭐⭐⭐⭐☆  
**Time**: 6-7 hours  
**Prerequisites**: Assignments 1-5 completed

---

## 📋 Requirements

### Must Have
1. ✅ Destructuring examples
2. ✅ Spread/rest operator demos
3. ✅ Arrow function examples
4. ✅ Template literals showcase
5. ✅ Array methods (map, filter, reduce)
6. ✅ Classes demonstration
7. ✅ Promises example
8. ✅ Async/await demo
9. ✅ Module pattern
10. ✅ Interactive UI

---

## 💻 Complete Implementation

### HTML (index.html)
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ES6+ Features</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>🚀 Modern JavaScript (ES6+)</h1>
        
        <!-- Destructuring -->
        <section class="demo-section">
            <h2>1. Destructuring</h2>
            <button onclick="demoDestructuring()">Show Examples</button>
            <div id="destructuringOutput" class="output"></div>
        </section>
        
        <!-- Spread/Rest -->
        <section class="demo-section">
            <h2>2. Spread & Rest Operators</h2>
            <button onclick="demoSpreadRest()">Show Examples</button>
            <div id="spreadRestOutput" class="output"></div>
        </section>
        
        <!-- Arrow Functions -->
        <section class="demo-section">
            <h2>3. Arrow Functions</h2>
            <button onclick="demoArrowFunctions()">Show Examples</button>
            <div id="arrowOutput" class="output"></div>
        </section>
        
        <!-- Array Methods -->
        <section class="demo-section">
            <h2>4. Modern Array Methods</h2>
            <div class="array-demo">
                <input type="text" id="numberInput" placeholder="Enter numbers (comma separated)">
                <div class="button-group">
                    <button onclick="testMap()">Map (×2)</button>
                    <button onclick="testFilter()">Filter (>5)</button>
                    <button onclick="testReduce()">Reduce (sum)</button>
                    <button onclick="testFind()">Find (>10)</button>
                </div>
            </div>
            <div id="arrayOutput" class="output"></div>
        </section>
        
        <!-- Classes -->
        <section class="demo-section">
            <h2>5. Classes</h2>
            <button onclick="demoClasses()">Show Examples</button>
            <div id="classOutput" class="output"></div>
        </section>
        
        <!-- Promises -->
        <section class="demo-section">
            <h2>6. Promises</h2>
            <button onclick="demoPromises()">Run Promise</button>
            <div id="promiseOutput" class="output"></div>
        </section>
        
        <!-- Async/Await -->
        <section class="demo-section">
            <h2>7. Async/Await</h2>
            <button onclick="demoAsyncAwait()">Fetch Data</button>
            <div id="asyncOutput" class="output"></div>
        </section>
        
        <!-- Template Literals -->
        <section class="demo-section">
            <h2>8. Template Literals</h2>
            <div class="template-demo">
                <input type="text" id="nameInput" placeholder="Name">
                <input type="number" id="ageInput" placeholder="Age">
                <button onclick="generateTemplate()">Generate</button>
            </div>
            <div id="templateOutput" class="output"></div>
        </section>
    </div>
    
    <script type="module" src="script.js"></script>
</body>
</html>
```

### JavaScript (script.js)
```javascript
// ===== 1. DESTRUCTURING =====
window.demoDestructuring = function() {
    const output = document.getElementById('destructuringOutput');
    
    // Array destructuring
    const colors = ['red', 'green', 'blue', 'yellow', 'purple'];
    const [first, second, ...rest] = colors;
    
    // Object destructuring
    const user = {
        name: 'John Doe',
        age: 30,
        email: 'john@example.com',
        city: 'Mumbai',
        country: 'India'
    };
    const { name, age, email, ...address } = user;
    
    // Nested destructuring
    const data = {
        id: 1,
        info: {
            title: 'Developer',
            skills: ['JavaScript', 'React', 'Node.js']
        }
    };
    const { info: { title, skills } } = data;
    
    output.innerHTML = `
        <div class="example-box">
            <h4>Array Destructuring</h4>
            <pre>const colors = ${JSON.stringify(colors, null, 2)}
const [first, second, ...rest] = colors;

first  → "${first}"
second → "${second}"
rest   → ${JSON.stringify(rest)}</pre>
        </div>
        
        <div class="example-box">
            <h4>Object Destructuring</h4>
            <pre>const user = ${JSON.stringify(user, null, 2)}
const { name, age, email, ...address } = user;

name    → "${name}"
age     → ${age}
email   → "${email}"
address → ${JSON.stringify(address, null, 2)}</pre>
        </div>
        
        <div class="example-box">
            <h4>Nested Destructuring</h4>
            <pre>const data = ${JSON.stringify(data, null, 2)}
const { info: { title, skills } } = data;

title  → "${title}"
skills → ${JSON.stringify(skills)}</pre>
        </div>
    `;
};

// ===== 2. SPREAD & REST =====
window.demoSpreadRest = function() {
    const output = document.getElementById('spreadRestOutput');
    
    // Spread with arrays
    const arr1 = [1, 2, 3];
    const arr2 = [4, 5, 6];
    const combined = [...arr1, ...arr2];
    
    // Spread with objects
    const obj1 = { a: 1, b: 2 };
    const obj2 = { c: 3, d: 4 };
    const merged = { ...obj1, ...obj2 };
    
    // Rest in function
    const sum = (...numbers) => numbers.reduce((a, b) => a + b, 0);
    
    // Copy arrays/objects
    const original = [1, 2, 3];
    const copy = [...original];
    copy.push(4);
    
    output.innerHTML = `
        <div class="example-box">
            <h4>Spread - Combine Arrays</h4>
            <pre>const arr1 = ${JSON.stringify(arr1)}
const arr2 = ${JSON.stringify(arr2)}
const combined = [...arr1, ...arr2]

Result → ${JSON.stringify(combined)}</pre>
        </div>
        
        <div class="example-box">
            <h4>Spread - Merge Objects</h4>
            <pre>const obj1 = ${JSON.stringify(obj1)}
const obj2 = ${JSON.stringify(obj2)}
const merged = { ...obj1, ...obj2 }

Result → ${JSON.stringify(merged)}</pre>
        </div>
        
        <div class="example-box">
            <h4>Rest - Function Parameters</h4>
            <pre>const sum = (...numbers) => 
    numbers.reduce((a, b) => a + b, 0);

sum(1, 2, 3, 4, 5) → ${sum(1, 2, 3, 4, 5)}</pre>
        </div>
        
        <div class="example-box">
            <h4>Spread - Copy Array</h4>
            <pre>const original = ${JSON.stringify([1, 2, 3])}
const copy = [...original]
copy.push(4)

original → ${JSON.stringify(original)}
copy     → ${JSON.stringify(copy)}</pre>
        </div>
    `;
};

// ===== 3. ARROW FUNCTIONS =====
window.demoArrowFunctions = function() {
    const output = document.getElementById('arrowOutput');
    
    // Various arrow function syntaxes
    const add = (a, b) => a + b;
    const square = x => x * x;
    const greet = () => 'Hello!';
    const multiLine = (name, age) => {
        const message = `${name} is ${age} years old`;
        return message.toUpperCase();
    };
    
    output.innerHTML = `
        <div class="example-box">
            <h4>Multiple Parameters</h4>
            <pre>const add = (a, b) => a + b;
add(5, 3) → ${add(5, 3)}</pre>
        </div>
        
        <div class="example-box">
            <h4>Single Parameter</h4>
            <pre>const square = x => x * x;
square(7) → ${square(7)}</pre>
        </div>
        
        <div class="example-box">
            <h4>No Parameters</h4>
            <pre>const greet = () => 'Hello!';
greet() → "${greet()}"</pre>
        </div>
        
        <div class="example-box">
            <h4>Multi-line</h4>
            <pre>const multiLine = (name, age) => {
    const message = \`\${name} is \${age} years old\`;
    return message.toUpperCase();
};
multiLine('Alice', 25) → "${multiLine('Alice', 25)}"</pre>
        </div>
    `;
};

// ===== 4. ARRAY METHODS =====
function getNumbers() {
    const input = document.getElementById('numberInput').value;
    return input.split(',').map(n => parseInt(n.trim())).filter(n => !isNaN(n));
}

window.testMap = function() {
    const numbers = getNumbers();
    if (numbers.length === 0) {
        alert('Enter some numbers first!');
        return;
    }
    
    const doubled = numbers.map(n => n * 2);
    
    document.getElementById('arrayOutput').innerHTML = `
        <div class="result-box">
            <h4>Map - Transform Each Element</h4>
            <pre>Original: ${JSON.stringify(numbers)}
numbers.map(n => n * 2)
Result: ${JSON.stringify(doubled)}</pre>
        </div>
    `;
};

window.testFilter = function() {
    const numbers = getNumbers();
    if (numbers.length === 0) {
        alert('Enter some numbers first!');
        return;
    }
    
    const filtered = numbers.filter(n => n > 5);
    
    document.getElementById('arrayOutput').innerHTML = `
        <div class="result-box">
            <h4>Filter - Keep Matching Elements</h4>
            <pre>Original: ${JSON.stringify(numbers)}
numbers.filter(n => n > 5)
Result: ${JSON.stringify(filtered)}</pre>
        </div>
    `;
};

window.testReduce = function() {
    const numbers = getNumbers();
    if (numbers.length === 0) {
        alert('Enter some numbers first!');
        return;
    }
    
    const sum = numbers.reduce((acc, n) => acc + n, 0);
    
    document.getElementById('arrayOutput').innerHTML = `
        <div class="result-box">
            <h4>Reduce - Calculate Sum</h4>
            <pre>Original: ${JSON.stringify(numbers)}
numbers.reduce((acc, n) => acc + n, 0)
Result: ${sum}</pre>
        </div>
    `;
};

window.testFind = function() {
    const numbers = getNumbers();
    if (numbers.length === 0) {
        alert('Enter some numbers first!');
        return;
    }
    
    const found = numbers.find(n => n > 10);
    
    document.getElementById('arrayOutput').innerHTML = `
        <div class="result-box">
            <h4>Find - First Match</h4>
            <pre>Original: ${JSON.stringify(numbers)}
numbers.find(n => n > 10)
Result: ${found !== undefined ? found : 'Not found'}</pre>
        </div>
    `;
};

// ===== 5. CLASSES =====
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
    
    greet() {
        return `Hello, I'm ${this.name} and I'm ${this.age} years old.`;
    }
    
    haveBirthday() {
        this.age++;
        return `Happy birthday! Now ${this.age} years old.`;
    }
}

class Developer extends Person {
    constructor(name, age, language) {
        super(name, age);
        this.language = language;
    }
    
    code() {
        return `${this.name} is coding in ${this.language}!`;
    }
}

window.demoClasses = function() {
    const output = document.getElementById('classOutput');
    
    const person = new Person('Alice', 25);
    const dev = new Developer('Bob', 30, 'JavaScript');
    
    output.innerHTML = `
        <div class="example-box">
            <h4>Basic Class</h4>
            <pre>class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
    
    greet() {
        return \`Hello, I'm \${this.name}\`;
    }
}

const person = new Person('Alice', 25);
person.greet() → "${person.greet()}"</pre>
        </div>
        
        <div class="example-box">
            <h4>Inheritance</h4>
            <pre>class Developer extends Person {
    constructor(name, age, language) {
        super(name, age);
        this.language = language;
    }
    
    code() {
        return \`\${this.name} codes in \${this.language}\`;
    }
}

const dev = new Developer('Bob', 30, 'JavaScript');
dev.greet() → "${dev.greet()}"
dev.code()  → "${dev.code()}"</pre>
        </div>
    `;
};

// ===== 6. PROMISES =====
function fakeAPICall() {
    return new Promise((resolve, reject) => {
        const success = Math.random() > 0.3;
        
        setTimeout(() => {
            if (success) {
                resolve({ message: 'Data loaded successfully!', data: [1, 2, 3, 4, 5] });
            } else {
                reject(new Error('Failed to load data'));
            }
        }, 2000);
    });
}

window.demoPromises = function() {
    const output = document.getElementById('promiseOutput');
    
    output.innerHTML = '<div class="loading">Loading... ⏳</div>';
    
    fakeAPICall()
        .then(response => {
            output.innerHTML = `
                <div class="success-box">
                    <h4>✅ Success!</h4>
                    <pre>${JSON.stringify(response, null, 2)}</pre>
                </div>
            `;
        })
        .catch(error => {
            output.innerHTML = `
                <div class="error-box">
                    <h4>❌ Error!</h4>
                    <pre>${error.message}</pre>
                </div>
            `;
        });
};

// ===== 7. ASYNC/AWAIT =====
async function fetchUserData() {
    try {
        const response = await fetch('https://jsonplaceholder.typicode.com/users/1');
        const data = await response.json();
        return data;
    } catch (error) {
        throw new Error('Failed to fetch user data');
    }
}

window.demoAsyncAwait = async function() {
    const output = document.getElementById('asyncOutput');
    
    output.innerHTML = '<div class="loading">Fetching data... ⏳</div>';
    
    try {
        const user = await fetchUserData();
        
        output.innerHTML = `
            <div class="success-box">
                <h4>✅ User Data Fetched!</h4>
                <pre>${JSON.stringify(user, null, 2)}</pre>
            </div>
        `;
    } catch (error) {
        output.innerHTML = `
            <div class="error-box">
                <h4>❌ Error!</h4>
                <pre>${error.message}</pre>
            </div>
        `;
    }
};

// ===== 8. TEMPLATE LITERALS =====
window.generateTemplate = function() {
    const name = document.getElementById('nameInput').value || 'Guest';
    const age = document.getElementById('ageInput').value || '0';
    
    const template = `
        <div class="profile-card">
            <h3>Profile</h3>
            <p><strong>Name:</strong> ${name}</p>
            <p><strong>Age:</strong> ${age}</p>
            <p><strong>Status:</strong> ${age >= 18 ? 'Adult' : 'Minor'}</p>
            <p><strong>Generated:</strong> ${new Date().toLocaleString()}</p>
        </div>
    `;
    
    document.getElementById('templateOutput').innerHTML = template;
};

console.log('✅ ES6+ Features loaded!');
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
    max-width: 1000px;
    margin: 0 auto;
}

h1 {
    color: white;
    text-align: center;
    margin-bottom: 2rem;
    font-size: 2.5rem;
}

.demo-section {
    background: white;
    padding: 2rem;
    border-radius: 15px;
    margin-bottom: 2rem;
    box-shadow: 0 10px 30px rgba(0,0,0,0.2);
}

h2 {
    color: #2c3e50;
    margin-bottom: 1.5rem;
}

button {
    background-color: #667eea;
    color: white;
    border: none;
    padding: 0.75rem 1.5rem;
    border-radius: 8px;
    cursor: pointer;
    font-size: 1rem;
    transition: all 0.3s;
    margin-right: 0.5rem;
}

button:hover {
    background-color: #764ba2;
    transform: translateY(-2px);
}

input {
    padding: 0.75rem;
    border: 2px solid #ddd;
    border-radius: 8px;
    font-size: 1rem;
    margin-right: 0.5rem;
}

.output {
    margin-top: 1.5rem;
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
    white-space: pre-wrap;
}

.result-box {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    padding: 1.5rem;
    border-radius: 10px;
}

.result-box h4 {
    margin-bottom: 0.75rem;
}

.result-box pre {
    background: rgba(0,0,0,0.2);
    padding: 1rem;
    border-radius: 5px;
    overflow-x: auto;
}

.loading {
    text-align: center;
    padding: 2rem;
    font-size: 1.2rem;
    color: #667eea;
}

.success-box {
    background: #d4edda;
    border: 2px solid #28a745;
    padding: 1.5rem;
    border-radius: 10px;
}

.success-box h4 {
    color: #155724;
    margin-bottom: 0.75rem;
}

.success-box pre {
    background: #fff;
    color: #155724;
    padding: 1rem;
    border-radius: 5px;
    overflow-x: auto;
}

.error-box {
    background: #f8d7da;
    border: 2px solid #dc3545;
    padding: 1.5rem;
    border-radius: 10px;
}

.error-box h4 {
    color: #721c24;
    margin-bottom: 0.75rem;
}

.error-box pre {
    background: #fff;
    color: #721c24;
    padding: 1rem;
    border-radius: 5px;
    overflow-x: auto;
}

.array-demo,
.template-demo {
    margin-bottom: 1rem;
}

.button-group {
    display: flex;
    gap: 0.5rem;
    flex-wrap: wrap;
    margin-top: 1rem;
}

.profile-card {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    padding: 2rem;
    border-radius: 15px;
    box-shadow: 0 5px 15px rgba(0,0,0,0.2);
}

.profile-card h3 {
    margin-bottom: 1rem;
}

.profile-card p {
    margin: 0.5rem 0;
}

@media (max-width: 768px) {
    .button-group {
        flex-direction: column;
    }
    
    button {
        margin-right: 0;
        margin-bottom: 0.5rem;
    }
}
```

---

## 📖 Key Concepts

### Promises vs Async/Await
```javascript
// Promises
fetch(url)
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error(error));

// Async/Await (cleaner)
async function getData() {
    try {
        const response = await fetch(url);
        const data = await response.json();
        console.log(data);
    } catch (error) {
        console.error(error);
    }
}
```

---

## ✅ Self-Assessment

- [ ] Destructuring examples work
- [ ] Spread/rest operators demonstrated
- [ ] Arrow functions shown
- [ ] Array methods functional
- [ ] Classes working
- [ ] Promises demonstrated
- [ ] Async/await working
- [ ] Template literals showcased
- [ ] All interactive features work
- [ ] Code uses modern ES6+ syntax

---

**Next**: [Assignment 7: Asynchronous JavaScript](../assignment-07-async-javascript/ASSIGNMENT_7_GUIDE.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

