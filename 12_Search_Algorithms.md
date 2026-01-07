# Search Algorithms

## Overview

A search algorithm takes a **search problem** and returns either a **solution** or an **indication of failure**.

---

## 1. Depth-First Search (DFS)

### Strategy
Expands the **deepest node** in the frontier first. Goes as deep as possible before backtracking.

### How it Works:
1. Start at root node
2. Expand deepest unexplored node
3. When can't go deeper, backtrack to most recent node with une xplored children
4. Repeat until goal found or all nodes explored

### Implementation:
- Uses a **Stack** (LIFO - Last In First Out)
- Or implemented recursively

### Example Trace:
```
       A
      / \
     B   C
    / \   \
   D   E   F

Order: A → B → D → E → C → F
```

### Properties:

| Property | Value |
|----------|-------|
| **Complete** | No (can get stuck in cycles) |
| **Optimal** | No |
| **Time** | O(b^m) where m = max depth |
| **Space** | O(b×m) - Only stores path |

### Advantages:
- ✅ Low memory usage
- ✅ Can find solutions quickly if lucky
- ✅ Simple to implement

### Disadvantages:
- ❌ Not complete (infinite loops possible)
- ❌ Not optimal (first solution found may not be best)
- ❌ Can get trapped in deep paths

### When to Use:
- Memory is limited
- Solutions are deep in tree
- All solutions are at similar depth

---

## 2. Breadth-First Search (BFS)

### Strategy
Expands the **shallowest node** in the frontier first. Explores level by level.

### How it Works:
1. Start at root node
2. Explore all neighbors at current depth
3. Move to next depth level
4. Repeat until goal found

### Implementation:
- Uses a **Queue** (FIFO - First In First Out)

### Example Trace:
```
       A
      / \
     B   C
    / \   \
   D   E   F

Order: A → B → C → D → E → F
```

### Properties:

| Property | Value |
|----------|-------|
| **Complete** | Yes (if branching factor is finite) |
| **Optimal** | Yes (if all costs equal) |
| **Time** | O(b^d) where d = depth of solution |
| **Space** | O(b^d) - Stores all nodes at level |

### Advantages:
- ✅ Complete
- ✅ Finds shallowest (optimal if costs equal)
- ✅ Systematic exploration

### Disadvantages:
- ❌ High memory usage
- ❌ Slow if solution is deep
- ❌ Exponential space complexity

### When to Use:
- Sufficient memory available
- Solution is shallow
- Want guaranteed optimal solution (uniform costs)

---

## 3. Depth-Limited Search (DLS)

### Strategy
DFS with a **predetermined depth limit** ℓ (ell). Nodes at depth ℓ are treated as if they have no successors.

### How it Works:
1. Perform DFS
2. Stop expanding nodes beyond depth ℓ
3. Backtrack when limit reached
4. Return failure if no solution found within limit

### Depth Limit Choice:
- Too small: Might miss solution
- Too large: Wastes computation
- Ideal: Slightly more than solution depth

### Properties:

| Property | Value |
|----------|-------|
| **Complete** | No (solution might be deeper than ℓ) |
| **Optimal** | No |
| **Time** | O(b^ℓ) |
| **Space** | O(b×ℓ) |

### Advantages:
- ✅ Avoids infinite loops
- ✅ Low memory like DFS
- ✅ Faster than unlimited DFS

### Disadvantages:
- ❌ Need to know good depth limit
- ❌ Not complete (might set ℓ too small)
- ❌ Not optimal

### When to Use:
- Know approximate solution depth
- Want DFS benefits with loop protection
- Limited memory available

---

## Iterative Deepening Search (IDS)

### Strategy
Combines benefits of BFS and DFS by running DLS with increasing limits: ℓ=0, 1, 2, 3, ...

### How it Works:
1. Try DLS with ℓ=0
2. If no solution, try ℓ=1
3. Keep increasing ℓ until solution found

### Properties:

| Property | Value |
|----------|-------|
| **Complete** | Yes |
| **Optimal** | Yes (if costs equal) |
| **Time** | O(b^d) |
| **Space** | O(b×d) |

### Advantages:
- ✅ Complete like BFS
- ✅ Optimal like BFS
- ✅ Space efficient like DFS
- ✅ Best of both worlds!

### Disadvantages:
- ❌ Revisits nodes multiple times
- ❌ Overhead of repeated searches

### Overhead Analysis:
Surprisingly low! For b=10, d=5:
- Nodes at level 5: 100,000 (generated once)
- Nodes at level 4: 10,000 (generated twice)
- Nodes at level 1: 10 (generated 5 times)
- **Total overhead: ~11% more than single search**

---

