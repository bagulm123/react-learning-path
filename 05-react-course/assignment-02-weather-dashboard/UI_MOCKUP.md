# 🌦️ Assignment 2: Weather Dashboard - UI Mockup

Visual guide showing the weather dashboard you'll build with API integration.

---

## 📱 Desktop Layout

```mermaid
graph TD
    A[Weather Dashboard] --> B[Header]
    A --> C[Search Section]
    A --> D[Current Weather Card]
    A --> E[5-Day Forecast]
    A --> F[Search History]
    
    B --> B1[App Title]
    B --> B2[Weather Icon]
    
    C --> C1[City Input]
    C --> C2[Search Button]
    
    D --> D1[City Name]
    D --> D2[Weather Icon]
    D --> D3[Temperature]
    D --> D4[Description]
    D --> D5[Details: Humidity, Wind, Pressure]
    
    E --> E1[Day 1 Card]
    E --> E2[Day 2 Card]
    E --> E3[Day 3 Card]
    E --> E4[Day 4 Card]
    E --> E5[Day 5 Card]
    
    F --> F1[Recent Search 1]
    F --> F2[Recent Search 2]
    F --> F3[Recent Search 3]
```

---

## 🎨 Page Layout Wireframe

```
┌──────────────────────────────────────────────────────┐
│  ☁️ Weather Dashboard                               │  ← Header
└──────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────┐
│  Search for a city:                                  │
│  [___London_____________________] [🔍 Search]        │  ← Search Bar
│                                                      │
│  Recent: [London] [Paris] [Tokyo] [New York]        │  ← History Tags
└──────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────┐
│  London, GB                                      ☀️  │
│                                                      │
│          ☀️                                          │
│         25°C                                         │  ← Current Weather
│                                                      │
│      Clear Sky                                       │
│                                                      │
│  Feels like: 23°C  |  Humidity: 45%                 │
│  Wind: 5 m/s       |  Pressure: 1013 hPa            │
│  Sunrise: 06:30    |  Sunset: 20:45                 │
└──────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────┐
│  5-Day Forecast                                      │
│                                                      │
│  ┌───────┐  ┌───────┐  ┌───────┐  ┌───────┐  ┌───────┐
│  │  Mon  │  │  Tue  │  │  Wed  │  │  Thu  │  │  Fri  │
│  │  ☀️   │  │  ⛅   │  │  🌧️   │  │  ☁️   │  │  ☀️   │
│  │  24°C │  │  22°C │  │  18°C │  │  20°C │  │  25°C │
│  │  Clear│  │Partly │  │ Rain  │  │Cloudy │  │ Clear │
│  └───────┘  └───────┘  └───────┘  └───────┘  └───────┘
└──────────────────────────────────────────────────────┘
```

---

## 📱 Mobile Layout

```
┌─────────────────┐
│ ☁️ Weather      │  ← Header
└─────────────────┘

┌─────────────────┐
│ [___Search___]  │  ← Search
│ [🔍 Search]     │
│                 │
│ [London][Paris] │  ← History (Wrap)
└─────────────────┘

┌─────────────────┐
│ London, GB  ☀️  │
│                 │
│      ☀️         │
│      25°C       │  ← Current (Full Width)
│                 │
│   Clear Sky     │
│                 │
│ Feels: 23°C     │
│ Humidity: 45%   │
│ Wind: 5 m/s     │
└─────────────────┘

┌─────────────────┐
│ 5-Day Forecast  │
│                 │
│ ┌─────────────┐ │
│ │ Mon    ☀️   │ │
│ │ 24°C  Clear │ │
│ └─────────────┘ │  ← Forecast (Vertical Stack)
│ ┌─────────────┐ │
│ │ Tue    ⛅   │ │
│ │ 22°C Partly │ │
│ └─────────────┘ │
└─────────────────┘
```

---

## 🧩 Component Hierarchy

