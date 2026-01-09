# Operators and String Manipulation

## Mathematical Operators

Python supports all the standard mathematical operations you'd expect from a calculator - and more!

### Basic Arithmetic Operators

| Operator | Name | Example | Result |
|----------|------|---------|--------|
| `+` | Addition | `5 + 3` | `8` |
| `-` | Subtraction | `5 - 3` | `2` |
| `*` | Multiplication | `5 * 3` | `15` |
| `/` | Division | `5 / 2` | `2.5` |
| `//` | Floor Division | `5 // 2` | `2` |
| `%` | Modulus (remainder) | `5 % 2` | `1` |
| `**` | Exponentiation | `5 ** 2` | `25` |

### Examples

```python
# Addition
x = 10 + 5
print(x)  # Output: 15

# Subtraction  
y = 10 - 5
print(y)  # Output: 5

# Multiplication
z = 10 * 5
print(z)  # Output: 50

# Division (always returns a float)
w = 10 / 5
print(w)  # Output: 2.0
```

### Division: / vs //

```{important}
Python has **two** division operators:
- `/` - Regular division (returns a float)
- `//` - Floor division (returns an integer, rounded down)
```

```python
# Regular division
print(7 / 2)   # Output: 3.5

# Floor division (rounds down)
print(7 // 2)  # Output: 3

# Works with negative numbers too
print(-7 // 2)  # Output: -4 (rounds down to more negative)
```

### Modulus Operator %

The modulus operator `%` gives you the **remainder** after division:

```python
print(7 % 2)   # Output: 1 (7 divided by 2 is 3 remainder 1)
print(10 % 3)  # Output: 1 (10 divided by 3 is 3 remainder 1)
print(15 % 4)  # Output: 3 (15 divided by 4 is 3 remainder 3)

# Common use: checking if a number is even or odd
number = 8
if number % 2 == 0:
    print("Even")
else:
    print("Odd")
```

### Exponentiation **

Use `**` to raise a number to a power:

```python
# Square a number
print(5 ** 2)  # Output: 25 (5 squared)

# Cube a number
print(2 ** 3)  # Output: 8 (2 cubed)

# Square root (raise to power of 0.5)
print(16 ** 0.5)  # Output: 4.0
```

## Order of Operations (PEMDAS)

Python follows the standard mathematical order of operations:

1. **P**arentheses
2. **E**xponentiation  
3. **M**ultiplication and **D**ivision (left to right)
4. **A**ddition and **S**ubtraction (left to right)

### Examples

```python
# Without parentheses
x = 1 + 2 * 3
print(x)  # Output: 7 (multiplication first: 1 + 6)

# With parentheses
x = (1 + 2) * 3
print(x)  # Output: 9 (parentheses first: 3 * 3)

# Complex expression
x = ((((13 + 5) * 2) - 4) / 2) - 13
print(x)  # Output: 3.0
```

**Step by step:**
```
((((13 + 5) * 2) - 4) / 2) - 13
(((18 * 2) - 4) / 2) - 13        # Innermost parentheses first
((36 - 4) / 2) - 13              # Next parentheses
(32 / 2) - 13                     # Division
16 - 13                           # Subtraction
3
```

```{tip}
**When in doubt, use parentheses!** They make your code more readable and ensure operations happen in the order you intend.
```

## Comparison Operators

Comparison operators compare two values and return `True` or `False`:

| Operator | Meaning | Example | Result |
|----------|---------|---------|--------|
| `==` | Equal to | `5 == 5` | `True` |
| `!=` | Not equal to | `5 != 3` | `True` |
| `>` | Greater than | `5 > 3` | `True` |
| `<` | Less than | `5 < 3` | `False` |
| `>=` | Greater than or equal | `5 >= 5` | `True` |
| `<=` | Less than or equal | `5 <= 3` | `False` |

### Common Mistake: = vs ==

```{warning}
**Don't confuse:**
- `=` is for **assignment** (storing a value)
- `==` is for **comparison** (checking equality)
```

```python
# Assignment (=)
x = 5  # Store the value 5 in variable x

# Comparison (==)
if x == 5:  # Check if x equals 5
    print("x is five")
```

## Working with Different Data Types

### Numbers (int and float)

When you use operators on numbers, the result depends on the types:

```python
# int + int = int
result = 5 + 3
print(type(result))  # <class 'int'>

# float + float = float
result = 5.0 + 3.0
print(type(result))  # <class 'float'>

# int + float = float (Python converts to float)
result = 5 + 3.0
print(type(result))  # <class 'float'>

# Division always returns float
result = 10 / 2
print(type(result))  # <class 'float'> (even though it's 5.0)
```

### Strings and the + Operator

With strings, `+` means **concatenation** (joining strings together), NOT addition:

```python
# String concatenation
first_name = "John"
last_name = "Doe"
full_name = first_name + " " + last_name
print(full_name)  # Output: John Doe

# Multiple concatenations
quote = "The sky above the port " + "was the color of television, " + \
        "tuned to a dead channel."
print(quote)
```

### String Repetition with *

You can use `*` to repeat strings:

```python
print("Ha" * 3)     # Output: HaHaHa
print("=" * 20)     # Output: ====================
print("-" * 10)     # Output: ----------
```

## Common Type Errors

### Cannot Concatenate String and Number

```python
# This causes an ERROR:
first_var = "The answer is: "
second_var = 42
print(first_var + second_var)  # TypeError!
```

**Error message:**
```
TypeError: can only concatenate str (not "int") to str
```

Python won't let you add a string and a number directly - you must convert one type to match the other.

## Type Conversion

Use these functions to convert between types:

| Function | Purpose | Example |
|----------|---------|---------|
| `str()` | Convert to string | `str(42)` → `"42"` |
| `int()` | Convert to integer | `int("42")` → `42` |
| `float()` | Convert to float | `float("3.14")` → `3.14` |
| `bool()` | Convert to boolean | `bool(1)` → `True` |

### Converting Numbers to Strings

```python
first_var = "The answer is: "
second_var = 42

# Convert the number to a string
sentence = first_var + str(second_var)
print(sentence)  # Output: The answer is: 42
```

### Converting Strings to Numbers

```python
# String to integer
age_string = "25"
age_number = int(age_string)
print(age_number + 5)  # Output: 30

# String to float
price_string = "19.99"
price_number = float(price_string)
print(price_number * 2)  # Output: 39.98
```

### Conversion Errors

Be careful - not all conversions are possible:

```python
# This works:
int("42")  # Returns 42

# This causes an ERROR:
int("Hello")  # ValueError: invalid literal for int()

# This works:
float("3.14")  # Returns 3.14

# This causes an ERROR:
int("3.14")  # ValueError: invalid literal for int()
# Use int(float("3.14")) instead
```

## String Methods (Preview)

Python has many built-in methods for working with strings. Here's a sneak peek (we'll cover these more in Week 3):

```python
message = "Hello World"

# Convert to uppercase
print(message.upper())  # HELLO WORLD

# Convert to lowercase
print(message.lower())  # hello world

# Replace text
print(message.replace("World", "Python"))  # Hello Python

# Split into words
print(message.split())  # ['Hello', 'World']
```

## Practical Examples

### Example 1: Calculating Averages

```python
# Calculate average of three test scores
score1 = 85
score2 = 92
score3 = 78

average = (score1 + score2 + score3) / 3
print("Average score:", average)  # Output: Average score: 85.0
```

### Example 2: Temperature Conversion

```python
# Convert Fahrenheit to Celsius
# Formula: C = (F - 32) * 5/9

fahrenheit = 98.6
celsius = (fahrenheit - 32) * 5 / 9
print(fahrenheit, "°F is", celsius, "°C")
# Output: 98.6 °F is 37.0 °C
```

### Example 3: Building Messages

```python
# Create a personalized greeting
name = "Alice"
age = 25
city = "Chicago"

message = "Hello, " + name + "! " + \
          "You are " + str(age) + " years old " + \
          "and you live in " + city + "."
          
print(message)
# Output: Hello, Alice! You are 25 years old and you live in Chicago.
```

## Summary

Key concepts:

✅ **Arithmetic operators**: `+`, `-`, `*`, `/`, `//`, `%`, `**`  
✅ **Order of operations**: PEMDAS (use parentheses for clarity)  
✅ **Comparison operators**: `==`, `!=`, `>`, `<`, `>=`, `<=`  
✅ **String concatenation**: Use `+` to join strings  
✅ **Type conversion**: `str()`, `int()`, `float()` to convert types  
✅ **Watch for type errors**: Can't mix strings and numbers without converting  

## Try It Yourself!

```{admonition} Practice Exercise
:class: tip

Create a Jupyter notebook cell and write code to:

1. Calculate the area of a circle (π × r²) where radius = 5
   - Hint: Use 3.14159 for π, or use `**` for squaring
2. Convert a temperature from Celsius to Fahrenheit
   - Formula: F = C × 9/5 + 32
3. Create a string that says "I am [age] years old" using variables and concatenation
4. Calculate what 15% tip would be on a $47.50 restaurant bill

Try to do each calculation and print the results with descriptive messages!
```

---

**Next:** Practice with the [Interactive Data Types Notebook](data-types.ipynb)!
