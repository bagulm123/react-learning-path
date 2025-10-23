# Assignment 8: Fetch API & AJAX - Real API Integration

**By Mahendra Bagul**

Time to connect to the real world! Fetch API lets you get data from servers, post data, and build truly dynamic applications. 🌍

---

## 📚 What You'll Learn

- ✅ Fetch API basics
- ✅ GET, POST, PUT, DELETE requests
- ✅ Request headers
- ✅ Request body (JSON)
- ✅ Response handling
- ✅ Status codes
- ✅ CORS (Cross-Origin Resource Sharing)
- ✅ Error handling
- ✅ REST API integration
- ✅ Building a complete CRUD app

---

## 🎯 Assignment Objectives

Create a **Post Manager** that performs all CRUD operations with a real API (JSONPlaceholder).

**Difficulty**: ⭐⭐⭐⭐☆  
**Time**: 6-7 hours  
**Prerequisites**: Assignments 1-7 completed

---

## 📋 Requirements

### Must Have
1. ✅ Fetch all posts (GET)
2. ✅ Create new post (POST)
3. ✅ Update post (PUT)
4. ✅ Delete post (DELETE)
5. ✅ Search/filter posts
6. ✅ Loading states
7. ✅ Error handling
8. ✅ Form validation
9. ✅ Response display
10. ✅ Complete CRUD UI

---

## 💻 Complete Implementation

### HTML (index.html)
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fetch API & AJAX</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>📡 Fetch API - Post Manager</h1>
        
        <!-- Create Post -->
        <section class="demo-section">
            <h2>Create New Post</h2>
            <form id="createForm" class="post-form">
                <input type="text" id="title" placeholder="Post Title" required>
                <textarea id="body" placeholder="Post Content" rows="4" required></textarea>
                <button type="submit">Create Post</button>
            </form>
        </section>
        
        <!-- Search & Filter -->
        <section class="demo-section">
            <h2>All Posts (<span id="postCount">0</span>)</h2>
            <div class="controls">
                <input type="text" id="searchInput" placeholder="Search posts...">
                <button onclick="loadPosts()">Refresh Posts</button>
            </div>
        </section>
        
        <!-- Posts List -->
        <section id="postsContainer" class="posts-grid">
            <div class="loading">⏳ Loading posts...</div>
        </section>
        
        <!-- API Reference -->
        <section class="demo-section">
            <h2>Fetch API Reference</h2>
            <div class="api-reference">
                <div class="api-method">
                    <h4>GET - Fetch Data</h4>
                    <pre>fetch('https://api.example.com/data')
    .then(res => res.json())
    .then(data => console.log(data))
    .catch(err => console.error(err));</pre>
                </div>
                
                <div class="api-method">
                    <h4>POST - Create Data</h4>
                    <pre>fetch('https://api.example.com/data', {
    method: 'POST',
    headers: {
        'Content-Type': 'application/json'
    },
    body: JSON.stringify({ name: 'John' })
})
    .then(res => res.json())
    .then(data => console.log(data));</pre>
                </div>
                
                <div class="api-method">
                    <h4>PUT - Update Data</h4>
                    <pre>fetch('https://api.example.com/data/1', {
    method: 'PUT',
    headers: {
        'Content-Type': 'application/json'
    },
    body: JSON.stringify({ name: 'Jane' })
})
    .then(res => res.json())
    .then(data => console.log(data));</pre>
                </div>
                
                <div class="api-method">
                    <h4>DELETE - Remove Data</h4>
                    <pre>fetch('https://api.example.com/data/1', {
    method: 'DELETE'
})
    .then(res => res.json())
    .then(data => console.log(data));</pre>
                </div>
            </div>
        </section>
    </div>
    
    <!-- Edit Modal -->
    <div id="editModal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeEditModal()">&times;</span>
            <h2>Edit Post</h2>
            <form id="editForm">
                <input type="hidden" id="editId">
                <input type="text" id="editTitle" placeholder="Post Title" required>
                <textarea id="editBody" placeholder="Post Content" rows="4" required></textarea>
                <button type="submit">Update Post</button>
            </form>
        </div>
    </div>
    
    <script src="script.js"></script>
</body>
</html>
```

### JavaScript (script.js)
```javascript
// API Configuration
const API_BASE = 'https://jsonplaceholder.typicode.com';
const POSTS_ENDPOINT = `${API_BASE}/posts`;

// State
let allPosts = [];

// ===== INITIALIZE =====
document.addEventListener('DOMContentLoaded', () => {
    loadPosts();
    setupEventListeners();
});

function setupEventListeners() {
    // Create form
    document.getElementById('createForm').addEventListener('submit', handleCreate);
    
    // Edit form
    document.getElementById('editForm').addEventListener('submit', handleUpdate);
    
    // Search
    document.getElementById('searchInput').addEventListener('input', filterPosts);
}

