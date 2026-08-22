# Glossary

Terms used in this book, in plain language. Where a term is introduced in a
particular week, that week is noted so you can go back and see it in context.

```{glossary}
`__init__`
: The method Python runs automatically when you create an object. Its job is to
  set up the object's starting state. Also called the *constructor*. (Week 12)

`__str__`
: The method that says how your object should look when printed. Without one you
  get `<object at 0x7f...>`; with one you get something readable. (Week 12)

accumulator
: A variable that collects a running result inside a loop — a total, a count, a
  longest-so-far. Set it up *before* the loop, add to it *inside*. (Week 5)

argument
: The actual value you hand to a function when you call it. In
  `calculate_fine(12)`, `12` is the argument. Compare {term}`parameter`. (Week 4)

API
: Application Programming Interface. A doorway one program opens so other
  programs can ask it for things. A *web* API is a URL that returns data —
  usually {term}`JSON` — instead of a web page. (Week 10)

attribute
: A piece of data attached to an object, reached with a dot: `book.title`. An
  *instance* attribute belongs to one object; a *class* attribute is shared by
  all objects of that class. (Week 12)

boolean
: A value that is either `True` or `False`. Every comparison produces one, and
  every decision a program makes rests on one. (Week 2)

break
: A statement that stops a loop immediately and continues after it. Compare
  {term}`continue`. (Week 5)

bug
: Behaviour you didn't intend. Not a moral failing — the normal condition of
  working software.

class
: A blueprint for building objects: what they know and what they can do. `Book`
  is a class; a particular book is an {term}`object`. (Week 12)

comment
: Text in a program that Python ignores, marked with `#`. Good comments explain
  *why*, not *what*. (Week 1)

comprehension
: A compact way to build a list or dictionary from another collection:
  `[title for title, count in circulation if count > 40]`. (Weeks 6–7)

composition
: Building a class that *holds* other objects — a `Library` **has** items. The
  usual alternative to {term}`inheritance`, and more often the right one.
  (Week 12)

constructor
: See `__init__`, above.

continue
: A statement that skips the rest of the current loop iteration and moves to the
  next item. Compare {term}`break`. (Week 5)

CSV
: Comma-Separated Values. A plain-text table, one record per line. Use Python's
  `csv` module rather than splitting on commas yourself — real data contains
  commas. (Week 9)

cursor
: In database work, the object you run SQL statements on and fetch results from.
  (Week 11)

dictionary
: A collection of key–value pairs, written with curly braces. Good at *lookup*:
  give me the value stored under this key. (Week 7)

docstring
: A string on the first line of a function or class that says what it does.
  `help()` reads it back to you. (Week 4)

dunder method
: A method whose name is wrapped in double underscores, like `__init__` or
  `__str__`. They hook your class into Python's built-in syntax. (Week 12)

encapsulation
: Keeping an object's internals private so outside code can't put it into an
  invalid state. In Python this is convention (a leading underscore) plus
  {term}`property`. (Week 12)

exception
: Python's way of reporting that something went wrong. Catch the ones you can
  handle with `try` / `except`; let the rest stop the program loudly. (Week 9)

f-string
: A string prefixed with `f` where `{expressions}` inside the braces are
  evaluated and inserted: `f"{name} owes ${fine:.2f}"`. (Week 1)

float
: A number with a decimal point. (Week 2)

function
: A named piece of work you can call more than once. Defined with `def`. (Week 4)

GitHub
: A website that hosts Git repositories. Where you'll store your code, and where
  this book lives.

immutable
: Cannot be changed after it's created. Strings and {term}`tuple`s are immutable;
  lists and dictionaries are not. (Week 6)

indentation
: The leading spaces that tell Python which statements belong inside an `if`, a
  loop, or a function. In Python this is syntax, not style. (Week 2)

index
: The position of an item in a sequence, counting from **0**. `titles[0]` is the
  first title. (Week 3)

inheritance
: Defining a class that starts from another class and overrides only what
  differs — a `DVD` **is a** `LibraryItem`. (Week 12)

int
: A whole number, positive or negative. (Week 2)

iterate
: To go through the items of a collection one at a time, usually with a `for`
  loop. (Week 5)

