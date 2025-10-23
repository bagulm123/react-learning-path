# Assignment 3: Task Management App

**Focus**: Material-UI, complex state management, theming  
**Estimated Time**: 12-15 hours  
**Difficulty**: ⭐⭐⭐⭐☆

---

## 🎯 Learning Objectives

By the end of this assignment, you will understand:
- Material-UI (MUI) component library
- Theme customization and dark/light mode
- Context API for global state
- Complex state management with custom hooks
- LocalStorage for data persistence
- CRUD operations in React
- Date handling with date-fns
- Form management with MUI components

---

## 📋 Requirements

### Technical Stack
- React 18+ with Vite
- Material-UI (MUI) v5
- MUI Icons
- date-fns for date formatting
- LocalStorage for data persistence
- Context API for theme management

### Features Required

1. ✅ **Task Management (CRUD)**
   - Create new tasks
   - Read/display all tasks
   - Update existing tasks
   - Delete tasks
   - Task properties: title, description, due date, priority, category, status

2. ✅ **Task Properties**
   - Title (required)
   - Description (optional)
   - Due date (with date picker)
   - Priority: Low, Medium, High
   - Category/tags
   - Status: Active, Completed

3. ✅ **Filtering & Sorting**
   - Filter by status (all, active, completed)
   - Filter by priority
   - Filter by category
   - Sort by date, priority

4. ✅ **UI Components**
   - App bar with title and theme toggle
   - Responsive drawer/sidebar (optional)
   - Task cards in grid/list view
   - Add task button (FAB - Floating Action Button)
   - Task dialog/modal for create/edit
   - Confirmation dialog for delete

5. ✅ **Theme Toggle**
   - Dark/Light mode switch
   - Persist theme preference
   - Custom theme colors

6. ✅ **Notifications**
   - Snackbar for success messages
   - Snackbar for errors
   - Auto-dismiss after 3 seconds

### Additional Requirements
- Data persists in LocalStorage
- Responsive design
- Empty state when no tasks
- Form validation
- Accessibility with MUI

---

## 🚀 Setup Instructions

### Step 1: Create Project

```bash
cd ~/DevEnv/learnings/react-course/assignment-03-task-manager

# Create Vite React project
npm create vite@latest . -- --template react

# Install dependencies
npm install
```

### Step 2: Install Material-UI

```bash
# Core MUI packages
npm install @mui/material @emotion/react @emotion/styled

# MUI Icons
npm install @mui/icons-material

# Date handling
npm install date-fns

# Optional: PropTypes
npm install prop-types
```

### Step 3: Start Development Server

```bash
npm run dev
```

---

## 📁 Recommended Folder Structure

```
assignment-03-task-manager/
├── public/
├── src/
│   ├── components/
│   │   ├── Layout/
│   │   │   ├── AppBar.jsx
│   │   │   └── Drawer.jsx (optional)
│   │   ├── TaskList/
│   │   │   ├── TaskList.jsx
│   │   │   └── TaskCard.jsx
│   │   ├── TaskDialog/
│   │   │   └── TaskDialog.jsx
│   │   ├── FilterBar/
│   │   │   └── FilterBar.jsx
│   │   └── ConfirmDialog/
│   │       └── ConfirmDialog.jsx
│   ├── context/
│   │   ├── ThemeContext.jsx
│   │   └── TaskContext.jsx
│   ├── hooks/
│   │   ├── useLocalStorage.js
│   │   └── useTasks.js
│   ├── theme/
│   │   └── theme.js
│   ├── utils/
│   │   └── helpers.js
│   ├── App.jsx
│   └── main.jsx
├── package.json
└── README.md
```

---

## 💻 Step-by-Step Implementation Plan

### Phase 1: Setup & Theme (3-4 hours)
1. Install and configure MUI
2. Create custom theme file
3. Set up ThemeContext for dark/light mode
4. Build AppBar with theme toggle
5. Test theme switching

### Phase 2: State Management (3-4 hours)
6. Create useLocalStorage hook
7. Create useTasks hook for CRUD operations
8. Set up TaskContext (optional)
9. Define task data structure
10. Test localStorage persistence

### Phase 3: Task Components (4-5 hours)
11. Build TaskCard component
12. Build TaskList component
13. Build TaskDialog for create/edit
14. Add date picker
15. Add priority and category selection

### Phase 4: Features & Polish (2-3 hours)
16. Build FilterBar component
17. Implement filtering logic
18. Add ConfirmDialog for delete
19. Add Snackbar notifications
20. Add empty state
21. Test all features

---

## 🎨 MUI Theme Configuration

### Basic Theme Setup

Create `src/theme/theme.js`:

