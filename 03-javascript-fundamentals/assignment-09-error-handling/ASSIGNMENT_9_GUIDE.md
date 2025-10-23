# Assignment 9: Error Handling & Debugging - Building Robust Apps

**By Mahendra Bagul**

Errors happen. Good developers handle them gracefully! Learn to catch, handle, and debug errors like a pro. 🐛

---

## 📚 What You'll Learn

- ✅ Types of errors (Syntax, Reference, Type)
- ✅ try/catch/finally
- ✅ Throwing custom errors
- ✅ Error objects
- ✅ console methods (log, error, warn, table, time)
- ✅ Debugger statement
- ✅ Browser DevTools
- ✅ Error boundaries
- ✅ Validation techniques
- ✅ Defensive programming

---

## 🎯 Assignment Objectives

Create an **Error Handling Playground** that demonstrates all error types and debugging techniques.

**Difficulty**: ⭐⭐⭐☆☆  
**Time**: 4-5 hours  
**Prerequisites**: Assignments 1-8 completed

---

## 📋 Requirements

### Must Have
1. ✅ Error types demonstrated
2. ✅ try/catch/finally examples
3. ✅ Custom error classes
4. ✅ Input validation
5. ✅ console methods showcase
6. ✅ Debugging examples
7. ✅ Error recovery
8. ✅ User-friendly error messages
9. ✅ Logging system
10. ✅ Interactive demos

---

## 💻 Complete Implementation

### HTML (index.html)
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Error Handling & Debugging</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>🐛 Error Handling & Debugging</h1>
        
        <!-- Error Types -->
        <section class="demo-section">
            <h2>1. Error Types</h2>
            <div class="button-group">
                <button onclick="triggerSyntaxError()">Syntax Error</button>
                <button onclick="triggerReferenceError()">Reference Error</button>
                <button onclick="triggerTypeError()">Type Error</button>
                <button onclick="triggerRangeError()">Range Error</button>
            </div>
            <div id="errorOutput" class="output"></div>
        </section>
        
        <!-- Try/Catch/Finally -->
        <section class="demo-section">
            <h2>2. Try/Catch/Finally</h2>
            <button onclick="demoTryCatch()">Run Try/Catch Example</button>
            <div id="tryCatchOutput" class="output"></div>
        </section>
        
        <!-- Custom Errors -->
        <section class="demo-section">
            <h2>3. Custom Errors</h2>
            <button onclick="demoCustomError()">Throw Custom Error</button>
            <div id="customErrorOutput" class="output"></div>
        </section>
        
        <!-- Input Validation -->
        <section class="demo-section">
            <h2>4. Input Validation</h2>
            <form id="validationForm" class="validation-form">
                <input type="text" id="emailInput" placeholder="Email">
                <input type="number" id="ageInput" placeholder="Age (18-100)">
                <input type="text" id="phoneInput" placeholder="Phone (10 digits)">
                <button type="submit">Validate</button>
            </form>
            <div id="validationOutput" class="output"></div>
        </section>
        
        <!-- Console Methods -->
        <section class="demo-section">
            <h2>5. Console Methods</h2>
            <p class="info">Open browser console (F12) to see output!</p>
            <div class="button-group">
                <button onclick="demoConsoleLog()">console.log()</button>
                <button onclick="demoConsoleTable()">console.table()</button>
                <button onclick="demoConsoleTime()">console.time()</button>
                <button onclick="demoConsoleGroup()">console.group()</button>
            </div>
        </section>
        
        <!-- Error Recovery -->
        <section class="demo-section">
            <h2>6. Error Recovery</h2>
            <button onclick="demoErrorRecovery()">Try API with Fallback</button>
            <div id="recoveryOutput" class="output"></div>
        </section>
        
        <!-- Logging System -->
        <section class="demo-section">
            <h2>7. Error Logs</h2>
            <button onclick="clearLogs()">Clear Logs</button>
            <div id="errorLogs" class="log-container"></div>
        </section>
    </div>
    
    <script src="script.js"></script>
</body>
</html>
```

### JavaScript (script.js)
```javascript
// ===== ERROR LOGGING SYSTEM =====
const errorLogs = [];

function logError(type, message, details = '') {
    const log = {
        timestamp: new Date().toLocaleString(),
        type: type,
        message: message,
        details: details
    };
    
    errorLogs.push(log);
    updateErrorLogs();
    
    console.error(`[${type}]`, message, details);
}

