# Wrap Up 🎓

You started this semester with a blank Jupyter cell and, for most of you, no idea
what to put in it. You are finishing it having built an autonomous robot.

That's worth sitting with for a moment before you close the tab.

---

## What You Actually Learned

Not the syllabus version — the honest version, block by block.

### Block 1 — You learned to think in steps

Variables, types, strings, conditionals, functions. But underneath the syntax,
the real skill was **decomposition**: taking a task described in one sentence of
English and breaking it into steps a machine can follow. That skill transfers to
work that has nothing to do with Python.

You also learned that `SyntaxError` on line 12 usually means the problem is on
line 11.

### Block 2 — You learned to work with data at scale

Loops meant you stopped doing things once and started doing them a thousand
times. Lists, tuples, and dictionaries gave you somewhere to put the results.
The counting pattern —

```python
counts[key] = counts.get(key, 0) + 1
```

— is four lines you will use for the rest of your career.

### Block 3 — You learned that programs don't live alone

Modules let you organize code across files. Files and CSVs let your programs
remember things after they exit. APIs let them reach data you didn't create.
JSON and SQL gave you two ways to store structure. And object-oriented
programming gave you a way to keep data and the rules about that data in one
place.

This is the block where "writing a script" became "building a system."

### Block 4 — You built something that acts on its own

A grid world, a robot, sensors, and a sense–think–act loop. Your robot perceives
its environment, weighs its options, chooses, moves, and logs why. Every single
piece of it came from an earlier block.

That's the point of the whole arc: the capstone wasn't new material. It was
everything you already knew, pointed at one problem.

---

## A Self-Check

Not a quiz. Just an honest inventory. Can you, without looking anything up:

- Explain the difference between `=` and `==`?
- Write a `for` loop that totals a list of numbers?
- Say what a function `return`s if it only `print`s?
- Look at `{"Dune": 42}` and `["Dune", 42]` and say which is which, and when
  you'd want each?
- Read a traceback and find the line that actually broke?
- Write a class with an `__init__` and one method?
- Explain to a non-programmer what an API is?

If some of those are shaky, that's normal and it's fixable. The relevant week is
still here, and so are the walkthrough notebooks.

```{tip}
The fastest way to find out what you really know: open a blank notebook and try
to rebuild one of the walkthroughs from memory. What you can rebuild, you own.
What you can't, you've only read.
```

---

## Where to Go Next

Programming is a big country and you've walked one road through it. A few
directions worth considering, depending on what you want to do:

### If you liked working with data

**Next:** pandas properly, then a visualization library.
Assignment 2 gave you a taste. Real proficiency with pandas is one of the most
directly employable skills in information work — collection analysis, usage
statistics, institutional reporting.

Start with the [pandas getting-started guides](https://pandas.pydata.org/docs/getting_started/index.html),
then [seaborn](https://seaborn.pydata.org/) for charts.

### If you liked the systems and APIs work

**Next:** more APIs, and then a small web application.
Look at Flask or FastAPI — both let you go from "my program consumes an API" to
"my program *is* an API." From there, automation: scripts that run on a schedule
and do the boring parts of a job for you.

### If you liked the robotics capstone

**Next:** simulation with real physics, or actual hardware.
[Webots](https://cyberbotics.com/) gives you a full simulator with a Python API.
Or spend \$40 on a Raspberry Pi and a couple of sensors — everything you learned
about the sense–think–act loop applies directly.

### If you're in an information-science program

**Next:** point Python at the systems you already work with.
MARC records, OAI-PMH harvesting, institutional-repository APIs, link checking,
metadata cleanup at scale. A lot of library work is repetitive in exactly the
way computers are good at. `pymarc` is a reasonable first stop.

---

## Keeping Your Code

Your notebooks are worth more than the grade attached to them.

1. **Put them on GitHub.** You made an account in Week 1. A public repository of
   coursework is a perfectly respectable thing to point an employer at.
2. **Write a README.** One paragraph per project: what it does, how to run it,
   what you'd change. Future-you will not remember.
3. **Keep the capstone somewhere findable.** It's the most substantial thing you
   built, and it demonstrates OOP, control flow, data structures, and
   documentation all at once.

---

## How to Keep Learning

The honest answer is: build things you actually want to exist. Tutorials teach
you syntax; projects teach you programming. The gap between the two is where
most people stall, and the only way across is to pick something small,
personally useful, and slightly beyond you — then finish it.

A few habits worth keeping:

- **Read other people's code.** Pick a small library on GitHub and read it.
- **Keep a snippets file.** Every time you solve something fiddly, save it.
- **Stay stuck productively.** Fifteen minutes on your own, then ask. Both halves
  of that rule matter.
- **Come back to the docs.** You'll understand [the tutorial](https://docs.python.org/3/tutorial/)
  very differently now than you would have in August.

---

## Thank You

Teaching people to program is my favourite thing about this job, mostly because
of the moment it clicks — and it clicks at a different week for everyone.

Thank you for the questions, for the code you typed out by hand when copying
would have been faster, and for being patient with a course that asks you to be
confused on purpose for fifteen weeks.

If you build something you're proud of after this course ends, I'd genuinely like
to hear about it.

— **Dr. Timothy D. Bowman**

---

```{note}
**One last practical thing.** This book stays online after the semester ends. The
walkthroughs, the glossary, the reference list — all of it remains available, and
none of it requires a Canvas login. Bookmark it.
```
