---
title: "Appendix C: Vendor-Neutral Hardware Evaluation Rubric"
subtitle: "A reproducible framework for evaluating any quantum hardware vendor, now or in 2031"
short_title: "Appendix C: Evaluation Rubric"
description: "A standalone, printable rubric for evaluating quantum hardware vendors and backends on seven objective, vendor-neutral criteria. Includes scoring worksheet, workload-modality matching guide, and red flags checklist."
label: appendix-c-evaluation-rubric
tags: [vendor evaluation, hardware rubric, quantum hardware, due diligence, procurement]
---

# Appendix C: Vendor-Neutral Hardware Evaluation Rubric

## Section 1: How to Use This Rubric

This rubric exists because the quantum hardware landscape changes faster than any book can be updated. Vendor leaderboards shift quarterly. New modalities emerge. Companies pivot, merge, or quietly stop publishing calibration data. What does not change are the fundamental properties that determine whether a quantum backend is actually useful for your workload.

The seven criteria in this rubric have been selected precisely because they are **modality-agnostic and evergreen**. They apply equally to superconducting systems from IBM or Google, trapped-ion systems from IonQ or Quantinuum, photonic systems from PsiQuantum or Xanadu, and any future modality that does not yet have a name. When you evaluate a vendor in 2028, you will use the same seven questions. The answers will be different. The questions will not.

### Demonstrated Today vs. Promised/Roadmapped

The single most important discipline in vendor evaluation is maintaining a hard line between what a vendor **has demonstrated** and what they **claim they will deliver**. This rubric scores only demonstrated, verifiable performance. Roadmap commitments belong in a separate risk register, not in a hardware score.

> **A vendor's roadmap is a marketing document until milestones are published with qualification criteria and verified by independent parties.**

When a vendor presents a roadmap slide, ask: *Which of these milestones have already been hit? What were the qualification criteria? Where is the peer-reviewed data?* Score only the milestones that have been crossed.

### How to Weight Criteria for Your Workload

Not all workloads care equally about all seven dimensions. A near-term variational algorithm tolerates lower qubit counts but demands high gate fidelity. A production integration cares intensely about queue time. A long-horizon fault-tolerant investment cares most about roadmap credibility and coherence time trajectory.

The scoring worksheet in Section 3 includes a **Weight** column. Before filling in vendor scores, assign weights first — this prevents vendor presentations from anchoring your priorities. Recommended starting weights by workload type are provided in Section 4.

### How to Conduct the Evaluation

1. Assign weights to each dimension before speaking to any vendor.
2. Score each dimension independently using only **demonstrated, published data**.
3. Flag any score that relies on vendor-provided-only data (not independently verified).
4. Calculate weighted composite scores.
5. Run the Red Flags Checklist (Section 5) as a final gate — a single red flag should trigger additional scrutiny.

---

## Section 2: The Evaluation Criteria

### Dimension 1: Coherence Time (T1/T2)

**Definition:** Coherence time measures how long a qubit maintains its quantum state before environmental noise causes it to decohere. T1 (energy relaxation time) measures how long a qubit stays in an excited state. T2 (dephasing time) measures how long a qubit maintains phase coherence. Both are measured in microseconds (μs) or milliseconds (ms) for leading systems.

**Why It Matters:** Every quantum gate takes time to execute. If your circuit requires 1,000 two-qubit gates and each gate takes 200 ns, your circuit needs roughly 200 μs of coherent operation time — just for the gate operations, before factoring in measurement and reset. If T2 is 100 μs, your circuit will fail before it finishes. Coherence time sets a hard ceiling on circuit depth.

**How to Measure/Find It:** Backend calibration data is the authoritative source. IBM Quantum publishes T1 and T2 per qubit in real time through their backend properties API. IonQ publishes average coherence times in their hardware specification sheets. For any vendor, ask specifically for per-qubit calibration data, not just a headline average — variance across qubits matters as much as the mean.

