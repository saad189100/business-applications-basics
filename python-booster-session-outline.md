# Python Basics Booster — 2-Hour Session Plan
### For business students who already know *what* the course wants, but get stuck on the code itself

---

## 1. Context & goal

**Who:** Business-background students currently enrolled in a 12–14 week course. Mixed level — some have never coded, some have dabbled. Plan for the lower end and let stronger students stretch.

**The real problem:** They don't need new topics. They're already being taught the full course. They get stuck on the *fundamentals underneath it* — reading code, basic syntax, why an error appears, what a function/loop actually does. This session fills those gaps so the rest of their course stops feeling like a wall.

**One-line objective:** *By the end, a student can read a short block of Python, predict what it does, fix a simple error, and write basic data logic without panicking.*

**Environment:** Google Colab (no install, runs in browser). One shared starter notebook + one dataset (a small CSV of sales/orders).

**Teaching stance:** Live-code everything. Students type along in their own copy. Talk in business terms first, code second. Normalize errors out loud.

---

## 2. What we deliberately leave out

To protect the 2 hours, we skip: installing Python locally, virtual environments, classes/OOP, file I/O beyond `read_csv`, plotting libraries, list comprehensions (mention only), and anything about performance. If a student asks, note it and move on.

---

## 3. Session timeline (120 minutes)

| Block | Topic | Time | Running total |
|-------|-------|------|---------------|
| 0 | Setup & mental model | 10 min | 0:10 |
| 1 | Variables, types, printing | 20 min | 0:30 |
| 2 | Collections: lists & dictionaries | 20 min | 0:50 |
| — | **Quick break / catch-up** | 5 min | 0:55 |
| 3 | Logic & loops (if / for) | 25 min | 1:20 |
| 4 | Functions (built-in + your own) | 15 min | 1:35 |
| 5 | A taste of pandas | 20 min | 1:55 |
| 6 | Errors, debugging & where to go next | 5 min | 2:00 |

---

## 4. Block-by-block plan

### Block 0 — Setup & mental model (10 min)
**Goal:** Everyone is in Colab and running cells; everyone shares one core idea.

- Open the shared notebook, **File → Save a copy in Drive** (so each student has their own).
- The 3 buttons that matter: run a cell (Shift+Enter), the order cells run in, and **Runtime → Restart** when things get weird.
- The one mental model for the whole session: *Code is just "store a value" and "do something with that value."* Everything today is a variation of those two moves.
- **Pitfall to flag early:** cells remember things across the notebook, so running them out of order causes confusing errors. Restart fixes most mysteries.

### Block 1 — Variables, types, printing (20 min)
**Goal:** Store values, know the basic types, see results.

- Variables as labeled boxes: `revenue = 5000`, `product = "Coffee Mug"`.
- The four everyday types: **int**, **float**, **string**, **bool** — with business examples (units sold, price, product name, is_returned).
- `print()` and f-strings: `print(f"Revenue was ${revenue}")`.
- `type()` to check what something is. `#` comments.
- **Common errors to show on purpose:** quotes missing on a string, typo'd variable name (`NameError`), mixing `"5" + 5` (`TypeError`).
- *Mini-exercise:* store a price and a quantity, print the total as a sentence.

### Block 2 — Collections: lists & dictionaries (20 min)
**Goal:** Hold many values; look things up by name.

- **List** = an ordered column of values: `sales = [200, 450, 130, 600]`. Indexing from 0, `len()`, `.append()`.
- Map it to business: "a list is one column of your spreadsheet."
- **Dictionary** = labeled lookup: `prices = {"mug": 12, "shirt": 25}` → `prices["mug"]`.
- When to use which: list = a sequence, dict = look up a value by a key.
- **Pitfall:** off-by-one indexing (`sales[4]` on a 4-item list → `IndexError`); the first item is `sales[0]`.
- *Mini-exercise:* make a list of 5 daily sales, print the first, last, and total (`sum()`).

### Quick break (5 min)
Stretch, catch up anyone whose notebook broke. This buffer also absorbs overrun from Blocks 1–2.

