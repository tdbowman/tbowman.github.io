# Week 7: Dictionaries

## Overview

Welcome to Week 7! Dictionaries are one of Python's most powerful data structures. They let you store data as key-value pairs, making it easy to organize and retrieve information efficiently.

```{important}
**MIDTERM EXAM THIS WEEK!** 
Be prepared to demonstrate your understanding of concepts from Weeks 1-6.
```

## Learning Objectives

By the end of this week, you will be able to:

- Create and use dictionaries with key-value pairs
- Access, add, modify, and delete dictionary items
- Use dictionary methods effectively
- Iterate through dictionaries
- Nest dictionaries and combine with lists
- Choose appropriate data structures for problems
- Apply dictionaries to real-world scenarios

## Topics Covered

1. **Dictionary Basics**
   - Creating dictionaries
   - Key-value pairs concept
   - Accessing values by key
   - Dictionary mutability

2. **Dictionary Methods**
   - `.get()`, `.keys()`, `.values()`, `.items()`
   - `.update()`, `.pop()`, `.clear()`
   - `.setdefault()`, `dict.fromkeys()`

3. **Working with Dictionaries**
   - Adding and modifying items
   - Deleting items
   - Checking membership with `in`
   - Iterating through keys, values, items

4. **Advanced Techniques**
   - Nested dictionaries
   - Dictionary comprehensions
   - Combining dictionaries with lists
   - Default values and error handling

5. **Practical Applications**
   - Contact management
   - Data lookup tables
   - Configuration settings
   - Counting and categorizing

## Assignments This Week

```{note}
All assignments are due by 11:59 PM on the specified date in Canvas
```

- **Exercise 5** - Dictionary Delve (assigned this week)
- **Assignment 1** - Due this week (Data Processing with Lists and Tuples)
- **Group Project Idea** - Due this week
- **MIDTERM EXAM** - Covers Weeks 1-6
- **Weekly Discussion** - Participate in forum

## Readings

**Required:**
- Mastrodomenico, R. (2022) - Chapter 9 (Dictionaries)
- Parker, J. R. (2021) - Chapter 8 (Dictionaries)
- Speight, A. (2020) - Chapter 8 (Dictionaries)

**Recommended:**
- [Python Dictionaries - W3Schools](https://www.w3schools.com/python/python_dictionaries.asp)
- [Real Python - Dictionaries](https://realpython.com/python-dicts/)

## Key Concepts

```{important}
**Dictionaries use keys instead of indices.** Unlike lists where you access items by position (0, 1, 2...), dictionaries let you access items by meaningful keys ("name", "age", "email").
```

### Why Dictionaries Matter

Dictionaries are everywhere in real programming:
- **JSON data** from web APIs uses dictionary structure
- **Database records** map naturally to dictionaries
- **Configuration files** store settings as key-value pairs
- **Fast lookups** - finding data by key is very efficient
- **Readable code** - `person["name"]` is clearer than `person[0]`

## Dictionaries vs Lists vs Tuples

**Lists:** Ordered, indexed by position, mutable  
**Tuples:** Ordered, indexed by position, immutable  
**Dictionaries:** Unordered*, indexed by key, mutable  

*Note: As of Python 3.7+, dictionaries maintain insertion order

## What's Different This Week?

**Weeks 1-6** focused on sequential data (lists, tuples).  
**Week 7** introduces **associative data** - connecting related information.

Instead of:
```python
student = ["Alice", 20, "Computer Science", 3.8]  # What does each mean?
```

Use:
```python
student = {
    "name": "Alice",
    "age": 20,
    "major": "Computer Science",
    "gpa": 3.8
}  # Self-documenting!
```

## Tips for Success

1. **Think key-value** - Every piece of data needs a descriptive key
2. **Keys must be unique** - Duplicate keys overwrite previous values
3. **Keys must be immutable** - Use strings, numbers, or tuples as keys
4. **Use .get()** - Safer than bracket notation for missing keys
5. **Practice with real data** - Create dictionaries for contacts, inventory, etc.

## Common Mistakes to Avoid

```{warning}
**Watch out for:**
- Using lists as dictionary keys (they're mutable - won't work!)
- Forgetting quotes around string keys
- Trying to access missing keys without .get()
- Modifying a dictionary while iterating over it
- Confusing dictionaries `{}` with sets `{1, 2, 3}`
```

## Midterm Exam Preparation

The midterm covers Weeks 1-6:
- Variables and data types
- Operators and expressions
- String manipulation
- Conditionals (if/elif/else)
- Functions
- Loops (for and while)
- Lists and tuples

**Study Tips:**
- Review all exercises from Weeks 1-6
- Practice writing functions
- Work through loop problems
- Understand list methods
- Be able to debug code

---

Let's start with [Dictionary Basics](dictionaries-basics.md)!
