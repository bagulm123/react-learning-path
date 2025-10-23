# 🎬 Assignment 5: Movie Database Explorer - UI Mockup

Visual guide for building your advanced movie explorer with Tailwind CSS and animations.

---

## 📱 Desktop Layout

```mermaid
graph TD
    A[Movie Explorer] --> B[Navbar]
    A --> C[Home Page]
    A --> D[Search Page]
    A --> E[Movie Details Page]
    A --> F[Favorites Page]
    
    B --> B1[Logo]
    B --> B2[Search Bar]
    B --> B3[Nav Links]
    B --> B4[Theme Toggle]
    
    C --> C1[Trending Section]
    C --> C2[Popular Section]
    C --> C3[Top Rated Section]
    C --> C4[Upcoming Section]
    
    D --> D1[Search Results Grid]
    D --> D2[Filters]
    D --> D3[Infinite Scroll]
    
    E --> E1[Backdrop Image]
    E --> E2[Movie Info]
    E --> E3[Cast Section]
    E --> E4[Videos Section]
    E --> E5[Similar Movies]
    
    F --> F1[Favorites Grid]
```

---

## 🎨 Home Page Layout

```
┌──────────────────────────────────────────────────────────────┐
│  🎬 MovieDB    [Search movies...]   Home Favorites Profile   │  ← Navbar
└──────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────┐
│  Trending This Week                              [See All →] │
│                                                              │
│  ◄ [🎬] [🎬] [🎬] [🎬] [🎬] [🎬] [🎬] [🎬] ►              │  ← Horizontal Scroll
│                                                              │
└──────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────┐
│  Popular Movies                                   [See All →]│
│                                                              │
│  ┌────────┐  ┌────────┐  ┌────────┐  ┌────────┐  ┌────────┐│
│  │  📷    │  │  📷    │  │  📷    │  │  📷    │  │  📷    ││
│  │ Poster │  │ Poster │  │ Poster │  │ Poster │  │ Poster ││
│  │        │  │        │  │        │  │        │  │        ││
│  │ Title  │  │ Title  │  │ Title  │  │ Title  │  │ Title  ││
│  │⭐ 8.5  │  │⭐ 7.9  │  │⭐ 8.2  │  │⭐ 7.5  │  │⭐ 8.8  ││
│  │ ❤️     │  │ ❤️     │  │ ❤️     │  │ ❤️     │  │ ❤️     ││
│  └────────┘  └────────┘  └────────┘  └────────┘  └────────┘│
│                                                              │
│  ┌────────┐  ┌────────┐  ┌────────┐  ┌────────┐  ┌────────┐│
│  │  📷    │  │  📷    │  │  📷    │  │  📷    │  │  📷    ││
│  └────────┘  └────────┘  └────────┘  └────────┘  └────────┘│
└──────────────────────────────────────────────────────────────┘

[Load More...]  ← Infinite Scroll Trigger

┌──────────────────────────────────────────────────────────────┐
│  Top Rated                                        [See All →]│
│  [Similar grid of movie posters]                             │
└──────────────────────────────────────────────────────────────┘
```

---

## 🔍 Search Results Page

```
┌──────────────────────────────────────────────────────────────┐
│  🎬 MovieDB  [avengers____________]  🔍                      │
└──────────────────────────────────────────────────────────────┘

┌───────────┬──────────────────────────────────────────────────┐
│ Filters   │  Search Results for "avengers" (124 movies)     │
│           │                                                   │
│ Genre     │  ┌────────┐  ┌────────┐  ┌────────┐  ┌────────┐│
│ □ Action  │  │  📷    │  │  📷    │  │  📷    │  │  📷    ││
│ □ Drama   │  │ Poster │  │ Poster │  │ Poster │  │ Poster ││
│ □ Comedy  │  │ Title  │  │ Title  │  │ Title  │  │ Title  ││
│           │  │⭐ 8.5  │  │⭐ 7.9  │  │⭐ 8.2  │  │⭐ 7.5  ││
│ Year      │  │ ❤️     │  │ ❤️     │  │ ❤️     │  │ ❤️     ││
│ ━●━━━━━━  │  └────────┘  └────────┘  └────────┘  └────────┘│
│2000  2024 │                                                   │
│           │  ┌────────┐  ┌────────┐  ┌────────┐  ┌────────┐│
│ Rating    │  │  📷    │  │  📷    │  │  📷    │  │  📷    ││
│⭐ 7.0+    │  └────────┘  └────────┘  └────────┘  └────────┘│
│           │                                                   │
│ Sort      │  [Loading more...]                               │
│ ● Popular │                                                   │
│ ○ Latest  │                                                   │
│ ○ Rating  │                                                   │
└───────────┴──────────────────────────────────────────────────┘
```

---

## 🎬 Movie Details Page

