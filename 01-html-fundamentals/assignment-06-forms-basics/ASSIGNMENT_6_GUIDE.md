# Assignment 6: Forms Basics - User Input

**By Mahendra Bagul**

Forms are how users interact with websites - login, signup, contact, search, everything! Master forms and you unlock interactivity.

---

## 📚 What You'll Learn

- ✅ Form structure (`<form>`)
- ✅ Input types (text, email, password, number, date, etc.)
- ✅ Textarea, select, checkbox, radio buttons
- ✅ Labels and fieldsets
- ✅ HTML5 validation
- ✅ Form attributes (required, placeholder, pattern)
- ✅ Submit and reset buttons

---

## 🎯 Assignment Objectives

Create a "Multi-Page Registration System" with signup form, contact form, and survey form.

**Difficulty**: ⭐⭐⭐⭐☆  
**Time**: 4-5 hours  
**Prerequisites**: Assignments 1-5

---

## 📋 Requirements

### Must Have
1. ✅ At least 3 forms (signup, contact, survey)
2. ✅ Use 10+ different input types
3. ✅ Proper labels for all inputs
4. ✅ At least 1 fieldset with legend
5. ✅ HTML5 validation (required, email, etc.)
6. ✅ Textarea for long text
7. ✅ Dropdown select menus
8. ✅ Radio buttons (at least one group)
9. ✅ Checkboxes (at least 3)
10. ✅ Submit buttons

---

## 💻 Key HTML Elements

### Form Structure
```html
<form action="/submit" method="POST">
    <label for="username">Username:</label>
    <input type="text" id="username" name="username" required>
    
    <button type="submit">Submit</button>
</form>
```

### Input Types
```html
<!-- Text input -->
<input type="text" name="name" required>

<!-- Email (with validation) -->
<input type="email" name="email" required>

<!-- Password -->
<input type="password" name="password" minlength="8" required>

<!-- Number -->
<input type="number" name="age" min="18" max="100">

<!-- Date -->
<input type="date" name="birthdate">

<!-- Checkbox -->
<input type="checkbox" name="agree" id="agree" required>
<label for="agree">I agree to terms</label>

<!-- Radio buttons -->
<input type="radio" name="gender" value="male" id="male">
<label for="male">Male</label>
<input type="radio" name="gender" value="female" id="female">
<label for="female">Female</label>

<!-- Textarea -->
<textarea name="message" rows="5" cols="40"></textarea>

<!-- Select dropdown -->
<select name="country">
    <option value="">Choose...</option>
    <option value="us">United States</option>
    <option value="uk">United Kingdom</option>
</select>
```

### Fieldset & Legend
```html
<fieldset>
    <legend>Personal Information</legend>
    <!-- Form fields here -->
</fieldset>
```

---

## 🏗️ Implementation Examples

### 1. Signup Form
```html
<form>
    <h2>Create Account</h2>
    
    <label for="fullname">Full Name:</label>
    <input type="text" id="fullname" required>
    
    <label for="email">Email:</label>
    <input type="email" id="email" required>
    
    <label for="password">Password:</label>
    <input type="password" id="password" minlength="8" required>
    
    <label for="confirm-password">Confirm Password:</label>
    <input type="password" id="confirm-password" required>
    
    <label for="dob">Date of Birth:</label>
    <input type="date" id="dob" required>
    
    <button type="submit">Sign Up</button>
</form>
```

### 2. Contact Form
```html
<form>
    <label for="name">Name:</label>
    <input type="text" id="name" required>
    
    <label for="email">Email:</label>
    <input type="email" id="email" required>
    
    <label for="subject">Subject:</label>
    <select id="subject">
        <option value="general">General Inquiry</option>
        <option value="support">Support</option>
        <option value="feedback">Feedback</option>
    </select>
    
    <label for="message">Message:</label>
    <textarea id="message" rows="6" required></textarea>
    
    <button type="submit">Send Message</button>
</form>
```

---

## ✅ Self-Assessment

- [ ] Created 3+ functional forms
- [ ] All inputs have proper labels
- [ ] Used 10+ different input types
- [ ] HTML5 validation working (required, email, etc.)
- [ ] Radio buttons grouped correctly (same name)
- [ ] Checkboxes work independently
- [ ] Fieldsets organize related inputs
- [ ] Forms are accessible (labels linked to inputs)

---

## 🐛 Common Mistakes

**1. Missing Labels**
- Always associate labels with inputs using `for` and `id`

**2. Wrong Input Types**
- Use `type="email"` for emails (gets validation!)
- Use `type="number"` for numbers

**3. Radio Buttons Not Grouped**
- Same `name` attribute groups radio buttons

---

**Next**: [Assignment 7: Semantic HTML](../assignment-07-semantic-html/ASSIGNMENT_7_GUIDE.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

