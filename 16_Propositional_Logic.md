# Propositional Logic (Syntax & Semantics)

## Overview

**Propositional Logic** is the simplest form of logic where we deal with propositions that can either be **true** or **false**. It forms the foundation for more complex logical systems used in AI.

---

## Syntax

Valid statements or sentences in propositional logic are determined according to specific rules.

### Atomic Sentences
**Propositions** are elementary atomic sentences that represent a single fact.
- Example: `P`, `Q`, `R`

### Compound Propositions
Compound propositions are formed from atomic formulas using **logical connectives**:

| Symbol | Meaning | Name |
|--------|---------|------|
| ¬ | not | Negation |
| ∧ | and | Conjunction |
| ∨ | or | Disjunction |
| → | if...then | Implication / Conditional |
| ↔ | if and only if | Biconditional |

### Recursive Definition of Syntax
The syntax of propositional logic is defined recursively:
1. **P** and **Q** are formal formulas (atomic).
2. If **P** and **Q** are formulas, then the following are also formulas:
   - ¬P
   - P ∧ Q
   - P ∨ Q
   - P → Q
   - P ↔ Q
3. All formulas are generated from a **finite number** of the above operations.

---

## Semantics — Interpretation

An **interpretation** for a sentence or a group of sentences is an assignment of a **truth value** to each propositional symbol. This determines the truth value of the entire sentence based on the truth tables of the connectives.

---

## Properties of Statements

- **Satisfiable:** A statement is satisfiable if there is **some** interpretation for which it is true.
- **Contradiction (Unsatisfiable):** A sentence is contradictory if there is **no** interpretation for which it is true.
- **Valid (Tautology):** A sentence is valid if it is **true for every interpretation**.
- **Equivalence:** Two sentences are **equivalent** if they have the **same truth value** under every interpretation.
- **Logical Consequence:** A sentence is a **logical consequence** of another if it is satisfied by all interpretations which satisfy the first.

> [!NOTE]
> A valid statement is always satisfiable, and a contradictory statement is always invalid, but the converse is not necessarily true.

---

## Equivalence Laws

| Law | Formula |
|-----|---------|
| **Idempotence (∨)** | P ∨ P ≡ P |
| **Idempotence (∧)** | P ∧ P ≡ P |
| **Association** | (P ∨ Q) ∨ R ≡ P ∨ (Q ∨ R) |
| **Commutativity** | P ∨ Q ≡ Q ∨ P |
| **Distribution** | P ∧ (Q ∨ R) ≡ (P ∧ Q) ∨ (P ∧ R) |
| **De Morgan's (∨)** | ¬(P ∨ Q) ≡ ¬P ∧ ¬Q |
| **De Morgan's (∧)** | ¬(P ∧ Q) ≡ ¬P ∨ ¬Q |
| **Double Negation** | ¬¬P ≡ P |
| **Conditional** | P → Q ≡ ¬P ∨ Q |
| **Biconditional** | P ↔ Q ≡ (P → Q) ∧ (Q → P) |

---

## Inference Rules

Inference rules are used to make **deductions**. Given a set of sentences **S**, we prove a conclusion **s** (S ⊢ s).

1. **Modus Ponens:** From `P` and `P → Q`, infer `Q`.
2. **Chain Rule:** From `P → Q` and `Q → R`, infer `P → R`.
3. **Substitution:** Consistently replacing propositions in a valid sentence results in a valid sentence.
4. **Simplification:** From `P ∧ Q`, infer `P` (or `Q`).
5. **Conjunction:** From `P` and `Q` separately, infer `P ∧ Q`.
6. **Transposition (Contrapositive):** From `P → Q`, infer `¬Q → ¬P`.

---

**Previous:** [← Minimax & Alpha-Beta](15_Minimax_Alpha_Beta.md) | **Next:** [First-Order Predicate Logic →](17_First_Order_Predicate_Logic.md)
