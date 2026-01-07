# Best-First Search & A* Algorithm

## Best-First Search

### Overview
**Best-First Search** is a family of search algorithms that select nodes to expand based on an **evaluation function** f(n).

### Core Idea:
- Use a priority queue ordered by f(n)
- Always expand the "best" node according to evaluation function
- Different f(n) → Different algorithms

---

---

## 2. A* Search (A-Star)

### The Optimal Informed Search Algorithm

#### Evaluation Function:
**f(n) = g(n) + h(n)**

Where:
- **g(n)** = actual cost from start to node n
- **h(n)** = heuristic estimate from n to goal
- **f(n)** = estimated total cost of cheapest solution through n

#### Strategy:
- Expand node with lowest **total estimated cost**
- Balances:
  - Cost already paid: g(n)
  - Estimated remaining cost: h(n)

#### Algorithm:
```
1. Add start node to frontier with f(start) = h(start)
2. Loop:
   a. If frontier empty, return failure
   b. Remove node with lowest f(n) from frontier
   c. If node is goal, return solution
   d. Expand node, add successors to frontier
   e. For each successor s:
      - Compute g(s) = g(node) + cost(node, s)
      - Compute f(s) = g(s) + h(s)
      - Add to frontier if not visited or found cheaper path
```

---

### Properties of A*

#### Completeness:
**Yes** - A* is complete
- If branching factor is finite
- Finds solution if one exists

#### Optimality:
**Yes** - A* is optimal **IF h(n) is admissible**

**Proof Sketch:**
1. Suppose suboptimal goal G₂ is returned before optimal goal G
2. There must be a node n on path to G in frontier
3. f(n) = g(n) + h(n) ≤ g(n) + h*(n) = C* (optimal cost)
4. f(G₂) = g(G₂) > C* (suboptimal)
5. Therefore f(n) < f(G₂)
6. So A* would expand n before G₂
7. Contradiction! ∎

#### Optimally Efficient:
A* is **optimally efficient** among all optimal algorithms using same heuristic.
- No other algorithm is guaranteed to expand fewer nodes
- Any algorithm that expands fewer nodes risks missing optimal solution

#### Complexity:

| Property | Value |
|----------|-------|
| **Complete** | Yes |
| **Optimal** | Yes (with admissible h) |
| **Time** | O(b^d) |
| **Space** | O(b^d) - Main limitation! |

---

### Why A* Works

#### Intuition:
- **g(n):** Actual cost so far (what we know)
- **h(n):** Estimated future cost (what we guess)
- **f(n):** Total estimated cost (know + guess)

A* chooses path that promises lowest total cost.

#### Contour Visualization:
A* expands nodes in order of f-value:
```
f = C₁  f = C₂  f = C₃ ... f = C* (goal)
```
Forms contours of equal f-value.

---

### A* vs Other Algorithms

| **A*** | $g(n) + h(n)$ | Yes | Yes* |

*With admissible heuristic

#### Relationship:
- **UCS** is A* with h(n) = 0
- **Greedy** is A* ignoring g(n)
- **A*** balances both optimally

---

### Improving A* Efficiency

#### 1. Better Heuristics
- More accurate h(n) → fewer nodes expanded
- Dominating heuristics preferred
- Trade-off: computation time vs. accuracy

#### 2. Iterative Deepening A* (IDA*)
IDA* performs a series of depth-first searches, but instead of using a depth limit, it uses an **f-limit** (total estimated cost). It combines the memory efficiency of DFS with the optimality of A*.

**Key Properties:**
- **Space complexity:** $O(d)$ (linear) instead of $O(b^d)$.
- **Optimality:** Guaranteed if the heuristic $h(n)$ is admissible.
- **Also known as:** Depth-First Iterative Deepening (DFID) with heuristic pruning.

**Steps:**
1. **Initial Threshold:** Set threshold $T = f(\text{start}) = h(\text{start})$.
2. **Search:** Perform a depth-first search.
3. **Pruning:** If $f(n) > T$, prune the branch.
4. **Update:** If no goal is found, set the new threshold $T$ to the minimum $f$-value that exceeded the previous threshold.
5. **Repeat:** Repeat the search with the new $T$ until the goal is found.

#### 3. Branch-and-Bound Search

**Branch-and-Bound** is a general search strategy that maintains the best solution found so far and prunes any branch whose lower bound ($f$-value) exceeds the current best. In AI, this often refers to Uniform Cost Search where we track the "cost of the best path to goal".

**Steps (Algorithm):**
1. **Initialize:** Place the starting node with path length 0 on a priority queue.
2. **Loop:** Until queue is empty or goal found:
   a. Remove the first path (lowest cost) from the queue.
   b. If it contains a goal node, **Success**.
   c. Otherwise, extend the path by one step to all possible children.
   d. Compute the cost of new paths and add them to the queue.
   e. Sort the queue by path cost (lowest first).
3. **Failure:** If queue is empty, exit with failure.

#### 4. Memory-Bounded A*

**SMA* (Simplified Memory-Bounded A*):**
- Uses all available memory.
- When memory is full, it drops the worst node.
- It remembers the $f$-value of forgotten subtrees to regenerate them if needed.

**RBFS (Recursive Best-First Search):**
- Mimics Best-First Search but uses only $O(bd)$ space.
- Uses recursion with $f$-limits to backtrack and explore better branches.

---

## Weighted A*

### Trade Optimality for Speed

#### Evaluation Function:
**f(n) = g(n) + w × h(n)**

Where $w > 1$ (typically 1.2 to 2.0).

#### Effect:
- **w = 1:** Standard A* (optimal).
- **w > 1:** More greedy behavior; finds solutions much faster but sacrifices optimality.
- **Guarantee:** The solution cost found will be no more than $w$ times the optimal cost.

---

## Practical Example: Route Finding

### Problem:
Find shortest route from Arad to Bucharest.

### Heuristic:
h(n) = straight-line distance to Bucharest

### A* Execution:

**Iteration 1:**
- Frontier: {Arad}
- f(Arad) = 0 + 366 = 366
- Expand Arad

**Iteration 2:**
- Frontier: {Sibiu, Timisoara, Zerind}
- f(Sibiu) = 140 + 253 = 393 ← **Lowest**
- f(Timisoara) = 118 + 329 = 447
- f(Zerind) = 75 + 374 = 449
- Expand Sibiu

**Iteration 3:**
- Add Sibiu's neighbors to frontier
- Continue expanding lowest f(n)...

**Final:**
- Path: Arad → Sibiu → Rimnicu Vilcea → Pitesti → Bucharest
- Cost: 418 km (optimal!)

---

## Key Insights

### When to Use A*:
✅ Have good admissible heuristic  
✅ Need optimal solution  
✅ Have sufficient memory  
✅ Problem is not too large  

### When to Use Alternatives:
- **IDA*** if memory limited
- **Weighted A*** if optimality not critical
- **Greedy** if just need any solution fast
- **UCS** if no heuristic available

---

## Summary

### A* is Gold Standard:
- **Optimal:** With admissible heuristic
- **Efficient:** Optimally efficient for given heuristic
- **Informed:** Uses domain knowledge effectively
- **Flexible:** Can adjust with different heuristics

### Main Limitation:
- **Space complexity:** $O(b^d)$ can be prohibitive
- **Solution:** Use IDA* or SMA* for memory-bounded search

### Success Formula:
**Good heuristic + A* = Efficient optimal search**

---

**Previous:** [← Heuristic Functions](13_Heuristic_Functions.md) | **Next:** [Minimax & Alpha-Beta →](15_Minimax_Alpha_Beta.md)
