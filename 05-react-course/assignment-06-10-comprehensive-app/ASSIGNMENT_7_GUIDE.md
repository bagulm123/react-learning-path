# Assignment 7: Core Dashboard Features

**Part of**: Comprehensive Social Media Dashboard (ConnectHub)  
**Estimated Time**: 12-15 hours  
**Difficulty**: ⭐⭐⭐⭐⭐  
**Prerequisites**: Complete Assignment 6

---

## 🎯 Learning Objectives

- Create, Read, Update, Delete (CRUD) operations with Firestore
- Image and video upload handling
- Feed pagination and infinite scroll
- Data visualization with Chart.js
- Complex Firestore queries
- Optimistic UI updates
- Cache management with Redux

---

## 📋 What You'll Build

### Features
1. ✅ Create posts (text, images, videos)
2. ✅ Edit your own posts
3. ✅ Delete your own posts
4. ✅ Like posts
5. ✅ Save posts for later
6. ✅ Home feed with pagination
7. ✅ Saved posts collection
8. ✅ Dashboard page with analytics
9. ✅ Charts showing activity (posts, likes, engagement)
10. ✅ Post statistics
11. ✅ Upload progress indicators
12. ✅ Image preview before upload

---

## 🛠️ New Packages to Install

```bash
# Charts
npm install react-chartjs-2 chart.js

# Image handling
npm install react-dropzone

# Rich text editor (optional)
npm install @mui/x-data-grid

# Date utilities
npm install date-fns
```

---

## 📁 New Files/Folders

```
src/
├── components/
│   ├── posts/
│   │   ├── CreatePostDialog.tsx
│   │   ├── PostCard.tsx
│   │   ├── PostList.tsx
│   │   ├── EditPostDialog.tsx
│   │   ├── DeletePostDialog.tsx
│   │   └── ImageUpload.tsx
│   ├── dashboard/
│   │   ├── StatsCard.tsx
│   │   ├── ActivityChart.tsx
│   │   ├── PostsChart.tsx
│   │   └── EngagementChart.tsx
│   └── feed/
│       ├── FeedContainer.tsx
│       └── InfiniteScrollLoader.tsx
├── pages/
│   ├── Home/
│   │   └── HomePage.tsx
│   ├── Dashboard/
│   │   └── DashboardPage.tsx
│   └── Saved/
│       └── SavedPostsPage.tsx
├── redux/
│   └── slices/
│       ├── postsSlice.ts
│       └── dashboardSlice.ts
└── services/
    └── firebase/
        └── posts.ts
```

---

## 💻 Implementation Plan

### Phase 1: Post CRUD (4-5 hours)

**Create Post**
- Dialog/Modal for creating posts
- Text input (multiline)
- Image upload (drag & drop or file picker)
- Video upload (optional)
- Preview before posting
- Upload to Firebase Storage
- Save post data to Firestore
- Add to Redux state

**Read Posts**
- Fetch posts from Firestore
- Display in feed
- Show author info
- Show timestamp
- Show like count
- Pagination (load more)

**Update Post**
- Edit dialog for your own posts
- Update text
- Replace or remove images
- Save changes to Firestore

**Delete Post**
- Confirmation dialog
- Delete from Firestore
- Delete images from Storage
- Remove from Redux state

---

### Phase 2: Interactions (2-3 hours)

**Like System**
- Like/unlike posts
- Update like count
- Store likes in Firestore subcollection
- Show if current user liked
- Optimistic updates

**Save System**
- Save/unsave posts
- Saved posts collection
- Saved posts page
- Show if current user saved

---

### Phase 3: Feed & Pagination (2-3 hours)

**Home Feed**
- Display all posts (chronological)
- Infinite scroll
- Load more on scroll
- Loading skeleton
- Empty state

**Firestore Queries**
- Order by timestamp
- Limit results
- Pagination with `startAfter`
- Query optimization

---

### Phase 4: Dashboard Analytics (3-4 hours)

**Statistics Cards**
- Total posts count
- Total likes received
- Total saves
- Posts this week

**Charts**
- Posts over time (line chart)
- Engagement by day (bar chart)
- Most liked posts (pie chart)
- Activity heatmap (optional)

**Data Aggregation**
- Query Firestore for stats
- Process data for charts
- Cache results in Redux

---

## 📊 Data Models

### Post
```typescript
interface Post {
  id: string;
  userId: string;
  author: {
    uid: string;
    displayName: string;
    photoURL?: string;
  };
  content: string;
  imageURLs?: string[];
  videoURL?: string;
  likesCount: number;
  savesCount: number;
  commentsCount: number;
  createdAt: Timestamp;
  updatedAt: Timestamp;
}
```

### Like
```typescript
interface Like {
  id: string;
  postId: string;
  userId: string;
  createdAt: Timestamp;
}
```

### SavedPost
```typescript
interface SavedPost {
  id: string;
  postId: string;
  userId: string;
  createdAt: Timestamp;
}
```

---

## 🔥 Firestore Collections

```
posts/
  {postId}/
    - Post data
    likes/
      {userId}/
        - Like data
    saves/
      {userId}/
        - Save data
    comments/ (will add in Assignment 8)
```

---

## ✅ Features Checklist

### Post Management
- [ ] Create post with text
- [ ] Create post with images
- [ ] Create post with video (optional)
- [ ] Edit post
- [ ] Delete post
- [ ] Validation (max length, file size)

### Interactions
- [ ] Like post
- [ ] Unlike post
- [ ] Save post
- [ ] Unsave post
- [ ] Like count updates
- [ ] Save count updates

### Feed
- [ ] Display all posts
- [ ] Chronological order
- [ ] Infinite scroll
- [ ] Pagination
- [ ] Loading states
- [ ] Empty state
- [ ] Error handling

### Dashboard
- [ ] Stats cards
- [ ] Posts chart
- [ ] Engagement chart
- [ ] Activity over time
- [ ] Responsive grid

---

## 🐛 Common Challenges

### Challenge 1: Firestore Pagination
Use `query`, `limit`, `orderBy`, and `startAfter` cursors.

### Challenge 2: Image Upload Performance
Compress images before upload, show progress.

### Challenge 3: Like Count Synchronization
Use Firestore transactions or increment().

### Challenge 4: Real-time Updates
Use `onSnapshot()` for real-time feed updates (optional).

---

## 🎓 Learning Resources

- [Firestore CRUD](https://firebase.google.com/docs/firestore/manage-data/add-data)
- [Firestore Pagination](https://firebase.google.com/docs/firestore/query-data/query-cursors)
- [Chart.js with React](https://react-chartjs-2.js.org/)
- [React Dropzone](https://react-dropzone.js.org/)

---

## 🧪 Testing Checklist

1. Create a post with text only
2. Create a post with image
3. Edit a post
4. Delete a post
5. Like a post
6. Unlike a post
7. Save a post
8. View saved posts
9. Scroll to load more posts
10. View dashboard analytics
11. Test on mobile

---

## 🎯 What's Next?

### Ready for Assignment 8?
Next, you'll add:
- Comments system
- User profiles (view others)
- Follow/unfollow
- Notifications

👉 [Continue to Assignment 8](./ASSIGNMENT_8_GUIDE.md)

---

**Excellent work building the core features! 🚀**

