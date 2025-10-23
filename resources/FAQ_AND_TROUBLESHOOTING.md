# FAQ & Troubleshooting Guide

**By Mahendra Bagul**

Common questions and solutions for the React Learning Path.

---

## 🤔 General Questions

### Q: I've never coded before. Can I really do this?

**A: Absolutely!** This course is designed for complete beginners. Start with Phase 1, Assignment 1, and follow the guides step-by-step. Thousands of developers started exactly where you are.

### Q: How long will it take to complete?

**A:**
- **Part-time (6-8 hrs/week)**: ~60 weeks (15 months)
- **Committed (10-15 hrs/week)**: ~50 weeks (12 months)
- **Intensive (20-30 hrs/week)**: ~30 weeks (7 months)

### Q: Do I need a powerful computer?

**A: No!** Any computer from the last 5-10 years will work fine. You just need:
- A web browser
- A text editor (VS Code)
- 4GB+ RAM recommended

### Q: Can I skip phases or assignments?

**A: Not recommended.** Each phase builds on the previous one. Skipping creates knowledge gaps that cause problems later.

### Q: When can I start applying for jobs?

**A:**
- After Phase 3 (JavaScript): Junior/Intern positions possible
- After Phase 4 (TypeScript): Better job prospects
- After Phase 5 (React): Ready for Junior React Developer roles

### Q: Do I need to memorize everything?

**A: No!** Professional developers Google things constantly. Focus on understanding concepts, not memorizing syntax.

---

## 💻 Setup & Installation Issues

### Problem: "command not found" errors

**Solution:**
1. Restart your terminal/command prompt
2. If still failing, restart your computer
3. Verify installation with `--version` commands

### Problem: Node.js not found after installation

**Windows:**
```bash
# Add to PATH:
1. Search "Environment Variables"
2. Edit "Path"
3. Add: C:\Program Files\nodejs\
4. Restart terminal
```

**Mac:**
```bash
# Reinstall using installer
# Restart Terminal
```

**Linux:**
```bash
# Use package manager
sudo apt-get install nodejs npm  # Ubuntu
```

### Problem: VS Code extensions not working

**Solution:**
1. Reload VS Code: Ctrl+Shift+P → "Reload Window"
2. Reinstall extension
3. Check if extension is enabled

### Problem: Live Server not launching

**Solution:**
1. Right-click HTML file → "Open with Live Server"
2. Or click "Go Live" button (bottom-right)
3. Make sure HTML file is saved
4. Check if port 5500 is available

---

## 📝 HTML Issues

### Problem: HTML file shows blank page

**Checklist:**
- [ ] File saved with .html extension?
- [ ] Doctype declared: `<!DOCTYPE html>`?
- [ ] HTML structure correct?
- [ ] Check browser console for errors (F12)

### Problem: Images not showing

**Solutions:**
- Check file path is correct
- Use relative paths: `./images/photo.jpg`
- Verify image file exists
- Check file extension matches exactly

### Problem: Links not working

**Solutions:**
- Check href attribute: `<a href="page.html">`
- For same folder: `href="page.html"`
- For parent folder: `href="../page.html"`
- For external: `href="https://example.com"`

---

## 🎨 CSS Issues

### Problem: Styles not applying

**Checklist:**
- [ ] CSS file linked in HTML? `<link rel="stylesheet" href="styles.css">`
- [ ] CSS file in correct location?
- [ ] Selector spelled correctly?
- [ ] Check browser DevTools (F12) → Elements → Styles
- [ ] Clear browser cache (Ctrl+Shift+Delete)

### Problem: Flexbox/Grid not working

**Solutions:**
- Parent must have `display: flex` or `display: grid`
- Check child elements are direct children
- Use browser DevTools to inspect

### Problem: Responsive design not working

**Solutions:**
- Add viewport meta tag:
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
- Test using browser DevTools → Toggle device toolbar
- Use relative units (%, em, rem) not fixed (px)

---

## ⚡ JavaScript Issues

### Problem: JavaScript not running

**Checklist:**
- [ ] Script tag added? `<script src="script.js"></script>`
- [ ] Script tag at end of body?
- [ ] Check console for errors (F12 → Console)
- [ ] File path correct?

### Problem: "Uncaught ReferenceError"

**Cause:** Variable/function not defined

**Solutions:**
- Check spelling
- Declare before using: `let variable = value;`
- Check scope (is variable accessible?)

### Problem: "Uncaught TypeError"

**Cause:** Wrong type or null/undefined

**Solutions:**
- Check if variable exists before using
- Use typeof to check type
- Add error handling

### Problem: Event listener not working

