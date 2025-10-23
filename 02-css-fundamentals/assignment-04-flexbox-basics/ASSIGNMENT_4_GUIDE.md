# Assignment 4: Flexbox Basics - Modern Layout Made Easy

**By Mahendra Bagul**

Flexbox changed everything! Before Flexbox, creating flexible, responsive layouts was painful. Now it's simple and intuitive.

Once you understand Flexbox, you'll wonder how you ever lived without it! 🎯

---

## 📚 What You'll Learn

- ✅ Flexbox container and item concepts
- ✅ `display: flex` and flex direction
- ✅ `justify-content` (main axis alignment)
- ✅ `align-items` (cross axis alignment)
- ✅ `flex-wrap` and multi-line layouts
- ✅ `flex-grow`, `flex-shrink`, `flex-basis`
- ✅ `align-self` for individual items
- ✅ Creating common layouts with Flexbox
- ✅ Responsive galleries and navigation

---

## 🎯 Assignment Objectives

Create a "Photo Gallery Website" using Flexbox for all layouts - navigation, grid, cards, and footer.

**Difficulty**: ⭐⭐⭐☆☆  
**Time**: 4-5 hours  
**Prerequisites**: CSS Assignments 1-3

---

## 📋 Requirements

### Must Have
1. ✅ Flexbox navigation bar
2. ✅ Photo gallery with flex-wrap
3. ✅ Card layout using Flexbox
4. ✅ Centered content with Flexbox
5. ✅ Footer with space-between
6. ✅ Use of `justify-content` (at least 3 values)
7. ✅ Use of `align-items` (at least 3 values)
8. ✅ Responsive design with flex-wrap
9. ✅ At least 12 photos in gallery
10. ✅ Hover effects on photos

---

## 📦 Flexbox Fundamentals

### The Flex Container

```css
.container {
    display: flex;  /* This makes it a flex container */
    
    /* Direction */
    flex-direction: row;        /* Default: left to right */
    flex-direction: column;      /* Top to bottom */
    flex-direction: row-reverse; /* Right to left */
    flex-direction: column-reverse; /* Bottom to top */
    
    /* Wrapping */
    flex-wrap: nowrap;  /* Default: single line */
    flex-wrap: wrap;    /* Wrap to multiple lines */
    
    /* Main Axis Alignment (horizontal if row) */
    justify-content: flex-start;    /* Default */
    justify-content: center;        /* Center items */
    justify-content: flex-end;      /* End of container */
    justify-content: space-between; /* Space between items */
    justify-content: space-around;  /* Space around items */
    justify-content: space-evenly;  /* Equal space */
    
    /* Cross Axis Alignment (vertical if row) */
    align-items: stretch;     /* Default: fill height */
    align-items: flex-start;  /* Top */
    align-items: center;      /* Middle */
    align-items: flex-end;    /* Bottom */
    
    /* Gap between items */
    gap: 20px;
}
```

### Flex Items

