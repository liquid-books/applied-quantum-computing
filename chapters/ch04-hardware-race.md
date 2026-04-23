---
title: "Chapter 4: The Hardware Race — Two Paradigms, Six Architectures"
subtitle: "Reading the Tea Leaves on Annealing, Superconducting, Trapped-Ion, Neutral-Atom, Photonic, and Topological Quantum Hardware"
short_title: "Ch. 4: The Hardware Race"
description: "There is no single quantum computer. Two distinct paradigms — annealing and gate-model — and six competing hardware architectures are racing toward commercial viability. FAU's Advantage2 annealing system is one of them. This chapter builds the vendor-neutral evaluation framework that works regardless of who wins."
label: ch-04-hardware-race
tags: [quantum hardware, annealing, D-Wave Advantage2, superconducting, trapped-ion, neutral-atom, photonic, topological, vendor evaluation, roadmap analysis, QUBO, FAU]
---

# Chapter 4: The Hardware Race — Two Paradigms, Six Architectures

:::{figure} ../images/ch04-explainer-infographic.png
:label: fig-ch04-explainer-infographic
:alt: Chapter 4 illustrated explainer infographic showing two quantum paradigms and six hardware architectures in a technology race
:width: 100%
:align: center

**Chapter 4 at a Glance.** Before you can evaluate any quantum vendor claim, you need to understand that quantum computing has two fundamentally different paradigms — annealing and gate-model — and six competing hardware architectures. One of those paradigms, running on FAU's campus, is production-ready today. The others are maturing toward fault tolerance on timelines measured in years to decades.
:::

The quantum hardware race is not about which qubit is "best." It is about which qubit is *best for your problem* — and whether you are asking the right question in the first place.

Most executives come to quantum hardware discussions with a single mental model: gate-model quantum computers, inspired by classical computers, manipulating qubits with sequences of quantum gates. This model is accurate but incomplete. There is a second paradigm — quantum annealing — that does not use gates at all, excels at an entirely different class of problems, and is already running in production at BASF, Volkswagen, and Mastercard. It is being installed on FAU's Boca Raton campus right now.

Understanding both paradigms — and knowing which one applies to your workload — is the most practically important hardware insight in this chapter. Everything else is framework.

---

## Opening Scene: Two Different Races

### The Betamax Parallel

The year is 1977. Sony's engineers are justifiably proud. Betamax cassettes deliver sharper picture resolution, better audio fidelity, and a more elegant form factor than the competing VHS format from JVC. In side-by-side technical tests, Betamax wins almost every metric.

You know how this story ends.

VHS captured longer recording time. Hollywood studios chose VHS for rental distribution. Once the installed base tipped, the game was over. Sony kept making better Betamax machines for years. They kept losing.

Today, five gate-model hardware architectures are making the same bet Sony made: *the technically superior technology will win*. History disagrees. In every major technology transition — VHS vs. Betamax, TCP/IP vs. OSI, AC vs. DC power — the winner was rarely the technically superior option at the moment of decision. Winners are shaped by ecosystem effects, manufacturing costs, regulatory support, and occasionally pure luck.

### The Parallel Race Nobody Mentions

Here is what the Betamax analogy misses: while five gate-model architectures race each other for the general-purpose quantum computing market, a sixth architecture — quantum annealing — is running a completely different race with completely different rules, against classical optimizers, not against gate-model systems.

D-Wave's Advantage2 annealer does not compete with IBM's Eagle processor the way Betamax competed with VHS. They are not targeting the same workload. An annealer solves combinatorial optimization problems — vehicle routing, manufacturing scheduling, portfolio construction — with a physical process that has no classical equivalent. A gate-model computer could theoretically solve the same problems using QAOA, but at current error rates and qubit counts, the gate-model approach cannot match the annealer's practical performance on production-scale problem instances.

This means the quantum hardware landscape is not a single race. It is two parallel contests:

1. **The Gate-Model Race:** Five architectures competing to reach fault-tolerant scale — the era when gate-model computers can run Shor's algorithm, accurate molecular simulation, and deep quantum ML. Timeline: late 2020s to mid-2030s.

2. **The Annealing Race:** D-Wave's Advantage2 vs. classical optimization software — a race that D-Wave's hybrid solver is already winning on specific workload classes. Timeline: now.

FAU has taken a position in the second race. That position, the \$20 million Advantage2 deployment, is not a bet on quantum computing's future. It is an investment in quantum computing's present.

---

## The Single Idea

```{epigraph}
There is no single "quantum computer." There are two fundamentally different quantum paradigms and six competing hardware architectures. The annealing paradigm is production-ready today. The gate-model paradigm is maturing toward fault tolerance. Learning which is which — and which applies to your workload — is the most important hardware skill in this course.
```

This chapter is not about memorizing qubit counts. It is about building the mental model that lets you evaluate any hardware claim from any vendor at any point in the next decade. The metrics do not change. The analytical rubric does not change. Only the numbers filling the rubric change.

---

## Part I: The Two Paradigms

Before examining individual architectures, you need to understand the fundamental split that most quantum introductions obscure.

:::{figure} ../images/ch04-two-paradigms.png
:label: fig-ch04-two-paradigms
:alt: Side-by-side comparison of quantum annealing and gate-model quantum computing paradigms, showing different physical approaches, problem classes, and commercial maturity
:width: 100%
:align: center

**Two Paradigms, One Field.** Quantum annealing and gate-model quantum computing use different physics to solve different problem classes on different timelines. The common mistake is evaluating them by the same metrics — like comparing a Formula 1 car to an off-road truck by top speed alone.
:::

### Paradigm 1: Quantum Annealing

Quantum annealing does not use quantum gates. Instead, it encodes an optimization problem as the energy landscape of a physical quantum system. The system begins in a superposition of all possible states simultaneously. It then slowly evolves — "anneals" — toward its lowest-energy configuration, using quantum tunneling to pass through energy barriers that would trap classical optimizers in locally good but globally suboptimal solutions.

The result: the physical state of the system, when measured, corresponds to a high-quality (often optimal or near-optimal) solution to the encoded problem.

**What types of problems does annealing solve?** Any problem that can be expressed as QUBO — Quadratic Unconstrained Binary Optimization. A QUBO is a cost function over binary variables (each variable is 0 or 1) that you want to minimize. A remarkable range of enterprise problems fits this description:

