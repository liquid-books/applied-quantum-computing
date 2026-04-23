---
title: "Chapter 3: The Quantum Cloud Economy — Access, Ecosystem, and Enterprise Adoption"
subtitle: "From QaaS Platforms to Break-Even Models: Everything You Need Before the First Vendor Proposal"
short_title: "Ch. 3: Quantum Cloud Economy"
description: "Quantum computing is now a cloud service — available today from D-Wave Leap, IBM Quantum, AWS Braket, Azure Quantum, and Google Quantum AI. This chapter maps the full QaaS ecosystem, explains each platform's access model and pricing, covers D-Wave Leap and the Stride hybrid solver in depth, and builds the evergreen economic frameworks executives need to evaluate any vendor proposal."
label: ch-03-bits-to-qubits-economics
tags: [quantum economics, QaaS, D-Wave Leap, Stride, AWS Braket, Azure Quantum, IBM Quantum, Google QAI, TCO, pricing, break-even, quantum advantage, quantum utility, enterprise adoption, QUBO]
---

# Chapter 3: The Quantum Cloud Economy — Access, Ecosystem, and Enterprise Adoption

:::{figure} ../images/ch03-explainer-infographic.png
:label: fig-ch03-explainer-infographic
:alt: Chapter 3 illustrated explainer infographic showing the five QaaS platforms, quantum economics overview, pricing archetypes, TCO framework, and break-even concept across a quantum cloud landscape
:width: 100%
:align: center

**Chapter 3 at a Glance.** Two revolutions are happening simultaneously: quantum hardware is maturing, and quantum access has moved to the cloud. This chapter gives you the framework to navigate both — knowing which platform to use, what it will cost, and how to build a break-even model that survives vendor changes.
:::

There is a question that looks simple and rarely gets a straight answer: *Can I use a quantum computer today?*

The answer is yes. Right now, on a credit card, you can submit an optimization problem to the same class of hardware being installed on FAU's Boca Raton campus and have a result in seconds. You can run a quantum chemistry experiment on IBM's 127-qubit Eagle processor. You can benchmark the same circuit across three different hardware modalities from a single AWS console. Quantum computing is no longer something you visit at a national laboratory. It is a cloud service, it is operational, and it has a pricing page.

The harder question — the one this chapter answers — is: *What does it actually cost, and when does it make economic sense for your specific workload?* Quantum vendors are excellent at generating excitement. They are considerably less excellent at generating invoices you can explain to your board. The gap between those two things is where enterprise quantum strategies fail.

This chapter closes that gap. The first half maps the five platforms that define the QaaS landscape and gives you a framework for choosing between them. The second half builds the durable economic model — pricing archetypes, true unit cost, TCO, and break-even analysis — that survives any vendor change, any hardware generation, and any point in the next decade.

---

## Opening Scene: The Procurement Email Nobody Expected

In February 2026, the CFO of a South Florida logistics firm — call her Maria Gutierrez — received an email from her VP of Operations. The subject line read: *"Quantum pilot — budget request."*

The attached memo proposed a \$180,000 pilot using D-Wave's Leap cloud platform to optimize their last-mile delivery routing across the Miami–Fort Lauderdale–Boca Raton corridor. The VP had been at a vendor briefing at FAU's Boca Raton campus, where D-Wave's local presence had given her direct access to application engineers. The proposal included a specific ROI calculation: classical routing software was taking 4–6 hours overnight to produce daily route plans. D-Wave's hybrid solver, on a comparable problem, was producing results in under 90 seconds — a speedup that would enable real-time re-routing when drivers encountered traffic, accidents, or delivery failures.

Maria had three options. She could approve it. She could kill it. Or she could do what most executives in her position do: ask someone to "look into it" — which typically means the proposal sits for six months while the technology window moves.

She chose a fourth option: she asked her team to build an economic model before making any decision. Not a feelings model. Not a vendor slide deck. A model with parameters she could update when pricing changed and milestones she could monitor without hiring a quantum physicist.

This chapter gives you that model. And by the end, you will know what Maria's team found — and whether the pilot made economic sense.

---

## The Single Idea: Two Revolutions, One Chapter

```{epigraph}
Quantum computing has two revolutions happening simultaneously. The hardware is maturing. The access model has already changed. Most enterprises are paying attention to the first and missing the second.
```

The narrative around quantum computing focuses almost entirely on hardware progress: qubit counts, error rates, fault-tolerance milestones. That is the technology revolution, and it is real and important. But there is a second revolution happening in parallel that has received far less attention and is far more immediately relevant to enterprise strategy: **quantum computing has become a cloud service**.

This transition matters for three reasons.

**First, the barrier to entry has collapsed.** Three years ago, accessing quantum hardware required a research partnership, a university affiliation, or a six-figure enterprise contract. Today, a developer can create a D-Wave Leap account, receive free credits, and submit a real optimization problem to real quantum hardware in under ten minutes. The ecosystem of tools, documentation, and community support around QaaS platforms is comparable to cloud AI in 2018 — early, but functional and growing fast.

**Second, the economics are cloud economics.** Quantum hardware itself is extraordinarily capital-intensive — a single dilution refrigerator for superconducting qubits costs over \$1 million, and FAU's Advantage2 represents a \$20 million institutional investment. But enterprises consuming quantum through Leap, Braket, or IBM Quantum pay per use, on demand, with no capital commitment. The total cost of a quantum pilot is no longer determined by hardware acquisition — it is determined by shots, queue time, and engineering hours. Those are costs you can model.

**Third, the choice of platform is now a strategic decision.** Not all quantum platforms are equivalent. D-Wave's annealing hardware excels at combinatorial optimization and is production-ready today. IBM's gate-model hardware is the right environment for quantum chemistry research and algorithm development. AWS Braket offers hardware flexibility for organizations that want to compare across modalities. Azure Quantum integrates into the Microsoft enterprise stack. Google Quantum AI provides access to the most advanced error correction hardware but is not a self-service platform. Choosing the wrong platform for your workload is the quantum equivalent of using a GPU cluster to run a spreadsheet — it is not that quantum doesn't work; it is that the architecture is mismatched to the problem.

The rest of this chapter addresses both the access landscape and the economic framework you need to navigate it.

---

## Part I: The QaaS Landscape

### From HPC to Quantum: A Familiar Transition

For anyone with a background in high-performance computing, the QaaS story is a familiar one. The HPC community went through a structurally similar transition in the 2010s: from dedicated institutional clusters (owned, operated, and queue-managed by the organization) to cloud HPC (AWS HPC, Azure CycleCloud, Google Batch) that democratized access to large-scale parallel compute. The transition did not eliminate on-premises HPC — FAU operates HPC infrastructure today, as do most R1 universities — but it changed the economics fundamentally. Organizations no longer needed to own hardware to conduct HPC-scale research. They needed a model, a workload, and a cloud account.

Quantum computing is following the same arc, approximately a decade behind. The national laboratory era is giving way to the QaaS era. Organizations that understand the cloud access model — pricing, queuing, hybrid architectures, platform selection — will move faster than those waiting for the hardware to arrive on their doorstep.

The Supercomputing (SC) community has recognized this transition explicitly. SC26, scheduled for Chicago in November 2026, features quantum-HPC hybrid architectures as a primary technical track — reflecting the consensus that quantum accelerators will integrate into HPC pipelines the same way GPUs did in the 2010s. FAU's Advantage2 deployment is an early instantiation of that integration at the institutional level.

:::{figure} ../images/ch03-hpc-quantum-transition.png
:label: fig-ch03-hpc-quantum-transition
:alt: Timeline showing the parallel between HPC cloud transition in 2010s and quantum cloud transition in 2020s, with SC conference milestones annotated
:width: 100%
:align: center

**The HPC-to-Quantum Cloud Transition.** High-performance computing moved from dedicated institutional clusters to cloud access over a decade. Quantum computing is following the same arc, with QaaS platforms now enabling enterprise access that previously required national laboratory partnerships or nine-figure institutional investments.
:::

---

### The Five Platforms

:::{figure} ../images/ch03-qaas-ecosystem-map.png
:label: fig-ch03-qaas-ecosystem-map
:alt: Visual map of the five major QaaS platforms (D-Wave Leap, IBM Quantum, AWS Braket, Azure Quantum, Google Quantum AI) positioned by hardware paradigm and access model, with enterprise use case zones indicated
:width: 100%
:align: center

