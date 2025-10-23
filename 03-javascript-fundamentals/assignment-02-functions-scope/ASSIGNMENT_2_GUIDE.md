# Assignment 2: Functions & Scope - Making Code Reusable

**By Mahendra Bagul**

Functions are the building blocks of JavaScript. They let you write code once and use it many times. Master this, and you're halfway to React! 🎯

---

## 📚 What You'll Learn

- ✅ Function declarations vs expressions
- ✅ Arrow functions (modern syntax)
- ✅ Parameters and arguments
- ✅ Return values
- ✅ Scope (global, function, block)
- ✅ Hoisting
- ✅ Default parameters
- ✅ Rest parameters
- ✅ IIFE (Immediately Invoked Function Expression)

---

## 🎯 Assignment Objectives

Create a **Utility Functions Library** with various calculator functions, string manipulators, and practical examples.

**Difficulty**: ⭐⭐☆☆☆  
**Time**: 4-5 hours  
**Prerequisites**: Assignment 1 completed

---

## 📋 Requirements

### Must Have
1. ✅ Function declarations
2. ✅ Function expressions
3. ✅ Arrow functions
4. ✅ Functions with parameters
5. ✅ Functions with return values
6. ✅ Default parameters
7. ✅ Rest parameters
8. ✅ Scope demonstrations (global, function, block)
9. ✅ Hoisting examples
10. ✅ Interactive UI for testing functions

---

## 🔧 Function Basics

### Function Declaration
```javascript
// Traditional way - hoisted
function greet(name) {
    return `Hello, ${name}!`;
}

console.log(greet('John'));  // "Hello, John!"
```

### Function Expression
```javascript
// Assigned to variable - not hoisted
const greet = function(name) {
    return `Hello, ${name}!`;
};

console.log(greet('Jane'));  // "Hello, Jane!"
```

### Arrow Function (Modern)
```javascript
// Concise syntax
const greet = (name) => {
    return `Hello, ${name}!`;
};

// Even shorter (implicit return)
const greet = name => `Hello, ${name}!`;

console.log(greet('Alice'));  // "Hello, Alice!"
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
    <title>Functions & Scope</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>⚡ JavaScript Functions</h1>
        
        <!-- Calculator Functions -->
        <section class="demo-section">
            <h2>🧮 Calculator Functions</h2>
            <div class="calc-group">
                <input type="number" id="calcNum1" placeholder="Number 1">
                <input type="number" id="calcNum2" placeholder="Number 2">
            </div>
            <div class="button-group">
                <button onclick="testAdd()">Add</button>
                <button onclick="testSubtract()">Subtract</button>
                <button onclick="testMultiply()">Multiply</button>
                <button onclick="testDivide()">Divide</button>
            </div>
            <div id="calcOutput" class="output"></div>
        </section>
        
        <!-- String Functions -->
        <section class="demo-section">
            <h2>📝 String Functions</h2>
            <input type="text" id="stringInput" placeholder="Enter text">
            <div class="button-group">
                <button onclick="testUpperCase()">Upper Case</button>
                <button onclick="testLowerCase()">Lower Case</button>
                <button onclick="testReverse()">Reverse</button>
                <button onclick="testPalindrome()">Is Palindrome?</button>
            </div>
            <div id="stringOutput" class="output"></div>
        </section>
        
        <!-- Arrow Functions -->
        <section class="demo-section">
            <h2>➡️ Arrow Functions</h2>
            <button onclick="demoArrowFunctions()">Show Arrow Function Examples</button>
            <div id="arrowOutput" class="output"></div>
        </section>
        
        <!-- Parameters -->
        <section class="demo-section">
            <h2>📦 Parameters Demo</h2>
            <button onclick="demoParameters()">Show Parameter Examples</button>
            <div id="paramOutput" class="output"></div>
        </section>
        
        <!-- Scope -->
        <section class="demo-section">
            <h2>🌐 Scope Demo</h2>
            <button onclick="demoScope()">Show Scope Examples</button>
            <div id="scopeOutput" class="output"></div>
        </section>
        
        <!-- Hoisting -->
        <section class="demo-section">
            <h2>⬆️ Hoisting Demo</h2>
            <button onclick="demoHoisting()">Show Hoisting Examples</button>
            <div id="hoistingOutput" class="output"></div>
        </section>
    </div>
    
    <script src="functions.js"></script>
    <script src="app.js"></script>
</body>
</html>
```

