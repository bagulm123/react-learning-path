# 🛒 Assignment 4: E-Commerce Product Catalog - UI Mockup

Visual guide for building your Redux-powered e-commerce application.

---

## 📱 Desktop Layout

```mermaid
graph TD
    A[E-Commerce App] --> B[Navbar]
    A --> C[Sidebar Filters]
    A --> D[Product Grid]
    A --> E[Cart Drawer]
    A --> F[Product Details Page]
    
    B --> B1[Logo]
    B --> B2[Search Bar]
    B --> B3[Cart Icon + Badge]
    B --> B4[Categories]
    
    C --> C1[Category Filter]
    C --> C2[Price Range Slider]
    C --> C3[Rating Filter]
    C --> C4[Clear Filters]
    
    D --> D1[Product Card 1]
    D --> D2[Product Card 2]
    D --> D3[Product Card N]
    
    E --> E1[Cart Items List]
    E --> E2[Totals]
    E --> E3[Checkout Button]
    
    F --> F1[Product Image Gallery]
    F --> F2[Product Info]
    F --> F3[Add to Cart]
    F --> F4[Product Details]
```

---

## 🎨 Main Page Layout

```
┌──────────────────────────────────────────────────────────────┐
│  [LOGO]  [Search products...]  [🛒 Cart (3)]                 │  ← Navbar
│  Electronics  Fashion  Home  Books  Sports                    │
└──────────────────────────────────────────────────────────────┘

┌───────────┬──────────────────────────────────────────────────┐
│ Filters   │  Products (24)                     [Sort by ▼]   │
│           │                                                   │
│ Category  │  ┌────────┐  ┌────────┐  ┌────────┐  ┌────────┐│
│ ○ All     │  │  📷    │  │  📷    │  │  📷    │  │  📷    ││
│ ○ Elect.. │  │ $99.99 │  │ $149   │  │ $79.99 │  │ $199   ││
│ ○ Fashion │  │ Title  │  │ Title  │  │ Title  │  │ Title  ││
│ ○ Home    │  │ ⭐⭐⭐⭐ │  │ ⭐⭐⭐⭐⭐│  │ ⭐⭐⭐   │  │ ⭐⭐⭐⭐ ││
│           │  │ [Cart] │  │ [Cart] │  │ [Cart] │  │ [Cart] ││
│ Price     │  └────────┘  └────────┘  └────────┘  └────────┘│
│ [$___$__] │                                                   │
│           │  ┌────────┐  ┌────────┐  ┌────────┐  ┌────────┐│
│ Rating    │  │  📷    │  │  📷    │  │  📷    │  │  📷    ││
│ ⭐⭐⭐⭐⭐   │  │ $89.99 │  │ $129   │  │ $69.99 │  │ $299   ││
│ ⭐⭐⭐⭐     │  └────────┘  └────────┘  └────────┘  └────────┘│
│ ⭐⭐⭐       │                                                   │
│           │  [Load More...]                                   │
│ [Clear]   │                                                   │
└───────────┴──────────────────────────────────────────────────┘
```

---

## 🛒 Cart Drawer (Slide-in from Right)

```
                    ┌────────────────────────────┐
                    │  Shopping Cart        [×]  │
                    ├────────────────────────────┤
                    │                            │
                    │  ┌────┐ Product Name       │
                    │  │ 📷 │ $99.99             │
                    │  └────┘ [- 1 +]      [🗑️] │
                    │                            │
                    │  ┌────┐ Product Name       │
                    │  │ 📷 │ $149.00            │
                    │  └────┘ [- 2 +]      [🗑️] │
                    │                            │
                    │  ┌────┐ Product Name       │
                    │  │ 📷 │ $79.99             │
                    │  └────┘ [- 1 +]      [🗑️] │
                    │                            │
                    ├────────────────────────────┤
                    │  Subtotal:        $328.98  │
                    │  Tax (10%):        $32.90  │
                    │  ─────────────────────────  │
                    │  Total:           $361.88  │
                    │                            │
                    │  [Proceed to Checkout]     │
                    │  [Continue Shopping]       │
                    └────────────────────────────┘
```

---

## 📦 Product Details Page