```css
.item {
    /* Flexibility */
    flex-grow: 1;    /* Grow to fill space */
    flex-shrink: 1;  /* Shrink if needed */
    flex-basis: 200px; /* Starting size */
    
    /* Shorthand */
    flex: 1 1 200px;  /* grow shrink basis */
    flex: 1;          /* Commonly used: grow equally */
    
    /* Individual alignment */
    align-self: center; /* Override container's align-items */
}
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
    <title>Photo Gallery - Flexbox</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <!-- Navigation -->
    <nav class="navbar">
        <div class="nav-brand">PhotoGallery</div>
        <ul class="nav-menu">
            <li><a href="#home">Home</a></li>
            <li><a href="#gallery">Gallery</a></li>
            <li><a href="#about">About</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
    </nav>
    
    <!-- Hero Section -->
    <header class="hero">
        <div class="hero-content">
            <h1>Beautiful Moments</h1>
            <p>A curated collection of stunning photography</p>
            <button class="cta-button">Explore Gallery</button>
        </div>
    </header>
    
    <!-- Gallery Section -->
    <main class="container">
        <section class="gallery-section">
            <h2 class="section-title">Photo Gallery</h2>
            
            <div class="gallery-grid">
                <!-- Photo Cards -->
                <div class="photo-card">
                    <div class="photo" style="background-color: #e74c3c;">
                        <div class="photo-overlay">
                            <h3>Sunset</h3>
                            <p>Golden hour magic</p>
                        </div>
                    </div>
                </div>
                
                <div class="photo-card">
                    <div class="photo" style="background-color: #3498db;">
                        <div class="photo-overlay">
                            <h3>Ocean</h3>
                            <p>Deep blue waters</p>
                        </div>
                    </div>
                </div>
                
                <div class="photo-card">
                    <div class="photo" style="background-color: #2ecc71;">
                        <div class="photo-overlay">
                            <h3>Forest</h3>
                            <p>Nature's embrace</p>
                        </div>
                    </div>
                </div>
                
                <div class="photo-card">
                    <div class="photo" style="background-color: #f39c12;">
                        <div class="photo-overlay">
                            <h3>Desert</h3>
                            <p>Golden sands</p>
                        </div>
                    </div>
                </div>
                
                <div class="photo-card">
                    <div class="photo" style="background-color: #9b59b6;">
                        <div class="photo-overlay">
                            <h3>Mountains</h3>
                            <p>Peaks and valleys</p>
                        </div>
                    </div>
                </div>
                
                <div class="photo-card">
                    <div class="photo" style="background-color: #1abc9c;">
                        <div class="photo-overlay">
                            <h3>Lake</h3>
                            <p>Calm reflections</p>
                        </div>
                    </div>
                </div>
                
                <div class="photo-card">
                    <div class="photo" style="background-color: #34495e;">
                        <div class="photo-overlay">
                            <h3>City</h3>
                            <p>Urban landscape</p>
                        </div>
                    </div>
                </div>
                
                <div class="photo-card">
                    <div class="photo" style="background-color: #e67e22;">
                        <div class="photo-overlay">
                            <h3>Autumn</h3>
                            <p>Fall colors</p>
                        </div>
                    </div>
                </div>
                
                <div class="photo-card">
                    <div class="photo" style="background-color: #16a085;">
                        <div class="photo-overlay">
                            <h3>Spring</h3>
                            <p>New beginnings</p>
                        </div>
                    </div>
                </div>
                
                <div class="photo-card">
                    <div class="photo" style="background-color: #c0392b;">
                        <div class="photo-overlay">
                            <h3>Winter</h3>
                            <p>Snowy wonderland</p>
                        </div>
                    </div>
                </div>
                
                <div class="photo-card">
                    <div class="photo" style="background-color: #8e44ad;">
                        <div class="photo-overlay">
                            <h3>Night</h3>
                            <p>Starry skies</p>
                        </div>
                    </div>
                </div>
                
                <div class="photo-card">
                    <div class="photo" style="background-color: #27ae60;">
                        <div class="photo-overlay">
                            <h3>Garden</h3>
                            <p>Blooming flowers</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        
        <!-- Featured Section -->
        <section class="featured-section">
            <h2 class="section-title">Featured Collections</h2>
            <div class="featured-cards">
                <div class="feature-card">
                    <h3>Nature</h3>
                    <p>Explore the beauty of natural landscapes</p>
                    <button>View Collection</button>
                </div>
                <div class="feature-card">
                    <h3>Urban</h3>
                    <p>Discover city life and architecture</p>
                    <button>View Collection</button>
                </div>
                <div class="feature-card">
                    <h3>Wildlife</h3>
                    <p>Get close to amazing creatures</p>
                    <button>View Collection</button>
                </div>
            </div>
        </section>
    </main>
    
    <!-- Footer -->
    <footer class="footer">
        <div class="footer-content">
            <div class="footer-section">
                <h4>About</h4>
                <p>Showcasing beautiful photography from around the world.</p>
            </div>
            <div class="footer-section">
                <h4>Links</h4>
                <ul>
                    <li><a href="#">Home</a></li>
                    <li><a href="#">Gallery</a></li>
                    <li><a href="#">Contact</a></li>
                </ul>
            </div>
            <div class="footer-section">
                <h4>Follow</h4>
                <div class="social-links">
                    <a href="#">Instagram</a>
                    <a href="#">Twitter</a>
                    <a href="#">Facebook</a>
                </div>
            </div>
        </div>
        <div class="footer-bottom">
            <p>&copy; 2025 PhotoGallery. All rights reserved.</p>
        </div>
    </footer>
</body>
</html>
```