### JavaScript - Functions Library (functions.js)
```javascript
// ===== FUNCTION DECLARATIONS =====
// These are hoisted - can be called before declaration

function add(a, b) {
    return a + b;
}

function subtract(a, b) {
    return a - b;
}

function multiply(a, b) {
    return a * b;
}

function divide(a, b) {
    if (b === 0) {
        return 'Cannot divide by zero!';
    }
    return a / b;
}

// ===== FUNCTION EXPRESSIONS =====
// Not hoisted - must be declared before use

const square = function(num) {
    return num * num;
};

const cube = function(num) {
    return num * num * num;
};

// ===== ARROW FUNCTIONS =====
// Modern, concise syntax

// Multiple parameters
const power = (base, exponent) => {
    return base ** exponent;
};

// Single parameter (parentheses optional)
const double = num => num * 2;

// No parameters
const getRandomNumber = () => Math.random();

// Multiple lines
const greet = name => {
    const message = `Hello, ${name}!`;
    return message.toUpperCase();
};

// ===== STRING FUNCTIONS =====

function toUpperCase(str) {
    return str.toUpperCase();
}

function toLowerCase(str) {
    return str.toLowerCase();
}

function reverseString(str) {
    // Convert to array, reverse, join back
    return str.split('').reverse().join('');
}

function isPalindrome(str) {
    // Clean string (remove spaces, lowercase)
    const cleaned = str.toLowerCase().replace(/\s/g, '');
    const reversed = cleaned.split('').reverse().join('');
    return cleaned === reversed;
}

function countVowels(str) {
    const vowels = 'aeiouAEIOU';
    let count = 0;
    for (let char of str) {
        if (vowels.includes(char)) {
            count++;
        }
    }
    return count;
}

// ===== DEFAULT PARAMETERS =====

function greetUser(name = 'Guest', greeting = 'Hello') {
    return `${greeting}, ${name}!`;
}

function calculateDiscount(price, discount = 10) {
    return price - (price * discount / 100);
}

// ===== REST PARAMETERS =====
// Collect multiple arguments into an array

function sum(...numbers) {
    return numbers.reduce((total, num) => total + num, 0);
}

function findMax(...numbers) {
    return Math.max(...numbers);
}

function concatenateStrings(...strings) {
    return strings.join(' ');
}

// ===== HIGHER-ORDER FUNCTIONS =====
// Functions that take or return functions

function repeatOperation(fn, times) {
    for (let i = 0; i < times; i++) {
        fn(i);
    }
}

function createMultiplier(multiplier) {
    return function(number) {
        return number * multiplier;
    };
}

// ===== UTILITY FUNCTIONS =====

function isEven(num) {
    return num % 2 === 0;
}

function isOdd(num) {
    return num % 2 !== 0;
}

function isPrime(num) {
    if (num < 2) return false;
    for (let i = 2; i <= Math.sqrt(num); i++) {
        if (num % i === 0) return false;
    }
    return true;
}

function factorial(n) {
    if (n === 0 || n === 1) return 1;
    return n * factorial(n - 1);
}

// ===== SCOPE DEMONSTRATIONS =====

// Global scope variable
let globalVar = 'I am global';

function demoFunctionScope() {
    // Function scope variable
    let functionVar = 'I am in function scope';
    
    if (true) {
        // Block scope variable
        let blockVar = 'I am in block scope';
        const blockConst = 'I am also block scope';
        
        console.log(globalVar);      // ✅ Accessible
        console.log(functionVar);    // ✅ Accessible
        console.log(blockVar);       // ✅ Accessible
    }
    
    console.log(globalVar);      // ✅ Accessible
    console.log(functionVar);    // ✅ Accessible
    // console.log(blockVar);    // ❌ Error - not accessible
}

console.log('✅ Functions library loaded!');
```

