# Course Folder Structure - Navigation Guide

**By Mahendra Bagul**

This document explains how the course is organized and where to find everything.

---

## 📁 Root Directory Structure

```
react-learning-path/
├── 📘 01-html-fundamentals/         # Phase 1: HTML (10 assignments)
├── 🎨 02-css-fundamentals/          # Phase 2: CSS (10 assignments)
├── ⚡ 03-javascript-fundamentals/   # Phase 3: JavaScript (10 assignments)
├── 📘 04-typescript-fundamentals/   # Phase 4: TypeScript (10 assignments)
├── ⚛️  05-react-course/              # Phase 5: React (11 assignments)
├── 📚 resources/                    # Shared resources and guides
├── 📝 notes/                        # Your learning tracker
├── 🎓 for-instructors/              # Teaching materials
├── 🚀 deployment-configs/           # Deployment guides
├── 🔧 common-components/            # Reusable code snippets
│
├── README.md                        # Course overview (START HERE!)
├── GET_STARTED_HERE.md              # Beginner's onboarding guide
├── QUICK_START.md                   # Environment setup guide
├── COURSE_SUMMARY.md                # All 51 assignments detailed
├── FOLDER_STRUCTURE.md              # This file!
└── CREDITS.md                       # About the author
```

---

## 📚 Phase Structure

Each phase (HTML, CSS, JavaScript, TypeScript, React) follows this structure:

```
XX-phase-name/
├── README.md                        # Phase overview
├── assignment-01-name/              # Assignment 1
│   ├── ASSIGNMENT_1_GUIDE.md        # Detailed instructions
│   ├── UI_MOCKUP.md                 # Visual reference (React only)
│   ├── src/                         # Your code goes here
│   └── solution/                    # Reference solution
├── assignment-02-name/              # Assignment 2
│   └── ...
└── assignment-10-name/              # Final assignment
    └── ...
```

---

## 📖 Assignment Structure

Each assignment contains:

```
assignment-XX-name/
├── ASSIGNMENT_X_GUIDE.md            # Main guide with:
│   ├── Learning objectives
│   ├── Requirements
│   ├── Step-by-step instructions
│   ├── Code examples
│   ├── Common mistakes
│   └── Self-assessment checklist
│
├── UI_MOCKUP.md                     # Visual mockup (React assignments)
│
├── src/                             # Where you code
│   ├── index.html                   # HTML file
│   ├── styles.css                   # CSS file
│   └── script.js/app.ts             # JavaScript/TypeScript file
│
└── solution/                        # Reference solution (if stuck)
    └── ...
```

---

## 🗺️ How to Navigate

### Starting Out:
1. Read **README.md** (main overview)
2. Read **GET_STARTED_HERE.md** (onboarding)
3. Setup with **QUICK_START.md**
4. Start **Phase 1 → Assignment 1**

