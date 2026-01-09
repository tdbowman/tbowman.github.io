# Dictionaries in Python

## What Are Dictionaries?

Dictionaries store data as **key-value pairs**. Instead of accessing items by position (like lists), you access them by a meaningful key.

```python
# List - access by position
student_list = ["Alice", 20, "CS"]
print(student_list[0])  # "Alice" - but what does position 0 mean?

# Dictionary - access by key
student_dict = {
    "name": "Alice",
    "age": 20,
    "major": "CS"
}
print(student_dict["name"])  # "Alice" - self-documenting!
```

## Creating Dictionaries

### Basic Syntax

```python
# Empty dictionary
empty_dict = {}
also_empty = dict()

# Dictionary with items
person = {
    "name": "Bob",
    "age": 25,
    "city": "Chicago"
}

# Keys and values can be different types
mixed = {
    "name": "Alice",      # string key, string value
    "age": 30,            # string key, int value
    "scores": [95, 87],   # string key, list value
    "active": True        # string key, bool value
}
```

### Key Rules

```{important}
**Keys must be:**
- **Unique** - duplicate keys overwrite previous values
- **Immutable** - strings, numbers, tuples OK; lists NOT OK

**Values can be:**
- **Any type** - strings, numbers, lists, even other dictionaries!
```

```python
# Valid keys
valid = {
    "name": "Alice",      # string key ✓
    42: "answer",         # number key ✓
    (1, 2): "coords"      # tuple key ✓
}

# Invalid key
# invalid = {
#     [1, 2]: "value"   # list key ✗ ERROR!
# }
```

## Accessing Dictionary Values

### Bracket Notation

```python
person = {
    "name": "Alice",
    "age": 25,
    "city": "Boston"
}

# Access by key
print(person["name"])  # "Alice"
print(person["age"])   # 25

# ERROR if key doesn't exist
# print(person["email"])  # KeyError!
```

### The .get() Method (Safer!)

```python
person = {"name": "Alice", "age": 25}

# get() returns None if key missing
email = person.get("email")
print(email)  # None

# get() with default value
email = person.get("email", "No email")
print(email)  # "No email"

# Compare with bracket notation
# person["email"]  # Would crash!
```

```{tip}
**Use .get() when you're not sure if a key exists!** It prevents crashes and lets you provide default values.
```

## Modifying Dictionaries

### Adding and Updating Items

```python
person = {"name": "Alice"}

# Add new key-value pair
person["age"] = 25
print(person)  # {"name": "Alice", "age": 25}

# Update existing value
person["age"] = 26
print(person)  # {"name": "Alice", "age": 26}

# Add multiple items
person["city"] = "Boston"
person["job"] = "Engineer"
```

### Deleting Items

```python
person = {
    "name": "Alice",
    "age": 25,
    "city": "Boston"
}

# del - remove item by key
del person["city"]
print(person)  # {"name": "Alice", "age": 25}

# pop() - remove and return value
age = person.pop("age")
print(age)     # 25
print(person)  # {"name": "Alice"}

# pop() with default (no error if missing)
email = person.pop("email", "Not found")
print(email)   # "Not found"

# clear() - remove all items
person.clear()
print(person)  # {}
```

## Dictionary Methods

### Getting Keys, Values, and Items

```python
student = {
    "name": "Bob",
    "age": 20,
    "major": "CS",
    "gpa": 3.7
}

# Get all keys
keys = student.keys()
print(keys)  # dict_keys(['name', 'age', 'major', 'gpa'])

# Get all values
values = student.values()
print(values)  # dict_values(['Bob', 20, 'CS', 3.7])

# Get all key-value pairs
items = student.items()
print(items)  # dict_items([('name', 'Bob'), ('age', 20), ...])

# Convert to lists
key_list = list(student.keys())
value_list = list(student.values())
```

### update() - Merge Dictionaries

```python
person = {"name": "Alice", "age": 25}
additional = {"city": "Boston", "job": "Engineer"}

# Add all items from additional to person
person.update(additional)
print(person)
# {"name": "Alice", "age": 25, "city": "Boston", "job": "Engineer"}

# update() overwrites existing keys
person.update({"age": 26, "state": "MA"})
print(person["age"])  # 26 (updated)
```

### setdefault() - Add if Missing

```python
person = {"name": "Alice"}

# Add key only if it doesn't exist
person.setdefault("age", 25)
print(person)  # {"name": "Alice", "age": 25}

# If key exists, does nothing
person.setdefault("age", 30)
print(person["age"])  # Still 25, not changed!
```

## Checking Membership

```python
person = {"name": "Alice", "age": 25, "city": "Boston"}

# Check if key exists
if "age" in person:
    print(f"Age is {person['age']}")

if "email" not in person:
    print("No email on file")

# This checks KEYS, not values
print("Alice" in person)  # False (Alice is a value, not a key)
print("name" in person)   # True (name is a key)
```

## Iterating Through Dictionaries

### Loop Through Keys

```python
person = {"name": "Alice", "age": 25, "city": "Boston"}

# Default: iterate over keys
for key in person:
    print(key)
# Output:
# name
# age
# city

# More explicit
for key in person.keys():
    print(f"{key}: {person[key]}")
```

### Loop Through Values

```python
person = {"name": "Alice", "age": 25, "city": "Boston"}

for value in person.values():
    print(value)
# Output:
# Alice
# 25
# Boston
```

