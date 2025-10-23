# Assignment 7: Semantic HTML - Meaningful Structure

**By Mahendra Bagul**

Semantic HTML is about using tags that have meaning, not just appearance. It makes your code better for SEO, accessibility, and maintainability.

---

## 📚 What You'll Learn

- ✅ `<header>`, `<nav>`, `<main>`, `<footer>`
- ✅ `<article>`, `<section>`, `<aside>`
- ✅ `<figure>`, `<figcaption>`
- ✅ `<time>`, `<address>`
- ✅ When to use semantic vs div/span
- ✅ Proper document outline
- ✅ SEO benefits

---

## 🎯 Assignment Objectives

Create a "Tech Blog" website using proper semantic HTML5 elements throughout.

**Difficulty**: ⭐⭐⭐⭐☆  
**Time**: 3-4 hours  
**Prerequisites**: Assignments 1-6

---

## 📋 Requirements

### Must Have
1. ✅ Proper use of `<header>`, `<nav>`, `<main>`, `<footer>`
2. ✅ At least 3 `<article>` elements
3. ✅ Multiple `<section>` elements
4. ✅ `<aside>` for sidebar content
5. ✅ `<figure>` with `<figcaption>`
6. ✅ `<time>` with datetime attribute
7. ✅ `<address>` for contact info
8. ✅ Meaningful heading hierarchy (h1-h6)
9. ✅ No unnecessary `<div>` tags

---

## 💻 Semantic HTML Structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Tech Blog</title>
</head>
<body>
    <!-- Site Header -->
    <header>
        <h1>My Tech Blog</h1>
        <nav>
            <ul>
                <li><a href="#home">Home</a></li>
                <li><a href="#articles">Articles</a></li>
                <li><a href="#about">About</a></li>
            </ul>
        </nav>
    </header>
    
    <!-- Main Content -->
    <main>
        <!-- Blog Post (Article) -->
        <article>
            <header>
                <h2>Understanding React Hooks</h2>
                <p>Published on <time datetime="2025-01-15">January 15, 2025</time></p>
                <p>By Jane Doe</p>
            </header>
            
            <section>
                <h3>Introduction</h3>
                <p>Content here...</p>
            </section>
            
            <section>
                <h3>What Are Hooks?</h3>
                <p>More content...</p>
                
                <figure>
                    <img src="hooks-diagram.png" alt="React Hooks diagram">
                    <figcaption>Figure 1: React Hooks lifecycle</figcaption>
                </figure>
            </section>
            
            <footer>
                <p>Tags: React, JavaScript, Hooks</p>
            </footer>
        </article>
        
        <!-- Sidebar -->
        <aside>
            <section>
                <h3>About the Author</h3>
                <p>Jane is a web developer...</p>
            </section>
            
            <section>
                <h3>Recent Posts</h3>
                <ul>
                    <li><a href="#">Post 1</a></li>
                    <li><a href="#">Post 2</a></li>
                </ul>
            </section>
        </aside>
    </main>
    
    <!-- Site Footer -->
    <footer>
        <address>
            Contact: <a href="mailto:hello@techblog.com">hello@techblog.com</a>
        </address>
        <p>&copy; 2025 Tech Blog. All rights reserved.</p>
    </footer>
</body>
</html>
```

---

## 🎯 Semantic Tag Guide

### Document Structure
- `<header>` - Top of page/section
- `<nav>` - Navigation links
- `<main>` - Primary content (one per page)
- `<footer>` - Bottom of page/section
- `<aside>` - Sidebar, related content

### Content Sectioning
- `<article>` - Self-contained content (blog post, news article)
- `<section>` - Thematic grouping
- `<figure>` - Images with captions
- `<figcaption>` - Caption for figure

### Inline Semantic
- `<time>` - Dates and times
- `<address>` - Contact information
- `<mark>` - Highlighted text
- `<strong>` - Important text
- `<em>` - Emphasized text

---

## ✅ Self-Assessment

- [ ] Used semantic HTML5 elements appropriately
- [ ] Document has clear structure
- [ ] No `<div>` where semantic tag fits better
- [ ] Heading hierarchy makes sense (h1 → h2 → h3)
- [ ] Articles are self-contained
- [ ] Sections group related content
- [ ] Time elements have datetime attribute
- [ ] Navigation is in `<nav>`
- [ ] Contact info in `<address>`

---

## 💡 When to Use What

**Use `<article>` when:**
- Content makes sense on its own
- Could be syndicated/reused
- Blog posts, news articles, comments

**Use `<section>` when:**
- Grouping related content
- Each has a heading
- Thematic divisions

**Use `<div>` when:**
- No semantic meaning
- Just for styling/layout
- Last resort!

---

**Next**: [Assignment 8: HTML5 Features](../assignment-08-html5-features/ASSIGNMENT_8_GUIDE.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

