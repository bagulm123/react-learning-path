# Assignment 2: Weather Dashboard

**Focus**: API integration, async operations, custom hooks  
**Estimated Time**: 10-12 hours  
**Difficulty**: ⭐⭐⭐☆☆

---

## 🎯 Learning Objectives

By the end of this assignment, you will understand:
- API integration with Axios
- useEffect hook for side effects
- Custom hooks for reusable logic
- Async/await in React
- Environment variables
- Error handling and loading states
- LocalStorage API
- Bootstrap styling in React

---

## 📋 Requirements

### Technical Stack
- React 18+ with Vite
- Axios for HTTP requests
- Bootstrap 5 / React Bootstrap
- OpenWeatherMap API
- React Icons or Font Awesome
- LocalStorage for persistence

### Features Required

1. ✅ **City Search**
   - Input field with search button
   - Search on Enter key press
   - Show search history (last 5 cities)
   - Click history item to load weather

2. ✅ **Current Weather Display**
   - City name and country
   - Weather icon (from API or react-icons)
   - Temperature (Celsius)
   - Weather description
   - Feels like temperature
   - Humidity, pressure, wind speed
   - Sunrise and sunset times

3. ✅ **5-Day Forecast**
   - Cards for each day
   - Date
   - Min/max temperature
   - Weather icon
   - Weather description

4. ✅ **Error Handling**
   - City not found
   - Network errors
   - API errors
   - User-friendly error messages

5. ✅ **Loading States**
   - Loading spinner during API calls
   - Disable search during loading
   - Skeleton loading (optional)

6. ✅ **LocalStorage**
   - Save search history
   - Load on app start
   - Max 5 recent searches

### Additional Requirements
- Responsive Bootstrap layout
- Professional UI with cards and spacing
- Clean error messages
- Temperature unit toggle (Celsius/Fahrenheit) - optional

---

## 🚀 Setup Instructions

### Step 1: Get OpenWeatherMap API Key

