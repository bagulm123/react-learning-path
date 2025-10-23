# Assignment 1: Personal Portfolio Website

**Focus**: React basics, routing, component composition  
**Estimated Time**: 8-10 hours  
**Difficulty**: ⭐⭐☆☆☆

---

## 🎯 Learning Objectives

By the end of this assignment, you will understand:
- React functional components
- Props and state with useState
- React Router v6 for navigation
- Event handling in React
- CSS Modules for component styling
- Form validation
- Responsive design principles

---

## 📋 Requirements

### Technical Stack
- React 18+ with Vite
- React Router v6
- React Icons
- CSS Modules
- No external UI libraries (custom CSS only)

### Features Required
1. ✅ Responsive navigation bar
   - Desktop: horizontal menu
   - Mobile: hamburger menu with slide-in drawer
   - Active link highlighting

2. ✅ Hero Section
   - Name and tagline
   - Call-to-action button
   - Background with gradient or image

3. ✅ About Section
   - Profile image
   - Bio text
   - Download resume button

4. ✅ Projects Section
   - Grid layout (responsive)
   - At least 3 project cards
   - Each card: image, title, description, tech stack, links
   - Hover effects

5. ✅ Skills Section
   - Display tech skills with icons
   - Grid or flex layout
   - Visual indicators (icons from react-icons)

6. ✅ Contact Section
   - Contact form with fields: name, email, message
   - Form validation
   - Success message on submit
   - Social media links

7. ✅ Footer
   - Copyright info
   - Social links
   - Quick navigation links

### Additional Requirements
- Smooth scrolling between sections
- Responsive for mobile, tablet, desktop
- Loading states for form submission
- Accessible (ARIA labels, semantic HTML)
- Clean, professional design

---

## 🚀 Setup Instructions

### Step 1: Create Project
```bash
cd ~/DevEnv/learnings/react-course/assignment-01-portfolio

# Create Vite React project
npm create vite@latest . -- --template react

# Install dependencies
npm install
```

### Step 2: Install Required Packages
```bash
# React Router
npm install react-router-dom

# React Icons
npm install react-icons

# PropTypes (optional but recommended)
npm install prop-types
```

### Step 3: Start Development Server
```bash
npm run dev
```

### Step 4: Open in Browser
Navigate to `http://localhost:5173`

---

## 📁 Recommended Folder Structure

```
assignment-01-portfolio/
├── public/
│   ├── resume.pdf
│   └── favicon.ico
├── src/
│   ├── components/
│   │   ├── Navbar/
│   │   │   ├── Navbar.jsx
│   │   │   └── Navbar.module.css
│   │   ├── Hero/
│   │   │   ├── Hero.jsx
│   │   │   └── Hero.module.css
│   │   ├── About/
│   │   │   ├── About.jsx
│   │   │   └── About.module.css
│   │   ├── Projects/
│   │   │   ├── Projects.jsx
│   │   │   ├── ProjectCard.jsx
│   │   │   └── Projects.module.css
│   │   ├── Skills/
│   │   │   ├── Skills.jsx
│   │   │   └── Skills.module.css
│   │   ├── Contact/
│   │   │   ├── Contact.jsx
│   │   │   └── Contact.module.css
│   │   └── Footer/
│   │       ├── Footer.jsx
│   │       └── Footer.module.css
│   ├── data/
│   │   ├── projects.js
│   │   └── skills.js
│   ├── assets/
│   │   └── images/
│   │       ├── profile.jpg
│   │       └── projects/
│   ├── App.jsx
│   ├── App.css
│   └── main.jsx
├── .gitignore
├── index.html
├── package.json
├── vite.config.js
└── README.md
```

---

## 💻 Step-by-Step Implementation Plan

### Phase 1: Setup & Navigation (Day 1)
1. Create folder structure
2. Set up React Router
3. Build Navbar component
4. Implement mobile hamburger menu
5. Add smooth scrolling

### Phase 2: Content Sections (Day 2)
6. Build Hero component
7. Build About component
8. Create project data file
9. Build Projects component and ProjectCard

### Phase 3: Skills & Contact (Day 3)
10. Build Skills component with icons
11. Build Contact form
12. Implement form validation
13. Build Footer component

### Phase 4: Styling & Polish (Day 4)
14. Make fully responsive
15. Add hover effects and animations
16. Test on different screen sizes
17. Accessibility improvements

---

## 🎨 Design Inspiration

### Color Schemes (Choose One)
1. **Modern Blue**
   - Primary: #3B82F6
   - Secondary: #1E40AF
   - Accent: #F59E0B
   - Background: #F9FAFB
   - Text: #1F2937

