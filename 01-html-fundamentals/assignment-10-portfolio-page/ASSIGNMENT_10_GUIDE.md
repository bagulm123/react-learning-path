# Assignment 10: Portfolio Page - HTML Capstone Project

**By Mahendra Bagul**

Congratulations! You've learned all the HTML fundamentals. Now it's time to put it all together in one complete, professional portfolio website.

---

## 📚 What You'll Demonstrate

- ✅ Complete HTML document structure
- ✅ Semantic HTML5 elements
- ✅ Text formatting and content organization
- ✅ Lists and navigation
- ✅ Images and media
- ✅ Tables (for skills/timeline)
- ✅ Contact form
- ✅ Accessibility best practices
- ✅ All previous concepts combined

---

## 🎯 Assignment Objectives

Create a **complete personal portfolio website** showcasing your HTML skills and projects. This will be a real portfolio you can use!

**Difficulty**: ⭐⭐⭐⭐⭐  
**Time**: 6-8 hours  
**Prerequisites**: Assignments 1-9 completed

---

## 📋 Requirements

### Must Have
1. ✅ Multi-page website (Home, About, Projects, Contact)
2. ✅ Professional navigation on all pages
3. ✅ Hero section with introduction
4. ✅ About section with your background
5. ✅ Projects showcase (at least 3)
6. ✅ Skills table or list
7. ✅ Contact form (working HTML)
8. ✅ Footer with social links
9. ✅ Semantic HTML throughout
10. ✅ Fully accessible
11. ✅ All images with alt text
12. ✅ Proper heading hierarchy

### Nice to Have
- ✨ Timeline of education/experience
- ✨ Testimonials section
- ✨ Blog page
- ✨ Resume download link
- ✨ Multiple language support

---

## 🏗️ Page Structure

### 1. Home Page (index.html)
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Portfolio of [Your Name] - Web Developer">
    <title>[Your Name] - Web Developer Portfolio</title>
</head>
<body>
    <!-- Skip link for accessibility -->
    <a href="#main" class="skip-link">Skip to main content</a>
    
    <!-- Header & Navigation -->
    <header>
        <nav role="navigation">
            <ul>
                <li><a href="index.html">Home</a></li>
                <li><a href="about.html">About</a></li>
                <li><a href="projects.html">Projects</a></li>
                <li><a href="contact.html">Contact</a></li>
            </ul>
        </nav>
    </header>
    
    <!-- Main Content -->
    <main id="main">
        <!-- Hero Section -->
        <section class="hero">
            <h1>Hi, I'm [Your Name]</h1>
            <p>Web Developer | HTML Expert | Lifelong Learner</p>
        </section>
        
        <!-- Featured Projects -->
        <section>
            <h2>Featured Projects</h2>
            <article>
                <h3>Project 1</h3>
                <figure>
                    <img src="project1.jpg" alt="Project 1 screenshot">
                    <figcaption>Description of project</figcaption>
                </figure>
            </article>
            <!-- More projects -->
        </section>
    </main>
    
    <!-- Footer -->
    <footer>
        <nav aria-label="Social media">
            <ul>
                <li><a href="#">GitHub</a></li>
                <li><a href="#">LinkedIn</a></li>
                <li><a href="#">Twitter</a></li>
            </ul>
        </nav>
        <p>&copy; 2025 [Your Name]. All rights reserved.</p>
    </footer>
</body>
</html>
```

### 2. About Page (about.html)
- Professional bio
- Skills table
- Education/Experience timeline
- Personal interests

### 3. Projects Page (projects.html)
- Showcase all 9 previous HTML assignments
- Include screenshots (can be placeholder)
- Brief description of each
- Technologies used
- Links (if hosted)

### 4. Contact Page (contact.html)
- Contact form (name, email, message)
- Alternative contact methods
- Social media links

---

## ✅ Self-Assessment Checklist

### Structure & Semantics
- [ ] Proper HTML5 document structure
- [ ] Semantic elements used correctly
- [ ] Heading hierarchy is logical
- [ ] Each page has one h1

### Navigation
- [ ] Navigation menu on all pages
- [ ] Current page indicated
- [ ] All links work correctly
- [ ] Breadcrumb navigation (optional)

### Content
- [ ] Professional, error-free writing
- [ ] All images have descriptive alt text
- [ ] Contact information provided
- [ ] Projects showcased effectively

### Accessibility
- [ ] Skip navigation link
- [ ] ARIA labels where needed
- [ ] Keyboard navigation works
- [ ] Passes WAVE/axe checker
- [ ] Forms are accessible

### Technical
- [ ] HTML validates (W3C validator)
- [ ] Meta tags present
- [ ] Character encoding set
- [ ] Viewport meta tag for responsive

---

## 💡 Content Ideas

### About Section
- Your journey into web development
- What motivates you
- Skills and technologies
- Education background
- Career goals

### Projects to Include
1. Hello World (Assignment 1)
2. Learning Journal (Assignment 2)
3. Recipe Website (Assignment 3)
4. Photo Gallery (Assignment 4)
5. Statistics Dashboard (Assignment 5)
6. Registration Forms (Assignment 6)
7. Tech Blog (Assignment 7)
8. HTML5 Showcase (Assignment 8)
9. Accessible Website (Assignment 9)

### Skills Table Example
```html
<table>
    <caption>My Web Development Skills</caption>
    <thead>
        <tr>
            <th>Technology</th>
            <th>Proficiency</th>
            <th>Experience</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>HTML5</td>
            <td>⭐⭐⭐⭐⭐</td>
            <td>10 Projects</td>
        </tr>
        <!-- More skills -->
    </tbody>
</table>
```

---

## 🎨 Design Tips (For Now, Structure Only)

Remember: This is HTML-only. It won't look pretty yet - that's okay! Focus on:
- Clear content hierarchy
- Logical organization
- Proper semantics
- Accessibility

**You'll style it with CSS in Phase 2!**

---

## 🚀 Going Further

1. **Validate your HTML** - Use W3C validator
2. **Test accessibility** - Use WAVE or axe
3. **Get feedback** - Share with friends/community
4. **Keep updating** - Add new projects as you build them
5. **Prepare for CSS** - This portfolio will look amazing once styled!

---

## 🎉 Congratulations!

You've completed **HTML Fundamentals**! 🎊

You can now:
- ✅ Structure any webpage from scratch
- ✅ Use semantic HTML correctly
- ✅ Create accessible websites
- ✅ Build forms and tables
- ✅ Organize content effectively
- ✅ Use HTML5 features

### Your Progress
- ✅ Phase 1: HTML Fundamentals - **COMPLETE!**
- ⏳ Phase 2: CSS Fundamentals - Up next!
- ⏳ Phase 3: JavaScript Fundamentals
- ⏳ Phase 4: TypeScript Fundamentals
- ⏳ Phase 5: React Mastery

---

## 📚 What's Next?

**Ready for CSS?** → [Phase 2: CSS Fundamentals](../../02-css-fundamentals/README.md)

In CSS, you'll learn to:
- Style your portfolio beautifully
- Create responsive layouts
- Add animations and transitions
- Use modern CSS features

**See you in Phase 2!** 🎨

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)  
**Phase 1: HTML Fundamentals** - COMPLETE! 🏆

