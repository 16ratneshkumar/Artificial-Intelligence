# Types of Agents

This section explores the four main architectural designs for intelligent agents, ranging from simple to complex.

---

## 1. Simple Reflex Agents
**"Do X if Y happens right now."**

-   **Concept:** These agents select actions based **only** on the current percept, ignoring the rest of the percept history.
-   **Requirement:** The environment must be fully observable (the agent needs to see the relevant part of the world to make the right decision).
-   **Logic:** Condition-Action Rule (If `Condition` then `Action`).

### Example: Thermostat
*   **Percept:** Current Temperature = 15°C
*   **Rule:** `IF temperature < 20°C THEN Turn Heater ON`
*   **Action:** Turn Heater ON
*   *(It doesn't care what the temperature was 5 minutes ago, only right now).*

---

## 2. Model-Based Reflex Agents
**"Do X based on what I see now AND what I remember."**

-   **Concept:** These agents maintain an **internal state** (history) to keep track of aspects of the world that are not currently visible.
-   **Why:** Necessary for partially observable environments.
-   **Key Component:** A "Model" of the world (knowledge about how the world works and evolves).

### Example: Autonomous Car Changing Lanes
*   **Percept:** The car in front is slow.
*   **Internal State:** Remembered that a fast car was approaching in the left lane 2 seconds ago (even if it's in the blind spot now).
*   **Action:** Wait before changing lanes.

---

## 3. Goal-Based Agents
**"Do X because it helps me get to Y."**

-   **Concept:** The agent acts to achieve a specific **Goal**.
-   **Difference:** Knowing the state of the world isn't enough; the agent needs to know what it's trying to achieve.
-   **Capability:** Search and Planning. The agent considers the *consequences* of its actions.

### Example: GPS Navigation (Google Maps)
*   **Current State:** At Home.
*   **Goal:** Reach the Airport.
*   **Decision:** The agent (app) calculates multiple routes and chooses the turn that gets it closer to the airport, not just any random turn.

---

## 4. Utility-Based Agents
**"Do X because it's the BEST way to get to Y."**

-   **Concept:** Goals are not enough (there might be many ways to reach the airport). We want the *best* way.
-   **Utility Function:** Maps a state to a real number (score) representing how "happy" or "successful" the agent is.
-   **Focus:** Maximizing **Utility** (Efficiency, Speed, Safety, Cost).

### Example: Taxi Routing
*   **Goal:** Reach destination.
*   **Utility Factors:** Time taken, Fuel cost, Passenger comfort.
*   **Decision:** Choose the route that is 5 minutes faster (Higher Utility) even if it's slightly longer in distance.

---

**Previous:** [← Intelligent Agents](4_Intelligent_Agents.md) | **Next:** [Environment Properties →](6_Environment_Properties.md)
