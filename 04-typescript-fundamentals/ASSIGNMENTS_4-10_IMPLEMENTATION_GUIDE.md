# TypeScript Assignments 4-10: Implementation Guide

**By Mahendra Bagul**

This guide provides complete implementation details for TypeScript assignments 4-10. Each assignment includes full code examples, project structure, and learning objectives.

---

## 📝 Assignment 4: Classes & OOP

### Project: Animal Management System

**File Structure:**
```
assignment-04-classes-oop/
├── src/
│   ├── Animal.ts
│   ├── Dog.ts
│   ├── Cat.ts
│   ├── Zoo.ts
│   ├── app.ts
│   ├── index.html
│   └── styles.css
├── dist/
└── tsconfig.json
```

**Complete Implementation:**

```typescript
// Animal.ts (Abstract Base Class)
abstract class Animal {
    protected name: string;
    protected age: number;
    
    constructor(name: string, age: number) {
        this.name = name;
        this.age = age;
    }
    
    abstract makeSound(): string;
    abstract getInfo(): string;
    
    getName(): string {
        return this.name;
    }
    
    getAge(): number {
        return this.age;
    }
}

// Dog.ts
class Dog extends Animal {
    private breed: string;
    
    constructor(name: string, age: number, breed: string) {
        super(name, age);
        this.breed = breed;
    }
    
    makeSound(): string {
        return "Woof! Woof!";
    }
    
    getInfo(): string {
        return `${this.name} is a ${this.age}-year-old ${this.breed}`;
    }
    
    fetch(): string {
        return `${this.name} is fetching the ball!`;
    }
}

// Cat.ts
class Cat extends Animal {
    private indoor: boolean;
    
    constructor(name: string, age: number, indoor: boolean = true) {
        super(name, age);
        this.indoor = indoor;
    }
    
    makeSound(): string {
        return "Meow!";
    }
    
    getInfo(): string {
        return `${this.name} is a ${this.age}-year-old ${this.indoor ? 'indoor' : 'outdoor'} cat`;
    }
    
    purr(): string {
        return `${this.name} is purring contentedly`;
    }
}

// Zoo.ts (Static Members)
class Zoo {
    private static instance: Zoo;
    private animals: Animal[] = [];
    private readonly name: string;
    
    private constructor(name: string) {
        this.name = name;
    }
    
    static getInstance(name: string = "My Zoo"): Zoo {
        if (!Zoo.instance) {
            Zoo.instance = new Zoo(name);
        }
        return Zoo.instance;
    }
    
    addAnimal(animal: Animal): void {
        this.animals.push(animal);
    }
    
    getAnimals(): Animal[] {
        return this.animals;
    }
    
    makeAllSounds(): string[] {
        return this.animals.map(animal => animal.makeSound());
    }
}
```

**Key Concepts:**
- Abstract classes and methods
- Inheritance with `extends`
- Access modifiers (public, private, protected)
- Static members and Singleton pattern
- Readonly properties

---

## 📝 Assignment 5: Advanced Types

### Project: Type Transformer Utility Library

**Complete Implementation:**

```typescript
// Mapped Types
type Readonly<T> = {
    readonly [P in keyof T]: T[P];
};

type Optional<T> = {
    [P in keyof T]?: T[P];
};

type Nullable<T> = {
    [P in keyof T]: T[P] | null;
};

// Conditional Types
type NonNullable<T> = T extends null | undefined ? never : T;

type Flatten<T> = T extends Array<infer U> ? U : T;

type ReturnTypeOf<T> = T extends (...args: any[]) => infer R ? R : never;

// Template Literal Types
type EventName = `on${Capitalize<string>}`;
type Direction = "north" | "south" | "east" | "west";
type CapitalizedDirection = Capitalize<Direction>;

// Index Types
function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
    return obj[key];
}

type Keys = keyof { name: string; age: number };  // "name" | "age"

// Practical Examples
interface User {
    id: number;
    name: string;
    email: string;
    age?: number;
}

type ReadonlyUser = Readonly<User>;
type PartialUser = Optional<User>;
type UserKeys = keyof User;

// Advanced Mapped Type
type DeepReadonly<T> = {
    readonly [P in keyof T]: T[P] extends object
        ? DeepReadonly<T[P]>
        : T[P];
};

// Conditional with Distribution
type ExtractStrings<T> = T extends string ? T : never;
type OnlyStrings = ExtractStrings<string | number | boolean>;  // string
```