function updateErrorLogs() {
    const container = document.getElementById('errorLogs');
    
    if (errorLogs.length === 0) {
        container.innerHTML = '<div class="no-logs">No errors logged yet</div>';
        return;
    }
    
    container.innerHTML = errorLogs.map(log => `
        <div class="log-entry ${log.type}">
            <div class="log-time">${log.timestamp}</div>
            <div class="log-type">${log.type.toUpperCase()}</div>
            <div class="log-message">${log.message}</div>
            ${log.details ? `<div class="log-details">${log.details}</div>` : ''}
        </div>
    `).reverse().join('');
}

function clearLogs() {
    errorLogs.length = 0;
    updateErrorLogs();
}

// ===== 1. ERROR TYPES =====
function triggerSyntaxError() {
    const output = document.getElementById('errorOutput');
    try {
        // This will cause a syntax error
        eval('const x = ');
    } catch (error) {
        output.innerHTML = `
            <div class="error-box">
                <h4>SyntaxError</h4>
                <p><strong>Name:</strong> ${error.name}</p>
                <p><strong>Message:</strong> ${error.message}</p>
                <p><strong>What it means:</strong> Invalid JavaScript syntax</p>
            </div>
        `;
        logError('syntax', error.message);
    }
}

function triggerReferenceError() {
    const output = document.getElementById('errorOutput');
    try {
        // This will cause a reference error
        console.log(undefinedVariable);
    } catch (error) {
        output.innerHTML = `
            <div class="error-box">
                <h4>ReferenceError</h4>
                <p><strong>Name:</strong> ${error.name}</p>
                <p><strong>Message:</strong> ${error.message}</p>
                <p><strong>What it means:</strong> Variable doesn't exist</p>
            </div>
        `;
        logError('reference', error.message);
    }
}

function triggerTypeError() {
    const output = document.getElementById('errorOutput');
    try {
        // This will cause a type error
        const num = 42;
        num.toUpperCase();
    } catch (error) {
        output.innerHTML = `
            <div class="error-box">
                <h4>TypeError</h4>
                <p><strong>Name:</strong> ${error.name}</p>
                <p><strong>Message:</strong> ${error.message}</p>
                <p><strong>What it means:</strong> Wrong data type used</p>
            </div>
        `;
        logError('type', error.message);
    }
}

function triggerRangeError() {
    const output = document.getElementById('errorOutput');
    try {
        // This will cause a range error
        const arr = new Array(-1);
    } catch (error) {
        output.innerHTML = `
            <div class="error-box">
                <h4>RangeError</h4>
                <p><strong>Name:</strong> ${error.name}</p>
                <p><strong>Message:</strong> ${error.message}</p>
                <p><strong>What it means:</strong> Value out of range</p>
            </div>
        `;
        logError('range', error.message);
    }
}

// ===== 2. TRY/CATCH/FINALLY =====
function demoTryCatch() {
    const output = document.getElementById('tryCatchOutput');
    let result = '';
    
    try {
        result += '1. Try block started\n';
        
        const data = JSON.parse('{"name": "John"}');
        result += `2. Parsed JSON: ${data.name}\n`;
        
        // This will throw an error
        JSON.parse('invalid json');
        
        result += '3. This won\'t execute\n';
    } catch (error) {
        result += `4. Caught error: ${error.message}\n`;
    } finally {
        result += '5. Finally block always runs\n';
    }
    
    output.innerHTML = `
        <div class="code-output">
            <h4>Try/Catch/Finally Flow:</h4>
            <pre>${result}</pre>
            <p class="info">The finally block runs whether error occurs or not!</p>
        </div>
    `;
}

// ===== 3. CUSTOM ERRORS =====
class ValidationError extends Error {
    constructor(message) {
        super(message);
        this.name = 'ValidationError';
    }
}

class NetworkError extends Error {
    constructor(message, statusCode) {
        super(message);
        this.name = 'NetworkError';
        this.statusCode = statusCode;
    }
}

function demoCustomError() {
    const output = document.getElementById('customErrorOutput');
    
    try {
        throw new ValidationError('Email format is invalid!');
    } catch (error) {
        if (error instanceof ValidationError) {
            output.innerHTML = `
                <div class="error-box">
                    <h4>Custom Error: ${error.name}</h4>
                    <p><strong>Message:</strong> ${error.message}</p>
                    <p><strong>Type:</strong> User input validation failed</p>
                    <pre>class ValidationError extends Error {
    constructor(message) {
        super(message);
        this.name = 'ValidationError';
    }
}

throw new ValidationError('Email format is invalid!');</pre>
                </div>
            `;
            logError('validation', error.message);
        }
    }
}

