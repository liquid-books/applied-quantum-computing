# Chapter 2 Quiz: The Quantum Mindset — Thinking in Probabilities
*Instructor resource — not published in the book.*

---

::::{exercise} Superposition Depth Check
:label: ex-superposition-depth

A classical computer must evaluate each candidate solution to an optimization problem sequentially. A quantum algorithm can hold N candidate solutions in superposition simultaneously. If evaluating each candidate takes time T on a classical machine, and a quantum algorithm achieves a quadratic speedup (Grover's algorithm applies):

1. How many time steps does the quantum algorithm require relative to a classical sequential search of N candidates?
2. For N = 1,000,000 candidates, what is the classical search time in units of T, and what is the quantum search time?
3. In a business context, describe one scenario where this quadratic speedup would be commercially meaningful and one where it would not. Justify both.

:::{dropdown} Solution

**Part 1:** Classical sequential search takes O(N) steps on average (N/2 in expectation). Grover's algorithm requires O(√N) oracle queries, achieving a quadratic speedup.

**Part 2:** For N = 1,000,000:
- Classical: ~500,000 steps (N/2 average) in units of T
- Quantum (Grover): ~1,000 steps (√N) in units of T — a 500× improvement

**Part 3:**
- *Commercially meaningful:* Drug molecule screening across a library of one million candidate compounds, where each evaluation is computationally expensive. A 500× speedup translates directly to reduced cloud computing costs and faster time-to-candidate.
- *Not commercially meaningful:* A product recommendation engine with N = 1,000,000 candidate items, where classical approximate-nearest-neighbor algorithms (e.g., FAISS, HNSW) already achieve O(log N) lookup in practice — faster than even Grover's O(√N) for most parameter settings. Quantum advantage depends on the structure of the problem, not just the size.

:::

::::

---

::::{exercise} Entanglement Classification
:label: ex-entanglement-classification

Consider three pairs of variables from a financial model:

**Pair A:** A company's revenue and its headcount — tracked independently, with a historical correlation of 0.72.

**Pair B:** Two tranches of a CDO (collateralized debt obligation) backed by the same pool of mortgages — their default correlation is near zero in normal times but approaches 1.0 during systemic stress events.

**Pair C:** The euro/dollar exchange rate and the price of Brent crude oil — structurally linked through petrodollar flows, with correlations that shift based on geopolitical regime.

1. Which pair best illustrates *entanglement-like* behavior? Explain why using the definition from this chapter.
2. What is the key difference between classical correlation and quantum entanglement that makes this analogy imperfect?
3. What would it mean, practically, to model Pair B in a quantum-entanglement-inspired framework?

:::{dropdown} Solution

**Part 1:** Pair B most closely illustrates entanglement-like behavior. The two CDO tranches backed by the same mortgage pool cannot, in the tail scenario, be treated as independent systems — their joint state under stress is irreducible. This maps onto the entanglement definition: the pair forms a single system under certain conditions, and modeling each element independently produces systematically wrong results precisely when accuracy matters most.

**Part 2:** The key difference is *mathematical structure*. Classical correlation is a property of probability distributions — it describes how two random variables co-vary in expectation. Quantum entanglement is a property of the state space — it means the joint quantum state *cannot be written as a product of individual states*, regardless of the probability interpretation. Entanglement captures a deeper form of non-separability that has no classical analog. The CDO pair is a behavioral analogy to entanglement; it is not quantum entanglement.

**Part 3:** A quantum-entanglement-inspired framework for Pair B would: (1) model the *joint* loss distribution of both tranches as a single inseparable object, rather than correlating two independently modeled distributions; (2) use techniques from quantum information theory — such as matrix product states or tensor network methods — that are designed to represent and manipulate non-separable joint distributions efficiently; (3) focus model calibration on the *tail behavior* of the joint distribution rather than the mean-field correlation. This approach has already been applied in academic research on systemic financial risk.

:::

::::

---

::::{exercise} Decoherence as Strategy
:label: ex-decoherence-strategy

The chapter argues that organizational "premature commitment" is analogous to decoherence: it collapses a distribution of possible strategies to a single path before sufficient information has been gathered.

1. Describe one real or hypothetical business decision where premature commitment was costly.
2. Identify the specific point at which the "measurement" (commitment) was forced — and what environmental factors caused it.
3. Propose a decision-process redesign that would delay the commitment point without creating organizational paralysis.
4. What is the organizational cost of maintaining superposition longer (i.e., keeping more options open)?

:::{dropdown} Solution

**Part 1:** Many organizations made premature technology platform commitments during the early enterprise cloud migration wave (2012–2016) — choosing a single cloud vendor before hybrid and multi-cloud architectures were well understood. Organizations that committed early to single-vendor lock-in often faced significant switching costs and architectural technical debt when requirements evolved.

**Part 2:** The measurement was forced by budget-cycle pressure and procurement timelines — the "environmental factors" being annual planning cycles that required decisions to be finalized before technical uncertainty was resolved. This is organizational decoherence: an external clock (the budget cycle) forcing a collapse of the option space before the quantum (technical) state had evolved to a useful answer.

**Part 3:** A redesigned process might include: (a) structured parallel pilots on two or three platforms through the first annual cycle, deferring vendor selection until real performance data exists; (b) modular architecture design that preserves switching optionality as a first-class requirement; (c) explicit "option preservation" KPIs tracked alongside cost and delivery metrics — making the value of optionality visible rather than invisible.

**Part 4:** The cost of maintaining superposition is real: parallel pilots are more expensive than a single committed path; modular architectures impose design overhead; delayed decisions create organizational anxiety and slow downstream execution. The quantum analogy is precise here — maintaining superposition requires a controlled environment (clear decision rights, ring-fenced budgets for exploration) and a defined commitment trigger (an explicit measurement event). Without those structures, "maintaining optionality" becomes strategic indecision rather than productive uncertainty management.

:::

::::

---

::::{exercise} Quantum Mindset Application
:label: ex-quantum-mindset-application

Choose a domain you are familiar with — healthcare, logistics, financial services, manufacturing, or another field. Identify one specific decision problem that you believe is:

- Currently solved with sequential classical methods (enumeration, simulation, or optimization)
- Potentially amenable to a quantum-native framing (superposition, entanglement, or interference)

Write a 400-word analysis that:
1. Describes the problem precisely — what inputs, what outputs, what constraints
2. Identifies the *bottleneck* in the current classical approach (state-space size, correlation complexity, or signal/noise ratio)
3. Maps the bottleneck to one of the three quantum concepts
4. Argues whether the improvement requires quantum hardware or could be achieved with quantum-inspired classical algorithms
5. Identifies the single most important risk to this analysis

:::{dropdown} Rubric and Sample Response

**Rubric:**
- Problem description is specific and operationally grounded (not vague): 20%
- Bottleneck identification is precise and tied to computational complexity: 20%
- Quantum concept mapping is rigorous, not just metaphorical: 20%
- Hardware vs. quantum-inspired distinction is thoughtful and defensible: 20%
- Risk identification is honest and specific: 20%

**Sample response (healthcare — clinical trial design):**

*Problem:* A Phase II adaptive oncology trial needs to allocate patients across a combinatorial space of drug combinations and dosing regimens (estimated at 8,000+ distinct arms). The trial must maximize the probability of identifying a superior treatment while minimizing patient exposure to inferior regimens. Current sequential adaptive designs drop arms based on interim analyses — but these decisions are irreversible and made under high uncertainty.

*Bottleneck:* The binding constraint is not compute time — it is the information-theoretic cost of early arm elimination. Classical adaptive designs introduce decoherence (premature commitment) because they lack a mechanism for holding multiple treatment hypotheses in superposition across interim analysis points.

*Quantum mapping:* The problem maps to interference. An ideal quantum algorithm would amplify the probability amplitude on the superior treatment arm while suppressing inferior arms — without committing to binary elimination at each interim step. This is Grover-like: progressive signal amplification rather than sequential elimination.

*Hardware vs. quantum-inspired:* The immediate improvement does not require quantum hardware. Quantum-inspired Bayesian adaptive designs — which maintain a full posterior distribution over all arms rather than making hard drops — approximate the interference logic classically. The quantum hardware advantage would become binding when arm counts exceed the horizon where classical posterior maintenance becomes computationally prohibitive (roughly 10,000+ arms with complex joint priors).

*Key risk:* The analysis assumes that the correlation structure between treatment arms is tractable. If genomic subgroup interactions create entangled arm dependencies that cannot be decomposed, the quantum-inspired classical approach may fail in the same way CDO correlation models failed — and genuine quantum entanglement hardware would be required sooner than estimated.

:::

::::
