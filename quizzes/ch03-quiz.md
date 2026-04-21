# Chapter 3 Quiz: From Bits to Qubits — The New Economics of Computation
*Instructor resource — not published in the book.*

---

## Exercise 3.1: Archetype Matching
:label: ex-ch03-archetype-matching

A pharmaceutical research team is in the third month of a quantum drug discovery pilot. They have validated their molecular simulation circuit and now want to run it 500 times per day, five days per week, for the next three months. They have a fixed monthly research budget of \$15,000.

(a) Which pricing archetype is most likely optimal for this workload? Justify your answer.

(b) What additional information would you need to confirm your recommendation?

(c) What is the primary risk of choosing the wrong archetype at this stage?

---

### Solution 3.1

(a) **Pay-per-minute or reserved capacity** is most likely optimal. The team has validated their workload (so the "exploration" phase justifying pay-per-shot or free tier is complete), and the volume — 500 runs × 22 days = 11,000 runs per month — is high and predictable. Pay-per-minute favors dense execution (which VQE-style circuits typically are), while reserved capacity offers the lowest per-run cost if the monthly budget covers the reservation fee.

(b) Additional information needed:
- Circuit execution time per run (to model pay-per-minute costs)
- Whether the runs are batched (affecting queue behavior) or spread throughout the day
- Vendor pricing for both archetypes at current market rates
- Whether the hardware availability SLA on pay-per-minute vs. reserved differs significantly

(c) **Choosing pay-per-shot at this volume would likely exceed the monthly budget** — at high run volumes, per-shot pricing has high marginal cost. Conversely, committing to reserved capacity before validating utilization risks paying for capacity that goes unused if the experiment completes early.

---

## Exercise 3.2: Cost Driver Decomposition
:label: ex-ch03-cost-driver

A quantum circuit runs at depth 80, requires 5,000 shots per experiment for statistical confidence, and experiences a 0.3% two-qubit gate error rate. Each experiment takes 3 hours of queue time. Your researcher rate is \$120/hour. QPU cost is \$0.00002 per shot.

(a) Calculate the error mitigation multiplier assuming you use zero-noise extrapolation requiring 3× the base shots.

(b) Calculate the total cost per experiment (QPU + queue).

(c) Which cost driver contributes most to total cost?

(d) If hardware improves to 0.03% gate error rate, how does the cost-per-useful-result change, assuming the error mitigation multiplier scales proportionally?

---

### Solution 3.2

(a) Error mitigation multiplier = 3× (given — ZNE requires 3× shots)

(b) Cost calculation:
- Effective shots = 5,000 × 3 = 15,000 shots
- QPU cost = 15,000 × \$0.00002 = \$0.30
- Queue cost = 3 hours × \$120 = \$360.00
- **Total = \$360.30 per experiment**

(c) **Queue time** dominates overwhelmingly — \$360 of \$360.30 (99.9%) is queue cost. This illustrates a critical point: for early-stage quantum access, researcher time waiting for hardware is almost always the largest cost driver, not QPU pricing.

(d) If error rate drops 10× (from 0.3% to 0.03%), the error mitigation multiplier may drop proportionally from 3× to perhaps 1.3× (fewer shots needed for equivalent accuracy). New QPU cost = 5,000 × 1.3 × \$0.00002 = \$0.13. Queue cost is unchanged. Total ≈ \$360.13. The improvement in QPU cost is negligible because queue cost dominates. The correct fix is reducing queue time (through tier upgrade or reserved access), not waiting for hardware improvement.

---

## Exercise 3.3: Overhead Ratio Impact
:label: ex-ch03-overhead

A quantum algorithm requires 20 logical qubits to run fault-tolerantly. Current hardware has a physical-to-logical overhead ratio of 1,000:1.

(a) How many physical qubits does the hardware need to support this workload?

(b) If the overhead ratio improves to 100:1, how does the required physical qubit count change?

(c) A vendor announces "100-qubit hardware." Explain, using the overhead framework, why this announcement does not change your answer to part (a).

(d) At what physical qubit count would the 1,000:1 overhead hardware become marginally sufficient for this workload?

---

### Solution 3.3

(a) Physical qubits required = 20 logical × 1,000 = **20,000 physical qubits**

(b) At 100:1 overhead: 20 logical × 100 = **2,000 physical qubits**

(c) A 100-qubit machine at 1,000:1 overhead provides only 100 ÷ 1,000 = 0.1 logical qubits — effectively zero. The announcement of 100 physical qubits does not approach the 20,000-qubit threshold required for this workload. The headline qubit count is irrelevant without the overhead ratio.

(d) Marginally sufficient at **20,000 physical qubits** (exactly 20 logical qubits at 1,000:1). In practice, you would want headroom — perhaps 25,000 physical qubits — to account for qubit connectivity constraints and ancilla qubits used by the error correction code.

---

## Exercise 3.4: Break-Even Construction
:label: ex-ch03-break-even

You are evaluating quantum optimization for a logistics routing problem. Classical optimization costs \$2.50 per problem instance and takes 8 minutes. A quantum QAOA approach would require 50,000 shots per instance at \$0.00003/shot, with an error mitigation multiplier of 2.5×, and an average queue time of 1.5 hours. Your team's hourly cost is \$175.

(a) Calculate the quantum cost per instance.

(b) Calculate the break-even QPU price at which quantum matches classical cost (holding other parameters constant).

(c) The vendor announces a 50% price reduction. Does this change the break-even outcome? Why or why not?

(d) What single operational change would have the largest impact on making quantum competitive for this workload?

---

### Solution 3.4

(a) Quantum cost calculation:
- Effective shots = 50,000 × 2.5 = 125,000
- QPU cost = 125,000 × \$0.00003 = \$3.75
- Queue cost = 1.5 × \$175 = \$262.50
- **Total quantum cost = \$266.25 per instance**
- Classical = \$2.50. Quantum is **106.5× more expensive**.

(b) Break-even QPU price: set QPU cost = Classical cost − Queue cost
= \$2.50 − \$262.50 = −\$260.00
This is negative — the queue cost alone exceeds the classical cost. **No positive QPU price achieves break-even at current queue times.** The workload is not economically viable under these parameters regardless of QPU pricing.

(c) A 50% QPU price reduction changes QPU cost from \$3.75 to \$1.875. Total quantum cost drops to \$264.375. The ratio changes from 106.5× to 105.7×. The improvement is negligible because queue cost (99% of total) is unchanged. The price cut is essentially irrelevant.

(d) **Reducing queue time** is the only lever that matters. If queue time dropped from 1.5 hours to 3 minutes (0.05 hours), queue cost = \$8.75, total quantum = \$12.50 — still 5× classical, but in the same order of magnitude. Reserved-capacity access (which typically eliminates queue time) would be the operational mechanism. This exercise illustrates why archetype selection and operational access tier matter far more than headline shot pricing.
