# String Methods and User Input

## String Methods

Python provides many built-in methods to manipulate strings. Remember: **strings are immutable** - these methods return NEW strings, they don't change the original.

### Case Conversion Methods

```python
message = "hello WORLD"

print(message.upper())      # "HELLO WORLD"
print(message.lower())      # "hello world"
print(message.title())      # "Hello World"
print(message.capitalize()) # "Hello world"
```

**When to use each:**
- `.upper()` - Comparing strings (case-insensitive), acronyms
- `.lower()` - Normalizing input for comparison
- `.title()` - Names, headings
- `.capitalize()` - Sentences

### Whitespace Removal

```python
text = "   hello world   "

print(text.strip())   # "hello world" (both ends)
print(text.lstrip())  # "hello world   " (left only)
print(text.rstrip())  # "   hello world" (right only)
```

```{tip}
**Always `.strip()` user input!** Users often accidentally add spaces.
```

### Finding and Replacing

```python
sentence = "Python is fun. Python is powerful."

# Replace
new_sentence = sentence.replace("Python", "Programming")
print(new_sentence)  # "Programming is fun. Programming is powerful."

# Find (returns index or -1 if not found)
position = sentence.find("fun")
print(position)  # 10

# Count occurrences
count = sentence.count("Python")
print(count)  # 2
```

### Splitting and Joining

```python
# Split - breaks string into list
sentence = "apple,banana,cherry,date"
fruits = sentence.split(",")
print(fruits)  # ['apple', 'banana', 'cherry', 'date']

# Split on whitespace (default)
words = "Hello world from Python".split()
print(words)  # ['Hello', 'world', 'from', 'Python']

# Join - combines list into string
fruits = ['apple', 'banana', 'cherry']
result = ", ".join(fruits)
print(result)  # "apple, banana, cherry"
```

### Checking String Content

```python
filename = "document.pdf"
email = "user@example.com"

# Starts with / Ends with
print(filename.endswith(".pdf"))  # True
print(email.startswith("admin"))  # False

# Check if all characters are...
print("123".isdigit())    # True
print("abc".isalpha())    # True
print("abc123".isalnum()) # True
```

## User Input

The `input()` function lets you get data from users.

### Basic Input

```python
name = input("What is your name? ")
print("Hello,", name)
```

**Output:**
```
What is your name? Alice
Hello, Alice
```

### Critical Rule: Input Returns Strings

```python
age = input("How old are you? ")
print(type(age))  # <class 'str'> - It's a STRING!

# This will cause an error:
# next_year = age + 1  # TypeError!

# Must convert first:
age_num = int(age)
next_year = age_num + 1
print("Next year you'll be", next_year)
```

### Converting Input

```python
# Get a number
age = int(input("Enter your age: "))

# Get a decimal
price = float(input("Enter price: "))

# Multiple inputs on one line
full_name = input("Enter first and last name: ")
first, last = full_name.split()  # Split into two parts
```

### Input Validation

Always check that input is what you expect:

```python
# Simple validation
age_str = input("Enter your age: ")

if age_str.isdigit():
    age = int(age_str)
    print("Your age is:", age)
else:
    print("That's not a valid age!")

# Better validation with try/except (preview)
try:
    age = int(input("Enter your age: "))
    if age < 0 or age > 120:
        print("That age seems unlikely!")
    else:
        print("Your age is:", age)
except ValueError:
    print("Please enter a number!")
```

## String Formatting

### F-Strings (Recommended - Python 3.6+)

The modern, clean way to format strings:

```python
name = "Alice"
age = 25
height = 5.7

# Basic f-string
message = f"My name is {name} and I'm {age} years old."
print(message)

# Expressions inside {}
print(f"Next year I'll be {age + 1}")
print(f"My height in inches: {height * 12}")

# Formatting numbers
pi = 3.14159265359
print(f"Pi to 2 decimals: {pi:.2f}")  # 3.14
print(f"Pi to 4 decimals: {pi:.4f}")  # 3.1416

price = 19.5
print(f"Price: ${price:.2f}")  # Price: $19.50
```

