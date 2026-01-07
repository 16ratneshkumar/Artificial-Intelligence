# Structured Knowledge Representation

Structured knowledge representation schemes group related information together to simplify search and inference. Unlike formal logic, which focuses on individual statements, these schemes focus on **objects** and their **relationships**.

---

## 1. Associative Networks (Semantic Nets)

**Associative Networks** represent knowledge as a graph of nodes (concepts) connected by labeled arcs (relationships).

### Core Components:
- **Nodes:** Represent objects, entities, or concepts.
- **Arcs:** Represent relationships between nodes (e.g., `is-a`, `has-part`, `instance-of`).

### Visual Example:
```text
      [ Bird ] --- (can) ---> [ Fly ]
         |
       (is-a)
         |
      [ Sparrow ] --- (eats) ---> [ Seeds ]
         |
      (instance-of)
         |
      [ "Jack" ]
```
*(Jack inherits "Fly" from the Bird node via the inheritance chain)*

### Key Concepts:
- **Inheritance:** Unless specified otherwise, nodes inherit properties from their ancestor nodes (e.g., if "Bird" can "Fly", then "Sparrow" inherits "Fly").
- **Default Inheritance:** Inheriting characteristics unless explicitly overridden.
- **Property Lists:** A common implementation where properties are linked to a single object atom.

---

## 2. Frame Structures

**Frames** are data structures used to represent stereotypical situations or objects. They are similar to "classes" or "records" in programming.

### Frame Components:
- **Slots:** Fields representing specific attributes (e.g., `Color`, `Age`, `Wife`).
- **Facets:** Sub-fields within slots that provide more detail:
  - **Value:** The actual data.
  - **Default:** Used if no value is provided.
  - **If-Needed:** A procedure triggered to calculate a value.
- **Demons (Procedural Attachments):** Procedures activated automatically when a slot is accessed or modified (`if-added`, `if-removed`, `if-needed`).

### Example Frame: Ford Car
```markdown
(Ford
  (AKO (VALUE Car))
  (Color (VALUE Silver))
  (Model (VALUE 4-door))
  (Gas-Mileage (DEFAULT 25))
  (Range (IF-NEEDED Calculate_Range))
)
```

---

## 3. Scripts

**Scripts** represent sequences of commonly occurring events in stereotypical situations, such as eating in a restaurant or shopping.

### Components of a Script:
1.  **Track:** The specific variation of the situation (e.g., "Fast Food" vs. "Fine Dining").
2.  **Roles:** The actors involved (e.g., Customer, Waiter, Cashier).
3.  **Props:** Physical objects used (e.g., Menu, Food, Money, Table).
4.  **Entry Conditions:** Facts that must be true for the script to start.
5.  **Scenes:** Chronological sequences of events (e.g., Entering, Ordering, Eating, Paying).
6.  **Results:** Facts that are true after the script is completed.

---

## 4. Conceptual Dependencies (CD)

**Conceptual Dependency Theory** provides a limited set of primitive actions to represent any natural language statement unambiguously.

### CD Primitives (ACTs):
- **ATRANS:** Transfer of an abstract entity (e.g., giving money).
- **PTRANS:** Physical transfer of an object (e.g., moving a chair).
- **MTRANS:** Transfer of mental information (e.g., telling a story).
- **INGEST:** Taking something into the body (e.g., eating).
- **PROPEL:** Application of physical force (e.g., pushing).
- **MOVE:** Moving a body part.
- **SPEAK:** Emitting a sound.
- **ATTEND:** Focusing attention on an object.

---

## Summary Comparison

| Scheme | Focus | Best For |
| :--- | :--- | :--- |
| **Semantic Nets** | Relationships | Hierarchical knowledge and taxonomies |
| **Frames** | Object properties | Stereotypical objects and entities |
| **Scripts** | Sequences | Stereotypical event sequences and storytelling |
| **CD Theory** | Meaning Primitives | Natural language understanding and semantics |

---

## 5. Production Systems (Rule-Based Systems)

A **Production System** consists of a set of rules (productions) and a control system that decides which rules to apply.

### Components:
1.  **Rule Base (Knowledge Base):** A set of rules in the form `IF (condition) THEN (action)`.
2.  **Working Memory:** A global database of facts representing the current state of the world.
3.  **Inference Engine:** The control mechanism that matches rules against working memory and selects which one to "fire".

### Inference Strategies:
- **Forward Chaining (Data-Driven):** Starts with known facts and applies rules to derive new facts until the goal is reached.
- **Backward Chaining (Goal-Driven):** Starts with the goal and works backward to see if there are facts in working memory that support it.

### Conflict Resolution:
When multiple rules match the working memory, a strategy is needed to pick one:
- **Specificity:** Pick the more specific rule.
- **Recency:** Pick the rule that matches the most recently added facts.
- **Priority:** Use pre-assigned rule weights.

---

**Previous:** [← Resolution Principle](20_Resolution_Principle.md) | **Next:** [Prolog Basics →](22_Prolog_Basics.md)
