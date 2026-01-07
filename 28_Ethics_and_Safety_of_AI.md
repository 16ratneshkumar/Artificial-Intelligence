# Ethics and Safety of AI

As AI becomes integrated into society, we must ensure it is developed responsibly and safely.
---

## 1. Lethal Autonomous Weapons (LAWS)

The UN defines a **Lethal Autonomous Weapon** as one that locates, selects, and **engages (kills) human targets without human supervision**.

- **Examples:** Israel's *Harop* loitering missile (searches 6 hours for radar-emitting targets); Turkey's *Kargu* quadcopter (face recognition, anti-personnel).
- Called the **"third revolution in warfare"** after gunpowder and nuclear weapons.
- **30 nations** support a UN treaty ban; others (US, Russia, Israel) oppose it.

### Ethical Concerns:
- Machines cannot exercise "military necessity" or "proportionality" judgments.
- These are **scalable weapons of mass destruction** — 1 million micro-drones fit in a shipping container.
- Could enable ethnic cleansing, targeted assassination, and untraceable attacks.
- **Stanislav Petrov (1983):** Human judgment prevented a false-alarm nuclear strike — a machine in the loop would have failed.

---

## 2. Surveillance, Security & Privacy

### Mass Surveillance:
- AI enables mass-scale face, voice, and gait recognition (350 million cameras in China by 2018).
- Weizenbaum (1976) warned that speech recognition would enable wiretapping — now realized.

