# Assignment 4: E-Commerce Product Catalog

**Focus**: Redux Toolkit, global state management  
**Estimated Time**: 15-18 hours  
**Difficulty**: ⭐⭐⭐⭐⭐

---

## 🎯 Learning Objectives

By the end of this assignment, you will understand:
- Redux Toolkit setup and configuration
- Slices and reducers
- Async thunks for API calls
- Redux Persist for state persistence
- Selectors and memoization
- Connecting Redux to React components
- Redux DevTools
- Complex filtering and sorting logic

---

## 📋 Requirements

### Technical Stack
- React 18+ with Vite
- Redux Toolkit
- Redux Persist
- React Router v6
- FakeStore API
- Bootstrap 5 or Tailwind CSS
- React Icons

### Features Required

1. ✅ **Product Listing**
   - Display all products in grid layout
   - Product card with image, title, price, rating
   - "Add to Cart" button
   - Loading state during API fetch
   - Responsive grid (1-4 columns based on screen size)

2. ✅ **Product Details Page**
   - Route: `/product/:id`
   - Full product information
   - Image gallery
   - Add to cart functionality
   - Quantity selector
   - Back to products button

3. ✅ **Shopping Cart**
   - Slide-in drawer from right side
   - List of cart items
   - Quantity controls (+/-)
   - Remove item button
   - Subtotal calculation
   - Total price
   - Cart item count badge on navbar

4. ✅ **Filtering & Sorting**
   - Filter by category
   - Filter by price range
   - Sort by: price (low-high, high-low), name (A-Z), rating
   - Search by product name
   - Clear all filters button

5. ✅ **Navigation**
   - Navbar with logo
   - Cart icon with item count
   - Category navigation
   - Search bar

6. ✅ **State Persistence**
   - Cart persists on page refresh
   - Uses Redux Persist

### Additional Requirements
- Error handling for API failures
- Empty states for cart and products
- Toast notifications for cart actions
- Responsive design
- Redux DevTools integration

---

## 🚀 Setup Instructions

### Step 1: Create Project

```bash
cd ~/DevEnv/learnings/react-course/assignment-04-ecommerce

# Create Vite React project
npm create vite@latest . -- --template react

# Install dependencies
npm install
```

### Step 2: Install Redux Toolkit

```bash
# Redux packages
npm install @reduxjs/toolkit react-redux redux-persist

# Routing
npm install react-router-dom

# Styling (choose one)
npm install bootstrap  # Option 1: Bootstrap
# OR
npm install -D tailwindcss postcss autoprefixer  # Option 2: Tailwind

# Other packages
npm install axios react-icons
```

### Step 3: Configure Redux Persist

No environment variables needed for this assignment (using FakeStore API).

### Step 4: Start Development Server

```bash
npm run dev
```

---

## 📁 Recommended Folder Structure

```
assignment-04-ecommerce/
├── public/
├── src/
│   ├── components/
│   │   ├── Navbar/
│   │   │   └── Navbar.jsx
│   │   ├── ProductCard/
│   │   │   └── ProductCard.jsx
│   │   ├── ProductList/
│   │   │   └── ProductList.jsx
│   │   ├── CartDrawer/
│   │   │   ├── CartDrawer.jsx
│   │   │   └── CartItem.jsx
│   │   ├── FilterSidebar/
│   │   │   └── FilterSidebar.jsx
│   │   ├── Loader/
│   │   │   └── Loader.jsx
│   │   └── ErrorMessage/
│   │       └── ErrorMessage.jsx
│   ├── pages/
│   │   ├── HomePage.jsx
│   │   └── ProductDetailsPage.jsx
│   ├── redux/
│   │   ├── store.js
│   │   ├── slices/
│   │   │   ├── productsSlice.js
│   │   │   ├── cartSlice.js
│   │   │   └── filtersSlice.js
│   │   └── selectors/
│   │       └── productSelectors.js
│   ├── services/
│   │   ├── api.js
│   │   └── productService.js
│   ├── App.jsx
│   └── main.jsx
├── package.json
└── README.md
```

---

## 💻 Step-by-Step Implementation Plan

### Phase 1: Redux Setup (4-5 hours)
1. Install Redux Toolkit and dependencies
2. Create Redux store with Redux Persist
3. Create productsSlice with async thunk
4. Create cartSlice with CRUD operations
5. Create filtersSlice
6. Test Redux DevTools

### Phase 2: API Integration (2-3 hours)
7. Create API service layer
8. Create product service functions
9. Test API calls
10. Handle loading and error states

### Phase 3: Product Components (4-5 hours)
11. Build ProductCard component
12. Build ProductList component
13. Build ProductDetailsPage
14. Connect to Redux store
15. Display products from API

### Phase 4: Cart & Filters (4-5 hours)
16. Build CartDrawer component
17. Build CartItem component
18. Build FilterSidebar component
19. Implement filtering logic with selectors
20. Add cart operations (add, remove, update quantity)

### Phase 5: Polish & Testing (2-3 hours)
21. Build Navbar with cart badge
22. Add routing
23. Add loading and error states
24. Test all features
25. Make responsive

---

## 🌐 FakeStore API

### Base URL
```
https://fakestoreapi.com
```

### Endpoints

**Get all products**
```
GET /products
```

**Get single product**
```
GET /products/1
```

**Get all categories**
```
GET /products/categories
```

**Get products in category**
```
GET /products/category/electronics
```

### Example Product Response
```json
{
  "id": 1,
  "title": "Fjallraven - Foldsack No. 1 Backpack",
  "price": 109.95,
  "description": "Your perfect pack...",
  "category": "men's clothing",
  "image": "https://fakestoreapi.com/img/...",
  "rating": {
    "rate": 3.9,
    "count": 120
  }
}
```