```
┌──────────────────────────────────────────────────────────────┐
│  ← Back to Products                                          │
└──────────────────────────────────────────────────────────────┘

┌─────────────────────────┬────────────────────────────────────┐
│                         │  Wireless Headphones               │
│      ┌─────────┐        │  $149.99                          │
│      │         │        │  ⭐⭐⭐⭐⭐ (245 reviews)            │
│      │  Main   │        │                                    │
│      │  Image  │        │  Premium wireless headphones with  │
│      │         │        │  noise cancellation and 30-hour    │
│      └─────────┘        │  battery life.                     │
│                         │                                    │
│  [📷] [📷] [📷] [📷]   │  Color: [⚫] [⚪] [🔴]             │
│                         │                                    │
│                         │  Quantity: [- 1 +]                 │
│                         │                                    │
│                         │  [🛒 Add to Cart]                  │
│                         │  [❤️ Add to Wishlist]              │
│                         │                                    │
├─────────────────────────┴────────────────────────────────────┤
│                                                              │
│  Product Details                                             │
│  • Bluetooth 5.0                                             │
│  • 30-hour battery life                                      │
│  • Active noise cancellation                                 │
│  • Foldable design                                           │
│                                                              │
│  Specifications                                              │
│  Brand: AudioPro | Weight: 250g | Color: Black              │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## 🧩 Component Hierarchy

```mermaid
graph TD
    App[App.tsx] --> Router[React Router]
    Router --> HomePage[HomePage]
    Router --> ProductPage[ProductDetailsPage]
    
    HomePage --> Navbar[Navbar]
    HomePage --> MainLayout[MainLayout]
    
    Navbar --> Logo[Logo]
    Navbar --> SearchBar[SearchBar]
    Navbar --> CartIcon[CartIcon + Badge]
    Navbar --> Categories[CategoryLinks]
    
    MainLayout --> Sidebar[FilterSidebar]
    MainLayout --> ProductArea[ProductArea]
    
    Sidebar --> CategoryFilter[CategoryFilter]
    Sidebar --> PriceFilter[PriceRangeSlider]
    Sidebar --> RatingFilter[RatingFilter]
    Sidebar --> ClearButton[Clear Filters]
    
    ProductArea --> SortBar[SortBar]
    ProductArea --> ProductGrid[ProductGrid]
    ProductArea --> Pagination[Pagination]
    
    ProductGrid --> ProductCard1[ProductCard]
    ProductGrid --> ProductCard2[ProductCard]
    ProductGrid --> ProductCardN[...]
    
    ProductCard1 --> CardImage[Image]
    ProductCard1 --> CardTitle[Title]
    ProductCard1 --> CardPrice[Price]
    ProductCard1 --> CardRating[Rating]
    ProductCard1 --> AddToCartBtn[Add to Cart]
    
    App --> CartDrawer[CartDrawer]
    CartDrawer --> CartItem1[CartItem]
    CartDrawer --> CartItem2[CartItem]
    CartDrawer --> CartSummary[CartSummary]
    
    ProductPage --> ProductGallery[ImageGallery]
    ProductPage --> ProductInfo[ProductInfo]
    ProductPage --> ProductActions[AddToCart Actions]
    ProductPage --> ProductDetails[Details Tabs]
    
    style App fill:#e1f5ff
    style Navbar fill:#ffe1e1
    style ProductGrid fill:#e1ffe1
    style CartDrawer fill:#fff3e1
```

---

## 🔄 Redux State Flow

```mermaid
sequenceDiagram
    participant User
    participant Component
    participant Redux
    participant API
    participant LocalStorage
    
    User->>Component: Clicks "Add to Cart"
    Component->>Redux: dispatch(addToCart(product))
    Redux->>Redux: Update cart state
    Redux->>LocalStorage: Persist cart
    Redux->>Component: Updated state
    Component->>User: Show cart badge update
    Component->>User: Show success notification
    
    User->>Component: Opens cart
    Component->>Redux: select cart items
    Redux->>Component: Return cart data
    Component->>User: Display cart items
```

---

## 🎨 Product Card States

### Normal State
```
┌──────────────┐
│   ┌──────┐   │
│   │ 📷   │   │
│   │Image │   │
│   └──────┘   │
│              │
│ Product Name │
│ $99.99       │
│ ⭐⭐⭐⭐      │
│              │
│ [Add to Cart]│
└──────────────┘
```

### Hover State
```
┌──────────────┐  ← Elevated shadow
│   ┌──────┐   │  ← Border highlight
│   │ 📷   │   │  ← Image zoom
│   │Image │   │
│   └──────┘   │
│              │
│ Product Name │
│ $99.99       │
│ ⭐⭐⭐⭐      │
│              │
│ [🛒 Add Now] │  ← Button highlight
└──────────────┘
```

### Added to Cart
```
┌──────────────┐
│   ┌──────┐   │
│   │ 📷   │   │
│   └──────┘   │
│              │
│ Product Name │
│ $99.99       │
│ ⭐⭐⭐⭐      │
│              │
│ [✓ In Cart]  │  ← Green checkmark
└──────────────┘
```

---

## 📱 Mobile Layout

```
┌────────────────┐
│ [☰] SHOP [🛒3] │  ← Mobile Navbar
└────────────────┘

┌────────────────┐
│ [Search box]   │
└────────────────┘

