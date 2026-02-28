# PEAS Description

## What is PEAS?

PEAS is a framework for specifying the task environment of an intelligent agent. It helps us design and analyze agents by clearly defining what they need to achieve and how they interact with their environment.

## Components of PEAS

**P - Performance Measure:** How we evaluate the agent's success  
**E - Environment:** The world in which the agent operates  
**A - Actuators:** The agent's means of taking actions  
**S - Sensors:** The agent's means of perceiving the environment

---

## Detailed PEAS Components

### 1. Performance Measure
- Defines the criteria for success
- Quantifies how well the agent is doing
- Must be objective and measurable

**Examples:**
- **Automated Taxi:** Safety, destination reached, profit, legality, passenger comfort
- **Medical Diagnosis System:** Patient health improved, cost efficiency, accuracy of diagnosis
- **Vacuum Cleaner Robot:** Amount of dirt cleaned, time taken, energy consumed, furniture damage avoided

### 2. Environment
- The world in which the agent operates
- Includes all aspects that affect the agent's decisions
- Can be physical or virtual

**Examples:**
- **Automated Taxi:** Roads, traffic, pedestrians, weather conditions, other vehicles
- **Medical Diagnosis System:** Patient, hospital facilities, medical staff, available equipment
- **Vacuum Cleaner Robot:** Rooms, furniture, dirt, obstacles, floor types

### 3. Actuators
- Physical or software components that allow the agent to act
- Enable the agent to affect its environment
- Transform decisions into actions

**Examples:**
- **Automated Taxi:** Steering wheel, accelerator, brake, horn, turn signals, display screen
- **Medical Diagnosis System:** Display screen, tests to order, treatments to prescribe, referrals
- **Vacuum Cleaner Robot:** Left/right wheel motors, vacuum motor, cleaning brushes

### 4. Sensors
- Components that perceive the environment
- Provide information to the agent about the current state
- Input devices for gathering data

**Examples:**
- **Automated Taxi:** Cameras, GPS, speedometer, odometer, engine sensors, accelerometer
- **Medical Diagnosis System:** Keyboard input, patient symptoms, test results, medical history
- **Vacuum Cleaner Robot:** Camera, dirt detection sensor, bump sensors, cliff sensors

---

## Complete PEAS Examples

### Example 1: Chess-Playing Agent
- **Performance:** Win the game, minimize time per move
- **Environment:** Chess board, chess pieces, opponent moves, time clock
- **Actuators:** Move pieces on board, resign button, draw offer
- **Sensors:** Vision system to see board position, clock reading

### Example 2: Internet Shopping Agent
- **Performance:** Price, quality, delivery time, customer satisfaction
- **Environment:** Websites, product databases, vendors, payment systems
- **Actuators:** Display results to user, place orders, send messages, process payments
- **Sensors:** Web pages, user preferences, product databases, reviews

### Example 3: Autonomous Mars Rover
- **Performance:** Scientific data collected, area explored, survival duration, energy efficiency
- **Environment:** Mars surface, rocks, craters, weather, terrain
- **Actuators:** Wheels, robotic arm, camera controls, drill, sample collection tools
- **Sensors:** Cameras, spectrometers, temperature sensors, gyroscope, radiation detector

### Example 4: Part-Picking Robot
- **Performance:** Percentage of parts in correct bins, speed, accuracy
- **Environment:** Conveyor belt with parts, bins for sorting
- **Actuators:** Jointed arm and hand, robotic gripper
- **Sensors:** Camera, joint angle sensors, force sensors

### Example 5: Satellite Image Analysis System
- **Performance:** Correct categorization of images, processing speed
- **Environment:** Satellite images, weather conditions, geographical data
- **Actuators:** Display categorized images, generate reports, alerts
- **Sensors:** Image pixel arrays, metadata, historical data

---

## Importance of PEAS Description

1. **Clear Specification:** Provides a structured way to define agent requirements
2. **Design Guidance:** Helps in designing appropriate agent architecture
3. **Evaluation Framework:** Enables objective assessment of agent performance
4. **Communication Tool:** Facilitates discussion among designers and stakeholders
5. **Completeness Check:** Ensures all aspects of the agent's environment are considered

## Key Considerations

- Performance measures should be **external** (not internal to agent)
- Environment should include **all relevant factors**
- Actuators must be **sufficient** to achieve goals
- Sensors should provide **adequate information** for decision making
- PEAS helps identify whether problems are **solvable** with available resources

---

**Previous:** [← PAGE Description](7_PAGE_Description.md) | **Next:** [Problem Solving Agents →](9_Problem_Solving_Agents.md)
