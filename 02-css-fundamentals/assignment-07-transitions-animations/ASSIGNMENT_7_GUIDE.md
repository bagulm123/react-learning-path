# Assignment 7: Transitions & Animations - Bringing Pages to Life

**By Mahendra Bagul**

Static websites are boring. Motion makes websites feel alive, guides user attention, and provides feedback. Let's add some life to your designs! ✨

---

## 📚 What You'll Learn

- ✅ CSS transitions (smooth property changes)
- ✅ Transform functions (translate, rotate, scale, skew)
- ✅ Keyframe animations (`@keyframes`)
- ✅ Animation properties (duration, timing, delay, iteration)
- ✅ Easing functions (ease, linear, cubic-bezier)
- ✅ Hover effects
- ✅ Loading animations
- ✅ Page transitions
- ✅ Performance considerations

---

## 🎯 Assignment Objectives

Create an "Animated Landing Page" with smooth transitions, hover effects, and animated elements.

**Difficulty**: ⭐⭐⭐⭐☆  
**Time**: 4-5 hours  
**Prerequisites**: CSS Assignments 1-6

---

## 📋 Requirements

### Must Have
1. ✅ At least 5 hover transitions
2. ✅ At least 3 keyframe animations
3. ✅ Transform effects (scale, rotate, translate)
4. ✅ Loading spinner animation
5. ✅ Fade-in animation on page load
6. ✅ Slide-in animations for sections
7. ✅ Button hover effects
8. ✅ Card flip animation
9. ✅ Smooth scroll behavior
10. ✅ Performance-optimized animations

---

## 🎬 CSS Transitions

### Basic Transition
```css
.button {
    background-color: blue;
    transition: background-color 0.3s ease;
}

.button:hover {
    background-color: red;
}
```

### Transition Properties
```css
.element {
    /* Individual properties */
    transition-property: background-color, transform;
    transition-duration: 0.3s;
    transition-timing-function: ease-in-out;
    transition-delay: 0.1s;
    
    /* Shorthand */
    transition: background-color 0.3s ease-in-out 0.1s,
                transform 0.3s ease;
    
    /* All properties */
    transition: all 0.3s ease;
}
```

### Timing Functions
```css
.element {
    /* Predefined */
    transition-timing-function: linear;     /* Constant speed */
    transition-timing-function: ease;       /* Slow-fast-slow (default) */
    transition-timing-function: ease-in;    /* Slow start */
    transition-timing-function: ease-out;   /* Slow end */
    transition-timing-function: ease-in-out; /* Slow start and end */
    
    /* Custom (Bezier curve) */
    transition-timing-function: cubic-bezier(0.68, -0.55, 0.265, 1.55);
}
```

---

## 🔄 CSS Transforms

```css
.element {
    /* Translate (move) */
    transform: translateX(100px);
    transform: translateY(-50px);
    transform: translate(100px, -50px);
    
    /* Rotate */
    transform: rotate(45deg);
    transform: rotateX(45deg);  /* 3D */
    transform: rotateY(45deg);  /* 3D */
    
    /* Scale */
    transform: scale(1.5);      /* 150% size */
    transform: scale(2, 1.5);   /* Width 2x, Height 1.5x */
    
    /* Skew */
    transform: skew(10deg, 5deg);
    
    /* Combine multiple */
    transform: translate(100px, 0) rotate(45deg) scale(1.2);
}
```

---

## 🎨 Keyframe Animations

### Define Animation
```css
@keyframes slideIn {
    from {
        transform: translateX(-100%);
        opacity: 0;
    }
    to {
        transform: translateX(0);
        opacity: 1;
    }
}

/* Or with percentages */
@keyframes bounce {
    0% { transform: translateY(0); }
    50% { transform: translateY(-20px); }
    100% { transform: translateY(0); }
}
```

