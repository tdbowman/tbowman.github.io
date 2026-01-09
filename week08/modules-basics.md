# Python Modules

## What Are Modules?

A module is simply a Python file (`.py`) containing functions, variables, and classes. Modules let you organize code and reuse it across projects.

```python
# This entire file could be a module!
# my_module.py

def greet(name):
    return f"Hello, {name}!"

PI = 3.14159

def circle_area(radius):
    return PI * radius ** 2
```

## Importing Modules

### Basic Import

```python
# Import entire module
import math

# Use module.function()
result = math.sqrt(16)
print(result)  # 4.0

print(math.pi)  # 3.141592653589793
```

### From Import

```python
# Import specific items
from math import sqrt, pi

# Use directly without module name
result = sqrt(16)
print(result)  # 4.0
print(pi)      # 3.141592653589793
```

### Import with Alias

```python
# Give module a shorter name
import datetime as dt

now = dt.datetime.now()
print(now)

# Or for specific imports
from datetime import datetime as DateTime
now = DateTime.now()
```

### Import Everything (Not Recommended!)

```python
# Import all items
from math import *

# Can use everything without prefix
print(sqrt(16))  # 4.0
print(pi)        # 3.141592653589793

# BUT: Can cause name conflicts!
```

```{warning}
**Avoid `from module import *`**  
It's unclear what names you're importing and can overwrite your variables!
```

## Popular Standard Library Modules

### math - Mathematical Functions

```python
import math

# Constants
print(math.pi)     # 3.141592653589793
print(math.e)      # 2.718281828459045

# Functions
print(math.sqrt(16))      # 4.0
print(math.ceil(4.3))     # 5
print(math.floor(4.7))    # 4
print(math.pow(2, 3))     # 8.0
print(math.sin(math.pi/2))  # 1.0
print(math.log(10))       # 2.302585092994046
```

### random - Random Numbers

```python
import random

# Random float between 0 and 1
print(random.random())

# Random integer in range
print(random.randint(1, 10))  # 1 to 10 inclusive

# Random choice from list
colors = ["red", "green", "blue"]
print(random.choice(colors))

# Shuffle a list
cards = [1, 2, 3, 4, 5]
random.shuffle(cards)
print(cards)

# Random sample (multiple choices)
print(random.sample([1, 2, 3, 4, 5], 3))
```

### datetime - Dates and Times

```python
from datetime import datetime, date, timedelta

# Current date and time
now = datetime.now()
print(now)  # 2024-12-21 14:30:45.123456

# Current date only
today = date.today()
print(today)  # 2024-12-21

# Create specific date
birthday = date(1990, 5, 15)
print(birthday)

# Date arithmetic
tomorrow = today + timedelta(days=1)
next_week = today + timedelta(weeks=1)

# Formatting
print(now.strftime("%Y-%m-%d"))  # 2024-12-21
print(now.strftime("%B %d, %Y"))  # December 21, 2024
```

### os - Operating System Interface

```python
import os

# Current directory
print(os.getcwd())

# List files in directory
print(os.listdir('.'))

# Check if file exists
print(os.path.exists('myfile.txt'))

# Join paths (works on any OS)
path = os.path.join('folder', 'subfolder', 'file.txt')

# Get file info
# size = os.path.getsize('myfile.txt')
```

### sys - System-Specific Parameters

```python
import sys

# Python version
print(sys.version)

# Command line arguments
print(sys.argv)

# Exit program
# sys.exit()

# Module search path
print(sys.path)
```

## Creating Your Own Modules

### Step 1: Create a Module File

```python
# my_utils.py

def greet(name):
    """Greet someone by name."""
    return f"Hello, {name}!"

def add(a, b):
    """Add two numbers."""
    return a + b

# Module-level variable
VERSION = "1.0"
```

### Step 2: Import and Use It

```python
# main.py (in same directory)

import my_utils

message = my_utils.greet("Alice")
print(message)  # "Hello, Alice!"

result = my_utils.add(5, 3)
print(result)  # 8

print(my_utils.VERSION)  # "1.0"
```

### if __name__ == "__main__"

This lets code run only when file is executed directly:

```python
# my_module.py

def greet(name):
    return f"Hello, {name}!"

# This runs only if file is executed directly
if __name__ == "__main__":
    print("Running module directly")
    print(greet("Test"))
    
# When imported, only functions are available
```

```python
# When you run: python my_module.py
# Output: Running module directly
#         Hello, Test!

# When you import: import my_module
# No output! Only functions available.
```

## Useful Functions for Modules

### dir() - List Module Contents

```python
import math

# See what's in the module
print(dir(math))
# ['__doc__', '__name__', 'acos', 'asin', 'atan', 'ceil', 
#  'cos', 'e', 'exp', 'floor', 'log', 'pi', 'pow', 'sin', 
#  'sqrt', 'tan', ...]
```

### help() - Get Documentation

```python
import math

# Get help on module
help(math)

# Get help on specific function
help(math.sqrt)
```

## Module Search Path

Python looks for modules in specific locations:

```python
import sys
print(sys.path)

# Typical order:
# 1. Current directory
# 2. PYTHONPATH environment variable
# 3. Standard library directories
# 4. Site-packages (third-party modules)
```

## Packages

Packages are folders containing modules with a special `__init__.py` file:

```
my_package/
    __init__.py
    module1.py
    module2.py
    subpackage/
        __init__.py
        module3.py
```

```python
# Import from package
from my_package import module1
from my_package.subpackage import module3
```

## Practical Example: Utility Module

```python
# utils.py

import random
import datetime

def random_date(start_year, end_year):
    """Generate random date between years."""
    year = random.randint(start_year, end_year)
    month = random.randint(1, 12)
    day = random.randint(1, 28)  # Keep it simple
    return datetime.date(year, month, day)

def format_currency(amount):
    """Format number as currency."""
    return f"${amount:,.2f}"

def validate_email(email):
    """Basic email validation."""
    return "@" in email and "." in email

if __name__ == "__main__":
    # Test functions
    print(random_date(2020, 2024))
    print(format_currency(1234.5))
    print(validate_email("user@example.com"))
```

```python
# main.py

import utils

date = utils.random_date(2020, 2024)
print(f"Random date: {date}")

price = utils.format_currency(99.99)
print(f"Price: {price}")

if utils.validate_email("test@example.com"):
    print("Valid email!")
```

## Summary

✅ **Modules** - Organize code into reusable files  
✅ **import** - Load modules into your program  
✅ **Standard library** - Vast collection of built-in modules  
✅ **Create modules** - Any .py file is a module  
✅ **`__name__ == "__main__"`** - Code for direct execution  
✅ **Packages** - Organize related modules  

---

**Next:** Work with file operations in Week 9!
