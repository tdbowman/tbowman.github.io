# Lists and Tuples

## Lists: Ordered, Mutable Collections

Lists store multiple items in a single variable. They're one of the most commonly used data structures in Python.

### Creating Lists

```python
# Empty list
my_list = []

# List with items
fruits = ["apple", "banana", "cherry"]
numbers = [1, 2, 3, 4, 5]
mixed = [1, "hello", 3.14, True]  # Can mix types

# Using list() constructor
my_list = list()
```

### Accessing List Elements

```python
fruits = ["apple", "banana", "cherry", "date"]
#          0        1          2         3
#         -4       -3         -2        -1

# Positive indexing
print(fruits[0])   # "apple"
print(fruits[2])   # "cherry"

# Negative indexing (from end)
print(fruits[-1])  # "date" (last item)
print(fruits[-2])  # "cherry"
```

### List Slicing

```python
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# [start:end] - end not included
print(numbers[2:5])    # [2, 3, 4]
print(numbers[:4])     # [0, 1, 2, 3] (from start)
print(numbers[6:])     # [6, 7, 8, 9] (to end)
print(numbers[-3:])    # [7, 8, 9] (last 3)

# [start:end:step]
print(numbers[::2])    # [0, 2, 4, 6, 8] (every 2nd)
print(numbers[::-1])   # [9, 8, 7...0] (reverse)
```

## List Methods - Modifying Lists

### Adding Items

```python
fruits = ["apple", "banana"]

# append() - add to end
fruits.append("cherry")
print(fruits)  # ["apple", "banana", "cherry"]

# insert() - add at specific position
fruits.insert(1, "blueberry")
print(fruits)  # ["apple", "blueberry", "banana", "cherry"]

# extend() - add multiple items
fruits.extend(["date", "elderberry"])
print(fruits)  # ["apple", "blueberry", "banana", "cherry", "date", "elderberry"]
```

### Removing Items

```python
fruits = ["apple", "banana", "cherry", "banana"]

# remove() - remove first occurrence
fruits.remove("banana")
print(fruits)  # ["apple", "cherry", "banana"]

# pop() - remove and return item
last_fruit = fruits.pop()  # Removes last item
print(last_fruit)  # "banana"
print(fruits)  # ["apple", "cherry"]

# pop(index) - remove at specific position
first_fruit = fruits.pop(0)
print(first_fruit)  # "apple"

# del - delete by index or slice
fruits = ["apple", "banana", "cherry", "date"]
del fruits[1]  # Delete banana
print(fruits)  # ["apple", "cherry", "date"]

# clear() - remove all items
fruits.clear()
print(fruits)  # []
```

### Organizing Lists

```python
numbers = [3, 1, 4, 1, 5, 9, 2]

# sort() - sort in place
numbers.sort()
print(numbers)  # [1, 1, 2, 3, 4, 5, 9]

# sort(reverse=True) - descending
numbers.sort(reverse=True)
print(numbers)  # [9, 5, 4, 3, 2, 1, 1]

# sorted() - return new sorted list (original unchanged)
original = [3, 1, 4]
sorted_list = sorted(original)
print(original)     # [3, 1, 4] (unchanged)
print(sorted_list)  # [1, 3, 4]

# reverse() - reverse in place
numbers.reverse()
print(numbers)
```

### Finding and Counting

```python
fruits = ["apple", "banana", "cherry", "banana"]

# index() - find first occurrence
position = fruits.index("banana")
print(position)  # 1

# count() - count occurrences
count = fruits.count("banana")
print(count)  # 2

# in operator - check membership
if "apple" in fruits:
    print("Apple is in the list!")

# len() - get length
print(len(fruits))  # 4
```

## Looping Through Lists

```python
fruits = ["apple", "banana", "cherry"]

# Simple loop
for fruit in fruits:
    print(fruit)

# With index
for i in range(len(fruits)):
    print(f"{i}: {fruits[i]}")

# With enumerate (better!)
for index, fruit in enumerate(fruits):
    print(f"{index}: {fruit}")

# With starting number
for num, fruit in enumerate(fruits, start=1):
    print(f"{num}. {fruit}")
```

## List Comprehensions

Create new lists in a concise way:

```python
# Traditional way
squares = []
for i in range(10):
    squares.append(i ** 2)

# List comprehension
squares = [i ** 2 for i in range(10)]
print(squares)  # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

# With condition
even_squares = [i ** 2 for i in range(10) if i % 2 == 0]
print(even_squares)  # [0, 4, 16, 36, 64]

# Transform strings
names = ["alice", "bob", "charlie"]
caps = [name.upper() for name in names]
print(caps)  # ["ALICE", "BOB", "CHARLIE"]
```

## Nested Lists