**UI Demo:**
Create an interactive page showing how each type transformation works with real examples.

---

## 📝 Assignment 6: Modules & Namespaces

### Project: Math Library with Modules

**File Structure:**
```
assignment-06-modules/
├── src/
│   ├── math/
│   │   ├── basic.ts
│   │   ├── advanced.ts
│   │   └── index.ts
│   ├── utils/
│   │   ├── formatters.ts
│   │   └── validators.ts
│   ├── types/
│   │   └── index.d.ts
│   └── app.ts
```

**Complete Implementation:**

```typescript
// math/basic.ts
export function add(a: number, b: number): number {
    return a + b;
}

export function subtract(a: number, b: number): number {
    return a - b;
}

export default class Calculator {
    private memory: number = 0;
    
    add(n: number): void {
        this.memory += n;
    }
    
    getMemory(): number {
        return this.memory;
    }
}

// math/advanced.ts
export function power(base: number, exponent: number): number {
    return Math.pow(base, exponent);
}

export function sqrt(n: number): number {
    return Math.sqrt(n);
}

// math/index.ts (Barrel Export)
export * from './basic';
export * from './advanced';

// app.ts
import Calculator, { add, subtract, power } from './math';

const calc = new Calculator();
const result = add(5, 3);

// Namespace Example
namespace Validation {
    export interface StringValidator {
        isValid(s: string): boolean;
    }
    
    export class EmailValidator implements StringValidator {
        isValid(s: string): boolean {
            return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(s);
        }
    }
}

// Declaration File (types/index.d.ts)
declare module 'my-library' {
    export function doSomething(value: string): void;
}
```

---

## 📝 Assignment 7: Decorators

### Project: Logging & Validation Framework

**tsconfig.json Update:**
```json
{
  "compilerOptions": {
    "experimentalDecorators": true,
    "emitDecoratorMetadata": true
  }
}
```

**Complete Implementation:**

```typescript
// Class Decorator
function Component(constructor: Function) {
    console.log(`Component created: ${constructor.name}`);
}

// Method Decorator
function Log(target: any, propertyName: string, descriptor: PropertyDescriptor) {
    const originalMethod = descriptor.value;
    
    descriptor.value = function(...args: any[]) {
        console.log(`Calling ${propertyName} with`, args);
        const result = originalMethod.apply(this, args);
        console.log(`Result:`, result);
        return result;
    };
    
    return descriptor;
}

// Property Decorator
function Required(target: any, propertyName: string) {
    let value: any;
    
    const getter = () => value;
    const setter = (newValue: any) => {
        if (!newValue) {
            throw new Error(`${propertyName} is required`);
        }
        value = newValue;
    };
    
    Object.defineProperty(target, propertyName, {
        get: getter,
        set: setter
    });
}

// Parameter Decorator
function LogParameter(target: any, propertyName: string, parameterIndex: number) {
    console.log(`Parameter at index ${parameterIndex} in ${propertyName}`);
}

// Decorator Factory
function MinLength(length: number) {
    return function(target: any, propertyName: string) {
        let value: string;
        
        const setter = (newValue: string) => {
            if (newValue.length < length) {
                throw new Error(`${propertyName} must be at least ${length} characters`);
            }
            value = newValue;
        };
        
        Object.defineProperty(target, propertyName, {
            set: setter,
            get: () => value
        });
    };
}

// Usage
@Component
class UserService {
    @Required
    name: string;
    
    @MinLength(8)
    password: string;
    
    @Log
    login(@LogParameter username: string, password: string): boolean {
        return username === "admin" && password === "password";
    }
}
```

