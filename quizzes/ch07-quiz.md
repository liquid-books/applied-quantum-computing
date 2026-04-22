# Chapter 7 Quiz: The Simulation Revolution — Drugs, Materials, and Climate

> **Instructor Use Only** — Not included in the published book TOC.

---

## Exercise 1: Conceptual — The Exponential Wall

**Question:**

A classical computer attempting to simulate a 50-electron molecule using full configuration interaction (FCI) — the exact method — would need to track approximately 2⁵⁰ states simultaneously. Explain why this represents a fundamental, not merely practical, barrier to classical molecular simulation. In your answer:

(a) Define what "exponential scaling" means in this context and why it cannot be solved by buying more powerful hardware.

(b) Explain how quantum computers circumvent this barrier — specifically, what property of quantum hardware allows it to represent exponentially many states with a polynomial number of qubits.

(c) Identify one limitation of the quantum approach: what can go wrong when a quantum computer attempts to simulate a 50-electron molecule on today's NISQ hardware?

**Answer Key:**

(a) Exponential scaling means the computational cost doubles with every additional electron. For 50 electrons: 2⁵⁰ ≈ 10¹⁵ states. The world's most powerful supercomputer (approximately 10¹⁸ floating-point operations per second) would require millions of years for a full simulation. Buying faster hardware does not change the exponent — it only shifts the threshold molecule size by a few electrons. This is a mathematical wall, not an engineering one.

(b) Quantum computers exploit **quantum superposition**: n qubits can exist in a superposition of 2ⁿ states simultaneously. A 50-qubit quantum register natively represents 2⁵⁰ states without requiring 2⁵⁰ memory locations. The quantum state is not stored classically — it *is* the quantum hardware. This is why the complexity scales polynomially (number of qubits, number of gates) rather than exponentially (classical memory).

(c) NISQ hardware has gate error rates of 0.1–1%, meaning each quantum gate operation has a small probability of introducing an error. For circuits with thousands of gates (required for 50-electron molecules), errors accumulate and corrupt the calculation. Current VQE on NISQ hardware is limited to molecules tractable in shallow circuits — typically 4–20 qubits (electrons). Mitigating this requires error correction, which requires thousands of physical qubits per logical qubit — hardware that does not yet exist at scale.

---

## Exercise 2: Application — VQE Economics

**Question:**

Pfizer has a drug candidate in Phase II clinical trials projected to generate \$1.2 billion per year at peak if approved. Current development timeline is 4 years to approval (assuming success). Pfizer's cost of capital is 10%. A quantum simulation vendor offers a service claiming to improve computational chemistry accuracy enough to reduce clinical failure risk — specifically, catching an estimated 30% of Phase II failures in preclinical stage. Pfizer's Phase II failure rate is 50%.

(a) What is the current expected NPV of the drug, assuming 50% Phase II success, 85% Phase III success, and a peak-revenue terminal value of \$1.2B/year at 10x earnings?

(b) The vendor's service costs \$30 million and would increase Phase II success to 65% (by catching failures earlier). Does this pass a positive NPV test? Show your calculation.

(c) A second vendor offers a timeline acceleration service: guaranteed 18-month acceleration to approval with 80% probability for \$50 million. Calculate the risk-adjusted NPV of this alternative investment. Which is the better investment, and why?

**Answer Key:**

(a) Base case NPV:
- Probability of approval = 0.50 × 0.85 = 0.425
- Terminal value = \$1.2B × 10 = \$12B
- Revenue stream discounted over 4 years: PV of \$1.2B/year starting in Year 5, discounted at 10%: ≈ \$12B × (1/1.10⁴) ≈ \$8.2B × 0.425 ≈ \$3.5B expected NPV (simplified; students should show DCF structure)

(b) With improved Phase II success (65%):
- New probability of approval = 0.65 × 0.85 = 0.553
- New expected NPV ≈ \$8.2B × 0.553 ≈ \$4.5B
- NPV improvement = \$4.5B − \$3.5B = \$1.0B
- Cost = \$30M
- Net benefit ≈ \$970M → **strongly positive NPV test**

(c) Timeline acceleration (18 months = 1.5 years, 80% probability):
- NPV of 1.5-year acceleration on \$1.2B/year at 10% discount: ≈ \$1.2B × 1.5 / 1.10¹·⁵ ≈ \$1.63B benefit
- Risk-adjusted: 0.80 × \$1.63B × 0.425 (base approval probability) ≈ \$554M
- Cost = \$50M → Net ≈ \$504M
- **Vendor 1 (failure avoidance) creates more value (\$970M net) than Vendor 2 (timeline acceleration, \$504M net)** under these assumptions, primarily because improving success probability multiplies across all downstream revenue. Students should recognize the sensitivity to the Phase II failure-catch assumption.

---

## Exercise 3: Analysis — The Boehringer Ingelheim Partnership Structure

**Question:**

Boehringer Ingelheim structured its quantum chemistry partnership with Google Quantum AI around milestone-based deliverables, parallel classical benchmarking, and internal capability building — rather than simply paying for quantum computing access.

(a) Explain the **optionality logic** behind this structure. Specifically: what value does the partnership create if quantum simulation *does not* reach pharmaceutical scale within the partnership timeline?

(b) The partnership produced published methodological advances in VQE error mitigation. These publications benefit all competitors equally — there is no IP protection for published methods. From a competitive strategy perspective, why would Boehringer choose to publish rather than keep the results proprietary?

