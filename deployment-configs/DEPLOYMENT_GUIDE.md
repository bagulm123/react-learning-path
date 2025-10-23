# 🚀 Complete Deployment Guide

**By Mahendra Bagul**

This is the moment! Taking your app from localhost to the world wide web! 🌍

I still remember my first deployment – I was nervous, triple-checking everything, convinced something would break. But you know what? It worked! And that feeling of sharing your work with the world? Absolutely incredible.

Let's get your projects live! (And don't worry, I'll walk you through every step.)

---

## 🌐 Netlify Deployment

### Method 1: Using Netlify CLI (Recommended)

#### Step 1: Install Netlify CLI
```bash
npm install -g netlify-cli
```

#### Step 2: Build Your Project
```bash
npm run build
```

#### Step 3: Login to Netlify
```bash
netlify login
```

#### Step 4: Initialize and Deploy
```bash
# Initialize (first time only)
netlify init

# Or deploy directly
netlify deploy

# For production deployment
netlify deploy --prod
```

---

### Method 2: Using Netlify Dashboard (Easiest)

#### Step 1: Push to GitHub
```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git push -u origin main
```

#### Step 2: Connect to Netlify
1. Go to [netlify.com](https://netlify.com)
2. Click "Add new site" → "Import an existing project"
3. Choose "GitHub" and authorize
4. Select your repository

#### Step 3: Configure Build Settings
- **Build command**: `npm run build`
- **Publish directory**: `dist` (for Vite) or `build` (for CRA)
- **Environment variables**: Add if needed

#### Step 4: Deploy
Click "Deploy site" and wait for completion.

---

### Netlify Configuration for React Router

Create `netlify.toml` in your project root:

```toml
[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200
```

Or create `public/_redirects`:
```
/*    /index.html   200
```

---

### Setting Environment Variables in Netlify

1. Go to Site settings → Environment variables
2. Click "Add a variable"
3. Add key-value pairs:
   - Key: `VITE_API_KEY` (for Vite)
   - Value: `your-api-key-here`
4. Redeploy if needed

---

## ▲ Vercel Deployment

### Method 1: Using Vercel CLI

#### Step 1: Install Vercel CLI
```bash
npm install -g vercel
```

#### Step 2: Deploy
```bash
# From your project directory
vercel

# Follow the prompts:
# - Set up and deploy? Yes
# - Which scope? (select)
# - Link to existing project? No (first time)
# - What's your project's name? (enter name)
# - In which directory is your code located? ./
# - Override settings? No (usually)
```

#### Step 3: Production Deployment
```bash
vercel --prod
```

---

### Method 2: Using Vercel Dashboard

#### Step 1: Push to GitHub
```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git push -u origin main
```

#### Step 2: Import Project
1. Go to [vercel.com](https://vercel.com)
2. Click "Add New" → "Project"
3. Import your GitHub repository

#### Step 3: Configure Project
Vercel auto-detects Vite/CRA, but verify:
- **Framework Preset**: Vite (or Create React App)
- **Build Command**: `npm run build` (or auto-detected)
- **Output Directory**: `dist` (or auto-detected)
- **Install Command**: `npm install` (or auto-detected)

#### Step 4: Add Environment Variables
Click "Environment Variables" and add:
- Key: `VITE_API_KEY`
- Value: `your-api-key-here`
- Select: Production, Preview, Development (as needed)

#### Step 5: Deploy
Click "Deploy" and wait for completion.

---

### Vercel Configuration (Optional)

Create `vercel.json` in project root:

```json
{
  "rewrites": [
    { "source": "/(.*)", "destination": "/index.html" }
  ]
}
```

---

## 🔑 Environment Variables Guide

### For Vite Projects

#### Development (.env.local)
```env
VITE_API_KEY=your_api_key_here
VITE_API_URL=https://api.example.com
VITE_APP_NAME=My App
```

#### Access in Code
```javascript
const API_KEY = import.meta.env.VITE_API_KEY;
const API_URL = import.meta.env.VITE_API_URL;
```

#### Important Notes:
- ✅ Prefix with `VITE_` to expose to client
- ❌ Don't commit `.env.local` to Git
- ✅ Commit `.env.example` as template

---

### For Create React App

#### Development (.env.local)
```env
REACT_APP_API_KEY=your_api_key_here
REACT_APP_API_URL=https://api.example.com
```

#### Access in Code
```javascript
const API_KEY = process.env.REACT_APP_API_KEY;
const API_URL = process.env.REACT_APP_API_URL;
```

---

### .env.example Template
```env
# API Keys
VITE_API_KEY=your_openweathermap_api_key_here
VITE_TMDB_API_KEY=your_tmdb_api_key_here

# API URLs
VITE_API_URL=https://api.openweathermap.org/data/2.5
VITE_TMDB_BASE_URL=https://api.themoviedb.org/3

# App Config
VITE_APP_NAME=Weather Dashboard
VITE_ENABLE_ANALYTICS=false
```

---

## 🔧 Common Deployment Issues & Fixes

### Issue 1: Blank Page After Deployment

**Cause**: Incorrect base path or routing issue

**Solutions**:

#### For Vite:
```javascript
// vite.config.js
export default {
  base: '/', // or '/your-repo-name/' for GitHub Pages
}
```

#### For Netlify:
Create `public/_redirects`:
```
/*    /index.html   200
```

#### For Vercel:
Add to `vercel.json`:
```json
{
  "rewrites": [{ "source": "/(.*)", "destination": "/index.html" }]
}
```

---

### Issue 2: Environment Variables Not Working

**Cause**: Wrong prefix or not set in hosting platform

**Solutions**:
1. Check prefix: `VITE_` for Vite, `REACT_APP_` for CRA
2. Set in hosting platform (Netlify/Vercel dashboard)
3. Redeploy after adding variables
4. Clear cache and hard refresh browser

---

### Issue 3: 404 on Page Refresh

**Cause**: React Router SPA not configured on server

**Solutions**: See Netlify/Vercel configuration sections above

---

### Issue 4: Build Fails

**Common Causes**:
- Missing dependencies
- TypeScript errors
- Linting errors
- Unused imports

**Solutions**:
```bash
# Test build locally first
npm run build

# Fix dependencies
npm install

# Check for errors
npm run lint
```

---

### Issue 5: Images Not Loading

**Cause**: Incorrect image paths

**Solutions**:
```jsx
// ❌ Wrong
<img src="/images/photo.jpg" />

// ✅ Correct (for Vite)
import photo from './assets/images/photo.jpg'
<img src={photo} alt="Photo" />

// ✅ Or use public folder
<img src="/photo.jpg" alt="Photo" />  // place in public/photo.jpg
```

---

## 📊 Assignment-Specific Deployment

### Assignment 1: Portfolio (No API, No Env Vars)
```bash
# Netlify
npm run build
netlify deploy --prod

# Vercel
vercel --prod
```
**No special configuration needed.**

---

### Assignment 2: Weather Dashboard (with API Key)

#### .env.local
```env
VITE_OPENWEATHER_API_KEY=your_key_here
```

#### Netlify Setup
1. Build command: `npm run build`
2. Add environment variable in dashboard
3. Deploy

#### Vercel Setup
1. Import project
2. Add `VITE_OPENWEATHER_API_KEY` in settings
3. Deploy

---

### Assignment 3: Task Manager (LocalStorage Only)
```bash
# No environment variables needed
npm run build
netlify deploy --prod
# or
vercel --prod
```

---

### Assignment 4: E-Commerce (External API)

#### If using FakeStore API (no key needed):
```bash
npm run build
netlify deploy --prod
```

#### If using API with key:
Set environment variables in hosting platform.

---

### Assignment 5: Movie Explorer (TMDB API)

#### .env.local
```env
VITE_TMDB_API_KEY=your_tmdb_key_here
VITE_TMDB_BASE_URL=https://api.themoviedb.org/3
```

#### Deployment:
1. Add environment variables in Netlify/Vercel
2. Deploy

---

## 🎨 Custom Domain Setup

### Netlify Custom Domain

1. Go to Site settings → Domain management
2. Click "Add custom domain"
3. Enter your domain (e.g., `myportfolio.com`)
4. Follow DNS configuration instructions
5. Wait for SSL certificate (automatic)

---

### Vercel Custom Domain

1. Go to Project settings → Domains
2. Enter your domain
3. Follow DNS configuration instructions
4. Wait for SSL certificate (automatic)

---

## 📈 Performance Optimization Before Deployment

### 1. Optimize Images
```bash
# Use image optimization tools
npm install -D vite-plugin-imagemin
```

### 2. Code Splitting
```jsx
import { lazy, Suspense } from 'react';

const About = lazy(() => import('./pages/About'));

function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <About />
    </Suspense>
  );
}
```

### 3. Remove Console Logs
```javascript
// vite.config.js
export default {
  build: {
    minify: 'terser',
    terserOptions: {
      compress: {
        drop_console: true,
      },
    },
  },
}
```

### 4. Analyze Bundle Size
```bash
npm run build -- --mode analyze
```

---

## 🧪 Pre-Deployment Checklist

Before deploying, ensure:

- [ ] `npm run build` works without errors
- [ ] All environment variables documented in `.env.example`
- [ ] No console.log statements in production code
- [ ] All images optimized
- [ ] Responsive design tested
- [ ] Accessibility checked
- [ ] Meta tags added for SEO
- [ ] Favicon added
- [ ] 404 page handled
- [ ] Loading states work
- [ ] Error boundaries in place
- [ ] React Router redirects configured
- [ ] HTTPS working (automatic with Netlify/Vercel)
- [ ] Tested on multiple browsers
- [ ] Mobile tested

---

## 📱 Adding PWA Features (Optional)

### Vite PWA Plugin
```bash
npm install -D vite-plugin-pwa
```

```javascript
// vite.config.js
import { VitePWA } from 'vite-plugin-pwa'

export default {
  plugins: [
    VitePWA({
      registerType: 'autoUpdate',
      manifest: {
        name: 'My App',
        short_name: 'App',
        theme_color: '#ffffff',
        icons: [
          {
            src: '/icon-192x192.png',
            sizes: '192x192',
            type: 'image/png'
          }
        ]
      }
    })
  ]
}
```

---

## 📊 Monitoring & Analytics

### Google Analytics (Optional)
```bash
npm install react-ga4
```

```javascript
// src/utils/analytics.js
import ReactGA from 'react-ga4';

export const initGA = () => {
  ReactGA.initialize('G-XXXXXXXXXX');
};

export const logPageView = () => {
  ReactGA.send({ hitType: 'pageview', page: window.location.pathname });
};
```

---

## 🔒 Security Best Practices

1. **Never commit API keys**
   - Use `.env.local`
   - Add to `.gitignore`

2. **Use HTTPS**
   - Automatic with Netlify/Vercel

3. **Validate inputs**
   - Sanitize user input
   - Use proper form validation

4. **Update dependencies**
   ```bash
   npm audit
   npm audit fix
   ```

---

## 📝 Deployment Workflow Template

```bash
# 1. Test locally
npm run dev
# Test all features

# 2. Build locally
npm run build
npm run preview  # Test production build

# 3. Commit changes
git add .
git commit -m "feat: add new feature"
git push origin main

# 4. Deploy (auto-deploy if connected to GitHub)
# Or manual:
netlify deploy --prod
# or
vercel --prod

# 5. Test production site
# Check all features work
# Test on mobile

# 6. Update README with live demo link
```

---

## 🎯 Quick Commands Reference

### Netlify
```bash
# Install CLI
npm install -g netlify-cli

# Login
netlify login

# Deploy to draft
netlify deploy

# Deploy to production
netlify deploy --prod

# Open dashboard
netlify open

# View logs
netlify logs
```

### Vercel
```bash
# Install CLI
npm install -g vercel

# Deploy to preview
vercel

# Deploy to production
vercel --prod

# List deployments
vercel ls

# View logs
vercel logs
```

---

## 📚 Additional Resources

- [Netlify Docs](https://docs.netlify.com/)
- [Vercel Docs](https://vercel.com/docs)
- [Vite Deployment](https://vitejs.dev/guide/static-deploy.html)
- [React Deployment](https://create-react-app.dev/docs/deployment/)

---

**Remember**: Always test your build locally with `npm run build` and `npm run preview` before deploying!