---

## 📝 Assignment 8: Type Guards & Narrowing

### Project: Validation & Type Checking System

**Complete Implementation:**

```typescript
// typeof Guards
function processValue(value: string | number) {
    if (typeof value === "string") {
        return value.toUpperCase();  // string methods
    } else {
        return value.toFixed(2);  // number methods
    }
}

// instanceof Guards
class Dog {
    bark() { console.log("Woof!"); }
}

class Cat {
    meow() { console.log("Meow!"); }
}

function makeSound(animal: Dog | Cat) {
    if (animal instanceof Dog) {
        animal.bark();
    } else {
        animal.meow();
    }
}

// Custom Type Guards
interface Fish {
    swim: () => void;
}

interface Bird {
    fly: () => void;
}

function isFish(pet: Fish | Bird): pet is Fish {
    return (pet as Fish).swim !== undefined;
}

function move(pet: Fish | Bird) {
    if (isFish(pet)) {
        pet.swim();
    } else {
        pet.fly();
    }
}

// Discriminated Unions
type Shape =
    | { kind: 'circle'; radius: number }
    | { kind: 'square'; size: number }
    | { kind: 'rectangle'; width: number; height: number };

function getArea(shape: Shape): number {
    switch (shape.kind) {
        case 'circle':
            return Math.PI * shape.radius ** 2;
        case 'square':
            return shape.size ** 2;
        case 'rectangle':
            return shape.width * shape.height;
    }
}

// never and Exhaustiveness Checking
function assertNever(x: never): never {
    throw new Error(`Unexpected value: ${x}`);
}

function handleShape(shape: Shape): number {
    switch (shape.kind) {
        case 'circle':
            return Math.PI * shape.radius ** 2;
        case 'square':
            return shape.size ** 2;
        case 'rectangle':
            return shape.width * shape.height;
        default:
            return assertNever(shape);  // Compile error if we miss a case
    }
}

// Truthiness Narrowing
function processString(str: string | null | undefined) {
    if (str) {
        return str.trim();  // str is string here
    }
    return "";
}

// Equality Narrowing
function example(x: string | number, y: string | boolean) {
    if (x === y) {
        // x and y must both be string
        x.toUpperCase();
        y.toUpperCase();
    }
}
```

---

## 📝 Assignment 9: Utility Types

### Project: Type Utility Showcase & Library

**Complete Implementation:**

