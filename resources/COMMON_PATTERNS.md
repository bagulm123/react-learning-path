# Common Code Patterns & Snippets

**By Mahendra Bagul**

Reusable code patterns you'll use throughout the course.

---

## 📝 HTML Patterns

### Basic HTML5 Template
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Page description">
    <title>Page Title</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <nav>
            <!-- Navigation -->
        </nav>
    </header>
    
    <main>
        <!-- Main content -->
    </main>
    
    <footer>
        <!-- Footer -->
    </footer>
    
    <script src="script.js"></script>
</body>
</html>
```

### Semantic HTML Structure
```html
<article>
    <header>
        <h1>Article Title</h1>
        <p>By Author Name on <time datetime="2024-01-01">January 1, 2024</time></p>
    </header>
    
    <section>
        <h2>Section Title</h2>
        <p>Content...</p>
    </section>
    
    <footer>
        <p>Article footer</p>
    </footer>
</article>
```

---

## 🎨 CSS Patterns

### CSS Reset/Normalize
```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

html {
    font-size: 16px;
}

body {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
    line-height: 1.6;
}
```

### Flexbox Patterns
```css
/* Center content */
.flex-center {
    display: flex;
    justify-content: center;
    align-items: center;
}

/* Space between */
.flex-between {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

/* Column layout */
.flex-column {
    display: flex;
    flex-direction: column;
    gap: 1rem;
}
```

### Grid Patterns
```css
/* Responsive grid */
.grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 1.5rem;
}

/* Fixed columns */
.grid-3 {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem;
}
```

### Responsive Design
```css
/* Mobile first */
.container {
    padding: 1rem;
}

/* Tablet */
@media (min-width: 768px) {
    .container {
        padding: 2rem;
    }
}

/* Desktop */
@media (min-width: 1024px) {
    .container {
        padding: 3rem;
        max-width: 1200px;
        margin: 0 auto;
    }
}
```

---

## ⚡ JavaScript Patterns

### DOM Manipulation
```javascript
// Select elements
const element = document.getElementById('id');
const elements = document.querySelectorAll('.class');

// Create element
const div = document.createElement('div');
div.className = 'my-class';
div.textContent = 'Content';
document.body.appendChild(div);

// Event listener
element.addEventListener('click', (e) => {
    e.preventDefault();
    // Handle event
});
```

### Array Methods
```javascript
const array = [1, 2, 3, 4, 5];

// Map - transform
const doubled = array.map(n => n * 2);

// Filter - select
const evens = array.filter(n => n % 2 === 0);

// Reduce - aggregate
const sum = array.reduce((total, n) => total + n, 0);

// Find - first match
const found = array.find(n => n > 3);

// Some - any match
const hasEven = array.some(n => n % 2 === 0);

// Every - all match
const allPositive = array.every(n => n > 0);
```

### Object Patterns
```javascript
// Destructuring
const { name, age } = person;

// Spread operator
const newObj = { ...oldObj, updated: true };

// Object methods
const keys = Object.keys(obj);
const values = Object.values(obj);
const entries = Object.entries(obj);
```

### Async Patterns
```javascript
// Async/await
async function fetchData() {
    try {
        const response = await fetch(url);
        const data = await response.json();
        return data;
    } catch (error) {
        console.error('Error:', error);
    }
}

// Promise chain
fetch(url)
    .then(res => res.json())
    .then(data => console.log(data))
    .catch(error => console.error(error));
```

### LocalStorage
```javascript
// Save
localStorage.setItem('key', JSON.stringify(data));

// Load
const data = JSON.parse(localStorage.getItem('key'));

// Remove
localStorage.removeItem('key');

// Clear all
localStorage.clear();
```

---

## 📘 TypeScript Patterns

### Type Definitions
```typescript
// Interface
interface User {
    id: number;
    name: string;
    email: string;
    age?: number;  // Optional
}

// Type alias
type Status = 'active' | 'inactive' | 'pending';

// Generic
function identity<T>(arg: T): T {
    return arg;
}
```

### Function Types
```typescript
// Function with types
function greet(name: string): string {
    return `Hello, ${name}!`;
}

// Arrow function
const add = (a: number, b: number): number => a + b;