### Loop Through Items (Keys AND Values)

```python
person = {"name": "Alice", "age": 25, "city": "Boston"}

# Best way to get both key and value
for key, value in person.items():
    print(f"{key}: {value}")

# Output:
# name: Alice
# age: 25
# city: Boston
```

## Nested Dictionaries

Dictionaries can contain other dictionaries:

```python
# Company with departments
company = {
    "engineering": {
        "manager": "Alice",
        "employees": 50,
        "budget": 2000000
    },
    "marketing": {
        "manager": "Bob",
        "employees": 20,
        "budget": 800000
    }
}

# Access nested values
print(company["engineering"]["manager"])  # "Alice"
print(company["marketing"]["budget"])     # 800000

# Add nested dictionary
company["sales"] = {
    "manager": "Charlie",
    "employees": 30,
    "budget": 1500000
}
```

## Lists of Dictionaries

Common pattern for storing multiple records:

```python
# List of student records
students = [
    {"name": "Alice", "age": 20, "major": "CS", "gpa": 3.8},
    {"name": "Bob", "age": 22, "major": "Math", "gpa": 3.6},
    {"name": "Charlie", "age": 21, "major": "CS", "gpa": 3.9}
]

# Process all students
for student in students:
    print(f"{student['name']} - GPA: {student['gpa']}")

# Find specific students
cs_students = [s for s in students if s["major"] == "CS"]
print(f"CS students: {len(cs_students)}")
```

## Dictionary Comprehensions

Create dictionaries concisely:

```python
# Create dictionary from two lists
keys = ["name", "age", "city"]
values = ["Alice", 25, "Boston"]
person = {k: v for k, v in zip(keys, values)}
print(person)  # {"name": "Alice", "age": 25, "city": "Boston"}

# Create dictionary with calculation
squares = {x: x**2 for x in range(5)}
print(squares)  # {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}

# With condition
even_squares = {x: x**2 for x in range(10) if x % 2 == 0}
print(even_squares)  # {0: 0, 2: 4, 4: 16, 6: 36, 8: 64}
```

## Practical Examples

### Example 1: Contact Manager

```python
contacts = {}

def add_contact(name, phone, email):
    contacts[name] = {
        "phone": phone,
        "email": email
    }
    print(f"Added {name}")

def find_contact(name):
    if name in contacts:
        contact = contacts[name]
        print(f"Name: {name}")
        print(f"Phone: {contact['phone']}")
        print(f"Email: {contact['email']}")
    else:
        print(f"{name} not found")

# Use it
add_contact("Alice", "555-1234", "alice@email.com")
add_contact("Bob", "555-5678", "bob@email.com")
find_contact("Alice")
```

### Example 2: Word Counter

```python
text = "the quick brown fox jumps over the lazy dog the fox"
words = text.split()

# Count word frequencies
word_count = {}
for word in words:
    word_count[word] = word_count.get(word, 0) + 1

# Display results
for word, count in word_count.items():
    print(f"{word}: {count}")

# Output:
# the: 3
# quick: 1
# brown: 1
# fox: 2
# ...
```

### Example 3: Gradebook

```python
gradebook = {
    "Alice": [95, 87, 92, 88],
    "Bob": [78, 85, 80, 82],
    "Charlie": [92, 94, 88, 90]
}

# Calculate averages
for student, grades in gradebook.items():
    average = sum(grades) / len(grades)
    print(f"{student}: {average:.1f}")

# Add new grade
gradebook["Alice"].append(90)

# Add new student
gradebook["Diana"] = [88, 92, 85]
```

### Example 4: Configuration Settings

```python
config = {
    "database": {
        "host": "localhost",
        "port": 5432,
        "name": "mydb"
    },
    "app": {
        "debug": True,
        "timeout": 30,
        "max_users": 100
    }
}

# Access settings
db_host = config["database"]["host"]
debug_mode = config["app"]["debug"]

# Update settings
config["app"]["timeout"] = 60
```

## Common Patterns

### Default Dictionary Pattern

```python
# Count items using get()
categories = {}
items = ["apple", "banana", "apple", "cherry", "banana", "apple"]

for item in items:
    categories[item] = categories.get(item, 0) + 1

print(categories)  # {"apple": 3, "banana": 2, "cherry": 1}
```

### Grouping Pattern

```python
# Group students by major
students = [
    {"name": "Alice", "major": "CS"},
    {"name": "Bob", "major": "Math"},
    {"name": "Charlie", "major": "CS"},
    {"name": "Diana", "major": "Math"}
]

by_major = {}
for student in students:
    major = student["major"]
    if major not in by_major:
        by_major[major] = []
    by_major[major].append(student["name"])

print(by_major)
# {"CS": ["Alice", "Charlie"], "Math": ["Bob", "Diana"]}
```

## Summary

✅ **Dictionaries** - Key-value pairs for associative data  
✅ **Keys** - Must be unique and immutable  
✅ **Values** - Can be any type  
✅ **.get()** - Safe access with defaults  
✅ **Methods** - keys(), values(), items(), update(), pop()  
✅ **Iteration** - Loop through keys, values, or items  
✅ **Nesting** - Dictionaries can contain dictionaries  
✅ **Real-world use** - Contacts, configs, data records  

---

**Next:** Practice with exercises!
