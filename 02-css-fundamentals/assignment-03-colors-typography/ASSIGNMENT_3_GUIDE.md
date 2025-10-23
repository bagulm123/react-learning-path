# Assignment 3: Colors & Typography - Beautiful Text Design

**By Mahendra Bagul**

Great typography can make or break a design. Colors set the mood. Together, they're the foundation of beautiful web design!

---

## 📚 What You'll Learn

- ✅ Color formats (hex, RGB, RGBA, HSL)
- ✅ Color theory basics
- ✅ Font properties (family, size, weight, style)
- ✅ Google Fonts integration
- ✅ Text styling (alignment, decoration, spacing)
- ✅ Line-height and letter-spacing
- ✅ Text shadows
- ✅ Web-safe fonts vs custom fonts

---

## 🎯 Assignment Objectives

Create a "Typography Showcase Website" demonstrating beautiful text design and color combinations.

**Difficulty**: ⭐⭐⭐☆☆  
**Time**: 4-5 hours  
**Prerequisites**: CSS Assignments 1-2

---

## 📋 Requirements

### Must Have
1. ✅ At least 5 different color formats used
2. ✅ At least 3 Google Fonts imported
3. ✅ Heading hierarchy with distinct styles (h1-h6)
4. ✅ At least 3 different font weights
5. ✅ Text shadows on headings
6. ✅ Color palette demonstration (3-5 colors)
7. ✅ Line-height and letter-spacing adjustments
8. ✅ Text alignment variations
9. ✅ Readable paragraphs (optimal line length)
10. ✅ Hover effects with color transitions

---

## 🎨 Colors in CSS

### Color Formats

```css
/* Hex (most common) */
.color1 { color: #3498db; }

/* RGB */
.color2 { color: rgb(52, 152, 219); }

/* RGBA (with transparency) */
.color3 { color: rgba(52, 152, 219, 0.8); }

/* HSL (Hue, Saturation, Lightness) */
.color4 { color: hsl(204, 70%, 53%); }

/* HSLA (with transparency) */
.color5 { color: hsla(204, 70%, 53%, 0.8); }

/* Named colors */
.color6 { color: dodgerblue; }
```

### Where to Use Colors

```css
.element {
    color: #333;                    /* Text color */
    background-color: #f0f0f0;      /* Background */
    border-color: #ddd;             /* Border */
}
```

---

## 📝 Typography in CSS

### Font Family

```css
body {
    /* System fonts (fallback chain) */
    font-family: Arial, Helvetica, sans-serif;
}

h1 {
    /* Google Font */
    font-family: 'Roboto', sans-serif;
}

code {
    /* Monospace for code */
    font-family: 'Courier New', monospace;
}
```

### Font Properties

```css
.text {
    font-size: 16px;              /* Size */
    font-weight: 700;             /* 100-900, or bold/normal */
    font-style: italic;           /* italic, normal, oblique */
    line-height: 1.6;             /* Space between lines */
    letter-spacing: 0.5px;        /* Space between letters */
    word-spacing: 2px;            /* Space between words */
}
```

### Text Styling

