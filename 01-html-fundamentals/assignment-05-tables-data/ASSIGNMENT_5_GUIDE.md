# Assignment 5: Tables & Data - Organizing Information

**By Mahendra Bagul**

Tables are perfect for displaying structured data - schedules, statistics, comparisons, pricing. Learn to present data clearly and accessibly.

---

## 📚 What You'll Learn

- ✅ Table structure (`<table>`, `<tr>`, `<td>`, `<th>`)
- ✅ Table headers (`<thead>`, `<tbody>`, `<tfoot>`)
- ✅ Colspan and rowspan
- ✅ Table captions
- ✅ Accessible tables
- ✅ Data organization

---

## 🎯 Assignment Objectives

Create a "Sports Statistics Dashboard" with multiple data tables showing team standings, player stats, and schedules.

**Difficulty**: ⭐⭐⭐☆☆  
**Time**: 3-4 hours  
**Prerequisites**: Assignments 1-4

---

## 📋 Requirements

### Must Have
1. ✅ At least 3 different tables
2. ✅ Proper table headers (`<th>`)
3. ✅ Use of `<thead>`, `<tbody>`, `<tfoot>`
4. ✅ At least 1 table with colspan
5. ✅ At least 1 table with rowspan
6. ✅ Table captions
7. ✅ At least 15 rows of real data

---

## 💻 Key HTML Elements

### Basic Table
```html
<table>
    <caption>Team Standings</caption>
    <thead>
        <tr>
            <th>Team</th>
            <th>Wins</th>
            <th>Losses</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Red Team</td>
            <td>15</td>
            <td>5</td>
        </tr>
        <tr>
            <td>Blue Team</td>
            <td>12</td>
            <td>8</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td>Total</td>
            <td>27</td>
            <td>13</td>
        </tr>
    </tfoot>
</table>
```

### Colspan (Merge Columns)
```html
<tr>
    <th colspan="3">Player Statistics</th>
</tr>
```

### Rowspan (Merge Rows)
```html
<tr>
    <td rowspan="2">John Doe</td>
    <td>Monday</td>
</tr>
<tr>
    <td>Tuesday</td>
</tr>
```

---

## 🏗️ Example Tables

### 1. Team Standings Table
- Columns: Rank, Team, Played, Won, Lost, Points
- At least 8 teams

### 2. Player Statistics Table  
- Columns: Player, Goals, Assists, Total Points
- At least 10 players

### 3. Match Schedule Table
- Columns: Date, Time, Home Team, Away Team, Venue
- Use colspan for section headers

---

## ✅ Self-Assessment

- [ ] Created 3+ tables with real data
- [ ] Used `<thead>`, `<tbody>`, `<tfoot>` correctly
- [ ] All tables have captions
- [ ] Used `<th>` for headers
- [ ] Implemented colspan correctly
- [ ] Implemented rowspan correctly
- [ ] Tables are readable and organized
- [ ] Data is meaningful and realistic

---

## 💡 Table Best Practices

1. **Always use `<th>` for headers** - Important for accessibility
2. **Add captions** - Explains what the table shows
3. **Keep tables simple** - Complex layouts confuse users
4. **Use thead/tbody/tfoot** - Semantic structure
5. **Don't use tables for layout** - That's CSS's job!

---

**Next**: [Assignment 6: Forms Basics](../assignment-06-forms-basics/ASSIGNMENT_6_GUIDE.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