**Scoring Guide (1–5):**

| Score | T1/T2 Benchmark |
|:-----:|:----------------|
| 1 | T2 \< 50 μs — severely limits circuit depth; suitable only for very shallow circuits |
| 2 | T2 50–200 μs — limited but usable for near-term NISQ algorithms with careful optimization |
| 3 | T2 200 μs–1 ms — solid for current NISQ workloads; adequate for most variational algorithms |
| 4 | T2 1–100 ms — excellent; enables deeper circuits; competitive with leading systems today |
| 5 | T2 \> 100 ms or demonstrated qubit lifetimes measured in seconds (trapped-ion class) |

---

### Dimension 2: Gate Fidelity (1Q and 2Q)

**Definition:** Gate fidelity measures the accuracy of a quantum operation — the probability that a gate performs exactly the intended transformation. Expressed as a percentage, where 100% is perfect and any deviation represents error. Single-qubit (1Q) gate fidelity and two-qubit (2Q) gate fidelity are reported separately; 2Q fidelity is almost always lower and is the critical number.

**Why It Matters:** Errors accumulate multiplicatively across gate operations. A circuit with 100 two-qubit gates at 99% fidelity per gate has a cumulative success probability of roughly 36%. At 95% fidelity, that same circuit succeeds only 0.6% of the time. Gate fidelity directly determines the maximum useful circuit depth, which determines what problems you can actually solve.

**How to Measure/Find It:** Look for **randomized benchmarking (RB)** or **cross-entropy benchmarking (XEB)** results, not raw Hamiltonian simulation numbers. RB is the industry standard for single-qubit gates. For two-qubit gates, ask for native gate fidelity (e.g., CNOT or CZ or Mølmer–Sørensen gate). For any published number, ask: *What benchmarking protocol was used? Is there a peer-reviewed paper?*

**Scoring Guide (1–5):**

| Score | 2Q Gate Fidelity |
|:-----:|:----------------|
| 1 | \< 90% — error rate too high for meaningful multi-qubit computation |
| 2 | 90–95% — marginal; suitable only for very short circuits or error mitigation research |
| 3 | 95–98% — acceptable for near-term NISQ work with error mitigation techniques |
| 4 | 98–99.5% — strong; enables meaningful variational circuits and small-scale algorithms |
| 5 | \> 99.5% — fault-tolerant-class fidelity; approaching thresholds for logical qubit encoding |

:::{tip}
**The 99% Threshold:** The fault-tolerance threshold for surface codes is approximately 99% two-qubit gate fidelity. Systems above this threshold are candidates for logical qubit demonstrations. Systems below it are NISQ-class regardless of their qubit count.
:::

---

### Dimension 3: Qubit Count (Physical)

**Definition:** The total number of physical qubits available on the hardware backend.

**Why It Matters — With an Important Caveat:** Raw qubit count is the most-marketed number in quantum computing and the least informative for workload planning. A system with 1,000 noisy, weakly connected qubits may be less useful than a system with 50 high-fidelity, densely connected qubits for the same workload. Physical qubit count matters only in the context of fidelity and connectivity.

**The Logical Qubit Reality:** For fault-tolerant quantum computing, the relevant number is **logical qubits** — error-corrected qubits formed from many physical qubits. Current estimates require roughly 1,000 physical qubits to encode a single high-quality logical qubit using surface codes. A system with 1,000 physical qubits therefore provides approximately 1 logical qubit for fault-tolerant work, not 1,000.

**How to Measure/Find It:** Physical qubit count is published by all vendors. What is rarely published clearly is: how many of those qubits meet the vendor's own fidelity and coherence specifications? Ask for the **yield** — the percentage of physical qubits that meet the published benchmark.

**Scoring Guide (1–5):**