---

## 🔴 Redux Toolkit Concepts

### Store Configuration

```javascript
// store.js
import { configureStore } from '@reduxjs/toolkit';
import { persistStore, persistReducer } from 'redux-persist';
import storage from 'redux-persist/lib/storage';
import productsReducer from './slices/productsSlice';
import cartReducer from './slices/cartSlice';

const cartPersistConfig = {
  key: 'cart',
  storage,
};

export const store = configureStore({
  reducer: {
    products: productsReducer,
    cart: persistReducer(cartPersistConfig, cartReducer),
  },
  middleware: (getDefaultMiddleware) =>
    getDefaultMiddleware({
      serializableCheck: {
        ignoredActions: ['persist/PERSIST'],
      },
    }),
});

export const persistor = persistStore(store);
```

### Slice Example Structure

```javascript
// cartSlice.js
import { createSlice } from '@reduxjs/toolkit';

const cartSlice = createSlice({
  name: 'cart',
  initialState: {
    items: [],
    totalQuantity: 0,
    totalAmount: 0,
  },
  reducers: {
    addToCart(state, action) {
      // Logic to add item
    },
    removeFromCart(state, action) {
      // Logic to remove item
    },
    updateQuantity(state, action) {
      // Logic to update quantity
    },
    clearCart(state) {
      // Logic to clear cart
    },
  },
});

export const { addToCart, removeFromCart, updateQuantity, clearCart } = cartSlice.actions;
export default cartSlice.reducer;
```

---

## ✅ Features Checklist

### Redux Setup
- [ ] Redux store configured
- [ ] Redux Persist configured
- [ ] Products slice created
- [ ] Cart slice created
- [ ] Filters slice created
- [ ] Redux DevTools working

### Products
- [ ] Fetch all products
- [ ] Display in grid
- [ ] Product card component
- [ ] Product details page
- [ ] Loading state
- [ ] Error handling

### Cart
- [ ] Add to cart
- [ ] Remove from cart
- [ ] Update quantity
- [ ] Clear cart
- [ ] Cart drawer
- [ ] Cart item count badge
- [ ] Calculate totals
- [ ] Persist cart data

### Filtering
- [ ] Filter by category
- [ ] Filter by price range
- [ ] Search by name
- [ ] Sort products
- [ ] Clear filters
- [ ] Selectors for filtered data

### UI/UX
- [ ] Responsive navigation
- [ ] Cart slide-in drawer
- [ ] Loading spinners
- [ ] Error messages
- [ ] Empty states
- [ ] Toast notifications
- [ ] Mobile responsive

---

## 🐛 Common Challenges & Solutions

### Challenge 1: Redux Persist Not Working
**Solution**: Wrap your app with PersistGate:
```javascript
import { PersistGate } from 'redux-persist/integration/react';
import { store, persistor } from './redux/store';

<Provider store={store}>
  <PersistGate loading={null} persistor={persistor}>
    <App />
  </PersistGate>
</Provider>
```

### Challenge 2: Can't Dispatch Actions
**Solution**: Use Redux hooks:
```javascript
import { useDispatch, useSelector } from 'react-redux';

const dispatch = useDispatch();
dispatch(addToCart(product));
```

### Challenge 3: State Not Updating
**Solution**: Redux Toolkit uses Immer, so you can "mutate" state:
```javascript
addToCart(state, action) {
  // This looks like mutation but Immer handles it
  state.items.push(action.payload);
}
```

---

## 📚 Key Concepts to Understand

### 1. Redux Toolkit Slices
Simplifies Redux by combining actions and reducers.

### 2. Async Thunks
Handle asynchronous operations in Redux.

### 3. Selectors
Functions that extract and compute derived state.

### 4. Redux Persist
Automatically saves and rehydrates Redux state.

### 5. Memoization
Optimize performance by caching computed values.

---

## 🎓 Learning Resources

- [Redux Toolkit Docs](https://redux-toolkit.js.org/)
- [Redux Persist](https://github.com/rt2zz/redux-persist)
- [FakeStore API](https://fakestoreapi.com/)
- [React Redux Hooks](https://react-redux.js.org/api/hooks)
- [Reselect Library](https://github.com/reduxjs/reselect)

---

## 🚀 Deployment

Deploy to Vercel or Netlify:

```bash
npm run build
vercel --prod
```

See `../deployment-configs/DEPLOYMENT_GUIDE.md` for detailed instructions.

---

## 📊 Self-Assessment

After completing, rate your understanding (1-5):
- [ ] Redux Toolkit setup
- [ ] Slices and reducers
- [ ] Async thunks
- [ ] Redux Persist
- [ ] Selectors
- [ ] Redux DevTools
- [ ] Connecting Redux to React
- [ ] Complex state management

---

## 🎯 Bonus Challenges (Optional)

1. Add wishlist functionality
2. Add product reviews and ratings
3. Add checkout process
4. Add order history
5. Add user authentication
6. Add product comparison feature
7. Add recently viewed products
8. Implement pagination or infinite scroll
9. Add filter by rating
10. Add product recommendations

---

## 🧪 Testing Scenarios

Test these scenarios:
1. Load products from API
2. Add item to cart
3. Update item quantity in cart
4. Remove item from cart
5. Filter by category
6. Search for product
7. Sort products
8. Refresh page (check persistence)
9. Add same item multiple times
10. Clear all filters
11. Navigate to product details
12. Test on mobile viewport

---

**This is the most complex assignment so far! Take your time to understand Redux concepts. 🚀**

