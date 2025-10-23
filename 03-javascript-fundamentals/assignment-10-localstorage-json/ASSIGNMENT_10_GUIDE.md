# Assignment 10: Local Storage & JSON - Data Persistence

**By Mahendra Bagul**

The final JavaScript assignment! Local Storage lets you save data in the browser, and JSON is how we transfer data. Perfect combo for real-world apps! 💾

---

## 📚 What You'll Learn

- ✅ What is Local Storage
- ✅ localStorage methods (setItem, getItem, removeItem, clear)
- ✅ Session Storage vs Local Storage
- ✅ JSON.stringify() and JSON.parse()
- ✅ Working with nested objects
- ✅ Data validation
- ✅ Storage limits
- ✅ Security considerations
- ✅ Building persistent apps
- ✅ Complete Note-Taking App

---

## 🎯 Assignment Objectives

Create a **Note-Taking App** with categories, tags, and full persistence using Local Storage.

**Difficulty**: ⭐⭐⭐⭐☆  
**Time**: 6-7 hours  
**Prerequisites**: Assignments 1-9 completed

---

## 📋 Requirements

### Must Have
1. ✅ Create, read, update, delete notes
2. ✅ Categories and tags
3. ✅ Search functionality
4. ✅ Filter by category
5. ✅ Export notes as JSON
6. ✅ Import notes from JSON
7. ✅ Data persistence
8. ✅ Storage info display
9. ✅ Backup/restore functionality
10. ✅ Rich text formatting

---

## 💻 Complete Implementation

### HTML (index.html)
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Note Taking App</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>📝 My Notes</h1>
        
        <!-- Storage Info -->
        <div class="storage-info">
            <span>Total Notes: <strong id="noteCount">0</strong></span>
            <span>Storage Used: <strong id="storageUsed">0 KB</strong></span>
        </div>
        
        <!-- Create Note -->
        <section class="demo-section">
            <h2>Create New Note</h2>
            <form id="noteForm" class="note-form">
                <input type="text" id="noteTitle" placeholder="Note Title" required>
                <textarea id="noteContent" placeholder="Note content..." rows="5" required></textarea>
                <select id="noteCategory">
                    <option value="Personal">Personal</option>
                    <option value="Work">Work</option>
                    <option value="Ideas">Ideas</option>
                    <option value="Tasks">Tasks</option>
                </select>
                <input type="text" id="noteTags" placeholder="Tags (comma separated)">
                <button type="submit">Add Note</button>
            </form>
        </section>
        
        <!-- Filters -->
        <section class="filters-section">
            <input type="text" id="searchInput" placeholder="Search notes...">
            <select id="filterCategory">
                <option value="">All Categories</option>
                <option value="Personal">Personal</option>
                <option value="Work">Work</option>
                <option value="Ideas">Ideas</option>
                <option value="Tasks">Tasks</option>
            </select>
            <button onclick="clearAllNotes()">Clear All</button>
            <button onclick="exportNotes()">Export JSON</button>
            <button onclick="document.getElementById('importFile').click()">Import JSON</button>
            <input type="file" id="importFile" accept=".json" style="display:none" onchange="importNotes(event)">
        </section>
        
        <!-- Notes Display -->
        <div id="notesContainer" class="notes-grid"></div>
        
        <!-- Local Storage Demo -->
        <section class="demo-section">
            <h2>Local Storage Demo</h2>
            <div class="storage-demo">
                <input type="text" id="demoKey" placeholder="Key">
                <input type="text" id="demoValue" placeholder="Value">
                <button onclick="setStorageItem()">Set Item</button>
                <button onclick="getStorageItem()">Get Item</button>
                <button onclick="removeStorageItem()">Remove Item</button>
            </div>
            <div id="storageOutput" class="output"></div>
        </section>
        
        <!-- JSON Demo -->
        <section class="demo-section">
            <h2>JSON Demo</h2>
            <button onclick="demoJSONStringify()">JSON.stringify()</button>
            <button onclick="demoJSONParse()">JSON.parse()</button>
            <div id="jsonOutput" class="output"></div>
        </section>
    </div>
    
    <!-- Edit Modal -->
    <div id="editModal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeEditModal()">&times;</span>
            <h2>Edit Note</h2>
            <form id="editForm">
                <input type="hidden" id="editId">
                <input type="text" id="editTitle" required>
                <textarea id="editContent" rows="5" required></textarea>
                <select id="editCategory">
                    <option value="Personal">Personal</option>
                    <option value="Work">Work</option>
                    <option value="Ideas">Ideas</option>
                    <option value="Tasks">Tasks</option>
                </select>
                <input type="text" id="editTags" placeholder="Tags (comma separated)">
                <button type="submit">Update Note</button>
            </form>
        </div>
    </div>
    
    <script src="script.js"></script>
