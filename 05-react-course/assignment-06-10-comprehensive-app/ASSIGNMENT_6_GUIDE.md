# Assignment 6: Foundation & Authentication

**Part of**: Comprehensive Social Media Dashboard (ConnectHub)  
**Estimated Time**: 10-12 hours  
**Difficulty**: ⭐⭐⭐⭐☆

---

## 🎯 Learning Objectives

By the end of this assignment, you will understand:
- Setting up a production-ready React project with TypeScript
- Project architecture and folder structure at scale
- Firebase Authentication setup
- Protected routes and auth guards
- User registration and login flows
- Profile management
- Theme system implementation
- Environment configuration for multiple environments

---

## 📋 What You'll Build

In this assignment, you'll set up the **foundation** of ConnectHub:

### Features
1. ✅ Project setup with TypeScript and Vite
2. ✅ Firebase Authentication integration
3. ✅ User registration (email/password)
4. ✅ User login
5. ✅ Google OAuth login
6. ✅ Password reset functionality
7. ✅ Email verification
8. ✅ Protected routes (auth required)
9. ✅ User profile page
10. ✅ Edit profile (name, bio, avatar)
11. ✅ Theme system (dark/light mode)
12. ✅ Responsive navigation

---

## 🛠️ Tech Stack for Assignment 6

### Core
- React 18 + TypeScript
- Vite
- React Router v6

### State Management
- Redux Toolkit
- Redux Persist

### UI
- Material-UI (MUI) v5
- Framer Motion (for animations)

### Authentication
- Firebase Authentication
- Firebase Firestore (for user profiles)
- Firebase Storage (for profile images)

### Forms
- React Hook Form
- Yup (validation)

---

## 🚀 Setup Instructions

### Step 1: Create Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click "Add project"
3. Name it "connecthub" (or your choice)
4. Disable Google Analytics (or enable if you want)
5. Click "Create project"

### Step 2: Enable Authentication Methods

1. In Firebase Console, go to **Authentication**
2. Click "Get started"
3. Enable **Email/Password**
4. Enable **Google** sign-in
5. Add your email as test user

### Step 3: Create Firestore Database

