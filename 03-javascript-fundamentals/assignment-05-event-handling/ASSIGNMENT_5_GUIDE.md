# Assignment 5: Event Handling - Responding to User Actions

**By Mahendra Bagul**

Events are how users interact with your website. Click, type, scroll, hover - all events! Let's master them. 🎮

---

## 📚 What You'll Learn

- ✅ Event types (click, input, submit, keypress, mouseover, etc.)
- ✅ Event listeners
- ✅ Event object and properties
- ✅ Event bubbling and capturing
- ✅ Event delegation
- ✅ preventDefault() and stopPropagation()
- ✅ Keyboard events
- ✅ Mouse events
- ✅ Form events
- ✅ Custom events

---

## 🎯 Assignment Objectives

Create an **Interactive Game Dashboard** with multiple event-driven mini-games and demos.

**Difficulty**: ⭐⭐⭐☆☆  
**Time**: 5-6 hours  
**Prerequisites**: Assignments 1-4 completed

---

## 📋 Requirements

### Must Have
1. ✅ Click counter game
2. ✅ Keyboard event handler
3. ✅ Mouse tracker
4. ✅ Drag and drop demo
5. ✅ Form validation with events
6. ✅ Event bubbling demonstration
7. ✅ Event delegation example
8. ✅ Scroll events
9. ✅ Custom events
10. ✅ Interactive UI

---

## 💻 Complete Implementation

### HTML (index.html)
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Event Handling Demo</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>🎮 Event Handling Games</h1>
        
        <!-- Click Counter -->
        <section class="game-section">
            <h2>1. Click Counter Game</h2>
            <p>Click as many times as you can in 10 seconds!</p>
            <button id="clickBtn" class="game-btn">Click Me!</button>
            <div class="score-display">
                <p>Clicks: <span id="clickCount">0</span></p>
                <p>Time: <span id="timeLeft">10</span>s</p>
                <p>Best: <span id="bestScore">0</span></p>
            </div>
            <button id="startBtn" class="start-btn">Start Game</button>
        </section>
        
        <!-- Keyboard Events -->
        <section class="game-section">
            <h2>2. Keyboard Events</h2>
            <p>Type in the box below:</p>
            <input type="text" id="keyInput" placeholder="Type here..." class="key-input">
            <div id="keyInfo" class="info-box"></div>
            <div id="keysPressed" class="keys-display"></div>
        </section>
        
        <!-- Mouse Tracker -->
        <section class="game-section">
            <h2>3. Mouse Tracker</h2>
            <div id="mouseArea" class="mouse-area">
                Move your mouse here!
                <div id="cursor" class="custom-cursor"></div>
            </div>
            <div id="mouseInfo" class="info-box"></div>
        </section>
        
        <!-- Drag and Drop -->
        <section class="game-section">
            <h2>4. Drag and Drop</h2>
            <div class="drag-container">
                <div class="drag-source">
                    <div class="drag-item" draggable="true" data-color="red">🔴 Red</div>
                    <div class="drag-item" draggable="true" data-color="blue">🔵 Blue</div>
                    <div class="drag-item" draggable="true" data-color="green">🟢 Green</div>
                </div>
                <div class="drop-zone" data-accepts="red">Red Zone</div>
                <div class="drop-zone" data-accepts="blue">Blue Zone</div>
                <div class="drop-zone" data-accepts="green">Green Zone</div>
            </div>
        </section>
        
        <!-- Form Validation -->
        <section class="game-section">
            <h2>5. Form Events & Validation</h2>
            <form id="demoForm" class="demo-form">
                <input type="text" id="username" placeholder="Username (min 3 chars)" required>
                <span class="validation-msg" id="usernameMsg"></span>
                
                <input type="email" id="email" placeholder="Email" required>
                <span class="validation-msg" id="emailMsg"></span>
                
                <input type="password" id="password" placeholder="Password (min 6 chars)" required>
                <span class="validation-msg" id="passwordMsg"></span>
                
                <button type="submit" class="submit-btn">Submit</button>
            </form>
            <div id="formOutput" class="output"></div>
        </section>
        
        <!-- Event Bubbling -->
        <section class="game-section">
            <h2>6. Event Bubbling & Capturing</h2>
            <div id="outer" class="bubble-box outer">
                Outer
                <div id="middle" class="bubble-box middle">
                    Middle
                    <div id="inner" class="bubble-box inner">
                        Inner (Click me!)
                    </div>
                </div>
            </div>
            <div id="bubbleOutput" class="output"></div>
            <button onclick="clearBubbleLog()">Clear Log</button>
        </section>
        
        <!-- Event Delegation -->
        <section class="game-section">
            <h2>7. Event Delegation</h2>
            <button onclick="addListItem()">Add Item</button>
            <ul id="itemList" class="item-list"></ul>
            <p class="info">Click any item to toggle it!</p>
        </section>
        
        <!-- Scroll Events -->
        <section class="game-section">
            <h2>8. Scroll Events</h2>
            <div id="scrollArea" class="scroll-area">
                <div class="scroll-content">
                    Scroll me! This is a long content area that demonstrates scroll events.
                    You'll see the scroll position update below.
                </div>
            </div>
            <div id="scrollInfo" class="info-box"></div>
        </section>
    </div>
    
    <script src="script.js"></script>