- Vehicle routing: which trucks take which routes to minimize total distance and time?
- Staff scheduling: which employees take which shifts to satisfy constraints and minimize cost?
- Portfolio construction: which assets in which proportions maximize return at a given risk level?
- Manufacturing sequencing: which machines process which jobs in which order to minimize throughput time?
- Fraud detection: which transaction patterns indicate coordinated fraud across a transaction graph?

**Current hardware:** D-Wave Advantage2 (7,000+ qubits, Pegasus topology) + Stride hybrid solver. FAU's on-campus system.

**Commercial maturity:** Production-ready for optimization workloads today. BASF, Volkswagen, Mastercard, Verge Ag running in production.

**Key limitation:** Purpose-built for optimization. Not a general-purpose computer. Cannot run quantum chemistry simulation, Shor's algorithm, or quantum ML.

---

### Paradigm 2: Gate-Model Quantum Computing

Gate-model quantum computers work more like classical computers. They initialize qubits, apply sequences of quantum gates to manipulate those qubits, and measure the result. The gates are the quantum equivalent of logic gates — they rotate qubit states, create superpositions, and generate entanglement.

Gate-model systems are general-purpose: in principle, any quantum algorithm can be expressed as a quantum circuit. In practice, the circuits required for commercially useful algorithms — molecular simulation, Shor's factoring, deep QAOA — require circuit depths, qubit counts, and error rates that today's hardware cannot reliably sustain.

The five architectures racing to solve these engineering challenges are: superconducting, trapped-ion, neutral-atom, photonic, and topological. Each uses different physics; each has different tradeoffs.

**Current hardware:** IBM (superconducting, up to 1,121 qubits), Google (superconducting, Willow 105 qubits), IonQ (trapped-ion), Quantinuum (trapped-ion), QuEra (neutral-atom), PsiQuantum (photonic, pre-commercial), Microsoft (topological, pre-commercial).

**Commercial maturity:** Research and near-term applications. No production deployments at gate-model equivalents of BASF or Volkswagen yet.

**Key strength:** General-purpose. Can run any quantum algorithm given sufficient qubits and fidelity.

---

:::{note} Plain Language: Annealing vs. Gate-Model for Executives

**Think of two different expert problem-solvers.**

A **quantum annealer** is like a world-class sommelier who has been training for thirty years to identify the best wine in any cellar. You show them the cellar (the problem), they explore it using their trained intuition (quantum tunneling), and they return with an excellent selection (a high-quality solution). Fast, accurate for its purpose, limited to wine problems.

A **gate-model quantum computer** is like a general-purpose genius who can solve any problem — if given sufficient time to learn the domain and write the algorithm. For a wine problem, they could match or beat the sommelier — eventually. For a molecular chemistry problem, only they can help. They are not production-ready for most tasks yet; the sommelier is.

**The practical implication:** For optimization problems that can be expressed as QUBO — logistics, scheduling, portfolio construction — the sommelier (D-Wave annealer) is available today, on FAU's campus, and delivering measurable ROI at BASF and Volkswagen. For quantum chemistry, QML, and cryptography applications — the genius (gate-model) is who you ultimately need, but you will need to wait while the engineering catches up.

Do not use the wrong expert for your problem.
:::

---

## Part II: The Evaluation Metrics

These five metrics apply to every hardware platform, every roadmap, and every vendor claim you will encounter. The metrics apply differently to annealing and gate-model systems — but both paradigms can be evaluated against some version of all five.

:::{list-table} The Five Metrics That Define Hardware Quality
:header-rows: 1
:widths: 20 25 30 25

* - Metric
  - Gate-Model Meaning
  - Annealing Meaning
  - Watch Out For
* - **Coherence Time** (T₁, T₂)
  - How long qubits stay quantum; limits circuit depth
  - Anneal time; controls solution quality vs. speed tradeoff
  - "Best qubit" vs. system average for gate-model
* - **Gate / Anneal Fidelity**
  - Error rate per gate operation
  - Solution quality vs. optimal; repeat-run consistency
  - Reported on best pairs, not all pairs (gate-model)
* - **Connectivity**
  - Which qubits can interact directly
  - Pegasus topology for Advantage2; affects QUBO embedding
  - Claimed vs. measured for gate-model; embedding overhead for annealing
* - **Qubit Count**
  - Physical qubits available
  - Physical qubits; ~7,000 on Advantage2 but not all available per problem
  - Physical ≠ logical for gate-model; embedding overhead for annealing
* - **Problem Scale**
  - Circuit depth + qubit count determines problem size
  - Variables + constraints in QUBO determines problem size
  - Both paradigms have practical limits far below headline specs
:::

:::{admonition} The Most Important Distinction in Quantum Hardware
:class: warning

**Physical qubits ≠ Logical qubits (gate-model)** and **Physical qubits ≠ Embedded variables (annealing).**

For gate-model systems: a physical qubit is raw, noisy hardware. A logical qubit requires ~1,000 physical qubits for error correction. When vendors announce qubit counts, they mean physical qubits.

For annealing systems: the Advantage2 has 7,000+ qubits, but embedding a QUBO problem onto the Pegasus topology requires multiple physical qubits per logical variable. A problem with 1,000 binary variables may require 3,000–5,000 physical qubits for embedding. The Stride hybrid solver sidesteps this limit for large problems by decomposing them classically.

Never use headline qubit counts as the primary metric for evaluating either paradigm.
:::

---

## Part III: D-Wave Advantage2 — The Production Annealing System

FAU's Advantage2 deserves a dedicated section. This is the hardware your coursework runs on. Understanding its architecture is not optional background — it is the foundation for Chapters 6 and every lab involving optimization.

:::{figure} ../images/ch04-dwave-advantage2-architecture.png
:label: fig-ch04-dwave-advantage2-architecture
:alt: D-Wave Advantage2 architecture diagram showing the Pegasus qubit topology, the dilution refrigerator housing, and the classical-quantum interface for the Stride hybrid solver
:width: 100%
:align: center

**D-Wave Advantage2 Architecture.** The Advantage2 QPU operates at 15 mK inside a dilution refrigerator, with 7,000+ superconducting flux qubits connected in the Pegasus topology. The Stride hybrid solver provides a classical-quantum interface that decomposes large problems into QPU-tractable subproblems.
:::

### The Physical Hardware

The Advantage2 QPU uses **superconducting flux qubits** — a different type of superconducting qubit than IBM or Google use. Where IBM's transmon qubits are designed for high-fidelity gate operations, D-Wave's flux qubits are designed for the annealing process: encoding a cost function as a magnetic energy landscape and letting the system find its lowest-energy state.

