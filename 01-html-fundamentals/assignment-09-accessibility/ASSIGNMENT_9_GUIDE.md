# Assignment 9: Accessibility - Building for Everyone

**By Mahendra Bagul**

Accessibility (a11y) ensures everyone can use your website, including people with disabilities. It's not optional - it's essential!

---

## 📚 What You'll Learn

- ✅ ARIA attributes and roles
- ✅ Semantic HTML for accessibility
- ✅ Keyboard navigation
- ✅ Screen reader compatibility
- ✅ Alt text best practices
- ✅ Focus management
- ✅ Color contrast
- ✅ WCAG guidelines basics

---

## 🎯 Assignment Objectives

Create a "Fully Accessible Website" that works perfectly with screen readers and keyboard navigation.

**Difficulty**: ⭐⭐⭐⭐⭐  
**Time**: 4-5 hours  
**Prerequisites**: Assignments 1-8

---

## 📋 Requirements

### Must Have
1. ✅ Semantic HTML throughout
2. ✅ Proper heading hierarchy
3. ✅ ARIA landmarks
4. ✅ ARIA labels where needed
5. ✅ Skip navigation link
6. ✅ Keyboard accessible (Tab navigation)
7. ✅ Focus indicators visible
8. ✅ Meaningful alt text for images
9. ✅ Form labels properly associated
10. ✅ Passes WAVE or axe accessibility checker

---

## 💻 Accessibility Techniques

### ARIA Landmarks
```html
<header role="banner">
    <nav role="navigation" aria-label="Main navigation">
        <!-- Nav items -->
    </nav>
</header>

<main role="main">
    <article role="article">
        <!-- Content -->
    </article>
    
    <aside role="complementary">
        <!-- Sidebar -->
    </aside>
</main>

<footer role="contentinfo">
    <!-- Footer -->
</footer>
```

### Skip Navigation
```html
<a href="#main-content" class="skip-link">Skip to main content</a>

<main id="main-content">
    <!-- Main content -->
</main>
```

### ARIA Labels
```html
<!-- For elements without visible labels -->
<button aria-label="Close dialog">
    <span aria-hidden="true">×</span>
</button>

<!-- For search form -->
<form role="search">
    <label for="search">Search:</label>
    <input type="search" id="search" aria-label="Search the website">
</form>
```

### Meaningful Alt Text
```html
<!-- Good: Descriptive -->
<img src="dog.jpg" alt="Golden retriever playing fetch in park">

<!-- Bad: Redundant or useless -->
<img src="dog.jpg" alt="image of dog">

<!-- Decorative: Empty alt -->
<img src="decoration.png" alt="" role="presentation">
```

### Keyboard Navigation
```html
<!-- Custom interactive elements need tabindex -->
<div tabindex="0" role="button" onclick="doSomething()">
    Clickable Div
</div>

<!-- Better: Use actual button -->
<button onclick="doSomething()">
    Clickable Button
</button>
```

### Form Accessibility
```html
<form>
    <fieldset>
        <legend>Contact Information</legend>
        
        <label for="name">Name: <span aria-label="required">*</span></label>
        <input type="text" id="name" required aria-required="true">
        
        <label for="email">Email:</label>
        <input type="email" id="email" aria-describedby="email-hint">
        <span id="email-hint">We'll never share your email</span>
    </fieldset>
</form>
```

---

## ♿ Accessibility Checklist

### Structure
- [ ] Proper heading hierarchy (h1 → h2 → h3, no skipping)
- [ ] Semantic HTML elements used
- [ ] ARIA landmarks defined
- [ ] Skip navigation link present

### Navigation
- [ ] All interactive elements keyboard accessible
- [ ] Tab order is logical
- [ ] Focus visible on all elements
- [ ] No keyboard traps

### Content
- [ ] All images have appropriate alt text
- [ ] Links have descriptive text (not "click here")
- [ ] Color not only way to convey information
- [ ] Text has sufficient contrast ratio

### Forms
- [ ] All inputs have associated labels
- [ ] Required fields indicated
- [ ] Error messages clear and helpful
- [ ] Fieldsets group related inputs

### ARIA
- [ ] ARIA roles used where appropriate
- [ ] ARIA labels provide context
- [ ] ARIA live regions for dynamic content
- [ ] ARIA hidden for decorative elements

---

## 🧪 Testing Your Accessibility

### Tools
1. **WAVE** - https://wave.webaim.org/
2. **axe DevTools** - Browser extension
3. **Lighthouse** - In Chrome DevTools
4. **NVDA** - Free screen reader (Windows)
5. **VoiceOver** - Built-in screen reader (Mac)

### Manual Testing
- Navigate entire site with keyboard only
- Test with screen reader
- Zoom to 200% - still usable?
- Check contrast ratios

---

## 💡 Common Accessibility Mistakes

1. ❌ Using `<div>` for buttons → ✅ Use `<button>`
2. ❌ Images without alt text → ✅ Always include alt
3. ❌ Poor color contrast → ✅ Check contrast ratios
4. ❌ Inputs without labels → ✅ Associate labels
5. ❌ Skipping heading levels → ✅ Use proper hierarchy

---

## 📚 Resources

- [WebAIM](https://webaim.org/)
- [WCAG Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)
- [A11y Project](https://www.a11yproject.com/)
- [MDN Accessibility](https://developer.mozilla.org/en-US/docs/Web/Accessibility)

---

**Next**: [Assignment 10: Portfolio Page](../assignment-10-portfolio-page/ASSIGNMENT_10_GUIDE.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

