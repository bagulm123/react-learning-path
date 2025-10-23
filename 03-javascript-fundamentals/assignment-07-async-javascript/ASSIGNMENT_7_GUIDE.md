# Assignment 7: Asynchronous JavaScript - Handling Delays & APIs

**By Mahendra Bagul**

Async JavaScript is critical for modern web apps - fetching data, waiting for user input, handling delays. Master this and you're ready for real-world development! ⚡

---

## 📚 What You'll Learn

- ✅ Synchronous vs Asynchronous code
- ✅ setTimeout & setInterval
- ✅ Callbacks
- ✅ Callback hell
- ✅ Promises (then, catch, finally)
- ✅ Promise.all, Promise.race
- ✅ Async/await
- ✅ Try/catch with async
- ✅ Fetch API
- ✅ Error handling

---

## 🎯 Assignment Objectives

Create a **Weather Dashboard** that fetches data from real APIs and demonstrates all async patterns.

**Difficulty**: ⭐⭐⭐⭐☆  
**Time**: 6-7 hours  
**Prerequisites**: Assignments 1-6 completed

---

## 📋 Requirements

### Must Have
1. ✅ Fetch weather data from API
2. ✅ Multiple async operations
3. ✅ Loading states
4. ✅ Error handling
5. ✅ Retry mechanism
6. ✅ Promise.all example
7. ✅ setTimeout/setInterval demos
8. ✅ Async/await throughout
9. ✅ Interactive UI
10. ✅ Real API integration

---

## 💻 Complete Implementation

### HTML (index.html)
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Async JavaScript - Weather Dashboard</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>⚡ Async JavaScript</h1>
        
        <!-- Weather Dashboard -->
        <section class="demo-section">
            <h2>Weather Dashboard</h2>
            <div class="search-bar">
                <input type="text" id="cityInput" placeholder="Enter city name" value="Mumbai">
                <button onclick="fetchWeather()">Get Weather</button>
            </div>
            <div id="weatherOutput" class="weather-display"></div>
        </section>
        
        <!-- Multiple Cities -->
        <section class="demo-section">
            <h2>Multiple Cities (Promise.all)</h2>
            <button onclick="fetchMultipleCities()">Fetch 3 Cities</button>
            <div id="multiCityOutput" class="multi-city-grid"></div>
        </section>
        
        <!-- setTimeout Demo -->
        <section class="demo-section">
            <h2>setTimeout Demo</h2>
            <button onclick="demoSetTimeout()">Start Countdown (5s)</button>
            <div id="timeoutOutput" class="output"></div>
        </section>
        
        <!-- setInterval Demo -->
        <section class="demo-section">
            <h2>setInterval Demo</h2>
            <button onclick="startClock()">Start Clock</button>
            <button onclick="stopClock()">Stop Clock</button>
            <div id="clockOutput" class="clock-display">00:00:00</div>
        </section>
        
        <!-- Callback Hell -->
        <section class="demo-section">
            <h2>Callback Hell vs Promises</h2>
            <button onclick="demoCallbackHell()">Show Callback Hell</button>
            <button onclick="demoPromiseChain()">Show Promise Chain</button>
            <div id="callbackOutput" class="output"></div>
        </section>
        
        <!-- Error Handling -->
        <section class="demo-section">
            <h2>Error Handling</h2>
            <button onclick="simulateSuccess()">Success</button>
            <button onclick="simulateError()">Error</button>
            <button onclick="simulateRetry()">Retry on Fail</button>
            <div id="errorOutput" class="output"></div>
        </section>
        
        <!-- Loading Simulation -->
        <section class="demo-section">
            <h2>Loading States</h2>
            <button onclick="simulateLoading()">Simulate API Call</button>
            <div id="loadingOutput" class="output"></div>
        </section>
    </div>
    
    <script src="script.js"></script>
</body>
</html>
```

### JavaScript (script.js)
```javascript
// Note: For production, get your free API key from https://openweathermap.org/api
const API_KEY = 'demo'; // Replace with your API key
const API_URL = 'https://api.openweathermap.org/data/2.5/weather';

