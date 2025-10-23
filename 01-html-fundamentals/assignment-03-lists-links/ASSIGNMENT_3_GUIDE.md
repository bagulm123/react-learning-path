# Assignment 3: Lists & Links - Building Navigation

**By Mahendra Bagul**

Lists and links are the backbone of web navigation. Every website you visit uses them - menus, navigation bars, breadcrumbs, site maps. Today, you'll master both!

---

## 📚 What You'll Learn

- ✅ Ordered lists (`<ol>`)
- ✅ Unordered lists (`<ul>`)
- ✅ Definition lists (`<dl>`)
- ✅ Nested lists
- ✅ Absolute vs relative links
- ✅ Internal page navigation
- ✅ Link attributes (target, rel, download)
- ✅ Email and phone links
- ✅ Navigation patterns

---

## 🎯 Assignment Objectives

Create a multi-page "Recipe Website" with proper navigation, lists of ingredients, and linked pages.

**Difficulty**: ⭐⭐☆☆☆  
**Time**: 3-4 hours  
**Prerequisites**: Assignments 1-2

---

## 📋 Requirements

### Must Have
1. ✅ At least 3 linked HTML pages (home, recipes, about)
2. ✅ Navigation menu on every page
3. ✅ At least 3 ordered lists (recipe steps)
4. ✅ At least 3 unordered lists (ingredients)
5. ✅ At least 1 nested list
6. ✅ Links to external websites (open in new tab)
7. ✅ "Back to top" anchor link
8. ✅ Email and/or phone link

### Nice to Have
- ✨ Breadcrumb navigation
- ✨ Definition list for glossary
- ✨ Download link for recipe PDF

---

## 💻 Key HTML Elements

### Unordered List (Bullets)
```html
<ul>
    <li>First item</li>
    <li>Second item</li>
    <li>Third item</li>
</ul>
```

### Ordered List (Numbers)
```html
<ol>
    <li>Step one</li>
    <li>Step two</li>
    <li>Step three</li>
</ol>
```

### Nested List
```html
<ul>
    <li>Parent item
        <ul>
            <li>Child item 1</li>
            <li>Child item 2</li>
        </ul>
    </li>
</ul>
```

### Links
```html
<!-- Internal link (same website) -->
<a href="about.html">About Us</a>

<!-- External link (different website) -->
<a href="https://example.com" target="_blank" rel="noopener">Visit Example</a>

<!-- Anchor link (same page) -->
<a href="#top">Back to Top</a>

<!-- Email link -->
<a href="mailto:hello@example.com">Email Us</a>

<!-- Phone link -->
<a href="tel:+1234567890">Call Us</a>
```

---

## 🏗️ Implementation Guide

### Step 1: Create Project Structure
```
assignment-03-lists-links/
├── index.html
├── recipes.html
└── about.html
```

### Step 2: Build Navigation (Add to ALL pages)
```html
<nav>
    <ul>
        <li><a href="index.html">Home</a></li>
        <li><a href="recipes.html">Recipes</a></li>
        <li><a href="about.html">About</a></li>
    </ul>
</nav>
```

### Step 3: Create Recipe Page with Lists
```html
<h1>Chocolate Chip Cookies</h1>

<h2>Ingredients</h2>
<ul>
    <li>2 cups flour</li>
    <li>1 cup butter</li>
    <li>1 cup sugar</li>
    <li>2 eggs</li>
    <li>2 cups chocolate chips</li>
</ul>

<h2>Instructions</h2>
<ol>
    <li>Preheat oven to 350°F</li>
    <li>Mix butter and sugar</li>
    <li>Add eggs and flour</li>
    <li>Fold in chocolate chips</li>
    <li>Bake for 12 minutes</li>
</ol>
```

---

## ✅ Self-Assessment

- [ ] Created 3+ HTML pages
- [ ] Navigation menu present on all pages
- [ ] Navigation links work correctly
- [ ] Used ordered lists appropriately
- [ ] Used unordered lists appropriately
- [ ] Included at least one nested list
- [ ] External links open in new tabs
- [ ] Anchor links navigate correctly
- [ ] Email/phone links work

---

## 🐛 Common Mistakes

**1. Broken Links**
- Problem: Link goes to 404
- Solution: Check file names match exactly (case-sensitive!)

**2. Forgetting target="_blank"**
- Problem: External sites open in same tab
- Solution: Add `target="_blank" rel="noopener"`

**3. Wrong List Type**
- Problem: Using `<ol>` for non-sequential items
- Solution: Use `<ul>` for unordered, `<ol>` for steps/rankings

---

## 🚀 Going Further

1. Create a sitemap page listing all pages
2. Add a dropdown navigation submenu
3. Create a table of contents with anchor links
4. Build a multi-level nested menu

---

**Next**: [Assignment 4: Images & Media](../assignment-04-images-media/ASSIGNMENT_4_GUIDE.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

