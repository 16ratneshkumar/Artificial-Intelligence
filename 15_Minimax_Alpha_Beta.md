# Game Theory: Minimax & Alpha-Beta Pruning

## Adversarial Search

### Overview
In games, we face an **opponent** trying to defeat us. Unlike standard search where environment is passive, games involve:
- Multiple agents
- Conflicting goals
- Competitive decision making

---

## Game Characteristics

### Types of Games:

| Property | Options |
|----------|---------|
| **Deterministic** | Chess, Checkers, Go |
| **Stochastic** | Backgammon, Monopoly |
| **Perfect Information** | Chess, Go |
| **Imperfect Information** | Poker, Bridge |
| **Zero-Sum** | One wins, other loses |
| **Cooperative** | Both can benefit |

**Focus:** Deterministic, perfect information, zero-sum games (like Chess, Tic-Tac-Toe)

---

## Game Formulation

### Components:
1. **Players:** Usually 2 (MAX and MIN)
2. **Initial State:** Starting configuration
3. **Actions(s):** Legal moves from state s
4. **Result(s, a):** Resulting state from action
5. **Terminal-Test(s):** Is game over?
6. **Utility(s, p):** Numerical value for player p when game ends

### Example: Tic-Tac-Toe
- **Players:** X (MAX) and O (MIN)
- **Initial:** Empty 3×3 board
- **Actions:** Place mark in empty cell
- **Terminal:** 3 in a row or board full
- **Utility:** +1 (X wins), -1 (O wins), 0 (draw)

---

## Minimax Algorithm

### Core Idea
- **MAX** tries to maximize utility
- **MIN** tries to minimize utility
- Both play optimally

### Strategy:
1. MAX chooses move with **highest** minimax value
2. MIN chooses move with **lowest** minimax value
3. Recursively evaluate game tree

### Minimax Value:

**Minimax(s) =**
- **Utility(s)** if s is terminal
- **max_{a} Minimax(Result(s,a))** if MAX's turn
- **min_{a} Minimax(Result(s,a))** if MIN's turn

### Algorithm:
```
function Minimax-Decision(state):
    return action with max value in:
        {(a, Min-Value(Result(state, a))) for all actions a}

function Max-Value(state):
    if Terminal-Test(state):
        return Utility(state)
    v = -∞
    for each action in Actions(state):
        v = max(v, Min-Value(Result(state, action)))
    return v

function Min-Value(state):
    if Terminal-Test(state):
        return Utility(state)
    v = +∞
    for each action in Actions(state):
        v = min(v, Max-Value(Result(state, action)))
    return v
```

---

### Minimax Example: Simple Game Tree

```
         A (MAX)
        /   \
       /     \
      B       C (MIN)
     / \     / \
    D   E   F   G (MAX)
    3   5   2   9

Evaluation:
- Min-Value(B) = min(3, 5) = 3
- Min-Value(C) = min(2, 9) = 2
- Max-Value(A) = max(3, 2) = 3
- Decision: Choose left branch (B)
```

---

### Properties of Minimax:

| Property | Value |
|----------|-------|
| **Complete** | Yes (finite tree) |
| **Optimal** | Yes (vs optimal opponent) |
| **Time** | O(b^m) |
| **Space** | O(bm) depth-first |

Where:
- b = branching factor
- m = maximum depth

---

## Problem: Complexity

### Real Games:
- **Chess:** b ≈ 35, m ≈ 100 → 35^100 ≈ 10^154 nodes!
- **Go:** b ≈ 250, m ≈ 150 → Impossible to search fully

### Solution: Depth-Limited Search
1. Cut off search at depth d
2. Use **evaluation function** instead of utility
3. Estimate position value

---

## Alpha-Beta Pruning

### The Optimization

**Key Insight:** We can ignore parts of the game tree that won't affect the final decision.

### Idea:
- Keep track of best values found so far
- **α:** Best value for MAX along path
- **β:** Best value for MIN along path
- **Prune** when further search is futile

---

### Alpha-Beta Rules:

**α (alpha):**
- MAX's best option on path to root
- Initially: α = -∞
- Updates: α = max(α, value)

**β (beta):**
- MIN's best option on path to root
- Initially: β = +∞
- Updates: β = min(β, value)

**Pruning Condition:**
- Prune when β ≤ α
- Remaining branches won't affect outcome

---

### Alpha-Beta Algorithm:

```
function Alpha-Beta-Search(state):
    v = Max-Value(state, -∞, +∞)
    return action with value v

function Max-Value(state, α, β):
    if Terminal-Test(state):
        return Utility(state)
    v = -∞
    for each action in Actions(state):
        v = max(v, Min-Value(Result(state, action), α, β))
        if v ≥ β:
            return v  # β cutoff (prune!)
        α = max(α, v)
    return v

function Min-Value(state, α, β):
    if Terminal-Test(state):
        return Utility(state)
    v = +∞
    for each action in Actions(state):
        v = min(v, Max-Value(Result(state, action), α, β))
        if v ≤ α:
            return v  # α cutoff (prune!)
        β = min(β, v)
    return v
```

---

### Alpha-Beta Example:

```
            MAX (α=-∞, β=+∞)
           /              \
          /                \
    MIN (α=-∞, β=+∞)    MIN (α=3, β=+∞)
      /    \              /    \
     /      \            /      \
   MAX      MAX        MAX      MAX
   / \      / \        / \      / \
  3   5    2   9      1   6    0   8
  
Step-by-step:
1. Explore left: finds 3, 5 → MIN chooses 3
2. Update α = 3 at root
3. Explore right/left: finds 1
   - β = 1 for right MIN node
4. At right MIN: β(1) ≤ α(3) → PRUNE!
   - No need to check 6, 0, 8
5. Result: Choose left (value 3)

Pruned: 3 nodes (6, 0, 8)
```

---

### Alpha-Beta Effectiveness:

**Perfect Ordering (best-case):**
- Time: O(b^(m/2))
- Effectively **doubles solvable depth!**
- Example: b=35, can search depth 8 instead of 4

**Random Ordering (average-case):**
- Time: O(b^(3m/4))
- Still significant improvement

**Move Ordering Matters:**
- Evaluate likely good moves first
- Use heuristics to sort moves
- Iterative deepening helps

---

## Evaluation Functions

### Purpose:
Estimate utility of non-terminal positions.

### Good Evaluation Functions:
1. **Correlate with winning chances**
2. **Fast to compute**
3. **Consider multiple features**

### Example: Chess Evaluation

**Simple:** Material count
```
Eval(s) = 9×(Q_we - Q_them) + 5×(R_we - R_them) + 
          3×(B_we - B_them) + 3×(N_we - N_them) + 
          1×(P_we - P_them)
```
Q=Queen, R=Rook, B=Bishop, N=Knight, P=Pawn

**Advanced:** Add positional factors
- Piece mobility
- King safety
- Pawn structure
- Control of center

---

## Practical Considerations

### 1. Quiescence Search
- Don't stop at unstable positions
- Continue through "quiet" position
- Avoid horizon effect

### 2. Iterative Deepening
- Search depth 1, then 2, then 3...
- Any-time algorithm
- Helps move ordering

### 3. Transposition Tables
- Cache previously evaluated positions
- Same position via different move orders
- Huge time savings

### 4. Opening Books & Endgame Databases
- Pre-computed optimal play
- Opening: Use known good moves
- Endgame: Perfect play from databases

---

## Comparison Summary

| Aspect | Minimax | Alpha-Beta |
|--------|---------|------------|
| **Result** | Optimal | Optimal (same as minimax) |
| **Nodes Searched** | O(b^m) | O(b^(m/2)) best case |
| **Pruning** | None | Yes |
| **Complexity** | Higher | Lower |
| **Correctness** | Guaranteed | Guaranteed |

**Key Point:** Alpha-Beta gives **same answer** as Minimax but **much faster!**

---

## Real-World Applications

### Games Using These Algorithms:
- **Chess:** Deep Blue, Stockfish
- **Checkers:** Chinook (solved game!)
- **Othello:** Logistello
- **Go:** Combined with Monte Carlo Tree Search

### Beyond Games:
- Economic decision making
- Military strategy
- Competitive robotics
- Auction bidding

---

## Key Takeaways

✅ **Minimax:** Optimal strategy for perfect play  
✅ **Alpha-Beta:** Same result, much faster via pruning  
✅ **Evaluation Functions:** Extend to larger games  
✅ **Move Ordering:** Critical for pruning effectiveness  
✅ **Depth-Limited:** Practical necessity for complex games  

### Success in Games:
**Good Evaluation + Deep Search + Alpha-Beta Pruning + Move Ordering = Strong Game AI**

---

**Previous:** [← A* Search](14_A_Star_Search.md) | **Next:** [Propositional Logic →](16_Propositional_Logic.md)