```python
# 2D list (matrix)
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

# Access elements
print(matrix[0])     # [1, 2, 3]
print(matrix[0][0])  # 1
print(matrix[1][2])  # 6

# Loop through 2D list
for row in matrix:
    for item in row:
        print(item, end=" ")
    print()  # New line after each row
```

## Tuples: Ordered, Immutable Collections

Tuples are like lists but **cannot be changed** after creation.

### Creating Tuples

```python
# Tuple with parentheses
coordinates = (10, 20)
rgb = (255, 0, 128)

# Without parentheses (tuple packing)
point = 5, 10

# Single item tuple (needs comma!)
single = (42,)  # Tuple
not_tuple = (42)  # Just a number!

# Empty tuple
empty = ()
```

### Accessing Tuples

```python
point = (10, 20, 30)

# Same indexing as lists
print(point[0])   # 10
print(point[-1])  # 30

# Slicing works too
print(point[1:])  # (20, 30)
```

### Tuple Unpacking

```python
# Assign tuple values to variables
coordinates = (10, 20)
x, y = coordinates
print(x)  # 10
print(y)  # 20

# Swap variables
a = 5
b = 10
a, b = b, a  # Swap!
print(a, b)  # 10, 5

# Multiple return values from function
def get_stats():
    return 100, 85, 92  # Returns a tuple

high, low, avg = get_stats()
```

### Tuple Methods

```python
numbers = (1, 2, 3, 2, 4, 2)

# count() - count occurrences
print(numbers.count(2))  # 3

# index() - find first occurrence
print(numbers.index(3))  # 2

# len() - get length
print(len(numbers))  # 6
```

### Why Use Tuples?

```{tip}
Use tuples when:
- Data shouldn't change (coordinates, RGB colors, dates)
- Returning multiple values from functions
- Dictionary keys (lists can't be keys!)
- Slightly faster and use less memory than lists
```

## Lists vs Tuples Comparison

```python
# Lists - Mutable
my_list = [1, 2, 3]
my_list[0] = 99  # OK - can modify
my_list.append(4)  # OK - can add items

# Tuples - Immutable
my_tuple = (1, 2, 3)
# my_tuple[0] = 99  # ERROR - cannot modify
# my_tuple.append(4)  # ERROR - no append method
```

## Practical Examples

### Example 1: Grade Manager

```python
# Store and analyze grades
grades = []

# Get grades from user
while True:
    grade = input("Enter grade (or 'done'): ")
    if grade.lower() == 'done':
        break
    if grade.isdigit():
        grades.append(int(grade))

# Calculate statistics
if grades:
    average = sum(grades) / len(grades)
    highest = max(grades)
    lowest = min(grades)
    
    print(f"Average: {average:.1f}")
    print(f"Highest: {highest}")
    print(f"Lowest: {lowest}")
    print(f"Grades: {sorted(grades, reverse=True)}")
```

### Example 2: Todo List

```python
todos = []

while True:
    print("\n1. Add task")
    print("2. View tasks")
    print("3. Complete task")
    print("4. Quit")
    
    choice = input("Choose: ")
    
    if choice == '1':
        task = input("Task: ")
        todos.append(task)
        print("Added!")
    
    elif choice == '2':
        if todos:
            for i, task in enumerate(todos, 1):
                print(f"{i}. {task}")
        else:
            print("No tasks")
    
    elif choice == '3':
        if todos:
            for i, task in enumerate(todos, 1):
                print(f"{i}. {task}")
            num = int(input("Complete #: ")) - 1
            if 0 <= num < len(todos):
                completed = todos.pop(num)
                print(f"Completed: {completed}")
        else:
            print("No tasks")
    
    elif choice == '4':
        break
```

### Example 3: Data Processing

```python
# Sales data (day, amount)
sales = [
    ("Monday", 1200),
    ("Tuesday", 1500),
    ("Wednesday", 980),
    ("Thursday", 1350),
    ("Friday", 2100)
]

# Find best day
best_day = max(sales, key=lambda x: x[1])
print(f"Best day: {best_day[0]} (${best_day[1]})")

# Calculate total and average
total = sum(amount for day, amount in sales)
average = total / len(sales)
print(f"Total: ${total}")
print(f"Average: ${average:.2f}")

# Days above average
print("\nAbove average days:")
for day, amount in sales:
    if amount > average:
        print(f"  {day}: ${amount}")
```

## Summary

✅ **Lists** - Mutable, use square brackets `[]`  
✅ **List methods** - append, insert, remove, pop, sort, etc.  
✅ **List comprehensions** - Concise way to create lists  
✅ **Tuples** - Immutable, use parentheses `()`  
✅ **Tuple unpacking** - Assign multiple variables at once  
✅ **Choose wisely** - Lists for changing data, tuples for fixed data  

---

**Next:** Practice with the interactive notebook!