The Advantage2 contains **7,000+ flux qubits** connected in D-Wave's **Pegasus topology** — a 3D graph structure where each qubit connects to up to 15 neighbors. This connectivity pattern is denser than the Chimera topology of older D-Wave systems, enabling more complex QUBO problems to be embedded without excessive qubit overhead.

Like all superconducting systems, the Advantage2 QPU operates at **approximately 15 millikelvin** — colder than outer space. FAU's deployment includes the full dilution refrigerator infrastructure required for this cooling, housed in a dedicated facility on the Boca Raton campus.

### The Annealing Process

A computation on the Advantage2 follows a specific sequence:

1. **Problem encoding:** The QUBO cost function is translated into the physical energy parameters of the QPU — the bias of each qubit and the coupling strength between connected qubits pairs.
2. **Initialization:** All qubits are set to equal superposition (50% probability of being 0 or 1). This is the quantum starting state.
3. **Annealing:** The system slowly evolves from a quantum state (dominated by a transverse magnetic field that maintains superposition) toward a classical state (dominated by the problem-specific energy landscape). Quantum tunneling during this evolution allows the system to explore the solution landscape more efficiently than classical hill-climbing.
4. **Measurement:** At the end of the anneal, each qubit collapses to 0 or 1. The resulting bitstring represents one candidate solution.
5. **Sampling:** The anneal is repeated many times (default: 1,000 reads). The lowest-energy solution across all reads is returned as the best result.
6. **Post-processing:** Classical algorithms refine the QPU output.

A single anneal takes **20–200 microseconds**. Including programming, sampling, and readout, a complete QPU job typically runs in **1–10 milliseconds**.

### The Stride Hybrid Solver

For problems larger than the QPU can handle natively (most enterprise problems), D-Wave's **Stride hybrid solver** provides the production interface.

Stride operates as a classical orchestration layer that:
1. Receives a large QUBO problem (potentially millions of variables)
2. Decomposes it into subproblems that fit within the QPU's variable capacity
3. Submits each subproblem to the Advantage2 QPU via D-Wave Leap
4. Aggregates and coordinates QPU results using classical optimization
5. Iterates until a stopping criterion is met
6. Returns the best solution found

From the enterprise perspective, Stride looks like a black-box optimization solver: you submit a QUBO problem, you receive a solution in seconds to minutes. The quantum computation happens internally and automatically. No quantum circuit writing, no qubit management, no error mitigation.

**This is why BASF uses Stride for production manufacturing scheduling.** The operational interface is a classical API. The quantum advantage (faster exploration of large solution spaces through tunneling) happens transparently.

### Embedded vs. Logical Variables

When you submit a QUBO problem to the QPU directly (bypassing Stride), your problem variables must be *embedded* onto the Pegasus topology — each logical variable in your problem is represented by one or more physical qubits, depending on connectivity requirements. This embedding overhead means you can solve problems with fewer variables than the physical qubit count suggests.

**Practical rule of thumb:** The Advantage2 can handle QUBO problems with roughly 1,000–3,000 logical binary variables on the QPU directly. The Stride hybrid solver removes this limit — it handles millions of variables by decomposing the problem.

:::{admonition} The FAU Advantage
:class: important

FAU's on-premises Advantage2 deployment provides two advantages over cloud-only D-Wave Leap access:

1. **Latency:** Direct QPU access without cloud queuing. Iterate on QUBO formulations in seconds rather than waiting in shared queues. This is critical for research workflows that require rapid experimentation.
2. **Partnership:** D-Wave's corporate headquarters is four miles away at the Boca Raton Innovation Center. Direct access to D-Wave application engineers for problem formulation support, optimization tuning, and co-development. A benefit unavailable to cloud-only customers.
:::

---

## Part IV: The Five Gate-Model Architectures

::::{tab-set}

:::{tab-item} ⚡ Superconducting
### Superconducting Qubits: The Formula 1 Car

**The analogy:** A Formula 1 car is the fastest vehicle on the planet. It needs a pit crew of 50 people, controlled environment, and millions in infrastructure. Extraordinary performance, extraordinary support requirements.

Superconducting qubits operate at 15 millikelvin. At that temperature, certain metals lose all electrical resistance and enter a quantum state. Engineers create artificial "atoms" on a chip using standard semiconductor fabrication — called transmon qubits — controlled with microwave pulses. Gate operations execute in nanoseconds.

**Key players:** IBM (Eagle, Heron, Condor, Flamingo roadmap), Google (Sycamore, Willow), Rigetti, OQC, Alice & Bob

**Specs (2025):**
- Gate time: 10–100 ns (1Q), 100–500 ns (2Q)
- Coherence time: T₁ = 100–500 μs, T₂ = 50–300 μs
- Gate fidelity: 1Q ~99.9%, 2Q ~99–99.5%
- Scale: 100–1,000+ physical qubits
- Temp: 15 mK (dilution refrigerator required)

**Biggest milestone (Dec 2024):** Google's Willow processor demonstrated below-threshold error correction — the first time adding more qubits reduced rather than amplified error rates. The entire field has been waiting for this milestone.

**Best for:** Speed-critical applications, large qubit counts, IBM/Google ecosystem integration
**Biggest challenge:** Coherence, cooling infrastructure, manufacturing yield at scale
:::

:::{tab-item} 🔬 Trapped-Ion
### Trapped-Ion Qubits: The Swiss Watch

**The analogy:** A Swiss watch doesn't go 200 mph. But it keeps perfect time for 50 years without a pit crew, at room temperature, with extraordinary precision from a fundamentally stable system.

Trapped-ion systems use individual atoms (typically ytterbium or barium ions) levitated in a vacuum by electromagnetic fields. Natural atoms are identical — nature's quality control. Laser pulses perform gate operations with extraordinary precision. Gates are slower than superconducting but error rates are dramatically lower and coherence times are orders of magnitude longer.

**Key players:** IonQ (NYSE: IONQ), Quantinuum (Honeywell + Cambridge Quantum), Oxford Ionics

**Specs (2025):**
- Gate time: 1–10 μs (1Q), 50–500 μs (2Q)
- Coherence time: Seconds to minutes (T₂ > 10 s achievable)
- Gate fidelity: 1Q >99.99%, 2Q >99.9% (Quantinuum H2: 99.8%+)
- Scale: 20–56 physical qubits (current commercial)
- Temp: Room temperature (vacuum system + laser infrastructure)