### JavaScript - App Logic (app.js)
```javascript
// ===== CALCULATOR TESTS =====

function testAdd() {
    const num1 = parseFloat(document.getElementById('calcNum1').value);
    const num2 = parseFloat(document.getElementById('calcNum2').value);
    
    if (isNaN(num1) || isNaN(num2)) {
        showOutput('calcOutput', 'Please enter valid numbers!', 'error');
        return;
    }
    
    const result = add(num1, num2);
    showOutput('calcOutput', `${num1} + ${num2} = ${result}`, 'success');
}

function testSubtract() {
    const num1 = parseFloat(document.getElementById('calcNum1').value);
    const num2 = parseFloat(document.getElementById('calcNum2').value);
    
    if (isNaN(num1) || isNaN(num2)) {
        showOutput('calcOutput', 'Please enter valid numbers!', 'error');
        return;
    }
    
    const result = subtract(num1, num2);
    showOutput('calcOutput', `${num1} - ${num2} = ${result}`, 'success');
}

function testMultiply() {
    const num1 = parseFloat(document.getElementById('calcNum1').value);
    const num2 = parseFloat(document.getElementById('calcNum2').value);
    
    if (isNaN(num1) || isNaN(num2)) {
        showOutput('calcOutput', 'Please enter valid numbers!', 'error');
        return;
    }
    
    const result = multiply(num1, num2);
    showOutput('calcOutput', `${num1} × ${num2} = ${result}`, 'success');
}

function testDivide() {
    const num1 = parseFloat(document.getElementById('calcNum1').value);
    const num2 = parseFloat(document.getElementById('calcNum2').value);
    
    if (isNaN(num1) || isNaN(num2)) {
        showOutput('calcOutput', 'Please enter valid numbers!', 'error');
        return;
    }
    
    const result = divide(num1, num2);
    showOutput('calcOutput', `${num1} ÷ ${num2} = ${result}`, 
               typeof result === 'string' ? 'error' : 'success');
}

// ===== STRING TESTS =====

function testUpperCase() {
    const input = document.getElementById('stringInput').value;
    if (!input) {
        showOutput('stringOutput', 'Please enter some text!', 'error');
        return;
    }
    const result = toUpperCase(input);
    showOutput('stringOutput', `Result: ${result}`, 'success');
}

function testLowerCase() {
    const input = document.getElementById('stringInput').value;
    if (!input) {
        showOutput('stringOutput', 'Please enter some text!', 'error');
        return;
    }
    const result = toLowerCase(input);
    showOutput('stringOutput', `Result: ${result}`, 'success');
}

function testReverse() {
    const input = document.getElementById('stringInput').value;
    if (!input) {
        showOutput('stringOutput', 'Please enter some text!', 'error');
        return;
    }
    const result = reverseString(input);
    showOutput('stringOutput', `Result: ${result}`, 'success');
}

function testPalindrome() {
    const input = document.getElementById('stringInput').value;
    if (!input) {
        showOutput('stringOutput', 'Please enter some text!', 'error');
        return;
    }
    const result = isPalindrome(input);
    showOutput('stringOutput', 
               `"${input}" ${result ? 'IS' : 'IS NOT'} a palindrome`, 
               result ? 'success' : 'info');
}

// ===== ARROW FUNCTIONS DEMO =====

function demoArrowFunctions() {
    const output = document.getElementById('arrowOutput');
    
    // Regular function
    function regularAdd(a, b) {
        return a + b;
    }
    
    // Arrow function
    const arrowAdd = (a, b) => a + b;
    
    // Examples
    const examples = [
        {
            title: 'Multiple Parameters',
            code: 'const add = (a, b) => a + b;',
            result: arrowAdd(5, 3)
        },
        {
            title: 'Single Parameter',
            code: 'const double = num => num * 2;',
            result: double(7)
        },
        {
            title: 'No Parameters',
            code: 'const getRandom = () => Math.random();',
            result: getRandomNumber().toFixed(4)
        },
        {
            title: 'Multiple Lines',
            code: `const greet = name => {
    const msg = \`Hello, \${name}!\`;
    return msg.toUpperCase();
};`,
            result: greet('Mahendra')
        }
    ];
    
    let html = '<div class="examples">';
    examples.forEach(ex => {
        html += `
            <div class="example-box">
                <h4>${ex.title}</h4>
                <pre>${ex.code}</pre>
                <p class="result">Result: ${ex.result}</p>
            </div>
        `;
    });
    html += '</div>';
    
    output.innerHTML = html;
}

