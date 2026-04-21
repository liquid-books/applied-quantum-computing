# Chapter 4 Quiz — The Quantum Hardware Race
## Instructor Use Only — Not in Public TOC

---

## Exercise 1: Modality Comparison (Conceptual)

**Question:** A pharmaceutical company needs to run a quantum chemistry simulation that requires 500 two-qubit gate operations with an overall circuit fidelity above 90%. Based on the chapter's metrics framework:

a) Which hardware modality is most likely to meet this requirement today? Justify your answer using specific metric thresholds.

b) Which modality would be least suitable for this workload, and why?

c) At what two-qubit gate fidelity threshold does (0.999)^500 drop below 90%? Show your calculation.

### Answer Key

**Part a)** Trapped-ion (IonQ/Quantinuum). At 99.9% two-qubit gate fidelity, cumulative fidelity over 500 gates = (0.999)^500 ≈ 60.6%. At 99.95% fidelity = (0.9995)^500 ≈ 77.8%. At 99.99% = (0.9999)^500 ≈ 95.1%. Trapped-ion systems are the only modality that has demonstrated 99.9%+ average two-qubit fidelity in published work (Quantinuum H2). No other modality consistently exceeds 99.5% system-average.

**Part b)** Topological qubits — not commercially available; still in experimental validation. Second: photonic (measurement-based model makes direct gate count comparison non-trivial; current photonic systems are small and have significant gate losses).

**Part c)** Need (f)^500 > 0.90. Taking ln: 500 × ln(f) > ln(0.90). ln(f) > -0.0002107. f > e^(-0.0002107) ≈ 0.99979. So the fidelity threshold is approximately **99.979%** per gate. Below that, 500 gates cannot maintain 90% circuit fidelity.

---

## Exercise 2: Roadmap Evaluation (Applied)

**Question:** Read the following vendor announcement and apply the chapter's roadmap rubric. Identify every claim, classify it as Green/Yellow/Red, and explain your reasoning.

*"QuantaCorp today announced its QC-5000 processor featuring 5,000 qubits — a 10× increase from its previous system. In internal testing, the system demonstrated quantum advantage on a supply chain optimization benchmark, completing in 3 minutes what classical supercomputers require 14 days to solve. QuantaCorp plans to offer cloud access to the QC-5000 by Q2 next year and has a roadmap to achieve a 10,000-qubit system with full error correction by 2027. The QC-5000 marks a turning point for practical quantum computing."*

### Answer Key

| Claim | Color | Reasoning |
|-------|-------|-----------|
| 5,000 qubits | 🟡 Yellow | Qubit count without fidelity. How many are usable? What is system-average 2Q error rate? Need this to evaluate. |
| 10× increase from previous | 🟡 Yellow | Scaling qubit count is less meaningful than scaling quality. What happened to fidelity? |
| "Internal testing" advantage | 🔴 Red | "Quantum advantage" without: (1) independent verification, (2) specified classical baseline (which supercomputer? what algorithm?), (3) peer review. Classic "demo trap." |
| "3 minutes vs 14 days" | 🔴 Red | No methodology, no baseline specification. "14 days on a classical supercomputer" — which one? What algorithm? What problem size? |
| Cloud access Q2 next year | 🟡 Yellow | 6-12 month horizon — moderately credible if infrastructure is built. Watch for delivery. |
| 10,000 qubit with "full error correction" by 2027 | 🔴 Red | "Full error correction" is a massive, unqualified claim. Surface code at scale requires millions of physical qubits or dramatically better fidelity than any demonstrated system. 2027 timeline is implausible for this milestone. |

**Overall assessment:** This roadmap is dominated by Red and Yellow flags. The "quantum advantage" claim without methodology is a textbook demo trap. The 2027 fault-tolerance claim is inconsistent with the current state of the field. An analyst should: (1) request the full technical paper for the supply chain benchmark, (2) ask for system-average 2Q fidelity on the QC-5000, and (3) apply heavy discount to the 2027 projection.

---

## Exercise 3: Portfolio Design (Strategic)

**Question:** A mid-sized insurance company (\$50B AUM) wants to explore quantum computing for catastrophic risk modeling and fraud detection. Their CTO has a 5-year horizon and a total quantum budget of \$10 million.