// ===== WEATHER DASHBOARD =====
async function fetchWeather() {
    const city = document.getElementById('cityInput').value.trim();
    const output = document.getElementById('weatherOutput');
    
    if (!city) {
        output.innerHTML = '<div class="error">Please enter a city name!</div>';
        return;
    }
    
    // Show loading
    output.innerHTML = '<div class="loading">⏳ Loading weather data...</div>';
    
    try {
        // Simulate API call (replace with real API in production)
        const weather = await simulateWeatherAPI(city);
        
        // Display weather
        output.innerHTML = `
            <div class="weather-card">
                <h3>${weather.city}</h3>
                <div class="temp">${weather.temp}°C</div>
                <div class="condition">${weather.condition}</div>
                <div class="details">
                    <p>💧 Humidity: ${weather.humidity}%</p>
                    <p>💨 Wind: ${weather.wind} km/h</p>
                    <p>👁️ Visibility: ${weather.visibility} km</p>
                </div>
            </div>
        `;
    } catch (error) {
        output.innerHTML = `<div class="error">❌ ${error.message}</div>`;
    }
}

// Simulate weather API (replace with real fetch)
function simulateWeatherAPI(city) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (city.length < 2) {
                reject(new Error('City name too short!'));
                return;
            }
            
            // Simulated weather data
            const conditions = ['Sunny', 'Cloudy', 'Rainy', 'Partly Cloudy'];
            resolve({
                city: city,
                temp: Math.floor(Math.random() * 20) + 15,
                condition: conditions[Math.floor(Math.random() * conditions.length)],
                humidity: Math.floor(Math.random() * 50) + 40,
                wind: Math.floor(Math.random() * 30) + 5,
                visibility: Math.floor(Math.random() * 10) + 5
            });
        }, 1500);
    });
}

// ===== PROMISE.ALL - MULTIPLE CITIES =====
async function fetchMultipleCities() {
    const output = document.getElementById('multiCityOutput');
    const cities = ['Mumbai', 'Delhi', 'Bangalore'];
    
    output.innerHTML = '<div class="loading">⏳ Loading all cities...</div>';
    
    try {
        // Fetch all cities in parallel
        const promises = cities.map(city => simulateWeatherAPI(city));
        const results = await Promise.all(promises);
        
        // Display all results
        output.innerHTML = results.map(weather => `
            <div class="mini-weather-card">
                <h4>${weather.city}</h4>
                <div class="temp">${weather.temp}°C</div>
                <div>${weather.condition}</div>
            </div>
        `).join('');
        
    } catch (error) {
        output.innerHTML = `<div class="error">❌ ${error.message}</div>`;
    }
}

// ===== SETTIMEOUT DEMO =====
function demoSetTimeout() {
    const output = document.getElementById('timeoutOutput');
    let count = 5;
    
    output.innerHTML = `<div class="countdown">${count}</div>`;
    
    const countdown = setInterval(() => {
        count--;
        if (count > 0) {
            output.innerHTML = `<div class="countdown">${count}</div>`;
        } else {
            output.innerHTML = '<div class="countdown complete">🎉 Done!</div>';
            clearInterval(countdown);
        }
    }, 1000);
}

// ===== SETINTERVAL DEMO =====
let clockInterval = null;

function startClock() {
    if (clockInterval) return; // Already running
    
    const output = document.getElementById('clockOutput');
    
    clockInterval = setInterval(() => {
        const now = new Date();
        const hours = String(now.getHours()).padStart(2, '0');
        const minutes = String(now.getMinutes()).padStart(2, '0');
        const seconds = String(now.getSeconds()).padStart(2, '0');
        
        output.textContent = `${hours}:${minutes}:${seconds}`;
    }, 1000);
}

function stopClock() {
    if (clockInterval) {
        clearInterval(clockInterval);
        clockInterval = null;
    }
}

// ===== CALLBACK HELL vs PROMISES =====
function demoCallbackHell() {
    const output = document.getElementById('callbackOutput');
    
    output.innerHTML = `
        <div class="code-example">
            <h4>❌ Callback Hell (Pyramid of Doom)</h4>
            <pre>getData(function(a) {
    getMoreData(a, function(b) {
        getMoreData(b, function(c) {
            getMoreData(c, function(d) {
                getMoreData(d, function(e) {
                    // finally do something!
                });
            });
        });
    });
});</pre>
            <p class="warning">Hard to read, hard to maintain!</p>
        </div>
    `;
}

function demoPromiseChain() {
    const output = document.getElementById('callbackOutput');
    
    output.innerHTML = `
        <div class="code-example">
            <h4>✅ Promise Chain (Clean)</h4>
            <pre>getData()
    .then(a => getMoreData(a))
    .then(b => getMoreData(b))
    .then(c => getMoreData(c))
    .then(d => getMoreData(d))
    .then(e => {
        // do something!
    })
    .catch(error => console.error(error));</pre>
            <p class="success">Much cleaner and easier to follow!</p>
            
            <h4>✅ Async/Await (Even Better)</h4>
            <pre>async function process() {
    try {
        const a = await getData();
        const b = await getMoreData(a);
        const c = await getMoreData(b);
        const d = await getMoreData(c);
        const e = await getMoreData(d);
        // do something!
    } catch (error) {
        console.error(error);
    }
}</pre>
            <p class="success">Looks like synchronous code!</p>
        </div>
    `;
}