**The QaaS Ecosystem Map.** Five platforms define the enterprise quantum cloud market as of 2026. Each occupies a distinct position: D-Wave for production optimization today; IBM for gate-model research and development; AWS for hardware-agnostic access; Azure for Microsoft enterprise integration; Google for research partnerships and advanced error correction.
:::

---

#### D-Wave Leap — Production Annealing and Hybrid Optimization

**URL:** cloud.dwavesys.com | **Paradigm:** Quantum annealing + classical-quantum hybrid

The most commercially mature QaaS platform for business optimization problems. D-Wave Leap provides two modes of access:

- **Direct QPU access** — problems submitted directly to the Advantage2 annealer. Solves in microseconds. Best for small, well-structured QUBO problems.
- **Stride hybrid solver** — problems that are too large for the QPU alone are decomposed classically, with subproblems routed to the quantum hardware. Handles millions of variables. Results in seconds to minutes. This is the enterprise-relevant mode.

The Stride solver accepts problems formulated as **QUBO (Quadratic Unconstrained Binary Optimization)** — a mathematical format that a vast range of business decisions can be expressed in: vehicle routing, staff scheduling, warehouse slotting, portfolio construction, production sequencing. You do not need to write quantum circuits. You define the problem as a set of binary decisions and a cost function; the solver finds the lowest-cost assignment.

**Enterprise track record (production deployments):**
- **BASF** — manufacturing scheduling reduced from hours to seconds
- **Volkswagen** — paint-shop sequencing optimization
- **Mastercard** — transaction graph fraud pattern detection
- **Verge Ag** — real-time routing for autonomous agricultural equipment
- **Anduril / Davidson Technologies** — defense planning optimization (details classified)

**FAU connection:** The Advantage2 system being installed on FAU's Boca Raton campus is the same hardware class as D-Wave Leap's cloud QPU. D-Wave's corporate headquarters, now at the Boca Raton Innovation Center, provides direct engineering support and co-development partnerships for FAU research programs. Students in this course use Leap for cloud-accessible coursework; when the on-premises system is operational, it eliminates the queue latency that constrains iterative research on cloud tiers.

**Pricing:** Free developer tier with initial QPU time credits (sufficient for coursework and prototyping). Hybrid solver jobs priced per second of solve time. Reserved access contracts available for production deployments. See Appendix F for current pricing.

---

#### IBM Quantum — Gate-Model Research and Enterprise Access

**URL:** quantum.ibm.com | **Paradigm:** Gate-model (superconducting qubits)

The most accessible gate-model platform for developers, researchers, and enterprise teams building quantum algorithm expertise. IBM Quantum offers three tiers:

- **Open Plan (free)** — access to quantum simulators and a subset of real hardware (5–7 qubit systems on free tier, with queue priority limits). Suitable for education and prototyping.
- **Pay-As-You-Go** — access to IBM's full hardware fleet (Eagle 127 qubits, Heron r2 133 qubits) with priority queuing. Billed by QPU seconds.
- **Premium / IBM Quantum Network** — enterprise membership with dedicated hardware access, co-development with IBM Research, and priority above standard queue. Members include JPMorgan Chase, Daimler, Boeing, and over 200 universities.

IBM's public hardware roadmap is the most detailed in the industry, with specific qubit count and error rate targets published through 2033. The Heron r2 processor (133 qubits, released 2024) achieved improved two-qubit gate fidelities over prior generations. IBM's Condor processor (1,121 qubits) demonstrated the largest gate-model processor commercially available as of 2026.

**Ecosystem:** Qiskit, IBM's open-source quantum SDK, is the most widely used quantum programming framework globally. Python-based, well-documented, with an active community and extensive course materials. Qiskit Runtime reduces queue overhead for iterative workloads by running parameterized circuits server-side.

**Best for:** Algorithm development, quantum chemistry research, quantum machine learning experiments, workforce training in gate-model programming.

---

#### AWS Braket — Hardware-Agnostic Quantum Marketplace

**URL:** aws.amazon.com/braket | **Paradigm:** Multi-vendor marketplace

AWS Braket is not a quantum hardware manufacturer — it is a distribution layer. Amazon provides a unified API and billing interface that abstracts across multiple hardware vendors:

- **IonQ Forte** — trapped-ion, highest gate fidelities commercially available
- **Rigetti Ankaa-3** — superconducting, fast gate operations
- **QuEra Aquila** — neutral-atom, reconfigurable qubit connectivity
- **IQM Garnet** — superconducting, European hardware

From a single AWS console, you can submit the same circuit to multiple hardware types and compare results — hardware-agnostic circuit testing that no single-vendor platform offers.

**HPC integration:** AWS Braket integrates directly with AWS HPC services (ParallelCluster, Batch), enabling hybrid quantum-classical workflows where the classical HPC component runs on AWS compute and the quantum component runs on Braket. For organizations with existing HPC workloads on AWS — a common configuration for financial services, life sciences, and logistics firms — Braket is the lowest-friction entry point for quantum experimentation.

**Pricing:** Per-task fee + per-shot fee, varying by hardware provider. Classical simulators (SV1, TN1, DM1) billed per compute-minute. No membership required — pure pay-as-you-go.

**Best for:** Multi-vendor comparison, AWS-integrated enterprises, HPC-to-quantum pipeline prototyping.

---

#### Azure Quantum — Microsoft Enterprise Stack Integration

**URL:** azure.microsoft.com/products/quantum | **Paradigm:** Multi-vendor + topological qubit roadmap

Azure Quantum mirrors Braket's marketplace model but with a stronger enterprise software integration story and a long-term hardware bet on Microsoft's proprietary topological qubit program.

Current hardware access:
- **IonQ** (trapped-ion, via Azure)
- **Quantinuum H-Series** — currently achieves the highest gate fidelities available commercially; H2-2 processor (56 qubits, fully connected) offers exceptional circuit depth for its qubit count
- **Rigetti** (superconducting, via Azure)

Microsoft's topological qubit research (using Majorana zero modes) published credible experimental evidence in *Nature* in 2023. Production topological hardware is not yet available but represents Microsoft's long-term differentiation claim. If the physics works at scale, topological qubits offer inherent error resistance that would dramatically reduce error correction overhead.

**Enterprise integration:** Azure Quantum connects to Azure Active Directory, Defender, Purview, and the full Microsoft security and compliance stack — a significant advantage for regulated enterprises (financial services, healthcare, government) with existing Azure deployments.

**SDK:** Q# and the Quantum Development Kit (QDK), plus Qiskit and Cirq compatibility for hardware-agnostic circuit submission.

**Best for:** Microsoft-centric enterprise environments, regulated industries requiring Azure compliance tools, organizations that want access to Quantinuum's best-in-class gate fidelity.

---

#### Google Quantum AI — Research Partnerships and Willow Access

**URL:** quantumai.google | **Paradigm:** Gate-model research (superconducting)

Google Quantum AI is structurally different from the other platforms: it is not a self-service cloud product. Access to Google's quantum hardware — including the Willow processor (105 qubits, December 2024 below-threshold error correction milestone) — is primarily through research partnerships and the Google Quantum AI Research Program. Limited access is available through Google Cloud for qualified collaborators.

**Why it matters despite limited access:** Google's December 2024 Willow result — demonstrating that adding more qubits reduces rather than increases error rates, confirming below-threshold operation — is the most significant hardware milestone in quantum computing in a decade. It places the gate-model fault-tolerance roadmap on physically credible footing. Organizations engaged in quantum chemistry, materials simulation, or AI research at a scale that justifies a research partnership application should monitor Google Quantum AI closely.

**Best for:** Academic research partnerships, quantum AI research, organizations with existing Google Cloud relationships pursuing research-level access.

---

### Platform Selection Framework

:::{figure} ../images/ch03-platform-selection-framework.png
:label: fig-ch03-platform-selection-framework
:alt: Platform selection decision matrix mapping business goals and existing infrastructure to the optimal QaaS platform, with D-Wave Leap, IBM Quantum, AWS Braket, Azure Quantum, and Google Quantum AI positioned across axes of problem type and enterprise maturity
:width: 100%
:align: center

**Platform Selection Framework.** Match platform to problem type, infrastructure, and organizational maturity. The most common mistake is using a gate-model platform for an optimization problem that D-Wave's Stride solver could handle in production today — or over-engineering a research experiment with an enterprise contract before the use case is validated.
:::

