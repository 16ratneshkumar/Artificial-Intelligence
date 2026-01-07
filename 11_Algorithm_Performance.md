# Algorithm Performance Evaluation

## Measuring Problem-Solving Algorithm Performance

A search algorithm's performance can be evaluated in **4 key ways:**

---

## 1. Completeness

### Definition
Completeness means whether the algorithm is **guaranteed to find a solution when one exists** and **report failure when there is none**.

### Questions to Ask:
- Will the algorithm always find a solution if one exists?
- Will it correctly report failure if no solution exists?
- Can it get stuck in infinite loops?

### Examples:
- **Complete Algorithm:** Breadth-First Search (BFS)
  - Always finds a solution if one exists
  - Cannot get stuck in cycles if handled properly

- **Incomplete Algorithm:** Depth-First Search (DFS) without depth limit
  - Can get stuck in infinite loops
  - May never find a solution even if it exists

### Importance:
**Critical** for real-world applications where reliability is essential.

---

## 2. Cost Optimality (Optimality)

### Definition
Cost optimality means whether the algorithm finds a solution with the **lowest path cost** among all possible solutions.

### Key Points:
- Optimal solution minimizes total cost
- Not all complete algorithms are optimal
- Trade-off between optimality and computational cost

### Path Cost Calculation:
```
Path Cost = Σ cost(state_i, action_i, state_i+1)
```

### Examples:
- **Optimal Algorithm:** Uniform Cost Search, A* with admissible heuristic
  - Guarantees lowest-cost solution

- **Sub-optimal Algorithm:** Greedy Best-First Search
  - Finds a solution quickly but may not be cheapest

### Importance:
**Essential** when solution quality matters (e.g., shortest route, minimum energy)

---

## 3. Time Complexity

### Definition
Time complexity relates to the **time taken to find a solution**. It measures computational efficiency.

### Measured By:
- Number of nodes expanded/generated
- Number of operations performed
- Actual execution time

### Notation:
Usually expressed using Big-O notation: O(b^d)
- **b:** Branching factor (average number of successors)
- **d:** Depth of solution

### Examples:
- **BFS:** O(b^d) - Exponential in depth
- **DFS:** O(b^m) where m is maximum depth
- **A*:** O(b^d) in worst case, but heuristic helps

### Factors Affecting Time:
1. **Branching Factor:** More choices = slower
2. **Solution Depth:** Deeper solutions = more time
3. **Search Strategy:** Different algorithms have different speeds
4. **Heuristic Quality:** Better heuristics = faster search

### Importance:
**Critical** for real-time systems and large problems

---

## 4. Space Complexity

### Definition
Space complexity relates to the **amount of memory needed** to perform the search.

### What Consumes Memory:
- Nodes stored in frontier (open list)
- Nodes stored in explored set (closed list)
- Path being constructed
- Additional data structures

### Notation:
Expressed using Big-O notation: O(b^d)

### Examples:
- **BFS:** O(b^d) - Stores all nodes at current level
- **DFS:** O(b×m) - Stores only path from root to current node
- **A*:** O(b^d) - Stores all generated nodes

### Memory Bottleneck:
- Space often more limiting than time
- Memory fills up faster than you might expect
- Example: b=10, d=6 → 1,000,000 nodes

### Importance:
**Critical** factor - many problems fail due to memory limits, not time

---

## Comparison Table

| Algorithm | Complete? | Optimal? | Time | Space |
|-----------|-----------|----------|------|-------|
| BFS | Yes | Yes* | O(b^d) | O(b^d) |
| DFS | No | No | O(b^m) | O(bm) |
| Depth-Limited | No | No | O(b^l) | O(bl) |
| Uniform Cost | Yes | Yes | O(b^(C*/ε)) | O(b^(C*/ε)) |
| A* | Yes** | Yes*** | O(b^d) | O(b^d) |

*If all step costs are equal  
**If branching factor is finite  
***With admissible heuristic

---

## Trade-offs

### Time vs. Space
- Some algorithms trade time for space (DFS)
- Others trade space for time (BFS)

### Completeness vs. Efficiency
- Complete algorithms may be slow
- Fast algorithms may not guarantee solutions

### Optimality vs. Speed
- Optimal algorithms often take longer
- Greedy algorithms are fast but sub-optimal

---

## Choosing the Right Algorithm

Consider these questions:
1. **Must** I find a solution if one exists? → Need completeness
2. **Must** the solution be optimal? → Need cost optimality
3. How much **time** do I have? → Consider time complexity
4. How much **memory** is available? → Consider space complexity
5. What's the **branching factor** and **depth**? → Affects all metrics

---

## Real-World Considerations

### Beyond the Four Metrics:
- **Implementation complexity**
- **Robustness to errors**
- **Adaptability to changes**
- **Parallelization potential**
- **Heuristic availability**

### Practical Example:
**GPS Navigation System:**
- **Completeness:** Required (must find route)
- **Optimality:** Desired (shortest/fastest route)
- **Time:** Must be fast (real-time response)
- **Space:** Limited by device memory

**Best choice:** A* algorithm with good heuristic

---

**Previous:** [← Search Problems](10_Search_Problems.md) | **Next:** [Search Algorithms →](12_Search_Algorithms.md)
