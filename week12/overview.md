# Week 12: Object-Oriented Programming (OOP)

## Overview

Welcome to Week 12! Object-Oriented Programming (OOP) is a powerful programming paradigm that lets you organize code around objects and classes.

## Learning Objectives

- Understand OOP concepts (classes, objects, inheritance)
- Create classes and objects
- Use attributes and methods
- Understand `__init__` and `self`
- Implement inheritance
- Use encapsulation principles
- Apply OOP to real problems

## Topics Covered

1. **Classes and Objects**
   - What are classes?
   - Creating classes
   - Instantiating objects
   - Class vs instance

2. **Attributes and Methods**
   - Instance attributes
   - Class attributes
   - Instance methods
   - `__init__` constructor

3. **Special Methods**
   - `__str__` and `__repr__`
   - `__len__`, `__eq__`
   - Magic methods

4. **Inheritance**
   - Parent and child classes
   - Overriding methods
   - `super()` function
   - Multiple inheritance

5. **Encapsulation**
   - Private attributes
   - Getter and setter methods
   - Property decorators

## Assignments This Week

```{note}
All assignments are due by 11:59 PM on the specified date in Canvas
```

- **Weekly Discussion** - Participate in forum

---

## OOP Quick Guide

### Creating a Class

```python
class Dog:
    # Class attribute
    species = "Canis familiaris"
    
    # Constructor
    def __init__(self, name, age):
        # Instance attributes
        self.name = name
        self.age = age
    
    # Instance method
    def bark(self):
        return f"{self.name} says Woof!"
    
    def description(self):
        return f"{self.name} is {self.age} years old"

# Create objects
buddy = Dog("Buddy", 3)
max_dog = Dog("Max", 5)

# Use methods
print(buddy.bark())  # "Buddy says Woof!"
print(buddy.description())  # "Buddy is 3 years old"
print(buddy.species)  # "Canis familiaris"
```

### The __str__ Method

```python
class Book:
    def __init__(self, title, author, year):
        self.title = title
        self.author = author
        self.year = year
    
    def __str__(self):
        return f"'{self.title}' by {self.author} ({self.year})"

book = Book("1984", "George Orwell", 1949)
print(book)  # '1984' by George Orwell (1949)
```

### Inheritance

```python
class Animal:
    def __init__(self, name):
        self.name = name
    
    def speak(self):
        return "Some sound"

class Dog(Animal):
    def speak(self):
        return f"{self.name} says Woof!"

class Cat(Animal):
    def speak(self):
        return f"{self.name} says Meow!"

dog = Dog("Buddy")
cat = Cat("Whiskers")

print(dog.speak())  # "Buddy says Woof!"
print(cat.speak())  # "Whiskers says Meow!"
```

### Using super()

```python
class Vehicle:
    def __init__(self, brand, model):
        self.brand = brand
        self.model = model
    
    def info(self):
        return f"{self.brand} {self.model}"

class Car(Vehicle):
    def __init__(self, brand, model, doors):
        super().__init__(brand, model)
        self.doors = doors
    
    def info(self):
        base_info = super().info()
        return f"{base_info} with {self.doors} doors"

car = Car("Toyota", "Camry", 4)
print(car.info())  # "Toyota Camry with 4 doors"
```

### Practical Example: Bank Account

```python
class BankAccount:
    def __init__(self, owner, balance=0):
        self.owner = owner
        self.balance = balance
        self.transactions = []
    
    def deposit(self, amount):
        if amount > 0:
            self.balance += amount
            self.transactions.append(f"Deposited ${amount}")
            return True
        return False
    
    def withdraw(self, amount):
        if amount > 0 and amount <= self.balance:
            self.balance -= amount
            self.transactions.append(f"Withdrew ${amount}")
            return True
        return False
    
    def get_balance(self):
        return self.balance
    
    def __str__(self):
        return f"Account({self.owner}): ${self.balance:.2f}"

# Use it
account = BankAccount("Alice", 1000)
account.deposit(500)
account.withdraw(200)
print(account)  # "Account(Alice): $1300.00"
print(f"Balance: ${account.get_balance()}")
```

### Encapsulation with Properties

```python
class Temperature:
    def __init__(self, celsius):
        self._celsius = celsius
    
    @property
    def celsius(self):
        return self._celsius
    
    @celsius.setter
    def celsius(self, value):
        if value < -273.15:
            raise ValueError("Temperature below absolute zero!")
        self._celsius = value
    
    @property
    def fahrenheit(self):
        return self._celsius * 9/5 + 32
    
    @fahrenheit.setter
    def fahrenheit(self, value):
        self.celsius = (value - 32) * 5/9

# Use it
temp = Temperature(25)
print(temp.celsius)     # 25
print(temp.fahrenheit)  # 77.0

temp.fahrenheit = 86
print(temp.celsius)     # 30.0
```

## When to Use OOP

Use classes when:
- You have data with related behaviors
- You need multiple instances of something
- You want to organize complex code
- You're modeling real-world entities

Examples:
- User accounts
- Products in inventory
- Game characters
- Database records
- UI components

## Summary

✅ **Classes** - Blueprints for objects  
✅ **Objects** - Instances of classes  
✅ **`__init__`** - Constructor method  
✅ **self** - Reference to current instance  
✅ **Inheritance** - Reuse and extend classes  
✅ **Encapsulation** - Hide implementation details  