</body>
</html>
```

### JavaScript (script.js)
```javascript
// ===== 1. CLICK COUNTER GAME =====
let clickCount = 0;
let gameActive = false;
let timeLeft = 10;
let bestScore = localStorage.getItem('bestScore') || 0;
let gameTimer;

const clickBtn = document.getElementById('clickBtn');
const startBtn = document.getElementById('startBtn');
const clickCountDisplay = document.getElementById('clickCount');
const timeLeftDisplay = document.getElementById('timeLeft');
const bestScoreDisplay = document.getElementById('bestScore');

bestScoreDisplay.textContent = bestScore;

clickBtn.addEventListener('click', () => {
    if (gameActive) {
        clickCount++;
        clickCountDisplay.textContent = clickCount;
        
        // Visual feedback
        clickBtn.style.transform = 'scale(0.95)';
        setTimeout(() => {
            clickBtn.style.transform = 'scale(1)';
        }, 100);
    }
});

startBtn.addEventListener('click', startGame);

function startGame() {
    clickCount = 0;
    timeLeft = 10;
    gameActive = true;
    
    clickCountDisplay.textContent = '0';
    timeLeftDisplay.textContent = '10';
    startBtn.disabled = true;
    clickBtn.disabled = false;
    
    gameTimer = setInterval(() => {
        timeLeft--;
        timeLeftDisplay.textContent = timeLeft;
        
        if (timeLeft <= 0) {
            endGame();
        }
    }, 1000);
}

function endGame() {
    gameActive = false;
    clearInterval(gameTimer);
    startBtn.disabled = false;
    clickBtn.disabled = true;
    
    if (clickCount > bestScore) {
        bestScore = clickCount;
        bestScoreDisplay.textContent = bestScore;
        localStorage.setItem('bestScore', bestScore);
        alert(`🎉 New Best Score: ${bestScore} clicks!`);
    } else {
        alert(`Game Over! You clicked ${clickCount} times!`);
    }
}

// ===== 2. KEYBOARD EVENTS =====
const keyInput = document.getElementById('keyInput');
const keyInfo = document.getElementById('keyInfo');
const keysPressed = document.getElementById('keysPressed');

let pressedKeys = [];

keyInput.addEventListener('keydown', (e) => {
    keyInfo.innerHTML = `
        <strong>Key Down:</strong><br>
        Key: ${e.key}<br>
        Code: ${e.code}<br>
        KeyCode: ${e.keyCode}<br>
        Shift: ${e.shiftKey}<br>
        Ctrl: ${e.ctrlKey}<br>
        Alt: ${e.altKey}
    `;
    
    // Add key to pressed keys
    if (!pressedKeys.includes(e.key)) {
        pressedKeys.push(e.key);
        updateKeysDisplay();
    }
});

keyInput.addEventListener('keyup', (e) => {
    // Remove key from pressed keys
    pressedKeys = pressedKeys.filter(k => k !== e.key);
    updateKeysDisplay();
});

function updateKeysDisplay() {
    keysPressed.innerHTML = pressedKeys.length > 0
        ? `Currently Pressed: ${pressedKeys.join(', ')}`
        : 'No keys pressed';
}

