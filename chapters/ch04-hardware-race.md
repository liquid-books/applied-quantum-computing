---
title: "Chapter 4: The Quantum Hardware Race — Reading the Tea Leaves"
subtitle: "Five Architectures, One Evaluation Framework, Zero Brand Loyalty"
short_title: "Ch. 4: The Hardware Race"
description: "There is no single quantum computer. Five competing hardware architectures are racing toward commercial viability — each with different physics, failure modes, and timelines. This chapter gives you the vendor-neutral evaluation framework that works regardless of who wins."
label: ch-04-hardware-race
tags: [quantum hardware, superconducting, trapped-ion, neutral-atom, photonic, topological, vendor evaluation, roadmap analysis]
---

# Chapter 4: The Quantum Hardware Race — Reading the Tea Leaves

:::{figure} ../images/ch04-explainer-infographic.png
:name: ch04-explainer-infographic
:alt: Chapter 4 illustrated explainer infographic showing five quantum hardware architectures in a race
:width: 100%

**Chapter 4 at a Glance.** Five physical architectures — superconducting, trapped-ion, neutral-atom, photonic, and topological — are competing to become the dominant quantum computing platform. This chapter gives you the vendor-neutral rubric to evaluate all of them, regardless of who is currently leading.
:::

The quantum hardware race isn't about which qubit is "best." It's about which qubit is *best for your problem* — and which vendor's roadmap you can actually trust. By the end of this chapter, you'll have the evaluation framework to answer both questions, regardless of who is currently winning.

---

## Opening Scene: Betamax Was Better. It Still Lost.

The year is 1977. Sony's engineers are justifiably proud. Betamax cassettes deliver sharper picture resolution, better audio fidelity, and a more elegant form factor than the competing VHS format from JVC. In side-by-side technical tests, Betamax wins almost every metric.

You know how this story ends.

VHS captured a longer recording time — initially four hours versus Betamax's one hour. Hollywood studios chose VHS for rental distribution. Once the installed base tipped toward VHS, the game was over. Sony kept making better Betamax machines for years. They kept losing.

Today, five quantum hardware camps are making the same bet Sony made: *the better technology will win.*

History disagrees. In every major technology transition — VHS vs. Betamax, TCP/IP vs. OSI, AC vs. DC power — the winner was rarely the technically superior option at the moment of decision. Winners are shaped by ecosystem effects, manufacturing costs, regulatory support, and occasionally pure luck.

The executive who studied only technical specs in 1977 bought a Betamax factory. The executive who studied *adoption dynamics* made money on VHS.

You are here to become the second kind of executive.

---

## The Single Idea

:::{admonition} Core Thesis
:class: important

There is no single "quantum computer." There are **five competing physical architectures**, each with different failure modes, cost curves, and commercial windows. The vendor leaderboard will change every year. The **criteria by which you evaluate the leaderboard** will not. Learn the criteria.
:::

This chapter is not about memorizing which company has the most qubits today. That number will be obsolete before this page loads. This chapter is about building the mental model that lets you evaluate *any* hardware claim, from *any* vendor, at *any* point in the next decade.

Think of it like learning to read financial statements. You don't need to memorize Apple's revenue from last quarter. You need to know what revenue, margin, and cash flow *mean* — so you can evaluate any company, any time.

---

## Why Are There Five Different Approaches?

::::{admonition} 🎓 9th Grader Test: Why So Many Hardware Types?
:class: tip

**Start with what you know:** Think about cars. You can get from New York to Miami in an internal combustion car, an electric vehicle, or a hydrogen fuel cell car. Same destination. Totally different engines, fuel sources, maintenance requirements, and infrastructure needs.

**Build the bridge:** Quantum computers face the same situation. Engineers want to build machines that can hold and manipulate quantum states. But the laws of physics allow *multiple different physical systems* to do this — trapped ions, superconducting circuits, photons of light, neutral atoms, and exotic quantum materials. Each approach uses completely different physics, runs at different temperatures, scales differently, and breaks down in different ways.

**The technical term:** These different physical implementations are called **quantum hardware modalities** — different physical substrates for encoding and processing quantum information.

**Where the analogy breaks down:** Unlike cars that all use the same roads, different quantum modalities may ultimately be better suited to *different kinds of problems*. A hybrid future — where you choose your modality like you choose your tool — may be more likely than one winner-takes-all platform.

**SELL THE REVOLUTION:** The existence of five competing modalities is not a weakness in the quantum industry — it's the most exciting feature. Here's why: when semiconductor computing had only one viable approach (silicon CMOS), progress was constrained by the physics of that single substrate. Quantum computing, by contrast, has five distinct physics engines racing in parallel. Each breakthrough in one modality creates pressure on the others to respond. Industries from pharmaceutical discovery to financial portfolio optimization to cryptographic security are watching this race and hedging across all five lanes. The organization that understands *when* to bet on which horse — and *how much* to hedge — will have a structural advantage measured in years, not months, against competitors who are waiting for a single winner to emerge. The global quantum hardware market is projected to exceed \$450 billion by 2040. That money will not flow to one modality. It will flow to whoever has the framework to navigate all five.
::::

:::{figure} ../images/ch04-five-modalities-comparison.png
:name: ch04-five-modalities-comparison
:alt: Comparison table of five quantum computing hardware modalities
:width: 100%

**The Five Modalities at a Glance.** Each architecture has distinct tradeoffs in coherence time, gate speed, fidelity, scalability, and operating requirements. No single modality dominates all dimensions.
:::

---

## The Metrics That Matter

Before we examine each modality, you need the evaluation rubric. These five metrics apply to every hardware platform, every roadmap, and every vendor claim you will encounter.

### Coherence Time

::::{admonition} 🎓 9th Grader Test: Coherence Time
:class: tip

**Start with what you know:** Imagine you're building an elaborate sand castle on a beach. You have a limited window — maybe 20 minutes — before the tide comes in and the waves destroy your work. Every detail you add to that castle uses up some of your time. If your wall-building is slow, you might only get a simple structure before the tide arrives. If you're lightning fast, you can build something remarkable.

**Build the bridge:** Quantum computers face an identical challenge. A qubit in a quantum superposition is extraordinarily fragile. The slightest interaction with the environment — a vibration, a stray electromagnetic field, even a passing cosmic ray — destroys the quantum state. The time a qubit can maintain its quantum state before the "tide" of environmental interference washes it away is called its **coherence time**. Every gate operation you perform "uses up" some of that beach time. More coherence time = more complex circuits = more powerful computations.

**The technical term:** **Coherence time** is measured in two components: T₁ (how long a qubit stays excited before relaxing to ground state) and T₂ (how long a qubit maintains phase coherence). Both matter. T₂ ≤ 2T₁ always. Practical circuit depth is roughly T₂ ÷ gate time.

**Where the analogy breaks down:** Unlike tides, decoherence is not perfectly predictable — it's probabilistic, and its sources are complex enough that even small improvements in isolation can yield disproportionate gains in circuit depth.