```typescript
interface User {
    id: number;
    name: string;
    email: string;
    age: number;
    phone?: string;
}

// ===== BUILT-IN UTILITY TYPES =====

// Partial - Make all properties optional
type PartialUser = Partial<User>;
// { id?: number; name?: string; email?: string; age?: number; phone?: string; }

function updateUser(user: User, updates: Partial<User>): User {
    return { ...user, ...updates };
}

// Required - Make all properties required
type RequiredUser = Required<PartialUser>;

// Readonly - Make all properties readonly
type ReadonlyUser = Readonly<User>;

// Pick - Select specific properties
type UserPreview = Pick<User, 'id' | 'name'>;
// { id: number; name: string; }

// Omit - Exclude specific properties
type UserWithoutAge = Omit<User, 'age'>;
// { id: number; name: string; email: string; phone?: string; }

// Record - Create object type with specific keys
type UserRoles = Record<'admin' | 'user' | 'guest', boolean>;
// { admin: boolean; user: boolean; guest: boolean; }

// Exclude - Remove types from union
type Status = 'pending' | 'active' | 'inactive' | 'deleted';
type ActiveStatus = Exclude<Status, 'deleted'>;
// 'pending' | 'active' | 'inactive'

// Extract - Keep only specified types from union
type InactiveStatus = Extract<Status, 'inactive' | 'deleted'>;
// 'inactive' | 'deleted'

// NonNullable - Remove null and undefined
type MaybeString = string | null | undefined;
type DefiniteString = NonNullable<MaybeString>;
// string

// ReturnType - Get return type of function
function getUser(): User {
    return { id: 1, name: "John", email: "john@example.com", age: 30 };
}
type UserReturnType = ReturnType<typeof getUser>;
// User

// Parameters - Get parameter types of function
function createUser(name: string, age: number): User {
    return { id: 1, name, email: "", age };
}
type CreateUserParams = Parameters<typeof createUser>;
// [name: string, age: number]

// Awaited - Get type from Promise
type UserPromise = Promise<User>;
type ResolvedUser = Awaited<UserPromise>;
// User

// ===== CUSTOM UTILITY TYPES =====

// DeepReadonly - Recursively make readonly
type DeepReadonly<T> = {
    readonly [P in keyof T]: T[P] extends object
        ? DeepReadonly<T[P]>
        : T[P];
};

// DeepPartial - Recursively make partial
type DeepPartial<T> = {
    [P in keyof T]?: T[P] extends object
        ? DeepPartial<T[P]>
        : T[P];
};

// Mutable - Remove readonly
type Mutable<T> = {
    -readonly [P in keyof T]: T[P];
};

// RequireAtLeastOne - Require at least one property
type RequireAtLeastOne<T, Keys extends keyof T = keyof T> =
    Pick<T, Exclude<keyof T, Keys>>
    & {
        [K in Keys]-?: Required<Pick<T, K>> & Partial<Pick<T, Exclude<Keys, K>>>
    }[Keys];

// RequireOnlyOne - Require exactly one property
type RequireOnlyOne<T, Keys extends keyof T = keyof T> =
    Pick<T, Exclude<keyof T, Keys>>
    & {
        [K in Keys]-?:
            Required<Pick<T, K>>
            & Partial<Record<Exclude<Keys, K>, undefined>>
    }[Keys];

// ===== PRACTICAL EXAMPLES =====

// API Response Type
type ApiResponse<T> = {
    data: T;
    status: number;
    message: string;
};

type UserResponse = ApiResponse<User>;

// Form State Type
type FormState<T> = {
    values: T;
    errors: Partial<Record<keyof T, string>>;
    touched: Partial<Record<keyof T, boolean>>;
    isSubmitting: boolean;
};

type UserFormState = FormState<User>;

// Async State Type
type AsyncState<T> = 
    | { status: 'idle' }
    | { status: 'loading' }
    | { status: 'success'; data: T }
    | { status: 'error'; error: Error };

type UserAsyncState = AsyncState<User>;
```

---

## 📝 Assignment 10: React with TypeScript

### Project: Typed React Todo App

**Complete Implementation:**

