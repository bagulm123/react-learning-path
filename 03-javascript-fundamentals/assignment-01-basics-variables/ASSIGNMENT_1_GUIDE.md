# Assignment 1: JavaScript Basics & Variables - Your First Code

**By Mahendra Bagul**

Welcome to JavaScript! This is where the real magic happens. You've built the structure (HTML) and made it pretty (CSS) - now let's make it DO things! 🚀

---

## 📚 What You'll Learn

- ✅ What JavaScript is and where it runs
- ✅ Variables (let, const, var)
- ✅ Data types (string, number, boolean, null, undefined)
- ✅ Operators (arithmetic, comparison, logical)
- ✅ Console.log for debugging
- ✅ Basic input/output
- ✅ Type conversion
- ✅ Template literals

---

## 🎯 Assignment Objectives

Create an **Interactive Calculator** that performs basic math operations and demonstrates all JavaScript fundamentals.

**Difficulty**: ⭐☆☆☆☆  
**Time**: 3-4 hours  
**Prerequisites**: HTML & CSS phases completed

---

## 📋 Requirements

### Must Have
1. ✅ Variables using let, const, and var (demonstrate difference)
2. ✅ All data types demonstrated
3. ✅ Arithmetic operations (+, -, *, /, %)
4. ✅ Comparison operators (==, ===, !=, !==, <, >)
5. ✅ Logical operators (&&, ||, !)
6. ✅ String concatenation and template literals
7. ✅ Type checking with typeof
8. ✅ Type conversion
9. ✅ Console.log outputs
10. ✅ Interactive calculator with HTML interface

---

## 💻 JavaScript Basics

### What is JavaScript?

JavaScript is a programming language that:
- Runs in web browsers (client-side)
- Makes websites interactive
- Can also run on servers (Node.js)
- Is THE language of the web

### Where Does JavaScript Go?

**Option 1: Inline** (not recommended)
```html
<button onclick="alert('Hello!')">Click Me</button>
```

**Option 2: Internal Script**
```html
<script>
    console.log('Hello!');
</script>
```

**Option 3: External File** (recommended)
```html
<script src="script.js"></script>
```

---

## 🔤 Variables

### let - Block-scoped, can be reassigned
```javascript
let name = 'John';
name = 'Jane';  // OK - can reassign
console.log(name);  // 'Jane'
```

### const - Block-scoped, cannot be reassigned
```javascript
const PI = 3.14159;
PI = 3.14;  // ERROR - cannot reassign
console.log(PI);  // 3.14159
```

### var - Function-scoped (old way, avoid)
```javascript
var age = 25;  // Works but use let instead
```

**Best Practice**: Use `const` by default, `let` when you need to reassign, avoid `var`.

---

## 📊 Data Types

### Primitive Types

```javascript
// String - text
let name = "John";
let greeting = 'Hello';
let message = `Hi, ${name}!`;  // Template literal

// Number - integers and decimals
let age = 25;
let price = 19.99;
let negative = -10;

// Boolean - true or false
let isStudent = true;
let hasLicense = false;

// Undefined - variable declared but not assigned
let something;
console.log(something);  // undefined

// Null - intentionally empty
let empty = null;

// Check type
console.log(typeof name);  // "string"
console.log(typeof age);   // "number"
console.log(typeof isStudent);  // "boolean"
```

---

## ➕ Operators

### Arithmetic Operators
```javascript
let a = 10;
let b = 3;

console.log(a + b);  // 13 - Addition
console.log(a - b);  // 7  - Subtraction
console.log(a * b);  // 30 - Multiplication
console.log(a / b);  // 3.333... - Division
console.log(a % b);  // 1  - Modulus (remainder)
console.log(a ** b); // 1000 - Exponentiation (10^3)

// Increment/Decrement
let count = 0;
count++;  // count = count + 1
count--;  // count = count - 1
```

### Comparison Operators
```javascript
let x = 5;
let y = '5';

console.log(x == y);   // true - loose equality (converts types)
console.log(x === y);  // false - strict equality (no conversion)
console.log(x != y);   // false
console.log(x !== y);  // true
console.log(x > 3);    // true
console.log(x < 10);   // true
console.log(x >= 5);   // true
console.log(x <= 5);   // true
```

**Always use === and !== for comparisons!**

