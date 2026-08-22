# Getting Started 📘

*Timothy D. Bowman, Dominican University*

This is the online textbook for **INF 426 / LIS 826: Introduction to Programming
in Python** at Dominican University's School of Information Studies. Everything
you need to read for the course is here, free, and open in your browser.

---

## Why an Open Textbook?

1. **Cost.** A single introductory programming textbook runs \$80 to \$150. You are
   already paying tuition. Asking you to also buy a book that will be out of date
   in three years is hard to justify when the language itself is free and its
   documentation is excellent.

2. **Currency.** Python changes. So do the libraries, the tools, and the good
   advice about how to use them. A printed book locks in whatever was true at
   press time. This one gets edited the week something changes, and you always
   see the current version.

3. **Fit.** Commercial textbooks are written for everyone, which means they are
   written for no one in particular. This book is written for *you* — students in
   an information school, most of whom have never programmed, who will use these
   skills on catalogs, collections, datasets, and systems rather than on
   shipping software products. The examples reflect that.

---

## How It Was Built

The book is written in **MyST Markdown** and built with **[MyST](https://mystmd.org/)**,
an open publishing toolchain from the Jupyter community. The source lives in a
public GitHub repository, and every push rebuilds and redeploys the site
automatically through GitHub Actions.

Pages that teach code are **Jupyter notebooks**, not screenshots of code. That
means you can download any walkthrough, open it in Jupyter, and run it yourself.
Every code example in this book was executed before publication — if it appears
here, it ran.

I use AI tools as part of my drafting and editing process, the same way I use a
spell-checker and a search engine. Everything published here has been read,
checked, and corrected by me, and I remain responsible for all of it. I mention
this because I ask you to be transparent about your own AI use, and that rule
should run in both directions.

---

## What You Need Before Week 1

Install these before our first meeting. All three are free, and all three run on
Windows, macOS, and Linux.

| Tool | What it's for | Where |
|---|---|---|
| **Anaconda Distribution** | Python plus Jupyter Notebook, in one installer | [anaconda.com](https://www.anaconda.com/) |
| **Visual Studio Code** | A proper code editor for when notebooks aren't enough | [code.visualstudio.com](https://code.visualstudio.com/) |
| **GitHub account** | Where you'll store and share code | [github.com](https://github.com/) |

You do not need a powerful computer. Any laptop that can run a web browser
comfortably can run everything in this course.

```{tip}
Install early, and open Jupyter once before Week 1 — just to confirm it launches.
Installation problems are much easier to solve on a quiet Tuesday than fifteen
minutes before class.
```

---

## How to Read This Book

The course is organized into **four thematic blocks** rather than fifteen
disconnected weekly topics. Each block answers one question, and each one builds
on the last:

| Block | Weeks | Core question |
|---|---|---|
| [Block 1](block01/overview.md) — Computational Thinking & Foundations | 1–4 | How do we tell computers to think? |
| [Block 2](block02/overview.md) — Data Structures & Meaningful Computation | 5–7 | How do programs manage and interpret information? |
| [Block 3](block03/overview.md) — Systems, APIs, AI & Object Thinking | 8–12 | How do programs interact with other systems? |
| [Block 4](block04/overview.md) — Python + Robotics Capstone | 13–15 | How do software systems perceive, decide, and act? |

Inside each week you'll usually find:

- an **overview** — objectives, topics, readings, and a quick reference guide
- one or more **lesson pages** — the concepts, explained with worked examples
- a **walkthrough notebook** — one small program built step by step, which you
  can run and modify
- **exercises**, some of which grade themselves in the browser

Read the overview first, then the lesson, then run the walkthrough. The
walkthroughs are where the material stops being abstract.

```{important}
**Type the code. Don't copy and paste it, and don't paste it in from an AI.**
The muscle memory of typing `for item in collection:` a hundred times is a real
part of learning to program, and skipping it is the single most reliable way to
reach Week 8 feeling lost.
```

---

## A Living Document

I edit this book during the semester. If you find an error — a broken link, code
that doesn't run, an explanation that doesn't land — tell me. That is genuinely
useful, and fixing it helps everyone in the room after you.

Where this book and a primary source disagree, **the primary source wins**. The
[official Python documentation](https://docs.python.org/3/) is the authority on
what Python does; I am only the authority on what we're doing this semester.

---

## Relationship to Canvas

Three places, three jobs. Keeping them straight will save you a lot of confusion:

- **This book** is the *content*. Lessons, examples, walkthroughs, reference
  material. It has no due dates in it on purpose, so it doesn't go stale.
- **Canvas** is the *authority on logistics*. Due dates, submissions, grades,
  announcements, and the discussion board. If a date here ever disagrees with a
  date in Canvas, **Canvas is correct**.
- **Your own computer** is where the work actually happens. Notebooks you
  downloaded, code you wrote, projects you built. Back it up — GitHub is right
  there.

---

## One Last Thing

You are going to spend a lot of this semester being stuck. That is not a sign
that you're bad at this; it is what programming *is*. Professionals are stuck
most of the day. The difference is that they've learned to read the error
message, try something small, and ask for help early.

Office hours exist for exactly this. Use them in Week 3, not Week 13.