| If your goal is... | Start here | Why |
|---|---|---|
| Solve optimization problems in production | **D-Wave Leap** | Stride hybrid solver handles production-scale problems now; no quantum circuits to write |
| Gate-model algorithm development | **IBM Quantum** | Best documentation, largest community, Qiskit ecosystem, free access |
| Multi-vendor hardware comparison | **AWS Braket** | Single API, multiple modalities, AWS HPC pipeline integration |
| Microsoft enterprise stack integration | **Azure Quantum** | Azure compliance tools; Quantinuum's best-in-class gate fidelity |
| Quantum chemistry or materials research | **Google Quantum AI** (partnership) | Willow hardware access; research program |
| FAU coursework and labs | **D-Wave Leap + IBM Quantum** | This course uses both; Leap for optimization, IBM for gate-model concepts |

:::{admonition} On-Premises vs. Cloud: The Make-vs.-Buy Decision
:class: important

Cloud QaaS is appropriate for exploration, prototyping, and most production optimization workloads where queue latency is acceptable. **On-premises hardware** — like FAU's Advantage2 — is appropriate when: research requires rapid iteration that cloud queues make impractical; data sovereignty requirements prevent cloud submission of sensitive problem instances; or the institution wants to attract industry partners who prefer local hardware access.

FAU's on-premises deployment eliminates the queue delays (typically seconds to minutes on Leap's hybrid solver) that constrain iterative research — a meaningful advantage for the kind of experimental, real-time problem-solving that characterizes both research and executive education coursework.
:::

---

## Part II: The New Economics of Quantum

### The Quantum Cost Curve Is Different — Not Just Higher

:::{figure} ../images/ch03-moores-law-end.png
:label: fig-ch03-moores-law-end
:alt: Chart showing Moore's Law transistor count growth flattening against the physical limit, alongside a new quantum cost curve that does not continue the classical trajectory but introduces a fundamentally different economic structure
:width: 100%
:align: center

**Two Cost Curves, Not One.** The classical Moore's Law trajectory — predictable, continuous, quantifiable — is ending. Quantum computing does not continue that curve. It introduces a different cost structure, shaped by error rates, coherence times, and physical-to-logical qubit ratios rather than transistor counts and clock speeds.
:::

For fifty years, computing economics followed a simple rule: more transistors, lower cost per operation, better performance per dollar. Gordon Moore's 1965 observation — that transistor counts would double roughly every two years — functioned as a business plan for the entire technology industry. You could forecast server refresh cycles, amortize hardware over three to five years, and benchmark performance against a commodity baseline. Strategy was tractable because the cost curve was predictable.

That curve is ending. Transistors are now measured in atoms. There is no room to shrink further. The hyperscalers know this — which is why AWS, Azure, and Google have all opened quantum divisions. Your CFO probably does not yet have a framework for what replaces the Moore's Law cost curve. Someone in your organization will need to brief her before the first vendor proposal lands.

Here is what she needs to understand: **quantum is not a faster classical computer**. It is a machine that operates on a fundamentally different cost structure. Classical computing costs scale with transistor counts and clock rates. Quantum computing costs scale with error rates, coherence times, and physical-to-logical qubit ratios. The arithmetic is different. The break-even math is different. The risk profile is different.

And for the specific case of D-Wave annealing, the cost structure is different again from gate-model quantum — closer to a specialized HPC accelerator than to a general-purpose computer, priced per optimization job rather than per gate operation.

:::{note} Plain Language: The Locksmith vs. the Brute-Force Safe-Cracker

**The problem.** You need to open a safe without the combination. A classical computer's approach is brute force: try 0000, then 0001, through every possible combination in sequence. Given enough speed, it succeeds — but for a trillion-combination safe, "enough speed" means billions of years. You can parallelize with a thousand machines: the problem grows exponentially faster than any speed improvement.

**The gate-model quantum approach.** A gate-model quantum computer uses *interference*: it puts the problem into superposition (all possible combinations simultaneously) and applies a sequence of operations that constructively reinforce the correct answer while canceling the wrong ones. It is closer to a skilled locksmith listening to the tumblers than a cracker grinding through combinations. The locksmith doesn't do more work — the locksmith does *different work*, mathematically structured in a way brute force cannot replicate.

**The annealing approach.** A quantum annealer like D-Wave's Advantage2 takes a third approach. It encodes the problem as an energy landscape — correct answers correspond to low-energy configurations — and uses quantum tunneling to "roll downhill" toward the solution, passing through energy barriers that would trap classical optimizers in locally good but globally suboptimal answers. Where the locksmith listens for tumblers, the annealer is more like water finding the lowest point in a landscape — but a quantum-mechanical landscape that classical simulation cannot reproduce.

**For your CFO:** The business implication is that quantum's advantage is *structural*, not just quantitative. For problems where the solution space grows exponentially — logistics routing, portfolio optimization, drug simulation, encryption — no amount of classical engineering closes the gap. The question is not "is quantum faster?" but "does a quantum algorithm exist for my problem, and is the hardware mature enough to run it?"
:::

---

### The True Cost of a Quantum Result

The most dangerous phrase in any quantum vendor conversation is **"cost per qubit."** It is meaningless as a unit of economic analysis because it omits everything that actually determines what you pay for useful computation.

The correct unit is **cost per useful result**, which depends on five multiplicative factors.

:::{figure} ../images/ch03-true-cost-formula.png
:label: fig-ch03-true-cost-formula
:alt: Visual formula diagram showing the five multiplicative factors of quantum true unit cost: shot count, circuit depth, error rate, queue time, and yield, with each factor illustrated and its typical range indicated
:width: 100%
:align: center

**The True Unit of Quantum Cost.** Five factors multiply together to determine the cost of a useful result. The dominant factor in most near-term workloads is not QPU pricing — it is queue time and engineering overhead around the quantum submission step.
:::

$$\text{Cost}_{\text{useful}} = \frac{S \cdot D \cdot \varepsilon \cdot Q}{Y}$$

Where:
- **S** — Shot count required per experiment (hundreds to thousands for statistical confidence)
- **D** — Circuit depth factor (deeper circuits accumulate more error, requiring more shots or mitigation)
- **ε** — Error rate per gate (compounds across every operation in the circuit)
- **Q** — Queue time cost (researcher time waiting for hardware access; frequently the dominant term)
- **Y** — Yield: fraction of shots producing a usable result

**The compounding problem.** These factors multiply. A circuit requiring 1,000 shots at depth 100 with 0.5% gate error rate and a 3-hour queue does not cost "1,000 shots." It costs a number that reflects the compounding of all five factors simultaneously. For most near-term quantum workloads, queue cost — measured in researcher hours — dominates QPU pricing. A 3-hour queue wait at a \$150/hr researcher rate costs \$450 before a single shot is submitted.

**D-Wave and the shot-count difference.** One reason D-Wave's hybrid solver has a more tractable cost structure than gate-model platforms for optimization problems is that annealing eliminates the shot-count / circuit-depth dynamic entirely for the quantum step. You submit a QUBO problem and receive a solution in one job — not thousands of probabilistic samples. The Stride hybrid solver's pricing reflects job time, not shot count, which dramatically simplifies the cost calculation and makes the economics more predictable for production deployment.

```{prf:definition} Shot
:label: def-shot
A **shot** is a single execution of a quantum circuit from initialization through measurement, returning one classical bitstring. Useful gate-model results require averaging across many shots — typically 1,000 to 10,000 for variational algorithms — because quantum measurement is probabilistic.
```

```{prf:definition} Circuit Depth
:label: def-circuit-depth
**Circuit depth** is the number of sequential layers of quantum gates. Each layer accumulates decoherence and gate errors. On today's hardware, circuits deeper than ~100 layers often produce outputs dominated by noise rather than signal.
```

---

### Four Pricing Archetypes

:::{figure} ../images/ch03-pricing-archetypes.png
:label: fig-ch03-pricing-archetypes
:alt: Quadrant diagram of four quantum cloud pricing archetypes positioned by workload volume and maturity, with example platforms for each archetype labeled
:width: 100%
:align: center

**The Four Pricing Archetypes.** Providers come and go. These four archetypes have persisted across every market generation. Match archetype to workload maturity: free tier for exploration, pay-per-shot for validation, pay-per-minute for optimization-intensive algorithms, reserved capacity for production.
:::

Cloud quantum providers have experimented with many pricing structures since commercial access opened in 2016. Four archetypes recur across every platform and generation. Memorize the archetypes, not any vendor's current price card.

::::{tab-set}

:::{tab-item} Pay-Per-Shot
**Pay-Per-Shot — Task-Based Pricing**

