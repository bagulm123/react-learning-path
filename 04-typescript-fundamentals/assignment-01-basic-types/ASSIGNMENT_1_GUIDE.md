# Assignment 1: TypeScript Basics & Types - Adding Safety to JavaScript

**By Mahendra Bagul**

Welcome to TypeScript! Think of it as JavaScript with superpowers - catching errors before they happen. This is what professional React developers use! 💪

---

## 📚 What You'll Learn

- ✅ What is TypeScript and why use it
- ✅ Basic types (string, number, boolean, any, unknown)
- ✅ Arrays and tuples
- ✅ Type inference
- ✅ Type annotations
- ✅ Union types
- ✅ Literal types
- ✅ Type assertions
- ✅ Setting up TypeScript
- ✅ Compiling TypeScript to JavaScript

---

## 🎯 Assignment Objectives

Create a **Type-Safe Calculator** that demonstrates all basic TypeScript types.

**Difficulty**: ⭐⭐☆☆☆  
**Time**: 4-5 hours  
**Prerequisites**: JavaScript phase completed

---

## 📋 Requirements

### Must Have
1. ✅ TypeScript configuration (tsconfig.json)
2. ✅ Basic types demonstrated
3. ✅ Type annotations on variables
4. ✅ Type annotations on functions
5. ✅ Union types usage
6. ✅ Literal types
7. ✅ Arrays and tuples
8. ✅ Type inference examples
9. ✅ Compilation to JavaScript
10. ✅ Interactive calculator

---

## 🚀 Setup

### Install TypeScript
```bash
# Install TypeScript globally
npm install -g typescript

# Check version
tsc --version

# Initialize TypeScript config
tsc --init
```

### Project Structure
```
assignment-01-basic-types/
├── src/
│   ├── index.html
│   ├── app.ts          # TypeScript source
│   └── styles.css
├── dist/
│   └── app.js          # Compiled JavaScript
├── tsconfig.json
└── package.json
```

---

## 💻 Complete Implementation

### tsconfig.json
```json
{
  "compilerOptions": {
    "target": "ES2020",
    "module": "ESNext",
    "lib": ["ES2020", "DOM"],
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true,
    "moduleResolution": "node"
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules"]
}
```

### src/app.ts
```typescript
// ===== BASIC TYPES =====

// String
let username: string = "John Doe";
let greeting: string = `Hello, ${username}!`;

// Number
let age: number = 25;
let price: number = 19.99;
let binary: number = 0b1010;  // 10 in decimal
let hex: number = 0xf00d;

// Boolean
let isActive: boolean = true;
let hasPermission: boolean = false;

// Any (avoid when possible)
let anything: any = "hello";
anything = 42;
anything = true;

// Unknown (safer than any)
let userInput: unknown;
userInput = "test";
userInput = 123;

// if (typeof userInput === "string") {
//     console.log(userInput.toUpperCase());
// }

// Void (for functions that don't return)
function logMessage(message: string): void {
    console.log(message);
}

// Null and Undefined
let nothing: null = null;
let notDefined: undefined = undefined;

// ===== ARRAYS =====

// Array of numbers
let numbers: number[] = [1, 2, 3, 4, 5];
let alsoNumbers: Array<number> = [6, 7, 8, 9, 10];

// Array of strings
let fruits: string[] = ["apple", "banana", "orange"];

// Mixed array (not recommended)
let mixed: (string | number)[] = ["hello", 42, "world"];

// ===== TUPLES =====

// Fixed length and types
let person: [string, number] = ["John", 30];
let coordinate: [number, number] = [10, 20];

// Named tuple
let student: [name: string, age: number, grade: string] = ["Alice", 20, "A"];

// ===== UNION TYPES =====

// Variable can be one of multiple types
let id: string | number;
id = "ABC123";
id = 456;

function printId(id: string | number): void {
    if (typeof id === "string") {
        console.log(`ID is: ${id.toUpperCase()}`);
    } else {
        console.log(`ID is: ${id * 2}`);
    }
}

// ===== LITERAL TYPES =====

// Only specific values allowed
let direction: "north" | "south" | "east" | "west";
direction = "north";
// direction = "up";  // Error!

type Status = "success" | "error" | "pending";
let requestStatus: Status = "pending";

// ===== TYPE INFERENCE =====

// TypeScript infers the type
let inferredString = "hello";  // inferred as string
let inferredNumber = 42;       // inferred as number

// ===== TYPE ASSERTIONS =====

// Tell TypeScript you know better
let someValue: unknown = "this is a string";
let strLength: number = (someValue as string).length;

// ===== CALCULATOR FUNCTIONS =====

function add(a: number, b: number): number {
    return a + b;
}

function subtract(a: number, b: number): number {
    return a - b;
}

function multiply(a: number, b: number): number {
    return a * b;
}

function divide(a: number, b: number): number {
    if (b === 0) {
        throw new Error("Cannot divide by zero!");
    }
    return a / b;
}

// Function with union type parameter
function formatResult(result: number | string): string {
    if (typeof result === "number") {
        return `Result: ${result.toFixed(2)}`;
    }
    return `Result: ${result}`;
}

// ===== DOM MANIPULATION =====

// DOM elements with type assertions
const calcNum1 = document.getElementById('calcNum1') as HTMLInputElement;
const calcNum2 = document.getElementById('calcNum2') as HTMLInputElement;
const calcResult = document.getElementById('calcResult') as HTMLDivElement;
const typeDemoOutput = document.getElementById('typeDemoOutput') as HTMLDivElement;

// Calculator functions with proper types
function performAdd(): void {
    const num1: number = parseFloat(calcNum1.value);
    const num2: number = parseFloat(calcNum2.value);
    
    if (isNaN(num1) || isNaN(num2)) {
        showResult("Please enter valid numbers!", "error");
        return;
    }
    
    const result: number = add(num1, num2);
    showResult(`${num1} + ${num2} = ${result}`, "success");
}

function performSubtract(): void {
    const num1: number = parseFloat(calcNum1.value);
    const num2: number = parseFloat(calcNum2.value);
    
    if (isNaN(num1) || isNaN(num2)) {
        showResult("Please enter valid numbers!", "error");
        return;
    }
    
    const result: number = subtract(num1, num2);
    showResult(`${num1} - ${num2} = ${result}`, "success");
}

function performMultiply(): void {
    const num1: number = parseFloat(calcNum1.value);
    const num2: number = parseFloat(calcNum2.value);
    
    if (isNaN(num1) || isNaN(num2)) {
        showResult("Please enter valid numbers!", "error");
        return;
    }
    
    const result: number = multiply(num1, num2);
    showResult(`${num1} × ${num2} = ${result}`, "success");
}

function performDivide(): void {
    const num1: number = parseFloat(calcNum1.value);
    const num2: number = parseFloat(calcNum2.value);
    
    if (isNaN(num1) || isNaN(num2)) {
        showResult("Please enter valid numbers!", "error");
        return;
    }
    
    try {
        const result: number = divide(num1, num2);
        showResult(`${num1} ÷ ${num2} = ${result}`, "success");
    } catch (error) {
        if (error instanceof Error) {
            showResult(error.message, "error");
        }
    }
}

function showResult(message: string, type: "success" | "error"): void {
    calcResult.innerHTML = `
        <div class="${type}-box">
            ${message}
        </div>
    `;
}

// ===== TYPE DEMOS =====

function demoBasicTypes(): void {
    const output: string = `
        <h4>Basic Types</h4>
        <pre>let username: string = "John Doe";
