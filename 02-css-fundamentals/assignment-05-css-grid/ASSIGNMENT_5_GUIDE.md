# Assignment 5: CSS Grid - Two-Dimensional Layouts

**By Mahendra Bagul**

If Flexbox is one-dimensional (row OR column), CSS Grid is two-dimensional (rows AND columns simultaneously). It's a game-changer for complex layouts!

Grid makes things possible that were painful or impossible before. Let's master it! 🎨

---

## 📚 What You'll Learn

- ✅ Grid container and items
- ✅ `grid-template-columns` and `grid-template-rows`
- ✅ `grid-gap` (or `gap`)
- ✅ Grid lines and track sizing
- ✅ `grid-template-areas` for named layouts
- ✅ `grid-column` and `grid-row` for item placement
- ✅ `repeat()` and `fr` units
- ✅ `minmax()` for responsive grids
- ✅ Auto-placement algorithm
- ✅ Creating dashboard layouts

---

## 🎯 Assignment Objectives

Create a "Dashboard Layout" using CSS Grid - header, sidebar, main content, widgets, and footer.

**Difficulty**: ⭐⭐⭐⭐☆  
**Time**: 4-5 hours  
**Prerequisites**: CSS Assignments 1-4

---

## 📋 Requirements

### Must Have
1. ✅ Dashboard with grid layout
2. ✅ Header spanning full width
3. ✅ Sidebar with navigation
4. ✅ Main content area
5. ✅ At least 6 widget cards
6. ✅ Footer spanning full width
7. ✅ Use of `grid-template-areas`
8. ✅ Use of `fr` units
9. ✅ Responsive grid with media queries
10. ✅ Gap between grid items

---

## 📐 CSS Grid Fundamentals

### Basic Grid
```css
.container {
    display: grid;
    
    /* Define columns */
    grid-template-columns: 200px 1fr 200px;  /* 3 columns */
    
    /* Define rows */
    grid-template-rows: 100px 1fr 80px;  /* 3 rows */
    
    /* Gap between items */
    gap: 20px;
    /* Or separately: */
    row-gap: 20px;
    column-gap: 10px;
}
```

### Grid Units

**Fixed**: `px`, `em`, `rem`
```css
grid-template-columns: 200px 400px 200px;
```

**Fractional (fr)** - Distributes available space
```css
grid-template-columns: 1fr 2fr 1fr;  /* Second column is 2x wider */
```

**Repeat**
```css
grid-template-columns: repeat(3, 1fr);  /* 3 equal columns */
grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));  /* Responsive! */
```

### Template Areas (Named Layout)
```css
.container {
    display: grid;
    grid-template-areas:
        "header header header"
        "sidebar main main"
        "footer footer footer";
    grid-template-columns: 200px 1fr 1fr;
    grid-template-rows: auto 1fr auto;
}

.header { grid-area: header; }
.sidebar { grid-area: sidebar; }
.main { grid-area: main; }
.footer { grid-area: footer; }
```

### Item Placement
```css
.item {
    /* Span columns */
    grid-column: 1 / 3;  /* From line 1 to line 3 */
    grid-column: span 2;  /* Span 2 columns */
    
    /* Span rows */
    grid-row: 1 / 4;
    grid-row: span 2;
}
```

---

## 💻 Complete Implementation