### Block 3 — Logic & loops (25 min)
**Goal:** Make decisions and repeat work — the two things that make code more than a calculator.

- Comparisons: `==`, `!=`, `>`, `<`, `>=`. Stress `==` (compare) vs `=` (assign) — a top beginner trap.
- `if / elif / else` with a business rule: classify an order as "Large" / "Medium" / "Small" by amount.
- **Indentation matters** — Python uses spaces to know what's inside the `if`. Show the `IndentationError`.
- `for` loops: walk through a list of sales, do something to each. Build a running total by hand in code.
- Combine them: loop over orders, count how many are "Large."
- *Mini-exercise:* given a list of order amounts, loop through and print "FLAG" for any over $500.

### Block 4 — Functions (15 min)
**Goal:** Reuse logic; understand the function calls they already see everywhere.

- They've *been using* functions all along: `print()`, `len()`, `sum()`, `round()`, `max()`, `min()`. A function = a named machine: inputs go in, a result comes out.
- Write your own with `def`, arguments, and `return`:
  ```python
  def with_tax(price, rate=0.1):
      return price * (1 + rate)
  ```
- Why bother: name a calculation once, reuse it everywhere; fix it in one place.
- **Pitfall:** confusing `print` (shows on screen) with `return` (hands a value back to use later).
- *Mini-exercise:* write a function `is_profitable(revenue, cost)` that returns `True`/`False`.

### Block 5 — A taste of pandas (20 min)
**Goal:** Show that everything so far scales to real data — "Excel, but in code."

- `import pandas as pd`, then `df = pd.read_csv(...)` on the provided dataset.
- Look around: `df.head()`, `df.shape`, `df.columns`.
- Pull one column (a Series): `df["Revenue"]` → connects back to "a list is a column."
- Quick numbers: `df["Revenue"].sum()`, `.mean()`, `.max()`.
- Filter rows with a condition (this is just Block 3's logic applied to a whole table): `df[df["Revenue"] > 500]`.
- One `groupby`: `df.groupby("Region")["Revenue"].sum()` — the payoff moment for business students.
- Keep it to *reading and summarizing* data; no cleaning/merging today.
- *Mini-exercise:* find the average order value and show only orders above it.

### Block 6 — Errors, debugging & next steps (5 min)
**Goal:** Leave them unafraid of red text.

- How to read a traceback: **look at the bottom line first** — it names the error and the line.
- The 4 errors they'll meet 90% of the time: `NameError`, `TypeError`, `IndexError`/`KeyError`, `IndentationError` — and the one-line fix for each (we saw them all today).
- Debugging habit: print the variable, re-run from the top, restart runtime.
- Where to get unstuck: official Python docs, pandas docs, and how to ask an AI assistant a *useful* question (paste the code + the full error).

---

## 5. Materials to build before the session

1. **Starter Colab notebook** — pre-sectioned by block, with empty "type along" cells and the mini-exercises stubbed out.
2. **Sample dataset** — a small CSV (~50–100 rows): columns like `OrderID, Date, Region, Product, Quantity, Revenue, Cost`. Realistic but clean.
3. **One-page cheat sheet** — syntax for variables, list/dict, if, for, def, and the 6 pandas calls used. (Markdown or PDF.)
4. **Solutions notebook** — completed versions of every mini-exercise, shared *after* the session.

---

## 6. Facilitation notes

- **Mixed levels:** every mini-exercise has a one-line "stretch" variant for fast finishers (e.g., "now also print the % over budget") so no one is idle and no one is left behind.
- **Pacing:** Blocks 3 and 5 are the high-value core. If time is tight, trim Block 2's dict depth and the Block 5 `groupby`, never the loops or functions.
- **Engagement:** ask the room to predict each cell's output *before* running it — prediction is where the learning happens.
- **Tone:** show errors on purpose and fix them live. The goal is that errors feel normal, not like failure.

---

## 7. Success check (how we know it worked)

A 5-minute exit task: give students a short unseen code block and ask them to (a) say what it prints, (b) spot one deliberate bug, and (c) write one line to filter a DataFrame. If most can do 2 of 3, the session hit its goal.
