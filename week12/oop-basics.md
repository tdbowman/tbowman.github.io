# Object-Oriented Programming in Python

## Why Classes?

Suppose you're tracking books in a small library. With what you know so far, you might reach for parallel lists:

```python
titles  = ["Dune", "Beloved", "Neuromancer"]
authors = ["Herbert", "Morrison", "Gibson"]
years   = [1965, 1987, 1984]
checked_out = [False, True, False]

# Who wrote the second book?
print(authors[1])
```

This works until it doesn't. Sort one list and the others no longer line up. Insert a book in the middle and you must remember to insert into all four. Add a fifth attribute and every function that touches a book needs another parameter.

The problem is that one book's data has been scattered across four places. A **class** lets you keep it together:

```python
class Book:
    def __init__(self, title, author, year):
        self.title = title
        self.author = author
        self.year = year
        self.checked_out = False

dune = Book("Dune", "Herbert", 1965)
print(dune.author)      # Herbert
```

Now a book is one thing. It cannot fall out of sync with itself.

```{note}
A **class** is the blueprint. An **object** (or *instance*) is a thing built from that blueprint. `Book` is the class; `dune` is an object.
```

## Your First Class

```python
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def bark(self):
        return f"{self.name} says Woof!"

buddy = Dog("Buddy", 3)
maisie = Dog("Maisie", 7)

print(buddy.bark())     # Buddy says Woof!
print(maisie.bark())    # Maisie says Woof!
print(maisie.age)       # 7
```

Three things to notice:

- `class Dog:` — class names use `CapitalCase` by convention
- `__init__` runs automatically when you write `Dog(...)`
- Every method's first parameter is `self`

## `__init__` and `self`

`__init__` is the **constructor**. Python calls it for you the moment an object is created, and its job is to set up the object's starting state.

```python
class Student:
    def __init__(self, name, program):
        print(f"Creating a student record for {name}")
        self.name = name
        self.program = program
        self.credits = 0        # every new student starts at zero

s = Student("Ana", "MLIS")     # prints "Creating a student record for Ana"
print(s.credits)               # 0
```

`self` is the object the method was called on. When you write `s.name`, Python passes `s` in as `self` behind the scenes. That's why you write `def bark(self)` with a parameter, but call `buddy.bark()` without one.

```{important}
Assigning `self.name = name` stores the value **on the object**. A plain `name = name` inside a method creates a local variable that vanishes when the method ends — one of the most common beginner bugs in OOP.
```

### Default Values

```python
class Student:
    def __init__(self, name, program="Undeclared", credits=0):
        self.name = name
        self.program = program
        self.credits = credits

a = Student("Ana", "MLIS", 12)
b = Student("Ben")                  # program and credits use the defaults

print(b.program)    # Undeclared
```

## Instance Attributes vs Class Attributes

An **instance attribute** belongs to one object. A **class attribute** is shared by every object of that class.

```python
class Dog:
    species = "Canis familiaris"        # class attribute — shared

    def __init__(self, name):
        self.name = name                # instance attribute — per object

buddy = Dog("Buddy")
maisie = Dog("Maisie")

print(buddy.species)     # Canis familiaris
print(maisie.species)    # Canis familiaris — same value, one copy
print(buddy.name)        # Buddy
print(maisie.name)       # Maisie — different values
```

Class attributes are good for constants and for counters:

```python
class Robot:
    count = 0                    # how many robots exist

    def __init__(self, name):
        self.name = name
        Robot.count += 1         # note: Robot.count, not self.count

r1 = Robot("Wall-E")
r2 = Robot("Eve")
print(Robot.count)               # 2
```

```{warning}
Never use a mutable value (a list or dictionary) as a class attribute unless you mean to share it. `history = []` at class level gives *every* object the same list, and appending from one object changes it for all of them. Put mutable state in `__init__` instead: `self.history = []`.
```

## Methods

A **method** is a function that lives on a class and knows about the object it was called on.

```python
class BankAccount:
    def __init__(self, owner, balance=0):
        self.owner = owner
        self.balance = balance
        self.history = []

    def deposit(self, amount):
        if amount <= 0:
            return False
        self.balance += amount
        self.history.append(f"Deposited ${amount}")
        return True

    def withdraw(self, amount):
        if amount <= 0 or amount > self.balance:
            return False
        self.balance -= amount
        self.history.append(f"Withdrew ${amount}")
        return True

    def statement(self):
        lines = [f"Account: {self.owner}", "-" * 30]
        lines.extend(self.history)
        lines.append(f"Balance: ${self.balance:.2f}")
        return "\n".join(lines)

account = BankAccount("Alice", 1000)
account.deposit(500)
account.withdraw(200)
print(account.statement())
```

Methods can call other methods on the same object through `self`:

```python
class Rectangle:
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

    def describe(self):
        return f"{self.width}x{self.height} rectangle, area {self.area()}"

print(Rectangle(3, 4).describe())    # 3x4 rectangle, area 12
```

## `__str__`: Making Objects Printable

By default, printing an object gives you something useless:

```python
book = Book("Dune", "Herbert", 1965)
print(book)      # <__main__.Book object at 0x104f2e910>
```

