# CNF Conversion & Unification Algorithm

## 1. Converting to Clause Form (CNF)

Clause Form (or Conjunctive Normal Form) is a simplified representation of WFFs that is necessary for the resolution algorithm.

### Steps to Convert:

1.  **Eliminate Implications:** Replace `P → Q` with `¬P ∨ Q` and `P ↔ Q` with `(¬P ∨ Q) ∧ (¬Q ∨ P)`.
2.  **Move Negations Inward:** Use De Morgan's laws and quantifier negation rules:
    - `¬∀x P(x) ≡ ∃x ¬P(x)`
    - `¬∃x P(x) ≡ ∀x ¬P(x)`
3.  **Standardize Variables:** Rename variables so that no two quantifiers use the same name.
4.  **Skolemize:** Replace existential variables (`∃`) with Skolem functions or constants.
    - If no universal quantifier (`∀`) precedes it: Use Skolem constant (e.g., `a`).
    - If inside the scope of `∀y`: Use Skolem function (e.g., `g(y)`).
5.  **Drop Universal Quantifiers:** Move all `∀` to the left and drop them as implicit.
6.  **Distribute Disjunction:** Use `A ∨ (B ∧ C) ≡ (A ∨ B) ∧ (A ∨ C)` to put the matrix into CNF.
7.  **Write as Clauses:** Each conjunct (part connected by `∧`) becomes a separate clause.

### CNF Conversion Worked Example:
**Formula:** `∃n∀y (∀z P(f(n), y, z) → (∃u Q(y, u) ∧ ∃v R(y, v)))`

- **Step 1 (Eliminate Implication):** `∃n∀y (¬∀z P(f(n), y, z) ∨ (∃u Q(y, u) ∧ ∃v R(y, v)))`
- **Step 2 (Negations Inward):** `∃n∀y (∃z ¬P(f(n), y, z) ∨ (∃u Q(y, u) ∧ ∃v R(y, v)))`
- **Step 4 (Skolemize):**
  - `n` → Skolem constant `a`
  - `z` → Skolem function `g(y)`
  - `u` → Skolem function `h(y)`
  - `v` → Skolem function `k(y)`
  Result: `∀y (¬P(f(a), y, g(y)) ∨ (Q(y, h(y)) ∧ R(y, k(y))))`
- **Step 5/6 (Distribute/Clauses):**
  1. `¬P(f(a), y, g(y)) ∨ Q(y, h(y))`
  2. `¬P(f(a), y, g(y)) ∨ R(y, k(y))`

---

## 2. Unification Algorithm

Unification is the process of making two expressions identical by finding a **substitution** for their variables.

### Key Definitions:
- **Substitution:** A set of pairs `{t/v}` where term `t` replaces variable `v`.
- **Unifier:** A substitution that makes expressions identical.
- **Most General Unifier (MGU):** The simplest possible unifier, from which all others can be derived.

### Algorithm Steps:
1.  **Set k=0, σ₀ = empty.**
2.  If all expressions are already identical, **STOP**. σₖ is the MGU.
3.  Find the **disagreement set** (first position where expressions differ).
4.  If there's a variable `v` and term `t` in the disagreement set such that **`v` does not occur in `t`** (the **occur check**):
    - Apply substitution `{t/v}`.
    - Increment `k` and repeat.
5.  Otherwise, **STOP** — not unifiable.

### Worked Example:
Unifying: `S = { P(f(a), g(x)), P(f(a), f(a)) }`
- **Disagreement Set:** `{ g(x), f(a) }`
- **Conclusion:** Neither is a variable that can be substituted for the other. Functions `g` and `f` are different.
- **Result:** **Not unifiable.**

---

**Previous:** [← First-Order Logic](17_First_Order_Predicate_Logic.md) | **Next:** [Resolution Principle →](19_Resolution_Principle.md)
