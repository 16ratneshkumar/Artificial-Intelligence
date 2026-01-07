# Resolution Principle & Solved Examples

## 1. Resolution Principle

Resolution is an inference rule used for theorem proving in AI. It works by **contradiction (refutation)**: we show that the negation of our goal leads to an empty clause (□).

### Steps of Resolution:
1.  **Convert to Clause Form (CNF):** Put all axioms into CNF.
2.  **Negate Goal:** Add the negation of the target statement to the clause set.
3.  **Resolve:** Find two clauses with complementary literals (`L` and `¬L`). Create a new clause (the **resolvent**) by combining the remaining literals.
4.  **Repeat:** Continue until an empty clause (`□`) is found or no more resolutions are possible.

---

## 2. Worked Example: Movie Ticket Problem

### Premises:
1. Everyone who sees a movie must buy a ticket. `¬See(x) ∨ Buy(x)`
2. A person who does not have money cannot buy a ticket. `¬Buy(x) ∨ Has(x)`
3. John sees a movie. `See(John)`

### Goal: Show John has money.
- **Negation of Goal:** `¬Has(John)`

### Resolution:
1. Resolve `See(John)` with `¬See(x) ∨ Buy(x)` [x=John] → **`Buy(John)`**
2. Resolve `Buy(John)` with `¬Buy(x) ∨ Has(x)` [x=John] → **`Has(John)`**
3. Resolve `Has(John)` with `¬Has(John)` → **`□` (Empty Clause)**

### Resolution Tree:
```text
    See(John)   ¬See(x) ∨ Buy(x)
       \           /
        \ [x=John]/
         v-------v
         Buy(John)    ¬Buy(x) ∨ Has(x)
             \           /
              \ [x=John]/
               v-------v
               Has(John)   ¬Has(John) (Negated Goal)
                   \           /
                    \         /
                     v-------v
                         □
```

✅ **Proved: John has money.**

---

## 3. Worked Example: Senior Citizens Problem

### Premises:
1. All senior citizens or politicians get air concession.
   - `¬S(x) ∨ G(x)`
   - `¬P(x) ∨ G(x)`
2. Mary is a senior citizen. `S(Mary)`
3. John does not get air concession. `¬G(John)`

### Goal: Show Mary gets air concession.
- **Negation of Goal:** `¬G(Mary)`

### Resolution:
1. Resolve `S(Mary)` with `¬S(x) ∨ G(x)` [x=Mary] → **`G(Mary)`**
2. Resolve `G(Mary)` with `¬G(Mary)` → **`□`**

✅ **Proved: Mary gets air concession.**

---

## 4. Worked Example: Rotary Club Members

### Premises:
1. Mary, Mickey, and John are Rotary Club members. `M(Mary)`, `M(Mickey)`, `M(John)`
2. Members who are not swimmers are mountain climbers. `¬M(x) ∨ Sw(x) ∨ MC(x)`
3. Mountain climbers do not like rain. `¬MC(x) ∨ ¬Likes(x, Rain)`
4. People who dislike water are not swimmers. `Likes(x, Water) ∨ ¬Sw(x)` (contrapositive: `Sw(x) → Likes(x, Water)`)
5. Mickey dislikes whatever Mary likes. `¬Likes(Mary, y) ∨ ¬Likes(Mickey, y)`
6. Mary likes rain and water. `Likes(Mary, Rain)`, `Likes(Mary, Water)`

### Goal: Find a member who is a swimmer but not a mountain climber.
By logical deduction:
- Mary likes Water → **Mary IS a swimmer.**
- Mary likes Rain → **Mary is NOT a mountain climber** (contrapositive of 3).
- Mary IS a member of the Rotary Club (Premise 1).

✅ **Result: Mary is a swimmer and not a mountain climber.**

---

## Summary of Resolution Effectiveness
Logic-based AI systems use the resolution principle because it is:
- **Sound:** Never proves something that isn't true.
- **Refutation Complete:** If a contradiction exists, resolution will eventually find it.

---

## 5. Worked Example: Monkey and Bananas Problem

### Scenario:
A room contains a monkey, a chair, and some bananas hung from the ceiling out of reach. The monkey can reach the bananas if he moves the chair under them and climbs on it.

### Axioms:
1. `dexterous(monkey)`
2. `tall(chair)`
3. `can_move(monkey, chair, bananas)`
4. `can_climb(monkey, chair)`
5. `∀x∀y (dexterous(x) ∧ close(x, y) → can_reach(x, y))`
6. `∀x∀y (get_on(x, y) ∧ under(y, bananas) ∧ tall(y) → close(x, bananas))`
7. `∀x∀y∀z (can_move(x, y, z) → under(y, z))`
8. `∀x∀y (can_climb(x, y) → get_on(x, y))`

### Goal: `can_reach(monkey, bananas)`
- **Negation of Goal:** `¬can_reach(monkey, bananas)`

### Resolution Proof:
1. From Axiom 7 & 3: **`under(chair, bananas)`**
2. From Axiom 8 & 4: **`get_on(monkey, chair)`**
3. From 1, 2, and Axiom 6 & 2: **`close(monkey, bananas)`**
4. From 3, Axiom 1, and Axiom 5: **`can_reach(monkey, bananas)`**
5. Resolve 4 with Negated Goal: **`□`**

✅ **Proved: The monkey can reach the bananas.**

---

## 4. Nondeductive Inference Methods

While resolution and modus ponens are **deductive** (guaranteed to be true if premises are true), common sense reasoning often uses **nondeductive** methods.

### 4.1 Abductive Inference
- **Logic:** Given $P \to Q$ and $Q$ is true, conclude $P$.
- **Purpose:** Finding the most likely explanation for an observation.
- **Example:** "If it rains, the grass is wet. The grass is wet, so it must have rained." (Not necessarily true, but a reasonable guess).

### 4.2 Inductive Inference
- **Logic:** Based on observing recurring patterns.
- **Purpose:** Generalizing from specific instances to a universal rule.
- **Example:** "The first 100 swans I saw were white, so all swans must be white." (The "Inductive Leap").

### 4.3 Analogical Inference
- **Logic:** If Situation A is like Situation B in some respects, they are likely similar in others.
- **Purpose:** Using past experience to solve new, similar problems.
- **Example:** "Solving a 3-variable equation using methods from 2-variable equations."

---

**Previous:** [← CNF & Unification](19_CNF_and_Unification.md) | **Next:** [Structured Knowledge →](21_Structured_KR.md)
