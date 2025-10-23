# Assignment 9: Advanced Features & Real-time

**Part of**: Comprehensive Social Media Dashboard (ConnectHub)  
**Estimated Time**: 12-15 hours  
**Difficulty**: ⭐⭐⭐⭐⭐  
**Prerequisites**: Complete Assignments 6-8

---

## 🎯 Learning Objectives

- WebSocket communication with Socket.io
- Real-time chat implementation
- Online status tracking
- Advanced search with filters
- Debouncing and throttling
- Performance optimization
- Code splitting and lazy loading
- SEO optimization

---

## 📋 What You'll Build

### Features
1. ✅ Real-time chat system
2. ✅ One-on-one messaging
3. ✅ Message history
4. ✅ Online/offline status
5. ✅ Typing indicators
6. ✅ Read receipts
7. ✅ Advanced search (users, posts)
8. ✅ Filter posts by category/tag
9. ✅ Sort posts (newest, popular, trending)
10. ✅ Explore page with trending content
11. ✅ Hashtag support
12. ✅ Performance optimizations

---

## 🛠️ New Packages

```bash
# Socket.io for real-time features
npm install socket.io-client

# Search optimization
npm install lodash

# Performance
npm install react-window # For virtual scrolling

# SEO (optional)
npm install react-helmet-async
```

---

## 📁 New Files/Folders

```
src/
├── components/
│   ├── chat/
│   │   ├── ChatList.tsx
│   │   ├── ChatWindow.tsx
│   │   ├── MessageBubble.tsx
│   │   ├── MessageInput.tsx
│   │   ├── TypingIndicator.tsx
│   │   └── OnlineStatus.tsx
│   ├── search/
│   │   ├── AdvancedSearch.tsx
│   │   ├── SearchFilters.tsx
│   │   ├── SearchResults.tsx
│   │   └── TrendingTags.tsx
│   └── explore/
│       ├── ExploreGrid.tsx
│       ├── TrendingPosts.tsx
│       └── SuggestedUsers.tsx
├── pages/
│   ├── Chat/
│   │   └── ChatPage.tsx
│   ├── Explore/
│   │   └── ExplorePage.tsx
│   └── Search/
│       └── SearchPage.tsx
├── redux/
│   └── slices/
│       ├── chatSlice.ts
│       ├── searchSlice.ts
│       └── exploreSlice.ts
├── services/
│   ├── socket/
│   │   ├── socketClient.ts
│   │   └── socketEvents.ts
│   └── firebase/
│       ├── messages.ts
│       └── search.ts
└── hooks/
    ├── useSocket.ts
    ├── useOnlineStatus.ts
    └── useDebounce.ts
```

---

## 💻 Implementation Plan

### Phase 1: Socket.io Setup (2-3 hours)

**Backend Setup (Simple Node.js Server)**
```javascript
// server.js
const express = require('express');
const http = require('http');
const socketIo = require('socket.io');

const app = express();
const server = http.createServer(app);
const io = socketIo(server, {
  cors: {
    origin: "http://localhost:5173",
    methods: ["GET", "POST"]
  }
});

io.on('connection', (socket) => {
  console.log('User connected:', socket.id);
  
  socket.on('join', (userId) => {
    socket.join(userId);
  });
  
  socket.on('send_message', (data) => {
    io.to(data.recipientId).emit('receive_message', data);
  });
  
  socket.on('typing', (data) => {
    io.to(data.recipientId).emit('user_typing', data);
  });
  
  socket.on('disconnect', () => {
    console.log('User disconnected:', socket.id);
  });
});

server.listen(3001, () => {
  console.log('Socket server on port 3001');
});
```

**Client Setup**
- Create Socket.io client
- Connect to server
- Custom hook: useSocket
- Handle connection/disconnection
- Store socket instance in context

---

### Phase 2: Chat System (5-6 hours)

**Chat List**
- List of conversations
- Last message preview
- Unread count badge
- Online status indicator
- Sort by last message time

**Chat Window**
- Message history
- Send messages
- Real-time updates
- Typing indicator
- Read receipts
- Scroll to bottom on new message

**Message Storage**
- Store in Firestore
- Load message history
- Pagination for old messages
- Real-time sync with Socket.io

---

### Phase 3: Online Status (1-2 hours)

**Status Tracking**
- Track when user connects
- Track when user disconnects
- Update status in Firestore
- Show online/offline indicators
- Last seen timestamp

