# First-Order Predicate Logic (FOPL)

## Overview

**First-Order Predicate Logic (FOPL)** is a more powerful form of logic than Propositional Logic. It allows us to express relationships between objects and use quantifiers to speak about properties of groups of objects.

---

## Formal Systems

A **formal system** consists of:
- **Set of Axioms (S):** Fundamental truths or premises.
- **Set of Inference Rules (L):** Rules from which new statements can be logically derived.

Notation: `⟨S, L⟩ → knowledge base`

### Properties of Inference
- **Soundness:** An inference procedure `L` is sound if every statement derived from `S` using `L` is a **logical consequence** of `S`.
- **Completeness:** An inference procedure `L` is complete if every statement logically implied by `S` can be derived using `L`.

---

## Quantifiers

FOPL uses two primary quantifiers:

| Symbol | Name | Meaning |
|--------|------|---------|
| **∀** | Universal Quantifier | "For all" / "For every" |
| **∃** | Existential Quantifier | "There exists" |

---

## Well-Formed Formulas (WFF)

WFFs are defined **recursively**:
1. Every **atomic formula** is a WFF.
2. If `P` and `Q` are WFFs, then `¬P`, `P ∧ Q`, `P ∨ Q`, `P → Q`, and `P ↔ Q` are also WFFs.
3. If `P(x)` is a WFF, then `∀x P(x)` and `∃x P(x)` are also WFFs.
4. Only WFFs formed by applying the above rules a **finite number of times** are WFFs.

> [!TIP]
> An expression with **no variables** is called a **ground atom**. Two WFFs with the same truth value at every interpretation are **logically equivalent**.

---

## Example: Employee Tax Problem

### Predicates:
- `E(x)`: x is an employee
- `GE(i(x), 1400)`: salary of x ≥ 1400
- `T(x)`: x pays tax
- `i(x)`: salary function of x
- `S(x)`: x is sick
- `P(y)`: y is the president

### Representing Sentences:

1. **"All employees earning $1400 or more per year pay taxes."**
   `∀x [E(x) ∧ GE(i(x), 1400) → T(x)]`

2. **"Some employees are sick."**
   `∃x [E(x) ∧ S(x)]`

3. **"No employee earns more than the president."**
   `∀x∀y [E(x) ∧ P(y) → ¬GE(i(x), i(y))]`

---

**Previous:** [← Propositional Logic](16_Propositional_Logic.md) | **Next:** [CNF & Unification →](18_CNF_and_Unification.md)
