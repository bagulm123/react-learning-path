# Assignment 3: Arrays & Objects - Working with Data

**By Mahendra Bagul**

Arrays and objects are how we store and organize data in JavaScript. Master these, and you can build anything! This is crucial for React where you'll work with arrays constantly. 📦

---

## 📚 What You'll Learn

- ✅ Array creation and access
- ✅ Array methods (push, pop, shift, unshift, splice, slice)
- ✅ Array iteration (for, forEach, map, filter, reduce)
- ✅ Object creation and access
- ✅ Object methods
- ✅ Destructuring (arrays and objects)
- ✅ Spread operator
- ✅ Rest operator
- ✅ Working with nested data

---

## 🎯 Assignment Objectives

Create a **Student Management System** that demonstrates arrays, objects, and their methods.

**Difficulty**: ⭐⭐⭐☆☆  
**Time**: 5-6 hours  
**Prerequisites**: Assignments 1-2 completed

---

## 📋 Requirements

### Must Have
1. ✅ Array CRUD operations
2. ✅ Array methods demonstrated
3. ✅ Array iteration techniques
4. ✅ Object creation and manipulation
5. ✅ Object destructuring
6. ✅ Array destructuring
7. ✅ Spread operator usage
8. ✅ Filter, map, reduce examples
9. ✅ Nested data structures
10. ✅ Interactive student management UI

---

## 📚 Arrays

### Creating Arrays
```javascript
// Array literal (common)
const fruits = ['apple', 'banana', 'orange'];

// Array constructor
const numbers = new Array(1, 2, 3, 4, 5);

// Empty array
const empty = [];

// Mixed types (avoid in production)
const mixed = [1, 'hello', true, null];
```

### Accessing Elements
```javascript
const fruits = ['apple', 'banana', 'orange'];

console.log(fruits[0]);  // 'apple' (first)
console.log(fruits[1]);  // 'banana'
console.log(fruits[fruits.length - 1]);  // 'orange' (last)
```

### Array Methods
```javascript
const arr = [1, 2, 3];

// Add to end
arr.push(4);  // [1, 2, 3, 4]

// Remove from end
arr.pop();  // Returns 4, arr is [1, 2, 3]

// Add to beginning
arr.unshift(0);  // [0, 1, 2, 3]

// Remove from beginning
arr.shift();  // Returns 0, arr is [1, 2, 3]

// Find index
arr.indexOf(2);  // 1

// Check if includes
arr.includes(2);  // true

// Slice (doesn't modify original)
arr.slice(0, 2);  // [1, 2]

// Splice (modifies original)
arr.splice(1, 1);  // Removes 1 element at index 1
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
    <title>Student Management System</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>📚 Student Management System</h1>
        
        <!-- Add Student Form -->
        <section class="add-section">
            <h2>Add New Student</h2>
            <div class="form-group">
                <input type="text" id="studentName" placeholder="Student Name">
                <input type="number" id="studentAge" placeholder="Age">
                <input type="text" id="studentCourse" placeholder="Course">
                <input type="number" id="studentGrade" placeholder="Grade (0-100)" min="0" max="100">
                <button onclick="addStudent()">Add Student</button>
            </div>
        </section>
        
        <!-- Students List -->
        <section class="students-section">
            <h2>All Students (<span id="studentCount">0</span>)</h2>
            <div class="filter-controls">
                <input type="text" id="searchInput" placeholder="Search by name...">
                <select id="courseFilter">
                    <option value="">All Courses</option>
                    <option value="JavaScript">JavaScript</option>
                    <option value="React">React</option>
                    <option value="Node.js">Node.js</option>
                    <option value="Python">Python</option>
                </select>
                <button onclick="sortByName()">Sort by Name</button>
                <button onclick="sortByGrade()">Sort by Grade</button>
            </div>
            <div id="studentsList" class="students-grid"></div>
        </section>
        
        <!-- Statistics -->
        <section class="stats-section">
            <h2>Statistics</h2>
            <div class="stats-grid">
                <div class="stat-card">
                    <h3>Total Students</h3>
                    <p id="totalStudents" class="stat-value">0</p>
                </div>
                <div class="stat-card">
                    <h3>Average Grade</h3>
                    <p id="avgGrade" class="stat-value">0</p>
                </div>
                <div class="stat-card">
                    <h3>Highest Grade</h3>
                    <p id="maxGrade" class="stat-value">0</p>
                </div>
                <div class="stat-card">
                    <h3>Lowest Grade</h3>
                    <p id="minGrade" class="stat-value">0</p>
                </div>
            </div>
        </section>
        
        <!-- Array Methods Demo -->
        <section class="demo-section">
            <h2>Array Methods Demo</h2>
            <button onclick="demoArrayMethods()">Show Array Methods</button>
            <div id="arrayOutput" class="output"></div>
        </section>
        
        <!-- Object Methods Demo -->
        <section class="demo-section">
            <h2>Object Methods Demo</h2>
            <button onclick="demoObjectMethods()">Show Object Methods</button>
            <div id="objectOutput" class="output"></div>
        </section>
        
        <!-- Destructuring Demo -->
        <section class="demo-section">
            <h2>Destructuring Demo</h2>
            <button onclick="demoDestructuring()">Show Destructuring</button>
            <div id="destructureOutput" class="output"></div>
        </section>
    </div>
    
    <script src="script.js"></script>
</body>
</html>
```