**Solutions:**
- Check element exists in DOM
- Use correct event name ('click' not 'onclick')
- Check selector is correct
- Put script after HTML or use DOMContentLoaded

```javascript
document.addEventListener('DOMContentLoaded', () => {
    // Your code here
});
```

---

## 📘 TypeScript Issues

### Problem: TypeScript not compiling

**Solutions:**
- Check tsconfig.json exists
- Run `tsc` in terminal
- Check for syntax errors
- Install TypeScript: `npm install -g typescript`

### Problem: Type errors everywhere

**Solutions:**
- Add type annotations
- Use `any` temporarily (not recommended)
- Check TypeScript documentation
- Enable strict mode gradually

### Problem: "Cannot find module"

**Solutions:**
- Check import path
- Install dependencies: `npm install`
- Check tsconfig.json paths
- Restart VS Code

---

## ⚛️ React Issues

### Problem: "npm start" fails

**Solutions:**
- Delete `node_modules` and `package-lock.json`
- Run `npm install` again
- Check Node.js version (use LTS)
- Try `npm cache clean --force`

### Problem: Component not rendering

**Checklist:**
- [ ] Component imported correctly?
- [ ] Component exported? `export default Component`
- [ ] Component name capitalized?
- [ ] Return statement present?
- [ ] JSX wrapped in single parent?

### Problem: State not updating

**Solutions:**
- Never mutate state directly
- Use setState or useState setter
- For arrays/objects, create new copies
```javascript
// ❌ Wrong
array.push(item);

// ✅ Correct
setArray([...array, item]);
```

### Problem: "Too many re-renders"

**Cause:** Infinite loop in useEffect or setState

**Solutions:**
- Add dependency array to useEffect
- Don't call setState in render
- Check for infinite loops

---

## 🔧 Common Errors

### SyntaxError

**Cause:** Invalid JavaScript syntax

**Solutions:**
- Check for missing brackets/parentheses
- Check for missing commas
- Use linter (ESLint)

### CORS Error

**Cause:** Trying to access API from file://

**Solutions:**
- Use Live Server or local server
- Don't open HTML directly from file system
- API may need CORS enabled

### 404 Not Found

**Cause:** File or resource doesn't exist

**Solutions:**
- Check file path
- Verify file exists
- Check spelling exactly

---

## 🆘 Debugging Tips

### Use Console.log

```javascript
console.log('Check value:', variable);
console.log('Function called');
```

### Use Browser DevTools

- **F12** - Open DevTools
- **Console** - See errors and logs
- **Elements** - Inspect HTML/CSS
- **Network** - Check API calls
- **Sources** - Debug JavaScript

### Read Error Messages

Error messages tell you:
- What went wrong
- Where it happened (file and line)
- Sometimes how to fix it

**Don't panic!** Read carefully.

### Google the Error

Copy error message → Google it

Likely someone else had the same problem!

Resources:
- Stack Overflow
- MDN Web Docs
- GitHub Issues

---

## 📚 Learning Tips

### Stuck on a Concept?

1. Re-read the guide
2. Try the example code yourself
3. Break it down into smaller pieces
4. Take a break, come back fresh
5. Search online for different explanations

### Code Not Working?

1. Read error message carefully
2. Check console for errors (F12)
3. console.log to check values
4. Comment out code to isolate issue
5. Start fresh with simple version

### Feeling Overwhelmed?

1. Take a break - you're not a machine
2. Review previous assignment
3. Break complex task into small steps
4. Remember: confusion means you're learning
5. Progress > Perfection

---

## 🌐 Helpful Resources

### Documentation
- **MDN Web Docs**: https://developer.mozilla.org/
- **React Docs**: https://react.dev/
- **TypeScript Handbook**: https://www.typescriptlang.org/docs/

### Q&A
- **Stack Overflow**: https://stackoverflow.com/
- **Reddit**: r/learnprogramming, r/webdev

### Tools
- **Can I Use**: https://caniuse.com/ (Browser support)
- **CodePen**: https://codepen.io/ (Test code online)
- **JSFiddle**: https://jsfiddle.net/ (Test code online)

---

## 💬 Still Stuck?

If you've tried everything and still stuck:

1. **Take a break** - Fresh eyes see solutions
2. **Start over** - Sometimes easiest solution
3. **Skip temporarily** - Come back later
4. **Ask in communities** - r/learnprogramming, Discord servers
5. **Check solution** - Learn from it, don't just copy

**Remember:** Every developer gets stuck. It's part of the process!

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

---

<div align="center">

**Still have questions?** → Open an issue on GitHub

**Found a solution not listed?** → Contribute it!

</div>