let age: number = 25;
let isActive: boolean = true;

// Inferred types
let inferredStr = "hello";  // string
let inferredNum = 42;       // number</pre>
        
        <h4>Arrays</h4>
        <pre>let numbers: number[] = [1, 2, 3];
let fruits: string[] = ["apple", "banana"];</pre>
        
        <h4>Tuples</h4>
        <pre>let person: [string, number] = ["John", 30];
let coordinate: [number, number] = [10, 20];</pre>
    `;
    
    typeDemoOutput.innerHTML = output;
}

function demoUnionTypes(): void {
    const output: string = `
        <h4>Union Types</h4>
        <pre>// Variable can be multiple types
let id: string | number;
id = "ABC123";  // ✅ Valid
id = 456;       // ✅ Valid
// id = true;   // ❌ Error!</pre>
        
        <h4>Type Guards</h4>
        <pre>function printId(id: string | number) {
    if (typeof id === "string") {
        console.log(id.toUpperCase());
    } else {
        console.log(id * 2);
    }
}</pre>
    `;
    
    typeDemoOutput.innerHTML = output;
}

function demoLiteralTypes(): void {
    const output: string = `
        <h4>Literal Types</h4>
        <pre>// Only specific values allowed
let direction: "north" | "south" | "east" | "west";
direction = "north";  // ✅ Valid
// direction = "up";  // ❌ Error!

type Status = "success" | "error" | "pending";
let status: Status = "pending";</pre>
        
        <h4>Literal Type Benefits</h4>
        <ul>
            <li>✅ Prevents typos</li>
            <li>✅ Clear API contracts</li>
            <li>✅ Better autocomplete</li>
        </ul>
    `;
    
    typeDemoOutput.innerHTML = output;
}

// Make functions globally available
(window as any).performAdd = performAdd;
(window as any).performSubtract = performSubtract;
(window as any).performMultiply = performMultiply;
(window as any).performDivide = performDivide;
(window as any).demoBasicTypes = demoBasicTypes;
(window as any).demoUnionTypes = demoUnionTypes;
(window as any).demoLiteralTypes = demoLiteralTypes;

console.log("✅ TypeScript app loaded!");
console.log("Try the calculator and type demos!");
```