```mermaid
graph TD
    App[App.jsx] --> Header[Header]
    App --> SearchBar[SearchBar]
    App --> SearchHistory[SearchHistory]
    App --> CurrentWeather[CurrentWeather]
    App --> Forecast[Forecast]
    App --> Loader[Loader]
    App --> ErrorMessage[ErrorMessage]
    
    SearchBar --> Input[Input Field]
    SearchBar --> Button[Search Button]
    
    SearchHistory --> HistoryTag1[Tag]
    SearchHistory --> HistoryTag2[Tag]
    SearchHistory --> HistoryTagN[...]
    
    CurrentWeather --> CityName[City Info]
    CurrentWeather --> WeatherIcon[Icon]
    CurrentWeather --> Temperature[Temp Display]
    CurrentWeather --> WeatherDetails[Details Grid]
    
    Forecast --> ForecastCard1[ForecastCard]
    Forecast --> ForecastCard2[ForecastCard]
    Forecast --> ForecastCard3[ForecastCard]
    Forecast --> ForecastCard4[ForecastCard]
    Forecast --> ForecastCard5[ForecastCard]
    
    ForecastCard1 --> CardDate[Date]
    ForecastCard1 --> CardIcon[Icon]
    ForecastCard1 --> CardTemp[Temperature]
    ForecastCard1 --> CardDesc[Description]
    
    style App fill:#e1f5ff
    style SearchBar fill:#ffe1e1
    style CurrentWeather fill:#e1ffe1
    style Forecast fill:#fff3e1
```

---

## 🔄 User Flow

```mermaid
sequenceDiagram
    participant User
    participant SearchBar
    participant API
    participant WeatherDisplay
    participant LocalStorage
    
    User->>SearchBar: Types "London"
    User->>SearchBar: Clicks Search
    SearchBar->>API: GET /weather?city=London
    SearchBar->>WeatherDisplay: Show Loading
    
    alt Success
        API->>WeatherDisplay: Weather Data
        WeatherDisplay->>User: Display Weather
        WeatherDisplay->>LocalStorage: Save to History
    else Error
        API->>WeatherDisplay: Error
        WeatherDisplay->>User: Show Error Message
    end
    
    User->>SearchBar: Clicks History Tag
    SearchBar->>API: GET /weather?city=Paris
```

---

## 🎨 UI States

### 1. Initial State (No Search)
```
┌──────────────────────────────┐
│  Search for a city:          │
│  [___________________] [🔍]  │
│                              │
│  👋 Welcome to Weather App!  │
│  Search for any city above   │
└──────────────────────────────┘
```

### 2. Loading State
```
┌──────────────────────────────┐
│  Searching...                │
│                              │
│       ⏳ Loading...          │
│       [Spinner Animation]    │
└──────────────────────────────┘
```

### 3. Success State
```
┌──────────────────────────────┐
│  London, GB              ☀️  │
│  25°C - Clear Sky            │
│  [Full weather details]      │
└──────────────────────────────┘
```

### 4. Error State
```
┌──────────────────────────────┐
│  ❌ City not found!          │
│                              │
│  Please try another city     │
│  [Try Again]                 │
└──────────────────────────────┘
```

---

## 🎨 Weather Icons Mapping

```mermaid
graph LR
    A[Weather Code] --> B{Condition}
    
    B -->|Clear| C[☀️]
    B -->|Clouds| D[☁️]
    B -->|Rain| E[🌧️]
    B -->|Snow| F[❄️]
    B -->|Thunderstorm| G[⛈️]
    B -->|Mist/Fog| H[🌫️]
```

---

## 🎯 Key Features Layout

### Search Bar with Validation
```
┌────────────────────────────────┐
│ City name:                     │
│ [___________________] [Search] │  ← Normal
└────────────────────────────────┘

┌────────────────────────────────┐
│ City name:                     │
│ [___________________] [Search] │  ← Focused (Blue border)
└────────────────────────────────┘

┌────────────────────────────────┐
│ City name:                     │
│ [___________________] [Search] │
│ ⚠️ Please enter a city name    │  ← Error
└────────────────────────────────┘
```

### Search History Tags
```
Recent Searches:
[London ×] [Paris ×] [Tokyo ×] [New York ×] [Clear All]

Click tag → Search that city
Click × → Remove from history
```