**Best for:** High-fidelity circuits, quantum chemistry, financial optimization, near-term quantum advantage
**Biggest challenge:** Gate speed, scaling beyond ~100 qubits in a single ion chain
:::

:::{tab-item} ⚛️ Neutral-Atom
### Neutral-Atom Qubits: The Programmable Grid

Neutral-atom systems use arrays of uncharged atoms held by optical tweezers — focused laser beams trapping individual atoms at programmable positions. Atoms are neutral, so they don't interact strongly by default (easy to isolate). Entanglement is created by temporarily exciting atoms to high-energy Rydberg states where they interact strongly.

**The defining advantage:** Reconfigurability. Unlike fixed-chip architectures, neutral-atom systems can physically rearrange their qubits mid-computation, creating arbitrary connectivity on demand. This dramatically reduces compilation overhead for certain algorithm classes.

**Key players:** QuEra (Harvard spinout), Pasqal, Atom Computing

**Specs (2025):**
- Gate time: ~0.5–5 μs (1Q), ~0.5–10 μs (2Q via Rydberg)
- Coherence time: ~1–10 s (nuclear spin qubits can reach minutes)
- Gate fidelity: 1Q ~99.5%, 2Q ~99–99.5% (improving rapidly)
- Scale: 256–10,000+ physical atoms
- Temp: Microkelvin (laser cooling only — no dilution fridge)

**Landmark (2023):** QuEra's 48-logical-qubit demonstration — the first time any platform demonstrated that many error-corrected logical qubits running algorithms. The field is watching this space closely.

**Best for:** Combinatorial optimization, analog simulation, quantum networking, large variational algorithms
**Biggest challenge:** Gate speed, fidelity at scale, deterministic atom loading
:::

:::{tab-item} 💡 Photonic
### Photonic Qubits: Room Temperature, Network Native

Photonic quantum computers encode quantum information in individual photons. Photons travel at the speed of light, don't interact with the environment in ways that cause decoherence, and can be transmitted over optical fiber. These properties make photonic systems uniquely suited for quantum communication and networking.

**Key players:** PsiQuantum (silicon photonics manufacturing bet), Xanadu (PennyLane), QuiX Quantum

**The manufacturing bet:** PsiQuantum has raised over \$700 million on the thesis that GlobalFoundries' silicon photonics manufacturing process can produce millions of photonic qubits — leapfrogging all other architectures at scale. If manufacturing yields hit targets, the approach is transformative. If not, the capital may be unrecoverable.