Charge per quantum circuit execution (job or task). Typical unit: cost per shot or cost per QPU-second of task execution.

*On which platforms:* AWS Braket (primary model), IBM Quantum Pay-As-You-Go tier, IonQ access on both Braket and Azure.

*Best for:* Exploratory workloads, prototyping, low-volume research. Any stage where volume is unpredictable.

*Watch for:* Minimum job fees that make very short circuits disproportionately expensive. Shot-rate caps on free tiers that create queuing even for paid users. Error mitigation overhead that multiplies effective shot count by 3–5×.

*Break-even risk:* High marginal cost at scale. Transitions to pay-per-minute once workload patterns are established.
:::

:::{tab-item} Pay-Per-Minute
**Pay-Per-Minute — Time-Based Pricing**

Charge for wall-clock time on a quantum processor, regardless of shot count or circuit activity during that time.

*On which platforms:* IBM Quantum Network (QPU-seconds), D-Wave Leap QPU access (QPU-microseconds for direct annealing access — effectively the same model at a different time scale).

*Best for:* Dense, back-to-back circuit execution — variational algorithms (VQE, QAOA) that require thousands of sequential evaluations. Workloads with known, predictable execution patterns.

*Watch for:* Idle time during hardware calibration events that is still billed. Minimum reservation windows (often one hour minimum) that inflate costs for short runs.

*Break-even risk:* Efficient for known, dense workloads; expensive when utilization is low.
:::

:::{tab-item} Hybrid Solver Jobs
**Hybrid Solver Jobs — D-Wave Specific**

D-Wave's Stride hybrid solver introduces a pricing model distinct from gate-model platforms: charge per solver job (a single optimization problem submission), measured in seconds of solver time. The job can encompass problems with millions of variables — far larger than direct QPU problems — because the classical-quantum decomposition is handled internally.

*On which platforms:* D-Wave Leap (Stride hybrid solver) exclusively.

*Best for:* Production optimization workloads — routing, scheduling, portfolio construction. Any enterprise problem formulated as QUBO with more than a few thousand variables.

*Watch for:* Problem formulation overhead. Converting a business problem to QUBO requires domain expertise and (for new problem types) engineering time. This is not a QPU cost — it is a one-time modeling investment.

*Break-even advantage:* The hybrid solver's per-job pricing is more predictable than shot-based models because the number of jobs in a production workflow is deterministic. BASF knows how many scheduling runs it does per day; they can model Leap costs as directly as classical software licensing.
:::

:::{tab-item} Reserved Capacity
**Reserved Capacity — Committed Use**

Commit to a defined quantum resource (specific processor, shot volume, or time allocation) over a fixed term (monthly or annual) in exchange for a discounted rate and priority access.

*On which platforms:* IBM Quantum Network membership, D-Wave Leap enterprise tier, Azure Quantum dedicated access.

*Best for:* Production workloads with predictable volume. Organizations where queue latency in a standard tier is operationally unacceptable. Enterprises with annual budget cycles who need cost predictability.

*Watch for:* Utilization thresholds — reserved capacity that goes unused is still paid for. Lock-in to a hardware generation that may be superseded. Require confident volume projections before committing.

*Break-even risk:* Lowest per-unit cost but highest fixed commitment. Never commit before you have validated your workload's production volume on pay-per-shot or hybrid-solver pricing.
:::

::::

:::{admonition} Archetype Selection Heuristic
:class: tip
**Free tier** for exploration. **Pay-per-shot** for validation. **Hybrid solver jobs** for D-Wave optimization production. **Pay-per-minute** for dense gate-model workloads. **Reserved capacity** for committed production. Never move to reserved capacity before validating volume on a variable pricing model.
:::

---

### Physical-to-Logical Qubit Overhead: The Number That Ruins Budget Models

:::{figure} ../images/ch03-physical-logical-overhead.png
:label: fig-ch03-physical-logical-overhead
:alt: Iceberg diagram showing the physical-to-logical qubit ratio, with the headline qubit count (physical qubits) visible above the waterline and the much smaller logical qubit count available for computation visible below
:width: 100%
:align: center

**The Physical-to-Logical Qubit Iceberg.** The headline qubit count vendors advertise is the visible tip. The logical qubits available for your computation are the submerged portion — currently 100 to 1,000 times smaller, depending on hardware quality and error correction overhead.
:::

When a quantum hardware vendor announces "1,000 qubits," that number describes physical qubits — individual quantum systems capable of holding a superposition state. It does not describe the number of *reliable* qubits available for your computation.

Physical qubits are fragile. They decohere and suffer gate errors. To perform reliable computation, multiple physical qubits must be combined into a single **logical qubit** through quantum error correction. The overhead for this conversion at current error rates: roughly **1,000 physical qubits per logical qubit** for the Surface Code.

Read that again: a "1,000-qubit processor" provides approximately **one reliable logical qubit** for fault-tolerant computation.

| Error Correction Code | Physical Qubits per Logical Qubit | Current Status |
|---|---|---|
| Surface Code (current hardware) | 1,000–10,000 | Most widely researched |
| Surface Code (near-term target, ~0.1% error rate) | 100–1,000 | Roadmap target for late 2020s |
| Color Code | 200–2,000 | Some geometries more efficient |
| No correction (NISQ regime) | 1:1 | Noisy; limited circuit depth |
| D-Wave annealing | N/A | No error correction needed for optimization; different paradigm |

The last row is important. D-Wave's annealing paradigm does not use quantum error correction codes. The Advantage2's optimization is inherently probabilistic — the annealer finds good solutions rather than exact answers, which is appropriate for most real-world optimization problems. This sidesteps the physical-to-logical overhead problem entirely for the optimization problem class. It is one reason D-Wave deployments are production-viable today while fault-tolerant gate-model computation remains years away.

:::{admonition} Board Briefing Rule
:class: warning
Never quote the headline qubit count to your board for gate-model hardware. The number to quote is the estimated number of *logical qubits* available for your workload, given current error correction overhead. That number is usually smaller by two to three orders of magnitude. For D-Wave optimization problems, the relevant metric is not qubit count — it is problem variable count and solve time.
:::

---

### TCO Framework: The Six-Stage Pipeline

:::{figure} ../images/ch03-tco-framework.png
:label: fig-ch03-tco-framework
:alt: Six-stage quantum TCO pipeline diagram showing data ingestion, pre-processing, quantum submission, error mitigation, post-processing, and validation as sequential stages with cost drivers and common mistakes labeled at each stage
:width: 100%
:align: center

**The Quantum TCO Pipeline.** Every quantum workload — gate-model or annealing — is a hybrid pipeline. The quantum submission stage is typically the *minority* of total cost. Most organizations budget only for quantum submission and are surprised by the cost of the stages surrounding it.
:::

Every real-world quantum application is a **hybrid workload** — a pipeline that begins and ends with classical computing, with a quantum step in the middle. Total cost of ownership must account for all six stages.

::::{grid} 2

:::{grid-item-card} 1. Data Ingestion
**Cost drivers:** Storage, network transfer, data encoding design.

**Watch for:** For gate-model workloads, quantum amplitude encoding can require circuit depth proportional to data size — eliminating quantum advantage before the algorithm runs. D-Wave's QUBO formulation sidesteps this; the classical problem description is the input.
:::

:::{grid-item-card} 2. Pre-Processing
**Cost drivers:** Classical compute time, circuit compilation, problem decomposition.

**Watch for:** Gate-model circuits compiled for abstract machines may require 10× more gates when mapped to a specific hardware topology. D-Wave problems require QUBO formulation — a one-time modeling investment but a real upfront cost.
:::

:::{grid-item-card} 3. Quantum Submission
**Cost drivers:** Shot count × QPU rate + queue time (gate-model); hybrid solver job time (D-Wave).

**Common mistake:** Treating this as total cost. It is often the minority of TCO. Engineering time around the submission stage frequently exceeds QPU costs in early-stage workloads.
:::

:::{grid-item-card} 4. Error Mitigation
**Cost drivers:** Additional shots for mitigation (2–10× base shot count), classical post-processing.

**D-Wave note:** Annealing-based optimization does not require error mitigation in the gate-model sense. The hybrid solver handles solution quality internally. This is a meaningful cost advantage for optimization workloads.
:::

:::{grid-item-card} 5. Post-Processing
**Cost drivers:** Classical compute, statistical aggregation, result decoding.

**Watch for:** For optimization workloads (D-Wave), post-processing is typically minimal — the solver returns a solution directly. For variational algorithms (gate-model), statistical analysis over thousands of shots is required.
:::