### Logical Operators
```javascript
let age = 25;
let hasID = true;

// AND - both must be true
console.log(age >= 18 && hasID);  // true

// OR - at least one must be true
console.log(age >= 21 || hasID);  // true

// NOT - inverts boolean
console.log(!hasID);  // false
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
    <title>JavaScript Calculator</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>JavaScript Calculator</h1>
        
        <!-- Variable Demo Section -->
        <section class="demo-section">
            <h2>Variables Demo</h2>
            <button onclick="demoVariables()">Run Variables Demo</button>
            <div id="variablesOutput" class="output"></div>
        </section>
        
        <!-- Data Types Demo -->
        <section class="demo-section">
            <h2>Data Types Demo</h2>
            <button onclick="demoDataTypes()">Run Data Types Demo</button>
            <div id="dataTypesOutput" class="output"></div>
        </section>
        
        <!-- Calculator -->
        <section class="calculator">
            <h2>Interactive Calculator</h2>
            <div class="calc-inputs">
                <input type="number" id="num1" placeholder="First number">
                <select id="operator">
                    <option value="+">+</option>
                    <option value="-">-</option>
                    <option value="*">×</option>
                    <option value="/">÷</option>
                    <option value="%">%</option>
                </select>
                <input type="number" id="num2" placeholder="Second number">
            </div>
            <button onclick="calculate()" class="btn-calculate">Calculate</button>
            <div id="result" class="result"></div>
        </section>
        
        <!-- Comparison Demo -->
        <section class="demo-section">
            <h2>Comparison Demo</h2>
            <div class="comparison-inputs">
                <input type="text" id="value1" placeholder="Value 1">
                <input type="text" id="value2" placeholder="Value 2">
            </div>
            <button onclick="compareValues()">Compare Values</button>
            <div id="comparisonOutput" class="output"></div>
        </section>
        
        <!-- Type Conversion -->
        <section class="demo-section">
            <h2>Type Conversion</h2>
            <input type="text" id="convertInput" placeholder="Enter something">
            <button onclick="convertTypes()">Convert</button>
            <div id="conversionOutput" class="output"></div>
        </section>
    </div>
    
    <script src="script.js"></script>
</body>
</html>
```

### JavaScript (script.js)
```javascript
// ===== VARIABLES DEMO =====
function demoVariables() {
    const output = document.getElementById('variablesOutput');
    
    // Using let (can reassign)
    let studentName = 'John';
    console.log('Initial name:', studentName);
    studentName = 'Jane';  // Reassignment works
    console.log('Updated name:', studentName);
    
    // Using const (cannot reassign)
    const PI = 3.14159;
    console.log('PI:', PI);
    // PI = 3.14;  // This would cause an error!
    
    // var (old way - avoid)
    var age = 25;
    console.log('Age:', age);
    
    output.innerHTML = `
        <strong>let Example:</strong>
        <pre>let studentName = 'John';
studentName = 'Jane';  // ✅ Works
Current value: ${studentName}</pre>
        
        <strong>const Example:</strong>
        <pre>const PI = 3.14159;
// PI = 3.14;  // ❌ Error!
Value: ${PI}</pre>
        
        <strong>var Example (avoid):</strong>
        <pre>var age = 25;