---

### Phase 4: Advanced Search (2-3 hours)

**Search Features**
- Search users by name
- Search posts by content
- Search by hashtags
- Debounced search input
- Filter results
- Sort results

**Search Filters**
- Date range
- Post type
- User type
- Category/tags
- Popularity

---

### Phase 5: Explore & Trending (2-3 hours)

**Explore Page**
- Trending posts
- Trending hashtags
- Suggested users to follow
- Popular posts this week
- New users

**Trending Algorithm (Simple)**
- Count likes, comments, saves
- Weight recent activity higher
- Calculate trending score
- Update periodically

---

### Phase 6: Performance Optimization (2-3 hours)

**Code Splitting**
- Lazy load routes
- Lazy load heavy components
- Dynamic imports

**Virtual Scrolling**
- Use react-window for long lists
- Render only visible items
- Improve feed performance

**Memoization**
- React.memo for expensive components
- useMemo for calculations
- useCallback for functions

**Image Optimization**
- Lazy load images
- Thumbnail sizes
- Progressive loading
- WebP format

---

## 📊 Data Models

### Message
```typescript
interface Message {
  id: string;
  conversationId: string;
  senderId: string;
  recipientId: string;
  content: string;
  read: boolean;
  createdAt: Timestamp;
}
```

### Conversation
```typescript
interface Conversation {
  id: string;
  participants: string[];
  lastMessage: string;
  lastMessageAt: Timestamp;
  unreadCount: { [userId: string]: number };
}
```

### UserStatus
```typescript
interface UserStatus {
  userId: string;
  online: boolean;
  lastSeen: Timestamp;
}
```

---

## 🔥 Firestore Structure

```
conversations/
  {conversationId}/
    - participants, lastMessage, etc.
    messages/
      {messageId}/
        - Message data

userStatus/
  {userId}/
    - online, lastSeen

trending/
  posts/
    {postId}/
      - score, timestamp
  hashtags/
    {tag}/
      - count, posts
```

---

## ✅ Features Checklist

### Chat
- [ ] View conversations list
- [ ] Open chat with user
- [ ] Send message
- [ ] Receive message (real-time)
- [ ] Message history
- [ ] Typing indicator
- [ ] Read receipts
- [ ] Unread count

### Online Status
- [ ] Show online/offline status
- [ ] Update status on connect
- [ ] Update status on disconnect
- [ ] Last seen timestamp
- [ ] Presence in chat list

### Search
- [ ] Search users
- [ ] Search posts
- [ ] Search by hashtags
- [ ] Debounced search
- [ ] Filter results
- [ ] Sort results

### Explore
- [ ] Trending posts
- [ ] Trending hashtags
- [ ] Suggested users
- [ ] Popular content
- [ ] Responsive grid

### Performance
- [ ] Code splitting implemented
- [ ] Virtual scrolling for feeds
- [ ] Memoization applied
- [ ] Images optimized
- [ ] Lazy loading

---

## 🐛 Common Challenges

### Challenge 1: Socket.io Connection Issues
Test CORS settings, ensure server running, check network.

### Challenge 2: Message Order
Use timestamp ordering, handle out-of-order messages.

### Challenge 3: Memory Leaks
Unsubscribe from listeners, disconnect socket on unmount.

### Challenge 4: Search Performance
Debounce input, limit results, use indexes in Firestore.

---

## 🎓 Learning Resources

- [Socket.io Client Docs](https://socket.io/docs/v4/client-api/)
- [React Performance](https://react.dev/learn/render-and-commit)
- [React Window](https://react-window.vercel.app/)
- [Firestore Indexes](https://firebase.google.com/docs/firestore/query-data/indexing)

---

## 🧪 Testing Checklist

1. Start chat with user
2. Send message
3. Receive message (open second browser/incognito)
4. See typing indicator
5. Check online status
6. Search for users
7. Search for posts
8. Search by hashtag
9. View trending posts
10. View explore page
11. Test performance with many posts
12. Check for memory leaks

---

## 🎯 What's Next?

### Ready for Assignment 10?
Final assignment! You'll:
- Write comprehensive tests
- Optimize for production
- Set up CI/CD
- Deploy to production
- Add monitoring and analytics

👉 [Continue to Assignment 10](./ASSIGNMENT_10_GUIDE.md)

---

**Almost there! Time to add the finishing touches! 🎯**