// ===== FETCH ALL POSTS (GET) =====
async function loadPosts() {
    const container = document.getElementById('postsContainer');
    container.innerHTML = '<div class="loading">⏳ Loading posts...</div>';
    
    try {
        const response = await fetch(`${POSTS_ENDPOINT}?_limit=10`);
        
        // Check if response is ok
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        
        allPosts = await response.json();
        document.getElementById('postCount').textContent = allPosts.length;
        
        renderPosts(allPosts);
    } catch (error) {
        container.innerHTML = `
            <div class="error-message">
                ❌ Failed to load posts: ${error.message}
            </div>
        `;
    }
}

// ===== RENDER POSTS =====
function renderPosts(posts) {
    const container = document.getElementById('postsContainer');
    
    if (posts.length === 0) {
        container.innerHTML = '<div class="no-data">No posts found</div>';
        return;
    }
    
    container.innerHTML = posts.map(post => `
        <div class="post-card">
            <h3>${post.title}</h3>
            <p>${post.body}</p>
            <div class="post-meta">
                <span>Post ID: ${post.id}</span>
            </div>
            <div class="post-actions">
                <button onclick="editPost(${post.id})" class="btn-edit">Edit</button>
                <button onclick="deletePost(${post.id})" class="btn-delete">Delete</button>
            </div>
        </div>
    `).join('');
}

// ===== CREATE POST (POST) =====
async function handleCreate(e) {
    e.preventDefault();
    
    const title = document.getElementById('title').value.trim();
    const body = document.getElementById('body').value.trim();
    
    if (!title || !body) {
        alert('Please fill all fields!');
        return;
    }
    
    try {
        const response = await fetch(POSTS_ENDPOINT, {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json'
            },
            body: JSON.stringify({
                title: title,
                body: body,
                userId: 1
            })
        });
        
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        
        const newPost = await response.json();
        
        // Add to beginning of array
        allPosts.unshift(newPost);
        renderPosts(allPosts);
        document.getElementById('postCount').textContent = allPosts.length;
        
        // Clear form
        document.getElementById('createForm').reset();
        
        // Show success message
        showNotification('✅ Post created successfully!', 'success');
        
        console.log('Created post:', newPost);
    } catch (error) {
        showNotification(`❌ Failed to create post: ${error.message}`, 'error');
    }
}

// ===== UPDATE POST (PUT) =====
window.editPost = function(id) {
    const post = allPosts.find(p => p.id === id);
    if (!post) return;
    
    document.getElementById('editId').value = post.id;
    document.getElementById('editTitle').value = post.title;
    document.getElementById('editBody').value = post.body;
    
    document.getElementById('editModal').style.display = 'flex';
};

window.closeEditModal = function() {
    document.getElementById('editModal').style.display = 'none';
};

async function handleUpdate(e) {
    e.preventDefault();
    
    const id = document.getElementById('editId').value;
    const title = document.getElementById('editTitle').value.trim();
    const body = document.getElementById('editBody').value.trim();
    
    if (!title || !body) {
        alert('Please fill all fields!');
        return;
    }
    
    try {
        const response = await fetch(`${POSTS_ENDPOINT}/${id}`, {
            method: 'PUT',
            headers: {
                'Content-Type': 'application/json'
            },
            body: JSON.stringify({
                id: parseInt(id),
                title: title,
                body: body,
                userId: 1
            })
        });
        
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        
        const updatedPost = await response.json();
        
        // Update in array
        const index = allPosts.findIndex(p => p.id == id);
        if (index !== -1) {
            allPosts[index] = updatedPost;
            renderPosts(allPosts);
        }
        
        closeEditModal();
        showNotification('✅ Post updated successfully!', 'success');
        
        console.log('Updated post:', updatedPost);
    } catch (error) {
        showNotification(`❌ Failed to update post: ${error.message}`, 'error');
    }
}

// ===== DELETE POST (DELETE) =====
window.deletePost = async function(id) {
    if (!confirm('Are you sure you want to delete this post?')) {
        return;
    }
    
    try {
        const response = await fetch(`${POSTS_ENDPOINT}/${id}`, {
            method: 'DELETE'
        });
        
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        
        // Remove from array
        allPosts = allPosts.filter(p => p.id !== id);
        renderPosts(allPosts);
        document.getElementById('postCount').textContent = allPosts.length;
        
        showNotification('✅ Post deleted successfully!', 'success');
        
        console.log('Deleted post ID:', id);
    } catch (error) {
        showNotification(`❌ Failed to delete post: ${error.message}`, 'error');
    }
};

// ===== SEARCH/FILTER =====
function filterPosts() {
    const searchTerm = document.getElementById('searchInput').value.toLowerCase();
    
    const filtered = allPosts.filter(post => 
        post.title.toLowerCase().includes(searchTerm) ||
        post.body.toLowerCase().includes(searchTerm)
    );
    
    renderPosts(filtered);
}