### CSS (styles.css)
```css
/* ===== RESET ===== */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Arial', sans-serif;
    line-height: 1.6;
    color: #333;
}

/* ===== NAVIGATION (FLEXBOX) ===== */
.navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #2c3e50;
    padding: 1rem 5%;
    position: sticky;
    top: 0;
    z-index: 100;
    box-shadow: 0 2px 5px rgba(0,0,0,0.1);
}

.nav-brand {
    font-size: 1.5rem;
    font-weight: bold;
    color: white;
}

.nav-menu {
    display: flex;
    list-style: none;
    gap: 2rem;
}

.nav-menu a {
    color: white;
    text-decoration: none;
    transition: color 0.3s;
}

.nav-menu a:hover {
    color: #3498db;
}

/* ===== HERO SECTION (FLEXBOX CENTERING) ===== */
.hero {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 400px;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    text-align: center;
}

.hero-content h1 {
    font-size: 3rem;
    margin-bottom: 1rem;
}

.hero-content p {
    font-size: 1.2rem;
    margin-bottom: 2rem;
}

.cta-button {
    padding: 12px 30px;
    font-size: 1.1rem;
    background-color: white;
    color: #667eea;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: transform 0.3s;
}

.cta-button:hover {
    transform: translateY(-3px);
}

/* ===== CONTAINER ===== */
.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 40px 20px;
}

.section-title {
    font-size: 2.5rem;
    text-align: center;
    margin-bottom: 40px;
    color: #2c3e50;
}

/* ===== GALLERY GRID (FLEXBOX WITH WRAP) ===== */
.gallery-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    justify-content: center;
}

.photo-card {
    flex: 0 1 calc(33.333% - 20px);
    min-width: 250px;
}

.photo {
    height: 300px;
    border-radius: 10px;
    display: flex;
    align-items: flex-end;
    position: relative;
    overflow: hidden;
    cursor: pointer;
    transition: transform 0.3s;
}

.photo:hover {
    transform: scale(1.05);
}

.photo-overlay {
    background: linear-gradient(transparent, rgba(0,0,0,0.8));
    width: 100%;
    padding: 20px;
    color: white;
    transform: translateY(100%);
    transition: transform 0.3s;
}

.photo:hover .photo-overlay {
    transform: translateY(0);
}

.photo-overlay h3 {
    font-size: 1.5rem;
    margin-bottom: 5px;
}

/* ===== FEATURED CARDS (FLEXBOX) ===== */
.featured-section {
    margin-top: 60px;
}

.featured-cards {
    display: flex;
    gap: 30px;
    justify-content: space-between;
}

.feature-card {
    flex: 1;
    background-color: #f8f9fa;
    padding: 30px;
    border-radius: 10px;
    text-align: center;
    transition: all 0.3s;
}

.feature-card:hover {
    background-color: #e9ecef;
    transform: translateY(-5px);
}

.feature-card h3 {
    font-size: 1.8rem;
    margin-bottom: 15px;
    color: #2c3e50;
}

.feature-card p {
    margin-bottom: 20px;
    color: #7f8c8d;
}

.feature-card button {
    padding: 10px 25px;
    background-color: #3498db;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s;
}

.feature-card button:hover {
    background-color: #2980b9;
}

/* ===== FOOTER (FLEXBOX) ===== */
.footer {
    background-color: #2c3e50;
    color: white;
    margin-top: 60px;
}

.footer-content {
    display: flex;
    justify-content: space-between;
    max-width: 1200px;
    margin: 0 auto;
    padding: 40px 20px;
    gap: 40px;
}

.footer-section {
    flex: 1;
}

.footer-section h4 {
    margin-bottom: 15px;
    font-size: 1.2rem;
}

.footer-section ul {
    list-style: none;
}

.footer-section a {
    color: #bdc3c7;
    text-decoration: none;
    transition: color 0.3s;
}

.footer-section a:hover {
    color: #3498db;
}

.social-links {
    display: flex;
    gap: 15px;
}

.footer-bottom {
    text-align: center;
    padding: 20px;
    background-color: #1a252f;
}

/* ===== RESPONSIVE ===== */
@media (max-width: 768px) {
    .nav-menu {
        flex-direction: column;
        gap: 1rem;
    }
    
    .hero-content h1 {
        font-size: 2rem;
    }
    
    .photo-card {
        flex: 0 1 calc(50% - 20px);
    }
    
    .featured-cards {
        flex-direction: column;
    }
    
    .footer-content {
        flex-direction: column;
    }
}

@media (max-width: 480px) {
    .photo-card {
        flex: 0 1 100%;
    }
}
```

---

## 📖 Flexbox Cheat Sheet

### Common Patterns

**Centering (horizontal & vertical)**:
```css
.container {
    display: flex;
    justify-content: center;
    align-items: center;
}
```

**Navigation Bar**:
```css
.nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
```

**Equal Width Columns**:
```css
.container {
    display: flex;
}
.item {
    flex: 1;  /* All items equal width */
}
```

**Gallery Grid**:
```css
.gallery {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
}
.item {
    flex: 0 1 calc(33.333% - 20px);
}
```

---

## ✅ Self-Assessment

- [ ] Navigation uses Flexbox
- [ ] Photo gallery wraps properly
- [ ] Centered content with Flexbox
- [ ] Footer with space-between
- [ ] Used multiple justify-content values
- [ ] Used multiple align-items values
- [ ] Gallery has 12+ photos
- [ ] Hover effects work
- [ ] Responsive on mobile
- [ ] All layouts use Flexbox

---

**Next**: [Assignment 5: CSS Grid](../assignment-05-css-grid/ASSIGNMENT_5_GUIDE.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