JSON
: JavaScript Object Notation. The usual text format for data moving between
  programs. Once parsed, it's just Python dictionaries and lists. (Weeks 10–11)

Jupyter Notebook
: A document that mixes prose, code, and the code's output. What most of this
  book is written in.

key
: The name you look something up by in a {term}`dictionary`. (Week 7)

library
: A body of code someone else wrote that you can use — `requests`, `pandas`,
  `csv`. Also called a package or, loosely, a {term}`module`.

list
: An ordered, changeable collection, written with square brackets. (Week 6)

loop
: A construct that repeats work. `for` when you know what you're going over,
  `while` when you only know when to stop. (Week 5)

method
: A {term}`function` that belongs to a class and receives the object as `self`.
  (Week 12)

module
: A `.py` file whose contents you can `import` into another program. (Week 8)

mutable
: Can be changed after it's created. Lists and dictionaries are mutable.
  Compare {term}`immutable`. (Week 6)

object
: A particular thing built from a {term}`class`, with its own data. (Week 12)

operator
: A symbol that does something to values: `+ - * / // % ** == != < > and or not`.
  (Week 2)

parameter
: The name a function gives to a value it expects. In
  `def calculate_fine(days_overdue):`, `days_overdue` is the parameter. Compare
  {term}`argument`. (Week 4)

parse
: To read text in some format and turn it into structured data you can work with
  — for example, turning a JSON string into a dictionary. (Week 10)

placeholder
: In SQL, the `?` or `%s` marks that let the database driver insert values
  safely. Building SQL with f-strings instead is how SQL injection happens.
  (Week 11)

polymorphism
: Different classes responding to the same method call in their own way, so code
  that uses them doesn't need to know which is which. (Week 12)

property
: A method that behaves like an attribute, letting you validate on assignment or
  compute a value on demand. (Week 12)

REST
: A common style for web APIs: addressable URLs, standard HTTP methods, and data
  in and out. (Week 10)

return
: What a function hands back to whoever called it. A function that only `print`s
  returns `None` — a distinction that catches nearly everyone once. (Week 4)

scope
: Where a name is visible. Names created inside a function live only there.
  (Week 4)

self
: The first parameter of every method — a reference to the object the method was
  called on. (Week 12)

sense-think-act
: The control loop at the heart of robotics: read the sensors, decide, do one
  thing, repeat. (Weeks 13–14)

slice
: A section of a sequence, written `thing[start:stop]`. The start is included,
  the stop is not. (Weeks 3, 6)

snake_case
: Python's naming convention: lowercase words joined by underscores, as in
  `days_overdue`. (Week 1)

SQL
: Structured Query Language. How you ask a relational database for things.
  (Week 11)

status code
: The number a web server returns to say how a request went. `200` success,
  `404` not found, `429` slow down, `500` their problem. (Week 10)

string
: Text, written in quotes. (Week 1)

syntax
: The grammar of the language — the rules about what counts as valid Python. A
  `SyntaxError` means Python couldn't even read your code, let alone run it.
  (Week 2)

traceback
: The block of text Python prints when an exception isn't caught. Read it from
  the **bottom up**: the last line names the error, the lines above show how you
  got there.

tuple
: An ordered collection that cannot be changed, written with round brackets.
  Right for fixed records like `("Dune", 42)`. (Week 6)

type
: What kind of value something is — `int`, `float`, `str`, `bool`, `list`,
  `dict`. `type(value)` tells you. (Week 2)

variable
: A name that points at a value. (Week 1)

with statement
: The construct that opens a resource and guarantees it gets closed, even if an
  error occurs: `with open("data.txt") as file:`. Always use it for files.
  (Week 9)
```

---

## A Note on Looking Things Up

Nobody memorizes all of this. Professional programmers look up syntax constantly
— the skill is knowing *what* to look up and *where*, not holding it all in your
head.

When you're stuck, in this order:

1. **Read the error message.** Bottom line first. It usually names the problem.
2. **Check this glossary** for the term you half-remember.
3. **Check the [official docs](https://docs.python.org/3/)** for what a function
   actually does.
4. **Ask.** Discussion board, office hours, a classmate.