```javascript
import { createTheme } from '@mui/material/styles';

export const getTheme = (mode) => createTheme({
  palette: {
    mode,
    primary: {
      main: '#1976d2',
    },
    secondary: {
      main: '#dc004e',
    },
  },
  typography: {
    fontFamily: '"Roboto", "Helvetica", "Arial", sans-serif',
  },
});
```

---

## 📊 Task Data Structure

```javascript
const task = {
  id: 'unique-id-123',
  title: 'Complete React Assignment',
  description: 'Build a task manager app with MUI',
  dueDate: '2025-10-30',
  priority: 'high', // 'low', 'medium', 'high'
  category: 'Work', // or tags: ['work', 'urgent']
  status: 'active', // 'active', 'completed'
  createdAt: '2025-10-21T10:00:00Z',
  updatedAt: '2025-10-21T10:00:00Z',
};
```

---

## ✅ Features Checklist

### Core Features
- [ ] Create task
- [ ] Read/display tasks
- [ ] Update task
- [ ] Delete task
- [ ] LocalStorage persistence
- [ ] Theme toggle (dark/light)
- [ ] Responsive layout

### Task Properties
- [ ] Title input
- [ ] Description textarea
- [ ] Date picker
- [ ] Priority selector
- [ ] Category/tags input
- [ ] Status toggle

### Filtering
- [ ] Filter by status
- [ ] Filter by priority
- [ ] Filter by category
- [ ] Clear filters

### UI Components
- [ ] MUI AppBar
- [ ] Task cards
- [ ] Add task FAB
- [ ] Task dialog (create/edit)
- [ ] Confirm delete dialog
- [ ] Snackbar notifications
- [ ] Empty state

### Validation
- [ ] Title required
- [ ] Date validation
- [ ] Form error messages

---

## 🐛 Common Challenges & Solutions

### Challenge 1: Theme Not Applying
**Solution**: Wrap your app with ThemeProvider:
```javascript
import { ThemeProvider } from '@mui/material/styles';
import { getTheme } from './theme/theme';

function App() {
  const [mode, setMode] = useState('light');
  const theme = getTheme(mode);
  
  return (
    <ThemeProvider theme={theme}>
      {/* Your app */}
    </ThemeProvider>
  );
}
```

### Challenge 2: LocalStorage Not Updating
**Solution**: Use useEffect to sync with localStorage:
```javascript
useEffect(() => {
  localStorage.setItem('tasks', JSON.stringify(tasks));
}, [tasks]);
```

### Challenge 3: Date Picker Issues
**Solution**: Use MUI's DatePicker with proper format:
```javascript
import { LocalizationProvider } from '@mui/x-date-pickers';
import { AdapterDateFns } from '@mui/x-date-pickers/AdapterDateFns';
```

---

## 📚 Key Concepts to Understand

### 1. MUI Theme Customization
Material-UI allows you to create a consistent design system across your app.

### 2. Context API
Share state across components without prop drilling.

### 3. Custom Hooks
Extract and reuse stateful logic.

### 4. LocalStorage
Browser storage for persisting data.

### 5. CRUD Operations
Create, Read, Update, Delete - fundamental operations for any data-driven app.

---

## 🎓 Learning Resources

- [Material-UI Documentation](https://mui.com/material-ui/)
- [MUI Components](https://mui.com/material-ui/all-components/)
- [React Context API](https://react.dev/reference/react/useContext)
- [date-fns Documentation](https://date-fns.org/)
- [LocalStorage MDN](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage)

---

## 🚀 Deployment

Deploy to Netlify or Vercel:

```bash
npm run build
netlify deploy --prod
# or
vercel --prod
```

See `../deployment-configs/DEPLOYMENT_GUIDE.md` for detailed instructions.

---

## 📊 Self-Assessment

After completing, rate your understanding (1-5):
- [ ] Material-UI components
- [ ] Theme customization
- [ ] Context API
- [ ] Custom hooks
- [ ] LocalStorage
- [ ] CRUD operations
- [ ] Date handling
- [ ] Form validation with MUI

---

## 🎯 Bonus Challenges (Optional)

1. Add task search functionality
2. Add drag-and-drop to reorder tasks
3. Add task templates
4. Add task notes/comments
5. Add task attachments (file upload)
6. Add recurring tasks
7. Export tasks to JSON/CSV
8. Add task statistics dashboard
9. Add multiple views (list, grid, calendar)
10. Add keyboard shortcuts

---

## 🧪 Testing Scenarios

Test these scenarios:
1. Create a task with all fields
2. Create a task with only required fields
3. Edit an existing task
4. Delete a task (with confirmation)
5. Mark task as completed
6. Filter tasks by different criteria
7. Switch between dark and light mode
8. Refresh page and verify data persists
9. Test on mobile viewport
10. Try to submit empty form (validation)

---

**Good luck with your task manager! This assignment will strengthen your understanding of MUI and state management. 🚀**

