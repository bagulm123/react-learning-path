# Assignment 5: Movie Database Explorer

**Focus**: Advanced patterns, animations, performance optimization  
**Estimated Time**: 18-20 hours  
**Difficulty**: ⭐⭐⭐⭐⭐

---

## 🎯 Learning Objectives

By the end of this assignment, you will understand:
- Tailwind CSS utility-first approach
- Framer Motion animations
- Infinite scroll implementation
- Debouncing for search optimization
- Intersection Observer API
- Lazy loading images
- Performance optimization (memo, useMemo, useCallback)
- Error boundaries
- Advanced React Router patterns
- Custom hooks for complex logic

---

## 📋 Requirements

### Technical Stack
- React 18+ with Vite
- Tailwind CSS
- Framer Motion
- TMDB API (The Movie Database)
- React Router v6
- React Intersection Observer
- Axios

### Features Required

1. ✅ **Home Page**
   - Trending movies section
   - Popular movies section
   - Top rated movies section
   - Upcoming movies section
   - Each section with horizontal scroll

2. ✅ **Search Functionality**
   - Search bar in navbar
   - Debounced search (wait for user to stop typing)
   - Search results page
   - Real-time search suggestions (optional)
   - Show "no results" state

3. ✅ **Infinite Scroll**
   - Load more movies as user scrolls
   - Loading indicator at bottom
   - Intersection Observer for trigger
   - Handle pagination from API

4. ✅ **Movie Card**
   - Poster image with lazy loading
   - Movie title
   - Release year
   - Rating with stars
   - Hover animation (scale up)
   - Click to navigate to details

5. ✅ **Movie Details Page**
   - Route: `/movie/:id`
   - Full movie information
   - Backdrop image
   - Poster, title, tagline
   - Overview, genres, runtime
   - Cast section (horizontal scroll)
   - Similar movies section
   - Trailers/videos section
   - Smooth page transitions

6. ✅ **Favorites System**
   - Add/remove from favorites
   - Favorites page showing saved movies
   - Persist in LocalStorage
   - Heart icon animation

7. ✅ **Performance Features**
   - Image lazy loading with placeholders
   - Debounced search
   - Memoized components
   - Optimized re-renders
   - Loading skeletons

8. ✅ **Animations**
   - Page transitions
   - Card hover effects
   - Favorite button animation
   - Smooth scrolling
   - Fade-in animations

### Additional Requirements
- Responsive design (mobile-first)
- Error boundaries for error handling
- Loading states everywhere
- Professional UI with Tailwind
- Accessible (keyboard navigation, ARIA labels)

---

## 🚀 Setup Instructions

### Step 1: Get TMDB API Key