`__str__` tells Python how to turn your object into readable text:

```python
class Book:
    def __init__(self, title, author, year):
        self.title = title
        self.author = author
        self.year = year

    def __str__(self):
        return f"'{self.title}' by {self.author} ({self.year})"

book = Book("Dune", "Herbert", 1965)
print(book)              # 'Dune' by Herbert (1965)
print(f"Reading {book}") # Reading 'Dune' by Herbert (1965)
```

```{tip}
Write a `__str__` for every class you create. It takes thirty seconds and makes debugging enormously easier — every `print()` starts telling you something useful.
```

## Other Special Methods

Methods named with double underscores hook your class into Python's built-in syntax.

```python
class Playlist:
    def __init__(self, name):
        self.name = name
        self.songs = []

    def add(self, song):
        self.songs.append(song)

    def __str__(self):
        return f"{self.name} ({len(self.songs)} songs)"

    def __len__(self):
        return len(self.songs)

    def __contains__(self, song):
        return song in self.songs

    def __eq__(self, other):
        return self.songs == other.songs

mix = Playlist("Study Mix")
mix.add("Clair de Lune")
mix.add("Blue in Green")

print(len(mix))                    # 2      — because of __len__
print("Blue in Green" in mix)      # True   — because of __contains__
print(mix)                         # Study Mix (2 songs)
```

| Method | Enables |
|--------|---------|
| `__str__` | `print(obj)`, `str(obj)`, f-strings |
| `__repr__` | How the object shows in the interpreter and inside lists |
| `__len__` | `len(obj)` |
| `__eq__` | `obj1 == obj2` |
| `__contains__` | `item in obj` |
| `__getitem__` | `obj[0]` |

## Inheritance

Inheritance lets a class start from another class and change only what's different.

```python
class LibraryItem:
    def __init__(self, title, item_id):
        self.title = title
        self.item_id = item_id
        self.checked_out = False

    def check_out(self):
        if self.checked_out:
            return f"{self.title} is already out"
        self.checked_out = True
        return f"Checked out: {self.title}"

    def loan_period(self):
        return 21        # days

    def __str__(self):
        return f"[{self.item_id}] {self.title}"


class DVD(LibraryItem):
    def loan_period(self):
        return 7         # DVDs go out for one week, not three


class ReferenceBook(LibraryItem):
    def check_out(self):
        return f"{self.title} is reference — library use only"
```

```python
items = [
    LibraryItem("Dune", "B001"),
    DVD("Arrival", "D014"),
    ReferenceBook("Oxford English Dictionary", "R002"),
]

for item in items:
    print(item)
    print("  ", item.check_out())
    print("  ", f"{item.loan_period()} day loan")
```

`DVD` and `ReferenceBook` never define `__init__` or `__str__` — they inherit them. Each **overrides** only the one method that differs.

```{note}
This is **polymorphism**: the loop above calls `item.check_out()` without knowing or caring which class each item is. Each object supplies its own behavior.
```

### `super()` — Extending Instead of Replacing

When a child class needs everything the parent does *plus* something extra, call `super()`:

```python
class Vehicle:
    def __init__(self, make, model):
        self.make = make
        self.model = model

    def describe(self):
        return f"{self.make} {self.model}"


class ElectricCar(Vehicle):
    def __init__(self, make, model, range_miles):
        super().__init__(make, model)      # run the parent's setup first
        self.range_miles = range_miles     # then add our own

    def describe(self):
        return f"{super().describe()} — {self.range_miles} mile range"


car = ElectricCar("Tesla", "Model 3", 272)
print(car.describe())     # Tesla Model 3 — 272 mile range
print(car.make)           # Tesla — inherited attribute
```

```{important}
If a child class defines `__init__` and forgets to call `super().__init__(...)`, the parent's attributes are never created — and you get an `AttributeError` later, far from the real cause.
```

## Encapsulation

Encapsulation means hiding an object's internals so that outside code can't put it into an invalid state.

Python has no truly private attributes. Instead there's a convention: **a leading underscore means "internal, don't touch."**

```python
class Thermostat:
    def __init__(self, temperature):
        self._temperature = temperature      # internal by convention
```

### Properties

A `@property` lets you run code when an attribute is read or written, while still using plain attribute syntax:

```python
class Thermostat:
    def __init__(self, celsius):
        self._celsius = celsius

    @property
    def celsius(self):
        return self._celsius

    @celsius.setter
    def celsius(self, value):
        if value < -273.15:
            raise ValueError("Below absolute zero")
        self._celsius = value

    @property
    def fahrenheit(self):
        """Computed on demand — never stored, so it can't go stale."""
        return self._celsius * 9 / 5 + 32


t = Thermostat(20)
print(t.celsius)       # 20        — calls the getter
print(t.fahrenheit)    # 68.0      — computed
t.celsius = 25         # calls the setter, which validates
print(t.fahrenheit)    # 77.0      — automatically consistent

t.celsius = -300       # ValueError: Below absolute zero
```

The payoff: `fahrenheit` can never disagree with `celsius`, because it isn't stored separately.

## Composition: Objects Inside Objects

