# Prolog Lists and Arithmetic

Lists are the most important data structure in Prolog for handling sequences of items.

---

## 1. List Representation

A list is either empty or it consists of a **Head** and a **Tail**.

- **Empty List:** `[]`
- **Head:** The first element of the list.
- **Tail:** The rest of the list (which is itself a list).

**Notation:**
- `[a, b, c]`
- `[Head | Tail]` → Head = `a`, Tail = `[b, c]`

---

## 2. Common List Operations

### 2.1 Membership
Checks if an item `X` is in list `L`.
```prolog
member(X, [X | _]).        % X is head of list
member(X, [_ | Tail]) :-   % X is in the tail
    member(X, Tail).
```

### 2.2 Concatenation
Joins list `L1` and `L2` to form `L3`.
```prolog
conc([], L, L).
conc([X | L1], L2, [X | L3]) :-
    conc(L1, L2, L3).
```
- **Usage:** Can be used to find prefixes, suffixes, or to split a list.

---

## 3. Arithmetic in Prolog

Arithmetic in Prolog is unique because it is performed using the `is` operator, not `=` (which is for matching).

### 3.1 The `is` Operator
Forces evaluation of an expression.
`?- X is 3 + 5.` → `X = 8.`
`?- 8 = 3 + 5.` → `no` (because the structures don't match literally).

### 3.2 Comparison Operators
- `X > Y`: X is greater than Y.
- `X < Y`: X is less than Y.
- `X >= Y`: X is greater than or equal to Y.
- `X =:= Y`: Values are equal.
- `X =\= Y`: Values are not equal.

### 3.3 Example: Factorial
```prolog
factorial(0, 1).
factorial(N, F) :-
    N > 0,
    N1 is N - 1,
    factorial(N1, F1),
    F is N * F1.
```

---

## 4. Length of a List
```prolog
list_length([], 0).
list_length([_ | Tail], N) :-
    list_length(Tail, N1),
    N is N1 + 1.
```

---

**Previous:** [← Prolog Syntax & Meaning](23_Prolog_Syntax_and_Meaning.md) | **Next:** [Prolog Advanced Control →](25_Prolog_Advanced.md)
