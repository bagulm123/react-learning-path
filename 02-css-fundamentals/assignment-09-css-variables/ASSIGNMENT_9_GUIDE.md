# Assignment 9: CSS Variables - Dynamic Theming

**By Mahendra Bagul**

CSS Variables (Custom Properties) let you store values and reuse them throughout your stylesheet. Perfect for themes, maintaining consistency, and creating dynamic designs! 🎨

---

## 📚 What You'll Learn

- ✅ CSS custom properties (`--variable-name`)
- ✅ `var()` function
- ✅ Variable scope (global vs local)
- ✅ Dark/light theme toggle
- ✅ Dynamic color schemes
- ✅ JavaScript + CSS variables
- ✅ Fallback values
- ✅ Calc() with variables

---

## 🎯 Assignment Objectives

Create a "Theme Switcher Application" with light mode, dark mode, and custom color themes using CSS variables.

**Difficulty**: ⭐⭐⭐⭐⭐  
**Time**: 4-5 hours  
**Prerequisites**: CSS Assignments 1-8

---

## 📋 Requirements

### Must Have
1. ✅ Light theme (default)
2. ✅ Dark theme toggle
3. ✅ At least 3 custom color themes
4. ✅ CSS variables for colors, spacing, fonts
5. ✅ Smooth transitions between themes
6. ✅ localStorage to remember preference
7. ✅ Variables scoped globally and locally
8. ✅ Use of `calc()` with variables
9. ✅ Fallback values for older browsers
10. ✅ Dynamic updates via JavaScript

---

## 🎨 CSS Variables Basics

### Defining Variables
```css
:root {
    /* Global variables */
    --primary-color: #3498db;
    --secondary-color: #2c3e50;
    --spacing-unit: 8px;
    --border-radius: 4px;
    --font-size-base: 16px;
}

.component {
    /* Local variables (scoped to .component) */
    --component-bg: white;
    --component-padding: calc(var(--spacing-unit) * 2);
}
```

### Using Variables
```css
.button {
    background-color: var(--primary-color);
    padding: var(--spacing-unit);
    border-radius: var(--border-radius);
    
    /* With fallback */
    color: var(--text-color, black);
}

.card {
    /* Using calc() */
    margin: calc(var(--spacing-unit) * 3);
    padding: calc(var(--spacing-unit) * 2);
}
```

### Updating with JavaScript
```javascript
// Set variable
document.documentElement.style.setProperty('--primary-color', '#e74c3c');

// Get variable
const color = getComputedStyle(document.documentElement)
    .getPropertyValue('--primary-color');
```

---

## 💻 Complete Implementation