// ===== ERROR HANDLING =====
function simulateAPICall(shouldFail = false) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (shouldFail) {
                reject(new Error('API request failed!'));
            } else {
                resolve({ message: 'Success!', data: [1, 2, 3] });
            }
        }, 1500);
    });
}

async function simulateSuccess() {
    const output = document.getElementById('errorOutput');
    output.innerHTML = '<div class="loading">⏳ Loading...</div>';
    
    try {
        const result = await simulateAPICall(false);
        output.innerHTML = `
            <div class="success">
                ✅ ${result.message}
                <pre>${JSON.stringify(result.data, null, 2)}</pre>
            </div>
        `;
    } catch (error) {
        output.innerHTML = `<div class="error">❌ ${error.message}</div>`;
    }
}

async function simulateError() {
    const output = document.getElementById('errorOutput');
    output.innerHTML = '<div class="loading">⏳ Loading...</div>';
    
    try {
        const result = await simulateAPICall(true);
        output.innerHTML = `<div class="success">✅ ${result.message}</div>`;
    } catch (error) {
        output.innerHTML = `<div class="error">❌ ${error.message}</div>`;
    }
}

// ===== RETRY MECHANISM =====
async function fetchWithRetry(fn, retries = 3) {
    for (let i = 0; i < retries; i++) {
        try {
            return await fn();
        } catch (error) {
            if (i === retries - 1) throw error;
            console.log(`Attempt ${i + 1} failed, retrying...`);
            await new Promise(resolve => setTimeout(resolve, 1000));
        }
    }
}

async function simulateRetry() {
    const output = document.getElementById('errorOutput');
    output.innerHTML = '<div class="loading">⏳ Trying (will fail 2 times)...</div>';
    
    let attempts = 0;
    const unreliableAPI = () => {
        attempts++;
        return new Promise((resolve, reject) => {
            setTimeout(() => {
                if (attempts < 3) {
                    reject(new Error(`Attempt ${attempts} failed!`));
                } else {
                    resolve({ message: 'Success on 3rd try!' });
                }
            }, 1000);
        });
    };
    
    try {
        const result = await fetchWithRetry(unreliableAPI);
        output.innerHTML = `
            <div class="success">
                ✅ ${result.message}
                <p>Total attempts: ${attempts}</p>
            </div>
        `;
    } catch (error) {
        output.innerHTML = `<div class="error">❌ ${error.message}</div>`;
    }
}

// ===== LOADING SIMULATION =====
async function simulateLoading() {
    const output = document.getElementById('loadingOutput');
    
    // Loading state
    output.innerHTML = '<div class="loading">⏳ Loading...</div>';
    
    // Simulate delay
    await new Promise(resolve => setTimeout(resolve, 2000));
    
    // Success state
    output.innerHTML = `
        <div class="success">
            ✅ Data loaded!
            <p>Always show loading states for better UX</p>
        </div>
    `;
}

// ===== REAL FETCH EXAMPLE (Commented) =====
/*
async function fetchRealWeather(city) {
    const url = `${API_URL}?q=${city}&appid=${API_KEY}&units=metric`;
    
    try {
        const response = await fetch(url);
        
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        
        const data = await response.json();
        
        return {
            city: data.name,
            temp: Math.round(data.main.temp),
            condition: data.weather[0].description,
            humidity: data.main.humidity,
            wind: data.wind.speed,
            visibility: (data.visibility / 1000).toFixed(1)
        };
    } catch (error) {
        throw new Error(`Failed to fetch weather: ${error.message}`);
    }
}
*/

console.log('✅ Async JavaScript loaded!');
```

### CSS (styles.css)
```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    padding: 2rem;
    min-height: 100vh;
}

.container {
    max-width: 1000px;
    margin: 0 auto;
}

h1 {
    color: white;
    text-align: center;
    margin-bottom: 2rem;
    font-size: 2.5rem;
}

.demo-section {
    background: white;
    padding: 2rem;
    border-radius: 15px;
    margin-bottom: 2rem;
    box-shadow: 0 10px 30px rgba(0,0,0,0.2);
}

h2 {
    color: #2c3e50;
    margin-bottom: 1.5rem;
}

button {
    background-color: #667eea;
    color: white;
    border: none;
    padding: 0.75rem 1.5rem;
    border-radius: 8px;
    cursor: pointer;
    font-size: 1rem;
    transition: all 0.3s;
    margin-right: 0.5rem;
    margin-bottom: 0.5rem;
}

