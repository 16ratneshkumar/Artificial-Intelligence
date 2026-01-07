# Prolog Syntax and Meaning

This section covers the data objects in Prolog and the formal logic behind how Prolog matches expressions.

---

## 1. Data Objects (Terms)

In Prolog, all data are called **terms**.

### 1.1 Atoms and Numbers
- **Atoms:** Constants that start with a lowercase letter (e.g., `anna`, `nil`, `x25`) or are enclosed in single quotes (`'Tom'`, `'South_America'`).
- **Numbers:** Integers (e.g., `1`, `-100`) and Real numbers (e.g., `3.14`).

### 1.2 Variables
- **Variables:** Symbols that start with an **uppercase letter** or an **underscore** (e.g., `X`, `Result`, `_person`).
- **Anonymous Variable:** The underscore `_` is used when the specific value of the variable does not matter.

### 1.3 Structures (Complex Terms)
- **Structures:** Objects that have several components.
- **Functor:** The name of the structure.
- **Arguments:** The components inside parentheses.
- **Example:** `date(1, may, 2024)` → Functor: `date`, Arguments: `1`, `may`, `2024`.

---

## 2. Matching (Unification)

**Matching** is the operation that Prolog performs to make two terms identical.

### Rules for Matching Term S and T:
1.  If S and T are constants (atoms or numbers), they match only if they are the **same**.
2.  If S is a variable and T is anything, they match. S becomes **instantiated** to T.
3.  If S and T are structures, they match if:
    -   They have the same **functor**.
    -   They have the same number of arguments (**arity**).
    -   All corresponding arguments match.

**Example:**
- `date(D, M, 2024)` matches `date(1, may, Y)`
- Result: `D = 1`, `M = may`, `Y = 2024`

---

## 3. Declarative vs. Procedural Meaning

- **Declarative Meaning:** Concerned with **what** is true.
  - "Goal G is true if there is a rule R such that the head of R matches G and all subgoals in the body are true."
- **Procedural Meaning:** Concerned with **how** the result is obtained.
  - "To execute goal G, find a rule R whose head matches G, and execute the subgoals in R sequentially."

---

## 4. Backtracking and Search Tree

Prolog uses a **Depth-First Search** on the goal tree to find solutions.
1. It tries rules in the order they appear in the file (Top to Bottom).
2. It tries goals in a rule from left to right.
3. When a goal fails, it backtracks to the most recent goal that had alternative matches.

---

**Previous:** [← Prolog Basics](22_Prolog_Basics.md) | **Next:** [Prolog Lists & Arithmetic →](24_Prolog_Lists.md)