</body>
</html>
```

### JavaScript (script.js)
```javascript
// ===== STATE =====
let notes = [];
let nextId = 1;

// ===== INITIALIZE =====
document.addEventListener('DOMContentLoaded', () => {
    loadNotesFromStorage();
    renderNotes();
    updateStorageInfo();
    setupEventListeners();
});

function setupEventListeners() {
    document.getElementById('noteForm').addEventListener('submit', handleCreateNote);
    document.getElementById('editForm').addEventListener('submit', handleUpdateNote);
    document.getElementById('searchInput').addEventListener('input', filterNotes);
    document.getElementById('filterCategory').addEventListener('change', filterNotes);
}

// ===== LOCAL STORAGE OPERATIONS =====
function saveNotesToStorage() {
    try {
        const notesJSON = JSON.stringify(notes);
        localStorage.setItem('notes', notesJSON);
        localStorage.setItem('nextId', nextId.toString());
        updateStorageInfo();
        console.log('Notes saved to localStorage');
    } catch (error) {
        console.error('Failed to save notes:', error);
        alert('Failed to save notes. Storage might be full!');
    }
}

function loadNotesFromStorage() {
    try {
        const savedNotes = localStorage.getItem('notes');
        const savedId = localStorage.getItem('nextId');
        
        if (savedNotes) {
            notes = JSON.parse(savedNotes);
            console.log('Loaded notes:', notes);
        }
        
        if (savedId) {
            nextId = parseInt(savedId);
        }
    } catch (error) {
        console.error('Failed to load notes:', error);
        notes = [];
    }
}

// ===== CREATE NOTE =====
function handleCreateNote(e) {
    e.preventDefault();
    
    const title = document.getElementById('noteTitle').value.trim();
    const content = document.getElementById('noteContent').value.trim();
    const category = document.getElementById('noteCategory').value;
    const tagsInput = document.getElementById('noteTags').value.trim();
    const tags = tagsInput ? tagsInput.split(',').map(t => t.trim()) : [];
    
    const note = {
        id: nextId++,
        title: title,
        content: content,
        category: category,
        tags: tags,
        createdAt: new Date().toISOString(),
        updatedAt: new Date().toISOString()
    };
    
    notes.unshift(note);
    saveNotesToStorage();
    renderNotes();
    
    // Clear form
    document.getElementById('noteForm').reset();
    
    showNotification('✅ Note created successfully!');
}

// ===== RENDER NOTES =====
function renderNotes() {
    const container = document.getElementById('notesContainer');
    const searchTerm = document.getElementById('searchInput').value.toLowerCase();
    const filterCat = document.getElementById('filterCategory').value;
    
    // Filter notes
    let filtered = notes.filter(note => {
        const matchesSearch = note.title.toLowerCase().includes(searchTerm) ||
                            note.content.toLowerCase().includes(searchTerm);
        const matchesCategory = !filterCat || note.category === filterCat;
        return matchesSearch && matchesCategory;
    });
    
    if (filtered.length === 0) {
        container.innerHTML = '<div class="no-notes">No notes yet. Create one above!</div>';
        return;
    }
    
    container.innerHTML = filtered.map(note => `
        <div class="note-card ${note.category.toLowerCase()}">
            <div class="note-header">
                <h3>${note.title}</h3>
                <span class="category-badge">${note.category}</span>
            </div>
            <p class="note-content">${note.content}</p>
            ${note.tags.length > 0 ? `
                <div class="tags">
                    ${note.tags.map(tag => `<span class="tag">#${tag}</span>`).join('')}
                </div>
            ` : ''}
            <div class="note-meta">
                <span>${new Date(note.createdAt).toLocaleDateString()}</span>
            </div>
            <div class="note-actions">
                <button onclick="editNote(${note.id})">Edit</button>
                <button onclick="deleteNote(${note.id})" class="delete-btn">Delete</button>
            </div>
        </div>
    `).join('');
}