button:hover {
    background-color: #764ba2;
    transform: translateY(-2px);
}

input {
    padding: 0.75rem;
    border: 2px solid #ddd;
    border-radius: 8px;
    font-size: 1rem;
    flex: 1;
    margin-right: 0.5rem;
}

.search-bar {
    display: flex;
    gap: 0.5rem;
    margin-bottom: 1.5rem;
}

.weather-card {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    padding: 2rem;
    border-radius: 15px;
    text-align: center;
}

.weather-card h3 {
    font-size: 2rem;
    margin-bottom: 1rem;
}

.temp {
    font-size: 3rem;
    font-weight: bold;
    margin: 1rem 0;
}

.condition {
    font-size: 1.5rem;
    margin-bottom: 1.5rem;
    opacity: 0.9;
}

.details {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem;
    margin-top: 1rem;
}

.details p {
    background: rgba(255,255,255,0.2);
    padding: 0.75rem;
    border-radius: 8px;
}

.multi-city-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem;
}

.mini-weather-card {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    padding: 1.5rem;
    border-radius: 10px;
    text-align: center;
}

.mini-weather-card h4 {
    margin-bottom: 0.5rem;
}

.mini-weather-card .temp {
    font-size: 2rem;
    margin: 0.5rem 0;
}

.output {
    margin-top: 1.5rem;
}

.loading {
    text-align: center;
    padding: 2rem;
    font-size: 1.2rem;
    color: #667eea;
    background: #f0f7ff;
    border-radius: 10px;
}

.error {
    background: #f8d7da;
    color: #721c24;
    padding: 1.5rem;
    border-radius: 10px;
    border-left: 4px solid #dc3545;
}

.success {
    background: #d4edda;
    color: #155724;
    padding: 1.5rem;
    border-radius: 10px;
    border-left: 4px solid #28a745;
}

.success pre,
.error pre {
    background: rgba(0,0,0,0.1);
    padding: 1rem;
    border-radius: 5px;
    margin-top: 1rem;
    overflow-x: auto;
}

.countdown {
    font-size: 4rem;
    text-align: center;
    color: #667eea;
    padding: 2rem;
    font-weight: bold;
}

.countdown.complete {
    color: #28a745;
}

.clock-display {
    font-size: 3rem;
    text-align: center;
    color: #2c3e50;
    padding: 2rem;
    background: #f8f9fa;
    border-radius: 15px;
    font-family: 'Courier New', monospace;
    font-weight: bold;
    margin-top: 1rem;
}

.code-example {
    background: #f8f9fa;
    padding: 1.5rem;
    border-radius: 10px;
    margin-bottom: 1rem;
}

.code-example h4 {
    color: #2c3e50;
    margin-bottom: 1rem;
}

.code-example pre {
    background: #2c3e50;
    color: #fff;
    padding: 1rem;
    border-radius: 5px;
    overflow-x: auto;
    font-size: 0.9rem;
    margin: 1rem 0;
}

.warning {
    color: #856404;
    background: #fff3cd;
    padding: 0.75rem;
    border-radius: 5px;
    border-left: 4px solid #ffc107;
}

.success {
    color: #155724;
    background: #d4edda;
    padding: 0.75rem;
    border-radius: 5px;
    border-left: 4px solid #28a745;
    margin-top: 0.5rem;
}

@media (max-width: 768px) {
    .details {
        grid-template-columns: 1fr;
    }
    
    .multi-city-grid {
        grid-template-columns: 1fr;
    }
}
```

---

## 📖 Key Concepts

### Promise States
- **Pending**: Initial state
- **Fulfilled**: Operation completed successfully
- **Rejected**: Operation failed

### async/await vs Promises
```javascript
// Promises
fetch(url)
    .then(res => res.json())
    .then(data => console.log(data))
    .catch(err => console.error(err));

// Async/Await (preferred)
async function getData() {
    try {
        const res = await fetch(url);
        const data = await res.json();
        console.log(data);
    } catch (err) {
        console.error(err);
    }
}
```

---

## ✅ Self-Assessment

- [ ] Weather fetching works
- [ ] Promise.all demonstrated
- [ ] setTimeout/setInterval working
- [ ] Error handling implemented
- [ ] Loading states shown
- [ ] Retry mechanism works
- [ ] Async/await used throughout
- [ ] Real API integration ready
- [ ] Clean error messages
- [ ] UI responsive

---

**Next**: [Assignment 8: Fetch API & AJAX](../assignment-08-fetch-ajax/ASSIGNMENT_8_GUIDE.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