```
┌──────────────────────────────────────────────────────────────┐
│                                                              │
│              ═══════════════════════════                     │
│              ║   BACKDROP IMAGE      ║                     │  ← Large backdrop
│              ║   (Gradient overlay)   ║                     │
│              ═══════════════════════════                     │
│                                                              │
└──────────────────────────────────────────────────────────────┘

┌─────────────┬────────────────────────────────────────────────┐
│             │  The Avengers                            ❤️    │
│   ┌─────┐   │  Action, Adventure, Sci-Fi               Fav  │
│   │     │   │  ⭐ 8.0 (1.2M reviews)                        │
│   │Post │   │  2h 23min  •  2012  •  PG-13                 │
│   │ er  │   │                                               │
│   │     │   │  "Earth's mightiest heroes must come         │
│   │Imag │   │   together to stop Loki..."                  │
│   │ e   │   │                                               │
│   │     │   │  [▶️ Watch Trailer]  [🔗 Share]              │
│   └─────┘   │                                               │
└─────────────┴────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────┐
│  Cast                                                        │
│  ◄ [👤] [👤] [👤] [👤] [👤] [👤] [👤] [👤] ►              │  ← Horizontal scroll
│     Name    Name    Name    Name                            │
│   Character Character Character                             │
└──────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────┐
│  Videos & Trailers                                           │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐         │
│  │  ▶️         │  │  ▶️         │  │  ▶️         │         │
│  │  Trailer 1  │  │  Trailer 2  │  │  Behind...  │         │
│  └─────────────┘  └─────────────┘  └─────────────┘         │
└──────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────┐
│  Similar Movies                                              │
│  [Grid of similar movie posters]                            │
└──────────────────────────────────────────────────────────────┘
```

---

## 🧩 Component Hierarchy

```mermaid
graph TD
    App[App.tsx] --> Router[React Router]
    Router --> HomePage[HomePage]
    Router --> SearchPage[SearchPage]
    Router --> DetailsPage[MovieDetailsPage]
    Router --> FavoritesPage[FavoritesPage]
    
    HomePage --> Navbar[Navbar]
    HomePage --> Hero[Hero Section]
    HomePage --> MovieRow1[MovieRow: Trending]
    HomePage --> MovieRow2[MovieRow: Popular]
    HomePage --> MovieRow3[MovieRow: Top Rated]
    
    Navbar --> Logo[Logo]
    Navbar --> SearchBar[SearchBar with Debounce]
    Navbar --> NavLinks[Navigation Links]
    
    MovieRow1 --> MovieCard1[MovieCard]
    MovieRow1 --> MovieCard2[MovieCard]
    MovieRow1 --> MovieCardN[...]
    
    MovieCard1 --> LazyImage[LazyImage]
    MovieCard1 --> CardInfo[Title, Rating]
    MovieCard1 --> FavoriteBtn[Favorite Button]
    
    SearchPage --> Filters[FilterSidebar]
    SearchPage --> SearchGrid[MovieGrid]
    SearchPage --> InfiniteScroll[InfiniteScrollTrigger]
    
    DetailsPage --> Backdrop[BackdropImage]
    DetailsPage --> MovieInfo[MovieInfo]
    DetailsPage --> CastSection[CastCarousel]
    DetailsPage --> VideosSection[VideosSection]
    DetailsPage --> SimilarMovies[SimilarMovies]
    
    style App fill:#e1f5ff
    style Navbar fill:#ffe1e1
    style MovieRow1 fill:#e1ffe1
    style DetailsPage fill:#fff3e1
```

---

## 🎯 Movie Card States

### Normal State
```
┌──────────┐
│          │
│  🎬      │
│  Image   │
│          │
├──────────┤
│ Title    │
│ ⭐ 8.5   │
│ ❤️       │
└──────────┘
```

### Hover State (with Framer Motion)
```
┌──────────┐  ← Scale up (1.05)
│   ✨     │  ← Glow effect
│  🎬      │  ← Image zoom in
│  Image   │  ← Overlay appears
│  ▶️      │  ← Play icon appears
├──────────┤
│ Title    │  ← Text color change
│ ⭐ 8.5   │
│ 💗       │  ← Heart filled
└──────────┘
```

### Loading State (Skeleton)
```
┌──────────┐
│ ▒▒▒▒▒▒▒▒ │  ← Shimmer animation
│ ▒▒▒▒▒▒▒▒ │
│ ▒▒▒▒▒▒▒▒ │
│ ▒▒▒▒▒▒▒▒ │
├──────────┤
│ ▒▒▒▒     │
│ ▒▒▒      │
└──────────┘
```

---

## 📱 Mobile Layout

```
┌────────────────┐
│ 🎬  [Search] ☰ │  ← Mobile Navbar
└────────────────┘

┌────────────────┐
│  Trending      │
│  ◄ [🎬][🎬] ► │  ← Horizontal scroll
└────────────────┘

┌────────────────┐
│  Popular       │
│  ┌──────────┐  │
│  │   🎬     │  │
│  │  Poster  │  │  ← 2-3 columns
│  │  Title   │  │
│  │  ⭐ 8.5  │  │
│  └──────────┘  │
│  ┌──────────┐  │
│  │   🎬     │  │
│  └──────────┘  │
└────────────────┘

[Infinite Scroll...]
```

---

## 🔍 Search with Debouncing