// ===== PARAMETERS DEMO =====

function demoParameters() {
    const output = document.getElementById('paramOutput');
    
    html = '<div class="examples">';
    
    // Default parameters
    html += `
        <div class="example-box">
            <h4>Default Parameters</h4>
            <pre>function greet(name = 'Guest') {
    return \`Hello, \${name}!\`;
}</pre>
            <p class="result">greet() → ${greetUser()}</p>
            <p class="result">greet('Alice') → ${greetUser('Alice')}</p>
        </div>
    `;
    
    // Rest parameters
    html += `
        <div class="example-box">
            <h4>Rest Parameters</h4>
            <pre>function sum(...numbers) {
    return numbers.reduce((a, b) => a + b, 0);
}</pre>
            <p class="result">sum(1, 2, 3) → ${sum(1, 2, 3)}</p>
            <p class="result">sum(1, 2, 3, 4, 5) → ${sum(1, 2, 3, 4, 5)}</p>
        </div>
    `;
    
    // Multiple strings
    html += `
        <div class="example-box">
            <h4>Concatenate Strings</h4>
            <pre>function concat(...strings) {
    return strings.join(' ');
}</pre>
            <p class="result">${concatenateStrings('Hello', 'from', 'JavaScript!')}</p>
        </div>
    `;
    
    html += '</div>';
    output.innerHTML = html;
}

// ===== SCOPE DEMO =====

function demoScope() {
    const output = document.getElementById('scopeOutput');
    
    // Global scope
    let globalMessage = 'Global scope';
    
    function outerFunction() {
        let outerMessage = 'Outer function scope';
        
        function innerFunction() {
            let innerMessage = 'Inner function scope';
            return `Inner can access: ${innerMessage}, ${outerMessage}, ${globalMessage}`;
        }
        
        return innerFunction();
    }
    
    const result = outerFunction();
    
    output.innerHTML = `
        <div class="scope-demo">
            <h4>Scope Chain</h4>
            <div class="scope-level global">
                <strong>Global Scope</strong>
                <p>let globalMessage = 'Global scope';</p>
                <div class="scope-level function">
                    <strong>Function Scope (outer)</strong>
                    <p>let outerMessage = 'Outer function scope';</p>
                    <div class="scope-level block">
                        <strong>Function Scope (inner)</strong>
                        <p>let innerMessage = 'Inner function scope';</p>
                        <p class="access">✅ Can access: inner, outer, global</p>
                    </div>
                    <p class="access">✅ Can access: outer, global</p>
                    <p class="access">❌ Cannot access: inner</p>
                </div>
                <p class="access">✅ Can access: global</p>
                <p class="access">❌ Cannot access: outer, inner</p>
            </div>
            <div class="result-box">
                <strong>Result:</strong>
                <p>${result}</p>
            </div>
        </div>
    `;
}

// ===== HOISTING DEMO =====

function demoHoisting() {
    const output = document.getElementById('hoistingOutput');
    
    output.innerHTML = `
        <div class="examples">
            <div class="example-box">
                <h4>✅ Function Declaration (Hoisted)</h4>
                <pre>// Can call before declaration
console.log(sayHello());

function sayHello() {
    return 'Hello!';
}
// Works! → "Hello!"</pre>
                <p class="result success">This works because function declarations are hoisted!</p>
            </div>
            
            <div class="example-box">
                <h4>❌ Function Expression (Not Hoisted)</h4>
                <pre>// Cannot call before declaration
console.log(sayHi());

const sayHi = function() {
    return 'Hi!';
};
// Error! sayHi is not defined</pre>
                <p class="result error">This causes an error because const is not hoisted!</p>
            </div>
            
            <div class="example-box">
                <h4>❌ Arrow Function (Not Hoisted)</h4>
                <pre>// Cannot call before declaration
console.log(greet());

const greet = () => 'Greetings!';
// Error! greet is not defined</pre>
                <p class="result error">Arrow functions are also not hoisted!</p>
            </div>
            
            <div class="example-box">
                <h4>💡 Best Practice</h4>
                <p>Always declare functions before using them. Don't rely on hoisting!</p>
            </div>
        </div>
    `;
}