### JavaScript (script.js)
```javascript
// ===== DATA STORAGE =====
let students = [];
let nextId = 1;

// ===== ADD STUDENT =====
function addStudent() {
    const name = document.getElementById('studentName').value.trim();
    const age = parseInt(document.getElementById('studentAge').value);
    const course = document.getElementById('studentCourse').value.trim();
    const grade = parseFloat(document.getElementById('studentGrade').value);
    
    // Validation
    if (!name || !age || !course || isNaN(grade)) {
        alert('Please fill all fields!');
        return;
    }
    
    if (grade < 0 || grade > 100) {
        alert('Grade must be between 0 and 100!');
        return;
    }
    
    // Create student object
    const student = {
        id: nextId++,
        name: name,
        age: age,
        course: course,
        grade: grade,
        enrolledDate: new Date().toLocaleDateString()
    };
    
    // Add to array
    students.push(student);
    
    console.log('Added student:', student);
    console.log('All students:', students);
    
    // Clear form
    document.getElementById('studentName').value = '';
    document.getElementById('studentAge').value = '';
    document.getElementById('studentCourse').value = '';
    document.getElementById('studentGrade').value = '';
    
    // Update UI
    renderStudents();
    updateStatistics();
}

// ===== RENDER STUDENTS =====
function renderStudents() {
    const container = document.getElementById('studentsList');
    const searchTerm = document.getElementById('searchInput').value.toLowerCase();
    const courseFilter = document.getElementById('courseFilter').value;
    
    // Filter students
    let filteredStudents = students.filter(student => {
        const matchesSearch = student.name.toLowerCase().includes(searchTerm);
        const matchesCourse = !courseFilter || student.course === courseFilter;
        return matchesSearch && matchesCourse;
    });
    
    // Update count
    document.getElementById('studentCount').textContent = filteredStudents.length;
    
    if (filteredStudents.length === 0) {
        container.innerHTML = '<p class="no-data">No students found</p>';
        return;
    }
    
    // Render students
    container.innerHTML = filteredStudents.map(student => `
        <div class="student-card ${getGradeClass(student.grade)}">
            <div class="student-header">
                <h3>${student.name}</h3>
                <button onclick="deleteStudent(${student.id})" class="delete-btn">×</button>
            </div>
            <p><strong>Age:</strong> ${student.age}</p>
            <p><strong>Course:</strong> ${student.course}</p>
            <p><strong>Grade:</strong> ${student.grade}/100</p>
            <p><strong>Enrolled:</strong> ${student.enrolledDate}</p>
            <div class="grade-badge">${getGradeLabel(student.grade)}</div>
        </div>
    `).join('');
}

// ===== DELETE STUDENT =====
function deleteStudent(id) {
    // Find index
    const index = students.findIndex(student => student.id === id);
    
    if (index !== -1) {
        const deleted = students.splice(index, 1)[0];
        console.log('Deleted student:', deleted);
        
        renderStudents();
        updateStatistics();
    }
}

// ===== SORTING =====
function sortByName() {
    students.sort((a, b) => a.name.localeCompare(b.name));
    renderStudents();
}

function sortByGrade() {
    students.sort((a, b) => b.grade - a.grade);  // Descending
    renderStudents();
}

// ===== STATISTICS =====
function updateStatistics() {
    const total = students.length;
    document.getElementById('totalStudents').textContent = total;
    
    if (total === 0) {
        document.getElementById('avgGrade').textContent = '0';
        document.getElementById('maxGrade').textContent = '0';
        document.getElementById('minGrade').textContent = '0';
        return;
    }
    
    // Calculate average using reduce
    const sum = students.reduce((acc, student) => acc + student.grade, 0);
    const average = (sum / total).toFixed(2);
    document.getElementById('avgGrade').textContent = average;
    
    // Find max and min
    const grades = students.map(student => student.grade);
    document.getElementById('maxGrade').textContent = Math.max(...grades);
    document.getElementById('minGrade').textContent = Math.min(...grades);
}

// ===== UTILITY FUNCTIONS =====
function getGradeClass(grade) {
    if (grade >= 90) return 'excellent';
    if (grade >= 75) return 'good';
    if (grade >= 60) return 'average';
    return 'poor';
}

function getGradeLabel(grade) {
    if (grade >= 90) return 'A - Excellent';
    if (grade >= 80) return 'B - Good';
    if (grade >= 70) return 'C - Average';
    if (grade >= 60) return 'D - Below Average';
    return 'F - Fail';
}

// ===== ARRAY METHODS DEMO =====
function demoArrayMethods() {
    const output = document.getElementById('arrayOutput');
    
    const numbers = [1, 2, 3, 4, 5];
    const fruits = ['apple', 'banana', 'orange'];
    
    output.innerHTML = `
        <div class="method-demo">
            <h4>Original Arrays</h4>
            <pre>numbers = ${JSON.stringify(numbers)}