### Current Weather Card
```
┌─────────────────────────────────────┐
│  London, United Kingdom        ☀️   │
│  ─────────────────────────────────  │
│                                     │
│              ☀️                     │
│             25°C                    │
│          Clear Sky                  │
│                                     │
│  ┌────────────┬────────────────┐   │
│  │ Feels like │    Humidity    │   │
│  │    23°C    │      45%       │   │
│  ├────────────┼────────────────┤   │
│  │    Wind    │   Pressure     │   │
│  │   5 m/s    │   1013 hPa     │   │
│  ├────────────┼────────────────┤   │
│  │  Sunrise   │    Sunset      │   │
│  │   06:30    │     20:45      │   │
│  └────────────┴────────────────┘   │
└─────────────────────────────────────┘
```

### Forecast Card
```
┌──────────────┐
│   Monday     │
│   Jan 22     │
│      ☀️      │
│              │
│   High: 25°C │
│   Low:  18°C │
│              │
│  Clear Sky   │
└──────────────┘

Hover Effect:
- Card lifts
- Shadow increases
- Background color changes
```

---

## 📐 Responsive Breakpoints

```mermaid
graph TD
    A[Screen Size] --> B{Width}
    
    B -->|< 768px| C[Mobile]
    B -->|768-1024px| D[Tablet]
    B -->|> 1024px| E[Desktop]
    
    C --> C1[Vertical Stack]
    C --> C2[1 Forecast Card Width]
    
    D --> D1[2 Column Grid]
    D --> D2[2-3 Forecast Cards]
    
    E --> E1[Side by Side]
    E --> E2[5 Forecast Cards in Row]
```

---

## 🎨 Color Scheme

### Light Mode
```
Primary:     #3B82F6 (Blue)
Secondary:   #10B981 (Green)
Background:  #F3F4F6 (Light Gray)
Card:        #FFFFFF (White)
Text:        #1F2937 (Dark)
Border:      #E5E7EB (Light Gray)
Error:       #EF4444 (Red)
Success:     #10B981 (Green)
```

### Dark Mode (Optional)
```
Primary:     #60A5FA (Light Blue)
Background:  #1F2937 (Dark Gray)
Card:        #374151 (Medium Gray)
Text:        #F9FAFB (White)
Border:      #4B5563 (Gray)
```

---

## 🎬 Animations

1. **Search Button**: Pulse on click
2. **Loading**: Spinner rotation
3. **Weather Card**: Fade in from bottom
4. **Forecast Cards**: Stagger fade in (delay each)
5. **History Tags**: Slide in from right
6. **Error Message**: Shake animation
7. **Icon**: Bounce on load

---

## 📊 Data Display

### Temperature
```
Large: 25°C  (Main temperature)
Small: 18°C  (Feels like, min/max)
```

### Details Grid
```
┌────────────┬────────────┐
│ Label      │ Label      │
│ VALUE      │ VALUE      │
├────────────┼────────────┤
│ Label      │ Label      │
│ VALUE      │ VALUE      │
└────────────┴────────────┘
```

---

## ✅ UI Checklist

- [ ] Header with app name and icon
- [ ] Search input with placeholder
- [ ] Search button with icon
- [ ] Search history tags (max 5)
- [ ] Loading spinner during API call
- [ ] Current weather card
- [ ] Weather icon display
- [ ] Temperature (large font)
- [ ] Weather description
- [ ] Details grid (humidity, wind, etc.)
- [ ] 5-day forecast cards
- [ ] Error message component
- [ ] Empty state message
- [ ] Responsive design
- [ ] Hover effects on cards

---

## 📝 Notes

- Use Bootstrap classes for quick styling
- Weather icons can be from API or React Icons
- LocalStorage saves last 5 searches
- API calls should show loading state
- Handle all error cases gracefully
- Make temperature units clear (°C or °F)
- Consider adding unit toggle (optional)

---

**Use this mockup as your reference while building the weather dashboard!** 🌦️