### src/index.html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TypeScript Basics</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>🔷 TypeScript Basics</h1>
        
        <!-- Calculator -->
        <section class="demo-section">
            <h2>Type-Safe Calculator</h2>
            <div class="calc-inputs">
                <input type="number" id="calcNum1" placeholder="Number 1">
                <input type="number" id="calcNum2" placeholder="Number 2">
            </div>
            <div class="button-group">
                <button onclick="performAdd()">Add (+)</button>
                <button onclick="performSubtract()">Subtract (-)</button>
                <button onclick="performMultiply()">Multiply (×)</button>
                <button onclick="performDivide()">Divide (÷)</button>
            </div>
            <div id="calcResult"></div>
        </section>
        
        <!-- Type Demos -->
        <section class="demo-section">
            <h2>Type Demos</h2>
            <div class="button-group">
                <button onclick="demoBasicTypes()">Basic Types</button>
                <button onclick="demoUnionTypes()">Union Types</button>
                <button onclick="demoLiteralTypes()">Literal Types</button>
            </div>
            <div id="typeDemoOutput" class="output"></div>
        </section>
        
        <!-- Why TypeScript -->
        <section class="demo-section">
            <h2>Why TypeScript?</h2>
            <div class="benefits">
                <div class="benefit-card">
                    <h3>🛡️ Type Safety</h3>
                    <p>Catch errors at compile time, not runtime</p>
                </div>
                <div class="benefit-card">
                    <h3>📝 Better Documentation</h3>
                    <p>Types serve as inline documentation</p>
                </div>
                <div class="benefit-card">
                    <h3>🚀 Better IDE Support</h3>
                    <p>Autocomplete and IntelliSense</p>
                </div>
                <div class="benefit-card">
                    <h3>🔄 Easier Refactoring</h3>
                    <p>Rename and refactor with confidence</p>
                </div>
            </div>
        </section>
    </div>
    
    <script src="../dist/app.js"></script>
</body>
</html>
```

### src/styles.css
```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background: linear-gradient(135deg, #3178c6 0%, #235a97 100%);
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

.calc-inputs {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
    margin-bottom: 1rem;
}

input {
    padding: 0.75rem;
    border: 2px solid #ddd;
    border-radius: 8px;
    font-size: 1rem;
}

.button-group {
    display: flex;
    gap: 0.5rem;
    flex-wrap: wrap;
    margin-bottom: 1rem;
}

button {
    flex: 1;
    background-color: #3178c6;
    color: white;
    border: none;
    padding: 0.75rem 1.5rem;
    border-radius: 8px;
    cursor: pointer;
    font-size: 1rem;
    transition: all 0.3s;
}

button:hover {
    background-color: #235a97;
    transform: translateY(-2px);
}

.success-box {
    background: #d4edda;
    color: #155724;
    padding: 1.5rem;
    border-radius: 10px;
    border-left: 4px solid #28a745;
    font-size: 1.2rem;
    text-align: center;
}

.error-box {
    background: #f8d7da;
    color: #721c24;
    padding: 1.5rem;
    border-radius: 10px;
    border-left: 4px solid #dc3545;
    text-align: center;
}

.output {
    margin-top: 1.5rem;
}

.output h4 {
    color: #3178c6;
    margin: 1.5rem 0 0.75rem 0;
}

.output h4:first-child {
    margin-top: 0;
}

.output pre {
    background: #2c3e50;
    color: #fff;
    padding: 1rem;
    border-radius: 8px;
    overflow-x: auto;
    margin: 0.75rem 0;
}

.output ul {
    list-style-position: inside;
    color: #666;
}

.output li {
    margin: 0.5rem 0;
}

.benefits {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 1.5rem;
}

.benefit-card {
    background: linear-gradient(135deg, #3178c6 0%, #235a97 100%);
    color: white;
    padding: 1.5rem;
    border-radius: 10px;
    text-align: center;
}

.benefit-card h3 {
    margin-bottom: 0.75rem;
}

.benefit-card p {
    opacity: 0.9;
}

@media (max-width: 768px) {
    .calc-inputs {
        grid-template-columns: 1fr;
    }
    
    .button-group {
        flex-direction: column;
    }
}
```

### package.json
```json
{
  "name": "typescript-basics",
  "version": "1.0.0",
  "scripts": {
    "build": "tsc",
    "watch": "tsc --watch",
    "start": "tsc && live-server src"
  },
  "devDependencies": {
    "typescript": "^5.0.0"
  }
}
```

---

## 📖 Key Concepts

### Type Annotations
```typescript
// Variables
let name: string = "John";
let age: number = 25;

// Functions
function greet(name: string): string {
    return `Hello, ${name}!`;
}
```

### Type Inference
```typescript
// TypeScript infers types automatically
let x = 10;  // inferred as number
let y = "hello";  // inferred as string
```

### Compiling
```bash
# Compile once
tsc

# Watch mode (auto-compile on save)
tsc --watch

# Compile specific file
tsc app.ts
```

---

## ✅ Self-Assessment

- [ ] TypeScript configured (tsconfig.json)
- [ ] Basic types used correctly
- [ ] Function type annotations
- [ ] Union types demonstrated
- [ ] Literal types used
- [ ] Arrays and tuples
- [ ] Type inference examples
- [ ] Successfully compiles to JavaScript
- [ ] Calculator works
- [ ] No type errors

---

**Next**: [Assignment 2: Interfaces & Type Aliases](../assignment-02-interfaces-types/ASSIGNMENT_2_GUIDE.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

