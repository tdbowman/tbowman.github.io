# Week 2 Exercises

## Exercise 2: Variable Data Types and Operations

This exercise will help you practice working with different data types, mathematical operations, and type conversions.

### Instructions

Create a new Jupyter Notebook named `week02_exercise.ipynb` and complete the following tasks. Make sure to include comments explaining your code!

---

## Part 1: Data Type Exploration

### Task 1.1: Create Variables

Create the following variables:

```python
# Integer variable
my_integer = 42

# Float variable
my_float = 3.14

# String variable
my_string = "Python"

# Boolean variable
my_boolean = True
```

### Task 1.2: Check Types

Use the `type()` function to verify the type of each variable you created. Print the results with descriptive messages.

**Example output:**
```
The type of my_integer is: <class 'int'>
The type of my_float is: <class 'float'>
...
```

### Task 1.3: Dynamic Typing

Demonstrate Python's dynamic typing by:
1. Creating a variable called `dynamic_var` and assigning it an integer
2. Printing its value and type
3. Reassigning it to a string
4. Printing its new value and type
5. Reassigning it to a float
6. Printing its final value and type

---

## Part 2: Mathematical Operations

### Task 2.1: Basic Calculations

Create variables and perform these calculations:

1. Add two integers and store the result
2. Multiply a float by an integer and store the result
3. Divide two numbers using `/` and store the result
4. Divide two numbers using `//` and store the result
5. Find the remainder of 17 divided by 5 using `%`
6. Calculate 2 to the power of 10 using `**`

Print each result with a descriptive message.

### Task 2.2: Order of Operations

Solve this problem: Calculate the result of this expression and print it:

```python
result = 10 + 5 * 2 - 3 ** 2
```

Then, show what the result would be if you added parentheses to change the order:
- Calculate `(10 + 5)` first
- Calculate the entire expression

**Example:**
```python
# Without extra parentheses
result1 = 10 + 5 * 2 - 3 ** 2
print("Without parentheses:", result1)

# With parentheses changing order
result2 = (10 + 5) * 2 - 3 ** 2
print("With parentheses:", result2)
```

### Task 2.3: Real-World Calculation

**The Problem:** You're shopping and want to calculate the total cost including sales tax.

Write code to:
1. Create a variable `item_price` = 29.99
2. Create a variable `tax_rate` = 0.08 (8%)
3. Calculate the tax amount (price × tax_rate)
4. Calculate the total cost (price + tax)
5. Print all values with descriptive labels

**Expected output format:**
```
Item price: $29.99
Tax amount: $2.40
Total cost: $32.39
```

---

## Part 3: String Manipulation

### Task 3.1: String Concatenation

1. Create variables for your first name, last name, and age
2. Use concatenation to create a complete sentence: "My name is [first] [last] and I am [age] years old."
3. Remember to convert age to a string!

### Task 3.2: String Repetition

1. Create a decorative line using the `=` character repeated 40 times
2. Create your name centered between two decorative lines
3. Print the result

**Example output:**
```
========================================
              Alice Smith
========================================
```

### Task 3.3: Building Formatted Output

Create variables for a book with:
- Title
- Author
- Year published
- Price

Then create a formatted string that displays all this information nicely.

**Example output:**
```
Book: The Great Gatsby
Author: F. Scott Fitzgerald
Published: 1925
Price: $12.99
```

---

## Part 4: Type Conversion

### Task 4.1: String to Number

```python
# You have these string variables:
number1 = "25"
number2 = "10"
number3 = "3.5"

# Convert and calculate:
# 1. Add number1 and number2 (as integers)
# 2. Multiply number3 by 2 (as a float)
# 3. Divide number1 by number2 (as integers, then convert to float)
```

### Task 4.2: Number to String

```python
# You need to create this exact output:
# "I have 3 apples, 5 oranges, and 2.5 pounds of grapes."

# Start with these numeric variables:
apples = 3
oranges = 5
grapes = 2.5

# Use string concatenation and type conversion to create the sentence
```

### Task 4.3: Error Handling (Understanding)

Try this code and observe the error:

```python
result = "10" + 5
```

Then:
1. Explain in a comment WHY this causes an error
2. Show TWO different ways to fix it (converting to int OR converting to string)

---

## Part 5: Conditional Logic

### Task 5.1: Simple If Statement

Write code that:
1. Creates a variable `temperature` with a numeric value
2. Uses an if/else statement to print "It's cold!" if temperature < 60
3. Prints "It's warm!" otherwise

Test with different temperature values.

### Task 5.2: Multiple Conditions

Write code that checks a student's grade and prints:
- "Excellent!" if grade >= 90
- "Good job!" if grade >= 80
- "Passing" if grade >= 70
- "Need to study more" if grade < 70

Use if/elif/else statements.

### Task 5.3: Comparison Operators

Create two variables and demonstrate each comparison operator:

```python
x = 10
y = 5

# Use ==, !=, >, <, >=, <= to compare x and y
# Print the result of each comparison with a descriptive message
```

**Example output:**
```
Is x equal to y? False
Is x not equal to y? True
Is x greater than y? True
...
```

---

## Challenge Exercises (Optional)

### Challenge 1: Even or Odd Checker

Write a program that:
1. Takes a number (use any number you like)
2. Uses the modulus operator `%` to determine if it's even or odd
3. Prints "The number X is even" or "The number X is odd"

**Hint:** A number is even if `number % 2 == 0`

### Challenge 2: Temperature Converter

Create a mini temperature conversion program:
1. Store a temperature in Fahrenheit
2. Calculate the equivalent in Celsius using: C = (F - 32) × 5/9
3. Use an if/else to determine if water would be:
   - "Frozen" (< 0°C)
   - "Liquid" (0°C to 100°C)
   - "Steam" (> 100°C)
4. Print both temperatures and the water state

### Challenge 3: String Analysis

Given a string, use various operations to:
1. Print its length (use `len()` function)
2. Convert it to all uppercase
3. Convert it to all lowercase
4. Replace a word in it
5. Repeat it 3 times

```python
message = "Python is fun"

# Your code here to analyze and manipulate this string
```

---

## Submission Guidelines

When you're finished:

1. **Save your notebook** as `LastName_FirstName_Week02.ipynb`
2. **Run all cells** from top to bottom to ensure everything works
3. **Check for errors** - fix any error messages before submitting
4. **Review comments** - make sure your code is well-documented
5. **Verify output** - ensure your results make sense
6. **Submit to Canvas** before the deadline

## Grading Rubric

| Criteria | Points |
|----------|--------|
| Part 1: Data Types (all tasks complete) | 15 |
| Part 2: Mathematical Operations | 20 |
| Part 3: String Manipulation | 20 |
| Part 4: Type Conversion | 20 |
| Part 5: Conditional Logic | 15 |
| Code quality (comments, formatting) | 5 |
| Code runs without errors | 5 |
| **Total** | **100** |

**Bonus Points:**
- Challenge 1: +3 points
- Challenge 2: +4 points
- Challenge 3: +3 points

## Common Mistakes to Avoid

```{warning}
**Watch out for:**
- Forgetting to convert numbers to strings before concatenating
- Using `=` when you mean `==` in comparisons
- Missing colons `:` after if/elif/else statements
- Incorrect indentation in code blocks
- Not testing your code before submitting
```

## Tips for Success

```{tip}
1. **Test each section** as you go - don't wait until the end
2. **Use print statements** liberally to check your work
3. **Read error messages** carefully - they tell you what's wrong
4. **Comment your code** to explain your thinking
5. **Try the optional challenges** for extra practice (and points!)
```

## Additional Resources

- [Python Data Types Tutorial](https://www.w3schools.com/python/python_datatypes.asp)
- [Python Operators Reference](https://www.w3schools.com/python/python_operators.asp)
- [Type Conversion in Python](https://www.programiz.com/python-programming/type-conversion-and-casting)
- [Python String Methods](https://www.w3schools.com/python/python_ref_string.asp)

---

**Great work on Week 2!** These exercises will give you a solid foundation in working with different data types and operations. Keep practicing!