| Score | Physical Qubit Count (Context-Dependent) |
|:-----:|:----------------|
| 1 | \< 20 qubits — very limited; research demonstrations only |
| 2 | 20–100 qubits — NISQ-class; suitable for small variational algorithms |
| 3 | 100–500 qubits — meaningful scale for NISQ exploration; insufficient for fault-tolerant work |
| 4 | 500–2,000 qubits — approaching early fault-tolerant demonstrations |
| 5 | \> 2,000 qubits with demonstrated yield \> 90% meeting fidelity specs |

:::{warning}
**Do not select a vendor based on qubit count alone.** A score of 5 on this dimension with scores of 1–2 on fidelity and coherence is a system that cannot do useful work. Weight this dimension accordingly.
:::

---

### Dimension 4: Connectivity

**Definition:** The connectivity graph describes which pairs of qubits can directly interact via two-qubit gates. In a fully connected (all-to-all) topology, any qubit can interact with any other. In constrained topologies, qubits can only interact with their physical neighbors.

**Why It Matters:** When a quantum circuit requires a two-qubit gate between qubits that are not directly connected, the compiler must insert SWAP gates to bring the logical qubits into physical proximity. Each SWAP gate requires 3 CNOT gates, adding error and depth. Sparse connectivity multiplies the cost of compilation overhead, effectively reducing the useful circuit depth your hardware budget can support.

**Common Topologies (Best to Worst for General Use):**
- **All-to-all** (trapped-ion): Every qubit can interact with every other qubit. Zero SWAP overhead.
- **Heavy-hex** (IBM superconducting): Each qubit connects to 2–3 neighbors. Moderate SWAP overhead.
- **Grid/2D** (Google superconducting): Each qubit connects to 4 neighbors. Good for 2D locality.
- **Linear** (early superconducting): Each qubit connects to 1–2 neighbors. High SWAP overhead for general circuits.

**How to Measure/Find It:** Connectivity graphs are published in backend documentation. For a quantitative measure, ask for the **average shortest path length** between arbitrary qubit pairs or the **connectivity ratio** (actual edges / maximum possible edges).

**Scoring Guide (1–5):**

| Score | Connectivity |
|:-----:|:----------------|
| 1 | Linear chain — severe SWAP overhead; only practical for 1D-local algorithms |
| 2 | Sparse graph, connectivity ratio \< 10% — significant compilation overhead |
| 3 | Heavy-hex or similar, connectivity ratio 10–30% — manageable overhead with good compilers |
| 4 | Dense 2D grid or equivalent, connectivity ratio \> 30% |
| 5 | All-to-all or near-all-to-all — negligible SWAP overhead; circuits compile at near-native efficiency |

---

### Dimension 5: Queue Time / Availability

**Definition:** The elapsed time from job submission to job execution on the hardware. Includes waiting in a shared queue, system calibration windows, and maintenance downtime.

**Why It Matters:** For research, a 24-hour queue is inconvenient. For production workloads, it is a showstopper. If your application requires near-real-time quantum computation — financial optimization, drug discovery pipelines, or any workflow integrated into a larger system — queue time is a critical operational constraint that often disqualifies otherwise capable hardware.

**How to Measure/Find It:** Do not rely on vendor SLA documents alone. Benchmark it directly: submit a simple 5-qubit circuit and record actual wait time over 5–10 trials across different times of day and days of the week. IBM Quantum publishes real-time queue estimates; IonQ offers reserved access tiers. Ask vendors specifically about **dedicated access options** and their pricing model.

**Scoring Guide (1–5):**

| Score | Typical Queue Time |
|:-----:|:----------------|
| 1 | \> 24 hours — unusable for any time-sensitive workflow |
| 2 | 4–24 hours — research use only; too slow for integrated pipelines |
| 3 | 1–4 hours — acceptable for batch research jobs with planning |
| 4 | \< 1 hour or dedicated/reserved access available |
| 5 | Near-real-time (\< 5 minutes) or on-premise deployment with guaranteed availability |

---

### Dimension 6: Roadmap Credibility