### During Learning:
1. Open the **phase folder** (e.g., `01-html-fundamentals/`)
2. Read **phase README** for overview
3. Open **assignment folder** (e.g., `assignment-01-hello-world/`)
4. Read **ASSIGNMENT_X_GUIDE.md**
5. Code in the **src/** folder
6. Check **UI_MOCKUP.md** for visual reference

### When Stuck:
1. Re-read the **ASSIGNMENT_GUIDE**
2. Check **UI_MOCKUP** for visuals
3. Review **example code** in guide
4. Check **resources/FAQ_AND_TROUBLESHOOTING.md**
5. Look at **solution/** folder as last resort

---

## 📚 Resources Folder

```
resources/
├── FAQ_AND_TROUBLESHOOTING.md       # Common questions & fixes
├── COMMON_PATTERNS.md               # Reusable code patterns
├── API_GUIDES.md                    # API integration guides
└── UI_MOCKUPS_INDEX.md              # All UI mockups (React)
```

**When to Use:**
- Stuck on something common? Check FAQ
- Need a code pattern? Check COMMON_PATTERNS
- Working with APIs? Check API_GUIDES

---

## 📝 Notes Folder

```
notes/
└── LEARNING_TRACKER.md              # Track your progress
```

**Use this to:**
- Mark completed assignments
- Note challenges faced
- Document solutions found
- Track weekly progress

---

## 🎓 For Instructors Folder

```
for-instructors/
├── README.md                        # Teaching guide overview
├── INSTRUCTOR_GUIDE.md              # How to teach this course
├── SOLUTION_GUIDELINES.md           # Grading and solutions
└── ASSESSMENT_RUBRICS.md            # How to evaluate students
```

**For:**
- Teachers
- Mentors
- Bootcamp instructors
- Study group leaders

---

## 🚀 Deployment Configs Folder

```
deployment-configs/
├── DEPLOYMENT_GUIDE.md              # General deployment guide
├── netlify.toml                     # Netlify configuration
├── vercel.json                      # Vercel configuration
└── github-actions.yml               # CI/CD configuration
```

**Use in Phase 5 (React)** when deploying your applications.

---

## 🔧 Common Components Folder

```
common-components/
├── Button.jsx                       # Reusable button
├── Card.jsx                         # Reusable card
├── Modal.jsx                        # Reusable modal
└── ...                              # More components
```

**Use in Phase 5 (React)** for reusable components across projects.

---

## 🎯 Finding Specific Content

### Want to learn about...?

**HTML basics:**  
`01-html-fundamentals/assignment-01-hello-world/`

**CSS layouts:**  
`02-css-fundamentals/assignment-04-flexbox/` or `assignment-05-grid/`

**JavaScript functions:**  
`03-javascript-fundamentals/assignment-02-functions-scope/`

**TypeScript types:**  
`04-typescript-fundamentals/assignment-01-basic-types/`

**React components:**  
`05-react-course/assignment-01-portfolio/`

**Redux state management:**  
`05-react-course/assignment-04-ecommerce/`

**Testing:**  
`05-react-course/assignment-10-testing-deployment/`

---

## 📊 Progress Tracking

### Recommended File Organization on Your Computer:

```
Documents/
└── web-dev-learning/
    ├── html-projects/
    │   ├── assignment-01-hello-world/
    │   ├── assignment-02-text-formatting/
    │   └── ...
    ├── css-projects/
    ├── javascript-projects/
    ├── typescript-projects/
    └── react-projects/
```

**Keep your code organized!** One folder per assignment.

---

## ✅ Checklist for Each Assignment

- [ ] Read phase README
- [ ] Read ASSIGNMENT_X_GUIDE.md
- [ ] Create project folder
- [ ] Code in src/
- [ ] Test your work
- [ ] Complete self-assessment
- [ ] Mark as complete in LEARNING_TRACKER.md
- [ ] Move to next assignment

---

## 🔍 Quick Find

### Documentation:
- **Getting started**: `README.md`, `GET_STARTED_HERE.md`
- **Setup help**: `QUICK_START.md`
- **All assignments**: `COURSE_SUMMARY.md`
- **Stuck?**: `resources/FAQ_AND_TROUBLESHOOTING.md`

### Learning:
- **Phase 1**: `01-html-fundamentals/`
- **Phase 2**: `02-css-fundamentals/`
- **Phase 3**: `03-javascript-fundamentals/`
- **Phase 4**: `04-typescript-fundamentals/`
- **Phase 5**: `05-react-course/`

### Help:
- **FAQ**: `resources/FAQ_AND_TROUBLESHOOTING.md`
- **Patterns**: `resources/COMMON_PATTERNS.md`
- **Deployment**: `deployment-configs/DEPLOYMENT_GUIDE.md`

---

## 💡 Tips

1. **Bookmark important files** - Quick access in your editor
2. **Use search** - Ctrl+Shift+F in VS Code searches all files
3. **Keep notes** - Use `notes/LEARNING_TRACKER.md`
4. **Stay organized** - One folder per assignment
5. **Don't skip** - Assignments build on each other

---

## 🆘 Lost?

**Start here:**
1. [Main README](./README.md) - What is this course?
2. [Get Started](./GET_STARTED_HERE.md) - How do I begin?
3. [Quick Start](./QUICK_START.md) - Setup my computer
4. [Course Summary](./COURSE_SUMMARY.md) - What will I learn?
5. [This File](./FOLDER_STRUCTURE.md) - Where is everything?

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

---

<div align="center">

**Ready to learn?** → [Get Started](./GET_STARTED_HERE.md)

**Know where things are?** → [Start Assignment 1](./01-html-fundamentals/assignment-01-hello-world/ASSIGNMENT_1_GUIDE.md)

</div>