### HTML
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Theme Switcher</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="app">
        <!-- Theme Controls -->
        <header class="header">
            <h1>Theme Switcher</h1>
            <div class="theme-controls">
                <button class="theme-btn" data-theme="light">☀️ Light</button>
                <button class="theme-btn" data-theme="dark">🌙 Dark</button>
                <button class="theme-btn" data-theme="blue">💙 Blue</button>
                <button class="theme-btn" data-theme="green">💚 Green</button>
                <button class="theme-btn" data-theme="purple">💜 Purple</button>
            </div>
        </header>
        
        <!-- Main Content -->
        <main class="content">
            <section class="showcase">
                <h2>CSS Variables Showcase</h2>
                <p>This entire page uses CSS variables for theming. Switch themes using the buttons above!</p>
                
                <div class="color-palette">
                    <div class="color-box primary">
                        <span>Primary</span>
                    </div>
                    <div class="color-box secondary">
                        <span>Secondary</span>
                    </div>
                    <div class="color-box accent">
                        <span>Accent</span>
                    </div>
                </div>
            </section>
            
            <section class="cards">
                <div class="card">
                    <h3>Card Title 1</h3>
                    <p>This card uses CSS variables for all its styling. Colors, spacing, and borders are all theme-aware.</p>
                    <button class="btn-primary">Primary Button</button>
                </div>
                
                <div class="card">
                    <h3>Card Title 2</h3>
                    <p>Notice how everything updates seamlessly when you change themes. That's the power of CSS variables!</p>
                    <button class="btn-secondary">Secondary Button</button>
                </div>
                
                <div class="card">
                    <h3>Card Title 3</h3>
                    <p>The theme preference is saved to localStorage, so your choice persists across page reloads.</p>
                    <button class="btn-accent">Accent Button</button>
                </div>
            </section>
            
            <section class="examples">
                <h2>Variable Examples</h2>
                
                <div class="example-grid">
                    <div class="example-item">
                        <h4>Spacing</h4>
                        <div class="spacing-demo">
                            <div class="box">Box 1</div>
                            <div class="box">Box 2</div>
                            <div class="box">Box 3</div>
                        </div>
                    </div>
                    
                    <div class="example-item">
                        <h4>Typography</h4>
                        <p class="text-sm">Small Text</p>
                        <p class="text-base">Base Text</p>
                        <p class="text-lg">Large Text</p>
                    </div>
                    
                    <div class="example-item">
                        <h4>Borders</h4>
                        <div class="border-demo">Rounded Borders</div>
                    </div>
                </div>
            </section>
        </main>
        
        <!-- Footer -->
        <footer class="footer">
            <p>Created with CSS Variables | Theme: <span id="currentTheme">light</span></p>
        </footer>
    </div>
    
    <script src="script.js"></script>
</body>
</html>
```

### CSS (styles.css)
```css
/* ===== DEFAULT THEME (LIGHT) ===== */
:root {
    /* Colors */
    --color-primary: #3498db;
    --color-secondary: #2c3e50;
    --color-accent: #e74c3c;
    --color-bg: #ffffff;
    --color-surface: #f8f9fa;
    --color-text: #333333;
    --color-text-secondary: #6c757d;
    
    /* Spacing */
    --spacing-xs: 0.5rem;
    --spacing-sm: 1rem;
    --spacing-md: 1.5rem;
    --spacing-lg: 2rem;
    --spacing-xl: 3rem;
    
    /* Typography */
    --font-size-sm: 0.875rem;
    --font-size-base: 1rem;
    --font-size-lg: 1.25rem;
    --font-size-xl: 1.5rem;
    --font-size-2xl: 2rem;
    
    /* Borders */
    --border-radius-sm: 4px;
    --border-radius-md: 8px;
    --border-radius-lg: 12px;
    --border-width: 2px;
    
    /* Shadows */
    --shadow-sm: 0 2px 4px rgba(0, 0, 0, 0.1);
    --shadow-md: 0 4px 8px rgba(0, 0, 0, 0.15);
    --shadow-lg: 0 8px 16px rgba(0, 0, 0, 0.2);
    
    /* Transitions */
    --transition-speed: 0.3s;
}

/* ===== DARK THEME ===== */
[data-theme="dark"] {
    --color-primary: #5dade2;
    --color-secondary: #34495e;
    --color-accent: #ec7063;
    --color-bg: #1a1a1a;
    --color-surface: #2d2d2d;
    --color-text: #e0e0e0;
    --color-text-secondary: #a0a0a0;
    --shadow-sm: 0 2px 4px rgba(0, 0, 0, 0.5);
    --shadow-md: 0 4px 8px rgba(0, 0, 0, 0.6);
    --shadow-lg: 0 8px 16px rgba(0, 0, 0, 0.7);
}

/* ===== BLUE THEME ===== */
[data-theme="blue"] {
    --color-primary: #2196F3;
    --color-secondary: #1976D2;
    --color-accent: #03A9F4;
    --color-bg: #E3F2FD;
    --color-surface: #BBDEFB;
    --color-text: #0D47A1;
    --color-text-secondary: #1565C0;
}

/* ===== GREEN THEME ===== */
[data-theme="green"] {
    --color-primary: #4CAF50;
    --color-secondary: #388E3C;
    --color-accent: #8BC34A;
    --color-bg: #E8F5E9;
    --color-surface: #C8E6C9;
    --color-text: #1B5E20;
    --color-text-secondary: #2E7D32;
}