**SELL THE REVOLUTION:** Coherence time is the single biggest engineering bottleneck between where quantum computing is today and where it needs to be. Current superconducting qubits maintain coherence for roughly 100–500 microseconds. Trapped ions reach tens of milliseconds. The quantum error correction algorithms that would allow us to run million-operation circuits — the circuits needed to simulate novel drugs, break cryptographic keys, or optimize global supply chains — require coherence times or error rates roughly 10–100× better than today's best systems. Every microsecond of additional coherence time engineers extract translates directly into more complex computable problems. The pharmaceutical industry alone spends over \$2.6 trillion annually on drug development, with a 90% clinical trial failure rate largely attributable to our inability to accurately simulate molecular interactions. Coherence time improvements are the engineering lever that unlocks that simulation capability. This is why the world's best quantum engineering teams — at IBM, Google, IonQ, Quantinuum, and a dozen startups — wake up every morning trying to squeeze more microseconds out of their qubits.
::::

:::{figure} ../images/ch04-coherence-time-analogy.png
:name: ch04-coherence-time-analogy
:alt: Sand castle analogy for coherence time showing time window for quantum operations
:width: 100%

**Coherence Time as a Sand Castle.** The coherence window determines how many gate operations you can perform before environmental noise destroys the quantum state. Longer coherence = deeper circuits = more powerful computations.
:::

### Gate Fidelity

::::{admonition} 🎓 9th Grader Test: Gate Fidelity
:class: tip

**Start with what you know:** You've played the telephone game. Twenty people sit in a circle. The first person whispers "The quantum computer simulated the protein fold." By the time the message reaches the 20th person, it might come out as "The quantum computer stimulated the protein cold." Each whisper introduces a tiny error. Over enough rounds, the message becomes unrecognizable.

**Build the bridge:** Quantum gate operations work exactly like this. Each time a quantum gate manipulates a qubit — flipping it, entangling it, rotating its state — there is a small probability of error. Modern gates achieve 99.9% fidelity, meaning a 0.1% error rate per operation. That sounds impressive until you chain 1,000 operations together: your overall accuracy drops to (0.999)^1000 = 36.8%. A calculation with 10,000 gates at 99.9% fidelity gives you essentially noise.

**The technical term:** **Gate fidelity** is the probability that a quantum gate performs its intended operation correctly. 1Q gate fidelity (single-qubit operations) and 2Q gate fidelity (two-qubit entangling operations) are tracked separately — 2Q gates are harder and generally less accurate.

**Where the analogy breaks down:** Unlike the telephone game, quantum errors can sometimes be *detected and corrected* using quantum error correction codes — but only if your physical qubit fidelity is high enough to make the overhead worthwhile (above roughly 99.9% for the surface code threshold).

**SELL THE REVOLUTION:** Gate fidelity is the most powerful commercial lever in quantum hardware. Here's the math that matters: moving from 99% to 99.9% 2Q gate fidelity doesn't sound like much — it's a 0.9 percentage point improvement. But it means the error rate dropped by 10×, which means useful circuit depth increased by roughly 10×. That single jump unlocks an entirely new class of algorithms. The financial services industry has been unable to deploy quantum advantage for portfolio optimization not because the algorithms don't exist — they do — but because the circuits are too deep for today's error rates. Quantinuum's trapped-ion systems recently achieved 99.9%+ two-qubit gate fidelity, a milestone that directly expands the set of commercially tractable problems. Every 0.1 percentage point of fidelity improvement is worth billions in addressable market. Fidelity improvements are the single biggest lever for unlocking commercial quantum value.
::::

:::{figure} ../images/ch04-gate-fidelity-analogy.png
:name: ch04-gate-fidelity-analogy
:alt: Telephone game analogy showing cumulative error growth with gate count
:width: 100%

**Gate Fidelity as a Telephone Game.** Each gate operation introduces a small error. The cumulative effect grows rapidly with circuit depth. High fidelity per gate is the difference between commercially useful quantum circuits and expensive noise generators.
:::

### The Full Metrics Framework

:::{list-table} The Five Metrics That Define Hardware Quality
:header-rows: 1
:widths: 20 25 30 25

* - Metric
  - What It Measures
  - Why It Matters
  - Watch Out For
* - **Coherence Time** (T₁, T₂)
  - How long qubits stay quantum
  - Limits circuit depth and complexity
  - "Best qubit" vs. system average
* - **Gate Fidelity** (1Q, 2Q)
  - Error rate per operation
  - Determines useful circuit depth
  - Reported on best pairs, not all pairs
* - **Connectivity**
  - Which qubits can interact directly
  - Affects compilation overhead
  - Claimed vs. measured connectivity
* - **Qubit Count**
  - Physical qubits available
  - Necessary but not sufficient
  - Physical ≠ logical qubits
* - **Logical Qubit Count**
  - Error-corrected, fault-tolerant qubits
  - Actual computational capacity
  - Almost always 0 today; watch timelines
:::

:::{admonition} The Most Important Distinction in Quantum Hardware
:class: warning

**Physical qubits ≠ Logical qubits.**

A physical qubit is raw hardware — noisy, fragile, imperfect. A logical qubit is a *group* of physical qubits working together to simulate one perfect, error-corrected qubit using quantum error correction codes. Today's most advanced machines have thousands of physical qubits but *zero* fully fault-tolerant logical qubits. When vendors announce qubit counts, they are almost always reporting physical qubits. When analysts project quantum advantage timelines, they are usually discussing logical qubits. These two numbers can differ by a factor of 1,000 or more.
:::

---

## The Five Modalities: A Deep Dive

::::{tab-set}

:::{tab-item} ⚡ Superconducting
### Superconducting Qubits: The Formula 1 Car

::::{admonition} 🎓 9th Grader Test: Superconducting Qubits
:class: tip

**Start with what you know:** Think about a Formula 1 race car. It's the fastest vehicle on the planet. It can accelerate from 0 to 200 mph in seconds. But it needs a pit crew of 50 people, specialized track conditions, a controlled environment, and millions of dollars of support infrastructure. You cannot take it to a gas station. You cannot drive it on a rainy highway. Its extraordinary performance is completely dependent on extraordinary support.

**Build the bridge:** Superconducting qubits are the Formula 1 cars of quantum computing. They operate at 15 millikelvin — colder than outer space (space is about 2.7 Kelvin; these machines run at 0.015 Kelvin). At that temperature, certain metals lose all electrical resistance and enter a quantum mechanical state that allows engineers to create artificial "atoms" on a chip using standard semiconductor fabrication techniques. These artificial atoms — called transmon qubits — can be controlled with microwave pulses and can execute gate operations in nanoseconds (billionths of a second).

**The technical term:** **Superconducting qubits** are quantum bits implemented using superconducting circuits, most commonly the Josephson junction — a quantum mechanical element that gives the circuit non-linear inductance. IBM, Google, and Rigetti all use superconducting architectures.

**Where the analogy breaks down:** Unlike F1 cars that can be tuned without changing the fundamental physics, superconducting qubits face fundamental coherence limits from the chip's material properties — limits that require new fabrication techniques, not just tuning, to overcome.

**SELL THE REVOLUTION:** IBM and Google have collectively invested over \$4 billion in superconducting quantum hardware — not because they are naive, but because the speed advantage is real and compounding. When quantum error correction matures, superconducting systems' nanosecond gate times mean they can run millions of error-correction cycles per second, using speed to compensate for noise. Google's Willow processor recently demonstrated below-threshold error correction — meaning adding more qubits *reduced* error rates rather than amplifying them. That is the breakthrough the entire field has been waiting for. Industries that require real-time quantum optimization — high-frequency trading, logistics routing, climate modeling — need systems fast enough to compute answers in operationally relevant timeframes. Superconducting may be the only architecture fast enough to meet that bar. The question is whether the cooling infrastructure can be industrialized. Several startups are working on modular dilution refrigerators that could reduce costs by 90% over the next decade.
::::