```mermaid
sequenceDiagram
    participant User
    participant SearchBar
    participant Debounce
    participant API
    participant Results
    
    User->>SearchBar: Types "ave"
    SearchBar->>Debounce: Start timer
    User->>SearchBar: Types "avengers"
    Debounce->>Debounce: Reset timer
    Note over Debounce: Wait 500ms
    Debounce->>API: Search "avengers"
    API->>Results: Return movies
    Results->>User: Display results
```

---

## ∞ Infinite Scroll Implementation

```mermaid
graph TD
    A[User Scrolls] --> B{Near Bottom?}
    B -->|Yes| C[Trigger Load More]
    B -->|No| A
    C --> D[Fetch Next Page]
    D --> E[Append to Results]
    E --> F[Update Page Number]
    F --> A
```

---

## 🎬 Animations with Framer Motion

### Page Transition
```jsx
// Fade in on page load
initial={{ opacity: 0 }}
animate={{ opacity: 1 }}
exit={{ opacity: 0 }}
transition={{ duration: 0.3 }}
```

### Movie Card Hover
```jsx
// Scale and lift
whileHover={{ 
  scale: 1.05,
  y: -10,
  transition: { duration: 0.2 }
}}
```

### Stagger Children
```jsx
// Cards appear one by one
variants={{
  hidden: { opacity: 0 },
  show: {
    opacity: 1,
    transition: {
      staggerChildren: 0.1
    }
  }
}}
```

---

## 🎨 Tailwind CSS Classes Examples

### Movie Card
```jsx
<div className="relative rounded-lg overflow-hidden shadow-lg 
                hover:shadow-2xl transform hover:scale-105 
                transition-all duration-300 cursor-pointer
                bg-gray-800">
  {/* Card content */}
</div>
```

### Search Bar
```jsx
<input className="w-full px-4 py-2 rounded-full 
                  bg-gray-800 text-white 
                  focus:outline-none focus:ring-2 
                  focus:ring-blue-500 transition-all" />
```

### Rating Badge
```jsx
<span className="absolute top-2 right-2 
                 bg-yellow-400 text-black 
                 px-2 py-1 rounded-full text-sm font-bold">
  ⭐ 8.5
</span>
```

---

## ✅ UI Checklist

- [ ] Navbar with search
- [ ] Debounced search input
- [ ] Home page with sections
- [ ] Horizontal scrolling rows
- [ ] Movie cards with lazy images
- [ ] Loading skeletons
- [ ] Hover animations (Framer Motion)
- [ ] Favorite button with animation
- [ ] Search page with filters
- [ ] Infinite scroll
- [ ] Movie details page
- [ ] Backdrop image with gradient
- [ ] Cast carousel (horizontal scroll)
- [ ] Video thumbnails
- [ ] Similar movies section
- [ ] Favorites page
- [ ] Empty states
- [ ] Page transitions
- [ ] Responsive design
- [ ] Dark theme

---

## 🎨 Color Scheme (Dark Theme)

```
Background: #0F172A (Dark Blue-Gray)
Surface:    #1E293B (Lighter Blue-Gray)
Card:       #334155 (Card Background)
Primary:    #3B82F6 (Blue)
Secondary:  #8B5CF6 (Purple)
Accent:     #F59E0B (Orange)
Text:       #F1F5F9 (Light Gray)
Muted:      #64748B (Gray)
Rating:     #FBBF24 (Gold)
```

---

## 🎬 Key Features Layout

### Horizontal Movie Row
```
Trending This Week                    [See All →]

◄ ┌─────┐ ┌─────┐ ┌─────┐ ┌─────┐ ┌─────┐ ►
  │ 🎬  │ │ 🎬  │ │ 🎬  │ │ 🎬  │ │ 🎬  │
  │Title│ │Title│ │Title│ │Title│ │Title│
  │⭐8.5│ │⭐7.9│ │⭐8.2│ │⭐7.5│ │⭐8.8│
  └─────┘ └─────┘ └─────┘ └─────┘ └─────┘
  
← Drag to scroll or use arrows →
```

### Cast Member Card
```
┌──────────┐
│  👤      │  ← Profile photo
│  Photo   │
├──────────┤
│ Actor    │  ← Name
│ Name     │
├──────────┤
│Character │  ← Character name
│Name      │
└──────────┘
```

---

## 📊 Performance Optimizations

1. **Image Lazy Loading**
   - Load images only when in viewport
   - Use placeholder while loading

2. **Debounced Search**
   - Wait 500ms after typing stops
   - Prevent excessive API calls

3. **Infinite Scroll**
   - Load 20 movies at a time
   - Pagination with TMDB API

4. **React.memo**
   - Memoize movie cards
   - Prevent unnecessary re-renders

5. **Virtual Scrolling** (Optional)
   - Only render visible items
   - Better performance with many items

---

## 📝 Notes

- Use TMDB API for movie data
- Images from TMDB image CDN
- Tailwind for styling (utility-first)
- Framer Motion for animations
- Intersection Observer for lazy loading
- LocalStorage for favorites
- React Router for navigation
- Responsive breakpoints: sm, md, lg, xl

---

**Build a stunning movie explorer with smooth animations!** 🎬