// ===== NOTIFICATION =====
function showNotification(message, type = 'info') {
    const notification = document.createElement('div');
    notification.className = `notification ${type}`;
    notification.textContent = message;
    
    document.body.appendChild(notification);
    
    setTimeout(() => {
        notification.classList.add('show');
    }, 100);
    
    setTimeout(() => {
        notification.classList.remove('show');
        setTimeout(() => {
            notification.remove();
        }, 300);
    }, 3000);
}

console.log('✅ Fetch API app loaded!');
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
    max-width: 1200px;
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

.post-form {
    display: flex;
    flex-direction: column;
    gap: 1rem;
}

input,
textarea {
    padding: 0.75rem;
    border: 2px solid #ddd;
    border-radius: 8px;
    font-size: 1rem;
    font-family: inherit;
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
}

button:hover {
    background-color: #764ba2;
    transform: translateY(-2px);
}

.controls {
    display: flex;
    gap: 1rem;
    margin-bottom: 1.5rem;
}

.controls input {
    flex: 1;
}

.posts-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 1.5rem;
}

.post-card {
    background: white;
    padding: 1.5rem;
    border-radius: 10px;
    box-shadow: 0 5px 15px rgba(0,0,0,0.1);
    transition: transform 0.3s;
}

.post-card:hover {
    transform: translateY(-5px);
}

.post-card h3 {
    color: #2c3e50;
    margin-bottom: 1rem;
}

.post-card p {
    color: #666;
    line-height: 1.6;
    margin-bottom: 1rem;
}

.post-meta {
    font-size: 0.875rem;
    color: #999;
    margin-bottom: 1rem;
}

.post-actions {
    display: flex;
    gap: 0.5rem;
}

.btn-edit {
    background-color: #17a2b8;
    flex: 1;
}

.btn-edit:hover {
    background-color: #138496;
}

.btn-delete {
    background-color: #dc3545;
    flex: 1;
}

.btn-delete:hover {
    background-color: #c82333;
}

.loading {
    grid-column: 1 / -1;
    text-align: center;
    padding: 3rem;
    font-size: 1.2rem;
    color: #667eea;
}

.error-message {
    grid-column: 1 / -1;
    background: #f8d7da;
    color: #721c24;
    padding: 2rem;
    border-radius: 10px;
    text-align: center;
}

.no-data {
    grid-column: 1 / -1;
    text-align: center;
    padding: 3rem;
    color: #999;
}

/* Modal */
.modal {
    display: none;
    position: fixed;
    z-index: 1000;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0,0,0,0.5);
    align-items: center;
    justify-content: center;
}

.modal-content {
    background: white;
    padding: 2rem;
    border-radius: 15px;
    max-width: 500px;
    width: 90%;
    position: relative;
}

.close {
    position: absolute;
    right: 1.5rem;
    top: 1rem;
    font-size: 2rem;
    cursor: pointer;
    color: #999;
}

.close:hover {
    color: #333;
}

/* Notification */
.notification {
    position: fixed;
    top: 2rem;
    right: 2rem;
    background: white;
    padding: 1rem 2rem;
    border-radius: 8px;
    box-shadow: 0 5px 15px rgba(0,0,0,0.2);
    transform: translateX(400px);
    transition: transform 0.3s;
    z-index: 1001;
}

.notification.show {
    transform: translateX(0);
}

.notification.success {
    border-left: 4px solid #28a745;
}

.notification.error {
    border-left: 4px solid #dc3545;
}

/* API Reference */
.api-reference {
    display: grid;
    gap: 1rem;
}

.api-method {
    background: #f8f9fa;
    padding: 1.5rem;
    border-radius: 10px;
}

.api-method h4 {
    color: #667eea;
    margin-bottom: 0.75rem;
}

.api-method pre {
    background: #2c3e50;
    color: #fff;
    padding: 1rem;
    border-radius: 5px;
    overflow-x: auto;
    font-size: 0.9rem;
}

@media (max-width: 768px) {
    .posts-grid {
        grid-template-columns: 1fr;
    }
    
    .controls {
        flex-direction: column;
    }
}
```

---

## 📖 Key Concepts

### HTTP Methods
- **GET**: Retrieve data
- **POST**: Create new data
- **PUT/PATCH**: Update existing data
- **DELETE**: Remove data

### Status Codes
- **200-299**: Success
- **400-499**: Client errors
- **500-599**: Server errors

### Headers
```javascript
const headers = {
    'Content-Type': 'application/json',
    'Authorization': 'Bearer token123'
};
```

---

## ✅ Self-Assessment

- [ ] Can fetch all posts
- [ ] Can create new posts
- [ ] Can update posts
- [ ] Can delete posts
- [ ] Search/filter works
- [ ] Loading states shown
- [ ] Error handling implemented
- [ ] Modal for editing works
- [ ] Notifications shown
- [ ] Clean, professional UI

---

**Next**: [Assignment 9: Error Handling & Debugging](../assignment-09-error-handling/ASSIGNMENT_9_GUIDE.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