**Definition:** An assessment of how reliably the vendor delivers on stated technical milestones, measured by their historical track record — not their future promises.

**Why It Matters:** You are not just buying today's hardware; you are placing a bet on a vendor's ability to scale. Vendors who consistently miss milestones, redefine metrics retroactively, or publish results without peer review are poor candidates for long-term investment regardless of their current hardware score.

**How to Measure/Find It:** Use **trailing indicators**, not forward projections. Look for: (1) a list of milestones the vendor publicly committed to in previous years; (2) which milestones were hit, missed, or redefined; (3) whether the results were published in peer-reviewed journals or only in press releases; (4) independent replication of key claims. IBM's published roadmaps with explicit qubit count targets are an example of scoreable commitments. Vague statements like "quantum advantage by 2026" are not.

**Scoring Guide (1–5):**

| Score | Roadmap Credibility |
|:-----:|:----------------|
| 1 | No published milestones or all recent milestones missed; results not peer-reviewed |
| 2 | Inconsistent delivery; significant milestone redefinition or metric shifts |
| 3 | Mixed track record; some milestones hit, some missed; partial peer-review publication |
| 4 | Consistent milestone delivery with published qualification criteria; peer-reviewed results |
| 5 | Exemplary track record; milestones hit on schedule; results independently verified and replicated |

---

### Dimension 7: Ecosystem & Tooling

**Definition:** The quality and maturity of the software development kit (SDK), documentation, cloud integration, community support, and vendor responsiveness to technical issues.

**Why It Matters:** This dimension is chronically underweighted by hardware-focused evaluators — and it shouldn't be. The best quantum hardware in the world is worthless if the SDK has undocumented breaking changes, the documentation is sparse, and support tickets go unanswered. Ecosystem maturity directly determines how quickly your team can move from concept to working circuit, and how much of your engineering budget goes to fighting tooling versus doing science.

**How to Measure/Find It:** Build something. Write a 50-line circuit, submit it, get results, and plot them — without asking the vendor for help. How long did that take? Was the documentation sufficient? Did the SDK install cleanly? Run a GitHub search for open issues in the vendor's public SDK repository. Check Stack Overflow and community forums for response quality and frequency.

**Scoring Guide (1–5):**

| Score | Ecosystem & Tooling |
|:-----:|:----------------|
| 1 | No public SDK or documentation; requires direct vendor support for all operations |
| 2 | Basic SDK with sparse documentation; significant friction for new users; slow support |
| 3 | Functional SDK with adequate documentation; community exists but limited; reasonable support |
| 4 | Mature SDK, comprehensive documentation, active community, responsive support, cloud-native integration |
| 5 | Best-in-class SDK widely adopted by third parties; extensive documentation; thriving community; first-class cloud integration; proactive support |

---

## Section 3: The Scoring Worksheet

### Instructions

1. **Assign weights before evaluating any vendor.** Enter weights in the Weight column totaling 100.
2. **Score each vendor independently** using only demonstrated, published data (1–5 per dimension).
3. **Calculate Weighted Score** = Score × (Weight / 100) for each cell.
4. **Sum Weighted Scores** to produce the Composite Score (max 5.0).
5. Flag any score marked with an asterisk (*) as relying on vendor-provided-only data.

### Blank Scoring Template

```{list-table} Hardware Vendor Evaluation Scorecard
:header-rows: 1
:widths: 22 10 10 10 10 10

* - Dimension
  - Vendor A
  - Vendor B
  - Vendor C
  - Weight (%)
  - Notes
* - 1. Coherence Time (T1/T2)
  - ___
  - ___
  - ___
  - ___
  - 
* - 2. Gate Fidelity (2Q)
  - ___
  - ___
  - ___
  - ___
  - 
* - 3. Qubit Count (Physical)
  - ___
  - ___
  - ___
  - ___
  - 
* - 4. Connectivity
  - ___
  - ___
  - ___
  - ___
  - 
* - 5. Queue Time / Availability
  - ___
  - ___
  - ___
  - ___
  - 
* - 6. Roadmap Credibility
  - ___
  - ___
  - ___
  - ___
  - 
* - 7. Ecosystem & Tooling
  - ___
  - ___
  - ___
  - ___
  - 
* - **Composite Score**
  - **___**
  - **___**
  - **___**
  - **100**
  - 
```