**Key players:** IBM (Eagle, Heron, Flamingo roadmap), Google (Sycamore, Willow), Rigetti, OQC, Alice & Bob

**Typical specs (2024–2025):**
- Gate time: 10–100 ns (1Q), 100–500 ns (2Q)
- Coherence time: T₁ = 100–500 μs, T₂ = 50–300 μs
- Gate fidelity: 1Q ~99.9%, 2Q ~99–99.5%
- Scale: 100–1,000+ physical qubits
- Operating temperature: 15 mK

**Best for:** Speed-critical applications, large qubit counts, integration with classical HPC workflows
**Biggest challenge:** Coherence, cooling infrastructure, manufacturing yield at scale
:::

:::{tab-item} 🔬 Trapped-Ion
### Trapped-Ion Qubits: The Swiss Watch

::::{admonition} 🎓 9th Grader Test: Trapped-Ion Qubits
:class: tip

**Start with what you know:** Compare a Formula 1 car to a Swiss watch. The watch doesn't go 200 mph. But it keeps perfect time for 50 years without a pit crew. It works at room temperature. It doesn't need a specialized track. Its precision comes from extraordinarily careful engineering of a fundamentally stable system, not from pushing the limits of speed.

**Build the bridge:** Trapped-ion quantum computers use individual atoms — typically ytterbium or barium ions — levitated in a vacuum chamber by electromagnetic fields. These natural atoms are identical to each other (nature's quality control), so every qubit starts with perfect uniformity. Laser pulses manipulate the quantum states of these suspended ions with extraordinary precision. The gates are slower than superconducting — microseconds rather than nanoseconds — but the error rates are dramatically lower and the coherence times are orders of magnitude longer.

**The technical term:** **Trapped-ion qubits** use the internal electronic states of ions (electrically charged atoms) as qubits. All-to-all connectivity (every qubit can interact with every other) is achievable within small chains, which reduces compilation overhead dramatically.

**Where the analogy breaks down:** Swiss watches scale to maybe 1,000 moving parts. Scaling trapped ions to thousands of interacting qubits faces serious challenges — shuttling ions and maintaining coherence in larger chains is an unsolved engineering problem.

**SELL THE REVOLUTION:** For applications where accuracy beats raw speed — molecular simulation for drug discovery, financial risk modeling, cryptographic protocol verification — trapped-ion systems may reach commercial advantage years before superconducting systems can match their fidelity. IonQ and Quantinuum have demonstrated two-qubit gate fidelities above 99.9%, a threshold that superconducting systems are only now beginning to approach. The pharmaceutical industry's inability to accurately simulate drug-protein interactions costs an estimated \$50 billion annually in failed clinical trials. A trapped-ion system with 50 high-fidelity logical qubits running accurate molecular dynamics simulations could change that equation entirely — and that system may be achievable before 2030. Financial firms that deploy quantum risk models on trapped-ion platforms today are building the algorithmic expertise that will be decisive competitive moats when larger systems arrive.
::::

**Key players:** IonQ, Quantinuum (Honeywell + Cambridge Quantum), Oxford Ionics

**Typical specs (2024–2025):**
- Gate time: 1–10 μs (1Q), 50–500 μs (2Q)
- Coherence time: seconds to minutes (T₂ > 10 s achievable)
- Gate fidelity: 1Q >99.99%, 2Q >99.9%
- Scale: 20–50 physical qubits (current), 1,000+ (roadmap)
- Operating temperature: Room temperature (trap itself); laser system required

**Best for:** High-fidelity circuits, chemistry simulation, financial optimization
**Biggest challenge:** Gate speed, scaling beyond ~100 qubits in a single trap
:::

:::{tab-item} ⚛️ Neutral-Atom
### Neutral-Atom Qubits: The Programmable Grid

Neutral-atom quantum computers use arrays of uncharged atoms (typically rubidium or cesium) held in place by optical tweezers — focused laser beams that trap individual atoms at programmable positions. Because the atoms are neutral, they don't interact strongly with each other by default, which makes them easy to isolate and control. To create entanglement, atoms are temporarily excited to highly energetic "Rydberg" states where they interact strongly.

**The defining advantage:** Reconfigurability. Unlike superconducting chips with fixed connectivity, neutral-atom systems can physically rearrange their qubits mid-computation, creating arbitrary connectivity patterns on demand.

**Key players:** QuEra (Harvard spinout), Pasqal, Atom Computing, Microsoft (investing)

**Typical specs (2024–2025):**
- Gate time: ~0.5–5 μs (1Q), ~0.5–10 μs (2Q via Rydberg)
- Coherence time: ~1–10 s (nuclear spin qubits can reach minutes)
- Gate fidelity: 1Q ~99.5%, 2Q ~99–99.5% (improving rapidly)
- Scale: 256–10,000+ physical qubits (atom loading)
- Operating temperature: ~microkelvin (laser cooling), no dilution fridge

**Best for:** Combinatorial optimization, analog simulation, quantum networking, large-scale variational algorithms
**Biggest challenge:** Gate speed, fidelity at scale, loading determinism

:::{admonition} The Neutral-Atom Inflection Point
:class: note
Neutral-atom systems are the most rapidly evolving modality as of 2024–2025. QuEra's 48-logical-qubit demonstration in 2023 was a landmark — the first time any platform demonstrated more than a handful of logical qubits running error-corrected algorithms. The field is watching this space extremely closely.
:::
:::

:::{tab-item} 💡 Photonic
### Photonic Qubits: Room Temperature, Network Native

Photonic quantum computers encode quantum information in individual photons — particles of light. Photons naturally travel at the speed of light, don't interact with the environment in ways that cause decoherence, and can be transmitted over optical fiber networks. These properties make photonic systems uniquely suited for quantum communication and networking.

**Key players:** PsiQuantum (aiming for utility-scale via silicon photonics manufacturing), Xanadu (PennyLane SDK), QuiX Quantum

**Typical specs (2024–2025):**
- Operating temperature: Room temperature (no dilution fridge)
- Coherence: Very long (photons don't thermalize easily)
- Gate model: Measurement-based (different computational model)
- Scale: Current systems are small; PsiQuantum's bet is manufacturing scale
- Key advantage: Silicon photonics fabrication leverages existing \$500B semiconductor manufacturing infrastructure

**Best for:** Quantum networking, quantum key distribution, distributed quantum computation
**Biggest challenge:** Deterministic single-photon sources, photon loss in gates, scaling measurement-based computation

:::{admonition} PsiQuantum's Manufacturing Bet
:class: warning
PsiQuantum has raised over \$700 million on the thesis that manufacturing millions of photonic qubits via GlobalFoundries' silicon photonics process is the fastest path to fault-tolerant scale. They are not building today's useful systems — they are engineering for a future where silicon photonics fab yield provides millions of physical qubits. This is a high-risk, high-reward bet on a 2027–2030 timeline. If it works, the photonic approach leapfrogs everyone. If the manufacturing yields don't hit targets, the capital investment may be unrecoverable.
:::
:::

:::{tab-item} 🔮 Topological
### Topological Qubits: Highest Risk, Highest Reward

Topological quantum computers would use exotic quantum states — specifically, quasi-particles called Majorana zero modes — to encode quantum information in a way that is inherently protected from local errors. The key insight: if the quantum information is stored in the *topology* of a quantum state rather than the state of any individual particle, local disturbances cannot corrupt it. It's like writing a message in a knot: you can stretch or wiggle the rope, but you cannot accidentally change what the knot *is* without deliberately cutting and retying it.

**Key players:** Microsoft (Topological Core / Azure Quantum), small academic groups worldwide

**Typical specs:** Still largely in experimental validation phase as of 2025
- Microsoft demonstrated the first topological qubit in a paper published February 2025, claiming to have observed Majorana zero modes on a semiconductor nanowire — a result that triggered intense scientific scrutiny
- Commercial viability: Estimated 5–10+ years

**Best for:** *Theoretically*, all-purpose fault-tolerant computation with dramatically lower overhead than surface codes
**Biggest challenge:** Majorana zero mode verification, materials fabrication, gate implementation — fundamental physics still being validated

:::{admonition} The Topological Wildcard
:class: important
Topological qubits are the highest-risk, highest-reward bet in quantum hardware. If the physics works as theorized, topological systems could achieve fault-tolerant computation with 10–100× fewer physical qubits than competing approaches, compressing the timeline to practical utility dramatically. Every well-managed quantum portfolio includes a small, monitored position in topological developments — not as a primary bet, but as an option on a paradigm shift.
:::
:::
::::

:::{figure} ../images/ch04-superconducting-architecture.png
:name: ch04-superconducting-architecture
:alt: Superconducting qubit dilution refrigerator architecture diagram
:width: 100%

**Superconducting Architecture.** The dilution refrigerator must maintain temperatures colder than outer space — 15 millikelvin — to allow superconducting circuits to function. This cooling requirement is the primary manufacturing and cost challenge for at-scale deployment.
:::

:::{figure} ../images/ch04-trapped-ion-architecture.png
:name: ch04-trapped-ion-architecture
:alt: Trapped-ion quantum computer architecture with ion trap and laser system
:width: 100%

**Trapped-Ion Architecture.** Individual ions levitated in a vacuum trap by electromagnetic fields. Laser pulses perform gate operations with extraordinary precision. The system operates at room temperature but requires complex laser and vacuum infrastructure.
:::

:::{figure} ../images/ch04-neutral-atom-architecture.png
:name: ch04-neutral-atom-architecture
:alt: Neutral atom quantum computer with optical tweezer array
:width: 100%

**Neutral-Atom Architecture.** Optical tweezers hold individual atoms in programmable grid patterns. The reconfigurable nature of the array allows dynamic qubit connectivity — a unique advantage over fixed-chip architectures.
:::

:::{figure} ../images/ch04-photonic-topological.png
:name: ch04-photonic-topological
:alt: Photonic and topological quantum computing architectures side by side
:width: 100%

**Photonic and Topological Architectures.** Photonic systems (left) operate at room temperature using light as the quantum carrier — enabling network integration. Topological systems (right) remain largely theoretical but promise inherently error-protected computation via exotic quantum states.
:::

---

## Reading a Roadmap Like an Analyst, Not a Fan

::::{admonition} 🎓 9th Grader Test: The Roadmap Reading Skill
:class: tip

**Start with what you know:** You've seen movie trailers. A trailer for a mediocre movie can make it look like the greatest film ever made. Dramatic music, the best 90 seconds of footage, narration that promises "an unforgettable journey." Then you see the actual film and... it's fine. The trailer was technically accurate — those scenes *are* in the movie — but it created a completely misleading impression of the whole.

**Build the bridge:** Quantum vendor roadmaps are movie trailers. They show the best-case demos. They list impressive milestone names without always clarifying whether those milestones have been *achieved* or merely *planned*. They use language like "demonstrated," "achieved," "launched" for things that happened, and "target," "planned," "expected" for things that haven't. The difference between those two categories is enormous — and easy to miss when you're excited about quantum computing.

**The technical term:** The skill of reading roadmaps analytically is called **vendor roadmap evaluation** — separating trailing indicators (things already demonstrated) from leading indicators (things promised on a future timeline), and weighting both appropriately given the technical risk at each step.

**Where the analogy breaks down:** Unlike movie trailers, roadmap accuracy is observable over time. Vendors who consistently miss milestones are giving you data. Build a personal database of vendor roadmap commits vs. actual delivery — it will be the most valuable research asset you own.

**SELL THE REVOLUTION:** Every executive who can read a quantum roadmap critically has a 3-year head start on every executive who cannot. Here is the edge in concrete terms: in 2023, multiple quantum vendors announced systems with "1,000+ qubits." Most analysts celebrated. Informed analysts read the footnotes and discovered that most of these systems had useful depths of fewer than 20 operations — because fidelity hadn't kept pace with qubit count. The "1,000 qubit" headlines were technically accurate and commercially misleading simultaneously. The organizations that understood this distinction didn't waste procurement cycles evaluating systems that couldn't serve their needs. That's the value of roadmap literacy — not just knowing which vendor is ahead, but knowing what "ahead" actually means. In a field where misinformed capital allocation decisions routinely run into eight figures, this skill is worth more than any single technical insight.
::::

:::{figure} ../images/ch04-roadmap-reading-framework.png
:name: ch04-roadmap-reading-framework
:alt: Quantum vendor roadmap analysis framework with evaluation rubric
:width: 100%

**The Roadmap Reading Framework.** Separate demonstrated milestones from planned ones. Apply the traffic-light rubric to any vendor's roadmap to get a calibrated view of near-term, mid-term, and speculative capability.
:::

### The Evergreen Roadmap Rubric

:::{list-table} Roadmap Evaluation Rubric
:header-rows: 1
:widths: 25 25 25 25

* - Claim Type
  - Green (Trust)
  - Yellow (Verify)
  - Red (Discount)
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
  - 6–18 month horizon with named dependencies
  - 2+ years, vague dependencies
* - **Demo scope**
  - Full-system benchmark on standard circuit
  - Subsystem demo extrapolated to system
  - Theoretical projection, no hardware demo
:::

### The Five Red Flags in Vendor Roadmaps

1. **Qubit count without fidelity.** A million low-fidelity qubits are worth less than 100 high-fidelity ones. Always ask: what is the system-average two-qubit gate error rate?

2. **"Quantum advantage" without specification.** Advantage over *what*, on *which problem*, measured *how*? Unspecified quantum advantage claims are marketing, not milestones.

3. **Demo on one algorithm.** A system optimized to perform well on the demonstration algorithm may perform very differently on your actual workload. Ask for benchmarks on *your* use case class.

4. **The hockey stick at year 3.** Roadmaps that show flat progress through years 1–2 and then a sudden vertical climb at year 3 should be scrutinized carefully. Quantum engineering doesn't hockey stick; it compounds.

5. **"Logical qubits" without overhead disclosure.** If a vendor claims logical qubits, ask how many physical qubits each logical qubit costs. A 1,000-physical-qubit system with 1,000-to-1 overhead has one logical qubit. That's a milestone, but not a commercial platform.

---

## The Portfolio Approach to Modality Risk

:::{admonition} Mental Model: Your Quantum Strategy Is a Seed Fund
:class: important

A well-managed venture capital seed fund doesn't bet everything on one startup. It takes 20–30 positions across different sectors, sizes, and stages. It tracks leading indicators for each portfolio company. It has pre-defined criteria for increasing allocation ("doubling down") and pre-defined criteria for writing off a position ("kill switch"). It rebalances annually.

Your organization's quantum hardware strategy should work exactly the same way. Diversify across modalities. Define kill-switch criteria before you deploy capital. Rebalance annually as the landscape shifts.
:::

### Suggested Portfolio Framework by Risk Tolerance

::::{grid} 1 2 3 3

:::{card} Conservative
:header: 🛡️ **Conservative**
:class-header: bg-primary text-white

**Focus: Deployed capability today**

- 60% Superconducting (IBM/Google access)
- 30% Trapped-Ion (IonQ/Quantinuum service)
- 10% Monitor neutral-atom progress

*Use case: Cloud API access only. No hardware procurement. Build algorithms now.*
:::

:::{card} Balanced
:header: ⚖️ **Balanced**
:class-header: bg-warning text-dark

**Focus: Near-term + option value**

- 40% Superconducting (service contracts)
- 30% Trapped-Ion (private placement consideration)
- 20% Neutral-Atom (early access programs)
- 10% Photonic (networking projects)

*Use case: Workload-specific pilots. Evaluate multiple backends. Track kill-switch criteria.*
:::

:::{card} Aggressive
:header: 🚀 **Aggressive**
:class-header: bg-danger text-white

**Focus: Long-term positioning**

- 30% Superconducting
- 25% Trapped-Ion
- 20% Neutral-Atom
- 15% Photonic
- 10% Topological (monitor)

*Use case: Strategic investment + talent acquisition. Position for fault-tolerant era. Accept 5–10 year horizon.*
:::
::::

### Kill-Switch Criteria

:::{admonition} Define These Before You Deploy Capital
:class: warning

For each modality position, define:

1. **Technical kill switch:** "If [modality] fails to achieve [specific fidelity/qubit/coherence target] by [date], we reduce allocation by [X%]."
2. **Commercial kill switch:** "If no use case in [our industry vertical] demonstrates measurable ROI by [date], we exit service contracts."
3. **Competitive kill switch:** "If a competing modality achieves [threshold], we shift [X%] of this position to the leader."

Without pre-defined kill switches, confirmation bias will keep you in losing positions.
:::

---

## Matching Modality to Workload

Not all quantum problems are created equal. The modality that's right for drug simulation may be wrong for financial optimization.

:::{list-table} Modality-to-Workload Matching Guide
:header-rows: 1
:widths: 30 25 25 20

* - Workload Type
  - Best Modality
  - Reason
  - Timeline
* - Molecular simulation (pharma/materials)
  - Trapped-Ion, Neutral-Atom
  - High fidelity, long coherence
  - 2026–2030
* - Financial portfolio optimization
  - Superconducting, Trapped-Ion
  - QAOA circuit depth needs
  - 2027–2032
* - Cryptographic key search
  - Superconducting (fault-tolerant era)
  - Shor's requires millions of gates
  - 2035+
* - Quantum networking / QKD
  - Photonic
  - Fiber-native, room temperature
  - Available now (limited)
* - Combinatorial optimization (logistics)
  - Neutral-Atom, Superconducting
  - Scale, connectivity
  - 2027–2030
* - Climate/fluid dynamics simulation
  - Superconducting (large-scale)
  - Speed-critical, large Hilbert space
  - 2030–2035
* - Machine learning (quantum ML)
  - All modalities (algorithm-dependent)
  - Depends on circuit structure
  - Speculative; near-term: NISQ era
:::

---

## Flagship Case Study: A Sovereign Wealth Fund's Quantum Hardware Portfolio

:::{figure} ../images/ch04-swf-portfolio-case.png
:name: ch04-swf-portfolio-case
:alt: Sovereign wealth fund quantum portfolio allocation diagram
:width: 100%

**The SWF Quantum Portfolio.** A sovereign wealth fund structures diversified quantum exposure across all five modalities using a mix of public equities, private placements, and service contracts — managing risk while maintaining optionality across a rapidly evolving landscape.
:::

### Situation

In early 2023, a \$400 billion sovereign wealth fund's technology investment committee convened to develop a formal quantum computing strategy. The fund had observed peer SWFs in Singapore, Norway, and the Gulf Cooperation Council beginning to take positions in quantum hardware companies. The committee faced a fundamental challenge: no single quantum hardware modality had yet demonstrated commercial advantage, yet waiting for a winner to emerge risked missing the early-mover benefits — talent pipelines, preferential access to research partnerships, and below-market entry into private placements.

The committee appointed a four-person Quantum Technology Working Group (QTWG) with a mandate to design a portfolio strategy that would (a) provide meaningful exposure to quantum hardware value creation, (b) manage the risk of backing the wrong modality, and (c) include objective kill-switch criteria to prevent sunk-cost thinking.

### Quantum Angle

The QTWG's central insight was that evaluating quantum hardware companies required a fundamentally different analytical framework from traditional technology investment. Standard metrics — revenue growth, market share, gross margin — were irrelevant for pre-commercial platforms. What mattered was:

- **Milestone velocity:** How quickly was each platform advancing on the five key technical metrics?
- **Roadmap credibility:** What fraction of past roadmap commitments had been delivered on schedule?
- **Ecosystem depth:** Were industry partners, algorithm developers, and government programs anchoring around this platform?
- **Defensibility:** Did the platform's physics or manufacturing approach provide durable competitive advantage, or could it be replicated quickly?

Using this framework, the QTWG built a proprietary scoring rubric — essentially the Roadmap Evaluation Rubric from this chapter — and applied it to 23 quantum hardware companies.

### Decisions Made

The QTWG structured the portfolio in three tiers:

**Tier 1 — Public Equity Exposure (\$800 million):**
- IBM (NYSE: IBM): Largest position, based on roadmap credibility score (IBM has consistently delivered on its superconducting roadmap milestones) and cloud access infrastructure. \$500 million.
- IonQ (NYSE: IONQ): Second position, reflecting trapped-ion's fidelity advantages for near-term applications. \$300 million.

**Tier 2 — Private Placements (\$250 million):**
- PsiQuantum: \$150 million participation in Series C. Rationale: the manufacturing thesis — that silicon photonics scale would leapfrog all other approaches — was high-risk but potentially paradigm-shifting. The QTWG limited this to a 3% portfolio position with a specific kill switch tied to GlobalFoundries yield metrics.
- Quantinuum: \$100 million in a strategic investment round. Rationale: strongest fidelity track record in the industry, with enterprise chemistry simulation contracts already signed with three pharmaceutical companies.

**Tier 3 — Service Contracts (\$50 million over 3 years):**
- IBM Quantum Network membership: Access to latest devices, research partnership rights, priority queue access.
- Quantinuum H-Series cloud access: Benchmark access for algorithm development.
- QuEra early-access program: Neutral-atom monitoring position.

**Kill-Switch Criteria Established:**
- PsiQuantum position: Exit if GlobalFoundries photonic qubit yield does not reach [redacted] by Q4 2025.
- IonQ position: Reduce by 50% if system-average 2Q fidelity does not reach 99.5% by Q2 2026.
- All positions: Rebalance annually at the June committee meeting, triggered by milestone scorecard review.

### Measured Outcome (18 Months Later)

By Q3 2024, the QTWG's first annual rebalancing was triggered. The scorecard revealed a mixed landscape:

- **IBM** had delivered the Heron processor on schedule, with measurable connectivity and fidelity improvements. Tier 1 position maintained.
- **IonQ** had made strong fidelity progress but faced commercial revenue shortfalls. The QTWG debated whether to apply the commercial kill switch; ultimately maintained position with a 90-day watch period.
- **PsiQuantum** had experienced manufacturing yield challenges at GlobalFoundries that put the internal kill-switch timeline at risk. The committee convened an emergency review and — critically — did *not* average down. They applied their pre-defined criteria and reduced the position from \$150 million to \$80 million. This discipline preserved \$70 million that was redeployed into neutral-atom positions.
- **Neutral-atom (QuEra):** The QTWG increased their early-access commitment and opened a private placement discussion, based on QuEra's 48-logical-qubit demonstration exceeding expectations.

### Open Question

The QTWG's June 2025 committee meeting faces a question with no clean answer: **Should the portfolio's photonic position be exited entirely, or is the manufacturing timeline merely delayed rather than failed?** The kill-switch criteria established in 2023 are triggering, but PsiQuantum's management argues that yield improvements are on track for a revised 2028 timeline — a 12-month slip, not a fundamental failure.

This is the exact situation kill-switch criteria are designed to prevent sunk-cost thinking from distorting. The data suggests the criteria should be applied. Sentiment — the billions already deployed — suggests waiting. What would you recommend?

:::{admonition} Discussion Anchor
:class: note
When analyzing this case, focus on process, not outcome. The QTWG made defensible decisions under genuine uncertainty. Evaluate whether their framework was well-designed, whether they applied it consistently, and whether the kill-switch approach served its intended function — independent of whether the specific bets ultimately paid off.
:::

---

## Industry Snapshots

### Snapshot 1: IBM vs. IonQ vs. Quantinuum — Reading Three Roadmaps

:::::{tab-set}

::::{tab-item} IBM
**IBM Quantum Roadmap — Evaluation**

IBM has published arguably the most consistently credible public quantum roadmap in the industry. Key milestones:

- **Eagle (127 qubits, 2021):** ✅ Delivered on schedule
- **Osprey (433 qubits, 2022):** ✅ Delivered on schedule
- **Condor (1,121 qubits, 2023):** ✅ Delivered on schedule
- **Heron (133 qubits, new coupling architecture, 2023):** ✅ Delivered
- **Flamingo / modular systems (2025+):** 🟡 In progress — modular interconnects are the critical dependency

**Roadmap credibility score:** High. IBM has a strong trailing indicator record. The shift from qubit count to quality metrics (error-per-gate, circuit layer operations per second) in 2023 was analytically mature — they stopped optimizing for the misleading headline metric and started optimizing for useful computation.

**Key risk:** IBM's superconducting roadmap requires modular interconnects to scale beyond ~1,000 qubits. That engineering challenge has no peer-reviewed demonstration yet.
::::

::::{tab-item} IonQ
**IonQ Roadmap — Evaluation**

IonQ is publicly traded (NYSE: IONQ) and publishes its roadmap with unusual transparency for a public company. Key metric: Algorithmic Qubits (#AQ), their proprietary metric combining qubit count and fidelity into a single performance measure.

- **#AQ 20 (2022):** ✅ Demonstrated
- **#AQ 35 (2023):** ✅ Demonstrated (Forte system)
- **#AQ 64 (2025):** 🟡 Claimed for Forte Enterprise; peer verification pending
- **#AQ 1000 (2028):** 🔴 Highly speculative; depends on photonic interconnect and ion shuttling breakthroughs not yet demonstrated

**Roadmap credibility score:** Moderate-High for near-term milestones; Low-Moderate for 2027+ projections. IonQ's #AQ metric is useful but proprietary — always ask for system-average 2Q gate fidelity alongside it.

**Key risk:** Scaling trapped-ion beyond ~100 physical qubits in a single trap is an unsolved engineering problem. IonQ's 2027+ roadmap depends on photonic interconnects that are still in R&D phase.
::::

::::{tab-item} Quantinuum
**Quantinuum Roadmap — Evaluation**

Quantinuum (formed from Honeywell Quantum Solutions + Cambridge Quantum) has the highest gate fidelity track record in the industry. Their H-Series systems have consistently achieved best-in-class two-qubit gate fidelity.

- **H1-1 (20 qubits, 99.1% 2Q fidelity, 2021):** ✅ Delivered
- **H2 (32 qubits, 99.8%+ 2Q fidelity, 2023):** ✅ Delivered — historic milestone
- **H3 (56+ qubits, 2025):** 🟡 In progress
- **1,000-qubit fault-tolerant system (2029):** 🔴 Highly ambitious; requires breakthrough in ion chain scaling

**Roadmap credibility score:** High for fidelity milestones; Moderate for scale milestones. Quantinuum's consistent over-delivery on fidelity targets is their strongest signal. Their scale roadmap requires solving ion-chain scalability, which is a hard problem.

**Key differentiator:** Quantinuum is the only hardware vendor with signed pharmaceutical simulation contracts at commercial rates — a strong leading indicator of near-term commercial relevance.
::::
:::::

### Snapshot 2: PsiQuantum's Manufacturing Bet

PsiQuantum's strategic thesis is worth understanding as a standalone case study in quantum strategy. Their argument:

1. Fault-tolerant quantum computing requires millions of physical qubits (surface code overhead)
2. No one will build millions of qubits by hand-crafting each one in a research fab
3. The only path to millions of qubits is commercial semiconductor manufacturing scale
4. Silicon photonics is the only quantum modality compatible with existing semiconductor fabs
5. Therefore, the winning quantum architecture will be silicon photonic, built by GlobalFoundries

This thesis is either completely correct or completely wrong — there is no middle scenario. If manufacturing yields hit targets, PsiQuantum has a scale advantage that no research lab can replicate. If photonic gate operations cannot be made deterministic at the required rate, the entire thesis fails.

PsiQuantum has raised over \$700 million and secured manufacturing agreements. They have been deliberately opaque about intermediate technical milestones, which is itself a yellow flag in the roadmap rubric — the absence of verifiable intermediate milestones makes the timeline difficult to evaluate.

**Portfolio implication:** Small position with explicit yield-based kill switch. Not a core holding until manufacturing demonstrations are publicly validated.

---

## Productive-Struggle Problem

:::{admonition} Productive-Struggle Problem: Three Redacted Roadmaps
:class: seealso

Below are three anonymized vendor roadmaps (Vendor A, B, and C). Using only the chapter's evaluation rubric, rank them by **plausibility** and **commercial relevance**. Flag every line between demonstrated and promised capability.

**Vendor A:**
- "Achieved 500-qubit system with average 2Q gate error rate of 0.8% (2022)" — *source: internal benchmark, not peer-reviewed*
- "Delivered 1,000-qubit system (2023)" — *source: press release*
- "Demonstrated quantum advantage on portfolio optimization (2023)" — *problem size and classical baseline not specified*
- "Plans 10,000-qubit system with 0.1% error rate by 2026"
- "Fault-tolerant logical qubit demonstration expected 2027"

**Vendor B:**
- "Published 2Q gate fidelity of 99.5% on 25-qubit system in Nature (2022)" — *peer-reviewed*
- "Demonstrated 35 algorithmic qubits with 99.6% average 2Q fidelity (2023)" — *confirmed by independent benchmarking*
- "40-qubit system with 99.7%+ fidelity in customer access (2024)"
- "100 physical qubit system (2025 target)"
- "1,000 physical qubit system using photonic interconnects (2028 target)"

**Vendor C:**
- "Operational 2,000-atom neutral-atom array (2024)" — *published*
- "Demonstrated 48 error-corrected logical qubits (2023)" — *Nature paper*
- "Site-selective entanglement with 99.5% average 2Q fidelity on arbitrary qubit pairs (2024)" — *conference presentation, independent replication pending*
- "10,000-atom system planned for 2026"
- "1,000 error-corrected logical qubits planned for 2028"

:::

:::{dropdown} Answer Key (Instructor View)
**Ranking: B > C > A**

**Vendor A Analysis — Rank 3 (Lowest Plausibility):**
- Red flags: Internal benchmark only, no peer review. "Quantum advantage" claim with no specified problem size or classical baseline — the definition of the "demo trap." The 2026 target of 10× fidelity improvement with 10× qubit scaling in 3 years is implausible given industry trajectory. The gap between demonstrated (2022–2023) and promised (2026–2027) is too large with too few verifiable intermediate milestones.
- Demonstrated: qubit count (unverified), some fidelity claim (unverified)
- Promised: essentially everything of commercial value

**Vendor C Analysis — Rank 2 (Moderate Plausibility):**
- Green: Nature paper on logical qubits is strong. Large atom count (2,000) is consistent with neutral-atom physics. 
- Yellow: "Independent replication pending" on the 2Q fidelity claim is a meaningful caveat.
- Red: 1,000 logical qubits by 2028 is an extremely aggressive target — a 20× increase in 4 years. Plausible if neutral-atom progress continues its current trajectory, but requires multiple simultaneous engineering breakthroughs.
- Verdict: Strong near-term credibility, aggressive but not implausible mid-term roadmap.

**Vendor B Analysis — Rank 1 (Highest Plausibility):**
- Green: Peer-reviewed fidelity data, independent benchmarking, granular intermediate milestones, conservative timeline. Every near-term claim has a verification method.
- Yellow: Photonic interconnect dependency for 2028 scale — this is real and hard.
- Verdict: This roadmap is consistent with trapped-ion physics, has strong verification, and the gap between demonstrated and promised is bridgeable by identified engineering work. This is how credible roadmaps look.

**The Key Insight:** Vendor A has the most impressive-sounding milestones ("10,000 qubits," "quantum advantage") but the weakest evidence. Vendor B has the most modest near-term claims but the strongest evidence. In quantum, the vendor with the most verifiable milestones is almost always the most trustworthy — and usually the most commercially relevant.
:::

---

## Module-Level Outcomes

By completing this chapter, you can:

1. **Compare** the five modalities on coherence time, gate fidelity, scalability, and error rates — identifying the tradeoffs each makes
2. **Interpret** any quantum vendor roadmap using the evergreen rubric: trailing vs. leading indicators, qualified vs. unqualified milestones, the demo trap
3. **Separate** demonstrated capability (published, peer-reviewed, independently replicated) from marketing promises (targeted, planned, expected)
4. **Match** a modality to a workload based on circuit depth requirements, fidelity needs, connectivity demands, and timeline
5. **Design** a multi-vendor hedging strategy with explicit kill-switch criteria, appropriate to a given organization's risk tolerance

---

## Lab 4 (Regular): Reading the Room — Comparing Quantum Backends

:::{admonition} Lab 4 Overview
:class: note

**Time:** ~45 minutes  
**Platform:** IBM Quantum Platform (free tier) at [quantum.ibm.com](https://quantum.ibm.com)  
**Skills practiced:** Backend evaluation, circuit execution, rubric application  
**Deliverable:** One-page "Backend Selection Memo"
:::

### Objective

Experience the chapter's evaluation rubric in practice. You will build a simple quantum circuit, run it on three different backends, and evaluate each backend using the five key metrics — documenting your analysis in a structured memo.

### Step 1: Create Your Circuit

Log into IBM Quantum Platform (free account). In the Quantum Composer, build a 3-qubit GHZ state:

```
Step 1: Apply H (Hadamard) gate to qubit 0
Step 2: Apply CNOT gate from qubit 0 → qubit 1
Step 3: Apply CNOT gate from qubit 0 → qubit 2
Step 4: Measure all three qubits
```

This circuit creates a maximally entangled state where all three qubits should measure either all-0 or all-1. Any other measurement outcome is an error.

**Expected ideal result:** 50% `|000⟩`, 50% `|111⟩`

### Step 2: Select Three Backends

Choose THREE backends from the IBM Quantum available systems. Try to select:
- One with the most qubits available to free tier
- One with the best reported 2Q error rate
- One that differs from the above (different qubit count range)

For each backend, record from the properties panel:

:::{list-table} Backend Data Collection Template
:header-rows: 1
:widths: 25 15 15 15 15 15

* - Field
  - Backend 1
  - Backend 2
  - Backend 3
  - Notes
  - Source
* - Backend name
  - 
  - 
  - 
  - 
  - IBM dashboard
* - Modality
  - 
  - 
  - 
  - All IBM = superconducting
  - 
* - Qubit count
  - 
  - 
  - 
  - 
  - Properties
* - T₁ (avg, μs)
  - 
  - 
  - 
  - 
  - Calibration data
* - T₂ (avg, μs)
  - 
  - 
  - 
  - 
  - Calibration data
* - 2Q error rate (avg)
  - 
  - 
  - 
  - 
  - Calibration data
* - Measured GHZ fidelity
  - 
  - 
  - 
  - `|000⟩ + |111⟩` fraction
  - Your run
:::

### Step 3: Apply the Rubric

Place each backend on the chapter's evaluation rubric. Score each on a 1–5 scale for:
- Coherence (T₁/T₂ relative to peer systems)
- Fidelity (2Q error rate relative to peer systems)
- Measured accuracy (your GHZ result)

### Deliverable: Backend Selection Memo

Write a one-page (400–500 word) "Backend Selection Memo" structured as:

1. **Executive Summary (2 sentences):** Which backend performed best and why
2. **Rubric Scores Table:** Your scored rubric for all three backends
3. **Analysis (2–3 paragraphs):** What drove the performance differences? Were the calibration specs predictive of measured results?
4. **Recommendation:** For a financial optimization workload requiring 20 qubits and 200 two-qubit gates, which backend would you select — and why? Use rubric scores, not brand names.

---

## Lab 4 (Optional Advanced): Automated Backend Benchmarking Suite

<a href="https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch04-backend-benchmarking.ipynb" target="_blank">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="margin-bottom: 1rem;"/>
</a>

:::{admonition} Advanced Lab Overview
:class: note

**Time:** ~2–3 hours  
**Tools:** Python 3, Qiskit Runtime, pandas, matplotlib, IBM Quantum account  
**Skills practiced:** Programmatic backend querying, calibration data analysis, automated benchmarking, composite scoring  
**Deliverable:** Working benchmarking tool + Backend Report Card + 500-word analytical memo
:::

### Objective

Build an automated tool that queries all available IBM Quantum backends, pulls live calibration data, runs a standardized GHZ benchmark circuit, computes a composite Quality Score for each, and outputs an auto-generated Backend Report Card.

### Architecture

```python
# High-level pipeline
1. service = QiskitRuntimeService(channel="ibm_quantum")
2. backends = service.backends(operational=True)
3. For each backend:
   a. Pull calibration: T1, T2, 1Q error, 2Q error (all pairs)
   b. Compute median system metrics
   c. Build standardized GHZ benchmark circuit
   d. Submit and collect results
   e. Compute fidelity: fraction of shots in {|000⟩, |111⟩}
4. Compute Quality Score = w1*(T2/T2_max) + w2*(1-err_2Q/err_max) + w3*fidelity
5. Generate Report Card: ranked table + visualization
```

### Quality Score Formula

$$QS = 0.35 \cdot \frac{T_2}{T_{2,\text{max}}} + 0.40 \cdot \left(1 - \frac{e_{2Q}}{e_{2Q,\text{max}}}\right) + 0.25 \cdot F_{\text{GHZ}}$$

Where:
- $T_2$ is the median T₂ coherence time across all qubits on the backend
- $e_{2Q}$ is the median two-qubit gate error rate
- $F_{\text{GHZ}}$ is the measured GHZ state fidelity (fraction of ideal-state outcomes)
- Weights (0.35, 0.40, 0.25) reflect the relative importance of coherence, fidelity, and measured performance

### Deliverable

1. **Working Python tool** (submitted as `.py` or Colab notebook)
2. **Backend Report Card** — auto-generated ranked table comparing all queried backends on all five metrics plus Quality Score, with a matplotlib visualization
3. **500-word analytical memo** addressing:
   - Which backend ranked highest and why
   - Were there backends where calibration specs predicted results well? Poorly? What might explain the discrepancies?
   - If you were advising a pharmaceutical company evaluating IBM systems for molecular simulation, which backend would you recommend? Justify using Quality Score components, not brand names.

---

## Discussion Guidelines

Post a 350–500 word initial response to the following prompt. Cite at least two sources (academic papers, vendor technical documentation, or credible news coverage). Respond substantively to **two peers**, engaging with their specific arguments rather than offering general agreement.

:::{admonition} Discussion Prompt
:class: seealso

The chapter argues that the criteria for evaluating quantum hardware are more durable than the current leaderboard positions. Do you agree? 

Choose one of the five hardware modalities and make the strongest possible case that it will *not* be a major player in commercial quantum computing by 2035. What would have to go wrong technically? What signals would you watch for? What would cause you to change your assessment?

Then identify one piece of evidence that cuts *against* your own argument, and explain how you weight it.
:::

---

## Glossary

```{glossary}
Coherence time
  The duration a qubit maintains its quantum state before environmental interaction destroys it. Measured as T₁ (energy relaxation time) and T₂ (dephasing time). T₂ ≤ 2T₁ always. Longer coherence enables deeper, more complex quantum circuits.

Gate fidelity
  The probability that a quantum gate performs its intended operation correctly. Expressed as a percentage; 99.9% means 0.1% error probability per gate. 1Q (single-qubit) and 2Q (two-qubit) fidelities are tracked separately; 2Q is harder and typically lower.

Physical qubit
  A raw hardware qubit — noisy, imperfect, subject to decoherence. The qubit counts reported by vendors are almost always physical qubit counts.

Logical qubit
  An error-corrected qubit formed by encoding quantum information across many physical qubits using quantum error correction. One logical qubit may require hundreds to thousands of physical qubits. Logical qubit counts are almost always near zero on today's systems.

Superconducting qubit
  A qubit implemented using superconducting circuits, typically a Josephson junction-based transmon. Operates at ~15 mK. Fast gates (nanoseconds) but relatively short coherence times. Used by IBM, Google, Rigetti.

Trapped-ion qubit
  A qubit implemented using the internal electronic states of trapped ions (e.g., ytterbium). Very long coherence times, very high gate fidelity, slower gate speeds. All-to-all connectivity possible in small chains. Used by IonQ, Quantinuum.

Neutral-atom qubit
  A qubit using the internal states of neutral (uncharged) atoms held by optical tweezers. Reconfigurable connectivity, scales to hundreds/thousands of atoms, Rydberg blockade for entanglement. Used by QuEra, Pasqal, Atom Computing.

Photonic qubit
  A qubit encoded in quantum properties of photons. Room-temperature operation, naturally network-compatible, measurement-based computation model. Used by PsiQuantum, Xanadu.

Topological qubit
  A theoretical qubit encoding information in topological quantum states (Majorana zero modes) for inherent error protection. Microsoft's primary quantum research direction. Still in experimental validation.

Josephson junction
  A quantum mechanical tunnel junction between two superconductors, separated by a thin insulating barrier. The nonlinear inductance of the Josephson junction is what gives superconducting circuits their qubit-like, anharmonic energy levels.

Dilution refrigerator
  A cryogenic cooling device used to achieve millikelvin temperatures required for superconducting quantum computers. Operates on the enthalpy of mixing helium-3 and helium-4 isotopes. Costs \$500K–\$2M and is the primary infrastructure challenge for scaling superconducting quantum computing.

Rydberg state
  A highly energized atomic state used in neutral-atom quantum computers to create temporary strong interactions between nearby atoms, enabling two-qubit gate operations. Named after physicist Johannes Rydberg.

Quantum error correction (QEC)
  A family of techniques for protecting quantum information from errors by encoding logical qubits in entangled states of many physical qubits, allowing errors to be detected and corrected without measuring (and thus disturbing) the logical qubit directly.

Surface code
  The most widely studied quantum error correction code. Arranges physical qubits in a 2D grid with alternating data and ancilla qubits. Requires error rates below ~1% (the threshold) to be effective. State-of-the-art systems are approaching this threshold.

NISQ (Noisy Intermediate-Scale Quantum)
  Term coined by John Preskill in 2018 for the current era of quantum computing: devices with 50–1,000+ physical qubits but no error correction, limited coherence, and finite gate fidelity. Describes essentially all commercial quantum hardware today.

Quantum volume
  An IBM-developed metric combining qubit count, connectivity, fidelity, and other factors into a single number representing the effective computational capability of a quantum system. Useful but hardware-specific; most meaningful for comparing IBM systems.

Algorithmic Qubits (#AQ)
  IonQ's proprietary performance metric combining qubit count and fidelity into a single score representing the number of "useful" qubits for real algorithm execution. Useful but proprietary; ask for underlying fidelity data when evaluating.

Kill-switch criterion
  A pre-defined, objective trigger condition that mandates reducing or exiting an investment position. In quantum hardware portfolio management, kill-switch criteria prevent sunk-cost thinking from trapping capital in failing modalities.

Two-qubit gate
  A quantum gate that operates on two qubits simultaneously, creating entanglement between them. The most error-prone common operation in quantum circuits. The controlled-NOT (CNOT) gate is the most widely used two-qubit gate.

Fault tolerance
  The property of a quantum system in which errors can be detected and corrected faster than they accumulate, allowing arbitrarily long computations. Requires logical qubits and error rates below the threshold. Not yet achieved on any commercial platform.
```

---

## Leader's Takeaway

:::{epigraph}
Don't fall in love with a qubit. Fall in love with a workload, and let the qubit earn its place.
:::

The Betamax lesson is not that better technology loses. It's that "better" is always relative to a specific set of criteria, at a specific moment, in a specific ecosystem. The criteria change. The ecosystem changes. The winner changes.

Five quantum hardware modalities are racing toward commercial viability. Each has genuine strengths, genuine weaknesses, and genuine uncertainty in its long-term trajectory. The executive who understands all five — who can read any roadmap, evaluate any fidelity claim, and build a diversified hardware portfolio with pre-defined kill switches — is not the executive who picks the right horse. They're the executive who built the system to re-evaluate the race every twelve months and adjust.

That system — the evaluation framework in this chapter — doesn't become obsolete when IBM announces a new processor or when a startup achieves a record fidelity. The metrics don't change. The analytical approach doesn't change. Only the numbers filling the rubric change.

Build the framework. Apply it consistently. Let the technology prove itself against your criteria, not against its own marketing.

The rest is just maintenance.