/* ===== PURPLE THEME ===== */
[data-theme="purple"] {
    --color-primary: #9C27B0;
    --color-secondary: #7B1FA2;
    --color-accent: #BA68C8;
    --color-bg: #F3E5F5;
    --color-surface: #E1BEE7;
    --color-text: #4A148C;
    --color-text-secondary: #6A1B9A;
}

/* ===== BASE STYLES ===== */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    font-size: var(--font-size-base);
    color: var(--color-text);
    background-color: var(--color-bg);
    line-height: 1.6;
    transition: background-color var(--transition-speed),
                color var(--transition-speed);
}

.app {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
}

/* ===== HEADER ===== */
.header {
    background-color: var(--color-primary);
    color: white;
    padding: var(--spacing-lg);
    box-shadow: var(--shadow-md);
}

.header h1 {
    font-size: var(--font-size-2xl);
    margin-bottom: var(--spacing-md);
    text-align: center;
}

.theme-controls {
    display: flex;
    gap: var(--spacing-sm);
    justify-content: center;
    flex-wrap: wrap;
}

.theme-btn {
    padding: var(--spacing-sm) var(--spacing-md);
    border: var(--border-width) solid white;
    border-radius: var(--border-radius-md);
    background-color: transparent;
    color: white;
    font-size: var(--font-size-base);
    cursor: pointer;
    transition: all var(--transition-speed);
}

.theme-btn:hover {
    background-color: white;
    color: var(--color-primary);
    transform: translateY(-2px);
}

.theme-btn.active {
    background-color: white;
    color: var(--color-primary);
}

/* ===== CONTENT ===== */
.content {
    flex: 1;
    max-width: 1200px;
    margin: 0 auto;
    padding: var(--spacing-xl) var(--spacing-lg);
    width: 100%;
}

.showcase {
    text-align: center;
    margin-bottom: var(--spacing-xl);
}

.showcase h2 {
    font-size: var(--font-size-xl);
    color: var(--color-primary);
    margin-bottom: var(--spacing-md);
}

.color-palette {
    display: flex;
    gap: var(--spacing-md);
    justify-content: center;
    margin-top: var(--spacing-lg);
    flex-wrap: wrap;
}

.color-box {
    width: 150px;
    height: 150px;
    border-radius: var(--border-radius-lg);
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    font-weight: bold;
    box-shadow: var(--shadow-md);
    transition: transform var(--transition-speed);
}

.color-box:hover {
    transform: scale(1.05);
}

.color-box.primary {
    background-color: var(--color-primary);
}

.color-box.secondary {
    background-color: var(--color-secondary);
}

.color-box.accent {
    background-color: var(--color-accent);
}

/* ===== CARDS ===== */
.cards {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: var(--spacing-lg);
    margin-bottom: var(--spacing-xl);
}

.card {
    background-color: var(--color-surface);
    padding: var(--spacing-lg);
    border-radius: var(--border-radius-lg);
    box-shadow: var(--shadow-sm);
    transition: all var(--transition-speed);
}

.card:hover {
    box-shadow: var(--shadow-lg);
    transform: translateY(-5px);
}

.card h3 {
    color: var(--color-primary);
    margin-bottom: var(--spacing-sm);
}

.card p {
    color: var(--color-text-secondary);
    margin-bottom: var(--spacing-md);
}

/* ===== BUTTONS ===== */
button {
    padding: calc(var(--spacing-sm) * 1.5) var(--spacing-lg);
    border: none;
    border-radius: var(--border-radius-md);
    font-size: var(--font-size-base);
    cursor: pointer;
    transition: all var(--transition-speed);
}

.btn-primary {
    background-color: var(--color-primary);
    color: white;
}

.btn-primary:hover {
    filter: brightness(1.1);
    transform: scale(1.05);
}