### Apply Animation
```css
.element {
    animation-name: slideIn;
    animation-duration: 1s;
    animation-timing-function: ease-out;
    animation-delay: 0.5s;
    animation-iteration-count: 1;  /* or infinite */
    animation-direction: normal;   /* or reverse, alternate */
    animation-fill-mode: forwards; /* Keeps final state */
    
    /* Shorthand */
    animation: slideIn 1s ease-out 0.5s 1 normal forwards;
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
    <title>Animated Landing Page</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <!-- Loading Spinner -->
    <div class="loader" id="loader">
        <div class="spinner"></div>
    </div>
    
    <!-- Main Content -->
    <div class="content" id="content">
        <!-- Hero Section -->
        <section class="hero">
            <div class="hero-content fade-in">
                <h1 class="glitch" data-text="Welcome">Welcome</h1>
                <p class="slide-up">Experience the power of CSS animations</p>
                <button class="btn-animated">Get Started</button>
            </div>
        </section>
        
        <!-- Features Section -->
        <section class="features">
            <h2 class="section-title">Amazing Features</h2>
            <div class="features-grid">
                <div class="feature-card">
                    <div class="icon-wrapper">
                        <div class="icon">⚡</div>
                    </div>
                    <h3>Lightning Fast</h3>
                    <p>Optimized for performance</p>
                </div>
                
                <div class="feature-card">
                    <div class="icon-wrapper">
                        <div class="icon">🎨</div>
                    </div>
                    <h3>Beautiful Design</h3>
                    <p>Modern and elegant</p>
                </div>
                
                <div class="feature-card">
                    <div class="icon-wrapper">
                        <div class="icon">🚀</div>
                    </div>
                    <h3>Easy to Use</h3>
                    <p>Intuitive interface</p>
                </div>
            </div>
        </section>
        
        <!-- Cards Section -->
        <section class="cards-section">
            <h2 class="section-title">Interactive Cards</h2>
            <div class="cards-grid">
                <div class="flip-card">
                    <div class="flip-card-inner">
                        <div class="flip-card-front">
                            <h3>Hover Me!</h3>
                            <p>Click to flip</p>
                        </div>
                        <div class="flip-card-back">
                            <h3>Back Side</h3>
                            <p>Amazing content here!</p>
                        </div>
                    </div>
                </div>
                
                <div class="pulse-card">
                    <h3>Pulse Effect</h3>
                    <p>Continuous animation</p>
                </div>
                
                <div class="shake-card">
                    <h3>Shake on Hover</h3>
                    <p>Interactive feedback</p>
                </div>
            </div>
        </section>
        
        <!-- CTA Section -->
        <section class="cta">
            <h2 class="bounce-text">Ready to Start?</h2>
            <button class="btn-glow">Join Now</button>
        </section>
    </div>
    
    <script src="script.js"></script>
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

html {
    scroll-behavior: smooth;
}

body {
    font-family: 'Arial', sans-serif;
    overflow-x: hidden;
}

/* ===== LOADER ANIMATION ===== */
.loader {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 9999;
    animation: fadeOut 0.5s ease 2s forwards;
}

@keyframes fadeOut {
    to {
        opacity: 0;
        visibility: hidden;
    }
}

.spinner {
    width: 50px;
    height: 50px;
    border: 5px solid rgba(255, 255, 255, 0.3);
    border-top-color: white;
    border-radius: 50%;
    animation: spin 1s linear infinite;
}

@keyframes spin {
    to {
        transform: rotate(360deg);
    }
}

/* ===== CONTENT (HIDDEN INITIALLY) ===== */
.content {
    opacity: 0;
    animation: fadeInContent 0.5s ease 2s forwards;
}

@keyframes fadeInContent {
    to {
        opacity: 1;
    }
}

/* ===== HERO SECTION ===== */
.hero {
    min-height: 100vh;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    text-align: center;
    padding: 2rem;
}

.fade-in {
    animation: fadeIn 1s ease 2.5s backwards;
}

@keyframes fadeIn {
    from {
        opacity: 0;
        transform: translateY(30px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

/* ===== GLITCH TEXT ===== */
.glitch {
    font-size: clamp(3rem, 8vw, 6rem);
    font-weight: bold;
    position: relative;
    animation: glitch 2s infinite;
}

@keyframes glitch {
    0%, 90%, 100% {
        transform: translate(0);
    }
    92% {
        transform: translate(-2px, 2px);
    }
    94% {
        transform: translate(2px, -2px);
    }
    96% {
        transform: translate(-2px, -2px);
    }
}

/* ===== SLIDE UP ===== */
.slide-up {
    font-size: 1.5rem;
    margin: 2rem 0;
    animation: slideUp 1s ease 2.7s backwards;
}

@keyframes slideUp {
    from {
        opacity: 0;
        transform: translateY(50px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

/* ===== ANIMATED BUTTON ===== */
.btn-animated {
    padding: 1rem 3rem;
    font-size: 1.2rem;
    border: none;
    background: white;
    color: #667eea;
    border-radius: 50px;
    cursor: pointer;
    position: relative;
    overflow: hidden;
    transition: transform 0.3s ease;
    animation: slideUp 1s ease 2.9s backwards;
}

.btn-animated::before {
    content: '';
    position: absolute;
    top: 50%;
    left: 50%;
    width: 0;
    height: 0;
    border-radius: 50%;
    background: rgba(102, 126, 234, 0.3);
    transform: translate(-50%, -50%);
    transition: width 0.6s ease, height 0.6s ease;
}

.btn-animated:hover::before {
    width: 300px;
    height: 300px;
}

.btn-animated:hover {
    transform: scale(1.05);
}

.btn-animated:active {
    transform: scale(0.95);
}

/* ===== FEATURES SECTION ===== */
.features {
    padding: 5rem 2rem;
}

.section-title {
    font-size: 2.5rem;
    text-align: center;
    margin-bottom: 3rem;
    color: #2c3e50;
}

.features-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 2rem;
    max-width: 1200px;
    margin: 0 auto;
}

.feature-card {
    background: white;
    padding: 2rem;
    border-radius: 15px;
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
    text-align: center;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    animation: fadeInUp 0.6s ease backwards;
}

.feature-card:nth-child(1) { animation-delay: 0.2s; }
.feature-card:nth-child(2) { animation-delay: 0.4s; }
.feature-card:nth-child(3) { animation-delay: 0.6s; }

@keyframes fadeInUp {
    from {
        opacity: 0;
        transform: translateY(40px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.feature-card:hover {
    transform: translateY(-10px);
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
}

.icon-wrapper {
    margin-bottom: 1rem;
}

.icon {
    font-size: 3rem;
    display: inline-block;
    transition: transform 0.3s ease;
}

.feature-card:hover .icon {
    transform: scale(1.2) rotate(10deg);
}

/* ===== CARDS SECTION ===== */
.cards-section {
    padding: 5rem 2rem;
    background: #f8f9fa;
}

.cards-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 2rem;
    max-width: 1200px;
    margin: 0 auto;
}

/* FLIP CARD */
.flip-card {
    perspective: 1000px;
    height: 300px;
}

.flip-card-inner {
    position: relative;
    width: 100%;
    height: 100%;
    transition: transform 0.6s;
    transform-style: preserve-3d;
}

.flip-card:hover .flip-card-inner {
    transform: rotateY(180deg);
}

.flip-card-front,
.flip-card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    backface-visibility: hidden;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    border-radius: 15px;
    padding: 2rem;
}

.flip-card-front {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
}

.flip-card-back {
    background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
    color: white;
    transform: rotateY(180deg);
}

/* PULSE CARD */
.pulse-card {
    background: white;
    padding: 2rem;
    border-radius: 15px;
    height: 300px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    animation: pulse 2s ease-in-out infinite;
}

@keyframes pulse {
    0%, 100% {
        transform: scale(1);
        box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
    }
    50% {
        transform: scale(1.05);
        box-shadow: 0 10px 30px rgba(102, 126, 234, 0.3);
    }
}

/* SHAKE CARD */
.shake-card {
    background: white;
    padding: 2rem;
    border-radius: 15px;
    height: 300px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    transition: transform 0.3s ease;
}

.shake-card:hover {
    animation: shake 0.5s ease;
}

@keyframes shake {
    0%, 100% { transform: translateX(0); }
    10%, 30%, 50%, 70%, 90% { transform: translateX(-10px); }
    20%, 40%, 60%, 80% { transform: translateX(10px); }
}

/* ===== CTA SECTION ===== */
.cta {
    padding: 5rem 2rem;
    text-align: center;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
}

.bounce-text {
    font-size: 3rem;
    margin-bottom: 2rem;
    animation: bounce 2s ease-in-out infinite;
}

@keyframes bounce {
    0%, 20%, 50%, 80%, 100% {
        transform: translateY(0);
    }
    40% {
        transform: translateY(-30px);
    }
    60% {
        transform: translateY(-15px);
    }
}

.btn-glow {
    padding: 1rem 3rem;
    font-size: 1.2rem;
    border: 2px solid white;
    background: transparent;
    color: white;
    border-radius: 50px;
    cursor: pointer;
    position: relative;
    overflow: hidden;
    transition: all 0.3s ease;
}

.btn-glow:hover {
    background: white;
    color: #667eea;
    box-shadow: 0 0 20px rgba(255, 255, 255, 0.8),
                0 0 40px rgba(255, 255, 255, 0.6),
                0 0 60px rgba(255, 255, 255, 0.4);
}

/* ===== RESPONSIVE ===== */
@media (max-width: 768px) {
    .glitch {
        font-size: 3rem;
    }
    
    .slide-up {
        font-size: 1.2rem;
    }
    
    .cards-grid {
        grid-template-columns: 1fr;
    }
}
```

