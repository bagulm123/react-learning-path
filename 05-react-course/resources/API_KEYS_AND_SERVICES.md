# 🔑 API Keys & Services Guide

**By Mahendra Bagul**

APIs can seem intimidating at first, but they're actually straightforward once you've set up a few. I'll walk you through each one we use in this course.

**Important:** Never, EVER commit your API keys to Git. Seriously. I've made that mistake (we all have), and it's a pain to fix. Learn from my mistakes! 😅

Let's get you set up! 🔑

---

## 🌦️ Assignment 2: Weather Dashboard

### OpenWeatherMap API

**Website**: [https://openweathermap.org/](https://openweathermap.org/)

**Steps to Get API Key**:
1. Go to [OpenWeatherMap](https://openweathermap.org/)
2. Click "Sign In" → "Create an Account"
3. Verify your email
4. Go to [API Keys](https://home.openweathermap.org/api_keys)
5. Copy your default API key (or create a new one)

**Important Notes**:
- Free tier: 60 calls/minute, 1,000,000 calls/month
- New API keys take 1-2 hours to activate
- Keep your key secure (use .env files)

**Endpoints Used**:
- Current Weather: `https://api.openweathermap.org/data/2.5/weather`
- 5-Day Forecast: `https://api.openweathermap.org/data/2.5/forecast`

**Documentation**: [OpenWeatherMap API Docs](https://openweathermap.org/api)

---

## 🎬 Assignment 5: Movie Explorer

### The Movie Database (TMDB) API

**Website**: [https://www.themoviedb.org/](https://www.themoviedb.org/)

**Steps to Get API Key**:
1. Go to [TMDB](https://www.themoviedb.org/)
2. Create an account
3. Go to Settings → API
4. Request an API key (choose "Developer" option)
5. Fill out the form (you can use placeholder URLs)
6. Copy your API key (v3 auth)

**Important Notes**:
- Free tier: 40 requests/10 seconds
- No credit card required
- Very generous free tier
- Read-only access for free accounts

**Endpoints Used**:
- Search Movies: `/search/movie`
- Popular Movies: `/movie/popular`
- Movie Details: `/movie/{movie_id}`
- Movie Credits: `/movie/{movie_id}/credits`
- Movie Videos: `/movie/{movie_id}/videos`

**Base URL**: `https://api.themoviedb.org/3`

**Documentation**: [TMDB API Docs](https://developers.themoviedb.org/3)

---

## 🛒 Assignment 4: E-Commerce

### FakeStore API

**Website**: [https://fakestoreapi.com/](https://fakestoreapi.com/)

**API Key**: Not required! ✅

**Important Notes**:
- Completely free
- No authentication needed
- Mock data for testing
- Returns fake product data

**Endpoints Used**:
- Get all products: `https://fakestoreapi.com/products`
- Get single product: `https://fakestoreapi.com/products/1`
- Get categories: `https://fakestoreapi.com/products/categories`
- Get products by category: `https://fakestoreapi.com/products/category/electronics`

**Documentation**: [FakeStore API Docs](https://fakestoreapi.com/docs)

---

## 🔥 Assignments 6-10: Comprehensive App

### Firebase (Authentication & Database)

**Website**: [https://firebase.google.com/](https://firebase.google.com/)

**Steps to Get Started**:
1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Sign in with Google account
3. Click "Add project"
4. Enter project name
5. Enable Google Analytics (optional)
6. Click "Create project"

**Setting Up Authentication**:
1. In Firebase Console, go to "Authentication"
2. Click "Get started"
3. Enable authentication methods:
   - Email/Password
   - Google Sign-in
4. Copy your Firebase config

**Getting Firebase Config**:
1. Project Settings (gear icon) → Project settings
2. Scroll to "Your apps"
3. Click web icon (</>)
4. Register app
5. Copy the firebaseConfig object

**Example Firebase Config**:
```javascript
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "your-app.firebaseapp.com",
  projectId: "your-app",
  storageBucket: "your-app.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abc123"
};
```

**Important Notes**:
- Free tier: Spark plan (good for learning)
- Authentication is free up to 10K/month
- Firestore has generous free quotas

**Documentation**: [Firebase Docs](https://firebase.google.com/docs)

---

## 📊 Assignments 6-10: Chart.js (Data Visualization)

### Chart.js

**Website**: [https://www.chartjs.org/](https://www.chartjs.org/)

**Installation**:
```bash
npm install chart.js react-chartjs-2
```

**API Key**: Not required! ✅

**Important Notes**:
- Completely free and open source
- Great documentation
- Many chart types available

**Documentation**: [Chart.js Docs](https://www.chartjs.org/docs/latest/)

---

## 💬 Assignments 9-10: Socket.io (Real-time Features)

### Socket.io

**Website**: [https://socket.io/](https://socket.io/)

**Installation**:
```bash
# Client
npm install socket.io-client

# Server (if you're building one)
npm install socket.io
```

**API Key**: Not required! ✅

**Important Notes**:
- You'll need a backend server
- Can use free hosting like Render or Railway
- Alternative: Use Firebase Realtime Database

**Documentation**: [Socket.io Docs](https://socket.io/docs/v4/)

---

## 🎨 Additional Services (Optional)

### Unsplash API (Free Stock Photos)

**Website**: [https://unsplash.com/developers](https://unsplash.com/developers)

**Use Case**: Get high-quality images for your projects

**Steps**:
1. Create Unsplash account
2. Go to [Developers](https://unsplash.com/developers)
3. Register as a developer
4. Create a new application
5. Copy your Access Key

**Free Tier**: 50 requests/hour

---

### JSONPlaceholder (Fake REST API)

**Website**: [https://jsonplaceholder.typicode.com/](https://jsonplaceholder.typicode.com/)

**API Key**: Not required! ✅

**Use Case**: Testing and prototyping

**Endpoints**:
- Posts: `/posts`
- Comments: `/comments`
- Users: `/users`

---

### REST Countries API

**Website**: [https://restcountries.com/](https://restcountries.com/)

**API Key**: Not required! ✅

**Use Case**: Country data for dropdowns, searches

**Example**: `https://restcountries.com/v3.1/all`

---

## 🔐 Security Best Practices

### 1. Never Commit API Keys
```bash
# Add to .gitignore
.env
.env.local
.env.production.local
```

### 2. Use Environment Variables
```env
# .env.local
VITE_API_KEY=your_key_here
```

```javascript
// Access in code
const API_KEY = import.meta.env.VITE_API_KEY;
```

### 3. Frontend vs Backend Keys

**Frontend-Safe** (OK to expose):
- OpenWeatherMap API key (with domain restrictions)
- TMDB API key (read-only)
- Firebase config

**Backend-Only** (NEVER expose):
- Payment API keys (Stripe secret key)
- Database credentials
- Admin API keys
- AWS secret keys

### 4. Set API Key Restrictions

For APIs that support it (Firebase, Google APIs):
1. Restrict by domain (e.g., only myapp.com)
2. Restrict by IP address
3. Limit API scopes
4. Set quotas

---

## 📊 API Comparison Table

| API | Assignment | Free Tier | API Key Required | Rate Limit |
|-----|------------|-----------|------------------|------------|
| OpenWeatherMap | 2 | ✅ 1M calls/month | ✅ Yes | 60/min |
| TMDB | 5 | ✅ Unlimited* | ✅ Yes | 40/10sec |
| FakeStore API | 4 | ✅ Unlimited | ❌ No | None |
| Firebase | 6-10 | ✅ Spark plan | ✅ Config | Varies |
| Chart.js | 6-10 | ✅ Open source | ❌ No | N/A |
| Socket.io | 9-10 | ✅ Open source | ❌ No | N/A |

---

## 🆘 Troubleshooting API Issues

### Issue: API Key Not Working

**Checklist**:
- [ ] Key is correctly copied (no extra spaces)
- [ ] Using correct environment variable prefix (`VITE_`)
- [ ] Restarted dev server after adding .env
- [ ] Key is activated (some take 1-2 hours)
- [ ] Not exceeding rate limits
- [ ] API key restrictions allow your domain

---

### Issue: CORS Error

**Common Causes**:
1. Trying to call API from browser without CORS support
2. Using wrong endpoint

**Solutions**:
- Most public APIs support CORS
- If not, you may need a backend proxy
- Check API documentation

---

### Issue: 401 Unauthorized

**Causes**:
- Wrong API key
- Expired API key
- API key not included in request

**Solution**:
```javascript
// Make sure API key is included
axios.get(url, {
  params: { api_key: API_KEY }
});
// or
axios.get(url, {
  headers: { Authorization: `Bearer ${API_KEY}` }
});
```

---

### Issue: 429 Too Many Requests

**Cause**: Exceeded rate limit

**Solutions**:
- Implement request caching
- Add delays between requests
- Upgrade to paid tier (if needed)
- Use request debouncing

---

## 📝 Environment Variables Template

Create this as `.env.example` in each project:

```env
# Assignment 2: Weather Dashboard
VITE_OPENWEATHER_API_KEY=your_openweather_api_key_here
VITE_OPENWEATHER_BASE_URL=https://api.openweathermap.org/data/2.5

# Assignment 5: Movie Explorer
VITE_TMDB_API_KEY=your_tmdb_api_key_here
VITE_TMDB_BASE_URL=https://api.themoviedb.org/3

# Assignment 6-10: Firebase
VITE_FIREBASE_API_KEY=your_firebase_api_key
VITE_FIREBASE_AUTH_DOMAIN=your-app.firebaseapp.com
VITE_FIREBASE_PROJECT_ID=your-project-id
VITE_FIREBASE_STORAGE_BUCKET=your-app.appspot.com
VITE_FIREBASE_MESSAGING_SENDER_ID=123456789
VITE_FIREBASE_APP_ID=1:123456789:web:abc123
```

---

## 🎯 Quick Setup Checklist

For each API-based assignment:
- [ ] Create account on API service
- [ ] Get API key / credentials
- [ ] Create `.env.local` file
- [ ] Add API key to `.env.local`
- [ ] Create `.env.example` (without actual keys)
- [ ] Add `.env.local` to `.gitignore`
- [ ] Restart dev server
- [ ] Test API call
- [ ] Add environment variables to hosting platform (Netlify/Vercel)

---

## 📚 Additional Resources

- [How to Hide API Keys](https://dev.to/aneeqakhan/how-to-hide-your-api-keys-in-react-apps-2hbb)
- [Environment Variables in Vite](https://vitejs.dev/guide/env-and-mode.html)
- [Best Practices for API Keys](https://cloud.google.com/docs/authentication/api-keys)

---

**Remember**: Keep your API keys secure and never commit them to Git! 🔒

