# Getting Started with Python

## What is Computer Programming?

Computer programming is the process of creating instructions that a computer can execute to perform specific tasks. Think of it as writing a recipe—you provide step-by-step directions that the computer follows precisely.

### Why Learn Python?

Python is an excellent first programming language because:

- **Readable syntax** - Python code reads almost like English
- **Versatile** - Used in web development, data science, AI, automation, and more
- **Popular** - Huge community and abundant resources
- **Powerful libraries** - Pre-built tools for almost any task
- **Career-ready** - High demand in job market

```{tip}
If you enjoy solving puzzles, programming is a skill that will allow you to solve countless puzzles!
```

## Installing Anaconda

Anaconda is a distribution of Python that includes everything you need to get started, including Jupyter Notebook.

### Installation Steps

1. **Download Anaconda**
   - Visit [anaconda.com/download](https://www.anaconda.com/download)
   - Select your operating system (Windows, macOS, or Linux)
   - Download the Python 3.x version (latest available)

2. **Run the Installer**
   - Double-click the downloaded file
   - Follow the installation wizard
   - **Important**: Check "Add Anaconda to my PATH environment variable" if prompted
   - Default settings are usually fine

3. **Verify Installation**
   - Open Anaconda Navigator (it will be in your applications)
   - You should see Jupyter Notebook as an option

### Troubleshooting

If you have issues:
- Make sure you have enough disk space (at least 3GB free)
- Try running the installer as administrator (Windows) or with sudo (Mac/Linux)
- Check the [Anaconda documentation](https://docs.anaconda.com/anaconda/install/)

## Launching Jupyter Notebook

Jupyter Notebook is an interactive environment where you can write and run Python code, add explanatory text, and see results immediately.

### Starting Jupyter

**Method 1: Anaconda Navigator**
1. Open Anaconda Navigator
2. Click "Launch" under Jupyter Notebook
3. Your browser will open with the Jupyter interface

**Method 2: Command Line**
```bash
jupyter notebook
```

### The Jupyter Interface

When Jupyter opens, you'll see:

- **File browser** - Navigate your computer's folders
- **New button** - Create new notebooks
- **Upload button** - Add existing files

## Creating Your First Notebook

Let's create your first Jupyter Notebook!

### Step-by-Step

1. **Click "New"** in the upper right
2. **Select "Python 3"** from the dropdown
3. **Name your notebook** by clicking on "Untitled" at the top

Your notebook is now ready!

### Understanding Cells

Jupyter notebooks contain **cells** that can hold either:

- **Code cells** - Python code that can be executed
- **Markdown cells** - Text with formatting (like this textbook!)

### Running Your First Code

In the first cell, type:

```python
print("Hello, World!")
```

Then:
- Press **Shift + Enter** to run the cell
- Or click the "Run" button in the toolbar

You should see the output below the cell:
```
Hello, World!
```

**Congratulations!** You've just written and executed your first Python program!

## Keyboard Shortcuts

Learning these shortcuts will make you much more efficient:

| Shortcut | Action |
|----------|--------|
| Shift + Enter | Run cell and move to next |
| Ctrl + Enter | Run cell and stay on it |
| Esc | Enter command mode |
| Enter | Enter edit mode |
| A (in command mode) | Insert cell above |
| B (in command mode) | Insert cell below |
| M (in command mode) | Change to Markdown cell |
| Y (in command mode) | Change to Code cell |
| DD (in command mode) | Delete cell |

## Markdown Basics

Markdown allows you to format text in your notebooks. Here are some basics:

```markdown
# Heading 1
## Heading 2
### Heading 3

**Bold text**
*Italic text*

- Bullet point 1
- Bullet point 2

1. Numbered item 1
2. Numbered item 2

[Link text](https://example.com)
```

### Markdown Resources

- [Markdown Cells in Jupyter](https://jupyter-notebook.readthedocs.io/en/stable/examples/Notebook/Working%20With%20Markdown%20Cells.html)
- [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
- [Markdown Guide](https://www.markdownguide.org/cheat-sheet)

## Try It Yourself!

```{admonition} Practice Exercise
:class: tip

Create a new Jupyter Notebook and:

1. Add a Markdown cell with a heading "My First Notebook"
2. Add a Markdown cell explaining what you want to learn in this course
3. Add a Code cell that prints your name
4. Add a Code cell that calculates 2 + 2 and displays the result
5. Save your notebook

Don't worry if you make mistakes—that's part of learning!
```

## Saving and Managing Notebooks

### Saving
- **Auto-save** - Jupyter saves automatically every 2 minutes
- **Manual save** - Click the save icon or press Ctrl+S (Cmd+S on Mac)
- **Checkpoint** - Jupyter creates checkpoints you can revert to

### File Format
- Notebooks are saved as `.ipynb` files
- They contain your code, output, and markdown text
- You can share them with others or submit them for assignments

### Best Practices
- Give your notebooks descriptive names
- Organize them in folders by week or topic
- Add comments and markdown to explain your work
- Run cells in order from top to bottom

---

**Next:** Learn about [Variables and Naming Conventions](variables-and-naming.md)