// ===== UPDATE NOTE =====
window.editNote = function(id) {
    const note = notes.find(n => n.id === id);
    if (!note) return;
    
    document.getElementById('editId').value = note.id;
    document.getElementById('editTitle').value = note.title;
    document.getElementById('editContent').value = note.content;
    document.getElementById('editCategory').value = note.category;
    document.getElementById('editTags').value = note.tags.join(', ');
    
    document.getElementById('editModal').style.display = 'flex';
};

window.closeEditModal = function() {
    document.getElementById('editModal').style.display = 'none';
};

function handleUpdateNote(e) {
    e.preventDefault();
    
    const id = parseInt(document.getElementById('editId').value);
    const note = notes.find(n => n.id === id);
    
    if (note) {
        note.title = document.getElementById('editTitle').value.trim();
        note.content = document.getElementById('editContent').value.trim();
        note.category = document.getElementById('editCategory').value;
        const tagsInput = document.getElementById('editTags').value.trim();
        note.tags = tagsInput ? tagsInput.split(',').map(t => t.trim()) : [];
        note.updatedAt = new Date().toISOString();
        
        saveNotesToStorage();
        renderNotes();
        closeEditModal();
        showNotification('✅ Note updated successfully!');
    }
}

// ===== DELETE NOTE =====
window.deleteNote = function(id) {
    if (!confirm('Delete this note?')) return;
    
    notes = notes.filter(n => n.id !== id);
    saveNotesToStorage();
    renderNotes();
    showNotification('✅ Note deleted!');
};

// ===== FILTER NOTES =====
function filterNotes() {
    renderNotes();
}

// ===== CLEAR ALL =====
window.clearAllNotes = function() {
    if (!confirm('Delete ALL notes? This cannot be undone!')) return;
    
    notes = [];
    nextId = 1;
    saveNotesToStorage();
    renderNotes();
    showNotification('✅ All notes cleared!');
};

// ===== EXPORT NOTES =====
window.exportNotes = function() {
    if (notes.length === 0) {
        alert('No notes to export!');
        return;
    }
    
    const dataStr = JSON.stringify(notes, null, 2);
    const dataBlob = new Blob([dataStr], { type: 'application/json' });
    const url = URL.createObjectURL(dataBlob);
    
    const link = document.createElement('a');
    link.href = url;
    link.download = `notes_${new Date().toISOString()}.json`;
    link.click();
    
    URL.revokeObjectURL(url);
    showNotification('✅ Notes exported!');
};

// ===== IMPORT NOTES =====
window.importNotes = function(event) {
    const file = event.target.files[0];
    if (!file) return;
    
    const reader = new FileReader();
    
    reader.onload = function(e) {
        try {
            const imported = JSON.parse(e.target.result);
            
            if (!Array.isArray(imported)) {
                throw new Error('Invalid format');
            }
            
            // Merge with existing notes
            imported.forEach(note => {
                note.id = nextId++;
            });
            
            notes = [...imported, ...notes];
            saveNotesToStorage();
            renderNotes();
            showNotification('✅ Notes imported successfully!');
        } catch (error) {
            alert('Failed to import notes. Invalid file format!');
            console.error(error);
        }
    };
    
    reader.readAsText(file);
    event.target.value = ''; // Reset file input
};

// ===== STORAGE INFO =====
function updateStorageInfo() {
    document.getElementById('noteCount').textContent = notes.length;
    
    try {
        const notesJSON = JSON.stringify(notes);
        const sizeInBytes = new Blob([notesJSON]).size;
        const sizeInKB = (sizeInBytes / 1024).toFixed(2);
        document.getElementById('storageUsed').textContent = `${sizeInKB} KB`;
    } catch (error) {
        document.getElementById('storageUsed').textContent = 'N/A';
    }
}