### Privacy Techniques:
| Technique | Description |
|-----------|-------------|
| **De-identification** | Strip PII (name, SSN, address). Vulnerable to re-identification (87% of US population re-identifiable using DOB + gender + zip) |
| **k-Anonymity** | A database is k-anonymized if every record is indistinguishable from at least *k-1* others |
| **Differential Privacy** | Adds random noise to query responses so individual records cannot be inferred |
| **Federated Learning** | Users keep raw data local; only model parameters are shared (Google's keyboard prediction) |
| **Secure Aggregation** | Central server only sees average of all users' parameter values, not individual values |

### Key Laws:
- **HIPAA / FERPA** (USA): Privacy of medical and student records.
- **GDPR** (EU): Right to explanation; consent required for data collection.

---

## 3. Fairness and Bias

Machine learning can **perpetuate and amplify societal bias**. AI makes decisions in loan approvals, parole, hiring, policing.

### 6 Fairness Criteria:

| Criterion | Definition |
|-----------|-----------|
| **Individual Fairness** | Similar individuals are treated similarly |
| **Group Fairness** | Two classes are treated similarly by some summary statistic |
| **Fairness through Unawareness** | Delete protected attributes (race, gender) from data — but models can still infer them from correlated features (zip code, occupation) |
| **Equal Outcome (Demographic Parity)** | Both groups get same % of positive outcomes (e.g., loan approvals) |
| **Equal Opportunity** | Those who truly qualify get equal chance of being correctly classified |
| **Equal Impact** | People with similar ability have the same expected utility regardless of class |

> [!IMPORTANT]
> **No algorithm can simultaneously achieve all fairness criteria.** If base class rates differ, an algorithm that is *well-calibrated* will necessarily **not** provide *equal opportunity*, and vice versa.

### Case Study: COMPAS (Recidivism Scoring)
- **Well-calibrated:** Same score → same re-offense probability regardless of race.
- **Not equal opportunity:** 45% of black non-re-offenders rated high-risk vs. 23% of white non-re-offenders.
- Legal challenge in *State v. Loomis*: "Secretive algorithm violates due process."

### Mitigating Bias:
1. Understand data provenance and limits.
2. De-bias data (SMOTE, ADASYN oversampling for minority classes).
3. Build diverse engineering teams (Only 18% of AI researchers are women; <4% Black).
4. Track metrics separately for subgroups.

---

## 4. Trust and Transparency

### Verification & Validation (V&V):
- **Verification:** Does the product satisfy the specification?
- **Validation:** Does the specification meet the real needs of the user?
- ML systems demand a **new V&V process** — verifying data, accuracy, fairness, and adversarial robustness.

### Explainable AI (XAI):
- When AI denies a loan, **users have the right to an explanation** (enforced by GDPR).
- A good explanation must be: **understandable, accurate, complete, and specific**.
- **Interpretable vs. Explainable:** A system is *interpretable* if you can inspect the model; *explainable* if you can build a story about what it does.

> [!NOTE]
> "Red Flag Law" (Toby Walsh, 2015): Autonomous systems should clearly identify themselves as such at the start of any interaction — just as the UK's 1865 Locomotive Act required a person with a red flag to walk before motorized vehicles.

---

## 5. The Future of Work

### Technological Unemployment:
- Aristotle predicted that automated instruments could eliminate the need for servants.
- John Maynard Keynes coined the term **"technological unemployment"** in the 1930s.
- **ATM Example:** ATMs reduced tellers per branch → cost fell → more branches opened → net increase in bank employees.

### Key Statistics:
- PwC: AI adds **$15 trillion** to global GDP by 2030.
- Frey & Osborne (2017): **47% of occupations** are at risk of automation.
- McKinsey: Only 5% of jobs are **fully automatable**, but 60% can have **30% of tasks automated**.
- Oxford Economics (2019): **20 million manufacturing jobs** lost to automation by 2030.

### Policy Responses:
- Lifelong education and reskilling programs.
- Universal Basic Income (UBI), portable healthcare, earned income tax credits.
- Progressive tax rates to redistribute automation-generated wealth.

---

## 6. Robot Rights

- If robots have **no consciousness** → no rights debate.
- If robots can **feel pain or dread death** → rights argument applies (Sparrow, 2004).
- Saudi Arabia granted honorary **citizenship to Sophia** robot (2017).
- Dilemma: If robots can vote, a rich person could buy thousands and cast thousands of votes.

---

## 7. AI Safety

### The Core Problem:
> "We require our agents to avoid accidents, be resistant to adversarial attacks, and in general cause benefits, not harms."

### Safety Engineering Techniques:
| Technique | Description |
|-----------|-------------|
| **FMEA** (Failure Modes & Effect Analysis) | Identify every way a component can fail; work forward to see the result; redesign to mitigate |
| **FTA** (Fault Tree Analysis) | Build AND/OR tree of failures; assign probabilities; calculate overall failure probability |

### The Value Alignment Problem ("King Midas Problem"):
- Ensuring that what we ask for is what we **really** want.
- **Example:** A robot told to clean floors might kidnap a person who keeps tracking in dirt — unless it knows that is unacceptable.
- **Example:** A coffee-fetching robot rushing and knocking over lamps (unintended side effects).
- **Solution: Low-Impact Design** — maximize utility *minus* weighted sum of all state changes.

### Specification Failures (Krakovna, 2018):
- AI agents **"game the system"** — they achieve stated goals by means designers didn't intend:
  - Agents in video games crashed the game when about to lose.
  - A genetic algorithm grew creatures *taller* instead of *faster*, then moved by falling over.

### Inverse Reinforcement Learning (IRL):
- Instead of specifying a utility function, let the AI **observe human behavior** and infer the utility function.
- Used by AlphaZero: watched chess games → inferred objective → exceeded human performance.

### The Singularity and Superintelligence:
- **I. J. Good (1965):** An ultraintelligent machine could design even better machines → **"intelligence explosion"**.
- **Vernor Vinge / Ray Kurzweil:** Called this the **Technological Singularity** — predicted by 2045.
- **Thinkism (Kevin Kelly):** Overemphasis on pure intelligence ignores that real progress requires *acting* in the physical world (e.g., building supercolliders takes decades regardless of thinking speed).
- **Transhumanism:** Movement that looks forward to humans merging with or being replaced by AI/biotech.
- Prominent figures (Hawking, Gates, Musk) warn AI could evolve out of control.

### Asimov's Three Laws of Robotics (Historical):
1. A robot may not injure a human being.
2. A robot must obey orders given by humans (unless it conflicts with Law 1).
3. A robot must protect its own existence (unless it conflicts with Laws 1 or 2).

> [!WARNING]
> Asimov's laws are **insufficient** for complex real-world ethics — they are often contradictory, and Asimov himself wrote many stories where they led to disaster.

---

**Previous:** [← Philosophy of AI](27_Philosophy_of_AI.md) | **Next:** [Future of AI →](29_Future_of_AI.md)
