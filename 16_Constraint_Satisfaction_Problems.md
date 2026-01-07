# Constraint Satisfaction Problems (CSP)

A **Constraint Satisfaction Problem (CSP)** is a mathematical problem defined as a set of objects whose state must satisfy a number of constraints or limitations. CSPs represent a powerful way to model many AI problems, from scheduling to Sudoku.

---

## 1. Formal Definition

A CSP is defined by a triple $(X, D, C)$:

- **$X$ (Variables):** A set of variables $\{X_1, X_2, \dots, X_n\}$ that need to be assigned values.
- **$D$ (Domains):** A set of domains $\{D_1, D_2, \dots, D_n\}$, where $D_i$ is the set of allowed values for $X_i$.
- **$C$ (Constraints):** A set of constraints that define the allowed combinations of values for subsets of variables.

### Goal:
To find a **complete** and **consistent** assignment:
- **Consistent:** No constraints are violated.
- **Complete:** Every variable is assigned a value.

---

## 2. Examples of CSPs

### A. Cryptarithmetic Problems
These are mathematical puzzles where each letter represents a distinct digit (0-9). The goal is to find digits that make the arithmetic sum correct.

#### **Example 1: SEND + MORE = MONEY**
```text
    S E N D
+   M O R E
-----------
  M O N E Y
```

**Step-by-Step Logical Solution:**

1.  **Column 5 ($M$):** The maximum sum of two 4-digit numbers is $9999 + 9999 = 19998$. The 5th digit $M$ can *only* be the carry from the 4th column. Therefore, **$M = 1$**.
2.  **Column 4 ($S + M = O$):** Since $M=1$, we have $S + 1 = 10 + O$ or $S + 1 + 1 (\text{carry}) = 10 + O$.
    - If $S + 1 = 10 + O$, then $S=9, O=0$. 
    - If $S + 2 = 10 + O$, then $S=8, O=0$ or $S=9, O=1$.
    - Since $M=1$, $O$ cannot be 1. Thus, **$O = 0$**. 
    - This also means $S$ must be **9** (or 8 if there is a carry from the 3rd column).
3.  **Column 3 ($E + O = N$):** Since $O=0$, we have $E + 0 = N$ (impossible as letters must be distinct) or $E + 0 + 1 (\text{carry}) = N$. Therefore, **$N = E + 1$**.
4.  **Column 2 ($N + R = E$):** Substitute $N = E + 1$:
    - $(E + 1) + R = 10 + E \implies R + 1 = 10 \implies R = 9$. (But $S=9$, and digits must be distinct).
    - Or $(E + 1) + R + 1 (\text{carry}) = 10 + E \implies R + 2 = 10 \implies \mathbf{R = 8}$.
5.  **Column 1 ($D + E = Y$):** We need a carry to Column 2, so $D + E = 10 + Y$.
    - Available digits: $\{2, 3, 4, 5, 6, 7\}$.
    - If we test $E=5$, then $N=6$. 
    - Then $D + 5 = 10 + Y \implies D = 5 + Y$.
    - If $Y=2$, then $D=7$. (Valid!)

**Final Assignment:**
- **S=9, E=5, N=6, D=7, M=1, O=0, R=8, Y=2**
- **Verification:** $9567 + 1085 = 10652$. ✅

---

#### **Example 2: TWO + TWO = FOUR**
```text
    T W O
+   T W O
---------
  F O U R
```

**Step-by-Step Logical Solution:**