Inheritance says a DVD **is a** library item. Composition says a library **has** items. Most real designs need more composition than inheritance.

```python
class Library:
    def __init__(self, name):
        self.name = name
        self.items = []          # a list of LibraryItem objects

    def add(self, item):
        self.items.append(item)

    def available(self):
        return [item for item in self.items if not item.checked_out]

    def __len__(self):
        return len(self.items)


crown = Library("Rebecca Crown Library")
crown.add(LibraryItem("Dune", "B001"))
crown.add(DVD("Arrival", "D014"))

crown.items[0].check_out()

print(f"{crown.name}: {len(crown)} items, {len(crown.available())} available")
```

```{tip}
When you're deciding between the two, say it out loud. "A DVD **is a** library item" — inheritance. "A library **has** items" — composition. If neither sentence sounds right, you probably want a plain function.
```

## Designing a Class

Before you write `class`, answer four questions:

1. **What is this thing?** One noun. `Book`, `Robot`, `Playlist` — not `BookManagerHelper`.
2. **What does it know?** Those become attributes set in `__init__`.
3. **What can it do?** Those become methods.
4. **What must always be true about it?** A balance is never negative; a temperature is never below absolute zero. Enforce it in the setter or the method.

```{note}
If a class has only data and no behavior, a dictionary may serve you better. If it has only behavior and no data, a function may serve you better. Classes earn their keep when data and behavior belong together.
```

## Practical Example: A Catalog Search

Everything so far, in one small program:

```python
class CatalogRecord:
    def __init__(self, title, author, year, subjects=None):
        self.title = title
        self.author = author
        self.year = year
        self.subjects = subjects or []

    def matches(self, term):
        """True if the term appears in any searchable field."""
        term = term.lower()
        haystack = [self.title, self.author] + self.subjects
        return any(term in field.lower() for field in haystack)

    def __str__(self):
        return f"{self.author} ({self.year}). {self.title}."


class Catalog:
    def __init__(self):
        self.records = []

    def add(self, record):
        self.records.append(record)

    def search(self, term):
        return [r for r in self.records if r.matches(term)]

    def __len__(self):
        return len(self.records)


catalog = Catalog()
catalog.add(CatalogRecord("Dune", "Herbert, Frank", 1965, ["science fiction", "ecology"]))
catalog.add(CatalogRecord("Beloved", "Morrison, Toni", 1987, ["historical fiction"]))
catalog.add(CatalogRecord("Silent Spring", "Carson, Rachel", 1962, ["ecology", "environment"]))

print(f"Catalog holds {len(catalog)} records\n")

for record in catalog.search("ecology"):
    print(record)
```

Output:

```
Catalog holds 3 records

Herbert, Frank (1965). Dune.
Carson, Rachel (1962). Silent Spring.
```

## Looking Ahead: Your Robot Is an Object

Block 4 asks you to build a virtual robot. Everything on this page is what makes that possible:

```python
class Robot:
    def __init__(self, x, y):
        self.x = x                  # what it knows: position
        self.y = y
        self.direction = "north"
        self.log = []               # and its own history

    def move_forward(self):         # what it can do
        if self.direction == "north":
            self.y += 1
        elif self.direction == "south":
            self.y -= 1
        elif self.direction == "east":
            self.x += 1
        else:
            self.x -= 1
        self.log.append(f"moved {self.direction} to ({self.x}, {self.y})")

    def turn_right(self):
        order = ["north", "east", "south", "west"]
        i = order.index(self.direction)
        self.direction = order[(i + 1) % 4]

    def __str__(self):
        return f"Robot at ({self.x}, {self.y}) facing {self.direction}"


robot = Robot(0, 0)
robot.move_forward()
robot.turn_right()
robot.move_forward()
print(robot)                    # Robot at (1, 1) facing east
print(len(robot.log), "moves logged")
```

A robot is a textbook object: it has state that changes over time, behavior that depends on that state, and a job that would be miserable to write with loose variables.

## Common Mistakes

| Mistake | Symptom | Fix |
|---------|---------|-----|
| Forgetting `self` in a method definition | `TypeError: takes 0 positional arguments but 1 was given` | `def method(self):` |
| Writing `name = name` instead of `self.name = name` | Attribute doesn't exist later | Assign to `self` |
| Mutable class attribute (`items = []`) | All objects share one list | Set it in `__init__` |
| Child `__init__` without `super().__init__()` | `AttributeError` on inherited attributes | Call `super()` first |
| No `__str__` | `<object at 0x7f...>` when printing | Add `__str__` |
| Inheriting when you meant composition | Awkward, deep hierarchies | Say "is a" vs "has a" out loud |

## Summary

✅ **Class** — a blueprint; **object** — a thing built from it  
✅ **`__init__`** — runs on creation, sets up starting state  
✅ **`self`** — the object the method was called on  
✅ **Instance vs class attributes** — per object vs shared  
✅ **`__str__`** — make your objects printable  
✅ **Inheritance + `super()`** — reuse a parent, override what differs  
✅ **Properties** — validate on assignment, compute on read  
✅ **Composition** — "has a" is more often right than "is a"
