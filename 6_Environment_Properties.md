# Environment Properties

Understanding the environment is crucial for designing the right agent. We classify environments based on several properties.

---

## 1. Accessible vs Inaccessible (Fully vs Partially Observable)

-   **Accessible (Fully Observable):** The agent's sensors give it access to the **complete state** of the environment at each point in time. The agent doesn't need to keep an internal memory.
    *   *Example:* **Chess**. (You can see the entire board and all pieces at all times).
-   **Inaccessible (Partially Observable):** Sensors are noisy or inaccurate, or parts of the state are missing.
    *   *Example:* **Poker**. (You cannot see the other players' cards).
    *   *Example:* **Self-Driving Car**. (You cannot see around corners or behind large trucks).

---

## 2. Deterministic vs Non-Deterministic (Stochastic)

-   **Deterministic:** The next state of the environment is completely determined by the **current state** and the **agent's action**. There is no randomness.
    *   *Example:* **Solving a Puzzle**. (If you move a piece, it ends up exactly where you put it).
-   **Non-Deterministic (Stochastic):** There is uncertainty. The same action in the same state might lead to different outcomes (due to other agents, wind, slippery roads, etc.).
    *   *Example:* **Dice Game**. (Throwing a die doesn't guarantee a 6).
    *   *Example:* **Taxi Driving**. (Traffic, pedestrians, and engine reliability are unpredictable).

---

## 3. Episodic vs Non-Episodic (Sequential)

-   **Episodic:** The agent's experience is divided into independent "episodes". Each episode consists of the agent perceiving and then acting. The quality of the action depends **only** on that episode.
    *   *Example:* **Image Classification Bot**. (Spotting a cat in Image A doesn't affect how it spots a dog in Image B).
    *   *Example:* **Factory Robot Arm**. (Picking up part #100 is the same task as picking up part #1).
-   **Non-Episodic (Sequential):** The current decision affects all future decisions. Short-term actions have long-term consequences.
    *   *Example:* **Chess**. (A move you make now determines your position 10 moves later).
    *   *Example:* **Driving**. (Changing lanes now affects where you will be in 1 minute).

---

## 4. Static vs Dynamic

-   **Static:** The environment **does not change** while the agent is deliberating (thinking). The agent doesn't need to worry about time passing.
    *   *Example:* **Crossword Puzzle**. (The clues don't change while you are thinking).
-   **Dynamic:** The environment changes while the agent is thinking. If the agent takes too long to decide, the delay itself is a disadvantage (e.g., getting hit by a car).
    *   *Example:* **Taxi Driving**. (Other cars keep moving while you decide to brake).
    *   *Example:* **Real-Time Strategy Games (StarCraft)**.

---

## 5. Discrete vs Continuous

-   **Discrete:** The environment has a finite number of distinct states, percepts, and actions.
    *   *Example:* **Chess**. (Finite number of squares, finite number of pieces, finite number of legal moves).
-   **Continuous:** The states and actions are continuous values (real numbers).
    *   *Example:* **Taxi Driving**. (Speed can be 40.1 km/h or 40.12 km/h; steering angle varies continuously).

---

**Previous:** [← Agent Types](5_Agent_Types.md) | **Next:** [Page Description →](7_PAGE_Description.md)

