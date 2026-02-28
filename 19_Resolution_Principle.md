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
By logical deduction (see rough notes):
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

*End of Artificial Intelligence Notes*

---

**Previous:** [← CNF & Unification](18_CNF_and_Unification.md)