// ===== UTILITY FUNCTION =====

function showOutput(elementId, message, type = 'info') {
    const element = document.getElementById(elementId);
    const className = type === 'error' ? 'error' : 
                     type === 'success' ? 'success' : 'info';
    element.innerHTML = `<div class="${className}">${message}</div>`;
}

console.log('✅ App loaded!');
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

input {
    width: 100%;
    padding: 0.75rem;
    border: 2px solid #ddd;
    border-radius: 8px;
    font-size: 1rem;
    margin-bottom: 1rem;
}

.calc-group {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
    margin-bottom: 1rem;
}

.button-group {
    display: flex;
    gap: 0.5rem;
    flex-wrap: wrap;
    margin-bottom: 1rem;
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
    flex: 1;
    min-width: 120px;
}

button:hover {
    background-color: #764ba2;
    transform: translateY(-2px);
}

.output {
    margin-top: 1rem;
}

.output > div {
    padding: 1rem;
    border-radius: 8px;
    margin-top: 0.5rem;
}

.success {
    background-color: #d4edda;
    color: #155724;
    border-left: 4px solid #28a745;
}

.error {
    background-color: #f8d7da;
    color: #721c24;
    border-left: 4px solid #dc3545;
}

.info {
    background-color: #d1ecf1;
    color: #0c5460;
    border-left: 4px solid #17a2b8;
}

.examples {
    display: grid;
    gap: 1rem;
}

.example-box {
    background: #f8f9fa;
    padding: 1.5rem;
    border-radius: 10px;
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
    margin: 0.75rem 0;
    font-size: 0.9rem;
}

.result {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    padding: 0.75rem;
    border-radius: 5px;
    margin-top: 0.5rem;
    font-weight: bold;
}

.scope-demo {
    background: #f8f9fa;
    padding: 1.5rem;
    border-radius: 10px;
}

.scope-level {
    border: 2px solid;
    padding: 1rem;
    border-radius: 8px;
    margin: 1rem 0;
}

.scope-level.global {
    border-color: #dc3545;
    background: #fff5f5;
}

.scope-level.function {
    border-color: #ffc107;
    background: #fffbf0;
}

.scope-level.block {
    border-color: #28a745;
    background: #f0fff4;
}

.access {
    margin: 0.5rem 0;
    font-size: 0.9rem;
}

.result-box {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    padding: 1.5rem;
    border-radius: 8px;
    margin-top: 1rem;
}

@media (max-width: 768px) {
    .calc-group {
        grid-template-columns: 1fr;
    }
    
    .button-group {
        flex-direction: column;
    }
    
    button {
        min-width: auto;
    }
}
```

---

## 📖 Key Concepts

### Parameters vs Arguments
```javascript
// Parameters: variables in function definition
function greet(name, age) {  // name and age are parameters
    return `${name} is ${age} years old`;
}

// Arguments: actual values passed
greet('John', 25);  // 'John' and 25 are arguments
```

### Return Statement
```javascript
// With return
function add(a, b) {
    return a + b;  // Returns value
}
const result = add(5, 3);  // result = 8

// Without return
function logSum(a, b) {
    console.log(a + b);  // No return
}
const result2 = logSum(5, 3);  // result2 = undefined
```

---

## ✅ Self-Assessment

- [ ] Created function declarations
- [ ] Created function expressions
- [ ] Used arrow functions
- [ ] Functions with parameters
- [ ] Functions with return values
- [ ] Default parameters used
- [ ] Rest parameters demonstrated
- [ ] Scope examples shown
- [ ] Hoisting explained
- [ ] Interactive UI works

---

## 🐛 Common Mistakes

**1. Forgetting to return**
```javascript
// ❌ Missing return
function add(a, b) {
    a + b;  // Does nothing!
}

// ✅ With return
function add(a, b) {
    return a + b;
}
```

**2. Calling function without ()**
```javascript
console.log(greet);     // ❌ Logs the function
console.log(greet());   // ✅ Calls the function
```

---

**Next**: [Assignment 3: Arrays & Objects](../assignment-03-arrays-objects/ASSIGNMENT_3_GUIDE.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