### HTML
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dashboard - CSS Grid</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="dashboard">
        <!-- Header -->
        <header class="header">
            <h1>Analytics Dashboard</h1>
            <div class="header-actions">
                <button>Profile</button>
                <button>Settings</button>
            </div>
        </header>
        
        <!-- Sidebar -->
        <aside class="sidebar">
            <nav class="sidebar-nav">
                <a href="#" class="nav-item active">📊 Dashboard</a>
                <a href="#" class="nav-item">📈 Analytics</a>
                <a href="#" class="nav-item">👥 Users</a>
                <a href="#" class="nav-item">📦 Products</a>
                <a href="#" class="nav-item">⚙️ Settings</a>
            </nav>
        </aside>
        
        <!-- Main Content -->
        <main class="main-content">
            <section class="stats-grid">
                <div class="stat-card">
                    <div class="stat-icon">👥</div>
                    <div class="stat-info">
                        <h3>Total Users</h3>
                        <p class="stat-number">12,543</p>
                        <span class="stat-change positive">+12.5%</span>
                    </div>
                </div>
                
                <div class="stat-card">
                    <div class="stat-icon">💰</div>
                    <div class="stat-info">
                        <h3>Revenue</h3>
                        <p class="stat-number">$45,678</p>
                        <span class="stat-change positive">+8.2%</span>
                    </div>
                </div>
                
                <div class="stat-card">
                    <div class="stat-icon">📦</div>
                    <div class="stat-info">
                        <h3>Orders</h3>
                        <p class="stat-number">3,241</p>
                        <span class="stat-change negative">-3.1%</span>
                    </div>
                </div>
                
                <div class="stat-card">
                    <div class="stat-icon">⭐</div>
                    <div class="stat-info">
                        <h3>Rating</h3>
                        <p class="stat-number">4.8</p>
                        <span class="stat-change positive">+0.3</span>
                    </div>
                </div>
            </section>
            
            <section class="charts-grid">
                <div class="chart-card large">
                    <h3>Sales Overview</h3>
                    <div class="chart-placeholder">
                        <p>📈 Line Chart Here</p>
                    </div>
                </div>
                
                <div class="chart-card">
                    <h3>Traffic Sources</h3>
                    <div class="chart-placeholder">
                        <p>🥧 Pie Chart Here</p>
                    </div>
                </div>
                
                <div class="chart-card">
                    <h3>Recent Activity</h3>
                    <ul class="activity-list">
                        <li>New user registered</li>
                        <li>Order #1234 completed</li>
                        <li>Product added</li>
                        <li>Payment received</li>
                    </ul>
                </div>
                
                <div class="chart-card">
                    <h3>Top Products</h3>
                    <ol class="product-list">
                        <li>Product A - $1,234</li>
                        <li>Product B - $987</li>
                        <li>Product C - $765</li>
                        <li>Product D - $543</li>
                    </ol>
                </div>
            </section>
        </main>
        
        <!-- Footer -->
        <footer class="footer">
            <p>&copy; 2025 Dashboard App. All rights reserved.</p>
            <div class="footer-links">
                <a href="#">Privacy</a>
                <a href="#">Terms</a>
                <a href="#">Support</a>
            </div>
        </footer>
    </div>
</body>
</html>
```

### CSS (styles.css)
```css
/* ===== RESET ===== */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-color: #f5f7fa;
    color: #2c3e50;
}

/* ===== MAIN DASHBOARD GRID ===== */
.dashboard {
    display: grid;
    grid-template-areas:
        "header header"
        "sidebar main"
        "footer footer";
    grid-template-columns: 250px 1fr;
    grid-template-rows: auto 1fr auto;
    min-height: 100vh;
    gap: 0;
}

/* ===== HEADER ===== */
.header {
    grid-area: header;
    background-color: #2c3e50;
    color: white;
    padding: 1.5rem 2rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

.header h1 {
    font-size: 1.5rem;
}

.header-actions {
    display: flex;
    gap: 1rem;
}

.header-actions button {
    padding: 0.5rem 1rem;
    background-color: #34495e;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s;
}

.header-actions button:hover {
    background-color: #3498db;
}

/* ===== SIDEBAR ===== */
.sidebar {
    grid-area: sidebar;
    background-color: #34495e;
    padding: 2rem 0;
}

.sidebar-nav {
    display: flex;
    flex-direction: column;
}

.nav-item {
    padding: 1rem 2rem;
    color: #bdc3c7;
    text-decoration: none;
    transition: all 0.3s;
    border-left: 4px solid transparent;
}

.nav-item:hover,
.nav-item.active {
    background-color: #2c3e50;
    color: white;
    border-left-color: #3498db;
}

/* ===== MAIN CONTENT ===== */
.main-content {
    grid-area: main;
    padding: 2rem;
    overflow-y: auto;
}

/* ===== STATS GRID ===== */
.stats-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
    gap: 1.5rem;
    margin-bottom: 2rem;
}

.stat-card {
    background-color: white;
    padding: 1.5rem;
    border-radius: 10px;
    box-shadow: 0 2px 10px rgba(0,0,0,0.08);
    display: flex;
    gap: 1rem;
    align-items: center;
    transition: transform 0.3s, box-shadow 0.3s;
}

.stat-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 4px 20px rgba(0,0,0,0.12);
}

.stat-icon {
    font-size: 2.5rem;
    width: 60px;
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: #e8f4f8;
    border-radius: 10px;
}

.stat-info h3 {
    font-size: 0.9rem;
    color: #7f8c8d;
    font-weight: normal;
    margin-bottom: 0.5rem;
}