// ===== STORAGE DEMO =====
window.setStorageItem = function() {
    const key = document.getElementById('demoKey').value;
    const value = document.getElementById('demoValue').value;
    
    if (!key) {
        alert('Enter a key!');
        return;
    }
    
    localStorage.setItem(key, value);
    
    document.getElementById('storageOutput').innerHTML = `
        <div class="success-box">
            ✅ Saved to localStorage<br>
            <strong>Key:</strong> ${key}<br>
            <strong>Value:</strong> ${value}
        </div>
    `;
};

window.getStorageItem = function() {
    const key = document.getElementById('demoKey').value;
    
    if (!key) {
        alert('Enter a key!');
        return;
    }
    
    const value = localStorage.getItem(key);
    
    document.getElementById('storageOutput').innerHTML = `
        <div class="${value !== null ? 'success-box' : 'error-box'}">
            ${value !== null ? '✅' : '❌'} Retrieved from localStorage<br>
            <strong>Key:</strong> ${key}<br>
            <strong>Value:</strong> ${value !== null ? value : 'Not found'}
        </div>
    `;
};

window.removeStorageItem = function() {
    const key = document.getElementById('demoKey').value;
    
    if (!key) {
        alert('Enter a key!');
        return;
    }
    
    localStorage.removeItem(key);
    
    document.getElementById('storageOutput').innerHTML = `
        <div class="success-box">
            ✅ Removed from localStorage<br>
            <strong>Key:</strong> ${key}
        </div>
    `;
};

// ===== JSON DEMO =====
window.demoJSONStringify = function() {
    const obj = {
        name: 'John Doe',
        age: 30,
        skills: ['JavaScript', 'React', 'Node.js'],
        address: {
            city: 'Mumbai',
            country: 'India'
        }
    };
    
    const jsonString = JSON.stringify(obj, null, 2);
    
    document.getElementById('jsonOutput').innerHTML = `
        <div class="demo-box">
            <h4>JavaScript Object:</h4>
            <pre>${JSON.stringify(obj, null, 2)}</pre>
            
            <h4>JSON String (JSON.stringify):</h4>
            <pre>"${jsonString.replace(/\n/g, '\\n').replace(/"/g, '\\"')}"</pre>
            
            <p class="info">JSON.stringify() converts object to string for storage/transmission</p>
        </div>
    `;
};

window.demoJSONParse = function() {
    const jsonString = '{"name":"Jane","age":25,"active":true}';
    const obj = JSON.parse(jsonString);
    
    document.getElementById('jsonOutput').innerHTML = `
        <div class="demo-box">
            <h4>JSON String:</h4>
            <pre>${jsonString}</pre>
            
            <h4>Parsed Object (JSON.parse):</h4>
            <pre>${JSON.stringify(obj, null, 2)}</pre>
            
            <h4>Access Properties:</h4>
            <pre>obj.name  → "${obj.name}"
obj.age   → ${obj.age}
obj.active → ${obj.active}</pre>
            
            <p class="info">JSON.parse() converts string back to object for use in code</p>
        </div>
    `;
};

// ===== NOTIFICATION =====
function showNotification(message) {
    const notification = document.createElement('div');
    notification.className = 'notification';
    notification.textContent = message;
    
    document.body.appendChild(notification);
    
    setTimeout(() => notification.classList.add('show'), 100);
    
    setTimeout(() => {
        notification.classList.remove('show');
        setTimeout(() => notification.remove(), 300);
    }, 3000);
}

console.log('✅ Note Taking App loaded!');
console.log('Storage available:', 'localStorage' in window);
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
    margin-bottom: 1rem;
    font-size: 2.5rem;
}

.storage-info {
    display: flex;
    justify-content: center;
    gap: 2rem;
    color: white;
    margin-bottom: 2rem;
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

.note-form {
    display: flex;
    flex-direction: column;
    gap: 1rem;
}

input,
textarea,
select {
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

.filters-section {
    background: white;
    padding: 1.5rem;
    border-radius: 15px;
    margin-bottom: 2rem;
    display: flex;
    gap: 1rem;
    flex-wrap: wrap;
    box-shadow: 0 10px 30px rgba(0,0,0,0.2);
}

.filters-section input,
.filters-section select {
    flex: 1;
    min-width: 200px;
}

.notes-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 1.5rem;
    margin-bottom: 2rem;
}

.note-card {
    background: white;
    padding: 1.5rem;
    border-radius: 10px;
    box-shadow: 0 5px 15px rgba(0,0,0,0.1);
    border-left: 4px solid;
    transition: transform 0.3s;
}

.note-card:hover {
    transform: translateY(-5px);
}

.note-card.personal {
    border-color: #667eea;
}

.note-card.work {
    border-color: #dc3545;
}

.note-card.ideas {
    border-color: #ffc107;
}

.note-card.tasks {
    border-color: #28a745;
}

.note-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 1rem;
}

