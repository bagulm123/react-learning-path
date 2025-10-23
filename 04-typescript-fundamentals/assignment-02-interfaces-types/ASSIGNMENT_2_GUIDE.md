# Assignment 2: Interfaces & Type Aliases - Structuring Complex Types

**By Mahendra Bagul**

Interfaces and type aliases let you define custom types for complex data structures. Essential for React components! 📋

---

## 📚 What You'll Learn

- ✅ Interfaces
- ✅ Type aliases
- ✅ Optional properties
- ✅ Readonly properties
- ✅ Extending interfaces
- ✅ Interface vs Type
- ✅ Index signatures
- ✅ Function types in interfaces
- ✅ Intersection types
- ✅ Type composition

---

## 🎯 Assignment Objectives

Create a **User Management System** with complex type definitions and validation.

**Difficulty**: ⭐⭐⭐☆☆  
**Time**: 5-6 hours  
**Prerequisites**: TypeScript Assignment 1 completed

---

## 📋 Requirements

### Must Have
1. ✅ Interface definitions
2. ✅ Type aliases
3. ✅ Optional properties
4. ✅ Readonly properties
5. ✅ Interface extending
6. ✅ Intersection types
7. ✅ Function type definitions
8. ✅ Index signatures
9. ✅ Type guards
10. ✅ Full CRUD with types

---

## 💻 Complete Implementation

### src/types.ts
```typescript
// ===== BASIC INTERFACE =====
interface User {
    id: number;
    name: string;
    email: string;
    age: number;
}

// ===== OPTIONAL PROPERTIES =====
interface UserProfile {
    id: number;
    name: string;
    email: string;
    age?: number;              // Optional
    phone?: string;            // Optional
    address?: string;          // Optional
}

// ===== READONLY PROPERTIES =====
interface Config {
    readonly apiKey: string;
    readonly baseUrl: string;
    timeout: number;           // Can be modified
}

// ===== EXTENDING INTERFACES =====
interface Person {
    name: string;
    age: number;
}

interface Employee extends Person {
    employeeId: number;
    department: string;
    salary: number;
}

// ===== TYPE ALIASES =====
type ID = string | number;
type Status = "active" | "inactive" | "pending";
type Coordinate = [number, number];

// Complex type alias
type ApiResponse<T> = {
    data: T;
    status: number;
    message: string;
};

// ===== FUNCTION TYPES =====
interface Calculator {
    add: (a: number, b: number) => number;
    subtract: (a: number, b: number) => number;
}

// Type alias for function
type ValidatorFn = (value: string) => boolean;

// ===== INDEX SIGNATURES =====
interface Dictionary {
    [key: string]: string;
}

interface NumberDictionary {
    [index: string]: number;
}

// ===== INTERSECTION TYPES =====
type Admin = Person & {
    permissions: string[];
    isAdmin: true;
};

// Combining multiple types
type SuperUser = Employee & Admin & {
    level: number;
};

// ===== UNION TYPE WITH INTERFACES =====
interface Success {
    type: "success";
    data: any;
}

interface Error {
    type: "error";
    message: string;
}

type Result = Success | Error;

// ===== EXPORT TYPES =====
export type {
    User,
    UserProfile,
    Config,
    Person,
    Employee,
    ID,
    Status,
    ApiResponse,
    Calculator,
    ValidatorFn,
    Dictionary,
    Admin,
    SuperUser,
    Result
};
```