### Worked Example: Near-Term Chemistry Simulation

The following example illustrates a plausible (hypothetical) evaluation for a team selecting a backend for a variational quantum eigensolver (VQE) chemistry workload. Weights reflect the priorities of that use case: gate fidelity and coherence time are paramount; raw qubit count matters less than quality.

```{list-table} Worked Example — VQE Chemistry Workload
:header-rows: 1
:widths: 22 10 10 10 8 14

* - Dimension
  - Vendor A (Superconducting)
  - Vendor B (Trapped-Ion)
  - Vendor C (Superconducting)
  - Weight (%)
  - Weighted Score (A / B / C)
* - 1. Coherence Time
  - 3
  - 5
  - 4
  - 20
  - 0.60 / 1.00 / 0.80
* - 2. Gate Fidelity (2Q)
  - 3
  - 5
  - 4
  - 30
  - 0.90 / 1.50 / 1.20
* - 3. Qubit Count
  - 5
  - 2
  - 4
  - 10
  - 0.50 / 0.20 / 0.40
* - 4. Connectivity
  - 3
  - 5
  - 3
  - 15
  - 0.45 / 0.75 / 0.45
* - 5. Queue Time
  - 2
  - 3
  - 3
  - 10
  - 0.20 / 0.30 / 0.30
* - 6. Roadmap Credibility
  - 4
  - 4
  - 3
  - 10
  - 0.40 / 0.40 / 0.30
* - 7. Ecosystem & Tooling
  - 5
  - 3
  - 4
  - 5
  - 0.25 / 0.15 / 0.20
* - **Composite Score**
  - **—**
  - **—**
  - **—**
  - **100**
  - **3.30 / 4.30 / 3.65**
```

In this example, Vendor B (trapped-ion) wins despite having far fewer physical qubits, because the workload weights fidelity and coherence heavily. A team that weighted qubit count at 40% instead of 10% would reach a different conclusion — which is exactly why weights must be assigned before vendor evaluation begins.

---

## Section 4: Workload-Modality Matching Guide

Use this table as a starting reference when assigning weights and selecting which modalities to include in your evaluation. It does not replace the full rubric — a given vendor's implementation may deviate significantly from modality averages.

```{list-table} Workload-to-Modality Reference Guide
:header-rows: 1
:widths: 28 24 48

* - Workload Type
  - Preferred Modality
  - Reason
* - Near-term optimization (QAOA, VQE)
  - Superconducting or trapped-ion
  - High gate throughput (superconducting) or high fidelity (trapped-ion); both handle 50–100 qubit circuits today
* - High-fidelity chemistry simulation
  - Trapped-ion
  - All-to-all connectivity eliminates SWAP overhead; long coherence times support deeper circuits; 2Q fidelity \> 99%
* - Machine learning / quantum kernels
  - Superconducting
  - Fast gate speeds support high-repetition sampling; large qubit counts enable more expressive feature maps
* - Quantum error correction research
  - Any — weight roadmap credibility and 2Q fidelity above all else
  - Fault tolerance requires fidelity above threshold (\~99%); modality matters less than raw fidelity numbers
* - Large-scale fault-tolerant (future)
  - Any modality with strongest error correction trajectory
  - Physical qubit count and fidelity roadmap matter most; ecosystem support for logical qubit abstractions
* - Quantum networking / communication
  - Photonic
  - Photons transmit naturally over fiber; photonic systems designed for entanglement distribution and quantum repeaters
* - Combinatorial optimization (large-scale)
  - Superconducting (gate-based) or quantum annealing
  - Annealing (D-Wave class) suited to QUBO problems; gate-based superconducting for QAOA at scale
* - Quantum simulation (condensed matter)
  - Neutral atom or trapped-ion
  - Programmable Hamiltonians; analog simulation mode available; coherence times support slow evolution
* - High-throughput production workload
  - Superconducting with dedicated access
  - Fast gate speeds (\~10–100 ns) enable high job throughput; cloud-native SDKs support integration
```