a) Design a portfolio allocation across the five modalities. Specify dollar amounts and investment types (service contract, private placement, public equity, internal R&D).

b) Write kill-switch criteria for your two largest positions.

c) What single technical milestone in the next 18 months would cause you to materially increase your investment? What would cause you to exit all positions?

### Answer Key (Sample — Multiple Valid Responses)

**Part a) Sample Allocation:**
- Superconducting (IBM Quantum Network) — \$2M, service contract. Rationale: most mature ecosystem, best algorithm development environment, risk modeling algorithms exist on QAOA.
- Trapped-Ion (Quantinuum cloud + research partnership) — \$3M over 5 years. Rationale: highest fidelity for actuarial simulation circuits; Quantinuum has pharmaceutical contracts suggesting chemistry simulation maturity applicable to molecular risk modeling.
- Neutral-Atom (QuEra early access) — \$1.5M. Rationale: monitoring position on fastest-evolving modality; combinatorial optimization for fraud detection network analysis.
- Photonic (PsiQuantum ecosystem program) — \$1M. Rationale: option value on manufacturing scale thesis; low near-term utility expectation.
- Internal R&D / Talent — \$2.5M. Rationale: quantum algorithm development team, regardless of modality winner.

**Part b) Kill-Switch Criteria:**
- Trapped-Ion position: "If Quantinuum does not demonstrate 50-qubit system with >99.9% average 2Q fidelity by Q4 2026, reduce service contract by 50% at next annual review."
- Superconducting position: "If IBM Quantum does not provide access to a system with >100 algorithmic qubits (#AQ or equivalent) by Q2 2026, reduce to monitoring-only tier."

**Part c):**
- Increase trigger: Any platform demonstrating a 100+ logical qubit error-corrected system in peer-reviewed publication. This milestone, if achieved, compresses the timeline to commercially useful fault-tolerant computation by years.
- Exit trigger: "If no modality demonstrates a quantum circuit with commercial-value output on an insurance-relevant benchmark (actuarial tables, CAT bond pricing, fraud graph analysis) by 2028, exit all hardware service contracts and focus budget entirely on talent/algorithm readiness for the fault-tolerant era."

---

## Exercise 4: Concept Application (Calculation + Analysis)

**Question:**

a) A superconducting system has T₂ = 200 μs and a 2Q gate time of 400 ns. What is the maximum theoretical circuit depth (number of 2Q gate layers) before decoherence destroys the computation?

b) A trapped-ion system has T₂ = 1 second and a 2Q gate time of 200 μs. Calculate the same maximum circuit depth.

c) Despite having ~5,000× longer coherence time, why might the trapped-ion system not provide 5,000× better performance on all real workloads?

d) For a quantum chemistry simulation requiring 10,000 two-qubit gate layers, which system (if either) is adequate, and what would need to change to make the other system viable?

### Answer Key

**Part a)** Superconducting max depth = T₂ / gate_time = 200 μs / 0.4 μs = **500 gate layers**

**Part b)** Trapped-ion max depth = 1,000,000 μs / 200 μs = **5,000 gate layers**

**Part c)** Multiple reasons:
1. Gate fidelity: even within coherence time, cumulative errors accumulate. A 200-layer circuit at 99.5% fidelity = (0.995)^200 = 36.8% success probability. Coherence time is necessary but not sufficient.
2. Total wall-clock time: 5,000 × 200 μs = 1 second per "circuit" on trapped-ion vs. 500 × 0.4 μs = 0.2 ms on superconducting. For real-time applications needing sub-second answers, trapped-ion's depth advantage is irrelevant.
3. Parallelism: superconducting systems can apply gates to many qubit pairs simultaneously; small trapped-ion chains often require serial operations.
4. Connectivity: trapped-ion all-to-all is powerful but doesn't always compensate for serial execution in practice.

**Part d)** Neither system is currently adequate for 10,000 gate layers without error correction.
- Superconducting: max ~500 layers (no error correction); needs ~20× improvement in coherence time OR error correction overhead reduction
- Trapped-ion: max ~5,000 layers; also insufficient, but closer; needs ~2× coherence improvement OR must use error correction
- **The key insight:** 10,000 gate layers requires either (a) fault-tolerant error correction with logical qubits, or (b) dramatic physical improvements. This is why fault tolerance is the critical milestone for commercially relevant quantum chemistry simulation.
