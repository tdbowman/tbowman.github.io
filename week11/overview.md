# Week 11: JSON, SQL & PostgreSQL

## Overview

Welcome to Week 11! Learn to work with JSON data format and connect Python to PostgreSQL databases for powerful data management.

## Learning Objectives

- Work with JSON data in Python
- Read and write JSON files
- Convert between Python objects and JSON
- Connect to PostgreSQL databases
- Execute SQL queries from Python
- Insert, update, and retrieve data
- Use parameters safely to prevent SQL injection

## Topics Covered

1. **JSON in Python**
   - What is JSON?
   - json.loads() and json.dumps()
   - Reading/writing JSON files
   - Working with nested JSON

2. **PostgreSQL Basics**
   - What is PostgreSQL?
   - Installing psycopg2
   - Connecting to databases
   - Creating tables

3. **SQL Operations**
   - SELECT queries
   - INSERT, UPDATE, DELETE
   - WHERE clauses
   - Parameters and safety

4. **Python + PostgreSQL**
   - Executing queries
   - Fetching results
   - Using cursors
   - Transaction management

## Assignments This Week

```{note}
All assignments are due by 11:59 PM on the specified date in Canvas
```

- **Assignment 2** - Due this week
- **Weekly Discussion** - Participate in forum


## Readings

**Required:**
### JSON
- [Real Python - Working with JSON data](https://realpython.com/python-json/)
- [The Hitchhiker's Guide to Python > JSON](https://docs.python-guide.org/scenarios/json/)
- [W3C > Python JSON](https://www.w3schools.com/python/python_json.asp)
- [The New Stack > Python for Beginners: How to Use JSON in Python](https://thenewstack.io/python-for-beginners-how-to-use-json-in-python/)

### XML
- [Real Python > A Roadmap to XML Parsers in Python](https://realpython.com/python-xml-parser/)
- [The Hitchhiker's Guide to Python > XML Parsing](https://docs.python-guide.org/scenarios/xml/)

### POSTGRESQL
- [FreeCodeCamp > How to Use Postgres in Python](https://www.freecodecamp.org/news/postgresql-in-python/)
- [PYnative > Python PostgreSQL Tutorial Using Psycopg2](https://pynative.com/python-postgresql-tutorial/)

---

## JSON in Python - Quick Guide

### JSON Basics

```python
import json

# Python to JSON (serialize)
data = {
    "name": "Alice",
    "age": 25,
    "courses": ["Python", "SQL", "Data Science"]
}

json_string = json.dumps(data, indent=2)
print(json_string)

# JSON to Python (deserialize)
json_data = '{"name": "Bob", "age": 30}'
python_dict = json.loads(json_data)
print(python_dict)
```

### Reading/Writing JSON Files

```python
import json

# Write to file
data = {"students": [{"name": "Alice", "grade": 95}]}
with open("data.json", "w") as file:
    json.dump(data, file, indent=2)

# Read from file
with open("data.json", "r") as file:
    data = json.load(file)
    print(data)
```

## PostgreSQL with Python

### Installing psycopg2

```bash
pip install psycopg2-binary --break-system-packages
```

### Connecting to Database

```python
import psycopg2

# Connection parameters
conn = psycopg2.connect(
    host="localhost",
    database="mydb",
    user="username",
    password="password"
)

# Create cursor
cursor = conn.cursor()

# Execute query
cursor.execute("SELECT version();")
version = cursor.fetchone()
print(version)

# Close connections
cursor.close()
conn.close()
```

### Better Way - Context Manager

```python
import psycopg2

with psycopg2.connect(
    host="localhost",
    database="mydb",
    user="username",
    password="password"
) as conn:
    with conn.cursor() as cursor:
        cursor.execute("SELECT * FROM students")
        results = cursor.fetchall()
        for row in results:
            print(row)
```

### Creating Tables

```python
import psycopg2

with psycopg2.connect(...) as conn:
    with conn.cursor() as cursor:
        cursor.execute("""
            CREATE TABLE IF NOT EXISTS students (
                id SERIAL PRIMARY KEY,
                name VARCHAR(100),
                age INTEGER,
                grade FLOAT
            )
        """)
        conn.commit()
```

### Inserting Data (Safe Way)

```python
# Use parameters to prevent SQL injection!
with psycopg2.connect(...) as conn:
    with conn.cursor() as cursor:
        # Single insert
        cursor.execute(
            "INSERT INTO students (name, age, grade) VALUES (%s, %s, %s)",
            ("Alice", 20, 95.5)
        )
        
        # Multiple inserts
        students = [
            ("Bob", 21, 87.0),
            ("Charlie", 22, 92.5)
        ]
        cursor.executemany(
            "INSERT INTO students (name, age, grade) VALUES (%s, %s, %s)",
            students
        )
        
        conn.commit()
```

### Querying Data

```python
with psycopg2.connect(...) as conn:
    with conn.cursor() as cursor:
        # Fetch all
        cursor.execute("SELECT * FROM students")
        all_students = cursor.fetchall()
        
        # Fetch one
        cursor.execute("SELECT * FROM students WHERE id = %s", (1,))
        student = cursor.fetchone()
        
        # Iterate results
        cursor.execute("SELECT name, grade FROM students WHERE grade > %s", (90,))
        for name, grade in cursor:
            print(f"{name}: {grade}")
```

### Updating and Deleting

```python
with psycopg2.connect(...) as conn:
    with conn.cursor() as cursor:
        # Update
        cursor.execute(
            "UPDATE students SET grade = %s WHERE name = %s",
            (96.0, "Alice")
        )
        
        # Delete
        cursor.execute(
            "DELETE FROM students WHERE grade < %s",
            (70,)
        )
        
        conn.commit()
```

## Practical Example: Student Database

```python
import psycopg2
import json

class StudentDatabase:
    def __init__(self, conn_params):
        self.conn_params = conn_params
    
    def add_student(self, name, age, grade):
        with psycopg2.connect(**self.conn_params) as conn:
            with conn.cursor() as cursor:
                cursor.execute(
                    "INSERT INTO students (name, age, grade) VALUES (%s, %s, %s)",
                    (name, age, grade)
                )
                conn.commit()
    
    def get_all_students(self):
        with psycopg2.connect(**self.conn_params) as conn:
            with conn.cursor() as cursor:
                cursor.execute("SELECT * FROM students ORDER BY name")
                return cursor.fetchall()
    
    def export_to_json(self, filename):
        students = self.get_all_students()
        data = [
            {"id": s[0], "name": s[1], "age": s[2], "grade": s[3]}
            for s in students
        ]
        with open(filename, "w") as file:
            json.dump(data, file, indent=2)

# Use it
db = StudentDatabase({
    "host": "localhost",
    "database": "school",
    "user": "user",
    "password": "pass"
})

db.add_student("Alice", 20, 95.5)
students = db.get_all_students()
db.export_to_json("students.json")
```

## Summary

✅ **JSON** - Lightweight data format  
✅ **json module** - Parse and generate JSON  
✅ **PostgreSQL** - Powerful relational database  
✅ **psycopg2** - Python PostgreSQL adapter  
✅ **Parameters** - Safe SQL execution  
✅ **CRUD operations** - Create, Read, Update, Delete  
