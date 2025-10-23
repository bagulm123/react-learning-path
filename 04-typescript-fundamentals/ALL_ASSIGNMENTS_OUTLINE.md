# TypeScript Fundamentals - All Assignments Outline

**By Mahendra Bagul**

This document outlines all 10 TypeScript assignments. Assignments 1-2 have complete guides. Assignments 3-10 are outlined here for implementation.

---

## ✅ Assignment 1: Basic Types (COMPLETE)
**Status**: Full guide created  
**Topics**: Basic types, arrays, tuples, union types, literals, type inference  
**Project**: Type-Safe Calculator

---

## ✅ Assignment 2: Interfaces & Types (COMPLETE)
**Status**: Full guide created  
**Topics**: Interfaces, type aliases, optional/readonly properties, extending, intersection types  
**Project**: User Management System

---

## 📝 Assignment 3: Functions & Generics

### Topics
- Function type annotations
- Generic functions
- Generic interfaces and classes
- Generic constraints
- Multiple type parameters
- Default generic types

### Project: Generic Data Structure Library
```typescript
// Generic Stack
class Stack<T> {
    private items: T[] = [];
    
    push(item: T): void {
        this.items.push(item);
    }
    
    pop(): T | undefined {
        return this.items.pop();
    }
}

// Generic function with constraints
function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
    return obj[key];
}
```

### Key Examples
1. Generic functions
2. Generic classes
3. Constrained generics
4. Generic utility functions
5. Real-world use cases

---

## 📝 Assignment 4: Classes & OOP

### Topics
- Classes and constructors
- Access modifiers (public, private, protected)
- Inheritance and super
- Abstract classes
- Static members
- Getters and setters

### Project: Animal Hierarchy System
```typescript
abstract class Animal {
    protected name: string;
    
    constructor(name: string) {
        this.name = name;
    }
    
    abstract makeSound(): void;
}

class Dog extends Animal {
    private breed: string;
    
    constructor(name: string, breed: string) {
        super(name);
        this.breed = breed;
    }
    
    makeSound(): void {
        console.log("Woof!");
    }
}
```

### Key Examples
1. Basic classes
2. Inheritance chain
3. Abstract classes
4. Access modifiers
5. Static methods and properties

---

## 📝 Assignment 5: Advanced Types

### Topics
- Mapped types
- Conditional types
- Template literal types
- Index types
- keyof operator
- typeof operator

### Project: Type Transformer Utility
```typescript
// Mapped type
type Readonly<T> = {
    readonly [P in keyof T]: T[P];
};

// Conditional type
type NonNullable<T> = T extends null | undefined ? never : T;

// Template literal type
type EventName = `on${Capitalize<string>}`;
```

### Key Examples
1. Creating mapped types
2. Conditional type logic
3. Template literal types
4. Practical utilities
5. Type transformations

---

## 📝 Assignment 6: Modules & Namespaces

### Topics
- ES6 modules
- Import/export syntax
- Default exports
- Namespaces
- Module resolution
- Declaration files (.d.ts)

### Project: Module-based Library
```typescript
// math.ts
export function add(a: number, b: number): number {
    return a + b;
}

export default class Calculator {
    // ...
}

// app.ts
import Calculator, { add } from './math';
```

### Key Examples
1. Named exports
2. Default exports
3. Re-exporting
4. Namespaces
5. Declaration files

---

## 📝 Assignment 7: Decorators

### Topics
- Class decorators
- Method decorators
- Property decorators
- Parameter decorators
- Decorator factories
- Decorator composition

### Project: Logging & Validation System
```typescript
function Component(constructor: Function) {
    console.log("Component created:", constructor.name);
}

function Log(target: any, propertyName: string, descriptor: PropertyDescriptor) {
    const original = descriptor.value;
    
    descriptor.value = function(...args: any[]) {
        console.log(`Calling ${propertyName} with`, args);
        return original.apply(this, args);
    };
}

@Component
class MyComponent {
    @Log
    doSomething() {
        // ...
    }
}
```

### Key Examples
1. Class decorators
2. Method decorators
3. Property decorators
4. Decorator factories
5. Real-world patterns