:::{grid-item-card} 6. Validation
**Cost drivers:** Classical simulation for small-scale verification, domain expert time, comparison to baseline.

**Watch for:** Validation is often the most expensive stage in terms of researcher time. A quantum result that cannot be validated against a classical baseline has no business value regardless of theoretical correctness.
:::

::::

:::{admonition} TCO Rule of Thumb
:class: note
For early-stage quantum projects: 20% QPU/solver time, 30% engineering and integration, 25% error mitigation and post-processing (gate-model) or QUBO formulation (D-Wave), 25% validation and iteration. D-Wave optimization workloads typically have lower mitigation overhead and faster time-to-result, shifting the distribution toward validation and formulation.
:::

---

### Quantum Advantage, Utility, and Supremacy: Three Terms You Must Not Conflate

:::{figure} ../images/ch03-advantage-vs-utility.png
:label: fig-ch03-advantage-vs-utility
:alt: Three-zone spectrum diagram showing quantum supremacy (task-specific, not commercially useful), quantum utility (novel scientific results), and quantum advantage (commercially useful problem solved better than classical), with D-Wave optimization positioned at the advantage boundary for specific problem classes
:width: 100%
:align: center

**Advantage, Utility, Supremacy — Three Different Finish Lines.** D-Wave's production deployments (BASF, Volkswagen, Mastercard) are argued as demonstrated quantum advantage for specific optimization workloads. Gate-model hardware is generally at the utility stage. Supremacy is a benchmark milestone, not a commercial claim.
:::

These three terms are used interchangeably in press releases and incorrectly in most board presentations. They are not interchangeable.

```{prf:definition} Quantum Supremacy
:label: def-quantum-supremacy
A quantum computer performs a specific computation faster than any classical computer within a practical timeframe. The task is typically chosen *because* it is hard to simulate classically — not because anyone wants the answer commercially. Google's 2019 Sycamore experiment is the canonical example.
```

```{prf:definition} Quantum Advantage
:label: def-quantum-advantage
A quantum computer solves a *practically useful* problem faster, cheaper, or more accurately than the best available classical alternative. This is the threshold that matters for business investment decisions.
```

```{prf:definition} Quantum Utility
:label: def-quantum-utility
A quantum computer produces results that are difficult or impossible to verify by classical simulation, contributing novel scientific insight even if not definitively faster than all classical methods. IBM's 2023 *Nature* paper demonstrated this on a 127-qubit system simulating a quantum material.
```

**Where D-Wave fits:** D-Wave's production deployments — BASF scheduling, Volkswagen paint-shop sequencing — are argued as demonstrated quantum *advantage* for specific optimization problem classes: the hybrid solver produces better solutions faster than the classical alternatives previously used. This claim is contested in the academic literature (classical solvers have improved significantly) but the production metrics are real: BASF reports scheduling computation reduced from hours to seconds. Whether that is "quantum advantage" in a strict computational complexity sense is an academic debate; whether it delivers operational ROI is not.

| Claim Type | Vendor Usually Means | What to Verify |
|---|---|---|
| "Quantum supremacy" | We beat a classical computer at a benchmark | Was the benchmark useful? Is the comparison fair? |
| "Quantum advantage" | We solved a real problem better | What classical baseline? At what problem size? |
| "Quantum utility" | Our machine produces novel results | Is this relevant to your workload? |
| "Production deployment" (D-Wave) | We are running in enterprise operations | What are the operational metrics? What classical alternative was replaced? |

---

### The Evergreen Break-Even Template

:::{figure} ../images/ch03-break-even-template.png
:label: fig-ch03-break-even-template
:alt: Break-even analysis chart showing the intersection of quantum and classical cost curves as problem size increases, with D-Wave and gate-model curves plotted separately against the classical baseline, and the break-even threshold zones marked
:width: 100%
:align: center

**The Break-Even Template.** Separate workload parameters (stable, determined by your problem) from vendor parameters (volatile, updated annually). The intersection of the quantum and classical cost curves defines when quantum becomes economically rational. D-Wave optimization workloads often reach break-even at smaller problem sizes than gate-model workloads because the hybrid solver is production-ready today.
:::

A break-even analysis for quantum must survive vendor changes and hardware generations. The template below achieves this by separating **workload parameters** (stable — your problem defines these) from **vendor parameters** (volatile — update annually).

```python
# ============================================================
# QUANTUM BREAK-EVEN TEMPLATE — UPDATE VENDOR PARAMS ANNUALLY
# ============================================================

# --- WORKLOAD PARAMETERS (stable — your problem defines these) ---
PROBLEM_SIZE = 100             # e.g., number of variables, assets, nodes
SHOTS_REQUIRED = 10_000        # gate-model only; D-Wave: set to 1 (one job)
CIRCUIT_DEPTH = 50             # gate-model only; D-Wave: N/A
EXPERIMENTS_PER_RUN = 20       # optimization iterations or problem instances
CLASSICAL_COST_PER_RUN = 0.85  # USD — BEST classical alternative, not legacy

# --- VENDOR PARAMETERS — Gate-Model (update annually) ---
QPU_COST_PER_SHOT = 0.00001        # USD; from vendor pricing page
GATE_ERROR_RATE = 0.005            # fractional error per two-qubit gate
QUEUE_OVERHEAD_HOURS = 2.0         # average queue wait on your tier
RESEARCHER_HOURLY_COST = 150       # USD — fully-loaded team rate
ERROR_MITIGATION_MULTIPLIER = 3.0  # shots multiplier for error mitigation

# --- VENDOR PARAMETERS — D-Wave Hybrid Solver (update annually) ---
DWAVE_SOLVER_COST_PER_SECOND = 0.00015   # USD; from D-Wave Leap pricing
DWAVE_SOLVE_TIME_SECONDS = 5.0           # typical hybrid solver job time
DWAVE_QUEUE_OVERHEAD_HOURS = 0.05        # minimal on hybrid solver tier

# --- DERIVED: Gate-Model ---
effective_shots = SHOTS_REQUIRED * ERROR_MITIGATION_MULTIPLIER
qpu_cost_gm = effective_shots * EXPERIMENTS_PER_RUN * QPU_COST_PER_SHOT
queue_cost_gm = QUEUE_OVERHEAD_HOURS * RESEARCHER_HOURLY_COST
total_gm = qpu_cost_gm + queue_cost_gm

# --- DERIVED: D-Wave ---
solver_cost_dw = DWAVE_SOLVE_TIME_SECONDS * DWAVE_SOLVER_COST_PER_SECOND * EXPERIMENTS_PER_RUN
queue_cost_dw = DWAVE_QUEUE_OVERHEAD_HOURS * RESEARCHER_HOURLY_COST
total_dw = solver_cost_dw + queue_cost_dw

# --- Classical Baseline ---
classical_total = CLASSICAL_COST_PER_RUN * EXPERIMENTS_PER_RUN

print(f"Gate-model quantum: ${total_gm:.4f} ({total_gm/classical_total:.2f}x classical)")
print(f"D-Wave hybrid:      ${total_dw:.4f} ({total_dw/classical_total:.2f}x classical)")
print(f"Classical baseline: ${classical_total:.4f}")
```

:::{admonition} The Most Important Parameter
:class: important
`CLASSICAL_COST_PER_RUN` is the most important number in the model and the one most organizations get wrong. It must represent the **best available classical algorithm** — not legacy infrastructure, not the solver you've used for ten years, not what you currently pay. If you benchmark quantum against a poorly optimized classical approach, your break-even analysis is theater.
:::

---

## Part III: Bringing It Together

### Flagship Case Study: Maria Gutierrez Builds the Model

:::{figure} ../images/ch03-pharma-cfo-case.png
:label: fig-ch03-logistics-cfo-case
:alt: Case study infographic showing logistics CFO Maria Gutierrez building a D-Wave break-even model for last-mile delivery routing optimization, with the model's key parameters and outcomes illustrated
:width: 100%
:align: center

**Case Study: The Logistics CFO's Break-Even Model.** Maria Gutierrez chose a fourth option when the quantum proposal landed: build a model before deciding. The model revealed that D-Wave's hybrid solver was already cost-competitive for her routing workload — but only if she could quantify the classical baseline accurately.
:::

### Situation