### JavaScript (script.js)
```javascript
// Hide loader after page loads
window.addEventListener('load', () => {
    setTimeout(() => {
        document.getElementById('loader').style.display = 'none';
    }, 2500);
});

// Intersection Observer for scroll animations
const observerOptions = {
    threshold: 0.1,
    rootMargin: '0px 0px -50px 0px'
};

const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            entry.target.style.animation = 'fadeInUp 0.6s ease forwards';
        }
    });
}, observerOptions);

// Observe all feature cards
document.querySelectorAll('.feature-card').forEach(card => {
    observer.observe(card);
});
```

---

## 📖 Animation Best Practices

1. **Performance**: Animate `transform` and `opacity` (GPU accelerated)
2. **Duration**: 200-500ms for micro-interactions, 500-1000ms for larger animations
3. **Easing**: Use `ease-out` for entrances, `ease-in` for exits
4. **Reduce Motion**: Respect `prefers-reduced-motion`
5. **Purpose**: Animate with purpose, not just because you can

### Performant Properties
✅ `transform` (translate, scale, rotate)
✅ `opacity`
❌ `width`, `height`, `top`, `left` (causes reflow)

---

## ✅ Self-Assessment

- [ ] 5+ hover transitions implemented
- [ ] 3+ keyframe animations created
- [ ] Transform effects used
- [ ] Loading spinner works
- [ ] Fade-in on page load
- [ ] Slide-in animations for sections
- [ ] Button hover effects smooth
- [ ] Card flip animation works
- [ ] Smooth scroll enabled
- [ ] Animations are performant (60fps)

---

**Next**: [Assignment 8: Advanced Layouts](../assignment-08-advanced-layouts/ASSIGNMENT_8_GUIDE.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

