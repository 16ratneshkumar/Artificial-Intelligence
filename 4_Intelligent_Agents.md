# Intelligent Agents: Basics & Rationality

## 1. What is an Agent?

### Definition
An **Agent** is anything that can be viewed as:
1.  **Perceiving** its environment through **<abbr title="Devices that detect input like cameras, microphones, keyboards">sensors</abbr>**.
2.  **Acting** upon that environment through **<abbr title="Devices that perform actions like motors, screens, speakers">effectors/actuators</abbr>**.

### Examples
| Agent Type | Sensors | Actuators | Goal |
| :--- | :--- | :--- | :--- |
| **Human** | Eyes, ears, skin, taste | Hands, legs, mouth, body | Survival, comfort, happiness |
| **Robotic Cleaner** | Cameras, dirt sensors, cliff sensors | Wheels, brushes, vacuum | Clean floor, avoid falling |
| **Software Bot** | Keystrokes, file contents, network packets | Screen display, writing files, sending packets | Filter spam, sort data |

---

## 2. Rational Agents

A **Rational Agent** is one that does the "right thing".

### Definition
For each possible <abbr title="History of everything the agent has perceived">percept sequence</abbr>, a rational agent should select an action that is expected to **maximize its performance measure**, given the evidence provided by the percept sequence and whatever built-in knowledge the agent has.

> **Note:** Rationality is NOT <abbr title="Knowing everything (impossible in reality)">omniscience</abbr>. Ominscience means knowing the actual outcome of actions. Rationality is about making the best decision with the *available information*.

### Omniscient Agent
An **Omniscient Agent** knows the **actual outcome** of its actions and can act accordingly; however, omniscience is impossible in reality. Rationality maximizes *expected* performance, while omniscience maximizes *actual* performance.

   *   *Example:* An omniscient agent knows everything in advance(including the actual outcome of its actions), so it acts accordingly to always achieve the best result. It creates an impossible standard for real-world agents.

### The 4 Factors of Rationality (PEAS)
What is rational at any given time depends on four things:

1.  **P**erformance Measure:
    *   The criteria that determine how successful an agent is.
    *   *Example (Vacuum):* +1 point for each clean square, -1 point for each move.
2.  **E**nvironment:
    *   Where the agent operates.
    *   *Example:* A carpeted room with obstacles.
3.  **A**ctuators:
    *   What the agent can do.
    *   *Example:* Move Left, Move Right, Suck dirt.
4.  **S**ensors:
    *   What the agent can perceive.
    *   *Example:* Is the current square dirty? Am I bumping into a wall?

### Ideal Rational Agent
An ideal rational agent always chooses the action that maximizes its expected performance, based on what it knows and sees.

---

## 3. Structure of Intelligent Agents

An agent consists of two main parts:

### Formula
`Agent = Architecture + Program`

1.  **Agent Program**:
    *   The internal logic or algorithm.
    *   **Function:** `Action = AgentFunction(Percept)`
    *   It implements the mapping from percepts to actions.

2.  **Architecture**:
    *   The physical computing device (hardware).
    *   Examples: Computer, Robot body, Server.
    *   The architecture makes the percepts available to the program and runs the program.

---

**Previous:** [← Total Turing Test](3_Total_Turing_Test.md) | **Next:** [Agent Types →](5_Agent_Types.md)
