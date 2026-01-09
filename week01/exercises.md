# Week 1 Exercises

## Exercise 1: Variables and Print Statements

This exercise will help you practice creating variables, assigning values, and using the `print()` function.

### Instructions

Create a new Jupyter Notebook named `week01_exercise.ipynb` and complete the following tasks:

### Part 1: Personal Information

1. Create a variable called `first_name` and assign it your first name as a string
2. Create a variable called `last_name` and assign it your last name as a string
3. Create a variable called `age` and assign it your age as a number
4. Create a variable called `favorite_color` and assign it your favorite color as a string

Then use `print()` statements to display:
```
My name is [first_name] [last_name]
I am [age] years old
My favorite color is [favorite_color]
```

### Part 2: Simple Calculations

5. Create a variable called `birth_year` and calculate it using your age (you can use the current year 2024)
6. Create a variable called `next_year_age` and calculate your age next year
7. Print both values with descriptive messages

### Part 3: Comments

8. Add comments above each section of code explaining what it does
9. Use the `#` symbol for single-line comments
10. Make sure your comments are clear and helpful

### Example Output

```python
# Student information variables
first_name = "Jane"
last_name = "Smith"
age = 20
favorite_color = "blue"

# Display student information
print("My name is", first_name, last_name)
print("I am", age, "years old")
print("My favorite color is", favorite_color)

# Calculate birth year (approximate)
birth_year = 2024 - age
print("I was born in", birth_year)

# Calculate next year's age
next_year_age = age + 1
print("Next year I will be", next_year_age)
```

**Expected Output:**
```
My name is Jane Smith
I am 20 years old
My favorite color is blue
I was born in 2004
Next year I will be 21
```

## Exercise 2: Variable Naming Practice

### Good vs. Bad Variable Names

For each scenario below, identify which variable name is better and explain why:

1. Storing a student's grade:
   - `g` or `student_grade`

2. Counting the number of items:
   - `numberOfItems` or `n`

3. Storing a person's email address:
   - `email_address` or `eaddress`

4. Tracking total price:
   - `x` or `total_price`

### Create Your Own Variables

Create variables with appropriate names for:

1. The number of courses you're taking this semester
2. Your student ID number
3. The name of your university
4. Whether you have programming experience (True/False)
5. Your graduation year

```python
# Example solution
num_courses = 5
student_id = 12345678
university_name = "Dominican University"
has_programming_experience = False
graduation_year = 2025
```

## Exercise 3: Following PEP 8

Review the following code and rewrite it to follow PEP 8 style guidelines:

```python
# Bad code - violates PEP 8
X=5
Y=10
z=X+Y
print(z)
a="Hello"
B="World"
print(a,B)
MyVariable=100
```

Rewrite this code with:
- Proper spacing around operators
- Consistent naming convention (snake_case)
- Descriptive variable names
- Comments explaining what the code does

```{admonition} Solution
:class: dropdown

```python
# Mathematical calculations
first_number = 5
second_number = 10

# Calculate sum
sum_result = first_number + second_number
print(sum_result)

# String variables for greeting
greeting = "Hello"
name = "World"
print(greeting, name)

# Store a count value
item_count = 100
```
\```
```

## Challenge Exercise (Optional)

Create a program that:

1. Stores information about your favorite book (title, author, year published, number of pages)
2. Calculates how many years ago it was published
3. Displays all information in a nicely formatted way

Example:
```python
# Book information
book_title = "The Catcher in the Rye"
book_author = "J.D. Salinger"
year_published = 1951
num_pages = 277
current_year = 2024

# Calculate years since publication
years_since_publication = current_year - year_published

# Display book information
print("Book Title:", book_title)
print("Author:", book_author)
print("Published:", year_published)
print("Pages:", num_pages)
print("This book was published", years_since_publication, "years ago")
```

## Submission Guidelines

When you're finished:

1. **Save your notebook** with a clear filename: `LastName_FirstName_Week01.ipynb`
2. **Test all your code** - Run all cells from top to bottom to make sure everything works
3. **Check for errors** - Fix any error messages
4. **Review your comments** - Make sure they're clear and helpful
5. **Submit to Canvas** - Upload your `.ipynb` file by the due date

## Grading Rubric

| Criteria | Points |
|----------|--------|
| All variables created correctly | 30 |
| Print statements work as expected | 20 |
| Proper naming conventions followed | 20 |
| Comments are clear and helpful | 15 |
| Code runs without errors | 10 |
| Follows PEP 8 style guidelines | 5 |
| **Total** | **100** |

```{tip}
Don't forget to test your code before submitting! Run each cell and verify the output is what you expect.
```

## Additional Resources

- [Python Variables Tutorial](https://www.w3schools.com/python/python_variables.asp)
- [PEP 8 Style Guide](https://www.python.org/dev/peps/pep-0008/)
- [Python print() Function](https://www.w3schools.com/python/ref_func_print.asp)

---

**Great job completing Week 1!** You're ready to move on to Week 2 where we'll explore data types in more depth.