// ===== 3. MOUSE TRACKER =====
const mouseArea = document.getElementById('mouseArea');
const cursor = document.getElementById('cursor');
const mouseInfo = document.getElementById('mouseInfo');

mouseArea.addEventListener('mousemove', (e) => {
    const rect = mouseArea.getBoundingClientRect();
    const x = e.clientX - rect.left;
    const y = e.clientY - rect.top;
    
    cursor.style.left = x + 'px';
    cursor.style.top = y + 'px';
    
    mouseInfo.innerHTML = `
        <strong>Mouse Position:</strong><br>
        X: ${Math.floor(x)}px<br>
        Y: ${Math.floor(y)}px<br>
        Client X: ${e.clientX}px<br>
        Client Y: ${e.clientY}px
    `;
});

mouseArea.addEventListener('mouseenter', () => {
    cursor.style.display = 'block';
});

mouseArea.addEventListener('mouseleave', () => {
    cursor.style.display = 'none';
});

// ===== 4. DRAG AND DROP =====
const dragItems = document.querySelectorAll('.drag-item');
const dropZones = document.querySelectorAll('.drop-zone');

let draggedItem = null;

dragItems.forEach(item => {
    item.addEventListener('dragstart', (e) => {
        draggedItem = e.target;
        e.target.style.opacity = '0.5';
    });
    
    item.addEventListener('dragend', (e) => {
        e.target.style.opacity = '1';
    });
});

dropZones.forEach(zone => {
    zone.addEventListener('dragover', (e) => {
        e.preventDefault();
        zone.classList.add('drag-over');
    });
    
    zone.addEventListener('dragleave', () => {
        zone.classList.remove('drag-over');
    });
    
    zone.addEventListener('drop', (e) => {
        e.preventDefault();
        zone.classList.remove('drag-over');
        
        const accepts = zone.dataset.accepts;
        const itemColor = draggedItem.dataset.color;
        
        if (accepts === itemColor) {
            zone.appendChild(draggedItem);
            zone.style.background = '#d4edda';
            setTimeout(() => {
                zone.style.background = '';
            }, 1000);
        } else {
            zone.style.background = '#f8d7da';
            setTimeout(() => {
                zone.style.background = '';
            }, 1000);
        }
    });
});

// ===== 5. FORM VALIDATION =====
const demoForm = document.getElementById('demoForm');
const username = document.getElementById('username');
const email = document.getElementById('email');
const password = document.getElementById('password');

// Real-time validation
username.addEventListener('input', () => {
    const msg = document.getElementById('usernameMsg');
    if (username.value.length === 0) {
        msg.textContent = '';
    } else if (username.value.length < 3) {
        msg.textContent = '❌ Too short';
        msg.className = 'validation-msg error';
    } else {
        msg.textContent = '✅ Good';
        msg.className = 'validation-msg success';
    }
});

email.addEventListener('input', () => {
    const msg = document.getElementById('emailMsg');
    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    
    if (email.value.length === 0) {
        msg.textContent = '';
    } else if (!emailRegex.test(email.value)) {
        msg.textContent = '❌ Invalid email';
        msg.className = 'validation-msg error';
    } else {
        msg.textContent = '✅ Valid';
        msg.className = 'validation-msg success';
    }
});

password.addEventListener('input', () => {
    const msg = document.getElementById('passwordMsg');
    if (password.value.length === 0) {
        msg.textContent = '';
    } else if (password.value.length < 6) {
        msg.textContent = '❌ Too short';
        msg.className = 'validation-msg error';
    } else {
        msg.textContent = '✅ Strong';
        msg.className = 'validation-msg success';
    }
});

// Form submit
demoForm.addEventListener('submit', (e) => {
    e.preventDefault();
    
    const output = document.getElementById('formOutput');
    output.innerHTML = `
        <div class="success-msg">
            ✅ Form submitted successfully!<br>
            Username: ${username.value}<br>
            Email: ${email.value}
        </div>
    `;
    
    demoForm.reset();
    document.querySelectorAll('.validation-msg').forEach(msg => msg.textContent = '');
});

// ===== 6. EVENT BUBBLING =====
const outer = document.getElementById('outer');
const middle = document.getElementById('middle');
const inner = document.getElementById('inner');
const bubbleOutput = document.getElementById('bubbleOutput');

let bubbleLog = [];