```css
.text {
    text-align: center;           /* left, right, center, justify */
    text-decoration: underline;   /* underline, line-through, none */
    text-transform: uppercase;    /* uppercase, lowercase, capitalize */
    text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
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
    <title>Typography Showcase</title>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700;900&family=Roboto:wght@300;400;700&family=Fira+Code&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header class="hero">
        <h1 class="hero-title">The Art of Typography</h1>
        <p class="hero-subtitle">Where design meets readability</p>
    </header>
    
    <main class="container">
        <!-- Color Palette Section -->
        <section class="section">
            <h2>Color Palette</h2>
            <div class="color-palette">
                <div class="color-swatch primary">
                    <span class="color-name">Primary</span>
                    <span class="color-code">#3498db</span>
                </div>
                <div class="color-swatch secondary">
                    <span class="color-name">Secondary</span>
                    <span class="color-code">#2ecc71</span>
                </div>
                <div class="color-swatch accent">
                    <span class="color-name">Accent</span>
                    <span class="color-code">#e74c3c</span>
                </div>
                <div class="color-swatch dark">
                    <span class="color-name">Dark</span>
                    <span class="color-code">#2c3e50</span>
                </div>
                <div class="color-swatch light">
                    <span class="color-name">Light</span>
                    <span class="color-code">#ecf0f1</span>
                </div>
            </div>
        </section>
        
        <!-- Typography Scale -->
        <section class="section">
            <h2>Typography Scale</h2>
            <div class="type-scale">
                <h1>Heading 1 - The largest heading</h1>
                <h2>Heading 2 - Major section heading</h2>
                <h3>Heading 3 - Sub-section heading</h3>
                <h4>Heading 4 - Minor heading</h4>
                <h5>Heading 5 - Small heading</h5>
                <h6>Heading 6 - Smallest heading</h6>
                <p>Paragraph text - Default body copy</p>
                <small>Small text - Fine print and captions</small>
            </div>
        </section>
        
        <!-- Font Families -->
        <section class="section">
            <h2>Font Families</h2>
            <div class="font-examples">
                <div class="font-card font-serif">
                    <h3>Serif Font</h3>
                    <p class="sample">The quick brown fox jumps over the lazy dog</p>
                    <p class="font-info">Playfair Display - Elegant, traditional</p>
                </div>
                <div class="font-card font-sans">
                    <h3>Sans-Serif Font</h3>
                    <p class="sample">The quick brown fox jumps over the lazy dog</p>
                    <p class="font-info">Roboto - Modern, clean</p>
                </div>
                <div class="font-card font-mono">
                    <h3>Monospace Font</h3>
                    <p class="sample">The quick brown fox jumps over the lazy dog</p>
                    <p class="font-info">Fira Code - Code, technical</p>
                </div>
            </div>
        </section>
        
        <!-- Font Weights -->
        <section class="section">
            <h2>Font Weights</h2>
            <div class="weight-examples">
                <p class="weight-300">Light (300) - Subtle and delicate</p>
                <p class="weight-400">Regular (400) - Standard body text</p>
                <p class="weight-700">Bold (700) - Strong emphasis</p>
                <p class="weight-900">Black (900) - Maximum impact</p>
            </div>
        </section>
        
        <!-- Text Styling -->
        <section class="section">
            <h2>Text Styling</h2>
            <div class="text-styles">
                <p class="uppercase">Uppercase text for headers</p>
                <p class="lowercase">lowercase for subtle text</p>
                <p class="capitalize">Capitalize Every Word</p>
                <p class="italic">Italic text for emphasis</p>
                <p class="underline">Underlined important text</p>
                <p class="strike">Strikethrough for removed text</p>
            </div>
        </section>
        
        <!-- Readable Paragraph -->
        <section class="section">
            <h2>Readable Paragraphs</h2>
            <div class="article">
                <p class="lead">
                    This is a lead paragraph with larger text to draw attention. 
                    It introduces the content that follows.
                </p>
                <p>
                    Typography is the art and technique of arranging type to make written 
                    language legible, readable and appealing. The arrangement of type involves 
                    selecting typefaces, point sizes, line lengths, line-spacing, and 
                    letter-spacing, and adjusting the space between pairs of letters.
                </p>
                <p>
                    Good typography should be invisible - readers shouldn't notice the design, 
                    they should simply enjoy reading. This requires careful attention to 
                    line length (45-75 characters is optimal), line height (1.5-1.8 for body text), 
                    and proper contrast between text and background.
                </p>
                <blockquote class="quote">
                    "Typography is what language looks like."
                    <cite>— Ellen Lupton</cite>
                </blockquote>
            </div>
        </section>
    </main>
</body>
</html>
```