Value: ${age}</pre>
    `;
}

// ===== DATA TYPES DEMO =====
function demoDataTypes() {
    const output = document.getElementById('dataTypesOutput');
    
    // String
    const name = "Alice";
    const greeting = 'Hello';
    const message = `Hi, ${name}!`;  // Template literal
    
    // Number
    const age = 30;
    const price = 19.99;
    const negative = -5;
    
    // Boolean
    const isStudent = true;
    const hasJob = false;
    
    // Undefined
    let notDefined;
    
    // Null
    const empty = null;
    
    output.innerHTML = `
        <table>
            <tr>
                <th>Type</th>
                <th>Value</th>
                <th>typeof</th>
            </tr>
            <tr>
                <td>String</td>
                <td>"${name}"</td>
                <td>${typeof name}</td>
            </tr>
            <tr>
                <td>String (template)</td>
                <td>"${message}"</td>
                <td>${typeof message}</td>
            </tr>
            <tr>
                <td>Number</td>
                <td>${age}</td>
                <td>${typeof age}</td>
            </tr>
            <tr>
                <td>Number (decimal)</td>
                <td>${price}</td>
                <td>${typeof price}</td>
            </tr>
            <tr>
                <td>Boolean</td>
                <td>${isStudent}</td>
                <td>${typeof isStudent}</td>
            </tr>
            <tr>
                <td>Undefined</td>
                <td>${notDefined}</td>
                <td>${typeof notDefined}</td>
            </tr>
            <tr>
                <td>Null</td>
                <td>${empty}</td>
                <td>${typeof empty}</td>
            </tr>
        </table>
    `;
    
    console.log('=== Data Types Demo ===');
    console.log('String:', name, typeof name);
    console.log('Template Literal:', message);
    console.log('Number:', age, typeof age);
    console.log('Boolean:', isStudent, typeof isStudent);
    console.log('Undefined:', notDefined, typeof notDefined);
    console.log('Null:', empty, typeof empty);
}

// ===== CALCULATOR =====
function calculate() {
    // Get input values
    const num1 = parseFloat(document.getElementById('num1').value);
    const num2 = parseFloat(document.getElementById('num2').value);
    const operator = document.getElementById('operator').value;
    const resultDiv = document.getElementById('result');
    
    // Validate inputs
    if (isNaN(num1) || isNaN(num2)) {
        resultDiv.innerHTML = '<p class="error">Please enter valid numbers!</p>';
        return;
    }
    
    // Perform calculation
    let result;
    let operation;
    
    switch(operator) {
        case '+':
            result = num1 + num2;
            operation = `${num1} + ${num2}`;
            break;
        case '-':
            result = num1 - num2;
            operation = `${num1} - ${num2}`;
            break;
        case '*':
            result = num1 * num2;
            operation = `${num1} × ${num2}`;
            break;
        case '/':
            if (num2 === 0) {
                resultDiv.innerHTML = '<p class="error">Cannot divide by zero!</p>';
                return;
            }
            result = num1 / num2;
            operation = `${num1} ÷ ${num2}`;
            break;
        case '%':
            result = num1 % num2;
            operation = `${num1} % ${num2}`;
            break;
        default:
            resultDiv.innerHTML = '<p class="error">Invalid operator!</p>';
            return;
    }
    
    // Display result
    resultDiv.innerHTML = `
        <div class="calculation">
            <p class="operation">${operation}</p>
            <p class="answer">= ${result}</p>
        </div>
    `;
    
    console.log(`Calculation: ${operation} = ${result}`);
}

// ===== COMPARISON DEMO =====
function compareValues() {
    const value1 = document.getElementById('value1').value;
    const value2 = document.getElementById('value2').value;
    const output = document.getElementById('comparisonOutput');
    
    // Try to convert to numbers
    const num1 = Number(value1);
    const num2 = Number(value2);
    
    output.innerHTML = `
        <strong>Values:</strong>
        <pre>Value 1: "${value1}" (type: ${typeof value1})
Value 2: "${value2}" (type: ${typeof value2})</pre>
        
        <strong>Loose Equality (==):</strong>
        <pre>${value1} == ${value2} → ${value1 == value2}</pre>
        
        <strong>Strict Equality (===):</strong>
        <pre>${value1} === ${value2} → ${value1 === value2}</pre>
        
        <strong>Not Equal (!=):</strong>
        <pre>${value1} != ${value2} → ${value1 != value2}</pre>
        
        <strong>Strict Not Equal (!==):</strong>
        <pre>${value1} !== ${value2} → ${value1 !== value2}</pre>
        
        <strong>As Numbers:</strong>
        <pre>${num1} > ${num2} → ${num1 > num2}
${num1} < ${num2} → ${num1 < num2}
${num1} >= ${num2} → ${num1 >= num2}
${num1} <= ${num2} → ${num1 <= num2}</pre>
    `;
}

// ===== TYPE CONVERSION =====
function convertTypes() {
    const input = document.getElementById('convertInput').value;
    const output = document.getElementById('conversionOutput');
    
    // Convert to different types
    const asString = String(input);
    const asNumber = Number(input);
    const asBoolean = Boolean(input);
    
    output.innerHTML = `
        <strong>Original Value:</strong>
        <pre>"${input}"
Type: ${typeof input}</pre>
        
        <strong>To String:</strong>
        <pre>String("${input}") → "${asString}"
Type: ${typeof asString}</pre>
        
        <strong>To Number:</strong>
        <pre>Number("${input}") → ${asNumber}
Type: ${typeof asNumber}
Is NaN? ${isNaN(asNumber)}</pre>
        
        <strong>To Boolean:</strong>
        <pre>Boolean("${input}") → ${asBoolean}