```typescript
// types.ts
export interface Todo {
    id: number;
    text: string;
    completed: boolean;
    createdAt: Date;
}

export type TodoStatus = 'all' | 'active' | 'completed';

// TodoItem.tsx
import React from 'react';
import { Todo } from './types';

interface TodoItemProps {
    todo: Todo;
    onToggle: (id: number) => void;
    onDelete: (id: number) => void;
    onEdit: (id: number, text: string) => void;
}

export const TodoItem: React.FC<TodoItemProps> = ({
    todo,
    onToggle,
    onDelete,
    onEdit
}) => {
    const [isEditing, setIsEditing] = React.useState(false);
    const [editText, setEditText] = React.useState(todo.text);
    
    const handleSubmit = (e: React.FormEvent) => {
        e.preventDefault();
        onEdit(todo.id, editText);
        setIsEditing(false);
    };
    
    return (
        <div className="todo-item">
            <input
                type="checkbox"
                checked={todo.completed}
                onChange={() => onToggle(todo.id)}
            />
            
            {isEditing ? (
                <form onSubmit={handleSubmit}>
                    <input
                        type="text"
                        value={editText}
                        onChange={(e: React.ChangeEvent<HTMLInputElement>) => 
                            setEditText(e.target.value)
                        }
                    />
                </form>
            ) : (
                <span onClick={() => setIsEditing(true)}>
                    {todo.text}
                </span>
            )}
            
            <button onClick={() => onDelete(todo.id)}>Delete</button>
        </div>
    );
};

// App.tsx
import React, { useState, useEffect } from 'react';
import { Todo, TodoStatus } from './types';
import { TodoItem } from './TodoItem';

const App: React.FC = () => {
    const [todos, setTodos] = useState<Todo[]>([]);
    const [inputText, setInputText] = useState<string>('');
    const [filter, setFilter] = useState<TodoStatus>('all');
    const [nextId, setNextId] = useState<number>(1);
    
    // Load from localStorage
    useEffect(() => {
        const saved = localStorage.getItem('todos');
        if (saved) {
            setTodos(JSON.parse(saved));
        }
    }, []);
    
    // Save to localStorage
    useEffect(() => {
        localStorage.setItem('todos', JSON.stringify(todos));
    }, [todos]);
    
    const addTodo = (e: React.FormEvent) => {
        e.preventDefault();
        
        if (!inputText.trim()) return;
        
        const newTodo: Todo = {
            id: nextId,
            text: inputText,
            completed: false,
            createdAt: new Date()
        };
        
        setTodos([...todos, newTodo]);
        setInputText('');
        setNextId(nextId + 1);
    };
    
    const toggleTodo = (id: number): void => {
        setTodos(todos.map(todo =>
            todo.id === id
                ? { ...todo, completed: !todo.completed }
                : todo
        ));
    };
    
    const deleteTodo = (id: number): void => {
        setTodos(todos.filter(todo => todo.id !== id));
    };
    
    const editTodo = (id: number, text: string): void => {
        setTodos(todos.map(todo =>
            todo.id === id ? { ...todo, text } : todo
        ));
    };
    
    const filteredTodos = todos.filter(todo => {
        if (filter === 'active') return !todo.completed;
        if (filter === 'completed') return todo.completed;
        return true;
    });
    
    return (
        <div className="app">
            <h1>TypeScript Todo App</h1>
            
            <form onSubmit={addTodo}>
                <input
                    type="text"
                    value={inputText}
                    onChange={(e: React.ChangeEvent<HTMLInputElement>) =>
                        setInputText(e.target.value)
                    }
                    placeholder="What needs to be done?"
                />
                <button type="submit">Add</button>
            </form>
            
            <div className="filters">
                <button onClick={() => setFilter('all')}>All</button>
                <button onClick={() => setFilter('active')}>Active</button>
                <button onClick={() => setFilter('completed')}>Completed</button>
            </div>
            
            <div className="todo-list">
                {filteredTodos.map(todo => (
                    <TodoItem
                        key={todo.id}
                        todo={todo}
                        onToggle={toggleTodo}
                        onDelete={deleteTodo}
                        onEdit={editTodo}
                    />
                ))}
            </div>
        </div>
    );
};

export default App;

// Custom Hook Example
function useTodos() {
    const [todos, setTodos] = useState<Todo[]>([]);
    
    const addTodo = (text: string): void => {
        // ...
    };
    
    const toggleTodo = (id: number): void => {
        // ...
    };
    
    return { todos, addTodo, toggleTodo };
}

// Context API Example
interface TodoContextType {
    todos: Todo[];
    addTodo: (text: string) => void;
    toggleTodo: (id: number) => void;
}

const TodoContext = React.createContext<TodoContextType | undefined>(undefined);

export const useTodoContext = (): TodoContextType => {
    const context = React.useContext(TodoContext);
    if (!context) {
        throw new Error('useTodoContext must be used within TodoProvider');
    }
    return context;
};
```

---

## 🎯 Implementation Notes

For each assignment:

1. **Create folder structure** as shown
2. **Set up tsconfig.json** with appropriate settings
3. **Implement all code examples** provided
4. **Create HTML/CSS** for interactive demos
5. **Test thoroughly** - ensure no type errors
6. **Add console logs** for debugging
7. **Create README** for each assignment

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

