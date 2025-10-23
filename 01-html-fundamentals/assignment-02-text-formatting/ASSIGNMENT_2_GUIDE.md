# Assignment 2: Text Formatting - Making Text Meaningful

**By Mahendra Bagul**

Now that you've mastered basic HTML structure, let's make your text more expressive! 

In Assignment 1, all your text looked the same. But on real websites, you see **bold** text, *italics*, `code snippets`, and more. That's what we're learning today!

---

## 📚 What You'll Learn

### Core Concepts
- ✅ Bold text with `<strong>` and `<b>`
- ✅ Italic text with `<em>` and `<i>`
- ✅ Underlined text with `<u>`
- ✅ Strikethrough text with `<s>` or `<del>`
- ✅ Superscript (`<sup>`) and subscript (`<sub>`)
- ✅ Inline code with `<code>`
- ✅ Preformatted text with `<pre>`
- ✅ Blockquotes with `<blockquote>`
- ✅ Abbreviations with `<abbr>`
- ✅ Marked/highlighted text with `<mark>`
- ✅ Small text with `<small>`

### Skills You'll Build
- Using semantic HTML (tags with meaning)
- Understanding inline vs block elements
- Combining multiple formatting tags
- Creating readable, well-formatted content

---

## 🎯 Assignment Objectives

Create a "Learning Journal" webpage showcasing your web development journey using various text formatting tags.

**Difficulty**: ⭐⭐☆☆☆ (Easy)  
**Estimated Time**: 2-3 hours  
**Prerequisites**: Assignment 1 completed

---

## 📋 Requirements

### Must Have (Required)
1. ✅ Proper HTML document structure
2. ✅ Use `<strong>` for important text (at least 3 times)
3. ✅ Use `<em>` for emphasized text (at least 3 times)
4. ✅ Use `<mark>` to highlight key points (at least 2 times)
5. ✅ Use `<code>` for inline code snippets (at least 2 times)
6. ✅ Use `<pre>` with `<code>` for a code block
7. ✅ Use `<blockquote>` for a quote (at least 1)
8. ✅ Use `<sup>` and `<sub>` appropriately (at least once each)
9. ✅ Use `<abbr>` for abbreviations (at least 2)
10. ✅ Use `<small>` for fine print/side notes

### Nice to Have (Optional)
- ✨ Use `<del>` and `<ins>` to show edits
- ✨ Combine multiple formatting tags creatively
- ✨ Add footnotes using `<sup>`
- ✨ Include a formatted code example

---

## 📖 Concepts Explained

### Semantic vs Non-Semantic Tags

**Semantic tags** have meaning beyond just appearance:
- `<strong>` = Important, strong importance (usually bold)
- `<em>` = Emphasized, stress emphasis (usually italic)

**Non-semantic tags** only affect appearance:
- `<b>` = Bold (just makes text bold, no meaning)
- `<i>` = Italic (just makes text italic, no meaning)

**Why use semantic tags?**
- Screen readers understand them (better accessibility)
- Search engines understand importance
- Better for SEO
- More meaningful code

### Inline vs Block Elements