Type: ${typeof asBoolean}</pre>
        
        <strong>Falsy Values:</strong>
        <pre>false, 0, "", null, undefined, NaN</pre>
    `;
    
    console.log('=== Type Conversion ===');
    console.log('Original:', input, typeof input);
    console.log('To String:', asString, typeof asString);
    console.log('To Number:', asNumber, typeof asNumber);
    console.log('To Boolean:', asBoolean, typeof asBoolean);
}

// ===== LOAD DEMO =====
console.log('🚀 JavaScript is loaded!');
console.log('Try clicking the demo buttons!');
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
    max-width: 900px;
    margin: 0 auto;
}

h1 {
    color: white;
    text-align: center;
    margin-bottom: 2rem;
    font-size: 2.5rem;
}

.demo-section,
.calculator {
    background: white;
    padding: 2rem;
    border-radius: 15px;
    margin-bottom: 2rem;
    box-shadow: 0 10px 30px rgba(0,0,0,0.2);
}

h2 {
    color: #2c3e50;
    margin-bottom: 1rem;
}

button {
    background-color: #667eea;
    color: white;
    border: none;
    padding: 0.75rem 2rem;
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
    margin-top: 1rem;
    padding: 1rem;
    background: #f8f9fa;
    border-radius: 8px;
    border-left: 4px solid #667eea;
}

.output pre {
    background: #2c3e50;
    color: #fff;
    padding: 1rem;
    border-radius: 5px;
    overflow-x: auto;
    margin: 0.5rem 0;
}

.output table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 1rem;
}

.output th,
.output td {
    padding: 0.75rem;
    text-align: left;
    border-bottom: 1px solid #ddd;
}

.output th {
    background-color: #667eea;
    color: white;
}

.calc-inputs {
    display: flex;
    gap: 1rem;
    margin-bottom: 1rem;
}

.calc-inputs input,
.calc-inputs select {
    flex: 1;
    padding: 0.75rem;
    border: 2px solid #ddd;
    border-radius: 8px;
    font-size: 1rem;
}

.btn-calculate {
    width: 100%;
}

.result {
    margin-top: 1rem;
}

.calculation {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    padding: 2rem;
    border-radius: 10px;
    color: white;
    text-align: center;
}

.operation {
    font-size: 1.5rem;
    margin-bottom: 0.5rem;
}

.answer {
    font-size: 2.5rem;
    font-weight: bold;
}

.error {
    background-color: #fee;
    color: #c00;
    padding: 1rem;
    border-radius: 8px;
    border-left: 4px solid #c00;
}

.comparison-inputs {
    display: flex;
    gap: 1rem;
    margin-bottom: 1rem;
}

.comparison-inputs input,
#convertInput {
    flex: 1;
    padding: 0.75rem;
    border: 2px solid #ddd;
    border-radius: 8px;
    font-size: 1rem;
}
```

---

## 📖 Key Concepts

### console.log()
Your best debugging tool!
```javascript
console.log('Hello!');
console.log('Value:', someVariable);
console.log('Multiple', 'values', 123, true);
```

### Template Literals
```javascript
const name = 'John';
const age = 25;

// Old way
console.log('Name: ' + name + ', Age: ' + age);

// Modern way (template literal)
console.log(`Name: ${name}, Age: ${age}`);
```

### Type Conversion
```javascript
// String to Number
let str = '42';
let num = Number(str);  // 42
let num2 = parseInt(str);  // 42
let num3 = parseFloat('3.14');  // 3.14

// Number to String
let n = 42;
let s = String(n);  // '42'
let s2 = n.toString();  // '42'

// To Boolean
Boolean(1);  // true
Boolean(0);  // false
Boolean('hello');  // true
Boolean('');  // false
```

---

## ✅ Self-Assessment

- [ ] Used let, const, and demonstrated var
- [ ] Showed all primitive data types
- [ ] Implemented arithmetic operations
- [ ] Demonstrated comparison operators
- [ ] Used logical operators
- [ ] String concatenation and template literals
- [ ] typeof operator used
- [ ] Type conversion demonstrated
- [ ] Console.log throughout
- [ ] Interactive calculator works

---

## 🐛 Common Mistakes

**1. Using var instead of let/const**
```javascript
// ❌ Don't
var x = 10;

// ✅ Do
let x = 10;
const PI = 3.14;
```

**2. Using == instead of ===**
```javascript
// ❌ Confusing
5 == '5'  // true (type coercion)

// ✅ Clear
5 === '5'  // false (strict)
```

**3. Forgetting to convert input values**
```javascript
// ❌ Wrong - strings concatenate
let result = '5' + '3';  // '53'

// ✅ Correct - convert to numbers
let result = Number('5') + Number('3');  // 8
```

---

## 💡 Tips

1. **Always use const** unless you need to reassign
2. **Always use ===** for comparisons
3. **console.log everything** when debugging
4. **Check types** with typeof
5. **Convert input values** - HTML inputs are always strings!

---

**Next**: [Assignment 2: Functions & Scope](../assignment-02-functions-scope/ASSIGNMENT_2_GUIDE.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

