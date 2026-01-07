# Prolog Basics: Facts, Rules, and Queries

**Prolog** (Programming in Logic) is a declarative language used in AI for symbolic reasoning. Unlike procedural languages, you describe the **problem** and the **relationships**, and Prolog finds the solution.

---

## 1. Facts

A **fact** declares a relationship between objects or a property of an object. Facts are always true.

**Example:**
```prolog
parent(pam, bob).    % Pam is a parent of Bob
parent(tom, bob).    % Tom is a parent of Bob
parent(tom, liz).    % Tom is a parent of Liz
female(pam).         % Pam is female
male(tom).           % Tom is male
```
- **Rules:** Facts must end with a full stop (`.`). Names must start with a lowercase letter (atoms).

---

## 2. Queries

A **query** asks Prolog if a relationship exists or who satisfies a relationship.

- **Yes/No Query:** `?- parent(pam, bob).` → Result: `yes`
- **Variable Query:** `?- parent(X, bob).` → Result: `X = pam ; X = tom.` (Prolog finds all possible values for X).

---

## 3. Rules

A **rule** defines a relationship that is true only if certain conditions are met. Rules consist of a **head** and a **body**.

**General Form:**
`Head :- Body.` (Read as "Head is true IF Body is true")

**Example:**
```prolog
offspring(Y, X) :- 
    parent(X, Y).    % Y is an offspring of X if X is a parent of Y

mother(X, Y) :- 
    parent(X, Y), 
    female(X).       % X is mother of Y if X is parent of Y AND X is female
```

---

## 4. Recursive Rules

Recursion is essential in Prolog to define relationships that can go infinitely deep, such as ancestry.

**Example: Predecessor (Ancestor)**
```prolog
% Base Case: A parent is a predecessor
predecessor(X, Z) :- 
    parent(X, Z).

% Recursive Case: X is a predecessor of Z if X is parent of Y AND Y is predecessor of Z
predecessor(X, Z) :- 
    parent(X, Y), 
    predecessor(Y, Z).
```

### Visualizing the Family Tree:
```ascii
      pam (f)
       |
      bob (m)
     /   \
  ann(f) pat(m)
   |       |
  jim(m)  ...
```

---

## 5. How Prolog Answers Queries

Prolog uses a strategy called **Backward Chaining** and **Backtracking**.
1. It starts with the query (goal).
2. It looks for a fact or the head of a rule that matches the goal.
3. If it finds a rule, the goals in the body become sub-goals.
4. If a path fails, Prolog "backtracks" to the last successful match and tries an alternative.

### Example: `?- predecessor(pam, ann).`
1. **Goal:** `predecessor(pam, ann)`
2. **Match Rule 1:** `predecessor(X, Z) :- parent(X, Z).`
   - Subgoal: `parent(pam, ann)`
   - Database check: No such fact. **Fail.**
3. **Backtrack** and try **Rule 2:** `predecessor(X, Z) :- parent(X, Y), predecessor(Y, Z).`
   - Subgoal 1: `parent(pam, Y)`
   - Database check: Matches `parent(pam, bob)`. So `Y = bob`.
   - Subgoal 2: `predecessor(bob, ann)` (Recursive call)
4. **New Goal:** `predecessor(bob, ann)`
   - Match Rule 1: `parent(bob, ann)`
   - Database check: Matches! **Success.**
5. **Result:** The original query succeeds.

---

**Previous:** [← Structured Knowledge](21_Structured_KR.md) | **Next:** [Prolog Syntax & Meaning →](23_Prolog_Syntax_and_Meaning.md)
