# PAGE Description

## What is PAGE?

**PAGE** is an acronym used to define the properties of an agent's task environment:
- **P**: Percepts
- **A**: Actions
- **G**: Goals
- **E**: Environment

---

## The PAGE Framework

### 1. Percepts
The inputs that the agent's sensors can detect at any given moment. 
*Example:* For a taxi driver, percepts include video from cameras, GPS coordinates, and speedometer readings.

### 2. Actions
The possible set of operations the agent can perform.
*Example:* For a taxi driver, actions include steering, braking, accelerating, and signaling.

### 3. Goals
The objectives the agent is trying to achieve.
*Example:* For a taxi driver, goals include reaching the destination safely, minimizing time, and passenger comfort.

### 4. Environment
The external world in which the agent operates.
*Example:* For a taxi driver, the environment includes roads, traffic, pedestrians, and weather conditions.

---

## PAGE Example: Automated Taxi

| Component | Description |
|-----------|-------------|
| **Percepts** | Images, sonar, GPS, speedometer, engine sensors, keyboard |
| **Actions** | Steer, accelerate, brake, signal, speak to passenger |
| **Goals** | Safe, fast, legal, comfortable trip, maximize profits |
| **Environment** | Roads, other traffic, pedestrians, customers |

---

## Difference between PEAS and PAGE

While **PEAS** focuses on the *interface* (Sensors/Actuators) and *performance*, **PAGE** focuses more on the *content* and *context* of the agent's existence (Goals/Environment). Most modern AI textbooks prioritize **PEAS**.

---

**Previous:** [← Environment Properties](06_Environment_Properties.md) | **Next:** [PEAS Description](08_PEAS_Description.md)