.note-header h3 {
    color: #2c3e50;
    font-size: 1.25rem;
}

.category-badge {
    background: #667eea;
    color: white;
    padding: 0.25rem 0.75rem;
    border-radius: 20px;
    font-size: 0.75rem;
}

.note-content {
    color: #666;
    line-height: 1.6;
    margin-bottom: 1rem;
}

.tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    margin-bottom: 1rem;
}

.tag {
    background: #f0f0f0;
    padding: 0.25rem 0.5rem;
    border-radius: 4px;
    font-size: 0.875rem;
    color: #667eea;
}

.note-meta {
    font-size: 0.875rem;
    color: #999;
    margin-bottom: 1rem;
}

.note-actions {
    display: flex;
    gap: 0.5rem;
}

.note-actions button {
    flex: 1;
}

.delete-btn {
    background-color: #dc3545;
}

.delete-btn:hover {
    background-color: #c82333;
}

.no-notes {
    grid-column: 1 / -1;
    text-align: center;
    padding: 3rem;
    color: #999;
    background: white;
    border-radius: 10px;
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

/* Storage Demo */
.storage-demo {
    display: flex;
    gap: 1rem;
    margin-bottom: 1rem;
}

.output {
    margin-top: 1.5rem;
}

.success-box {
    background: #d4edda;
    color: #155724;
    padding: 1.5rem;
    border-radius: 10px;
    border-left: 4px solid #28a745;
}

.error-box {
    background: #f8d7da;
    color: #721c24;
    padding: 1.5rem;
    border-radius: 10px;
    border-left: 4px solid #dc3545;
}

.demo-box {
    background: #f8f9fa;
    padding: 1.5rem;
    border-radius: 10px;
}

.demo-box h4 {
    color: #667eea;
    margin: 1rem 0 0.5rem 0;
}

.demo-box h4:first-child {
    margin-top: 0;
}

.demo-box pre {
    background: #2c3e50;
    color: #fff;
    padding: 1rem;
    border-radius: 5px;
    overflow-x: auto;
    font-size: 0.9rem;
}

.info {
    color: #666;
    font-style: italic;
    margin-top: 1rem;
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
    border-left: 4px solid #28a745;
}

.notification.show {
    transform: translateX(0);
}

@media (max-width: 768px) {
    .notes-grid {
        grid-template-columns: 1fr;
    }
    
    .filters-section {
        flex-direction: column;
    }
    
    .storage-demo {
        flex-direction: column;
    }
}
```

---

## 📖 Key Concepts

### Local Storage vs Session Storage
```javascript
// localStorage - persists even after browser closes
localStorage.setItem('key', 'value');

// sessionStorage - cleared when tab closes
sessionStorage.setItem('key', 'value');
```

### JSON Methods
```javascript
// Object to JSON string
const obj = { name: 'John', age: 30 };
const json = JSON.stringify(obj);

// JSON string to object
const parsed = JSON.parse(json);
```

### Storage Limits
- Usually 5-10 MB per domain
- Check with: `try/catch` blocks
- Handle quota exceeded errors

---

## ✅ Self-Assessment

- [ ] CRUD operations work
- [ ] Data persists after reload
- [ ] Search/filter functional
- [ ] Export/import JSON works
- [ ] Categories and tags implemented
- [ ] Storage info displayed
- [ ] Local Storage demo works
- [ ] JSON demo functional
- [ ] Error handling implemented
- [ ] Clean, professional UI

---

## 🎉 JavaScript Phase Complete!

Congratulations! You've completed all 10 JavaScript assignments. You're now ready for TypeScript and React! 🚀

---

**Next**: [TypeScript Fundamentals →](../../04-typescript-fundamentals/README.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