Maria Gutierrez, CFO of a South Florida logistics firm, received the memo from the opening scene: a \$180,000 D-Wave pilot to optimize last-mile routing across the Miami–Fort Lauderdale–Boca Raton corridor. Classical routing software was taking 4–6 hours overnight to produce daily route plans. D-Wave's hybrid solver was producing comparable results in under 90 seconds.

### Quantum Angle

The problem — vehicle routing with time windows, driver constraints, and dynamic traffic inputs — is a classical QUBO workload. It does not require gate-model quantum hardware. It does not require fault tolerance. It requires a solver that handles large combinatorial optimization problems faster than the classical alternatives — which D-Wave's Stride hybrid solver demonstrably does at this problem scale.

### The Model Maria's Team Built

**Classical baseline (correctly computed):** The firm was paying \$0.22 per routing run using their existing solver — but the operations team's time waiting for the 4–6 hour overnight computation was the real cost. When fully loaded (scheduler time + delayed decision-making), the true cost per routing cycle was \$8.40 — not \$0.22.

This changed the break-even calculation fundamentally.

**D-Wave hybrid solver cost:** At D-Wave Leap enterprise pricing, the team estimated \$0.08–\$0.14 per routing job (90-second solve time × solver rate). No error mitigation overhead. No shot count. One job submission, one result.

**Quantum-to-classical ratio:** \$0.11 quantum / \$8.40 classical = **0.013×** — quantum was 77× cheaper per run when correctly accounting for the full classical cost.

**The model output:** At current problem size (200 vehicles, 1,800 delivery points), D-Wave's hybrid solver was already cost-competitive and operationally superior. The \$180,000 pilot would pay back in under four months at the firm's routing volume.

### Decisions Made

Maria approved the pilot — but structured it as a 90-day proof of value with three specific outcome gates:
1. Solve time under 3 minutes for the production problem size ✓
2. Route quality (total distance) within 5% of classical overnight solver ✓
3. Integration with the firm's TMS (Transportation Management System) demonstrated ✓

The committed production contract followed after all three gates cleared.

**What she got right:**
- She computed the classical baseline as a *fully loaded business cost*, not just software licensing
- She isolated the quantum submission cost from the engineering integration cost
- She structured the pilot with measurable outcome gates before committing to production

**What she got wrong:**
- She underestimated the QUBO formulation effort for the TMS integration. Converting the firm's routing problem to D-Wave's Ocean SDK format took a D-Wave engineer 3 weeks — a cost not included in the original proposal. The pilot still made economic sense, but the model should have included a formulation budget.

### Measured Outcome

At the close of the pilot: routing computation reduced from 4–6 hours overnight to under 90 seconds. Dynamic re-routing (previously impossible with overnight batch processing) became operationally feasible. The firm activated D-Wave Leap's enterprise tier and is now running production routing on the hybrid solver.

### Open Question

The pilot optimized routing across a fixed geography. The next question for Maria's team: can the same QUBO approach handle *network design* optimization — not just routing on a fixed network, but simultaneously optimizing the delivery network topology, depot locations, and vehicle assignments? The problem scale grows significantly; preliminary conversations with D-Wave's Boca Raton engineering team (co-located with FAU) suggest it is feasible but would require a dedicated formulation engagement.

---

### Industry Snapshots

**The Hyperscaler's Internal Framework.** A major cloud provider's quantum product team built a TCO framework for internal pricing that the external sales team was explicitly *not* allowed to use in customer conversations. The reason: the framework made clear that for workloads below a certain problem size, the honest recommendation was to use the provider's classical HPC service instead. The framework's key insight was a "quantum premium curve" — the ratio of quantum TCO to classical TCO as a function of problem size. Below a threshold (the "breakover point"), quantum was always more expensive. Above it, quantum could be competitive. The breakover point shifted left (toward smaller problem sizes) as hardware improved — requiring the framework to be re-run every hardware generation.

**The Bank That Skipped the Early Contract.** A large retail bank's innovation team was presented with a gate-model quantum contract in 2021 for portfolio optimization. The contract was structured as a \$3.5M two-year research partnership. The bank's quant team declined on a single basis: the TCO model showed the optimization problem sizes that mattered required logical qubit counts two orders of magnitude beyond any available hardware. The bank allocated \$200,000 to internal quantum literacy instead. In 2025, the same team re-ran the analysis with updated hardware parameters; the breakover point had moved significantly. They are now in active evaluation — with two years of internal expertise that the teams who signed early contracts spent on vendor-specific integrations requiring complete rebuilds.

---

## Productive-Struggle Problem

```{admonition} Productive Struggle: Build the Break-Even
:class: important

**Scenario:** You are a strategy analyst at a logistics firm evaluating D-Wave Leap for vehicle routing optimization. Your current classical solver costs \$2.10 per routing run (fully loaded) and takes 3 hours. D-Wave's hybrid solver is estimated at \$0.09 per job based on your problem size.

**Build a two-page break-even analysis:**
1. All pricing in a single parameter block — updating vendor pricing should require changing one section only
2. Apply the six-stage TCO framework — account for all stages, not just solver cost
3. Include a sensitivity table: what happens if (a) classical solver improves by 50%, (b) QUBO formulation costs double, (c) D-Wave pricing doubles
4. State your break-even condition: at what routing volume per month does D-Wave become cost-positive?
5. State what would change your recommendation — what hardware or pricing event would reverse the decision?

**Deliverable:** Two-page memo to your CFO, structured as: What we analyzed → What the model shows → Key assumptions → Recommendation → Monitoring triggers.
```

::::{dropdown} Discussion Guidance

**The formulation cost trap.** Most break-even models for D-Wave undercount the QUBO formulation cost — the engineering time to express the business problem in the format the solver accepts. For a routing problem that has never been run on D-Wave, formulation typically takes one to three weeks of a domain expert's time. This is a fixed cost (not recurring), but at \$150/hr it can represent \$12,000–\$24,000 upfront. Include it as an amortized cost across the expected production lifetime.

**The classical baseline trap.** The single most common error in quantum break-even models is benchmarking quantum against an unoptimized classical system. If your classical solver is poorly tuned, quantum will look attractive even when it shouldn't be. The classical baseline must represent the best available classical alternative — including modern heuristics, commercial solvers, and cloud HPC options.

**The monitoring trigger.** A well-built break-even model includes a monitoring trigger: a specific hardware or pricing event that would change the recommendation. For gate-model optimization, the trigger might be "when logical qubit count exceeds X." For D-Wave, it might be "when hybrid solver pricing drops below Y per second." Build the trigger into the model, not just the memo.
::::

---

## Module-Level Outcomes

By the end of this chapter, you should be able to:

::::{grid} 1 1 2 2
:::{grid-item-card} Outcome 1
**Platform Selection**

Compare the five QaaS platforms (D-Wave Leap, IBM Quantum, AWS Braket, Azure Quantum, Google Quantum AI) and select the appropriate platform for a given workload, explaining the rationale in terms of problem type, pricing model, and enterprise integration requirements.
:::

:::{grid-item-card} Outcome 2
**Pricing Archetypes**

Distinguish the four pricing archetypes — pay-per-shot, pay-per-minute, hybrid solver jobs, and reserved capacity — and match each to workload maturity and volume characteristics.
:::

:::{grid-item-card} Outcome 3
**True Unit Cost**

Decompose quantum cost per useful result into its five multiplicative factors (shot count, circuit depth, error rate, queue time, yield) and explain how D-Wave's hybrid solver changes this calculation for optimization workloads.
:::

:::{grid-item-card} Outcome 4
**TCO Framework**

Apply the six-stage TCO framework to a quantum workload, identifying all cost drivers — not just QPU or solver time — and building a model with isolated vendor parameters that can be updated without rebuilding the analysis.
:::

:::{grid-item-card} Outcome 5
**Break-Even Analysis**

Build a break-even model distinguishing gate-model and D-Wave annealing cost structures, benchmark against the best classical alternative (not legacy systems), and articulate the monitoring triggers that would change the investment recommendation.
:::
::::

---

## Lab 3A (Regular): Running Your First Quantum Circuit and Reading the Bill

**Duration:** ~45 minutes | **Tool:** IBM Quantum (quantum.ibm.com) — free tier  
**Deliverable:** One-page TCO memo

### Instructions

**Part 1: Build and Run the Circuit**

1. Create a free IBM Quantum account at quantum.ibm.com
2. In Quantum Composer, build a 3-qubit GHZ state circuit:
   - Hadamard gate on qubit 0
   - CNOT (control: qubit 0, target: qubit 1)
   - CNOT (control: qubit 1, target: qubit 2)
   - Measure all three qubits