// Optional parameters
function log(message: string, level?: string): void {
    console.log(`[${level || 'INFO'}] ${message}`);
}
```

---

## ⚛️ React Patterns

### Functional Component
```typescript
import React, { useState } from 'react';

interface Props {
    title: string;
    onAction: () => void;
}

export const Component: React.FC<Props> = ({ title, onAction }) => {
    const [count, setCount] = useState(0);
    
    return (
        <div>
            <h1>{title}</h1>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>
                Increment
            </button>
        </div>
    );
};
```

### Custom Hook
```typescript
import { useState, useEffect } from 'react';

function useLocalStorage<T>(key: string, initialValue: T) {
    const [value, setValue] = useState<T>(() => {
        const saved = localStorage.getItem(key);
        return saved ? JSON.parse(saved) : initialValue;
    });
    
    useEffect(() => {
        localStorage.setItem(key, JSON.stringify(value));
    }, [key, value]);
    
    return [value, setValue] as const;
}
```

### Context Pattern
```typescript
import React, { createContext, useContext, useState } from 'react';

interface ThemeContextType {
    theme: 'light' | 'dark';
    toggleTheme: () => void;
}

const ThemeContext = createContext<ThemeContextType | undefined>(undefined);

export const ThemeProvider: React.FC<{ children: React.ReactNode }> = ({ children }) => {
    const [theme, setTheme] = useState<'light' | 'dark'>('light');
    
    const toggleTheme = () => {
        setTheme(prev => prev === 'light' ? 'dark' : 'light');
    };
    
    return (
        <ThemeContext.Provider value={{ theme, toggleTheme }}>
            {children}
        </ThemeContext.Provider>
    );
};

export const useTheme = () => {
    const context = useContext(ThemeContext);
    if (!context) {
        throw new Error('useTheme must be used within ThemeProvider');
    }
    return context;
};
```

### API Fetch Pattern
```typescript
import { useState, useEffect } from 'react';

interface Data {
    // Your data type
}

function useApi(url: string) {
    const [data, setData] = useState<Data | null>(null);
    const [loading, setLoading] = useState(true);
    const [error, setError] = useState<Error | null>(null);
    
    useEffect(() => {
        async function fetchData() {
            try {
                const response = await fetch(url);
                if (!response.ok) throw new Error('Failed to fetch');
                const data = await response.json();
                setData(data);
            } catch (err) {
                setError(err as Error);
            } finally {
                setLoading(false);
            }
        }
        
        fetchData();
    }, [url]);
    
    return { data, loading, error };
}
```

---

## 🎯 Design Patterns

### Singleton Pattern
```typescript
class Singleton {
    private static instance: Singleton;
    
    private constructor() {}
    
    static getInstance(): Singleton {
        if (!Singleton.instance) {
            Singleton.instance = new Singleton();
        }
        return Singleton.instance;
    }
}
```

### Factory Pattern
```typescript
interface Product {
    operation(): string;
}

class ConcreteProductA implements Product {
    operation(): string {
        return 'Product A';
    }
}

class Factory {
    static createProduct(type: string): Product {
        switch (type) {
            case 'A':
                return new ConcreteProductA();
            default:
                throw new Error('Unknown type');
        }
    }
}
```

---

## 🔧 Utility Functions

### Debounce
```javascript
function debounce(func, wait) {
    let timeout;
    return function executedFunction(...args) {
        clearTimeout(timeout);
        timeout = setTimeout(() => func(...args), wait);
    };
}

// Usage
const debouncedSearch = debounce((query) => {
    // Search logic
}, 300);
```

### Format Date
```javascript
function formatDate(date) {
    return new Intl.DateTimeFormat('en-US', {
        year: 'numeric',
        month: 'long',
        day: 'numeric'
    }).format(date);
}
```

### Generate ID
```javascript
function generateId() {
    return Date.now().toString(36) + Math.random().toString(36).substring(2);
}
```

---

## 💡 Tips

- **Copy, but understand** - Don't blindly copy. Understand what each line does.
- **Adapt to your needs** - Modify patterns for your specific use case.
- **Keep patterns handy** - Bookmark this file for quick reference.
- **Learn the why** - Understanding why patterns work matters more than memorizing them.

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

---

<div align="center">

**Need more patterns?** → Check MDN Web Docs

**Have a useful pattern?** → Contribute it!

</div>