1.  **Column 1 ($O + O = R$):** $2O = R$ or $2O = 10 + R$.
2.  **Column 4 ($F$):** Like the previous example, $F$ must be the carry from $T+T$. Since $T < 10$, $F$ can only be **1**.
3.  **Column 3 ($T + T = O$):** $2T = 10 + O$ (since there's a carry to $F$).
    - If $F=1, T=7$, then $2(7)=14 \implies O=4$.
    - If $O=4$, then $2O = 8 \implies \mathbf{R=8}$.
4.  **Column 2 ($W + W = U$):** Use remaining digits $\{2, 3, 5, 6, 9\}$.
    - If $W=3$, $2W=6 \implies \mathbf{U=6}$. (No carry to $T+T$, which fits).

**Final Assignment:**
- **T=7, W=3, O=4, F=1, U=6, R=8**
- **Verification:** $734 + 734 = 1468$. ✅


#### **Example 3: ODD + ODD = EVEN**
```text
    O D D
+   O D D
---------
  E V E N
```

**Step-by-Step Logical Solution:**

1.  **Column 4 ($E$):** The maximum sum of two 3-digit numbers is $999 + 999 = 1998$. The 4th digit $E$ must be the carry from the 3rd column. Thus, **$E = 1$**.
2.  **Column 2 ($D + D = E$):** Since $E=1$, $D + D$ must end in 1, which is impossible since $2D$ is always even. Therefore, there must be a carry from Column 1.
    - $D + D + 1 (\text{carry}) = E + 10 \times C_2$.
    - $2D + 1 = 11$ or $21$. Since $D \le 9$, $2D + 1 \le 19$. So $2D + 1 = 11 \implies 2D = 10 \implies \mathbf{D = 5}$.
3.  **Column 1 ($D + D = N$):** With $D = 5$, $5 + 5 = 10$. So **$N = 0$**, and we generate a carry of 1 to Column 2 (which matches our assumption in step 2).
4.  **Column 3 ($O + O + C_2 = V$):** From Column 2, $5 + 5 + 1 = 11$, so the carry to Column 3 is $C_2 = 1$.
    - $O + O + 1 = V + 10 \times E \implies 2O + 1 = 10 + V$.
    - This means $V$ must be an odd number (since $2O - 9 = V$, and an even minus an odd is odd).
    - Available digits: $\{2, 3, 4, 6, 7, 8, 9\}$ (since $E=1, D=5, N=0$).
    - If $V = 3$, $2O = 12 \implies \mathbf{O = 6}$. (Valid)
    - If $V = 7$, $2O = 16 \implies \mathbf{O = 8}$. (Valid)
    - If $V = 9$, $2O = 18 \implies O = 9$. (Invalid: $O$ and $V$ must be distinct).

**Final Assignments (Multiple Valid Solutions):**
- **Solution 1:** O=6, D=5, E=1, V=3, N=0
    - **Verification:** $655 + 655 = 1310$. ✅
- **Solution 2:** O=8, D=5, E=1, V=7, N=0
    - **Verification:** $855 + 855 = 1710$. ✅

---

---

## 3. Constraint Propagation (Inference)

CSPs can be solved by search, but we can often reduce the search space through **inference** (constraint propagation).

### 3.1 Node Consistency
A single variable is **node-consistent** if all values in its domain satisfy its unary constraints.
- **Example:** If $X \in \{1, 2, 3, 4\}$ and $X > 2$, then $X$ becomes node-consistent with domain $\{3, 4\}$.

### 3.2 Arc Consistency (2-Consistency)
A variable $X_i$ is **arc-consistent** with respect to $X_j$ if for every value in $D_i$ there is some value in $D_j$ that satisfies the binary constraint $(X_i, X_j)$.

#### **The AC-3 Algorithm:**
1. Maintain a queue of all arcs in the CSP.
2. While queue is not empty:
   - Pop arc $(X_i, X_j)$.
   - Remove values from $D_i$ that have no consistent match in $D_j$.
   - If $D_i$ changed, add all neighboring arcs $(X_k, X_i)$ back to the queue.
3. If any domain becomes empty, the CSP is unsolvable.

### 3.3 Path Consistency (3-Consistency)
A pair $\{X_i, X_j\}$ is **path-consistent** with respect to $X_m$ if for every consistent assignment $\{X_i=a, X_j=b\}$, there is an assignment to $X_m$ that satisfies constraints on $(X_i, X_m)$ and $(X_m, X_j)$.
- It looks at triples of variables to find inconsistencies that arc consistency misses.

### 3.4 K-Consistency
- **1-Consistency:** Node consistency.
- **2-Consistency:** Arc consistency.
- **3-Consistency:** Path consistency.
- **Strong K-Consistency:** A graph is strongly k-consistent if it is $j$-consistent for all $j \le k$.
- **Theorem:** If a graph is strongly $n$-consistent (where $n$ is the number of nodes), it can be solved without backtracking.

---

## 4. CSP Solving Techniques (Search)

1.  **Backtracking Search:** A depth-first search that chooses values for one variable at a time.
2.  **Constraint Propagation:** Reducing the domain of variables (e.g., Arc Consistency, AC-3).
3.  **Heuristics:**
    - **Minimum Remaining Values (MRV):** Choose the variable with the fewest remaining "legal" values.
    - **Degree Heuristic:** Choose the variable with the most constraints on other unassigned variables.
    - **Least Constraining Value:** Choose the value that leaves the most options for neighboring variables.

---

**Previous:** [← Minimax & Alpha-Beta](15_Minimax_Alpha_Beta.md) | **Next:** [Propositional Logic →](17_Propositional_Logic.md)