3. Run on **ibmq_qasm_simulator** (1,024 shots). Record results.
4. Run the same circuit on a **real backend** (any available). Record queue time.

**Part 2: Fill the Cost Worksheet**

| Metric | Simulator | Real Hardware |
|---|---|---|
| Shots submitted | 1,024 | 1,024 |
| Queue time | ~0 sec | Record yours |
| Cost (USD) | \$0 | \$0 (free tier) |
| % correct results (`000` or `111`) | ~100% | Record yours |
| Cost per useful result | \$0 | Calculate |

**Part 3: Write the CFO Memo** (one page, six-stage TCO framework)

---

## Lab 3B (Regular): D-Wave Break-Even for a Routing Problem

**Duration:** ~60 minutes | **Tools:** D-Wave Leap + spreadsheet  
**Deliverable:** Platform comparison memo

### Overview

You will run a D-Wave sample optimization problem, record the actual cost metrics from the Leap dashboard, and build a simple break-even model comparing D-Wave's hybrid solver to a classical alternative.

### Part 1: Run the Sample Problem

1. Log into D-Wave Leap (cloud.dwavesys.com)
2. Navigate to Examples → select a routing or scheduling problem
3. Run on the Leap hybrid solver. Record:
   - **Problem size** (number of variables)
   - **Solve time** (seconds, from timing breakdown)
   - **QPU access time** (microseconds, from timing breakdown)
   - **Compute time used** (from account dashboard — your actual cost deducted from credits)

### Part 2: Build the Break-Even Model

Using the break-even template from this chapter, populate the D-Wave parameters from your actual run. Then set the classical baseline as "a classical greedy heuristic solving the same problem size in 45 seconds at \$0.04 per run" (a reasonable estimate for small routing problems).

Calculate: at what problem *size* does D-Wave's solver become cost-competitive with classical heuristics? Use the problem size axis — run the calculation for 50, 100, 500, and 1,000 variables.

### Part 3: Write the Comparison Memo

One-page memo to a logistics manager. Recommend whether to use D-Wave Leap for a routing problem with 200 delivery points and 15 vehicles. Justify with your model.

---

## Lab 3 (Optional Advanced): Build Your Own Quantum TCO Calculator

**Duration:** ~2–3 hours | **Tools:** Python 3, pandas | **Deliverable:** Working calculator + README + 400-word memo

Build a reusable quantum TCO calculator that accepts workload parameters, loads vendor pricing from an external `vendor_config.json` file, and outputs cost comparisons across gate-model and D-Wave pricing models.

```python
#!/usr/bin/env python3
"""
quantum_tco.py — Quantum TCO Calculator (Gate-Model + D-Wave)
Update vendor_config.json annually; workload params stay stable.
"""

import json, pandas as pd
from dataclasses import dataclass

@dataclass
class WorkloadParams:
    shots_per_experiment: int = 10_000      # gate-model
    experiments_per_run: int = 20
    circuit_depth: int = 50                 # gate-model
    researcher_hourly_rate_usd: float = 150.0
    classical_cost_per_run_usd: float = 0.85

def load_vendor_config(path="vendor_config.json"):
    try:
        with open(path) as f: return json.load(f)
    except FileNotFoundError:
        return {
            "gate_model": {
                "cost_per_shot_usd": 0.00001,
                "avg_queue_hours": 2.0,
                "error_mitigation_multiplier": 3.0
            },
            "dwave_hybrid": {
                "cost_per_second_usd": 0.00015,
                "avg_solve_time_seconds": 5.0,
                "avg_queue_hours": 0.05
            }
        }

def calculate_gate_model_tco(w: WorkloadParams, v: dict) -> dict:
    gm = v["gate_model"]
    shots = w.shots_per_experiment * gm["error_mitigation_multiplier"] * w.experiments_per_run
    qpu = shots * gm["cost_per_shot_usd"]
    queue = gm["avg_queue_hours"] * w.researcher_hourly_rate_usd
    total = qpu + queue
    classical = w.classical_cost_per_run_usd * w.experiments_per_run
    return {"model": "Gate-Model", "qpu_cost": round(qpu,4),
            "queue_cost": round(queue,4), "total": round(total,4),
            "classical": round(classical,4), "ratio": round(total/classical,2)}

def calculate_dwave_tco(w: WorkloadParams, v: dict) -> dict:
    dw = v["dwave_hybrid"]
    solver = dw["avg_solve_time_seconds"] * dw["cost_per_second_usd"] * w.experiments_per_run
    queue = dw["avg_queue_hours"] * w.researcher_hourly_rate_usd
    total = solver + queue
    classical = w.classical_cost_per_run_usd * w.experiments_per_run
    return {"model": "D-Wave Hybrid", "solver_cost": round(solver,4),
            "queue_cost": round(queue,4), "total": round(total,4),
            "classical": round(classical,4), "ratio": round(total/classical,2)}

if __name__ == "__main__":
    w = WorkloadParams()
    v = load_vendor_config()
    gm = calculate_gate_model_tco(w, v)
    dw = calculate_dwave_tco(w, v)
    print(f"\nGate-Model: ${gm['total']:.4f} ({gm['ratio']}x classical)")
    print(f"D-Wave:     ${dw['total']:.4f} ({dw['ratio']}x classical)")
    print(f"Classical:  ${gm['classical']:.4f}")
```

**Deliverable:** Working script + `vendor_config.json` template + 400-word CFO memo.

---

## Discussion Guidelines

**Prompt 1:** The BASF case (D-Wave hybrid solver reducing manufacturing scheduling from hours to seconds) is cited as a production quantum deployment. Using the three-term framework (supremacy, advantage, utility), evaluate whether this constitutes genuine quantum advantage or a well-engineered classical-quantum hybrid that is primarily a classical optimization improvement. Cite at least one scholarly or technical source.

**Prompt 2:** A colleague argues: "D-Wave is quantum in name only — the real computation is classical, and the quantum part is just a heuristic subroutine." Using what you know about quantum annealing, quantum tunneling, and the physical-to-logical overhead section, construct a response. Does the architecture classification matter for enterprise investment decisions?

**Peer response requirement:** Respond substantively to at least two peers. Engage with their specific claims — challenge an assumption, introduce evidence they did not cite, or extend their argument to a domain they did not consider. Minimum 150 words per response.

---

## Glossary

**Quantum-as-a-Service (QaaS)** — A cloud delivery model providing remote access to quantum hardware, billed by usage. The five major QaaS platforms are D-Wave Leap, IBM Quantum, AWS Braket, Azure Quantum, and Google Quantum AI.

**D-Wave Leap** — D-Wave's cloud quantum platform providing access to the Advantage2 annealing hardware and Stride hybrid solver. The same hardware class as FAU's on-premises system. Production-ready for combinatorial optimization today.

**Stride Hybrid Solver** — D-Wave's production hybrid quantum-classical solver. Decomposes large optimization problems classically, routes subproblems to the Advantage2 QPU, and returns solutions in seconds. Handles problems with millions of variables.

**QUBO (Quadratic Unconstrained Binary Optimization)** — The mathematical problem format accepted by quantum annealers. A wide range of business problems — routing, scheduling, portfolio construction — can be expressed as QUBO. The formulation step (converting a business problem to QUBO) is a one-time modeling investment.

**AWS Braket** — Amazon's hardware-agnostic quantum marketplace providing unified API access to IonQ, Rigetti, QuEra, and IQM hardware. Best for multi-vendor comparison and AWS-integrated enterprises.

**Azure Quantum** — Microsoft's quantum cloud platform integrating IonQ, Quantinuum, and Rigetti hardware within the Azure enterprise stack. Long-term bet on topological qubits.

**IBM Quantum Network** — IBM's enterprise quantum access and co-development program. Priority hardware, IBM Research collaboration, dedicated access.

**Google Quantum AI** — Google's quantum research division and Willow processor program. Research partnership access model; demonstrated below-threshold error correction December 2024.

**Shot** — A single execution of a gate-model quantum circuit, returning one classical bitstring. Useful results require hundreds to thousands of shots.

**Circuit Depth** — The number of sequential gate layers in a quantum circuit. Deeper circuits accumulate more noise. On current hardware, circuits beyond ~100 layers often produce noise-dominated results.

**Physical Qubit** — An individual quantum system subject to noise and decoherence. The unit vendors advertise.

**Logical Qubit** — An error-corrected qubit built from ~1,000 physical qubits. The unit relevant for fault-tolerant computation.

