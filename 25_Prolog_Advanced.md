# Prolog Advanced Control: Cut, Negation, and Built-ins

This section covers how to control Prolog's search behavior and use built-in predicates for input/output and database management.

---

## 1. The Cut (!) Operator

The **Cut** is a special predicate used to prevent backtracking. It "freezes" the choices made so far in the current rule.

### Purpose:
- **Efficiency:** Prune search branches that we know will not lead to a solution.
- **Mutually Exclusive Rules:** Ensure that only one rule is applied (e.g., if-then-else behavior).

**Example: Max of two numbers**
```prolog
max(X, Y, X) :- X >= Y, !.
max(X, Y, Y).
```
- If `X >= Y`, the first rule matches, the cut is executed, and Prolog will **not** try the second rule even if the first rule eventually fails later.

---

## 2. Negation as Failure (`not`)

Prolog uses the **Closed World Assumption**: anything it cannot prove to be true is assumed to be false.

- **`not(P)`:** Succeeds if the goal `P` fails.
- **Limitation:** It is not true logical negation. It only means "not provable".

---

## 3. Built-in Predicates

Prolog provides many pre-defined predicates for common tasks.

### 3.1 Input and Output (6.7)
- **`read(X)`:** Reads the next term from the input stream.
- **`write(X)`:** Outputs the term X to the output stream.
- **`nl`:** Outputs a new line.
- **`tab(N)`:** Outputs N spaces.
- **`see(File)` / `tell(File)`:** Switches input/output to a file.
- **`seen` / `told`:** Closes the current input/output file.

### 3.2 Database Manipulation
- **`assert(P)`:** Adds fact or rule P to the database at runtime.
- **`retract(P)`:** Removes P from the database.

---

## 4. Processing Files of Terms (6.7.2)

A common pattern is to read all terms from a file until the end.

**Example:**
```prolog
process_file(File) :-
    see(File),
    repeat,
    read(Term),
    ( Term = end_of_file -> true ; process(Term), fail ),
    seen.
```
- **`end_of_file`:** A special atom returned by `read` when the file ends.

---

## 5. Summary of Prolog Programming Style
1.  **Declarative:** Focus on what is true.
2.  **Recursive:** Use recursion for loops.
3.  **Symbolic:** Handle data as symbols and structures.
4.  **Controlled:** Use the Cut (!) for performance and logic control.

---

---

## 4. Case Study: The Monkey-Banana Problem

The Monkey-Banana problem is a classic AI puzzle that demonstrates Prolog's power in planning and goal-oriented search.

### Problem Scenario:
A monkey is in a room. Suspended from the ceiling are some bananas, out of the monkey's reach. Also in the room is a chair. The monkey can move around, push the chair, climb onto the chair, and grasp the bananas if it is on the chair under the bananas.

### Prolog Implementation:
```prolog
% state(MonkeyLocation, ChairLocation, HasBananas)

% 1. Grasping the bananas
move(state(middle, middle, hasnot), grasp, state(middle, middle, has)).

% 2. Climbing onto the chair
move(state(L, L, hasnot), climb, state(L, L, hasnot)).

% 3. Pushing the chair
move(state(L1, L1, hasnot), push(L1, L2), state(L2, L2, hasnot)).

% 4. Walking around
move(state(L1, L2, hasnot), walk(L1, L3), state(L3, L2, hasnot)).

% Recursive definition of a solution
canget(state(_, _, has)).
canget(State1) :-
    move(State1, Action, State2),
    canget(State2).
```

---

**Previous:** [← Prolog Lists](24_Prolog_Lists.md) | **Next:** [Formal Grammars & NLP →](26_Formal_Grammars_and_NLP.md)