1. Go to [TMDB](https://www.themoviedb.org/)
2. Create account and verify email
3. Go to Settings → API
4. Request API key (Developer option)
5. Fill the form
6. Copy your API key (v3 auth)

### Step 2: Create Project

```bash
cd ~/DevEnv/learnings/react-course/assignment-05-movie-explorer

# Create Vite React project
npm create vite@latest . -- --template react

# Install dependencies
npm install
```

### Step 3: Install Packages

```bash
# Core packages
npm install axios react-router-dom

# Tailwind CSS
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p

# Framer Motion for animations
npm install framer-motion

# Intersection Observer
npm install react-intersection-observer

# Icons
npm install react-icons
```

### Step 4: Configure Tailwind CSS

Update `tailwind.config.js`:
```javascript
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

Update `src/index.css`:
```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### Step 5: Set Up Environment Variables

Create `.env.local`:
```env
VITE_TMDB_API_KEY=your_api_key_here
VITE_TMDB_BASE_URL=https://api.themoviedb.org/3
VITE_TMDB_IMAGE_BASE_URL=https://image.tmdb.org/t/p
```

Create `.env.example`:
```env
VITE_TMDB_API_KEY=your_tmdb_api_key_here
VITE_TMDB_BASE_URL=https://api.themoviedb.org/3
VITE_TMDB_IMAGE_BASE_URL=https://image.tmdb.org/t/p
```

### Step 6: Start Development Server

```bash
npm run dev
```

---

## 📁 Recommended Folder Structure

```
assignment-05-movie-explorer/
├── public/
├── src/
│   ├── components/
│   │   ├── Layout/
│   │   │   ├── Navbar.jsx
│   │   │   └── Footer.jsx
│   │   ├── MovieCard/
│   │   │   └── MovieCard.jsx
│   │   ├── MovieGrid/
│   │   │   └── MovieGrid.jsx
│   │   ├── MovieRow/
│   │   │   └── MovieRow.jsx
│   │   ├── SearchBar/
│   │   │   └── SearchBar.jsx
│   │   ├── LazyImage/
│   │   │   └── LazyImage.jsx
│   │   ├── LoadingSkeleton/
│   │   │   └── MovieCardSkeleton.jsx
│   │   ├── ErrorBoundary/
│   │   │   └── ErrorBoundary.jsx
│   │   └── FavoriteButton/
│   │       └── FavoriteButton.jsx
│   ├── pages/
│   │   ├── HomePage.jsx
│   │   ├── SearchPage.jsx
│   │   ├── MovieDetailsPage.jsx
│   │   └── FavoritesPage.jsx
│   ├── hooks/
│   │   ├── useDebounce.js
│   │   ├── useMovies.js
│   │   ├── useInfiniteScroll.js
│   │   ├── useFavorites.js
│   │   └── useLocalStorage.js
│   ├── services/
│   │   ├── api.js
│   │   └── tmdbService.js
│   ├── utils/
│   │   ├── imageUrls.js
│   │   └── helpers.js
│   ├── App.jsx
│   └── main.jsx
├── .env.local
├── .env.example
├── tailwind.config.js
├── package.json
└── README.md
```

---

## 💻 Step-by-Step Implementation Plan

### Phase 1: Setup & API (3-4 hours)
1. Install all dependencies
2. Configure Tailwind CSS
3. Set up TMDB API service
4. Create image helper utilities
5. Test API calls

### Phase 2: Core Components (4-5 hours)
6. Build Navbar with search
7. Build MovieCard with lazy loading
8. Build MovieGrid component
9. Build Loading Skeletons
10. Build Error Boundary

### Phase 3: Pages & Routing (4-5 hours)
11. Set up React Router
12. Build HomePage with sections
13. Build SearchPage
14. Build MovieDetailsPage
15. Build FavoritesPage

### Phase 4: Advanced Features (4-5 hours)
16. Implement debounced search
17. Implement infinite scroll
18. Create useFavorites hook
19. Add Framer Motion animations
20. Optimize with memo/useMemo/useCallback

### Phase 5: Polish & Performance (3-4 hours)
21. Add loading states everywhere
22. Improve animations
23. Test all features
24. Optimize performance
25. Make fully responsive
26. Add final touches

---

## 🎬 TMDB API Endpoints

### Base URL
```
https://api.themoviedb.org/3
```

### Endpoints

**Trending Movies**
```
GET /trending/movie/week?api_key={API_KEY}
```

**Popular Movies**
```
GET /movie/popular?api_key={API_KEY}&page=1
```

**Top Rated**
```
GET /movie/top_rated?api_key={API_KEY}
```

**Search Movies**
```
GET /search/movie?api_key={API_KEY}&query=avengers&page=1
```

**Movie Details**
```
GET /movie/{movie_id}?api_key={API_KEY}
```

**Movie Credits (Cast)**
```
GET /movie/{movie_id}/credits?api_key={API_KEY}
```

**Movie Videos**
```
GET /movie/{movie_id}/videos?api_key={API_KEY}
```

**Similar Movies**
```
GET /movie/{movie_id}/similar?api_key={API_KEY}
```

### Image URLs
```
Poster: https://image.tmdb.org/t/p/w500/{poster_path}
Backdrop: https://image.tmdb.org/t/p/original/{backdrop_path}
Profile: https://image.tmdb.org/t/p/w185/{profile_path}
```

---

## ✅ Features Checklist

### Setup
- [ ] Tailwind CSS configured
- [ ] TMDB API key obtained
- [ ] Environment variables set
- [ ] Framer Motion installed
- [ ] React Router configured

### Components
- [ ] Navbar with search
- [ ] MovieCard
- [ ] MovieGrid
- [ ] LazyImage
- [ ] LoadingSkeleton
- [ ] ErrorBoundary
- [ ] FavoriteButton

### Pages
- [ ] HomePage
- [ ] SearchPage
- [ ] MovieDetailsPage
- [ ] FavoritesPage

### Features
- [ ] Debounced search
- [ ] Infinite scroll
- [ ] Lazy load images
- [ ] Favorites system
- [ ] Page animations
- [ ] Hover effects
- [ ] Loading states
- [ ] Error handling

### Performance
- [ ] React.memo on expensive components
- [ ] useMemo for calculations
- [ ] useCallback for functions
- [ ] Image lazy loading
- [ ] Debouncing implemented

---

## 🐛 Common Challenges & Solutions

### Challenge 1: Images Not Loading
**Solution**: Check image URL construction:
```javascript
const IMAGE_BASE = 'https://image.tmdb.org/t/p/w500';
const imageUrl = posterPath ? `${IMAGE_BASE}${posterPath}` : '/placeholder.jpg';
```

### Challenge 2: Infinite Scroll Triggering Too Early
**Solution**: Adjust Intersection Observer threshold:
```javascript
const { ref, inView } = useInView({
  threshold: 0,
  rootMargin: '100px', // Trigger 100px before bottom
});
```

### Challenge 3: Search Making Too Many Requests
**Solution**: Use debounce:
```javascript
const debouncedSearch = useDebounce(searchTerm, 500);

useEffect(() => {
  if (debouncedSearch) {
    searchMovies(debouncedSearch);
  }
}, [debouncedSearch]);
```

---

## 🎨 Tailwind CSS Tips

### Responsive Grid
```jsx
<div className="grid grid-cols-2 md:grid-cols-4 lg:grid-cols-5 gap-4">
  {/* Movie cards */}
</div>
```

### Hover Effects
```jsx
<div className="transform transition hover:scale-105 hover:shadow-xl">
  {/* Card content */}
</div>
```

### Gradient Background
```jsx
<div className="bg-gradient-to-br from-purple-900 to-blue-900">
  {/* Content */}
</div>
```

---

## 💫 Framer Motion Examples

### Page Transition
```jsx
import { motion } from 'framer-motion';

<motion.div
  initial={{ opacity: 0 }}
  animate={{ opacity: 1 }}
  exit={{ opacity: 0 }}
  transition={{ duration: 0.3 }}
>
  {/* Page content */}
</motion.div>
```

### Card Animation
```jsx
<motion.div
  whileHover={{ scale: 1.05 }}
  whileTap={{ scale: 0.95 }}
>
  {/* Card */}
</motion.div>
```

---

## 📚 Key Concepts to Understand

### 1. Debouncing
Delay execution until user stops typing.

### 2. Infinite Scroll
Load more data as user reaches the bottom.

### 3. Intersection Observer
Detect when element enters viewport.

### 4. Lazy Loading
Load images only when they're about to be visible.

### 5. Memoization
Cache expensive calculations and components.

---

## 🎓 Learning Resources

- [TMDB API Docs](https://developers.themoviedb.org/3)
- [Tailwind CSS Docs](https://tailwindcss.com/docs)
- [Framer Motion Docs](https://www.framer.com/motion/)
- [Intersection Observer API](https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API)
- [React Performance Optimization](https://react.dev/learn/render-and-commit)

---

## 🚀 Deployment

Deploy to Vercel:

```bash
npm run build
vercel --prod
```

**Important**: Add `VITE_TMDB_API_KEY` in Vercel dashboard.

See `../deployment-configs/DEPLOYMENT_GUIDE.md` for detailed instructions.

---

## 📊 Self-Assessment

After completing, rate your understanding (1-5):
- [ ] Tailwind CSS
- [ ] Framer Motion
- [ ] Debouncing
- [ ] Infinite scroll
- [ ] Intersection Observer
- [ ] Lazy loading
- [ ] Performance optimization
- [ ] Advanced React patterns

---

## 🎯 Bonus Challenges (Optional)

1. Add TV shows alongside movies
2. Add person/actor search
3. Add user ratings
4. Add advanced filters (genre, year, rating)
5. Add "Watch Later" list
6. Add movie recommendations based on favorites
7. Add social sharing
8. Add dark/light theme toggle
9. Add keyboard shortcuts
10. Add PWA features

---

## 🧪 Testing Scenarios

Test these scenarios:
1. Load home page with all sections
2. Search for a movie
3. Scroll to trigger infinite scroll
4. Click movie card to see details
5. Add movie to favorites
6. Remove from favorites
7. Navigate between pages
8. Test search with no results
9. Test with slow internet (throttle in DevTools)
10. Test all animations
11. Test on mobile
12. Test keyboard navigation

---

**This is the most advanced assignment! Focus on learning performance optimization and advanced patterns. 🎬🚀**