**Physical-to-Logical Ratio** — The number of physical qubits required per logical qubit. Currently 100–10,000 depending on hardware quality and error correction code.

**Error Mitigation** — Classical post-processing to reduce noise impact without full error correction. Requires 2–10× additional shots. Not required for D-Wave annealing workloads.

**Quantum Supremacy** — Performing a specific computation faster than any classical computer. Task is usually not commercially useful. Google Sycamore 2019.

**Quantum Advantage** — Solving a practically useful problem better than the best available classical alternative. The commercially relevant threshold.

**Quantum Utility** — Producing results that classical simulation cannot easily verify, enabling novel research. IBM 2023 *Nature* paper. Lower bar than advantage.

**TCO (Total Cost of Ownership)** — Complete cost across all six pipeline stages: ingestion, pre-processing, quantum submission, error mitigation, post-processing, validation. QPU/solver time is typically the minority of TCO.

**Break-Even Point** — The problem scale or hardware capability at which quantum cost equals classical cost. The core metric for quantum investment decisions.

**Pay-Per-Shot** — QPU pricing per circuit execution. Optimal for low-volume, exploratory workloads.

**Hybrid Solver Job** — D-Wave's per-job pricing for Stride hybrid solver submissions. More predictable than shot-based models for production optimization.

**Reserved Capacity** — Committed quantum resource for a fixed term at a discounted rate. Appropriate for production workloads with predictable volume.

**Make-vs.-Buy (Quantum)** — The decision between on-premises quantum hardware (capital expenditure, low latency, data sovereignty) and cloud QaaS (operational expenditure, managed infrastructure). FAU's Advantage2 is an on-premises deployment.

---

## Going Deeper (Optional): Quantum Complexity and Why Speedup Isn't Free

*This section is for readers with a STEM background or those interested in the theoretical foundations of quantum advantage. Not required for course assessments.*

### Complexity Classes: Where Quantum Fits

Computer science classifies problems by how hard they are to solve as input size grows. The key classes relevant to quantum computing:

- **P** — problems solvable in polynomial time on a classical computer (fast, tractable)
- **NP** — problems whose solutions can be *verified* in polynomial time, but may require exponential time to *find* (e.g., factoring a large number, solving combinatorial optimization)
- **BQP** (Bounded-error Quantum Polynomial time) — problems solvable in polynomial time on a quantum computer with error probability ≤ 1/3

The widely believed (but unproven) relationship: **P ⊆ BQP ⊆ NP**. Quantum computers are faster than classical for problems in BQP that are not in P — but they are not believed to solve all NP problems efficiently. This is the most important nuance in quantum computing claims: quantum is not a universal speed-up.

### Grover's and Shor's Speedup Quantified

**Grover's search algorithm** provides a quadratic speedup for unstructured search: searching a database of $N$ entries requires $O(N)$ steps classically and $O(\sqrt{N})$ steps on a quantum computer. Significant, but not exponential.

*In plain terms: If you're searching a billion-record database, a classical computer checks up to 1,000,000,000 records. Grover's algorithm checks up to √1,000,000,000 ≈ 31,623 records. That's ~30,000× faster — real, useful, but not the sci-fi "instant answer" people imagine. It's a square root improvement, not an infinite one.*

**Shor's factoring algorithm** provides an *exponential* speedup for integer factorization: factoring an $n$-bit integer requires $O(2^{n/2})$ classical steps with the best known algorithm, versus $O(n^3)$ quantum steps. This is why RSA encryption — whose security rests on the hardness of factoring — is cryptographically broken by a fault-tolerant quantum computer.

*In plain terms: For a standard 2,048-bit encryption key, the best classical method needs roughly 10³⁴ steps — more operations than there are atoms in the universe, effectively impossible. Shor's algorithm needs roughly 2,048³ ≈ 8.6 billion steps — easy for a computer. That's the difference between "takes longer than the age of the universe" and "done in an afternoon." This is why encryption is in danger.*

### Why QaaS Pricing Reflects Marginal Cost, Not Value

From a microeconomics perspective, quantum cloud pricing follows a pattern familiar from early cloud computing: vendors price near marginal cost (primarily electricity, cryogenic maintenance, and depreciation per shot) to capture market share and drive adoption, while classical HPC infrastructure has already paid off capital costs. The formula for break-even quantum value — introduced in Chapter 3's TCO framework — formalizes this:

$$\text{Quantum ROI} = \frac{\Delta \text{Solution Quality} \times \text{Business Value per Unit}}{\text{QPU Cost per Run} + \text{Integration Cost}} - 1$$

*In plain terms: This is just a business ROI formula with quantum-specific variables plugged in. The numerator asks "how much better is the quantum solution, and what's that improvement worth in dollars?" The denominator asks "what did it cost to run?" If the improvement is tiny (quantum barely beats classical), the fraction is small and ROI is negative. If D-Wave's cloud cost is near zero (which it often is), even small improvements look great. That's the economic logic behind why D-Wave's Stride solver is winning enterprise deals right now.*

When $\Delta$ Solution Quality is small (quantum finds only marginally better solutions than classical), the denominator dominates and ROI is negative. This is the current state for most NISQ-era gate-model applications. D-Wave's hybrid Stride solver changes the denominator: LeapHybridSampler time is priced near zero for developers, making even modest solution quality improvements ROI-positive — the commercial insight behind every D-Wave enterprise deployment in this book.

### Connection to Chapter Content

The QaaS ecosystem comparison in this chapter — Leap, Braket, Azure, IBM, Google — is ultimately a comparison across different positions in the BQP landscape: annealing optimizers targeting combinatorial problems (D-Wave), universal gate-model simulators targeting chemistry/ML (IBM, Google), and hybrid platforms bridging both (AWS Braket). Each service tier price reflects where the vendor's marginal cost sits and what problem class they're pricing against.

---

## Leader's Takeaway

```{epigraph}
The most expensive quantum strategy is the one that commits too early. The second most expensive is the one that starts too late to build expertise before the hardware is ready.
```

The lesson of this chapter is that quantum computing has two parallel timelines, and most enterprise strategies are calibrated to only one of them.

The first timeline — fault-tolerant gate-model quantum — is measured in years to decades. It requires patience, capability building, cryptographic preparation, and careful monitoring of hardware milestones. It should not receive committed production investment before the hardware reaches the problem scales your workloads require.

The second timeline — quantum annealing and hybrid optimization — is already here. D-Wave's hybrid solver is running in production at BASF, Volkswagen, Mastercard, and a growing list of logistics and financial services firms. The hardware has crossed the break-even threshold for specific optimization problem classes. The economics work today for the right workloads. The question is not "when will D-Wave be ready?" It is "which of my optimization problems are ready for D-Wave?"

Maria Gutierrez's routing firm did not need to wait for fault tolerance. It needed a model, a problem, and a pilot with outcome gates. The model revealed that the quantum economics were already favorable — not because the technology was exotic, but because the classical baseline had hidden costs that the vendor comparison ignored.

Build the model. Know your classical baseline — fully loaded, best available. Match platform to problem type. Monitor hardware milestones rather than press releases. And remember: the cheapest quantum strategy is the one that knows which of your workloads *should not* go quantum yet. Optionality compounds. The bank that declined the 2021 gate-model contract did not lose two years — it bought two years to build expertise without carrying the technical debt of premature commitment.

```{admonition} Chapter Summary
:class: note

- Quantum computing is a cloud service today. Five platforms compete for enterprise customers: D-Wave Leap (optimization, production-ready), IBM Quantum (gate-model development), AWS Braket (multi-vendor), Azure Quantum (Microsoft stack), Google Quantum AI (research partnerships).
- D-Wave's Stride hybrid solver runs production optimization workloads at BASF, Volkswagen, Mastercard, and others today. FAU's Advantage2 is the same hardware class.
- Quantum economics are not classical economics. True cost = shots × depth × error rate × queue time, divided by yield. For D-Wave, cost = jobs × solver time — simpler and more predictable.
- Physical-to-logical qubit overhead (currently ~1,000:1 for gate-model) makes headline qubit counts misleading. D-Wave annealing sidesteps this overhead for optimization workloads.
- TCO has six stages; QPU/solver time is typically the minority. Engineering, formulation, and validation costs dominate early-stage projects.
- Advantage, utility, and supremacy are not synonyms. Only advantage matters for production investment decisions.
- The break-even template separates stable workload parameters from volatile vendor parameters. Update the vendor block annually; never rebuild the model.
```