**Inline elements** (don't start new lines):
- `<strong>`, `<em>`, `<code>`, `<mark>`, `<small>`
- Flow within text like normal words

**Block elements** (start new lines):
- `<blockquote>`, `<pre>`
- Take up full width available

---

## 💻 Key HTML Tags Explained

### 1. Strong & Bold

```html
<!-- Semantic (preferred) -->
<p>This is <strong>very important</strong> text!</p>

<!-- Non-semantic -->
<p>This is <b>bold</b> text.</p>
```

**When to use:**
- `<strong>`: Important information, warnings, key points
- `<b>`: Just visual bold, no special importance

### 2. Emphasis & Italic

```html
<!-- Semantic (preferred) -->
<p>I <em>really</em> love coding!</p>

<!-- Non-semantic -->
<p><i>This is just italic</i></p>
```

**When to use:**
- `<em>`: Stress emphasis, change in meaning
- `<i>`: Technical terms, foreign phrases, thoughts

### 3. Mark (Highlighting)

```html
<p>Remember: <mark>HTML</mark> structures content, <mark>CSS</mark> styles it!</p>
```

**Appears as yellow highlight** (like marking with a highlighter pen)

### 4. Code Tags

**Inline code**:
```html
<p>Use the <code>&lt;strong&gt;</code> tag for important text.</p>
```

**Code blocks**:
```html
<pre><code>
function greet() {
    console.log("Hello World!");
}
</code></pre>
```

**Difference:**
- `<code>`: Inline, for short code snippets
- `<pre>`: Preserves formatting (spaces, line breaks)
- Together: Perfect for code blocks!

### 5. Blockquote (Quotes)

```html
<blockquote>
    <p>"The only way to learn a new programming language is by writing programs in it."</p>
    <footer>— Dennis Ritchie</footer>
</blockquote>
```

**Use for:**
- Quotes from people
- Citations from sources
- Pulled-out important text

### 6. Superscript & Subscript

```html
<!-- Superscript (above) -->
<p>E = mc<sup>2</sup></p>
<p>10<sup>th</sup> of January</p>

<!-- Subscript (below) -->
<p>H<sub>2</sub>O is water</p>
```

### 7. Abbreviations

```html
<p>I'm learning <abbr title="HyperText Markup Language">HTML</abbr> and <abbr title="Cascading Style Sheets">CSS</abbr>!</p>
```

**Hover over the abbreviation to see the full meaning!**

### 8. Small Text

```html
<p><small>This is fine print or side notes</small></p>
```

### 9. Delete & Insert (Track Changes)

```html
<p>My favorite language is <del>Java</del> <ins>JavaScript</ins>!</p>
```

Shows edits/changes (deleted = strikethrough, inserted = underlined)

---

## 🏗️ Step-by-Step Implementation

### Step 1: Create Your HTML File

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Learning Journal - Text Formatting</title>
</head>
<body>
    <h1>My Web Development Learning Journal</h1>
    
    <!-- Content goes here -->
</body>
</html>
```

### Step 2: Add an Introduction with Formatting

```html
    <!-- Introduction -->
    <h2>Why I'm Learning Web Development</h2>
    <p>
        I've always been <em>fascinated</em> by how websites work. The idea that
        I can <strong>create something from nothing</strong> using just code is
        incredibly exciting! Today, I'm learning about <mark>text formatting in HTML</mark>.
    </p>
```

### Step 3: Add a Section About HTML & CSS

```html
    <hr>
    
    <h2>What I've Learned So Far</h2>
    <p>
        In my journey, I've discovered that web development has three core technologies:
    </p>
    <ul>
        <li><strong><abbr title="HyperText Markup Language">HTML</abbr></strong> - Structure</li>
        <li><strong><abbr title="Cascading Style Sheets">CSS</abbr></strong> - Styling</li>
        <li><strong><abbr title="JavaScript">JS</abbr></strong> - Interactivity</li>
    </ul>
    <p>
        <mark>HTML is the foundation</mark> of every webpage. Without it, you can't build anything!
    </p>
```

### Step 4: Add a Code Example

```html
    <hr>
    
    <h2>My First HTML Code</h2>
    <p>
        Here's the <em>very first</em> code I wrote. I'll never forget how <strong>amazing</strong> 
        it felt when it worked!
    </p>
    
    <pre><code>&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
    &lt;title&gt;Hello World&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;h1&gt;Hello World!&lt;/h1&gt;
&lt;/body&gt;
&lt;/html&gt;</code></pre>
    
    <p>
        <small>Note: I now use <code>&lt;strong&gt;</code> instead of <code>&lt;b&gt;</code> because it's semantic!</small>
    </p>
```

### Step 5: Add an Inspiring Quote

```html
    <hr>
    
    <h2>My Motivation</h2>
    <blockquote>
        <p>"The best time to plant a tree was 20 years ago. The second best time is now."</p>
        <footer>— Chinese Proverb</footer>
    </blockquote>
    <p>
        This quote reminds me that it's <em>never too late</em> to start learning something new.
        Even if I didn't start coding years ago, <mark>starting today is what matters</mark>!
    </p>
```

### Step 6: Add Fun Facts Section

```html
    <hr>
    
    <h2>Fun Facts I Learned</h2>
    <p>
        Did you know? The first website went live on <strong>August 6<sup>th</sup>, 1991</strong>!
        That's over 30 years ago!
    </p>
    <p>
        Also, water (H<sub>2</sub>O) and energy (E=mc<sup>2</sup>) aren't just science formulas -
        they can be written in HTML too!
    </p>
```

### Step 7: Add Goals with Tracked Changes

```html
    <hr>
    
    <h2>My Goals</h2>
    <p>
        Original goal: Learn <del>web design</del> in 6 months.<br>
        Updated goal: Learn <ins>full-stack web development</ins> in 1 year!
    </p>
    <p>
        Why the change? I realized I want to build <strong>complete applications</strong>,
        not just design websites. That requires knowing both <em>frontend and backend</em>!
    </p>
```

---

## 💻 Complete Example Code

See [`index.html`](./index.html) in this folder for a complete working example!

Here's a condensed version:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Learning Journal - Text Formatting</title>
</head>
<body>
    <h1>My Web Development Learning Journey</h1>
    
    <h2>Introduction</h2>
    <p>
        I'm <strong>excited</strong> to share my journey learning
        <abbr title="HyperText Markup Language">HTML</abbr>! This is my
        <em>second assignment</em> and I'm already seeing <mark>huge progress</mark>.
    </p>
    
    <hr>
    
    <h2>What I Learned Today</h2>
    <p>
        Today I learned about <strong>semantic HTML</strong>. The difference between
        <code>&lt;strong&gt;</code> and <code>&lt;b&gt;</code> is fascinating!
    </p>
    
    <blockquote>
        <p>"First, solve the problem. Then, write the code."</p>
        <footer>— John Johnson</footer>
    </blockquote>
    
    <hr>
    
    <h2>My First Code Block</h2>
    <pre><code>&lt;p&gt;Hello &lt;strong&gt;World&lt;/strong&gt;!&lt;/p&gt;</code></pre>
    
    <p><small>Created on January 10<sup>th</sup>, 2025</small></p>
    
</body>
</html>
```

---

## ✅ Self-Assessment Checklist

- [ ] Used `<strong>` for at least 3 important words/phrases
- [ ] Used `<em>` for at least 3 emphasized words/phrases
- [ ] Used `<mark>` to highlight key points (2+)
- [ ] Used `<code>` for inline code mentions (2+)
- [ ] Used `<pre><code>` for a formatted code block
- [ ] Included at least one `<blockquote>` with a quote
- [ ] Used `<sup>` for superscript (e.g., dates, math)
- [ ] Used `<sub>` for subscript (e.g., chemical formulas)
- [ ] Used `<abbr>` with title attribute (2+)
- [ ] Used `<small>` for fine print/notes
- [ ] All HTML is properly structured and indented
- [ ] Page displays correctly in browser

---

## 🎨 UI Mockup

See [`UI_MOCKUP.md`](./UI_MOCKUP.md) for visual examples!

---

## 🐛 Common Mistakes

### 1. Confusing `<strong>` with `<b>`

**Problem**: Using `<b>` everywhere instead of `<strong>`.

**Solution**: Use `<strong>` for important content, `<b>` only for visual styling without meaning.

### 2. Forgetting to Escape HTML in Code Blocks

**Problem**: Browser tries to render HTML inside `<code>`.

**Solution**: Use HTML entities:
- `<` becomes `&lt;`
- `>` becomes `&gt;`
- `&` becomes `&amp;`

### 3. Missing Title in `<abbr>`

**Problem**: Abbreviation doesn't show tooltip.

**Solution**: Always add `title` attribute:
```html
<abbr title="Cascading Style Sheets">CSS</abbr>
```

---

## 💡 Tips for Success

1. **Use semantic tags first**: Prefer `<strong>` and `<em>` over `<b>` and `<i>`
2. **Don't overuse formatting**: Too much bold/italic makes nothing stand out
3. **Test in browser**: See how formatting actually looks
4. **Hover over abbreviations**: Make sure tooltips work
5. **Check code blocks**: Ensure they preserve formatting

---

## 🚀 Going Further

Try these challenges:

1. **Create a recipe page** using formatting (ingredients, steps)
2. **Write a mini tutorial** with code examples
3. **Make a quote collection** using `<blockquote>`
4. **Create a glossary** using `<abbr>` for terms
5. **Write a changelog** using `<del>` and `<ins>`

---

## 📚 Key Takeaways

- ✅ Semantic tags (`<strong>`, `<em>`) are better than non-semantic (`<b>`, `<i>`)
- ✅ `<code>` and `<pre>` are perfect for code snippets
- ✅ `<mark>` highlights important text
- ✅ `<abbr>` provides tooltips for abbreviations
- ✅ Formatting makes content more readable and meaningful

---

**Next Assignment**: [Assignment 3: Lists & Links](../assignment-03-lists-links/ASSIGNMENT_3_GUIDE.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)  
**Course**: Complete React Learning Path  
**Phase**: 01 - HTML Fundamentals

