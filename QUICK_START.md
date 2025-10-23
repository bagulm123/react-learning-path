# Quick Start Guide - Setup Your Environment

**By Mahendra Bagul**

This guide will help you set up your computer for web development in under 30 minutes!

---

## 🎯 What You'll Install

1. **Web Browser** (Chrome or Firefox)
2. **Code Editor** (VS Code)
3. **Node.js** (For JavaScript/React)
4. **Git** (Version control)

All software is FREE and works on Windows, Mac, and Linux!

---

## 🌐 Step 1: Install a Modern Browser

### Google Chrome (Recommended)
1. Go to: https://www.google.com/chrome/
2. Click "Download Chrome"
3. Install and set as default browser

**Why Chrome?** Best DevTools for web development.

### OR Firefox Developer Edition
1. Go to: https://www.mozilla.org/firefox/developer/
2. Download and install

---

## 💻 Step 2: Install VS Code

**Visual Studio Code** is the most popular code editor.

### Installation:
1. Visit: https://code.visualstudio.com/
2. Download for your operating system
3. Install with default settings
4. Launch VS Code

### Essential VS Code Extensions:

Open VS Code, click Extensions (sidebar), and install:

1. **Live Server** - Launch local development server
2. **Prettier** - Code formatter
3. **ESLint** - JavaScript linter
4. **HTML CSS Support** - Better HTML/CSS editing
5. **Auto Rename Tag** - Auto rename HTML tags

---

## 📦 Step 3: Install Node.js

Node.js lets you run JavaScript outside the browser.

### Installation:
1. Visit: https://nodejs.org/
2. Download **LTS** version (Long Term Support)
3. Install with default settings
4. Verify installation:

**Windows:**
```bash
# Open Command Prompt (cmd) and type:
node --version
npm --version
```

**Mac/Linux:**
```bash
# Open Terminal and type:
node --version
npm --version
```

You should see version numbers (e.g., v20.x.x).

---

## 🔧 Step 4: Install Git

Git helps you save and track changes to your code.

### Installation:

**Windows:**
1. Visit: https://git-scm.com/
2. Download and install
3. Use default settings
4. Verify: `git --version` in Command Prompt

**Mac:**
Git is pre-installed! Verify: `git --version` in Terminal

**Linux:**
```bash
sudo apt-get install git  # Ubuntu/Debian
sudo yum install git       # CentOS/Fedora
```

### Configure Git:
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

---

## 📁 Step 5: Create Project Folder

### Windows:
1. Open File Explorer
2. Navigate to Documents
3. Create folder: `web-dev-projects`
4. Inside, create:
   - `html-projects`
   - `css-projects`
   - `javascript-projects`
   - `typescript-projects`
   - `react-projects`

### Mac/Linux:
```bash
mkdir -p ~/web-dev-projects/{html,css,javascript,typescript,react}-projects
```

---

## ✅ Verify Your Setup

### Check All Installations:

```bash
# Browser - Open Chrome or Firefox
# Should work!

# VS Code - Type in terminal:
code --version

# Node.js
node --version

# npm
npm --version

# Git
git --version
```

**All commands should show version numbers!**

---

## 🎨 VS Code Settings (Optional but Recommended)

Open VS Code Settings (Ctrl+, or Cmd+,):

```json
{
  "editor.fontSize": 14,
  "editor.tabSize": 2,
  "editor.wordWrap": "on",
  "editor.formatOnSave": true,
  "editor.minimap.enabled": false,
  "files.autoSave": "afterDelay",
  "liveServer.settings.donotShowInfoMsg": true
}
```

---

## 🚀 Create Your First File

Let's test everything works!

### Create Hello World:

1. Open VS Code
2. File → Open Folder → Select `html-projects`
3. Create new file: `test.html`
4. Type:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Test</title>
</head>
<body>
    <h1>Hello, World!</h1>
    <p>Setup successful!</p>
</body>
</html>
```

5. Right-click file → "Open with Live Server"
6. Browser opens → You should see "Hello, World!"

**✅ Success!** You're ready to code!

---

## 🆘 Troubleshooting

### "command not found" errors:
- **Solution**: Restart your terminal/command prompt
- **If still fails**: Restart your computer

### Node/npm not found:
- **Windows**: Add to PATH environment variable
- **Mac**: Use installer, restart Terminal
- **Linux**: Use package manager

### VS Code extensions not working:
- **Solution**: Reload VS Code window (Ctrl+Shift+P → "Reload Window")

### Live Server not working:
- **Solution**: Right-click HTML file → "Open with Live Server"
- **Alternative**: Use "Go Live" button in bottom-right corner

---

## 📚 Optional Tools (Install Later)

### TypeScript (Phase 4):
```bash
npm install -g typescript
```

### Create React App (Phase 5):
```bash
npm install -g create-react-app
```

**Don't install these now!** You'll do it when needed.

---

## ✅ You're Ready!

Your development environment is set up! 🎉

**Next Steps:**
1. Read [GET_STARTED_HERE.md](./GET_STARTED_HERE.md) if you haven't
2. Start [Assignment 1: Hello World](./01-html-fundamentals/assignment-01-hello-world/ASSIGNMENT_1_GUIDE.md)

---

## 🔗 Useful Links

- **VS Code**: https://code.visualstudio.com/docs
- **Node.js**: https://nodejs.org/docs
- **Git**: https://git-scm.com/doc
- **MDN Web Docs**: https://developer.mozilla.org/

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

---

<div align="center">

**Environment ready!** → [Start Learning](./GET_STARTED_HERE.md)

</div>

