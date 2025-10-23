# Assignment 8: Social Interactions

**Part of**: Comprehensive Social Media Dashboard (ConnectHub)  
**Estimated Time**: 12-15 hours  
**Difficulty**: ⭐⭐⭐⭐⭐  
**Prerequisites**: Complete Assignments 6-7

---

## 🎯 Learning Objectives

- Nested data structures in Firestore
- Comments and replies system
- User relationships (follow/unfollow)
- Notifications system
- Complex Firestore queries with relationships
- Real-time updates with Firestore listeners
- Profile pages for other users

---

## 📋 What You'll Build

### Features
1. ✅ Comment on posts
2. ✅ Reply to comments (nested comments)
3. ✅ Edit/delete your comments
4. ✅ Like comments
5. ✅ View any user's profile
6. ✅ Follow/unfollow users
7. ✅ Followers list
8. ✅ Following list
9. ✅ Notifications center
10. ✅ Notification types (like, comment, follow)
11. ✅ Mark notifications as read
12. ✅ Activity feed
13. ✅ User search

---

## 🛠️ New Packages

```bash
# No new packages required (using existing Firebase, MUI, Redux)
```

---

## 📁 New Files/Folders

```
src/
├── components/
│   ├── comments/
│   │   ├── CommentList.tsx
│   │   ├── CommentItem.tsx
│   │   ├── CommentForm.tsx
│   │   ├── ReplyForm.tsx
│   │   └── DeleteCommentDialog.tsx
│   ├── profile/
│   │   ├── UserProfile.tsx
│   │   ├── FollowButton.tsx
│   │   ├── FollowersList.tsx
│   │   ├── FollowingList.tsx
│   │   └── UserPostsList.tsx
│   ├── notifications/
│   │   ├── NotificationCenter.tsx
│   │   ├── NotificationItem.tsx
│   │   ├── NotificationBadge.tsx
│   │   └── NotificationDrawer.tsx
│   └── search/
│       ├── UserSearch.tsx
│       └── UserSearchResult.tsx
├── pages/
│   ├── Profile/
│   │   └── UserProfilePage.tsx
│   └── Notifications/
│       └── NotificationsPage.tsx
├── redux/
│   └── slices/
│       ├── commentsSlice.ts
│       ├── followSlice.ts
│       └── notificationsSlice.ts
└── services/
    └── firebase/
        ├── comments.ts
        ├── follow.ts
        └── notifications.ts
```

---

## 💻 Implementation Plan

### Phase 1: Comments System (4-5 hours)

**Comment Structure**
- Comments on posts
- Nested replies (1 level deep)
- Author information
- Timestamp
- Like count

**Comment CRUD**
- Add comment to post
- Edit own comment
- Delete own comment
- Reply to comment
- Like/unlike comment

**UI Components**
- Comment list
- Comment item
- Comment form
- Reply form
- Nested comment display

---

### Phase 2: User Profiles & Follow System (3-4 hours)

**User Profile Pages**
- View any user's profile
- Display user's posts
- Show follower/following counts
- Show bio and info

**Follow System**
- Follow button
- Unfollow button
- Update follower/following counts
- Followers list modal
- Following list modal

**Firestore Structure**
```
users/
  {userId}/
    followers/
      {followerId}
    following/
      {followingId}
```

---

### Phase 3: Notifications System (3-4 hours)

**Notification Types**
1. Someone liked your post
2. Someone commented on your post
3. Someone replied to your comment
4. Someone followed you
5. Someone mentioned you (optional)

**Notification Features**
- Notification center in navbar
- Badge with unread count
- Mark as read
- Mark all as read
- Navigate to related post/profile
- Real-time updates

**Notification Creation**
- Trigger on like
- Trigger on comment
- Trigger on follow
- Don't notify self

---

### Phase 4: Activity Feed (2-3 hours)

