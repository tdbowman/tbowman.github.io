# Block 2: Data Structures & Meaningful Computation

**Duration:** Weeks 5-7 (Late September - Mid October)  
**Core Question:** *How do programs manage and interpret information?*

---

## 🎯 Block Themes

This block shifts from "how to write code" to "how to work with data." You'll learn to organize, store, and process information using Python's powerful data structures.

Data is everywhere—in files, databases, APIs, and user input. Block 2 teaches you to structure, manipulate, and extract meaning from data, which is the foundation of real-world programming.

---

## 📚 What You'll Learn

### Core Competencies
- **Work with real data** - Not just toy examples
- **Pattern recognition** - See structure in information
- **Data-driven logic** - Make decisions based on data
- **Choose appropriate structures** - Lists, tuples, or dictionaries?
- **Organize complex programs** - Multiple files and modules

### Technical Skills
✅ Loops (for and while)  
✅ Lists and list methods  
✅ Tuples and immutability  
✅ Dictionaries and key-value pairs  
✅ Nested data structures  
✅ Importing and creating modules  
✅ File I/O operations  

---

## 📅 Weekly Topics

### [Week 5: Loops](../week05/overview.md)
- For loops with `range()` and `enumerate()`
- While loops for conditional repetition
- Loop control (`break`, `continue`, `else`)
- Nested loops
- Common patterns (accumulator, search, filter)

**Key Concept:** Loops automate repetition—computers excel at this

### [Week 6: Lists & Tuples](../week06/overview.md)
- Creating and manipulating lists
- List methods (`append`, `insert`, `remove`, `pop`, `sort`)
- List comprehensions
- Tuples and when to use them
- Choosing between lists and tuples

**Key Concept:** Lists are mutable (changeable), tuples are immutable (fixed)

### [Week 7: Dictionaries](../week07/overview.md)
- Key-value pairs and dictionary operations
- Dictionary methods (`.get()`, `.keys()`, `.values()`, `.items()`)
- Nested dictionaries
- Dictionary comprehensions
- Combining dictionaries with lists
- **MIDTERM EXAM** (covers Blocks 1-2)

**Key Concept:** Dictionaries connect related information using meaningful keys

---

## 📝 Assignments in This Block

### Interactive Exercises
- **Exercise 4** - Loop the Loop *(Week 5)*
- **Exercise 5** - Dictionary Delve *(Week 7)*

### Programming Assignments
- **Assignment 2** - Assigned Week 8 *(Due Week 11)*
  - Apply data structures to real problems
  - Work with files and structured data

### Projects
- **Group Project Idea** - Due Week 7
  - Propose a data-driven project
  - Form teams and plan approach

### Assessments
- **MIDTERM EXAM** - Week 7
  - Covers Blocks 1-2 (Weeks 1-6)
  - Programming fundamentals
  - Data structures and loops

---

## 🎯 Skills You'll Lock In

By the end of Block 2, you will be able to:

### Working with Real Data
- Read data from multiple sources
- Clean and validate data
- Transform data between formats
- Extract insights from structured information

### Pattern Recognition
- Identify repeating structures
- Design loops for different scenarios
- Choose appropriate data structures
- Optimize data organization

### Data-Driven Logic
- Make decisions based on data
- Filter and search collections
- Aggregate and summarize information
- Connect related data meaningfully

---

## 🌟 Why This Block Matters

**Block 2 makes your programs useful.** Real applications process data:

### Real-World Examples
- **Web apps** store user data in dictionaries
- **Data science** analyzes lists of measurements
- **APIs** return JSON (which maps to Python dicts)
- **Databases** organize data in structured formats

### Building on Block 1
You now have the foundation (Block 1). Block 2 gives you the tools to:
- Store collections of information (lists, tuples, dicts)
- Process data at scale (loops)
- Organize complex programs (modules)

### Preparing for Block 3
Block 3 connects to external systems. You'll need to:
- Parse JSON data (uses dictionaries!)
- Query databases (returns lists of records!)
- Process API responses (loops through results!)

---

## 💡 Tips for Success

### Week by Week Strategy

**Week 5:** Master loops before moving on—everything uses them  
**Week 6:** Practice list methods until they're second nature  
**Week 7:** Prepare for midterm by reviewing Blocks 1-2  

### Study Habits
1. **Work with real data** - Download CSV files, process text files
2. **Draw diagrams** - Visualize data structures on paper
3. **Practice selecting structures** - When to use list vs dict vs tuple?
4. **Build mini-projects** - Grade calculator, contact list, todo app
5. **Prepare for midterm** - Review all exercises from Weeks 1-6

### Common Patterns to Master

**Accumulator Pattern** (counting/summing):
```python
total = 0
for item in items:
    total += item
```

**Search Pattern** (finding items):
```python
for item in items:
    if item meets criteria:
        return item
```

**Filter Pattern** (selecting items):
```python
results = [item for item in items if condition]
```

**Dictionary Pattern** (grouping):
```python
groups = {}
for item in items:
    key = item["category"]
    if key not in groups:
        groups[key] = []
    groups[key].append(item)
```

---

## 🎓 Midterm Preparation Guide

### Topics Covered (Weeks 1-6)

**Week 1-2:** Foundations
- Variables, data types, operators
- Conditionals (if/elif/else)
- String manipulation

**Week 3-4:** Functions
- Function definition and calls
- Parameters and returns
- Scope and documentation

**Week 5-6:** Data Structures
- Loops (for and while)
- Lists and tuples
- List methods and operations

### How to Prepare
1. **Review all exercises** - Make sure you can solve them
2. **Practice writing functions** - Common exam task
3. **Master loops** - Be able to write them from scratch
4. **Understand data structures** - Know when to use each type
5. **Work through past problems** - See patterns in questions

### Study Resources
- Textbook exercises (with auto-grading!)
- Programming assignments
- Weekly discussion examples
- Instructor office hours

---

## 🚀 Getting Started

**Continue from Block 1:** [Week 5: Loops](../week05/overview.md)

**Or review:** [Block 1: Foundations](../block01/overview.md)

---

## 📊 Block Structure

```
Block 2: Data Structures & Meaningful Computation
├── Week 5: Loops
├── Week 6: Lists & Tuples
└── Week 7: Dictionaries + MIDTERM

Previous: Block 1 ← Foundations
Next: Block 3 → Systems & Integration
```

---

**Remember:** Data structures aren't just syntax—they're ways of thinking about information. Choosing the right structure makes everything easier.

**Ready to work with data?** Let's go! 📊
