# Assignment 1: CSS Selectors Basics - Styling Your First Page

**By Mahendra Bagul**

Welcome to CSS! After mastering HTML structure, it's time to make things look good. CSS is where web design magic happens! 🎨

---

## 📚 What You'll Learn

- ✅ CSS syntax and structure
- ✅ Element, class, and ID selectors
- ✅ Pseudo-classes (:hover, :focus)
- ✅ Combinators (descendant, child, sibling)
- ✅ Specificity and cascade
- ✅ Linking CSS to HTML
- ✅ Basic text and color styling

---

## 🎯 Assignment Objectives

Create a styled "Digital Business Card" using various CSS selectors.

**Difficulty**: ⭐☆☆☆☆  
**Time**: 3-4 hours  
**Prerequisites**: HTML Phase completed

---

## 📋 Requirements

### Must Have
1. ✅ External CSS file linked to HTML
2. ✅ Element selectors (h1, p, etc.)
3. ✅ At least 5 class selectors
4. ✅ At least 2 ID selectors
5. ✅ Hover effects on links
6. ✅ At least 3 different text colors
7. ✅ At least 2 background colors
8. ✅ Font styling (size, weight, family)

---

## 💻 CSS Basics

### Linking CSS to HTML
```html
<!-- In HTML <head> -->
<link rel="stylesheet" href="styles.css">
```

### CSS Syntax
```css
selector {
    property: value;
    another-property: value;
}
```

### Selectors

**Element Selector** (styles all h1 elements)
```css
h1 {
    color: blue;
    font-size: 32px;
}
```

**Class Selector** (styles elements with class="card")
```css
.card {
    background-color: white;
    padding: 20px;
}
```

**ID Selector** (styles element with id="header")
```css
#header {
    background-color: navy;
    color: white;
}
```

**Multiple Selectors**
```css
h1, h2, h3 {
    font-family: Arial, sans-serif;
}
```

**Descendant Selector** (p inside .card)
```css
.card p {
    line-height: 1.6;
}
```

**Pseudo-classes**
```css
a:hover {
    color: red;
    text-decoration: underline;
}

input:focus {
    border-color: blue;
}
```

---

## 🏗️ Implementation

### HTML Structure (businesscard.html)
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>John Doe - Business Card</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="business-card">
        <header id="card-header">
            <h1 class="name">John Doe</h1>
            <p class="title">Web Developer</p>
        </header>
        
        <section class="contact-info">
            <p class="email">john@example.com</p>
            <p class="phone">+1 (555) 123-4567</p>
            <p class="website"><a href="#">www.johndoe.com</a></p>
        </section>
        
        <section class="skills">
            <h2>Skills</h2>
            <ul>
                <li class="skill">HTML</li>
                <li class="skill">CSS</li>
                <li class="skill">JavaScript</li>
            </ul>
        </section>
    </div>
</body>
</html>
```

### CSS (styles.css)
```css
/* Reset default styles */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial, sans-serif;
    background-color: #f0f0f0;
    padding: 50px;
}

/* Business Card Container */
.business-card {
    background-color: white;
    max-width: 400px;
    margin: 0 auto;
    padding: 30px;
    border-radius: 10px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

/* Header Section */
#card-header {
    text-align: center;
    border-bottom: 2px solid #333;
    padding-bottom: 20px;
    margin-bottom: 20px;
}

/* Name Styling */
.name {
    font-size: 28px;
    color: #2c3e50;
    margin-bottom: 10px;
}

/* Job Title */
.title {
    font-size: 16px;
    color: #7f8c8d;
    font-style: italic;
}

/* Contact Info Section */
.contact-info {
    margin-bottom: 20px;
}

.contact-info p {
    margin: 8px 0;
    color: #34495e;
}

/* Email specific styling */
.email {
    font-weight: bold;
}

/* Links */
a {
    color: #3498db;
    text-decoration: none;
}

a:hover {
    color: #2980b9;
    text-decoration: underline;
}

/* Skills Section */
.skills h2 {
    font-size: 18px;
    color: #2c3e50;
    margin-bottom: 10px;
}

.skills ul {
    list-style: none;
}

.skill {
    background-color: #ecf0f1;
    padding: 8px 12px;
    margin: 5px 0;
    border-radius: 5px;
    color: #2c3e50;
}

.skill:hover {
    background-color: #3498db;
    color: white;
}
```

---

## 📖 CSS Concepts Explained

### Specificity (Which style wins?)
1. **Inline styles** (highest) - style="color: red"
2. **IDs** - #header
3. **Classes, attributes, pseudo-classes** - .card, :hover
4. **Elements** - h1, p

**Example:**
```css
p { color: black; }           /* Specificity: 1 */
.text { color: blue; }        /* Specificity: 10 */
#main { color: green; }       /* Specificity: 100 */
```
If an element has all three, green wins!

### The Cascade
When specificity is equal, the **last rule wins**:
```css
p { color: red; }
p { color: blue; }  /* This one applies */
```

---

## ✅ Self-Assessment

- [ ] Created external CSS file
- [ ] Linked CSS to HTML correctly
- [ ] Used element selectors
- [ ] Used 5+ class selectors
- [ ] Used 2+ ID selectors
- [ ] Implemented hover effects
- [ ] Applied colors and fonts
- [ ] Page looks styled (not default HTML)
- [ ] All selectors work as expected

---

## 🐛 Common Mistakes

**1. Forgot to link CSS**
- Check `<link>` tag in HTML `<head>`
- Verify file path is correct

**2. Wrong selector syntax**
- Class: `.classname` (with dot)
- ID: `#idname` (with hash)
- Element: `elementname` (no prefix)

**3. Typos in property names**
- `colour` ❌ → `color` ✅
- `font-familly` ❌ → `font-family` ✅

---

## 💡 CSS Tips

1. **Use classes for reusability** - IDs only once per page
2. **Start with element selectors** - Then add classes for specifics
3. **Group similar selectors** - h1, h2, h3 { ... }
4. **Add comments** - /* Section Title */
5. **Keep it organized** - Group related styles

---

**Next**: [Assignment 2: Box Model](../assignment-02-box-model/ASSIGNMENT_2_GUIDE.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