## Uniform Cost Search (UCS)

### Strategy
Expands node with **lowest path cost** first. Finds optimal solution even with varying costs.

### How it Works:
1. Use priority queue ordered by path cost
2. Always expand cheapest (g(n) = cost from start)
3. Continue until goal is expanded (not just generated!)

### Properties:

| Property | Value |
|----------|-------|
| **Complete** | Yes (if costs > 0) |
| **Optimal** | Yes |
| **Time** | O(b^(1+⌊C*/ε⌋)) |
| **Space** | O(b^(1+⌊C*/ε⌋)) |

C* = optimal solution cost, ε = minimum step cost

### When to Use:
- Action costs vary
- Need guaranteed optimal solution
- Sufficient memory available

---

## 4. Bidirectional Search

### Strategy
Runs two simultaneous searches: one **forward** from the initial state and one **backward** from the goal. The search stops when the two frontiers meet in the middle.

### Properties:
- **Time Complexity:** $O(b^{d/2})$
- **Space Complexity:** $O(b^{d/2})$
- **Optimality:** Yes (if BFS used).
- **Requirement:** Must be able to search backward from the goal.

---

## Comparison Summary

| Algorithm | Complete | Optimal | Time | Space | Use Case |
|-----------|----------|---------|------|-------|----------|
| **DFS** | No | No | O(b^m) | O(bm) | Deep solutions, low memory |
| **BFS** | Yes | Yes* | O(b^d) | O(b^d) | Shallow solutions |
| **IDS/DFID**| Yes | Yes* | O(b^d) | O(bd) |  |
| **UCS** | Yes | Yes | $O(b^{1+\lfloor C^*/\epsilon \rfloor})$ | $O(b^{1+\lfloor C^*/\epsilon \rfloor})$ | Varying costs |
| **Bidirectional** | Yes | Yes* | O(b^(d/2)) | O(b^(d/2)) |  |
| **Greedy** | No | No | $O(b^m)$ | $O(b^m)$ |  |
| **Hill Climbing**| No | No | N/A | $O(1)$ | Local optimization |

*Optimal if all step costs equal

---

## 5. Greedy Best-First Search


**Greedy Best-First Search** expands the node that appears to be closest to the goal based on the heuristic function $h(n)$.

- **Evaluation Function:** $f(n) = h(n)$
- **Logic:** It "greedily" follows the heuristic estimate, ignoring the cost already paid to reach the current node.
- **Properties:**
  - **Complete:** No (can get stuck in loops).
  - **Optimal:** No.
  - **Complexity:** $O(b^m)$ in worst case.

---

## 6. Local Search: Hill Climbing

**Hill Climbing** is an iterative improvement algorithm that moves in the direction of increasing value (or decreasing cost). It only keeps track of the current state and its neighbors.

### Traps in Hill Climbing:
1. **Local Maxima (Foothills):** A peak that is higher than all neighbors but lower than the global maximum.
2. **Ridges:** A sequence of local maxima that is difficult for greedy algorithms to navigate.
3. **Plateau:** A flat area where all neighbors have the same value (leads to random walks).

### Variants:
- **Stochastic Hill Climbing:** Chooses at random from among the uphill moves.
- **First-choice Hill Climbing:** Generates successors randomly until one is better than current.
- **Random-restart Hill Climbing:** Conducts a series of searches from different random starting states.

---

## 7. Problem Reduction (AND-OR Search)

Some problems are best solved by decomposing them into a set of **subproblems**.

### AND-OR Graphs:
- **OR Nodes:** Represent choices (solve one path).
- **AND Nodes:** Represent subproblems (solve **all** paths).
- **Goal:** A solution is a subtree where every leaf is a goal state and every AND node has all its children included.

**Example:** To "Acquire a Car", you must (AND) "Get Money" AND "Visit Dealer". To "Get Money", you can (OR) "Work" OR "Take Loan".

---

## Choosing the Right Algorithm

### Decision Tree:
1. **Do action costs vary?**
   - Yes → Use UCS or A*
   - No → Continue to #2

2. **Is memory limited?**
   - Yes → Use IDS or DLS
   - No → Continue to #3

3. **Know solution depth?**
   - Yes → Use DLS
   - No → Use BFS or IDS

### General Recommendations:
- **Default choice:** Iterative Deepening Search (IDS)
- **Varying costs:** Uniform Cost Search (UCS)
- **Limited memory:** Depth-First Search (DFS) with cycle checking
- **Known depth:** Depth-Limited Search (DLS)

---

**Previous:** [← Algorithm Performance](11_Algorithm_Performance.md) | **Next:** [Heuristic Functions →](13_Heuristic_Functions.md)