### .format() Method

Older but still used:

```python
name = "Bob"
score = 95.7

message = "Student {} scored {:.1f}%".format(name, score)
print(message)  # Student Bob scored 95.7%

# Named placeholders
message = "Hello {name}, you scored {score}".format(name="Alice", score=100)
```

### Format Specifications

```python
number = 1234.5678

print(f"{number:.2f}")   # 1234.57 (2 decimal places)
print(f"{number:.0f}")   # 1235 (rounded, no decimals)
print(f"{number:,.2f}")  # 1,234.57 (with comma separator)
print(f"{number:10.2f}") # "   1234.57" (width 10, right-aligned)
```

## Escape Characters

Special characters in strings:

```python
# Newline
print("Line 1\nLine 2")
# Output:
# Line 1
# Line 2

# Tab
print("Name:\tAlice\nAge:\t25")
# Output:
# Name:   Alice
# Age:    25

# Backslash
print("Path: C:\\Users\\Documents")
# Output: Path: C:\Users\Documents

# Quotes within strings
print("She said, \"Hello!\"")
# Output: She said, "Hello!"

# Alternative: use different quote types
print('She said, "Hello!"')
```

## String Slicing

Access parts of strings using indices:

```python
text = "Python"
#       012345  (positive indices)
#      -6-5-4-3-2-1 (negative indices)

# Single character
print(text[0])   # "P"
print(text[-1])  # "n" (last character)

# Slicing [start:end]
print(text[0:3]) # "Pyt" (indices 0, 1, 2)
print(text[2:])  # "thon" (from index 2 to end)
print(text[:4])  # "Pyth" (from start to index 4)

# Negative slicing
print(text[-3:]) # "hon" (last 3 characters)

# Step value [start:end:step]
print(text[::2])  # "Pto" (every 2nd character)
print(text[::-1]) # "nohtyP" (reverse!)
```

## Practical Examples

### Example 1: Clean and Format Name

```python
# Get name from user
name = input("Enter your full name: ")

# Clean it up
name = name.strip()  # Remove extra spaces
name = name.title()  # Capitalize properly

print(f"Welcome, {name}!")
```

### Example 2: Email Validator (Simple)

```python
email = input("Enter your email: ").strip().lower()

if "@" in email and "." in email:
    if email.endswith(".com") or email.endswith(".edu"):
        print("Email looks valid!")
    else:
        print("Email must end with .com or .edu")
else:
    print("Email must contain @ and a domain")
```

### Example 3: Build a Receipt

```python
# Get purchase info
item = input("Item name: ").strip().title()
price = float(input("Price: $"))
quantity = int(input("Quantity: "))

# Calculate
subtotal = price * quantity
tax = subtotal * 0.08
total = subtotal + tax

# Print formatted receipt
print("\n" + "=" * 30)
print("RECEIPT")
print("=" * 30)
print(f"Item:     {item}")
print(f"Price:    ${price:.2f}")
print(f"Quantity: {quantity}")
print("-" * 30)
print(f"Subtotal: ${subtotal:.2f}")
print(f"Tax:      ${tax:.2f}")
print(f"TOTAL:    ${total:.2f}")
print("=" * 30)
```

## Practice Exercises

```{admonition} Try It Yourself
:class: tip

1. **Name Formatter:**
   - Ask for first and last name
   - Display in formats: "LAST, First" and "First Last"

2. **Word Counter:**
   - Get a sentence from user
   - Count total words
   - Count specific word occurrences

3. **Password Validator:**
   - Check length >= 8
   - Contains uppercase and lowercase
   - Contains at least one digit

4. **Mad Libs:**
   - Ask for noun, verb, adjective, place
   - Insert into a story template
```

## Summary

✅ **String methods** - Powerful tools for text manipulation  
✅ **User input** - Always returns strings, validate and convert  
✅ **F-strings** - Modern, clean formatting  
✅ **Escape characters** - Handle special formatting needs  
✅ **Slicing** - Extract parts of strings efficiently  

---

**Next:** Continue practicing with more exercises!
