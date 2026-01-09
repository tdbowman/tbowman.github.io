# Loops in Python

## What Are Loops?

Loops let you repeat code multiple times without writing it over and over. They're essential for processing collections of data and automating repetitive tasks.

## For Loops

For loops iterate over a sequence (list, string, range, etc.).

### Basic For Loop

```python
# Loop over a list
fruits = ["apple", "banana", "cherry"]

for fruit in fruits:
    print(fruit)

# Output:
# apple
# banana
# cherry
```

### The range() Function

`range()` generates a sequence of numbers:

```python
# range(stop) - from 0 to stop-1
for i in range(5):
    print(i)  # Prints: 0, 1, 2, 3, 4

# range(start, stop)
for i in range(2, 6):
    print(i)  # Prints: 2, 3, 4, 5

# range(start, stop, step)
for i in range(0, 10, 2):
    print(i)  # Prints: 0, 2, 4, 6, 8
```

### Looping Over Strings

```python
name = "Python"

for letter in name:
    print(letter)
# Prints each letter on a new line
```

### Using enumerate()

Get both index and value:

```python
fruits = ["apple", "banana", "cherry"]

for index, fruit in enumerate(fruits):
    print(f"{index}: {fruit}")

# Output:
# 0: apple
# 1: banana
# 2: cherry
```

### Practical For Loop Examples

**Example 1: Sum numbers**
```python
numbers = [1, 2, 3, 4, 5]
total = 0

for num in numbers:
    total += num

print(f"Sum: {total}")  # Sum: 15
```

**Example 2: Find average**
```python
grades = [85, 92, 78, 90, 88]
total = 0

for grade in grades:
    total += grade

average = total / len(grades)
print(f"Average: {average:.1f}")  # Average: 86.6
```

**Example 3: Process names**
```python
names = ["alice", "bob", "charlie"]

for name in names:
    print(name.title())  # Capitalize each name
```

## While Loops

While loops repeat as long as a condition is True.

### Basic While Loop

```python
count = 0

while count < 5:
    print(count)
    count += 1  # CRITICAL: Must change condition eventually!

# Prints: 0, 1, 2, 3, 4
```

### User Input Loop

```python
password = ""

while password != "secret":
    password = input("Enter password: ")

print("Access granted!")
```

### Input Validation

```python
while True:
    age_str = input("Enter your age: ")
    
    if age_str.isdigit():
        age = int(age_str)
        if 0 < age < 120:
            break  # Exit loop - valid input!
        else:
            print("Age must be between 1 and 119")
    else:
        print("Please enter a number")

print(f"Your age is {age}")
```

### Avoiding Infinite Loops

```{warning}
**Infinite loops run forever!** Always ensure the condition can become False.

```python
# BAD - Infinite loop:
count = 0
while count < 10:
    print(count)
    # Forgot to increment count!

# GOOD - Will terminate:
count = 0
while count < 10:
    print(count)
    count += 1  # Condition will eventually be False
```
```

## Loop Control Statements

### break - Exit Loop Early

```python
# Find first even number
numbers = [1, 3, 5, 8, 9, 10]

for num in numbers:
    if num % 2 == 0:
        print(f"Found even number: {num}")
        break  # Stop looking, we found one

# Output: Found even number: 8
```

### continue - Skip to Next Iteration

```python
# Print only odd numbers
for i in range(10):
    if i % 2 == 0:
        continue  # Skip even numbers
    print(i)

# Prints: 1, 3, 5, 7, 9
```

### else with Loops

The `else` block runs if loop completes normally (no `break`):

```python
# Search for an item
items = ["apple", "banana", "cherry"]
search = "grape"

for item in items:
    if item == search:
        print(f"Found {search}!")
        break
else:
    print(f"{search} not found")

# Output: grape not found
```

## Nested Loops

Loops within loops - useful for multi-dimensional data:

```python
# Multiplication table
for i in range(1, 4):
    for j in range(1, 4):
        product = i * j
        print(f"{i} x {j} = {product}")
    print()  # Blank line after each row

# Output:
# 1 x 1 = 1
# 1 x 2 = 2
# 1 x 3 = 3
#
# 2 x 1 = 2
# 2 x 2 = 4
# 2 x 3 = 6
# ...
```