function logEvent(phase, target) {
    bubbleLog.push(`${phase}: ${target}`);
    bubbleOutput.innerHTML = '<strong>Event Path:</strong><br>' + 
        bubbleLog.map(l => `• ${l}`).join('<br>');
}

inner.addEventListener('click', () => logEvent('Bubble', 'Inner'));
middle.addEventListener('click', () => logEvent('Bubble', 'Middle'));
outer.addEventListener('click', () => logEvent('Bubble', 'Outer'));

function clearBubbleLog() {
    bubbleLog = [];
    bubbleOutput.innerHTML = '';
}

// ===== 7. EVENT DELEGATION =====
const itemList = document.getElementById('itemList');
let itemCount = 0;

function addListItem() {
    itemCount++;
    const li = document.createElement('li');
    li.textContent = `Item ${itemCount}`;
    li.className = 'list-item';
    itemList.appendChild(li);
}

// Event delegation: one listener on parent
itemList.addEventListener('click', (e) => {
    if (e.target.tagName === 'LI') {
        e.target.classList.toggle('active');
    }
});

// Add initial items
for (let i = 0; i < 3; i++) {
    addListItem();
}

// ===== 8. SCROLL EVENTS =====
const scrollArea = document.getElementById('scrollArea');
const scrollInfo = document.getElementById('scrollInfo');

scrollArea.addEventListener('scroll', (e) => {
    const scrollTop = e.target.scrollTop;
    const scrollHeight = e.target.scrollHeight;
    const clientHeight = e.target.clientHeight;
    const scrollPercent = (scrollTop / (scrollHeight - clientHeight)) * 100;
    
    scrollInfo.innerHTML = `
        <strong>Scroll Info:</strong><br>
        Position: ${Math.floor(scrollTop)}px<br>
        Percentage: ${Math.floor(scrollPercent)}%<br>
        Total Height: ${scrollHeight}px
    `;
});

console.log('✅ Event Handling Demo loaded!');
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
    max-width: 1000px;
    margin: 0 auto;
}

h1 {
    color: white;
    text-align: center;
    margin-bottom: 2rem;
    font-size: 2.5rem;
}

.game-section {
    background: white;
    padding: 2rem;
    border-radius: 15px;
    margin-bottom: 2rem;
    box-shadow: 0 10px 30px rgba(0,0,0,0.2);
}

h2 {
    color: #2c3e50;
    margin-bottom: 1rem;
}

.game-btn {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    border: none;
    padding: 2rem 4rem;
    border-radius: 15px;
    font-size: 1.5rem;
    cursor: pointer;
    transition: all 0.3s;
    margin: 1rem 0;
}

.game-btn:hover {
    transform: scale(1.05);
}

.game-btn:disabled {
    opacity: 0.5;
    cursor: not-allowed;
}

.score-display {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem;
    margin: 1rem 0;
}

.score-display p {
    background: #f8f9fa;
    padding: 1rem;
    border-radius: 10px;
    text-align: center;
    font-size: 1.2rem;
}

.start-btn {
    background: #28a745;
    color: white;
    border: none;
    padding: 1rem 2rem;
    border-radius: 10px;
    font-size: 1rem;
    cursor: pointer;
    transition: all 0.3s;
}

.start-btn:hover {
    background: #218838;
}

.key-input {
    width: 100%;
    padding: 1rem;
    border: 2px solid #667eea;
    border-radius: 10px;
    font-size: 1.2rem;
    margin-bottom: 1rem;
}

.info-box {
    background: #f8f9fa;
    padding: 1rem;
    border-radius: 10px;
    border-left: 4px solid #667eea;
    margin-top: 1rem;
}

.keys-display {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    padding: 1rem;
    border-radius: 10px;
    margin-top: 1rem;
    text-align: center;
    font-weight: bold;
}