(c) Critics argue that pharmaceutical companies investing in quantum simulation today are making a "premature" bet — that the hardware is not ready and the investment would generate higher returns elsewhere. Construct a three-sentence rebuttal using the concept of **path dependency** in technology adoption.

**Answer Key:**

(a) Optionality value: (1) the partnership builds a team of quantum chemistry experts who will be ready to apply the technology when hardware scales — hiring and training this expertise after the technology matures would be more expensive and slower; (2) the published benchmarks establish the company as a credible scientific partner, enabling better terms in future partnerships; (3) the parallel classical benchmarking improved Boehringer's classical computational chemistry methods regardless of quantum outcomes — a direct R&D return independent of quantum advancement.

(b) Publishing creates **scientific reputation capital** that attracts top talent (quantum researchers want to work where science gets published), generates positive collaborator relationships (Google has incentives to continue and deepen the partnership with a credible publishing partner), and positions Boehringer as a field leader — affecting how regulators, partners, and investors perceive the company's scientific rigor. The competitive moat is not the method but the *people who know how to apply it* and the *experimental data that validates it against real drug chemistry problems* — both of which Boehringer retains.

(c) Path dependency rebuttal: Technology platforms reward early adopters not just with first-mover product advantage but with **compounding organizational learning** — the companies that ran early VQE calculations in 2022 understand the algorithm's failure modes, accuracy thresholds, and vendor landscape in ways that newcomers in 2028 will have to relearn expensively. Waiting for hardware maturity before investing is equivalent to waiting for the internet to be "proven" before building e-commerce capabilities — the window for cheap option acquisition closes long before the value becomes obvious. The cost of a \$25-50M quantum chemistry program today is one phase of clinical trials; the cost of **not** having the expertise when fault-tolerant hardware arrives is an entire drug discovery cycle.

---

## Exercise 4: Strategic — Nitrogen Fixation and Option Value

**Question:**

The Haber-Bosch process currently consumes approximately 1-2% of global energy production and emits an estimated 450 million tons of CO₂ annually. Quantum simulation of nitrogenase (specifically the FeMoco active site) is a stated research goal of IBM, Google, and Microsoft — with estimated hardware requirements of 100-200 logical qubits with error rates below 0.1%.

(a) Current best estimates suggest that fault-tolerant quantum computers with 100+ logical qubits are 8-12 years away. Using a 10% discount rate, calculate the **present value** of a \$500 billion energy market disruption (representing 30% of the addressable market in synthetic ammonia, carbon offset credits, and agricultural efficiency) discounted over 10 years.

(b) The same \$500 billion market disruption could be achieved — perhaps — through classical AI-driven materials discovery, protein structure prediction advances (e.g., AlphaFold for enzyme engineering), or directed evolution of nitrogen-fixing organisms. Identify two **substitution risks** that could reduce the option value of quantum simulation for nitrogen fixation, and explain how a company should account for these in its quantum R&D investment thesis.

(c) Microsoft has invested heavily in topological qubits specifically because they promise lower error rates at smaller physical footprints — potentially reaching the 100-logical-qubit threshold years before superconducting or trapped-ion competitors. From an investment perspective, why might this hardware-architecture bet be more valuable for quantum simulation than for quantum optimization or cryptography?

**Answer Key:**

(a) PV = \$500B / (1.10)¹⁰ = \$500B / 2.59 ≈ **\$193 billion** present value. With 20% probability of quantum simulation being the enabling technology (accounting for competition from classical AI): risk-adjusted PV ≈ \$38.6 billion. Even a 1% position in this outcome space (through IP, partnerships, or service contracts) is worth hundreds of millions — justifying significant R&D investment.

(b) **Substitution Risk 1: AlphaFold / enzyme engineering.** If protein structure prediction advances can accurately model the FeMoco active site well enough for directed evolution approaches — engineering bacteria with enhanced nitrogenase efficiency — the quantum simulation advantage may arrive too late. Companies should track *publication velocity* in computational enzyme engineering alongside quantum hardware milestones. **Substitution Risk 2: Classical AI for catalyst discovery.** Graph neural network approaches (e.g., GNoME by DeepMind) have already identified thousands of novel stable materials. If classical AI can screen nitrogen-reduction catalysts empirically fast enough, the need for quantum simulation of the exact reaction mechanism may be bypassed. Investment thesis adjustment: quantum simulation for nitrogen fixation has highest option value in scenarios where *mechanistic accuracy* (not empirical screening) is the bottleneck — companies should fund research to determine which constraint is binding.

(c) Quantum simulation (specifically VQE and quantum phase estimation for electronic structure) requires circuit depths that grow with molecular accuracy requirements. Error rates are the binding constraint — every gate error shifts the energy estimate. Lower error rates directly translate to larger, more accurate molecular simulations. For quantum optimization, approximate solutions are often acceptable (the optimization landscape is forgiving). For post-quantum cryptography, errors are catastrophic but the required circuit depth is fixed. For molecular simulation, **the accuracy-error rate trade-off is fundamental** — making Microsoft's topological qubit bet (which specifically targets error rate reduction) the most strategically valuable for chemistry applications, even if it achieves similar qubit counts to competitors later.

---

*End of Chapter 7 Quiz — Answer Key Included*