1. Go to [OpenWeatherMap](https://openweathermap.org/)
2. Sign up for free account
3. Go to API Keys section
4. Copy your API key

### Step 2: Create Project

```bash
cd ~/DevEnv/learnings/react-course/assignment-02-weather-dashboard

# Create Vite React project
npm create vite@latest . -- --template react

# Install dependencies
npm install
```

### Step 3: Install Required Packages

```bash
# Axios for API calls
npm install axios

# Bootstrap
npm install bootstrap react-bootstrap

# Icons
npm install react-icons

# Optional: PropTypes
npm install prop-types
```

### Step 4: Set Up Environment Variables

Create `.env.local`:
```env
VITE_OPENWEATHER_API_KEY=your_api_key_here
VITE_OPENWEATHER_BASE_URL=https://api.openweathermap.org/data/2.5
```

Create `.env.example`:
```env
VITE_OPENWEATHER_API_KEY=your_openweathermap_api_key_here
VITE_OPENWEATHER_BASE_URL=https://api.openweathermap.org/data/2.5
```

Add to `.gitignore`:
```
.env.local
```

### Step 5: Import Bootstrap

In `src/main.jsx`:
```jsx
import 'bootstrap/dist/css/bootstrap.min.css';
```

### Step 6: Start Development Server

```bash
npm run dev
```

---

## 📁 Recommended Folder Structure

```
assignment-02-weather-dashboard/
├── public/
│   └── favicon.ico
├── src/
│   ├── components/
│   │   ├── SearchBar/
│   │   │   ├── SearchBar.jsx
│   │   │   └── SearchBar.css
│   │   ├── SearchHistory/
│   │   │   ├── SearchHistory.jsx
│   │   │   └── SearchHistory.css
│   │   ├── CurrentWeather/
│   │   │   ├── CurrentWeather.jsx
│   │   │   └── CurrentWeather.css
│   │   ├── Forecast/
│   │   │   ├── Forecast.jsx
│   │   │   ├── ForecastCard.jsx
│   │   │   └── Forecast.css
│   │   ├── Loader/
│   │   │   ├── Loader.jsx
│   │   │   └── Loader.css
│   │   └── ErrorMessage/
│   │       ├── ErrorMessage.jsx
│   │       └── ErrorMessage.css
│   ├── services/
│   │   ├── api.js
│   │   └── weatherService.js
│   ├── hooks/
│   │   ├── useWeatherData.js
│   │   └── useLocalStorage.js
│   ├── utils/
│   │   ├── weatherIcons.js
│   │   └── formatters.js
│   ├── App.jsx
│   ├── App.css
│   └── main.jsx
├── .env.local (DO NOT COMMIT)
├── .env.example (COMMIT THIS)
├── .gitignore
├── index.html
├── package.json
├── vite.config.js
└── README.md
```

---

## 💻 Step-by-Step Implementation Plan

### Phase 1: API Setup (2-3 hours)
1. Set up environment variables
2. Create Axios instance in `services/api.js`
3. Create weather service functions
4. Test API calls in browser console

### Phase 2: Core Components (3-4 hours)
5. Build SearchBar component
6. Build CurrentWeather component
7. Build Forecast components
8. Build Loader and ErrorMessage components

### Phase 3: State Management (2-3 hours)
9. Create useLocalStorage custom hook
10. Create useWeatherData custom hook
11. Integrate hooks in App.jsx
12. Handle loading and error states

### Phase 4: Polish & Testing (2-3 hours)
13. Add search history
14. Improve styling
15. Test error scenarios
16. Make fully responsive
17. Add final touches

---

## 🌐 API Endpoints

### Current Weather
```
GET https://api.openweathermap.org/data/2.5/weather
Parameters:
- q: city name (e.g., "London")
- appid: your API key
- units: metric (for Celsius) or imperial (for Fahrenheit)
```

### 5-Day Forecast
```
GET https://api.openweathermap.org/data/2.5/forecast
Parameters:
- q: city name
- appid: your API key
- units: metric or imperial
```

### Example Response (Current Weather)
```json
{
  "name": "London",
  "sys": { "country": "GB" },
  "weather": [
    {
      "main": "Clouds",
      "description": "scattered clouds",
      "icon": "03d"
    }
  ],
  "main": {
    "temp": 15.5,
    "feels_like": 14.8,
    "humidity": 72,
    "pressure": 1013
  },
  "wind": { "speed": 3.5 },
  "dt": 1634567890
}
```

---

## ✅ Features Checklist

### Core Features
- [ ] City search functionality
- [ ] Current weather display
- [ ] 5-day forecast
- [ ] Loading spinner
- [ ] Error messages
- [ ] Search history
- [ ] Responsive design

### API Integration
- [ ] Axios configured
- [ ] Environment variables set up
- [ ] API service layer created
- [ ] Error handling for API calls
- [ ] Loading states during requests

### Custom Hooks
- [ ] useLocalStorage hook
- [ ] useWeatherData hook
- [ ] Proper cleanup in useEffect

### LocalStorage
- [ ] Save search history
- [ ] Load history on app start
- [ ] Max 5 searches
- [ ] Click history to search

### Error Handling
- [ ] City not found
- [ ] Network errors
- [ ] API key invalid
- [ ] Rate limit exceeded
- [ ] User-friendly messages

### UI/UX
- [ ] Bootstrap cards
- [ ] Professional layout
- [ ] Weather icons
- [ ] Responsive grid
- [ ] Loading indicators
- [ ] Clear CTAs

---

## 🎨 Design Guidelines

### Layout Structure
```
┌─────────────────────────────────┐
│          Header/Title           │
├─────────────────────────────────┤
│  [Search Bar] [Search Button]   │
│     [Search History Tags]       │
├─────────────────────────────────┤
│      Current Weather Card       │
│  ┌───────────────────────────┐  │
│  │ City Name, Country        │  │
│  │ Weather Icon  Temperature │  │
│  │ Description               │  │
│  │ Details (humidity, etc.)  │  │
│  └───────────────────────────┘  │
├─────────────────────────────────┤
│       5-Day Forecast Grid       │
│  [Card] [Card] [Card] [Card]    │
└─────────────────────────────────┘
```

---

## 🐛 Common Challenges & Solutions

### Challenge 1: CORS Error
**Solution**: OpenWeatherMap API should work without CORS issues. If you encounter issues, check your API key.

### Challenge 2: API Key Not Working
**Solution**: 
- Ensure `.env.local` has `VITE_` prefix
- Restart dev server after adding .env
- Check API key is activated (can take a few hours)

### Challenge 3: useEffect Infinite Loop
**Problem**:
```jsx
useEffect(() => {
  fetchWeather();
}, [fetchWeather]); // fetchWeather changes every render
```

**Solution**:
```jsx
useEffect(() => {
  fetchWeather();
}, [city]); // Depend on actual data
```

### Challenge 4: LocalStorage Not Persisting
**Solution**: Ensure you're calling localStorage.setItem:
```jsx
useEffect(() => {
  localStorage.setItem('searchHistory', JSON.stringify(history));
}, [history]);
```

---

## 📚 Key Concepts to Understand

### 1. useEffect Hook
```jsx
useEffect(() => {
  // Side effect code (API call, localStorage, etc.)
  
  return () => {
    // Cleanup function (optional)
  };
}, [dependency]); // Runs when dependency changes
```

### 2. Async/Await in React
```jsx
const fetchData = async () => {
  try {
    const response = await axios.get(url);
    setData(response.data);
  } catch (error) {
    setError(error.message);
  }
};

useEffect(() => {
  fetchData();
}, []);
```

### 3. Custom Hooks
```jsx
// Extract reusable logic into custom hooks
const useWeatherData = (city) => {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(false);
  
  // ... logic
  
  return { data, loading, error };
};
```

### 4. Environment Variables (Vite)
```jsx
const API_KEY = import.meta.env.VITE_OPENWEATHER_API_KEY;
```

---

## 🎓 Learning Resources

- [OpenWeatherMap API Docs](https://openweathermap.org/api)
- [Axios Documentation](https://axios-http.com/docs/intro)
- [React useEffect Hook](https://react.dev/reference/react/useEffect)
- [Custom Hooks Guide](https://react.dev/learn/reusing-logic-with-custom-hooks)
- [LocalStorage MDN](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage)

---

## 🚀 Deployment

Deploy to Vercel:

```bash
npm run build
vercel
```

**Important**: Add environment variable in Vercel dashboard:
- Key: `VITE_OPENWEATHER_API_KEY`
- Value: Your API key

See `../deployment-configs/DEPLOYMENT_GUIDE.md` for detailed instructions.

---

## 📊 Self-Assessment

After completing, rate your understanding (1-5):
- [ ] API integration with Axios
- [ ] useEffect hook
- [ ] Custom hooks
- [ ] Async/await operations
- [ ] Error handling
- [ ] LocalStorage
- [ ] Environment variables
- [ ] Bootstrap styling

---

## 🎯 Bonus Challenges (Optional)

1. Add temperature unit toggle (°C / °F)
2. Add geolocation to get user's current location
3. Add more weather details (UV index, visibility)
4. Add hourly forecast
5. Add weather maps
6. Add favorites cities
7. Add auto-complete for city search
8. Add weather alerts

---

## 🧪 Testing Scenarios

Test these scenarios:
1. Search for valid city (e.g., "London")
2. Search for invalid city (e.g., "asdfghjkl")
3. Turn off internet and search
4. Search multiple cities and check history
5. Refresh page and verify history persists
6. Test on mobile viewport

---

**Ready to start? Use the Cursor prompt above to begin building your API service layer!**