.mouse-area {
    position: relative;
    height: 300px;
    background: linear-gradient(135deg, #e0c3fc 0%, #8ec5fc 100%);
    border-radius: 15px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.5rem;
    color: #fff;
    cursor: none;
}

.custom-cursor {
    position: absolute;
    width: 20px;
    height: 20px;
    background: red;
    border-radius: 50%;
    pointer-events: none;
    transform: translate(-50%, -50%);
    display: none;
}

.drag-container {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 1rem;
}

.drag-source {
    grid-column: 1;
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
}

.drag-item {
    padding: 1rem;
    background: #f8f9fa;
    border: 2px solid #ddd;
    border-radius: 10px;
    cursor: move;
    text-align: center;
    font-weight: bold;
}

.drop-zone {
    padding: 2rem;
    border: 3px dashed #ddd;
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.3s;
}

.drop-zone.drag-over {
    border-color: #667eea;
    background: #f0f7ff;
}

.demo-form {
    display: flex;
    flex-direction: column;
    gap: 1rem;
}

.demo-form input {
    padding: 1rem;
    border: 2px solid #ddd;
    border-radius: 10px;
    font-size: 1rem;
}

.validation-msg {
    font-size: 0.9rem;
    margin-top: -0.5rem;
}

.validation-msg.error {
    color: #dc3545;
}

.validation-msg.success {
    color: #28a745;
}

.submit-btn {
    background: #667eea;
    color: white;
    border: none;
    padding: 1rem;
    border-radius: 10px;
    font-size: 1rem;
    cursor: pointer;
    transition: all 0.3s;
}

.submit-btn:hover {
    background: #764ba2;
}

.output {
    margin-top: 1rem;
    padding: 1rem;
    background: #f8f9fa;
    border-radius: 10px;
}

.success-msg {
    background: #d4edda;
    color: #155724;
    padding: 1rem;
    border-radius: 10px;
}

.bubble-box {
    padding: 2rem;
    border: 3px solid;
    border-radius: 10px;
    margin: 1rem;
    cursor: pointer;
    transition: all 0.3s;
}

.bubble-box:hover {
    transform: scale(1.02);
}

.outer {
    border-color: #dc3545;
    background: #fff5f5;
}

.middle {
    border-color: #ffc107;
    background: #fffbf0;
}

.inner {
    border-color: #28a745;
    background: #f0fff4;
}

.item-list {
    list-style: none;
    margin-top: 1rem;
}

.list-item {
    padding: 1rem;
    background: #f8f9fa;
    border: 2px solid #ddd;
    border-radius: 10px;
    margin-bottom: 0.5rem;
    cursor: pointer;
    transition: all 0.3s;
}

.list-item:hover {
    background: #e9ecef;
}

.list-item.active {
    background: #667eea;
    color: white;
}

.scroll-area {
    height: 200px;
    overflow-y: scroll;
    border: 2px solid #ddd;
    border-radius: 10px;
    padding: 1rem;
}

.scroll-content {
    height: 600px;
    background: linear-gradient(to bottom, #667eea, #764ba2, #667eea);
    padding: 2rem;
    color: white;
    border-radius: 10px;
}

@media (max-width: 768px) {
    .drag-container {
        grid-template-columns: 1fr;
    }
    
    .score-display {
        grid-template-columns: 1fr;
    }
}
```

---

## 📖 Key Concepts

### Event Types
```javascript
// Mouse Events
element.addEventListener('click', handler);
element.addEventListener('dblclick', handler);
element.addEventListener('mouseenter', handler);
element.addEventListener('mouseleave', handler);
element.addEventListener('mousemove', handler);

// Keyboard Events
element.addEventListener('keydown', handler);
element.addEventListener('keyup', handler);
element.addEventListener('keypress', handler);

// Form Events
form.addEventListener('submit', handler);
input.addEventListener('input', handler);
input.addEventListener('change', handler);
input.addEventListener('focus', handler);
input.addEventListener('blur', handler);
```

### Event Delegation
```javascript
// Instead of many listeners
buttons.forEach(btn => btn.addEventListener('click', handler));

// One listener on parent
parent.addEventListener('click', (e) => {
    if (e.target.matches('.btn')) {
        // Handle click
    }
});
```

---

## ✅ Self-Assessment

- [ ] Click counter game works
- [ ] Keyboard events captured
- [ ] Mouse tracker works
- [ ] Drag and drop functional
- [ ] Form validation working
- [ ] Event bubbling demonstrated
- [ ] Event delegation works
- [ ] Scroll events tracked
- [ ] All interactive elements respond
- [ ] Code is well-organized

---

**Next**: [Assignment 6: ES6 Features](../assignment-06-es6-features/ASSIGNMENT_6_GUIDE.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

