# Python Syntax Fundamentals

## What is Syntax?

**Syntax** refers to the set of rules that define how a Python program is written and interpreted. Just like grammar in human languages, programming syntax determines what is "correct" code.

Think of it this way:
- **English**: "I am learning Python" (correct grammar)
- **English**: "Python learning am I" (incorrect grammar, but might be understood)
- **Python**: Code must follow exact syntax rules or it won't run at all!

## Indentation: Python's Special Rule

```{important}
Python uses **indentation** (spaces or tabs at the beginning of lines) to define code blocks. This is unique to Python - most other languages use curly braces `{}` or keywords.
```

### Why Indentation Matters

In Python, indentation is **not** just for readability - it's **required** for the code to run. Indentation tells Python which lines of code belong together.

### Correct Indentation

```python
if 5 > 2:
    print("Five is greater than two!")
```

**Output:**
```
Five is greater than two!
```

In this example:
- The `if` statement ends with a colon `:`
- The `print()` statement is **indented** (moved to the right with a tab or spaces)
- This indentation tells Python: "Execute this print statement ONLY if the condition is True"

### Incorrect Indentation - Error!

```python
if 5 > 2:
print("Five is greater than two!")
```

**Error:**
```
IndentationError: expected an indented block
```

Without indentation, Python doesn't know that the `print()` statement should be executed as part of the `if` block. The error message even tells us what's wrong!

### How Much Indentation?

The Python community standard (PEP 8) recommends **4 spaces** for each indentation level. However:
- You can use tabs OR spaces
- You must be **consistent** - don't mix tabs and spaces!
- Most code editors (including Jupyter) automatically use 4 spaces when you press Tab

### Example: Multiple Indentation Levels

```python
age = 20

if age >= 18:
    print("You are an adult")
    
    if age >= 65:
        print("You qualify for senior discounts")
    else:
        print("You do not qualify for senior discounts yet")
else:
    print("You are a minor")
```

Notice how we have **two levels** of indentation:
1. Code inside the first `if` is indented once
2. Code inside the nested `if`/`else` is indented twice

## Code Blocks

A **code block** is a group of statements that are treated as a single unit. In Python, code blocks are defined by:

1. **A colon `:` at the end of the previous line**
2. **Indentation of all lines in the block**

### Common Code Blocks

You'll use indented code blocks for:
- `if`/`elif`/`else` statements (we'll learn more about these soon)
- `for` loops (coming in Week 5)
- `while` loops (coming in Week 5)
- Functions (coming in Week 4)
- Classes (advanced topic)

## Line Breaks and Continuation

### Single Statement Per Line

Typically, each Python statement goes on its own line:

```python
name = "Alice"
age = 25
city = "Chicago"
```

### Long Lines

If a line is too long, you can break it up using a backslash `\`:

```python
total = 1 + 2 + 3 + 4 + 5 + \
        6 + 7 + 8 + 9 + 10
```

Or, if you're inside parentheses, brackets, or braces, Python automatically allows line breaks:

```python
total = (1 + 2 + 3 + 4 + 5 +
         6 + 7 + 8 + 9 + 10)
```

### PEP 8 Guideline

```{tip}
**Maximum line length:** PEP 8 recommends keeping lines under 79 characters. This makes code easier to read, especially when viewing multiple files side-by-side.
```

## Comments: Documenting Your Code

Comments are notes in your code that Python ignores. They're for human readers (including your future self!).

### Single-Line Comments

Use the `#` symbol:

```python
# This is a comment
print("Hello")  # This is also a comment
```

Everything after `#` on that line is ignored by Python.

### Multi-Line Comments

Python doesn't have official multi-line comments, but there are two approaches:

**Option 1: Multiple single-line comments**
```python
# This is a longer comment
# that spans multiple lines
# for detailed explanations
```

**Option 2: Multi-line string (not officially a comment)**
```python
"""
This is technically a string, not a comment.
But if it's not assigned to a variable,
Python ignores it, so it acts like a comment.
"""
```

### When to Use Comments

```python
# Good comments explain WHY, not WHAT
user_count = user_count + 1  # Bad: comment just repeats the code
user_count = user_count + 1  # Good: increment for new registration
```

**Best practices:**
- Explain complex logic
- Document assumptions
- Note why you made specific choices
- Describe the purpose of code sections
- **Don't** just repeat what the code obviously does

## Common Syntax Errors

### 1. Missing Colon

```python
# ERROR:
if x > 5
    print("Greater than 5")

# CORRECT:
if x > 5:
    print("Greater than 5")
```

### 2. Inconsistent Indentation

```python
# ERROR:
if x > 5:
    print("Line 1")
      print("Line 2")  # Extra spaces!
  
# CORRECT:
if x > 5:
    print("Line 1")
    print("Line 2")
```

### 3. Missing Quotation Marks

```python
# ERROR:
message = Hello World

# CORRECT:
message = "Hello World"
```

### 4. Unmatched Parentheses

```python
# ERROR:
print("Hello"

# CORRECT:
print("Hello")
```

## Reading Error Messages

When you make a syntax error, Python gives you helpful information:

```
  File "<ipython-input-7>", line 2
    print("Five is greater than two!")
        ^
IndentationError: expected an indented block
```

This tells you:
- **Where**: Line 2
- **What**: The problem is with indentation
- **Why**: Python expected an indented block but didn't find one

```{tip}
**Error messages are your friend!** Read them carefully - they usually tell you exactly what's wrong and where to look.
```

## Practice: Spotting Syntax Errors

Can you find the errors in this code?

```python
name = "Alice
age = 25
if age >= 18
    print("Adult")
    print "Can vote"
```

<details>
<summary>Click to see the answers</summary>

**Errors:**
1. Line 1: Missing closing quotation mark after "Alice"
2. Line 3: Missing colon `:` after the if condition
3. Line 5: Missing parentheses around `"Can vote"` in print function

**Corrected code:**
```python
name = "Alice"
age = 25
if age >= 18:
    print("Adult")
    print("Can vote")
```
</details>

## Summary

Key syntax rules to remember:

✅ **Indentation defines code blocks** - use 4 spaces consistently  
✅ **Colons `:` introduce code blocks** - if, for, while, functions  
✅ **Comments use `#`** - explain your code for others (and yourself)  
✅ **One statement per line** - unless using continuation  
✅ **Error messages help** - read them carefully!  

## Try It Yourself!

```{admonition} Practice Exercise
:class: tip

Open a new Jupyter notebook cell and:

1. Write an if statement that checks if a number is positive
2. Include proper indentation
3. Add a comment explaining what the code does
4. Try removing the indentation and see what error you get
5. Try removing the colon and see what error you get

Experiment with breaking the code - this helps you understand what each syntax rule does!
```

---

**Next:** Learn about [Data Types](data-types.md) in Python!
