# Working with Files in Python

## Opening and Reading Files

### The Basic Way (Not Recommended)

```python
# Open file
file = open("data.txt", "r")

# Read content
content = file.read()
print(content)

# MUST close file!
file.close()
```

### The Better Way - with Statement

```python
# File automatically closes when done
with open("data.txt", "r") as file:
    content = file.read()
    print(content)

# File is already closed here!
```

```{important}
**Always use `with open()` for file operations!**  
It automatically closes files even if errors occur.
```

## File Modes

| Mode | Meaning | Creates if Missing? |
|------|---------|---------------------|
| `'r'` | Read (default) | No - Error if missing |
| `'w'` | Write (overwrites!) | Yes |
| `'a'` | Append | Yes |
| `'r+'` | Read and write | No |
| `'w+'` | Write and read | Yes |
| `'b'` | Binary mode | Use with others: 'rb', 'wb' |

## Reading Files

### read() - Entire File as String

```python
with open("story.txt", "r") as file:
    content = file.read()
    print(content)
    print(type(content))  # str
```

### readline() - One Line at a Time

```python
with open("data.txt", "r") as file:
    line1 = file.readline()
    line2 = file.readline()
    print(line1)  # First line
    print(line2)  # Second line
```

### readlines() - All Lines as List

```python
with open("data.txt", "r") as file:
    lines = file.readlines()
    print(type(lines))  # list
    for line in lines:
        print(line.strip())  # Remove \n
```

### Best Way - Iterate Directly

```python
with open("data.txt", "r") as file:
    for line in file:
        print(line.strip())
```

## Writing Files

### Write to File

```python
# Write (overwrites file!)
with open("output.txt", "w") as file:
    file.write("Hello, World!\n")
    file.write("This is line 2.\n")
```

### Append to File

```python
# Append (adds to end)
with open("log.txt", "a") as file:
    file.write("New log entry\n")
```

### Write Multiple Lines

```python
lines = [
    "First line\n",
    "Second line\n",
    "Third line\n"
]

with open("output.txt", "w") as file:
    file.writelines(lines)
```

## CSV Files

### Reading CSV

```python
import csv

with open("students.csv", "r") as file:
    reader = csv.reader(file)
    
    # Skip header
    header = next(reader)
    
    # Process rows
    for row in reader:
        print(row)  # row is a list
```

### Writing CSV

```python
import csv

students = [
    ["Name", "Age", "Grade"],
    ["Alice", "20", "A"],
    ["Bob", "21", "B"]
]

with open("output.csv", "w", newline='') as file:
    writer = csv.writer(file)
    writer.writerows(students)
```

### CSV with Dictionaries

```python
import csv

# Reading
with open("students.csv", "r") as file:
    reader = csv.DictReader(file)
    for row in reader:
        print(row["Name"], row["Age"])

# Writing
students = [
    {"Name": "Alice", "Age": 20},
    {"Name": "Bob", "Age": 21}
]

with open("output.csv", "w", newline='') as file:
    fieldnames = ["Name", "Age"]
    writer = csv.DictWriter(file, fieldnames=fieldnames)
    writer.writeheader()
    writer.writerows(students)
```

## Error Handling

```python
try:
    with open("data.txt", "r") as file:
        content = file.read()
        print(content)
except FileNotFoundError:
    print("File not found!")
except PermissionError:
    print("Permission denied!")
```

## Practical Examples

### Example 1: Word Counter

```python
with open("document.txt", "r") as file:
    text = file.read()
    words = text.split()
    print(f"Word count: {len(words)}")
```

### Example 2: Log Analyzer

```python
error_count = 0
with open("server.log", "r") as file:
    for line in file:
        if "ERROR" in line:
            error_count += 1
            print(line.strip())

print(f"\nTotal errors: {error_count}")
```

### Example 3: Grade Report

```python
# Read grades
grades = {}
with open("grades.csv", "r") as file:
    reader = csv.reader(file)
    next(reader)  # Skip header
    for name, score in reader:
        grades[name] = int(score)

# Calculate statistics
average = sum(grades.values()) / len(grades)

# Write report
with open("report.txt", "w") as file:
    file.write("Grade Report\n")
    file.write("=" * 40 + "\n\n")
    for name, score in grades.items():
        file.write(f"{name}: {score}\n")
    file.write(f"\nAverage: {average:.1f}\n")
```

## Summary

✅ **with open()** - Always use for automatic file closing  
✅ **Modes** - 'r' read, 'w' write (overwrite), 'a' append  
✅ **Reading** - read(), readline(), readlines(), or iterate  
✅ **Writing** - write(), writelines()  
✅ **CSV module** - Easy CSV file handling  
✅ **Error handling** - Use try/except for file operations  