### src/app.ts
```typescript
import type {
    User,
    UserProfile,
    Employee,
    ID,
    Status,
    ApiResponse,
    Dictionary
} from './types';

// ===== USER DATA =====
let users: UserProfile[] = [];
let nextId: number = 1;

// ===== CREATE USER =====
function createUser(
    name: string,
    email: string,
    age?: number,
    phone?: string
): UserProfile {
    const user: UserProfile = {
        id: nextId++,
        name,
        email,
        age,
        phone
    };
    
    users.push(user);
    return user;
}

// ===== GET USER BY ID =====
function getUserById(id: ID): UserProfile | undefined {
    return users.find(u => u.id === id);
}

// ===== UPDATE USER =====
function updateUser(id: number, updates: Partial<UserProfile>): UserProfile | null {
    const user = getUserById(id);
    
    if (!user) return null;
    
    // Can't update id or readonly properties
    Object.assign(user, { ...updates, id: user.id });
    
    return user;
}

// ===== DELETE USER =====
function deleteUser(id: number): boolean {
    const index = users.findIndex(u => u.id === id);
    
    if (index === -1) return false;
    
    users.splice(index, 1);
    return true;
}

// ===== VALIDATOR FUNCTIONS =====
const validators: Dictionary = {
    email: "email",
    phone: "phone",
    age: "age"
};

function validateEmail(email: string): boolean {
    const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return regex.test(email);
}

function validatePhone(phone: string): boolean {
    const regex = /^\d{10}$/;
    return regex.test(phone);
}

// ===== TYPE GUARDS =====
function isEmployee(person: any): person is Employee {
    return (
        'employeeId' in person &&
        'department' in person &&
        'salary' in person
    );
}

// ===== DOM MANIPULATION =====
const userForm = document.getElementById('userForm') as HTMLFormElement;
const nameInput = document.getElementById('nameInput') as HTMLInputElement;
const emailInput = document.getElementById('emailInput') as HTMLInputElement;
const ageInput = document.getElementById('ageInput') as HTMLInputElement;
const phoneInput = document.getElementById('phoneInput') as HTMLInputElement;
const usersContainer = document.getElementById('usersContainer') as HTMLDivElement;
const typesOutput = document.getElementById('typesOutput') as HTMLDivElement;

// ===== HANDLE CREATE =====
userForm.addEventListener('submit', (e: Event) => {
    e.preventDefault();
    
    const name = nameInput.value.trim();
    const email = emailInput.value.trim();
    const age = ageInput.value ? parseInt(ageInput.value) : undefined;
    const phone = phoneInput.value.trim() || undefined;
    
    // Validate
    if (!name || !email) {
        showMessage("Name and email are required!", "error");
        return;
    }
    
    if (!validateEmail(email)) {
        showMessage("Invalid email format!", "error");
        return;
    }
    
    if (phone && !validatePhone(phone)) {
        showMessage("Phone must be 10 digits!", "error");
        return;
    }
    
    createUser(name, email, age, phone);
    renderUsers();
    userForm.reset();
    showMessage("User created successfully!", "success");
});

// ===== RENDER USERS =====
function renderUsers(): void {
    if (users.length === 0) {
        usersContainer.innerHTML = '<div class="no-data">No users yet</div>';
        return;
    }
    
    usersContainer.innerHTML = users.map(user => `
        <div class="user-card">
            <h3>${user.name}</h3>
            <p><strong>Email:</strong> ${user.email}</p>
            ${user.age ? `<p><strong>Age:</strong> ${user.age}</p>` : ''}
            ${user.phone ? `<p><strong>Phone:</strong> ${user.phone}</p>` : ''}
            <div class="user-actions">
                <button onclick="editUser(${user.id})">Edit</button>
                <button onclick="deleteUserById(${user.id})" class="delete-btn">Delete</button>
            </div>
        </div>
    `).join('');
}

// ===== GLOBAL FUNCTIONS =====
(window as any).deleteUserById = (id: number): void => {
    if (confirm('Delete this user?')) {
        deleteUser(id);
        renderUsers();
        showMessage("User deleted!", "success");
    }
};

(window as any).editUser = (id: number): void => {
    const user = getUserById(id);
    if (user) {
        nameInput.value = user.name;
        emailInput.value = user.email;
        ageInput.value = user.age?.toString() || '';
        phoneInput.value = user.phone || '';
        
        deleteUser(id);
        renderUsers();
    }
};

// ===== TYPE DEMOS =====
(window as any).demoInterfaces = (): void => {
    typesOutput.innerHTML = `
        <h4>Interface Definition</h4>
        <pre>interface UserProfile {
    id: number;
    name: string;
    email: string;
    age?: number;              // Optional
    phone?: string;            // Optional
}</pre>
        
        <h4>Using the Interface</h4>
        <pre>const user: UserProfile = {
    id: 1,
    name: "John Doe",
    email: "john@example.com",
    // age and phone are optional
};</pre>
    `;
};

(window as any).demoTypeAliases = (): void => {
    typesOutput.innerHTML = `
        <h4>Type Aliases</h4>
        <pre>type ID = string | number;
type Status = "active" | "inactive" | "pending";

type ApiResponse<T> = {
    data: T;
    status: number;
    message: string;
};</pre>
        
        <h4>Using Type Aliases</h4>
        <pre>let userId: ID = 123;
userId = "ABC123";  // Also valid

let status: Status = "active";

type UserResponse = ApiResponse<User>;
const response: UserResponse = {
    data: { id: 1, name: "John", email: "john@example.com" },
    status: 200,
    message: "Success"
};</pre>
    `;
};

(window as any).demoExtending = (): void => {
    typesOutput.innerHTML = `
        <h4>Extending Interfaces</h4>
        <pre>interface Person {
    name: string;
    age: number;
}

interface Employee extends Person {
    employeeId: number;
    department: string;
    salary: number;
}</pre>
        
        <h4>Using Extended Interface</h4>
        <pre>const employee: Employee = {
    // From Person
    name: "Alice",
    age: 30,
    
    // From Employee
    employeeId: 101,
    department: "Engineering",
    salary: 100000
};</pre>
        
        <h4>Intersection Types</h4>
        <pre>type Admin = Person & {
    permissions: string[];
    isAdmin: true;
};

const admin: Admin = {
    name: "Bob",
    age: 35,
    permissions: ["read", "write", "delete"],
    isAdmin: true
};</pre>
    `;
};

(window as any).demoReadonly = (): void => {
    typesOutput.innerHTML = `
        <h4>Readonly Properties</h4>
        <pre>interface Config {
    readonly apiKey: string;
    readonly baseUrl: string;
    timeout: number;
}

const config: Config = {
    apiKey: "abc123",
    baseUrl: "https://api.example.com",
    timeout: 5000
};

// This works
config.timeout = 10000;

// This causes an error
// config.apiKey = "new-key";  // Error!
// config.baseUrl = "new-url";  // Error!</pre>
    `;
};

// ===== MESSAGE =====
function showMessage(message: string, type: "success" | "error"): void {
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

console.log("✅ TypeScript app with interfaces loaded!");
```

---

## 📖 Key Concepts

### Interface vs Type
```typescript
// Interface
interface User {
    name: string;
}

// Type Alias
type User = {
    name: string;
};

// Use interface for objects, type for unions/primitives
type ID = string | number;  // Can't do this with interface
```

### Partial and Required
```typescript
// Make all properties optional
function updateUser(id: number, updates: Partial<User>) {
    // ...
}

// Make all properties required
type RequiredUser = Required<UserProfile>;
```

---

## ✅ Self-Assessment

- [ ] Interfaces defined
- [ ] Type aliases created
- [ ] Optional properties used
- [ ] Readonly properties demonstrated
- [ ] Interfaces extended
- [ ] Intersection types used
- [ ] Function types defined
- [ ] Type guards implemented
- [ ] User CRUD works
- [ ] All types compile correctly

---

**Next**: [Assignment 3: Functions & Generics](../assignment-03-functions-generics/ASSIGNMENT_3_GUIDE.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