2. **Dark Theme**
   - Primary: #10B981
   - Secondary: #059669
   - Background: #1F2937
   - Surface: #374151
   - Text: #F9FAFB

3. **Minimal**
   - Primary: #000000
   - Secondary: #4B5563
   - Accent: #EF4444
   - Background: #FFFFFF
   - Text: #111827

---

## ✅ Features Checklist

### Core Features
- [ ] Responsive navbar
- [ ] Mobile hamburger menu
- [ ] Hero section with CTA
- [ ] About section
- [ ] Projects showcase (min 3)
- [ ] Skills with icons
- [ ] Contact form
- [ ] Footer
- [ ] Smooth scrolling

### Form Validation
- [ ] Name required
- [ ] Email required and valid format
- [ ] Message required (min 10 characters)
- [ ] Show errors on blur
- [ ] Clear errors on input
- [ ] Success message on submit
- [ ] Reset form after submit

### Responsive Design
- [ ] Mobile (< 768px)
- [ ] Tablet (768px - 1024px)
- [ ] Desktop (> 1024px)
- [ ] Hamburger menu on mobile
- [ ] Touch-friendly buttons
- [ ] Readable font sizes

### Accessibility
- [ ] Semantic HTML (header, nav, main, section, footer)
- [ ] ARIA labels
- [ ] Keyboard navigation
- [ ] Focus indicators
- [ ] Alt text for images
- [ ] Proper heading hierarchy

### Code Quality
- [ ] PropTypes defined
- [ ] No console.log statements
- [ ] Comments on complex logic
- [ ] DRY principle followed
- [ ] Consistent naming conventions
- [ ] CSS Modules (no global styles conflicts)

---

## 🐛 Common Challenges & Solutions

### Challenge 1: Smooth Scrolling Not Working
**Solution**:
```jsx
const scrollToSection = (sectionId) => {
  const element = document.getElementById(sectionId);
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' });
  }
};
```

### Challenge 2: Hamburger Menu Not Closing on Link Click
**Solution**:
```jsx
const handleLinkClick = (sectionId) => {
  setIsMenuOpen(false); // Close menu
  scrollToSection(sectionId); // Then scroll
};
```

### Challenge 3: CSS Modules Not Working
**Solution**: Ensure files are named `*.module.css` and imported correctly:
```jsx
import styles from './Navbar.module.css';
<nav className={styles.navbar}>
```

---

## 📚 Key Concepts to Understand

### 1. useState Hook
```jsx
const [isMenuOpen, setIsMenuOpen] = useState(false);
// isMenuOpen: current state value
// setIsMenuOpen: function to update state
```

### 2. Props
```jsx
// Parent component
<ProjectCard title="My Project" description="Description here" />

// Child component
const ProjectCard = ({ title, description }) => {
  return <div><h3>{title}</h3><p>{description}</p></div>;
};
```

### 3. Event Handlers
```jsx
const handleSubmit = (e) => {
  e.preventDefault(); // Prevent default form submission
  // Your logic here
};

<form onSubmit={handleSubmit}>
```

### 4. Conditional Rendering
```jsx
{isMenuOpen && <div className={styles.menu}>Menu content</div>}
// Renders only when isMenuOpen is true
```

---

## 🎓 Learning Resources

- [React Docs - useState](https://react.dev/reference/react/useState)
- [React Router Tutorial](https://reactrouter.com/en/main/start/tutorial)
- [CSS Modules Documentation](https://github.com/css-modules/css-modules)
- [React Icons](https://react-icons.github.io/react-icons/)
- [MDN - Accessibility](https://developer.mozilla.org/en-US/docs/Web/Accessibility)

---

## 🚀 Deployment

Once completed, deploy to Netlify:
```bash
npm run build
netlify deploy --prod
```

See `../deployment-configs/DEPLOYMENT_GUIDE.md` for detailed instructions.

---

## 📊 Self-Assessment

After completing, rate your understanding (1-5):
- [ ] React components and JSX
- [ ] useState hook
- [ ] Props
- [ ] Event handling
- [ ] CSS Modules
- [ ] React Router
- [ ] Form validation
- [ ] Responsive design

---

## 🎯 Bonus Challenges (Optional)

1. Add dark mode toggle
2. Add animations with Framer Motion
3. Implement a blog section
4. Add unit tests
5. Add SEO meta tags
6. Implement i18n (internationalization)

---

**Ready to start? Use the Cursor prompt above to begin building your Navbar component!**