:::{tip}
**Modality is a prior, not a verdict.** Trapped-ion systems generally win on fidelity; superconducting generally wins on speed and scale. But individual vendor implementations vary enormously. Always score the actual hardware, not the modality category.
:::

---

## Section 5: Red Flags Checklist

Run this checklist as a final gate after scoring. A single red flag does not disqualify a vendor, but each one should trigger specific follow-up questions. More than three red flags on a single vendor warrants serious scrutiny before any procurement decision.

:::{warning}
**Red flags do not necessarily indicate fraud or incompetence.** They indicate information gaps that must be resolved before a decision is made. A vendor who responds to red flag questions with transparent, well-documented answers is a vendor you can trust.
:::

**Pre-Evaluation Checklist:**

- [ ] **Headline qubit count is the lead metric.** The vendor's primary marketing claim is qubit count without accompanying fidelity, coherence time, or connectivity data.

- [ ] **No published calibration data or error rates.** The vendor cannot provide per-qubit T1, T2, and gate fidelity data. Backend properties are not accessible programmatically or through published datasheets.

- [ ] **"Quantum advantage" claimed without classical baseline comparison.** A claim of quantum advantage is meaningless without a side-by-side comparison against the best available classical algorithm on the same problem instance, with runtime and resource costs documented.

- [ ] **No peer-reviewed publications supporting key technical claims.** Core performance claims appear only in press releases, blog posts, or white papers without independent peer review. No arXiv preprints with methodology details.

- [ ] **Roadmap milestones have no qualification criteria.** Future milestones are stated as aspirational targets ("we plan to achieve 1,000 logical qubits by 2027") without specifying what error rates, fidelity levels, or benchmarks would constitute achievement of that milestone.

- [ ] **Historical milestones were missed or quietly redefined.** Comparing the vendor's current roadmap documentation against archived versions reveals milestones that were shifted, dropped, or redefined without public acknowledgment.

- [ ] **Proprietary benchmarks only.** Performance is described exclusively using the vendor's own benchmark suite with no mapping to standard benchmarks (e.g., quantum volume, CLOPS, mirror benchmarking) that would allow cross-vendor comparison.

- [ ] **SDK is closed-source with no independent community.** The SDK cannot be evaluated independently; there is no open-source component, no active community forum, no third-party integrations. All support flows through a vendor sales channel.

- [ ] **No independent replication of key results.** Major technical claims (e.g., a specific gate fidelity or circuit depth record) have not been replicated by any independent academic or research group.

- [ ] **Pricing is available only after NDA.** The vendor requires a non-disclosure agreement before discussing pricing or access terms. This makes competitive evaluation structurally impossible and is inconsistent with the transparency expected for enterprise procurement.

---

## Using This Rubric Over Time

Quantum hardware improves rapidly. A score of 3 on coherence time today may represent a score of 1 in three years as the field advances. We recommend re-running this evaluation annually, or whenever a vendor announces a new hardware generation.

The scoring guides in this rubric use **relative** language (e.g., "approaching fault-tolerant threshold") rather than fixed absolute numbers wherever possible. When absolute numbers are used (such as the T2 benchmarks in Dimension 1), treat them as calibrated to the 2024–2026 hardware generation and adjust upward as leading systems advance.

The weights you assign, the workload you are solving, and the absolute performance numbers you score against will all change. The seven dimensions will not.

> **A vendor who cannot answer all seven questions transparently is a vendor who is not ready for production deployment — regardless of how impressive their headline numbers look.**