1. Go to **Firestore Database**
2. Click "Create database"
3. Start in **Test mode** (we'll add security rules later)
4. Choose a location close to you

### Step 4: Set Up Storage

1. Go to **Storage**
2. Click "Get started"
3. Start in **Test mode**

### Step 5: Get Firebase Config

1. Go to Project Settings (gear icon)
2. Scroll to "Your apps"
3. Click web icon `</>`
4. Register app: "connecthub-web"
5. Copy the firebaseConfig object

### Step 6: Create React Project

```bash
cd ~/DevEnv/learnings/react-course/assignment-06-10-comprehensive-app

# Create Vite project with TypeScript
npm create vite@latest connecthub -- --template react-ts

cd connecthub

# Install dependencies
npm install
```

### Step 7: Install Required Packages

```bash
# Routing
npm install react-router-dom

# State Management
npm install @reduxjs/toolkit react-redux redux-persist

# Firebase
npm install firebase

# UI
npm install @mui/material @emotion/react @emotion/styled
npm install @mui/icons-material

# Forms
npm install react-hook-form yup @hookform/resolvers

# Animations
npm install framer-motion

# Utils
npm install date-fns

# TypeScript types
npm install -D @types/node
```

### Step 8: Set Up Environment Variables

Create `.env.local`:
```env
VITE_FIREBASE_API_KEY=your_api_key
VITE_FIREBASE_AUTH_DOMAIN=your_auth_domain
VITE_FIREBASE_PROJECT_ID=your_project_id
VITE_FIREBASE_STORAGE_BUCKET=your_storage_bucket
VITE_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
VITE_FIREBASE_APP_ID=your_app_id
```

Create `.env.example`:
```env
VITE_FIREBASE_API_KEY=your_api_key
VITE_FIREBASE_AUTH_DOMAIN=your_auth_domain
VITE_FIREBASE_PROJECT_ID=your_project_id
VITE_FIREBASE_STORAGE_BUCKET=your_storage_bucket
VITE_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
VITE_FIREBASE_APP_ID=your_app_id
```

### Step 9: Start Development Server

```bash
npm run dev
```

---

## 📁 Project Structure for Assignment 6

```
connecthub/
├── public/
├── src/
│   ├── components/
│   │   ├── auth/
│   │   │   ├── LoginForm.tsx
│   │   │   ├── RegisterForm.tsx
│   │   │   ├── GoogleAuthButton.tsx
│   │   │   └── PasswordResetDialog.tsx
│   │   ├── layout/
│   │   │   ├── Navbar.tsx
│   │   │   ├── Footer.tsx
│   │   │   └── MainLayout.tsx
│   │   ├── profile/
│   │   │   ├── ProfileHeader.tsx
│   │   │   ├── ProfileEditDialog.tsx
│   │   │   └── AvatarUpload.tsx
│   │   └── common/
│   │       ├── LoadingSpinner.tsx
│   │       ├── ErrorMessage.tsx
│   │       └── ProtectedRoute.tsx
│   ├── pages/
│   │   ├── Auth/
│   │   │   ├── LoginPage.tsx
│   │   │   └── RegisterPage.tsx
│   │   ├── Profile/
│   │   │   └── ProfilePage.tsx
│   │   └── Home/
│   │       └── HomePage.tsx
│   ├── redux/
│   │   ├── store.ts
│   │   ├── slices/
│   │   │   ├── authSlice.ts
│   │   │   ├── userSlice.ts
│   │   │   └── themeSlice.ts
│   │   └── hooks.ts
│   ├── services/
│   │   ├── firebase/
│   │   │   ├── config.ts
│   │   │   ├── auth.ts
│   │   │   ├── firestore.ts
│   │   │   └── storage.ts
│   │   └── api/
│   │       └── userApi.ts
│   ├── types/
│   │   ├── user.ts
│   │   └── auth.ts
│   ├── hooks/
│   │   ├── useAuth.ts
│   │   └── useFirestore.ts
│   ├── utils/
│   │   ├── validators.ts
│   │   └── helpers.ts
│   ├── theme/
│   │   └── theme.ts
│   ├── routes/
│   │   └── AppRoutes.tsx
│   ├── App.tsx
│   ├── main.tsx
│   └── vite-env.d.ts
├── .env.local
├── .env.example
├── .gitignore
├── package.json
├── tsconfig.json
├── vite.config.ts
└── README.md
```

---

## 💻 Step-by-Step Implementation Plan

### Phase 1: Project Setup & Configuration (2-3 hours)

**1.1 Firebase Configuration**
- Create `src/services/firebase/config.ts`
- Initialize Firebase app
- Export auth, firestore, storage instances

**1.2 TypeScript Types**
- Create `src/types/user.ts` for User interface
- Create `src/types/auth.ts` for Auth types
- Set up proper type definitions

**1.3 Redux Setup**
- Configure store with TypeScript
- Set up Redux Persist
- Create typed hooks (useAppDispatch, useAppSelector)

**1.4 MUI Theme**
- Create custom theme in `src/theme/theme.ts`
- Set up dark/light mode
- Configure colors and typography

---

### Phase 2: Authentication Service (2-3 hours)

**2.1 Firebase Auth Service**
Create `src/services/firebase/auth.ts` with functions:
- `signUpWithEmail(email, password, displayName)`
- `signInWithEmail(email, password)`
- `signInWithGoogle()`
- `signOut()`
- `resetPassword(email)`
- `getCurrentUser()`

**2.2 Firestore User Service**
Create `src/services/firebase/firestore.ts` with:
- `createUserProfile(userId, data)`
- `getUserProfile(userId)`
- `updateUserProfile(userId, data)`

**2.3 Storage Service**
Create `src/services/firebase/storage.ts` with:
- `uploadAvatar(file, userId)`
- `deleteAvatar(userId)`

---

### Phase 3: Redux Slices (2 hours)

**3.1 Auth Slice**
`src/redux/slices/authSlice.ts`:
- State: user, loading, error
- Actions: login, logout, signup
- Async thunks for Firebase calls

**3.2 User Slice**
`src/redux/slices/userSlice.ts`:
- State: profile data
- Actions: updateProfile, uploadAvatar

**3.3 Theme Slice**
`src/redux/slices/themeSlice.ts`:
- State: mode (light/dark)
- Actions: toggleTheme

---

### Phase 4: Auth Components (2-3 hours)

**4.1 Login Form**
`src/components/auth/LoginForm.tsx`:
- Email and password inputs
- Form validation with Yup
- Error handling
- "Forgot password" link
- "Sign up" link

**4.2 Register Form**
`src/components/auth/RegisterForm.tsx`:
- Name, email, password, confirm password
- Validation rules
- Terms acceptance
- Error handling

**4.3 Google Auth Button**
- Single sign-on with Google
- Error handling

**4.4 Password Reset Dialog**
- Email input
- Send reset email

---

### Phase 5: Protected Routes & Navigation (1-2 hours)

**5.1 Protected Route Component**
`src/components/common/ProtectedRoute.tsx`:
- Check if user is authenticated
- Redirect to login if not
- Show loading state

**5.2 App Routes**
`src/routes/AppRoutes.tsx`:
- Public routes: /login, /register
- Protected routes: /home, /profile
- 404 page

**5.3 Navbar**
`src/components/layout/Navbar.tsx`:
- Logo
- Navigation links
- User menu (avatar, dropdown)
- Theme toggle
- Logout button

---

### Phase 6: Profile Management (2-3 hours)

**6.1 Profile Page**
`src/pages/Profile/ProfilePage.tsx`:
- Display user info
- Avatar
- Bio
- Member since date
- Edit button

**6.2 Profile Edit Dialog**
`src/components/profile/ProfileEditDialog.tsx`:
- Edit name
- Edit bio
- Upload avatar
- Save changes

**6.3 Avatar Upload**
`src/components/profile/AvatarUpload.tsx`:
- Image preview
- File upload
- Crop functionality (optional)
- Progress indicator

---

## ✅ Features Checklist

### Setup
- [ ] Firebase project created
- [ ] Authentication enabled
- [ ] Firestore database created
- [ ] Storage configured
- [ ] Environment variables set
- [ ] All packages installed

### Authentication
- [ ] User registration working
- [ ] User login working
- [ ] Google OAuth working
- [ ] Password reset working
- [ ] Email verification (optional)
- [ ] Logout working
- [ ] Auth state persistence

### Routes
- [ ] Public routes accessible
- [ ] Protected routes require auth
- [ ] Redirect to login when not authenticated
- [ ] Redirect to home after login
- [ ] 404 page

### Profile
- [ ] View profile
- [ ] Edit profile
- [ ] Upload avatar
- [ ] Update display name
- [ ] Update bio
- [ ] Changes persist in Firestore

### UI/UX
- [ ] Responsive navbar
- [ ] Theme toggle (dark/light)
- [ ] Loading states
- [ ] Error messages
- [ ] Form validation
- [ ] Success notifications
- [ ] Mobile responsive

---

## 🔥 Firebase Security Rules

After testing, update your Firestore rules:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Users collection
    match /users/{userId} {
      // Users can read their own profile
      allow read: if request.auth != null && request.auth.uid == userId;
      // Users can create their own profile
      allow create: if request.auth != null && request.auth.uid == userId;
      // Users can update their own profile
      allow update: if request.auth != null && request.auth.uid == userId;
      // Only admins can delete (add admin check later)
      allow delete: if false;
    }
  }
}
```

Storage rules:
```javascript
rules_version = '2';
service firebase.storage {
  match /b/{bucket}/o {
    match /avatars/{userId}/{allPaths=**} {
      // Users can read/write their own avatars
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

---

## 📊 Data Models

### User Profile (Firestore)
```typescript
interface UserProfile {
  uid: string;
  email: string;
  displayName: string;
  photoURL?: string;
  bio?: string;
  createdAt: Timestamp;
  updatedAt: Timestamp;
  // Will add more fields in later assignments
}
```

### Auth State (Redux)
```typescript
interface AuthState {
  user: User | null;
  loading: boolean;
  error: string | null;
  isAuthenticated: boolean;
}
```

---

## 🐛 Common Challenges & Solutions

### Challenge 1: Firebase Not Initializing
**Solution**: Check environment variables are properly prefixed with `VITE_` and restart dev server.

### Challenge 2: "Permission Denied" Firestore Error
**Solution**: Start with test mode, update rules after testing.

### Challenge 3: Google OAuth Not Working in Development
**Solution**: Add localhost to authorized domains in Firebase Console → Authentication → Settings.

### Challenge 4: TypeScript Errors with Firebase
**Solution**: Ensure Firebase v9+ is installed (modular SDK).

### Challenge 5: Protected Routes Not Working
**Solution**: Check auth state is properly loaded before rendering routes.

---

## 📚 Key Concepts

### 1. Firebase Authentication
Modern authentication with various providers.

### 2. Protected Routes
Route guards that require authentication.

### 3. Redux with TypeScript
Properly typed state management.

### 4. Firebase Firestore
NoSQL document database for user data.

### 5. File Uploads
Uploading and storing images in Firebase Storage.

---

## 🎓 Learning Resources

- [Firebase Auth Docs](https://firebase.google.com/docs/auth)
- [Firestore Docs](https://firebase.google.com/docs/firestore)
- [Redux Toolkit with TypeScript](https://redux-toolkit.js.org/usage/usage-with-typescript)
- [React Hook Form](https://react-hook-form.com/)
- [Yup Validation](https://github.com/jquense/yup)

---

## 🧪 Testing Checklist

Test these scenarios:
1. Register a new account
2. Login with email/password
3. Login with Google
4. Logout and login again
5. Request password reset
6. View profile
7. Edit profile
8. Upload avatar
9. Toggle theme
10. Try accessing protected routes when logged out
11. Refresh page (check persistence)
12. Test on mobile viewport

---

## 🚀 Deployment (Optional for Assignment 6)

You can deploy early to test:
```bash
npm run build
vercel --prod
```

Add environment variables in Vercel dashboard.

---

## 📊 Self-Assessment

After completing, rate your understanding (1-5):
- [ ] Firebase Authentication
- [ ] Firestore database
- [ ] Firebase Storage
- [ ] Protected routes
- [ ] Redux with TypeScript
- [ ] Form validation
- [ ] File uploads
- [ ] MUI theming

---

## 🎯 What's Next?

Once you've completed Assignment 6, you should have:
- ✅ Fully functional authentication system
- ✅ User profiles
- ✅ Protected routes
- ✅ Theme system
- ✅ Solid foundation for the app

### Ready for Assignment 7?
In the next assignment, you'll add:
- Posts creation and management
- Image/video uploads
- Like and save functionality
- Feed with pagination
- Dashboard with analytics charts

👉 [Continue to Assignment 7](./ASSIGNMENT_7_GUIDE.md)

---

**Great job setting up the foundation! Now let's build the core features! 🚀**

