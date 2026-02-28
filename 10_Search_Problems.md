# Search Problems - Formal Definition

## What is a Search Problem?

A search problem is a formal specification of a problem that an agent needs to solve by finding a sequence of actions. It provides a abstract model that allows algorithms to find solutions.

---

## Formal Definition of a Search Problem

A search problem can be formally defined with the following components:

### 1. State Space
- **Definition:** A set of all possible states that the environment can be in
- **Representation:** States must be abstract yet sufficient
- **Example:** In a chess game, each board configuration is a state

### 2. Initial State
- **Definition:** The state that the agent starts in
- **Notation:** Often denoted as S₀ or S_initial
- **Example:** In route finding, the starting city

### 3. Goal State(s)
- **Definition:** A set of one or more states that satisfy the goal
- **Goal Test:** A function that determines if a state is a goal state
- **Types:**
  - **Explicit:** Specific goal states listed
  - **Implicit:** Goal defined by properties (e.g., checkmate in chess)

### 4. Actions
- **Definition:** The actions available to the agent
- **Function:** ACTIONS(s) returns the set of actions executable in state s
- **Example:** In 8-puzzle, actions = {UP, DOWN, LEFT, RIGHT}

### 5. Transition Model
- **Definition:** Describes what each action does
- **Function:** RESULT(s, a) returns the state resulting from doing action a in state s
- **Also called:** Successor function
- **Deterministic:** Single outcome for each (state, action) pair
- **Stochastic:** Multiple possible outcomes with probabilities

### 6. Action Cost Function
- **Definition:** Gives the numeric cost of applying action a in state s to reach state s'
- **Notation:** COST(s, a, s') or c(s, a, s')
- **Default:** Usually assumed to be 1 if not specified
- **Example:** In route finding, the distance between cities

---

## Additional Concepts

### Path
- **Definition:** A sequence of actions that connects states
- **Example:** [Action1, Action2, Action3]
- **Path through states:** [S₀, S₁, S₂, S₃]

### Solution
- **Definition:** A path from the initial state to a goal state
- **Any solution:** Reaches the goal (may not be optimal)
- **Example:** Any route from City A to City B

### Optimal Solution
- **Definition:** A solution with the **lowest path cost** among all solutions
- **Path Cost:** Sum of individual action costs along the path
- **Formula:** Path Cost = Σ COST(sᵢ, aᵢ, sᵢ₊₁) for all steps in path
- **Goal:** Most algorithms aim to find optimal or near-optimal solutions

---

## Example: 8-Puzzle Problem

**State Space:**
- All configurations of 8 numbered tiles + 1 blank space in a 3×3 grid
- Total states: 9!/2 = 181,440 reachable states

**Initial State:**
```
1 2 3
4 5 6
7 8 _
```

**Goal State:**
```
1 2 3
8 _ 4
7 6 5
```

**Actions:**
- Move blank space: UP, DOWN, LEFT, RIGHT (when legal)

**Transition Model:**
- Moving blank swaps it with adjacent tile

**Action Cost:**
- Each move costs 1

**Solution:**
- Sequence of moves that transforms initial state to goal state

---

## Example: Route Finding Problem

**State Space:**
- All cities on the map

**Initial State:**
- Arad (starting city)

**Goal State:**
- Bucharest (destination city)

**Actions:**
- Drive from current city to any directly connected city

**Transition Model:**
- RESULT(Arad, DriveToBucharest) = Bucharest

**Action Cost:**
- Distance between cities in kilometers

**Solution:**
- Path: Arad → Sibiu → Fagaras → Bucharest
- Path Cost: 140 + 99 + 211 = 450 km

---

## State Space vs. Search Tree

### State Space Graph
- Nodes represent states
- Edges represent actions
- May contain cycles
- States can be revisited

### Search Tree
- Root is initial state
- Nodes represent states in exploration
- Same state can appear multiple times
- No cycles (tree structure)
- Used by search algorithms

---

## Key Principles

1. **Abstraction:** Remove unnecessary details from states
2. **Completeness:** Ensure all relevant information is captured
3. **Efficiency:** Balance between detail and computational cost
4. **Goal-oriented:** Everything should serve finding the solution

---

**Previous:** [← Problem Solving Agents](9_Problem_Solving_Agents.md) | **Next:** [Algorithm Performance →](11_Algorithm_Performance.md)