**Activity Timeline**
- Posts from followed users
- Chronological feed
- Pagination
- Empty state (follow users to see content)

**User Search**
- Search users by name
- Display results
- Navigate to profile
- Quick follow button in results

---

## 📊 Data Models

### Comment
```typescript
interface Comment {
  id: string;
  postId: string;
  userId: string;
  author: {
    uid: string;
    displayName: string;
    photoURL?: string;
  };
  content: string;
  parentCommentId?: string; // For replies
  likesCount: number;
  repliesCount: number;
  createdAt: Timestamp;
  updatedAt: Timestamp;
}
```

### Follow
```typescript
interface Follow {
  id: string;
  followerId: string;
  followingId: string;
  createdAt: Timestamp;
}
```

### Notification
```typescript
interface Notification {
  id: string;
  userId: string; // Who receives the notification
  type: 'like' | 'comment' | 'follow' | 'reply';
  actor: {
    uid: string;
    displayName: string;
    photoURL?: string;
  };
  postId?: string;
  commentId?: string;
  message: string;
  read: boolean;
  createdAt: Timestamp;
}
```

---

## 🔥 Firestore Structure

```
posts/
  {postId}/
    comments/
      {commentId}/
        - Comment data
        replies/
          {replyId}/
            - Reply data

users/
  {userId}/
    followers/
      {followerId}/
        - createdAt
    following/
      {followingId}/
        - createdAt

notifications/
  {userId}/
    notifications/
      {notificationId}/
        - Notification data
```

---

## ✅ Features Checklist

### Comments
- [ ] Add comment to post
- [ ] Reply to comment
- [ ] Edit comment
- [ ] Delete comment
- [ ] Like comment
- [ ] Display nested replies
- [ ] Comment count on post

### User Profiles
- [ ] View other users' profiles
- [ ] Display user info
- [ ] Show user's posts
- [ ] Show follower count
- [ ] Show following count
- [ ] Navigate between profiles

### Follow System
- [ ] Follow user
- [ ] Unfollow user
- [ ] Followers list
- [ ] Following list
- [ ] Follow button states
- [ ] Update counts

### Notifications
- [ ] Create notification on like
- [ ] Create notification on comment
- [ ] Create notification on follow
- [ ] Notification center in navbar
- [ ] Unread count badge
- [ ] Mark as read
- [ ] Mark all as read
- [ ] Navigate to related content
- [ ] Real-time updates

### Search & Discovery
- [ ] Search users
- [ ] Display search results
- [ ] Navigate to profiles from search

---

## 🐛 Common Challenges

### Challenge 1: Nested Comments Performance
Limit nesting to 1-2 levels, paginate if needed.

### Challenge 2: Notification Spam
Batch notifications, don't notify on own actions.

### Challenge 3: Real-time Updates
Use Firestore listeners, unsubscribe on unmount.

### Challenge 4: Follow Count Consistency
Use Firestore transactions or cloud functions.

---

## 🎓 Learning Resources

- [Firestore Subcollections](https://firebase.google.com/docs/firestore/data-model#subcollections)
- [Firestore Real-time Listeners](https://firebase.google.com/docs/firestore/query-data/listen)
- [Firestore Security Rules](https://firebase.google.com/docs/firestore/security/get-started)

---

## 🧪 Testing Checklist

1. Add comment to post
2. Reply to comment
3. Edit comment
4. Delete comment
5. Like comment
6. View another user's profile
7. Follow user
8. Unfollow user
9. View followers list
10. View following list
11. Receive notification on like
12. Receive notification on comment
13. Mark notification as read
14. Search for users
15. Test on mobile

---

## 🎯 What's Next?

### Ready for Assignment 9?
Next, you'll add:
- Real-time chat with Socket.io
- Online status
- Advanced search and filters
- Explore page with trending content

👉 [Continue to Assignment 9](./ASSIGNMENT_9_GUIDE.md)

---

**Awesome work adding social features! 🎉**