**Specs:**
- Operating temp: Room temperature (no dilution fridge)
- Coherence: Very long (photons don't thermalize easily)
- Computation model: Measurement-based (different from circuit model)
- Current scale: Small (PsiQuantum's bet is on manufacturing scale, not today's demos)

**Best for:** Quantum networking, quantum key distribution, distributed quantum computation
**Biggest challenge:** Deterministic single-photon sources, photon loss in gates
:::

:::{tab-item} 🔮 Topological
### Topological Qubits: Highest Risk, Highest Reward

Topological quantum computers would encode information in exotic quantum states — Majorana zero modes — where the information is stored in the *topology* of a quantum state rather than the state of any individual particle. Local disturbances cannot corrupt topological information: it is like writing a message in a knot — you cannot accidentally change what the knot *is* without deliberately cutting and retying it.

**Key players:** Microsoft (primary backer, Azure Quantum roadmap)

**Status (2025):** Microsoft published a *Nature* paper in February 2025 claiming to have observed Majorana zero modes on a semiconductor nanowire. The result triggered significant scientific scrutiny — independent replication is ongoing. Commercial viability: 5–10+ years.

**If it works:** Topological systems could achieve fault-tolerant computation with 10–100× fewer physical qubits than surface codes require — compressing the timeline to practical utility dramatically. That is the bet.

**Best for:** If validated — all-purpose fault-tolerant computation with dramatically lower overhead
**Biggest challenge:** Fundamental physics still being validated; materials fabrication; gate implementation
:::
::::

---

## Part V: Reading a Roadmap Like an Analyst

Quantum vendor roadmaps are movie trailers. They show the best-case demos. They use "demonstrated" for things that happened and "targets" and "plans" for things that haven't. The difference between those two categories is enormous — and easy to miss when you're excited.

:::{figure} ../images/ch04-roadmap-reading-framework.png
:label: fig-ch04-roadmap-reading-framework
:alt: Quantum vendor roadmap analysis framework showing green-yellow-red evaluation rubric applied to timeline milestones
:width: 100%
:align: center

**The Roadmap Reading Framework.** Every roadmap claim falls into one of three categories: demonstrated (trust), announced (verify), or projected (discount). Apply this rubric to any vendor's roadmap to get a calibrated view of near-term, mid-term, and speculative capability.
:::

### The Evergreen Roadmap Rubric

:::{list-table} Roadmap Evaluation Rubric
:header-rows: 1
:widths: 25 25 25 25

* - Claim Type
  - ✅ Green (Trust)
  - 🟡 Yellow (Verify)
  - 🔴 Red (Discount)
* - **Achievement language**
  - "Demonstrated," "published," "peer-reviewed"
  - "Announced," "showed," internal report
  - "Plans to," "expects to," "targeting"
* - **Fidelity claims**
  - Best-pair AND system-average reported
  - Best-pair only, with caveats
  - No fidelity reported; qubit count only
* - **Timeline**
  - Milestone already delivered
  - 6–18 months with named dependencies
  - 2+ years, vague dependencies
* - **Demo scope**
  - Full-system benchmark on standard circuit
  - Subsystem demo extrapolated to system
  - Theoretical projection, no hardware demo
* - **D-Wave specific**
  - Production deployment named, metrics cited
  - Pilot completion announced
  - Advantage projected from lab benchmark
:::

### The Five Red Flags

1. **Qubit count without fidelity.** A million low-fidelity qubits are worth less than 100 high-fidelity ones. Always ask for system-average two-qubit gate error rate.
2. **"Quantum advantage" without specification.** Advantage over *what*, on *which problem*, measured *how*? Unspecified claims are marketing.
3. **Demo on one algorithm.** A system optimized for one benchmark may perform very differently on your workload. Ask for benchmarks on your use-case class.
4. **The hockey stick at year 3.** Roadmaps that show flat progress through years 1–2 then sudden vertical climb at year 3 deserve scrutiny. Quantum engineering compounds; it doesn't hockey stick.
5. **"Logical qubits" without overhead.** Ask how many physical qubits each logical qubit costs. A 1,000-qubit system at 1,000-to-1 overhead has one logical qubit. That is a milestone — not a commercial platform.

---

## Part VI: Matching Hardware to Workload

The paradigm and architecture that is right for drug simulation is wrong for logistics routing.

:::{figure} ../images/ch04-workload-matching.png
:label: fig-ch04-workload-matching
:alt: Workload-to-hardware matching matrix showing which quantum hardware paradigm and architecture is best suited to different enterprise use cases across axes of problem type and timeline
:width: 100%
:align: center

**Matching Hardware to Workload.** The most common and most expensive quantum strategy mistake is using the wrong hardware paradigm for a given problem. Annealing (D-Wave) for today's optimization problems. Gate-model for tomorrow's simulation and cryptographic applications.
:::

:::{list-table} Paradigm-to-Workload Matching Guide
:header-rows: 1
:widths: 28 20 22 15 15

* - Workload Type
  - Paradigm
  - Best Architecture
  - Timeline
  - FAU Hardware?
* - Vehicle routing, scheduling
  - **Annealing**
  - D-Wave Advantage2
  - Now
  - ✅ Yes
* - Portfolio optimization
  - **Annealing** (near-term); Gate-model (future)
  - D-Wave Stride; Superconducting (QAOA)
  - Now / 2027+
  - ✅ Yes
* - Manufacturing sequencing
  - **Annealing**
  - D-Wave Advantage2
  - Now
  - ✅ Yes
* - Drug simulation (molecular)
  - Gate-model
  - Trapped-ion, Neutral-atom
  - 2026–2030
  - ❌ No
* - Battery / materials chemistry
  - Gate-model
  - Superconducting, Trapped-ion
  - 2028–2033
  - ❌ No
* - Quantum ML / classification
  - Gate-model
  - All (algorithm-dependent)
  - Speculative / research
  - ❌ No
* - RSA / cryptographic break
  - Gate-model (fault-tolerant)
  - Superconducting (Shor's)
  - 2035+
  - ❌ No
* - Quantum networking / QKD
  - Photonic
  - Photonic
  - Available now (limited)
  - ❌ No
:::

---

## Part VII: The Portfolio Approach

:::{admonition} Mental Model: Your Quantum Strategy Is a Seed Fund
:class: important

A well-managed venture capital seed fund doesn't bet everything on one startup. It takes 20–30 positions, tracks leading indicators, has pre-defined kill-switch criteria, and rebalances annually.

Your quantum hardware strategy should work the same way. Diversify across paradigms and architectures. Define kill-switch criteria before you deploy capital. Rebalance annually as the landscape shifts.
:::

### Suggested Portfolio Allocation by Risk Tolerance

::::{grid} 1 1 3 3
:::{grid-item-card} Conservative

**🛡️ Conservative**

- **D-Wave Leap** cloud access — production optimization pilots
- **IBM Quantum** free tier — gate-model literacy
- Monitor neutral-atom progress

*Cloud API access only. No hardware procurement. Build QUBO and gate-model skills now.*
:::
:::{grid-item-card} Balanced

**⚖️ Balanced**

- **D-Wave Stride** service contract — production workloads
- **IBM/IonQ** service — gate-model pilots
- **Neutral-atom** early access program
- Monitor photonic and topological

*Workload-specific pilots. Multiple backends. Explicit kill-switch criteria.*
:::
:::{grid-item-card} Aggressive

**🚀 Aggressive**

- **On-premises annealing** (like FAU) — production + research
- **Trapped-ion** private placement consideration
- **Neutral-atom** early access
- **Photonic** strategic monitoring position
- **Topological** watch brief

*Long-term positioning, talent acquisition, 5–10 year horizon.*
:::
::::

### Kill-Switch Criteria

Define before deploying capital:

1. **Technical:** "If [platform] fails to achieve [target] by [date], reduce allocation by [X%]"
2. **Commercial:** "If no ROI demonstrated in [industry] by [date], exit service contracts"
3. **Competitive:** "If competing paradigm achieves [threshold], shift [X%] from this position"

---

## Flagship Case Study: A Sovereign Wealth Fund's Quantum Hardware Portfolio

In early 2023, a \$400 billion sovereign wealth fund's technology investment committee convened to develop a formal quantum computing strategy. Peer SWFs in Singapore, Norway, and the Gulf Cooperation Council were beginning to take positions in quantum hardware companies. The committee faced a fundamental challenge: no single quantum hardware approach had yet demonstrated commercial advantage at scale — and waiting for a winner risked missing the early-mover benefits.

**The Committee's Framework**

The Quantum Technology Working Group (QTWG) rejected the standard technology investment rubric (revenue growth, market share, gross margin — irrelevant for pre-commercial platforms). Instead they built a proprietary scoring rubric based on:

- **Milestone velocity:** How quickly was each platform advancing on the five key technical metrics?
- **Roadmap credibility:** What fraction of past roadmap commitments had been delivered on schedule?
- **Ecosystem depth:** Were industry partners, algorithm developers, and government programs anchoring around this platform?
- **Paradigm fit:** Were near-term commercial applications available now (annealing) or speculative future (gate-model)?

**Portfolio Structured in Three Tiers**

*Tier 1 — Public Equity (\$800M):* IBM (\$500M — superconducting roadmap credibility and cloud infrastructure) + IonQ (\$300M — trapped-ion fidelity advantages)

*Tier 2 — Private Placements (\$250M):* PsiQuantum (\$150M — manufacturing thesis, high-risk) + Quantinuum (\$100M — strongest fidelity track record, pharmaceutical enterprise contracts)

*Tier 3 — Service Contracts (\$50M over 3 years):* IBM Quantum Network + Quantinuum H-Series cloud + QuEra early-access + **D-Wave Leap enterprise** (added in 2024 rebalancing after BASF deployment validation)

**The 18-Month Rebalancing**

By Q3 2024, the QTWG's kill-switch criteria triggered a rebalancing. PsiQuantum's manufacturing yields missed internal targets — the QTWG reduced the position from \$150M to \$80M, preserving \$70M for redeployment. QuEra's 48-logical-qubit demonstration exceeded expectations — the QTWG increased their neutral-atom position. D-Wave's BASF production deployment was independently validated — a D-Wave Leap enterprise contract was added to Tier 3.

**Open Question**

The QTWG's June 2025 committee meeting faces a question with no clean answer: should the photonic position be exited entirely (kill-switch criteria triggered) or maintained (management argues 12-month slip, not failure)? The kill-switch exists precisely to prevent sunk-cost thinking. The data says apply it. Sentiment says wait.

What would you recommend?

---

## Productive-Struggle Problem

:::{admonition} Three Redacted Roadmaps
:class: important

Using the chapter's evaluation rubric, rank these three anonymized vendor roadmaps by plausibility and commercial relevance. Flag every line between demonstrated and promised capability.

**Vendor A:**
- "Achieved 500-qubit system with average 2Q gate error rate of 0.8% (2022)" — *internal benchmark, not peer-reviewed*
- "Delivered 1,000-qubit system (2023)" — *press release*
- "Demonstrated quantum advantage on portfolio optimization (2023)" — *problem size and classical baseline unspecified*
- "Plans 10,000-qubit system with 0.1% error rate by 2026"

**Vendor B:**
- "Published 2Q gate fidelity of 99.5% on 25-qubit system in Nature (2022)" — *peer-reviewed*
- "Demonstrated 35 algorithmic qubits with 99.6% average 2Q fidelity (2023)" — *independent benchmarking confirmed*
- "40-qubit system in customer access (2024)"
- "100 physical qubits (2025 target); 1,000 with photonic interconnects (2028)"

**Vendor C (Annealing):**
- "Production deployment at BASF: manufacturing scheduling from 4 hours to 90 seconds (2023)" — *press release; BASF confirmed publicly*
- "7,000+ qubit Advantage2 system; Pegasus topology (2024)" — *published specs*
- "Stride hybrid solver handles problems with millions of variables (2024)" — *Volkswagen, Mastercard named as production customers*
- "On-premises installation at FAU Boca Raton (2026)" — *announced Qubits26*

Rank the three vendors. Apply the rubric. For each: what is the strongest evidence for their claims, what is the biggest unresolved question, and what kill-switch criterion would you set?
:::

:::{dropdown} Answer Key

**Ranking: C > B > A**

**Vendor C (Annealing):** Highest near-term commercial credibility. Every production claim has a named customer who confirmed it publicly. The BASF and Volkswagen deployments are independently verifiable. The FAU installation is a matter of public record. Vendor C's claims are specific, falsifiable, and verified. The unresolved question: does the annealing advantage persist as classical optimization software improves? Kill-switch: "If a specific classical solver matches Stride's solve time and quality on the same BASF problem class within 18 months, reduce annealing service contract."

**Vendor B (Trapped-Ion):** Strong near-term credibility from peer-reviewed fidelity data and independent benchmarking. The photonic interconnect dependency for 2028 scale is real and hard — but the roadmap acknowledges it rather than hiding it. Near-term claims are verifiable; mid-term claims are aggressive but traceable. Kill-switch: "If 2Q fidelity does not reach 99.7% system-average by Q4 2026, reduce Tier 2 position."

**Vendor A (Gate-Model):** Lowest plausibility. Internal benchmark without peer review. "Quantum advantage" claim with no specified problem size or classical baseline — the cardinal sin of quantum marketing. The 2026 targets require simultaneous 10× improvements in fidelity and qubit count — implausible given industry trajectory. Kill-switch triggers immediately: no independent verification of any claim.

**The meta-lesson:** Vendor C — the annealing system — ranks highest because it has the most verifiable production evidence. Vendor A — the gate-model system with the biggest qubit count claim — ranks lowest because it has the least verifiable evidence. Headline qubit count is inversely correlated with roadmap credibility in this example. That is not always true, but it is true often enough to be a useful prior.
:::

---

## Module-Level Outcomes

By completing this chapter, you can:

::::{grid} 1 1 2 2
:::{grid-item-card} Outcome 1
**Paradigm Distinction**

Distinguish quantum annealing from gate-model quantum computing: different physics, different problem classes, different commercial timelines. Explain why D-Wave's Advantage2 is production-ready today while gate-model systems remain in research/near-term deployment.
:::

:::{grid-item-card} Outcome 2
**D-Wave Architecture**

Describe the Advantage2 architecture — flux qubits, Pegasus topology, annealing process, Stride hybrid solver — at a level sufficient to evaluate vendor claims and formulate optimization problems for submission.
:::

:::{grid-item-card} Outcome 3
**Gate-Model Modalities**

Compare the five gate-model architectures on coherence time, gate fidelity, scalability, connectivity, and operating requirements — identifying the tradeoffs each makes and the workloads each is best suited for.
:::

:::{grid-item-card} Outcome 4
**Roadmap Reading**

Apply the evergreen roadmap rubric to any vendor claim, distinguishing demonstrated milestones from marketing projections and flagging the five red flags.
:::

:::{grid-item-card} Outcome 5
**Hardware-Workload Matching**

Given a business workload, select the appropriate quantum paradigm (annealing vs. gate-model) and architecture, justify the selection using the matching framework, and set kill-switch criteria for the recommendation.
:::
::::

---

## Lab 4 (Regular): Comparing Quantum Backends — IBM and D-Wave

**Duration:** ~60 minutes | **Platforms:** IBM Quantum + D-Wave Leap (both free tier)  
**Deliverable:** Backend Selection Memo

### Overview

You will evaluate quantum hardware from both paradigms — IBM gate-model and D-Wave annealing — using the chapter's evaluation rubric. The goal is to experience the operational difference between paradigms and apply the rubric to real hardware, not manufacturer slides.

### Part 1: IBM Gate-Model Backend Evaluation

1. Log into [quantum.ibm.com](https://quantum.ibm.com) (free account)
2. In Quantum Composer, build a 3-qubit GHZ state: H gate on qubit 0 → CNOT (0→1) → CNOT (0→2) → Measure all
3. Run on two available backends — pick one with more qubits, one with lower reported error rate
4. Record for each backend:

| Field | Backend 1 | Backend 2 |
|---|---|---|
| Name | | |
| Qubit count | | |
| T₁ avg (μs) | | |
| T₂ avg (μs) | | |
| 2Q error rate (avg) | | |
| GHZ fidelity (your run) | | |
| Queue time | | |

### Part 2: D-Wave Annealing Backend Evaluation

1. Log into [cloud.dwavesys.com](https://cloud.dwavesys.com) (free developer account)
2. Navigate to Examples — run a **graph coloring** or **job scheduling** sample on the Leap hybrid solver
3. Record:

| Field | D-Wave Stride |
|---|---|
| Problem type | |
| Problem size (variables) | |
| Solve time (seconds) | |
| QPU access time (μs, from timing breakdown) | |
| Solution quality (valid? best found?) | |
| Compute time used (from dashboard) | |

### Part 3: Apply the Rubric

For each of the three backends (2 IBM + 1 D-Wave), fill in the evaluation rubric:

| Metric | IBM Backend 1 | IBM Backend 2 | D-Wave Stride |
|---|---|---|---|
| Coherence (1–5) | | | N/A (annealing) |
| Fidelity/accuracy (1–5) | | | (solution quality) |
| Problem scale fit | | | |
| Queue time | | | |
| Best suited for | | | |

### Deliverable: Backend Selection Memo

One page (400–500 words):
1. **Which backend performed best for the task you ran, and why?**
2. **Paradigm comparison:** For a logistics company needing to optimize 200-truck routing daily, which paradigm and platform would you recommend? Which would you *not* recommend, and why?
3. **Kill-switch criterion:** Write one specific, measurable kill-switch criterion for each platform you recommend.

---

## Lab 4 (Optional Advanced): Automated Backend Benchmarking Suite

<a href="https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch04-backend-benchmarking.ipynb" target="_blank">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="margin-bottom: 1rem;"/>
</a>

Build an automated tool that queries IBM Quantum backends, pulls live calibration data, runs a standardized GHZ benchmark, computes a composite Quality Score, and outputs a ranked Backend Report Card. Then extend to compare a D-Wave hybrid solver job using the same optimization problem submitted both to D-Wave and a classical solver.

**Quality Score Formula:**

$$QS = 0.35 \cdot \frac{T_2}{T_{2,\text{max}}} + 0.40 \cdot \left(1 - \frac{e_{2Q}}{e_{2Q,\text{max}}}\right) + 0.25 \cdot F_{\text{GHZ}}$$

**Deliverable:** Working Python script + Backend Report Card + 500-word memo comparing gate-model and annealing performance characteristics on their respective problem classes.

---

## Discussion Guidelines

Post 350–500 words. Cite at least two sources. Respond substantively to two peers.

:::{admonition} Discussion Prompt
:class: note

The chapter argues that quantum annealing (D-Wave) and gate-model quantum computing are parallel paradigms solving different problem classes — not competing approaches racing to the same finish line.

Do you agree? Make the strongest possible case for or against this framing. Then address: if you were advising FAU's provost on how to use the Advantage2 system to generate research outcomes with commercial relevance in the next 3 years, what problem domain would you recommend prioritizing, and why? What classical baseline would you benchmark against?
:::

---

## Glossary

**Quantum Annealing** — A quantum computing paradigm that encodes optimization problems as the energy landscape of a quantum system and uses quantum tunneling to find low-energy (high-quality) solutions. D-Wave's approach. Purpose-built for QUBO optimization problems.

**Gate-Model Quantum Computing** — A quantum computing paradigm that manipulates qubits using sequences of quantum gates, analogous to classical logic gates. General-purpose. IBM, Google, IonQ, Quantinuum, QuEra, PsiQuantum, Microsoft all pursue gate-model approaches.

**D-Wave Advantage2** — D-Wave's current flagship quantum annealing processor. 7,000+ flux qubits in Pegasus topology. FAU's on-campus system. Paired with the Stride hybrid solver for enterprise optimization.

**Flux Qubit** — A superconducting qubit type used by D-Wave, implemented as a superconducting loop interrupted by Josephson junctions. Designed for annealing, not gate-model computation. Different from IBM's transmon qubits.

**Pegasus Topology** — The qubit connectivity graph of the D-Wave Advantage2. Each qubit connects to up to 15 neighbors in a 3D graph structure. Denser than older D-Wave topologies, enabling more complex QUBO embeddings.

**QUBO** — Quadratic Unconstrained Binary Optimization. The mathematical problem format native to quantum annealers. A wide range of business optimization problems — routing, scheduling, portfolio construction — can be expressed as QUBO.

**Stride Hybrid Solver** — D-Wave's production classical-quantum hybrid solver. Decomposes large QUBO problems into subproblems for the QPU, coordinates results classically, and returns solutions in seconds to minutes. Handles problems with millions of variables.

**Coherence Time** — How long a qubit maintains its quantum state. Measured as T₁ (energy relaxation) and T₂ (dephasing). Determines maximum useful circuit depth for gate-model systems. T₂ ≤ 2T₁ always.

**Gate Fidelity** — The probability a quantum gate performs correctly. Expressed as a percentage. 1Q (single-qubit) and 2Q (two-qubit) fidelities tracked separately; 2Q is harder and typically lower.

**Physical Qubit** — Raw hardware qubit. Noisy and imperfect. The unit vendors advertise.

**Logical Qubit** — Error-corrected qubit built from ~1,000 physical qubits. The unit relevant for fault-tolerant gate-model computation.

**Transmon Qubit** — A superconducting qubit type used by IBM and Google, based on a Josephson junction shunted by a large capacitor to reduce charge noise. Used for gate-model computation.

**Superconducting Qubit** — A qubit implemented using superconducting circuits operating at ~15 mK. Used by IBM (transmon), Google (transmon), and D-Wave (flux). Different subtypes for different paradigms.

**Trapped-Ion Qubit** — A qubit using internal electronic states of levitated ions. Very high fidelity, long coherence, slower gates. Used by IonQ and Quantinuum.

**Neutral-Atom Qubit** — A qubit using internal states of neutral atoms held by optical tweezers. Reconfigurable connectivity, scales to thousands of atoms. Used by QuEra and Pasqal.

**Photonic Qubit** — A qubit encoded in photons. Room temperature, network-native. PsiQuantum's manufacturing bet.

**Topological Qubit** — A theoretical qubit using Majorana zero modes for inherent error protection. Microsoft's primary quantum research direction. Still in experimental validation.

**Surface Code** — The most widely studied quantum error correction code. ~1,000 physical qubits per logical qubit at current error rates. Most gate-model fault-tolerance roadmaps target surface code implementation.

**Kill-Switch Criterion** — A pre-defined, objective trigger that mandates reducing or exiting an investment position. Prevents sunk-cost thinking in hardware portfolio management.

**Roadmap Credibility** — The fraction of a vendor's past roadmap commitments delivered on schedule. The most durable leading indicator of future roadmap reliability.

---

## Going Deeper (Optional): Coherence, Fidelity, and the Ising Hamiltonian

*This section is for readers with a STEM background. Not required for course assessments.*

### Coherence Time: The Clock Ticking Against Your Algorithm

Every gate-model qubit has two critical timescales:

- **$T_1$ (relaxation time):** How long before a qubit in state $|1\rangle$ spontaneously decays to $|0\rangle$. Typical superconducting values: 100–500 microseconds on current IBM Eagle/Heron processors.
- **$T_2$ (dephasing time):** How long before a qubit's phase relationship (the $e^{i\phi}$ term in the Bloch sphere representation) becomes randomized due to environmental noise. Always $T_2 \leq 2T_1$.

A quantum algorithm must complete all its operations within $T_2$. Gate execution times are on the order of 10–100 nanoseconds, so modern processors can execute approximately $T_2 / t_{\text{gate}} \sim 10{,}000$ gates before decoherence destroys the computation. Fault-tolerant quantum computing requires extending this to billions of logical gate operations — hence the enormous engineering challenge.

### Gate Fidelity

**Fidelity** measures how accurately a gate operation is performed. A single-qubit gate fidelity of 99.9% means 1 in 1,000 operations introduces an error. Two-qubit gate fidelity is typically lower: 99.0–99.5% on best-in-class hardware. For a circuit with $d$ gates in sequence, the total fidelity scales roughly as $F_{\text{total}} \approx f^d$, where $f$ is the per-gate fidelity. For $d = 100$ gates at $f = 0.999$: $F \approx 0.999^{100} \approx 0.905$. At $d = 1{,}000$: $F \approx 0.37$. This is why NISQ algorithms are limited to shallow circuits.

*In plain terms: Errors compound like a bad telephone game. If each gate is 99.9% accurate, running 100 gates gives you a 90.5% chance the final answer is right. Run 1,000 gates and you're down to 37% — barely better than a coin flip. This is exactly why today's quantum computers can only run short programs, and why fault tolerance (the ability to run millions of gates) is such a critical milestone.*

### The D-Wave Ising Hamiltonian

D-Wave's approach is fundamentally different: rather than applying gate sequences, it implements a physical **Hamiltonian** — an energy function — directly in hardware:

$$H = -\sum_{i} h_i \sigma_i^z - \sum_{i<j} J_{ij} \sigma_i^z \sigma_j^z$$

*In plain terms: This is the D-Wave energy landscape encoded as physics. Each qubit ($i$) has a personal "preference" ($h_i$) for being spin-up or spin-down. Each pair of connected qubits has a "relationship" ($J_{ij}$) — they either like to agree or like to disagree. The whole system naturally settles into the lowest-energy state, like a ball rolling downhill. That lowest-energy state is the answer to your optimization problem. You don't program D-Wave — you describe the energy landscape of your problem, and physics solves it for you.*

Where $\sigma_i^z$ is the Pauli-Z operator for qubit $i$, $h_i$ are local biases (linear coefficients), and $J_{ij}$ are qubit-qubit couplings (quadratic coefficients). Finding the ground state of this Hamiltonian — the minimum energy configuration — is exactly equivalent to solving a QUBO problem (Chapter 6). The Advantage2 chip has ~5,000 qubits and over 40,000 couplers physically implemented in superconducting metal.

The annealing process evolves from a transverse-field Hamiltonian (all qubits in superposition) to the problem Hamiltonian over a controllable anneal time (1–2,000 microseconds). The system exploits quantum tunneling — the ability to pass through energy barriers rather than climb over them — to find low-energy solutions. Coherence is not required to be preserved for the full computation; the annealing process is robust to thermal noise in ways gate-model circuits are not, which is why D-Wave hardware operates at a higher temperature (15 mK) than some gate-model systems while still delivering commercial optimization results.

### Connection to Chapter Content

The hardware comparison in this chapter — coherence times, qubit counts, fidelity benchmarks — is the engineering translation of the Hamiltonians and timescales above. When you evaluate a quantum vendor on "error rates," you are asking about $f$ in the gate fidelity formula. When you ask "how many logical qubits," you are asking how many physical qubits survive the error correction overhead.

---

## Leader's Takeaway

```{epigraph}
Don't fall in love with a qubit. Fall in love with a workload, and let the hardware earn its place.
```

The Betamax lesson is not that better technology loses. It is that "better" is always relative to a specific set of criteria, at a specific moment, in a specific ecosystem. The criteria change. The ecosystem changes.

Two quantum paradigms are running two different races. The annealing race — D-Wave's Advantage2 vs. classical optimization software — has a winner in specific workload classes. That winner is running in production at BASF, Volkswagen, and Mastercard, and it is being installed on this campus.

The gate-model race — five architectures competing to reach fault-tolerant scale — has no winner yet. Google's Willow milestone in December 2024 is the most significant hardware progress in a decade, and it confirms the pathway is physically real. But fault-tolerant gate-model quantum computing is still a 2030s story for most commercially relevant applications.

The executive who understands both races — who can evaluate any roadmap, apply the fidelity rubric, match hardware to workload, and build a portfolio with kill-switch criteria — is not the one who picks the right horse. They are the one who built the system to re-evaluate the race every twelve months.

Build the framework. Apply it consistently. Let the hardware prove itself against your criteria, not against its own press releases.

```{admonition} Chapter Summary
:class: note

- Quantum computing has two paradigms: **annealing** (D-Wave, production-ready for optimization today) and **gate-model** (five architectures, maturing toward fault tolerance).
- FAU's Advantage2 is a D-Wave annealing system — not a gate-model computer. It excels at QUBO optimization problems: routing, scheduling, portfolio construction, manufacturing sequencing.
- The Stride hybrid solver is the enterprise interface: submit a QUBO problem, receive a solution in seconds. No quantum circuit writing required.
- The five gate-model architectures — superconducting, trapped-ion, neutral-atom, photonic, topological — each make different tradeoffs. Superconducting is fastest; trapped-ion is most accurate; neutral-atom is most reconfigurable; photonic is network-native; topological remains experimental.
- The Roadmap Rubric: demonstrated (peer-reviewed, named customer) > announced (press release) > projected (targeted, planned). Apply it to every vendor claim.
- Match hardware to workload before choosing a platform. Use annealing for today's optimization. Use gate-model for chemistry, cryptography, and QML research.
- Portfolio approach with kill-switch criteria prevents sunk-cost thinking in a rapidly evolving landscape.
```