---

## 📝 Assignment 8: Type Guards & Narrowing

### Topics
- typeof guards
- instanceof guards
- Custom type guards
- Discriminated unions
- never type
- Exhaustiveness checking

### Project: Validation Framework
```typescript
// Type guard
function isString(value: unknown): value is string {
    return typeof value === 'string';
}

// Discriminated union
type Shape =
    | { kind: 'circle'; radius: number }
    | { kind: 'square'; size: number };

function getArea(shape: Shape): number {
    switch (shape.kind) {
        case 'circle':
            return Math.PI * shape.radius ** 2;
        case 'square':
            return shape.size ** 2;
    }
}
```

### Key Examples
1. Built-in type guards
2. Custom type guards
3. Discriminated unions
4. Control flow analysis
5. Exhaustiveness checking

---

## 📝 Assignment 9: Utility Types

### Topics
- Partial, Required, Readonly
- Pick, Omit
- Record, Exclude, Extract
- ReturnType, Parameters
- Awaited, NonNullable
- Creating custom utility types

### Project: Type Utility Showcase
```typescript
// Built-in utilities
type User = {
    id: number;
    name: string;
    email: string;
    age: number;
};

type PartialUser = Partial<User>;
type RequiredUser = Required<PartialUser>;
type UserPreview = Pick<User, 'id' | 'name'>;
type UserWithoutAge = Omit<User, 'age'>;

// Custom utility
type DeepReadonly<T> = {
    readonly [P in keyof T]: T[P] extends object
        ? DeepReadonly<T[P]>
        : T[P];
};
```

### Key Examples
1. All built-in utilities
2. Use cases for each
3. Combining utilities
4. Custom utility types
5. Real-world applications

---

## 📝 Assignment 10: React with TypeScript

### Topics
- Typing functional components
- Props and children
- State typing
- Event handlers
- useRef, useEffect with types
- Custom hooks with TypeScript
- Context API with types
- Generic components

### Project: Typed React Todo App
```typescript
import React, { useState } from 'react';

interface Todo {
    id: number;
    text: string;
    completed: boolean;
}

interface TodoProps {
    todo: Todo;
    onToggle: (id: number) => void;
    onDelete: (id: number) => void;
}

const TodoItem: React.FC<TodoProps> = ({ todo, onToggle, onDelete }) => {
    return (
        <div>
            <input
                type="checkbox"
                checked={todo.completed}
                onChange={() => onToggle(todo.id)}
            />
            <span>{todo.text}</span>
            <button onClick={() => onDelete(todo.id)}>Delete</button>
        </div>
    );
};

const App: React.FC = () => {
    const [todos, setTodos] = useState<Todo[]>([]);
    
    const addTodo = (text: string): void => {
        // ...
    };
    
    return <div>{/* ... */}</div>;
};
```

### Key Examples
1. Component props typing
2. State and hooks
3. Event handlers
4. Custom hooks
5. Context API
6. Generic components
7. Children props
8. Ref typing

---

## 🎯 Implementation Priority

**Complete Guides Needed For:**
1. Assignment 3: Functions & Generics (Critical - used everywhere)
2. Assignment 10: React with TypeScript (Critical - final goal)
3. Assignment 4: Classes & OOP (Important - OOP patterns)
4. Assignment 9: Utility Types (Important - daily use)

**Can Use Outlines:**
5. Assignment 5: Advanced Types (Reference material)
6. Assignment 6: Modules (Standard patterns)
7. Assignment 7: Decorators (Advanced feature)
8. Assignment 8: Type Guards (Covered in basics)

---

## 📝 Note

Assignments 1-2 have **complete implementation guides** with:
- Full source code
- HTML/CSS
- TypeScript configuration
- Step-by-step instructions
- Self-assessment checklists

Assignments 3-10 have **comprehensive outlines** with:
- All topics covered
- Code examples
- Project descriptions
- Key concepts
- Clear learning objectives

Students can implement Assignments 3-10 using these outlines as blueprints, referring to Assignments 1-2 as templates for structure.

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