// ===== 4. INPUT VALIDATION =====
document.getElementById('validationForm').addEventListener('submit', (e) => {
    e.preventDefault();
    
    const email = document.getElementById('emailInput').value;
    const age = document.getElementById('ageInput').value;
    const phone = document.getElementById('phoneInput').value;
    const output = document.getElementById('validationOutput');
    
    const errors = [];
    
    // Email validation
    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    if (!emailRegex.test(email)) {
        errors.push('Invalid email format');
    }
    
    // Age validation
    const ageNum = parseInt(age);
    if (isNaN(ageNum) || ageNum < 18 || ageNum > 100) {
        errors.push('Age must be between 18 and 100');
    }
    
    // Phone validation
    const phoneRegex = /^\d{10}$/;
    if (!phoneRegex.test(phone)) {
        errors.push('Phone must be exactly 10 digits');
    }
    
    if (errors.length > 0) {
        output.innerHTML = `
            <div class="error-box">
                <h4>Validation Errors:</h4>
                <ul>
                    ${errors.map(err => `<li>${err}</li>`).join('')}
                </ul>
            </div>
        `;
        errors.forEach(err => logError('validation', err));
    } else {
        output.innerHTML = `
            <div class="success-box">
                <h4>✅ All inputs valid!</h4>
                <p>Email: ${email}</p>
                <p>Age: ${age}</p>
                <p>Phone: ${phone}</p>
            </div>
        `;
    }
});

// ===== 5. CONSOLE METHODS =====
function demoConsoleLog() {
    console.log('Basic log message');
    console.log('Multiple', 'values', 123, true);
    console.log('%cStyled log!', 'color: blue; font-size: 20px; font-weight: bold');
    
    console.info('ℹ️ Info message');
    console.warn('⚠️ Warning message');
    console.error('❌ Error message');
    
    alert('Check browser console (F12) for output!');
}

function demoConsoleTable() {
    const users = [
        { name: 'John', age: 30, city: 'Mumbai' },
        { name: 'Jane', age: 25, city: 'Delhi' },
        { name: 'Bob', age: 35, city: 'Bangalore' }
    ];
    
    console.table(users);
    alert('Check browser console for table!');
}

function demoConsoleTime() {
    console.time('Loop Timer');
    
    let sum = 0;
    for (let i = 0; i < 1000000; i++) {
        sum += i;
    }
    
    console.timeEnd('Loop Timer');
    console.log('Sum:', sum);
    
    alert('Check browser console for timing!');
}

function demoConsoleGroup() {
    console.group('User Details');
    console.log('Name: John Doe');
    console.log('Age: 30');
    console.log('Email: john@example.com');
    
    console.group('Address');
    console.log('City: Mumbai');
    console.log('Country: India');
    console.groupEnd();
    
    console.groupEnd();
    
    alert('Check browser console for grouped logs!');
}

// ===== 6. ERROR RECOVERY =====
async function demoErrorRecovery() {
    const output = document.getElementById('recoveryOutput');
    
    output.innerHTML = '<div class="loading">⏳ Trying API...</div>';
    
    try {
        // Try main API (will fail)
        const response = await fetch('https://invalid-api-url.com/data');
        if (!response.ok) throw new Error('API failed');
        
        const data = await response.json();
        output.innerHTML = `<div class="success-box">✅ Success: ${data}</div>`;
        
    } catch (error) {
        logError('network', error.message);
        
        try {
            // Fallback to backup API
            output.innerHTML = '<div class="loading">⏳ Trying fallback...</div>';
            
            await new Promise(resolve => setTimeout(resolve, 1000));
            
            // Simulate fallback success
            const fallbackData = { message: 'Loaded from backup!', users: 10 };
            
            output.innerHTML = `
                <div class="success-box">
                    <h4>✅ Recovered from error!</h4>
                    <p>Main API failed, used fallback</p>
                    <pre>${JSON.stringify(fallbackData, null, 2)}</pre>
                </div>
            `;
        } catch (fallbackError) {
            logError('network', 'Both APIs failed');
            output.innerHTML = `
                <div class="error-box">
                    <h4>❌ Complete failure</h4>
                    <p>Both main and fallback APIs failed</p>
                </div>
            `;
        }
    }
}