.stat-number {
    font-size: 2rem;
    font-weight: bold;
    color: #2c3e50;
    margin-bottom: 0.5rem;
}

.stat-change {
    font-size: 0.85rem;
    font-weight: 600;
}

.stat-change.positive {
    color: #27ae60;
}

.stat-change.negative {
    color: #e74c3c;
}

/* ===== CHARTS GRID ===== */
.charts-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 1.5rem;
}

.chart-card {
    background-color: white;
    padding: 1.5rem;
    border-radius: 10px;
    box-shadow: 0 2px 10px rgba(0,0,0,0.08);
}

.chart-card h3 {
    margin-bottom: 1rem;
    color: #2c3e50;
    font-size: 1.1rem;
}

.chart-card.large {
    grid-column: span 2;
}

.chart-placeholder {
    height: 200px;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    font-size: 1.2rem;
}

.activity-list,
.product-list {
    list-style: none;
}

.activity-list li,
.product-list li {
    padding: 0.75rem 0;
    border-bottom: 1px solid #ecf0f1;
}

.activity-list li:last-child,
.product-list li:last-child {
    border-bottom: none;
}

/* ===== FOOTER ===== */
.footer {
    grid-area: footer;
    background-color: #2c3e50;
    color: #bdc3c7;
    padding: 1.5rem 2rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.footer-links {
    display: flex;
    gap: 1.5rem;
}

.footer-links a {
    color: #bdc3c7;
    text-decoration: none;
    transition: color 0.3s;
}

.footer-links a:hover {
    color: #3498db;
}

/* ===== RESPONSIVE ===== */
@media (max-width: 1024px) {
    .dashboard {
        grid-template-areas:
            "header"
            "sidebar"
            "main"
            "footer";
        grid-template-columns: 1fr;
        grid-template-rows: auto auto 1fr auto;
    }
    
    .sidebar {
        padding: 1rem 0;
    }
    
    .sidebar-nav {
        flex-direction: row;
        overflow-x: auto;
    }
    
    .nav-item {
        white-space: nowrap;
        border-left: none;
        border-bottom: 4px solid transparent;
    }
    
    .nav-item:hover,
    .nav-item.active {
        border-left-color: transparent;
        border-bottom-color: #3498db;
    }
    
    .chart-card.large {
        grid-column: span 1;
    }
}

@media (max-width: 768px) {
    .header {
        flex-direction: column;
        gap: 1rem;
        text-align: center;
    }
    
    .stats-grid {
        grid-template-columns: 1fr;
    }
    
    .charts-grid {
        grid-template-columns: 1fr;
    }
    
    .footer {
        flex-direction: column;
        gap: 1rem;
        text-align: center;
    }
}
```

---

## 📖 Grid Concepts Explained

### Fr Units (Fractional)
- `1fr` = 1 fraction of available space
- `2fr` = twice as much space
```css
grid-template-columns: 1fr 2fr 1fr;
/* Left: 25%, Center: 50%, Right: 25% */
```

### Repeat Function
```css
grid-template-columns: repeat(3, 1fr);
/* Same as: 1fr 1fr 1fr */

grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
/* Responsive: As many 200px+ columns as fit */
```

### Template Areas (Semantic)
```css
grid-template-areas:
    "header header header"
    "sidebar main main"
    "footer footer footer";
```
- Each string is a row
- Each word is a cell
- Same word = spans multiple cells
- `.` = empty cell

### Auto-Placement
Grid automatically places items if you don't specify position!

---

## ✅ Self-Assessment

- [ ] Dashboard uses CSS Grid
- [ ] Header spans full width
- [ ] Sidebar navigation works
- [ ] Main content area displays stats
- [ ] At least 6 widget cards
- [ ] Footer spans full width
- [ ] Used grid-template-areas
- [ ] Used fr units
- [ ] Responsive on mobile
- [ ] Gap between grid items

---

## 💡 Grid vs Flexbox

**Use Grid when:**
- Two-dimensional layout (rows AND columns)
- Fixed layout structure (dashboard, magazine layout)
- Need precise control over rows and columns

**Use Flexbox when:**
- One-dimensional layout (row OR column)
- Content size determines layout
- Navigation bars, cards in a row

**Often**: Use both together! Grid for page layout, Flexbox for components.

---

**Next**: [Assignment 6: Responsive Design](../assignment-06-responsive-design/ASSIGNMENT_6_GUIDE.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