fruits = ${JSON.stringify(fruits)}</pre>
            
            <h4>map() - Transform each element</h4>
            <pre>numbers.map(n => n * 2)
→ ${JSON.stringify(numbers.map(n => n * 2))}</pre>
            
            <h4>filter() - Keep elements that match</h4>
            <pre>numbers.filter(n => n > 2)
→ ${JSON.stringify(numbers.filter(n => n > 2))}</pre>
            
            <h4>reduce() - Reduce to single value</h4>
            <pre>numbers.reduce((sum, n) => sum + n, 0)
→ ${numbers.reduce((sum, n) => sum + n, 0)}</pre>
            
            <h4>find() - Find first match</h4>
            <pre>numbers.find(n => n > 3)
→ ${numbers.find(n => n > 3)}</pre>
            
            <h4>some() - Check if any match</h4>
            <pre>numbers.some(n => n > 4)
→ ${numbers.some(n => n > 4)}</pre>
            
            <h4>every() - Check if all match</h4>
            <pre>numbers.every(n => n > 0)
→ ${numbers.every(n => n > 0)}</pre>
            
            <h4>join() - Array to string</h4>
            <pre>fruits.join(', ')
→ "${fruits.join(', ')}"</pre>
            
            <h4>slice() - Extract portion (doesn't modify)</h4>
            <pre>fruits.slice(0, 2)
→ ${JSON.stringify(fruits.slice(0, 2))}
Original: ${JSON.stringify(fruits)}</pre>
        </div>
    `;
}

// ===== OBJECT METHODS DEMO =====
function demoObjectMethods() {
    const output = document.getElementById('objectOutput');
    
    const student = {
        name: 'John Doe',
        age: 22,
        course: 'JavaScript',
        grade: 85
    };
    
    output.innerHTML = `
        <div class="method-demo">
            <h4>Original Object</h4>
            <pre>${JSON.stringify(student, null, 2)}</pre>
            
            <h4>Object.keys() - Get all keys</h4>
            <pre>${JSON.stringify(Object.keys(student))}</pre>
            
            <h4>Object.values() - Get all values</h4>
            <pre>${JSON.stringify(Object.values(student))}</pre>
            
            <h4>Object.entries() - Get key-value pairs</h4>
            <pre>${JSON.stringify(Object.entries(student), null, 2)}</pre>
            
            <h4>Accessing Properties</h4>
            <pre>student.name → "${student.name}"
student['age'] → ${student['age']}</pre>
            
            <h4>Adding Properties</h4>
            <pre>student.email = 'john@example.com'
${JSON.stringify({...student, email: 'john@example.com'}, null, 2)}</pre>
            
            <h4>Deleting Properties</h4>
            <pre>delete student.age
// age would be removed</pre>
        </div>
    `;
}

// ===== DESTRUCTURING DEMO =====
function demoDestructuring() {
    const output = document.getElementById('destructureOutput');
    
    // Array destructuring
    const colors = ['red', 'green', 'blue', 'yellow'];
    const [first, second, ...rest] = colors;
    
    // Object destructuring
    const person = {
        name: 'Alice',
        age: 25,
        city: 'Mumbai',
        country: 'India'
    };
    const { name, age, ...address } = person;
    
    output.innerHTML = `
        <div class="method-demo">
            <h4>Array Destructuring</h4>
            <pre>const colors = ${JSON.stringify(colors)}

const [first, second, ...rest] = colors;

first → "${first}"
second → "${second}"
rest → ${JSON.stringify(rest)}</pre>
            
            <h4>Object Destructuring</h4>
            <pre>const person = ${JSON.stringify(person, null, 2)}

const { name, age, ...address } = person;

name → "${name}"
age → ${age}
address → ${JSON.stringify(address, null, 2)}</pre>
            
            <h4>Spread Operator</h4>
            <pre>const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const combined = [...arr1, ...arr2];
→ ${JSON.stringify([...[1, 2, 3], ...[4, 5, 6]])}</pre>
            
            <h4>Object Spread</h4>
            <pre>const obj1 = { a: 1, b: 2 };
const obj2 = { c: 3, d: 4 };
const merged = { ...obj1, ...obj2 };
→ ${JSON.stringify({...{a: 1, b: 2}, ...{c: 3, d: 4}})}</pre>
        </div>
    `;
}

// ===== EVENT LISTENERS =====
document.getElementById('searchInput').addEventListener('input', renderStudents);
document.getElementById('courseFilter').addEventListener('change', renderStudents);

// ===== INITIALIZE =====
console.log('✅ Student Management System loaded!');
updateStatistics();
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
    max-width: 1200px;
    margin: 0 auto;
}

h1 {
    color: white;
    text-align: center;
    margin-bottom: 2rem;
    font-size: 2.5rem;
}

section {
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

.form-group {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 1rem;
}

input, select {
    padding: 0.75rem;
    border: 2px solid #ddd;
    border-radius: 8px;
    font-size: 1rem;
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

.filter-controls {
    display: flex;
    gap: 1rem;
    margin-bottom: 1.5rem;
    flex-wrap: wrap;
}

.filter-controls input,
.filter-controls select {
    flex: 1;
    min-width: 200px;
}

.students-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 1.5rem;
}

.student-card {
    border: 2px solid;
    padding: 1.5rem;
    border-radius: 10px;
    transition: transform 0.3s;
}

.student-card:hover {
    transform: translateY(-5px);
}

.student-card.excellent {
    border-color: #28a745;
    background: #f0fff4;
}

.student-card.good {
    border-color: #17a2b8;
    background: #f0faff;
}

.student-card.average {
    border-color: #ffc107;
    background: #fffbf0;
}

.student-card.poor {
    border-color: #dc3545;
    background: #fff5f5;
}

.student-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 1rem;
}

.student-header h3 {
    color: #2c3e50;
    font-size: 1.2rem;
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
    padding: 0;
}

.delete-btn:hover {
    background: #c82333;
}

.student-card p {
    margin: 0.5rem 0;
    color: #555;
}

.grade-badge {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    padding: 0.5rem;
    border-radius: 5px;
    text-align: center;
    font-weight: bold;
    margin-top: 1rem;
}

.stats-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 1.5rem;
}

.stat-card {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    padding: 1.5rem;
    border-radius: 10px;
    text-align: center;
}

.stat-card h3 {
    font-size: 1rem;
    margin-bottom: 0.5rem;
}

.stat-value {
    font-size: 2.5rem;
    font-weight: bold;
}

.no-data {
    text-align: center;
    color: #999;
    padding: 2rem;
}

.output {
    margin-top: 1rem;
}

.method-demo {
    background: #f8f9fa;
    padding: 1.5rem;
    border-radius: 10px;
}

.method-demo h4 {
    color: #667eea;
    margin: 1.5rem 0 0.75rem 0;
}

.method-demo h4:first-child {
    margin-top: 0;
}

.method-demo pre {
    background: #2c3e50;
    color: #fff;
    padding: 1rem;
    border-radius: 5px;
    overflow-x: auto;
    font-size: 0.9rem;
}

@media (max-width: 768px) {
    .form-group {
        grid-template-columns: 1fr;
    }
    
    .filter-controls {
        flex-direction: column;
    }
    
    .students-grid {
        grid-template-columns: 1fr;
    }
}
```

---

## 📖 Key Concepts

### Map, Filter, Reduce
```javascript
const numbers = [1, 2, 3, 4, 5];

// map - transform each element
const doubled = numbers.map(n => n * 2);  // [2, 4, 6, 8, 10]

// filter - keep matching elements
const evens = numbers.filter(n => n % 2 === 0);  // [2, 4]

// reduce - reduce to single value
const sum = numbers.reduce((total, n) => total + n, 0);  // 15
```

### Destructuring
```javascript
// Array
const [a, b, ...rest] = [1, 2, 3, 4, 5];
// a = 1, b = 2, rest = [3, 4, 5]

// Object
const {name, age} = {name: 'John', age: 25, city: 'Mumbai'};
// name = 'John', age = 25
```

---

## ✅ Self-Assessment

- [ ] Array CRUD operations work
- [ ] Map, filter, reduce demonstrated
- [ ] Objects created and manipulated
- [ ] Destructuring used
- [ ] Spread operator demonstrated
- [ ] Student management works
- [ ] Sorting implemented
- [ ] Statistics calculated
- [ ] Search/filter works
- [ ] UI responsive

---

**Next**: [Assignment 4: DOM Manipulation](../assignment-04-dom-manipulation/ASSIGNMENT_4_GUIDE.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