// ===== DEFENSIVE PROGRAMMING =====
function safeJSONParse(jsonString) {
    try {
        return JSON.parse(jsonString);
    } catch (error) {
        console.error('Failed to parse JSON:', error.message);
        return null;
    }
}

function safeDivide(a, b) {
    if (typeof a !== 'number' || typeof b !== 'number') {
        throw new TypeError('Both arguments must be numbers');
    }
    if (b === 0) {
        throw new Error('Cannot divide by zero');
    }
    return a / b;
}

// ===== INITIALIZE =====
console.log('✅ Error Handling demo loaded!');
console.log('Try triggering different errors and watch the logs!');
updateErrorLogs();
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
}

button:hover {
    background-color: #764ba2;
    transform: translateY(-2px);
}

.output {
    margin-top: 1.5rem;
}

.error-box {
    background: #f8d7da;
    border: 2px solid #dc3545;
    padding: 1.5rem;
    border-radius: 10px;
    color: #721c24;
}

.error-box h4 {
    color: #dc3545;
    margin-bottom: 1rem;
}

.error-box p {
    margin: 0.5rem 0;
}

.error-box pre {
    background: #fff;
    padding: 1rem;
    border-radius: 5px;
    overflow-x: auto;
    margin-top: 1rem;
    color: #333;
}

.success-box {
    background: #d4edda;
    border: 2px solid #28a745;
    padding: 1.5rem;
    border-radius: 10px;
    color: #155724;
}

.success-box h4 {
    color: #28a745;
    margin-bottom: 1rem;
}

.code-output {
    background: #f8f9fa;
    padding: 1.5rem;
    border-radius: 10px;
}

.code-output h4 {
    color: #667eea;
    margin-bottom: 1rem;
}

.code-output pre {
    background: #2c3e50;
    color: #fff;
    padding: 1rem;
    border-radius: 5px;
    white-space: pre-wrap;
}

.info {
    color: #666;
    font-style: italic;
    margin-top: 0.5rem;
}

.validation-form {
    display: flex;
    flex-direction: column;
    gap: 1rem;
}

input {
    padding: 0.75rem;
    border: 2px solid #ddd;
    border-radius: 8px;
    font-size: 1rem;
}

.loading {
    text-align: center;
    padding: 2rem;
    font-size: 1.2rem;
    color: #667eea;
}

.log-container {
    max-height: 400px;
    overflow-y: auto;
    background: #f8f9fa;
    padding: 1rem;
    border-radius: 10px;
}

.log-entry {
    background: white;
    padding: 1rem;
    border-radius: 8px;
    margin-bottom: 0.5rem;
    border-left: 4px solid;
}

.log-entry.syntax,
.log-entry.reference,
.log-entry.type,
.log-entry.range {
    border-color: #dc3545;
}

.log-entry.validation {
    border-color: #ffc107;
}

.log-entry.network {
    border-color: #17a2b8;
}

.log-time {
    font-size: 0.875rem;
    color: #999;
    margin-bottom: 0.5rem;
}

.log-type {
    display: inline-block;
    padding: 0.25rem 0.5rem;
    background: #667eea;
    color: white;
    border-radius: 4px;
    font-size: 0.75rem;
    font-weight: bold;
    margin-bottom: 0.5rem;
}

.log-message {
    color: #333;
    margin-bottom: 0.5rem;
}

.log-details {
    font-size: 0.875rem;
    color: #666;
    font-family: 'Courier New', monospace;
}

.no-logs {
    text-align: center;
    color: #999;
    padding: 2rem;
}

@media (max-width: 768px) {
    .button-group {
        flex-direction: column;
    }
}
```

---

## 📖 Key Concepts

### Error Object Properties
```javascript
try {
    // code
} catch (error) {
    console.log(error.name);      // Error type
    console.log(error.message);   // Error message
    console.log(error.stack);     // Stack trace
}
```

### Best Practices
1. **Always use try/catch with async code**
2. **Validate user input**
3. **Provide helpful error messages**
4. **Log errors for debugging**
5. **Have fallback strategies**

---

## ✅ Self-Assessment

- [ ] All error types demonstrated
- [ ] try/catch/finally working
- [ ] Custom errors created
- [ ] Input validation implemented
- [ ] Console methods explored
- [ ] Error recovery shown
- [ ] Logging system works
- [ ] User-friendly error messages
- [ ] Defensive programming examples
- [ ] Clean, organized code

---

**Next**: [Assignment 10: Local Storage & JSON](../assignment-10-localstorage-json/ASSIGNMENT_10_GUIDE.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

