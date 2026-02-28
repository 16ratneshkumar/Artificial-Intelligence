# Transition Model & Problem Solving Agents

## Transition Model

A **Transition Model** describes how the environment changes in response to the agent's actions. It specifies the result of applying an action in a particular state.

**Key Aspects:**
- Defines state transitions
- Maps (state, action) pairs to resulting states
- May be deterministic or stochastic
- Essential for planning and search

---

## Problem Solving Agent

### Definition
A **Problem Solving Agent** is an agent that plans ahead by considering a sequence of actions that form a path to a goal state when the correct action to take is not immediately obvious.

### Characteristics
- Uses **search** as the computational process
- Considers multiple possible action sequences
- Evaluates paths before execution
- Goal-directed behavior

### When to Use Problem Solving Agents
- Environment is predictable
- Actions have known effects
- Goal is clearly defined
- Solution requires multiple steps

---

## Search Process

**Search** is the computational process undertaken by problem-solving agents to find a sequence of actions leading from the initial state to a goal state.

### Search Components:
1. **State Space:** All possible configurations
2. **Initial State:** Starting point
3. **Goal Test:** Determines if goal is reached
4. **Actions:** Available choices at each state
5. **Transition Model:** Effects of actions
6. **Path Cost:** Total cost of action sequence

### Example: Route Finding
- **States:** Cities on a map
- **Initial State:** Starting city
- **Goal:** Destination city
- **Actions:** Drive between connected cities
- **Transition Model:** Roads connecting cities
- **Path Cost:** Distance traveled

---

## Types of Search Problems

### 1. Toy Problems
- Simple, well-defined
- Used for testing algorithms
- Examples: 8-puzzle, Missionaries and Cannibals

### 2. Real-world Problems
- Complex, practical applications
- Examples: Route planning, scheduling, robotics

---

## Search Strategy

A search strategy determines which state to expand next during the search process.

**Key Decisions:**
- Order of node expansion
- When to stop searching
- How to handle repeated states
- Memory vs. time trade-offs

**Goal:** Find a solution efficiently while minimizing computational cost.

---

**Previous:** [← PEAS Description](8_PEAS_Description.md) | **Next:** [Search Problems →](10_Search_Problems.md)