┌────────────────┐
│ [Filters ▼]    │  ← Collapsible Filters
└────────────────┘

┌────────────────┐
│ ┌────────────┐ │
│ │    📷      │ │
│ │  Product   │ │
│ │  $99.99    │ │  ← 2-column grid
│ │  ⭐⭐⭐⭐   │ │
│ │  [Cart]    │ │
│ └────────────┘ │
│ ┌────────────┐ │
│ │    📷      │ │
│ └────────────┘ │
└────────────────┘
```

---

## 🎯 Filter Sidebar

```
┌───────────────────┐
│ Filters           │
├───────────────────┤
│                   │
│ Categories        │
│ ○ All Products    │
│ ○ Electronics     │
│ ○ Fashion         │
│ ○ Home & Garden   │
│ ○ Books           │
│ ○ Sports          │
│                   │
├───────────────────┤
│ Price Range       │
│ $0 ━━●━━━━━━ $500│
│ $0 - $250         │
│                   │
├───────────────────┤
│ Customer Rating   │
│ ⭐⭐⭐⭐⭐ & Up     │
│ ⭐⭐⭐⭐ & Up       │
│ ⭐⭐⭐ & Up         │
│                   │
├───────────────────┤
│ [Clear All]       │
└───────────────────┘
```

---

## 🎨 Cart Item Component

```
┌─────────────────────────────────────┐
│  ┌────┐                             │
│  │ 📷 │  Wireless Headphones        │
│  │    │  Color: Black, Size: L      │
│  └────┘                             │
│         $149.99                     │
│         [- 2 +]  [🗑️ Remove]        │
│         Subtotal: $299.98           │
└─────────────────────────────────────┘
```

---

## 🎬 User Interactions

```mermaid
sequenceDiagram
    participant User
    participant ProductGrid
    participant Filters
    participant Cart
    participant API
    
    User->>API: Load products
    API->>ProductGrid: Display products
    
    User->>Filters: Select "Electronics"
    Filters->>ProductGrid: Filter products
    
    User->>ProductGrid: Click product
    ProductGrid->>User: Show details
    
    User->>Cart: Add to cart
    Cart->>Cart: Update count
    Cart->>User: Show notification
    
    User->>Cart: Open cart drawer
    Cart->>User: Show items
    
    User->>Cart: Update quantity
    Cart->>Cart: Recalculate total
```

---

## 🎨 Sort Options

```
Sort by: [Relevance        ▼]

Options:
• Relevance
• Price: Low to High
• Price: High to Low
• Rating: High to Low
• Name: A to Z
• Newest First
```

---

## ✅ UI Checklist

- [ ] Navbar with logo, search, cart icon
- [ ] Cart badge showing item count
- [ ] Category navigation
- [ ] Filter sidebar
- [ ] Category checkboxes
- [ ] Price range slider
- [ ] Rating filter
- [ ] Clear filters button
- [ ] Product grid (responsive)
- [ ] Product cards with images
- [ ] Product price and rating
- [ ] Add to cart button
- [ ] Sort dropdown
- [ ] Cart drawer (slide-in)
- [ ] Cart items list
- [ ] Quantity controls (+ -)
- [ ] Remove item button
- [ ] Cart totals (subtotal, tax, total)
- [ ] Product details page
- [ ] Image gallery
- [ ] Color/size selectors
- [ ] Loading states
- [ ] Empty cart state
- [ ] Success notifications

---

## 🎨 Color Scheme

```
Primary:    #3B82F6 (Blue)
Secondary:  #10B981 (Green)
Success:    #10B981 (Green)
Error:      #EF4444 (Red)
Warning:    #F59E0B (Orange)
Background: #F9FAFB (Light Gray)
Card:       #FFFFFF (White)
Text:       #1F2937 (Dark)
Border:     #E5E7EB (Light Gray)
```

---

## 🎬 Animations

1. **Product Cards**: Fade in on scroll
2. **Add to Cart**: Button success animation
3. **Cart Drawer**: Slide in from right
4. **Cart Badge**: Bounce on update
5. **Filters**: Smooth expand/collapse
6. **Product Image**: Zoom on hover
7. **Price Slider**: Smooth drag
8. **Notification**: Toast slide in

---

## 📊 Responsive Breakpoints

```
Mobile:  < 768px  → 2 columns, bottom filters
Tablet:  768-1024 → 3 columns, side filters
Desktop: > 1024px → 4 columns, full sidebar
```

---

## 📝 Notes

- Use Redux Toolkit for state
- Redux Persist for cart
- FakeStore API for products
- Loading skeletons while fetching
- Optimistic UI updates
- Toast notifications
- Lazy load images
- Virtual scrolling (optional)

---

**Build a professional e-commerce experience with Redux!** 🛒