.btn-secondary {
    background-color: var(--color-secondary);
    color: white;
}

.btn-accent {
    background-color: var(--color-accent);
    color: white;
}

/* ===== EXAMPLES ===== */
.examples {
    margin-bottom: var(--spacing-xl);
}

.examples h2 {
    font-size: var(--font-size-xl);
    color: var(--color-primary);
    margin-bottom: var(--spacing-lg);
}

.example-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: var(--spacing-lg);
}

.example-item {
    background-color: var(--color-surface);
    padding: var(--spacing-lg);
    border-radius: var(--border-radius-md);
}

.spacing-demo {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-sm);
}

.box {
    background-color: var(--color-primary);
    color: white;
    padding: var(--spacing-sm);
    border-radius: var(--border-radius-sm);
    text-align: center;
}

.text-sm {
    font-size: var(--font-size-sm);
}

.text-base {
    font-size: var(--font-size-base);
}

.text-lg {
    font-size: var(--font-size-lg);
}

.border-demo {
    background-color: var(--color-accent);
    color: white;
    padding: var(--spacing-md);
    border-radius: var(--border-radius-lg);
    text-align: center;
}

/* ===== FOOTER ===== */
.footer {
    background-color: var(--color-secondary);
    color: white;
    padding: var(--spacing-lg);
    text-align: center;
}

/* ===== RESPONSIVE ===== */
@media (max-width: 768px) {
    .cards {
        grid-template-columns: 1fr;
    }
    
    .example-grid {
        grid-template-columns: 1fr;
    }
}
```

### JavaScript (script.js)
```javascript
// Get saved theme or default to 'light'
let currentTheme = localStorage.getItem('theme') || 'light';

// Apply theme on load
document.documentElement.setAttribute('data-theme', currentTheme);
updateThemeDisplay();

// Theme button handlers
const themeButtons = document.querySelectorAll('.theme-btn');
themeButtons.forEach(btn => {
    btn.addEventListener('click', () => {
        const theme = btn.dataset.theme;
        setTheme(theme);
    });
    
    // Mark active button
    if (btn.dataset.theme === currentTheme) {
        btn.classList.add('active');
    }
});

function setTheme(theme) {
    currentTheme = theme;
    document.documentElement.setAttribute('data-theme', theme);
    localStorage.setItem('theme', theme);
    updateThemeDisplay();
    updateActiveButton();
}

function updateThemeDisplay() {
    document.getElementById('currentTheme').textContent = currentTheme;
}

function updateActiveButton() {
    themeButtons.forEach(btn => {
        btn.classList.toggle('active', btn.dataset.theme === currentTheme);
    });
}

// Keyboard shortcuts
document.addEventListener('keydown', (e) => {
    // Ctrl/Cmd + T for theme toggle
    if ((e.ctrlKey || e.metaKey) && e.key === 't') {
        e.preventDefault();
        const themes = ['light', 'dark', 'blue', 'green', 'purple'];
        const currentIndex = themes.indexOf(currentTheme);
        const nextIndex = (currentIndex + 1) % themes.length;
        setTheme(themes[nextIndex]);
    }
});
```

---

## 📖 CSS Variables Benefits

1. **Easy theming**: Change entire site with few lines
2. **Maintainability**: Update once, apply everywhere
3. **Dynamic**: Can be changed with JavaScript
4. **Scoped**: Can be global or component-specific
5. **calc() compatible**: Math with variables
6. **No build step**: Native CSS feature

---

## ✅ Self-Assessment

- [ ] Light theme works
- [ ] Dark theme toggle works
- [ ] 3+ custom themes available
- [ ] Variables for colors, spacing, fonts
- [ ] Smooth theme transitions
- [ ] localStorage saves preference
- [ ] Global and local scoping used
- [ ] calc() with variables demonstrated
- [ ] Fallback values provided
- [ ] JavaScript updates variables

---

**Next**: [Assignment 10: Complete Website](../assignment-10-complete-website/ASSIGNMENT_10_GUIDE.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