**Pattern Example:**
```python
for i in range(5):
    for j in range(i + 1):
        print("*", end="")
    print()  # New line

# Output:
# *
# **
# ***
# ****
# *****
```

## Practical Examples

### Example 1: Grade Calculator

```python
# Get multiple grades from user
grades = []

while True:
    grade_input = input("Enter grade (or 'done' to finish): ")
    
    if grade_input.lower() == 'done':
        break
    
    if grade_input.isdigit():
        grade = int(grade_input)
        if 0 <= grade <= 100:
            grades.append(grade)
        else:
            print("Grade must be 0-100")
    else:
        print("Please enter a number")

# Calculate statistics
if grades:
    average = sum(grades) / len(grades)
    highest = max(grades)
    lowest = min(grades)
    
    print(f"\nStatistics for {len(grades)} grades:")
    print(f"Average: {average:.1f}")
    print(f"Highest: {highest}")
    print(f"Lowest: {lowest}")
```

### Example 2: Find Prime Numbers

```python
# Find all prime numbers up to n
n = 20
primes = []

for num in range(2, n + 1):
    is_prime = True
    
    for divisor in range(2, int(num ** 0.5) + 1):
        if num % divisor == 0:
            is_prime = False
            break
    
    if is_prime:
        primes.append(num)

print(f"Primes up to {n}: {primes}")
```

### Example 3: Process Shopping List

```python
shopping_list = []

print("Shopping List Builder")
print("Enter items (type 'done' when finished)")

while True:
    item = input("Item: ").strip()
    
    if item.lower() == 'done':
        break
    
    if item:
        shopping_list.append(item.title())
    else:
        print("Please enter an item name")

# Display list
print("\nYour Shopping List:")
for index, item in enumerate(shopping_list, start=1):
    print(f"{index}. {item}")
```

## Common Patterns

### Accumulator Pattern

```python
# Count positive numbers
numbers = [5, -2, 8, -1, 3, 0]
positive_count = 0

for num in numbers:
    if num > 0:
        positive_count += 1

print(f"Positive numbers: {positive_count}")
```

### Search Pattern

```python
# Find item position
names = ["Alice", "Bob", "Charlie", "David"]
search_name = "Charlie"
position = -1

for index, name in enumerate(names):
    if name == search_name:
        position = index
        break

if position != -1:
    print(f"Found at position {position}")
else:
    print("Not found")
```

### Filter Pattern

```python
# Get even numbers
numbers = [1, 2, 3, 4, 5, 6, 7, 8]
even_numbers = []

for num in numbers:
    if num % 2 == 0:
        even_numbers.append(num)

print(even_numbers)  # [2, 4, 6, 8]
```

## Loop Efficiency Tips

```{tip}
1. **Pre-calculate when possible** - Don't recalculate the same value each iteration
2. **Break early** - Exit loop as soon as you find what you need
3. **Use appropriate loop** - For loops for known iterations, while for conditions
4. **Avoid modifying list while iterating** - Can cause unexpected behavior
```

## Practice Exercises

```{admonition} Try It Yourself
:class: tip

1. **FizzBuzz:** Print numbers 1-100, but:
   - "Fizz" for multiples of 3
   - "Buzz" for multiples of 5
   - "FizzBuzz" for multiples of both

2. **Reverse a String:** Use a loop to reverse any string

3. **Password Strength:** Check if password has:
   - At least 8 characters
   - Uppercase and lowercase
   - At least one digit

4. **Number Guessing Game:** Computer picks random number, user guesses until correct
```

## Summary

✅ **For loops** - Iterate over sequences  
✅ **While loops** - Repeat while condition is True  
✅ **break** - Exit loop early  
✅ **continue** - Skip to next iteration  
✅ **Nested loops** - Loops within loops  
✅ **Common patterns** - Accumulate, search, filter  

---

**Next:** Practice with exercises!