### CSS (styles.css)
```css
/* ===== RESET & BASE ===== */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Roboto', Arial, sans-serif;
    font-size: 16px;
    line-height: 1.6;
    color: #2c3e50;
    background-color: #ecf0f1;
}

/* ===== HERO SECTION ===== */
.hero {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    text-align: center;
    padding: 100px 20px;
    margin-bottom: 40px;
}

.hero-title {
    font-family: 'Playfair Display', serif;
    font-size: 4em;
    font-weight: 900;
    margin-bottom: 15px;
    text-shadow: 3px 3px 6px rgba(0, 0, 0, 0.3);
    letter-spacing: -1px;
}

.hero-subtitle {
    font-size: 1.5em;
    font-weight: 300;
    letter-spacing: 2px;
    text-transform: uppercase;
    opacity: 0.9;
}

/* ===== CONTAINER ===== */
.container {
    max-width: 1000px;
    margin: 0 auto;
    padding: 20px;
}

.section {
    background-color: white;
    padding: 40px;
    margin-bottom: 30px;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.section h2 {
    font-family: 'Playfair Display', serif;
    font-size: 2.5em;
    color: #2c3e50;
    margin-bottom: 30px;
    border-bottom: 3px solid #3498db;
    padding-bottom: 10px;
}

/* ===== COLOR PALETTE ===== */
.color-palette {
    display: flex;
    gap: 15px;
    flex-wrap: wrap;
    justify-content: center;
}

.color-swatch {
    width: 150px;
    height: 150px;
    border-radius: 10px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    color: white;
    font-weight: bold;
    transition: transform 0.3s ease;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.color-swatch:hover {
    transform: translateY(-5px);
    box-shadow: 0 6px 12px rgba(0, 0, 0, 0.2);
}

.color-name {
    font-size: 1.1em;
    margin-bottom: 5px;
}

.color-code {
    font-family: 'Fira Code', monospace;
    font-size: 0.9em;
    opacity: 0.9;
}

.primary { background-color: #3498db; }
.secondary { background-color: #2ecc71; }
.accent { background-color: #e74c3c; }
.dark { background-color: #2c3e50; }
.light { 
    background-color: #ecf0f1; 
    color: #2c3e50;
    border: 2px solid #bdc3c7;
}

/* ===== TYPOGRAPHY SCALE ===== */
.type-scale h1 { 
    font-size: 3em; 
    font-weight: 900;
    margin: 20px 0;
    color: #2c3e50;
}

.type-scale h2 { 
    font-size: 2.5em; 
    font-weight: 700;
    margin: 18px 0;
    color: #34495e;
}

.type-scale h3 { 
    font-size: 2em; 
    font-weight: 700;
    margin: 16px 0;
    color: #34495e;
}

.type-scale h4 { 
    font-size: 1.5em; 
    font-weight: 600;
    margin: 14px 0;
    color: #7f8c8d;
}

.type-scale h5 { 
    font-size: 1.25em; 
    font-weight: 600;
    margin: 12px 0;
    color: #7f8c8d;
}

.type-scale h6 { 
    font-size: 1em; 
    font-weight: 600;
    margin: 10px 0;
    color: #95a5a6;
}

.type-scale p {
    font-size: 1em;
    margin: 10px 0;
    line-height: 1.8;
}

.type-scale small {
    font-size: 0.875em;
    color: #7f8c8d;
}

/* ===== FONT FAMILIES ===== */
.font-examples {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 20px;
}

.font-card {
    padding: 25px;
    border-radius: 8px;
    background-color: #f8f9fa;
    border: 2px solid #dee2e6;
    transition: all 0.3s ease;
}

.font-card:hover {
    border-color: #3498db;
    box-shadow: 0 4px 8px rgba(52, 152, 219, 0.2);
}

.font-card h3 {
    margin-bottom: 15px;
    color: #2c3e50;
}

.font-card .sample {
    font-size: 1.2em;
    margin: 15px 0;
    padding: 15px;
    background-color: white;
    border-radius: 5px;
}

.font-card .font-info {
    font-size: 0.9em;
    color: #7f8c8d;
    font-style: italic;
}

.font-serif .sample { 
    font-family: 'Playfair Display', serif; 
}

.font-sans .sample { 
    font-family: 'Roboto', sans-serif; 
}

.font-mono .sample { 
    font-family: 'Fira Code', monospace; 
}

/* ===== FONT WEIGHTS ===== */
.weight-examples p {
    font-size: 1.5em;
    margin: 15px 0;
}

.weight-300 { font-weight: 300; }
.weight-400 { font-weight: 400; }
.weight-700 { font-weight: 700; }
.weight-900 { font-weight: 900; }

/* ===== TEXT STYLING ===== */
.text-styles p {
    font-size: 1.3em;
    margin: 12px 0;
}

.uppercase { text-transform: uppercase; letter-spacing: 2px; }
.lowercase { text-transform: lowercase; }
.capitalize { text-transform: capitalize; }
.italic { font-style: italic; }
.underline { text-decoration: underline; }
.strike { text-decoration: line-through; }

/* ===== ARTICLE/READABLE TEXT ===== */
.article {
    max-width: 700px;
    margin: 0 auto;
}

.lead {
    font-size: 1.3em;
    font-weight: 300;
    line-height: 1.8;
    color: #34495e;
    margin-bottom: 25px;
}

.article p {
    margin-bottom: 20px;
    line-height: 1.8;
    text-align: justify;
}

.quote {
    font-family: 'Playfair Display', serif;
    font-size: 1.4em;
    font-style: italic;
    color: #34495e;
    padding: 30px;
    margin: 30px 0;
    border-left: 5px solid #3498db;
    background-color: #f8f9fa;
    border-radius: 0 8px 8px 0;
}

.quote cite {
    display: block;
    margin-top: 15px;
    font-size: 0.8em;
    font-style: normal;
    color: #7f8c8d;
}

/* ===== RESPONSIVE ===== */
@media (max-width: 768px) {
    .hero-title {
        font-size: 2.5em;
    }
    
    .hero-subtitle {
        font-size: 1.2em;
    }
    
    .section {
        padding: 25px;
    }
    
    .color-palette {
        gap: 10px;
    }
    
    .color-swatch {
        width: 120px;
        height: 120px;
    }
}
```

---

## 📖 Typography Best Practices

1. **Line Length**: 45-75 characters per line for readability
2. **Line Height**: 1.5-1.8 for body text, 1.2-1.4 for headings
3. **Font Size**: 16px minimum for body text
4. **Contrast**: 4.5:1 ratio for normal text, 3:1 for large text
5. **Font Pairing**: Max 2-3 fonts per site
6. **Hierarchy**: Clear size difference between heading levels

---

## ✅ Self-Assessment

- [ ] Used 5+ different color formats
- [ ] Integrated Google Fonts
- [ ] Created heading hierarchy (h1-h6)
- [ ] Applied various font weights
- [ ] Added text shadows
- [ ] Color palette with 3-5 colors
- [ ] Adjusted line-height and letter-spacing
- [ ] Paragraphs are readable (proper line length)
- [ ] Hover effects with transitions
- [ ] Responsive on mobile

---

**Next**: [Assignment 4: Flexbox Basics](../assignment-04-flexbox-basics/ASSIGNMENT_4_GUIDE.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

