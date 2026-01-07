# The Future of AI

> "We can see only a short distance ahead, but we can see that much remains to be done." — Alan Turing (1950)

---

## 1. AI Components — Where Progress is Needed

### 1.1 Better Sensors and Actuators

AI is moving from pure software to **embedded robotic systems**. Key trends:
- LIDAR cost: $75,000 → $1,000 (potentially $10/unit by mass production).
- MEMS (micro-electromechanical systems): miniaturized accelerometers, gyroscopes, tiny flying robots.
- 3D bioprinting for prototyping.
- State of robotics today ≈ **personal computers in the early 1980s** — widespread deployment within a decade.

### 1.2 Representing the World

Current AI can recognize objects ("that's a cat") and low-level predicates ("cup is on the table"). **Harder challenges:**
- Recognizing **high-level actions** ("Dr. Russell is having tea while discussing next week's plans").
- Combining **probability + first-order logic** for structured, relational uncertainty.
- Abstract temporal reasoning ("what goes up must come down").

### 1.3 Learning

- **Deep learning** drove the modern AI renaissance (more data from the web + GPU hardware + algorithmic tricks: GANs, batch normalization, dropout, ReLU).
- **Transfer learning**: apply knowledge from one domain to improve performance in a related domain.
- **Predictive / Unsupervised learning** (Yann LeCun): models that predict future states of the world from raw, unannotated data.
- **Differentiable programming** (LeCun): merge general programming languages with machine learning models so the *entire* system can be automatically optimized.
- Geoffrey Hinton (2017): "My view is throw it all away and start again" — the principle of learning by adjusting network parameters endures, but architectures need rethinking.

### 1.4 Computational Resources

| Resource | Trend |
|----------|-------|
| General-purpose CPU | 100,000× speedup since 1970s |
| ML-specific hardware (GPU, TPU, FPGA) | 1,000× faster than CPUs for training |
| Storage cost | $1M/MB in 1969 → $0.02/MB in 2019 |
| Training time (ImageNet) | 1 full day (2014) → 2 minutes (2018) |
| AI publications | Doubled every 2 years on arXiv (2009–2017) |

**Quantum Computing:** Fast quantum algorithms for linear algebra exist, but quantum hardware only handles tens of bits — millions needed for ML. A division of labor (quantum hyperparameter search + classical training) is a future possibility.

---

## 2. AI Architectures

### Symbolic vs. Connectionist:
| Approach | Strength | Weakness |
|----------|----------|----------|
| **Symbolic (Logic/Probabilistic)** | Long chains of reasoning; structured representations | Brittle to noisy data |
| **Connectionist (Neural Networks)** | Pattern recognition in noisy data | Hard to interpret; needs huge data |

The challenge: **combine the two** — probabilistic programming + deep learning.

### Anytime Algorithms:
Algorithms whose **output quality improves gradually over time**, allowing a reasonable decision to be returned at any interruption point.
- Examples: Iterative deepening, MCMC in Bayesian networks.

### Decision-Theoretic Metareasoning:
Applying **information value theory** to decide *which computations to perform* — choosing thinking steps that give the highest expected improvement in decision quality per unit time.

### Bounded Optimality:
Since perfect rationality is computationally impossible, the real goal is to find the **best possible agent program** within a fixed architecture — the *bounded optimal* agent.

---

## 3. Towards General AI (AGI)

**Current AI:** Separate systems for separate tasks (ImageNet, chess, poker, Jeopardy!), each trained from scratch.

**The goal of General AI:** A system that can perform a wide variety of tasks — like a human.

> Alan Turing's list: be kind, learn from experience, use words properly, do something really new...
> Robert Heinlein's list (1973): change a diaper, plan an invasion, cook a meal, write a sonnet, solve equations, fight efficiently...

### Steps Towards AGI:
1. **Multitask models**: Google's machine translation now handles 100 language pairs in one system.
2. **Foundation models** (BERT, GPT): Massive pre-trained models fine-tuned for specific tasks.
3. **Ensemble networks**: Up to 68 billion parameters in a single model.

### Challenges Remaining:
- Common sense reasoning and causal understanding.
- Long-horizon planning (billions of primitive steps for real-world goals).
- Sample efficiency: learning from few examples, not millions.
- Hierarchical Reinforcement Learning for partially observable environments (POMDPs).

---

## 4. AI Engineering as a Mature Discipline

The AI field lacks the **software engineering maturity** of traditional programming:
- **Available tools**: TensorFlow, Keras, PyTorch, CAFFE, Scikit-Learn, SciPy.
- **Problem**: GANs and deep RL are still hard to train — require expert intuition.
- **Vision (Jeff Dean)**: One massive shared model → extract task-specific subsets for each new task.
- **Shared model APIs**: Amazon, Microsoft, Google, IBM offer pre-built ML APIs (vision, speech, translation).

---

## 5. The Big Picture

### AI as a Revolutionary Technology:
AI is similar to printing, plumbing, air travel, and telephony — all made positive impacts but had unintended side effects disproportionately harming disadvantaged groups.

**AI is different in one crucial way:**
> Improving printing/plumbing/telephony to their logical limits cannot threaten human supremacy. **Improving AI to its logical limit certainly could.**

### The Intelligence Explosion (I. J. Good, 1965):
> "Let an ultraintelligent machine be defined as a machine that can far surpass all the intellectual activities of any man however clever. Since the design of machines is one of these intellectual activities, an ultraintelligent machine could design even better machines; there would then be an **intelligence explosion**, and the intelligence of man would be left far behind. Thus the first ultraintelligent machine is the last invention that man need ever make, provided that the machine is docile enough to tell us how to keep it under control."

- **Technological Singularity** (Vernor Vinge): Predicted superhuman AI within 30 years (1993).
- **Ray Kurzweil (2005)**: Singularity by 2045 — "We will gain power over our fates. We will be able to live as long as we want."
- **Counter-argument (Thinkism)**: Progress in physics requires building supercolliders (decades), not just thinking. The "ultraintelligent thinking" part may be the *least* important part of solving hard real-world problems.

### Human-AI Collaboration:
The future is **not AI vs. Humans**, but **AI + Humans**:
- AI co-pilots for programmers, doctors, engineers.
- Personalized AI tutors adapting to each student.
- Personal agents protecting our long-term interests from addictive attention-grabbers.
- Marvin Minsky on robots inheriting Earth: **"Yes, but they will be our children."**
- Eric Brynjolfsson: **"The future is not preordained by machines. It's created by humans."**

---

## 6. Summary of Open Problems in AI

| Problem Area | Key Challenge |
|-------------|---------------|
| Perception | High-level action recognition; combining vision + language |
| Representation | Relational uncertainty; abstract temporal reasoning |
| Learning | Sample efficiency; weakly supervised / unsupervised learning |
| Planning | Long-horizon hierarchical planning; POMDPs at scale |
| Alignment | Specifying what we *really* want; inverse reinforcement learning |
| Architecture | Combining symbolic + connectionist; real-time anytime decision making |
| General AI | Unified multi-task systems; bounded optimal agent programs |

---

**Previous:** [← Ethics & Safety](28_Ethics_and_Safety_of_AI.md) | **Index:** [Back to Introduction](01_Introduction.md)
