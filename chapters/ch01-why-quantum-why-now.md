---
title: "Chapter 1: The $850 Billion Question — Why Quantum, Why Now"
subtitle: "From Physics Experiment to Enterprise Agenda"
short_title: "Ch. 1: Why Quantum, Why Now"
description: "Quantum computing has crossed from physics experiment to enterprise agenda item. This chapter explains why — through market forecasts, historical context, three structural accelerants, and a roadmap from NISQ to fault-tolerant systems."
label: ch-01-why-quantum-why-now
tags: [quantum computing, business strategy, NISQ, fault tolerance, market forecasts, quantum winters]
---

# Chapter 1: The \$850 Billion Question — Why Quantum, Why Now

:::{figure} ../images/ch01-explainer-infographic.png
:label: fig-ch01-explainer-infographic
:alt: Comprehensive explainer infographic summarizing Chapter 1, showing the quantum computing timeline, three accelerants, NISQ-to-fault-tolerant roadmap, and market forecast ranges.
:width: 100%
:align: center

**Chapter 1 at a Glance.** This infographic maps the journey from the physics laboratory to the enterprise boardroom — the timeline, the three structural accelerants, and the roadmap from noisy intermediate-scale quantum devices to mature fault-tolerant systems.
:::

This chapter answers a question that a surprising number of senior executives have quietly postponed: *Should we care about quantum computing yet?* The honest answer is that the question itself is now slightly outdated. The more productive question is: *What happens to organizations that start caring eighteen months after their competitors do?* The gap between those two questions — the space between "not yet" and "already too late" — is precisely where this chapter lives.

---

## Opening Scene: October 2019

The paper landed in *Nature* on October 23, 2019, under a title that read like a physics journal article and hit financial news desks like a press release. Google's team, led by researcher John Martinis and his colleagues at the University of California Santa Barbara, announced that their 53-qubit processor — named Sycamore — had performed a specific computational task in approximately 200 seconds. Their estimate: the same task would take the world's fastest classical supercomputer, Summit at Oak Ridge National Laboratory, roughly 10,000 years.

The phrase embedded in the abstract was deliberate: *quantum supremacy*.

Press coverage was immediate and overwhelming. "Google Achieves Quantum Supremacy, Marking a New Era in Computing" ran across every major technology publication. Financial headlines pivoted the story toward markets: IonQ stock surged when it eventually went public; IBM, Honeywell, and a constellation of quantum startups saw increased investor attention within days. For one news cycle, it felt as though the future had arrived early and was asking for a parking spot.

Then IBM fired back.

Within 24 hours, IBM's research team published a blog post — not a peer-reviewed paper, but a pointed technical rebuttal — arguing that Summit could solve the same problem in approximately 2.5 days, not 10,000 years, given optimized classical algorithms and sufficient disk storage. The argument was technically sound: Google's benchmark used a specific random circuit sampling task, and IBM demonstrated that a classical simulation with enough storage and clever optimization could reduce the gap dramatically. "Quantum supremacy," IBM argued, was a marketing claim dressed as a scientific milestone.

Wall Street, characteristically, called it Monday.

Six years later, the argument between Google and IBM feels less like a conflict and more like a parable. Both sides were correct about different things. Google had demonstrated a genuine hardware engineering achievement — fifty-three qubits operating with sufficient coherence to execute a circuit that would be genuinely difficult to simulate classically. IBM correctly noted that the specific benchmark chosen was tuned to favor quantum hardware, and that a better classical algorithm closed the gap significantly. The lesson is not that one side was dishonest. The lesson is that quantum milestone announcements require careful reading — and that lesson will recur many times over the coming decade.

What mattered most in the long run was not the 10,000-year claim. What mattered was that the largest internet company on Earth had deployed over one billion dollars in quantum hardware research, published in the world's most prestigious scientific journal, and used the word *supremacy*. The enterprise world began paying attention. The companies that ignored the headline are, six years later, scrambling to write quantum strategy decks.

---

## The Single Idea

```{epigraph}
Quantum computing has crossed from physics experiment to enterprise agenda item — not because it is finished, but because the cost of being late now exceeds the cost of being early.
```

This idea deserves unpacking, because it runs counter to the usual technology-adoption instinct. Most enterprise technology decisions reward patience. Early adopters of enterprise software, cloud infrastructure, and even artificial intelligence frequently overpaid for immature systems and spent years managing the technical debt. The conventional wisdom — *let the technology mature before committing* — has been empirically validated in dozens of technology waves.

Quantum computing appears to be the exception, for three reasons that will occupy the rest of this chapter.

First, the strategic preparation required for quantum advantage is long-lead. Identifying which business processes are genuinely quantum-amenable, retraining technical staff, building vendor relationships, and beginning cryptographic migration all take years. Starting that preparation when quantum hardware matures means starting too late.

Second, the competitive landscape is not waiting. As of 2025, JPMorgan Chase employs a team of quantum researchers. Airbus has run quantum-enhanced aerodynamic optimization pilots. BMW has partnered with quantum chemistry firms to model hydrogen fuel cell reactions at the molecular level. The organizations that treat quantum computing as a "2030 problem" are competing against organizations that started treating it as a "2024 investment."

Third, and most urgently for any organization that handles sensitive data: the cryptographic threat is not contingent on quantum computers being useful for optimization or simulation. A quantum computer capable of running Shor's algorithm at scale breaks most of the public-key cryptography currently protecting the internet. Adversaries are harvesting encrypted data today, with the explicit strategy of decrypting it when sufficiently powerful quantum hardware arrives. The window for cryptographic migration has already opened.

```{admonition} The Core Tension
:class: important

The central challenge of quantum strategy is that the technology matures on a different timescale than the preparation it requires. Organizations that wait for quantum computers to be "ready" will find themselves unprepared when readiness arrives.
```

---

## The Shape of the Forecasts: Ranges, Not Points

Before examining the numbers, it is worth establishing a discipline that should govern every market-sizing analysis in this course: **treat forecast ranges as structural signals, not precise predictions**.

:::{figure} ../images/ch01-market-forecast-ranges.png
:label: fig-ch01-market-forecast-ranges
:alt: Market forecast chart showing quantum computing market size projections from 2024 to 2035 with conservative, base case, and optimistic scenarios.
:width: 100%
:align: center

**Quantum Computing Market Projections, 2024–2035.** The wide uncertainty bands reflect genuine disagreement about adoption timelines, hardware scaling, and application unlock dates — not analytical imprecision. Conservative estimates project \$450B by 2035; optimistic scenarios reach \$850B. Source: McKinsey Global Institute (2021), BCG Quantum Advantage report (2023).
:::

The headline figure of \$850 billion comes from McKinsey Global Institute's 2021 analysis, which projected that quantum computing could generate between \$450 billion and \$850 billion in value across four sectors by 2035: pharmaceuticals and chemicals, finance, logistics and mobility, and materials science. The range — nearly a factor of two — is not a sign of analytical sloppiness. It reflects three genuinely uncertain variables: hardware scaling timelines, application discovery rates, and competitive market dynamics.

Boston Consulting Group's parallel analysis, updated in 2023, projected a more conservative base case of \$450 billion but noted that the pharmaceutical sector alone could see \$50–\$100 billion in value creation from accelerated drug discovery. IBM's internal market projections, shared with enterprise clients, suggest a "quantum utility" inflection point — the moment when quantum computers solve commercially meaningful problems faster than classical alternatives — arriving in the late 2020s for specific narrow applications.

What do these ranges tell a strategist? Several things:

**The sectors are consistent across forecasters.** Every major analysis identifies the same four domains as primary value capture zones: (1) pharmaceutical simulation, where quantum chemistry can model molecular interactions at a level of fidelity inaccessible to classical computers; (2) financial optimization, where portfolio construction, risk modeling, and derivative pricing involve combinatorial problems that scale poorly classically; (3) logistics and supply chain, where route optimization and scheduling represent tractable near-term quantum applications; and (4) materials science and battery chemistry, where quantum simulation of electron behavior could unlock next-generation energy storage.

**The timelines are wide and honestly so.** The difference between a \$450 billion and \$850 billion outcome by 2035 largely depends on whether certain hardware thresholds are crossed in 2028 or 2032. Nobody knows. Forecasters who offer narrower ranges are making unstated assumptions about hardware progress that they cannot fully justify.

**The floor is nonzero and rising.** Even pessimistic scenarios now project meaningful quantum value creation. The era when the honest answer was "possibly never" has passed. The question is when and how much, not whether.

```{admonition} A Note on Forecast Credibility
:class: tip

When evaluating any quantum market forecast, ask three questions: (1) Does it distinguish between quantum value *creation* and quantum industry *revenue*? These differ by an order of magnitude. (2) Does it account for the time between hardware availability and enterprise deployment? Historically, this gap is 3–7 years. (3) Does it specify which applications unlock which value, or is it a top-down extrapolation from total addressable market?
```

---

## Quantum Winters: History and Why This Cycle Is Different

:::{figure} ../images/ch01-quantum-winters-timeline.png
:label: fig-ch01-quantum-winters-timeline
:alt: Timeline showing the history of quantum winters, from the first quantum winter in the 1980s-90s through the current quantum renaissance.
:width: 100%
:align: center

**The Quantum Winters and the Current Spring.** Three distinct eras of quantum computing investment reveal a pattern: scientific promise followed by engineering disappointment, followed by renewed investment on more solid ground. The current cycle is structurally differentiated from its predecessors by corporate capital, government mandates, and a clear near-term application path.
:::

Any honest assessment of quantum computing must grapple with the field's history of promising too much too soon. The term "quantum winter" — borrowed from the AI community's "AI winters" of the 1970s and 1980s — describes periods when funding contracted sharply after promises outpaced delivery.

**The First Quantum Winter (approximately 1985–1994)** followed the initial wave of enthusiasm after Richard Feynman's 1982 proposal of a quantum simulator and David Deutsch's 1985 formalization of the quantum Turing machine. The theoretical foundations were stunning. The hardware was nonexistent. Academic funding agencies, unable to point to a physical quantum computer, gradually shifted resources toward more tractable problems. The field survived primarily in university physics departments.

**The Mid-Cycle Thaw and Second Cooling (1994–2015)** began dramatically when Peter Shor published his polynomial-time quantum algorithm for integer factorization in 1994. The implications were immediate and alarming: a sufficiently powerful quantum computer could break RSA encryption. DARPA, NSA, and a handful of corporate research labs (notably AT&T Bell Labs and IBM Research) injected significant funding. But the hardware progress was brutally slow. Building a stable qubit required isolating a quantum system from all environmental noise — a challenge that consumed two decades of experimental physics. By the mid-2000s, public and private funding had again contracted, though classified government investment (particularly from intelligence agencies worried about cryptographic vulnerability) continued.

**The Current Cycle (2015–present)** is structurally different from both predecessors in four distinct ways:

First, it is funded by *corporate capital*, not primarily by government grants. Google, IBM, Microsoft, Amazon, and Intel have each invested billions in quantum research programs. This capital does not disappear when a five-year grant cycle ends.

Second, there is a clear *near-term application path*. NISQ-era computers — imperfect, limited, but real — can already run quantum circuits that provide genuine research value for chemistry simulation, optimization heuristics, and quantum machine learning experiments. The field no longer requires waiting for fault-tolerant hardware before delivering any value.

Third, the *geopolitical context* has transformed the funding calculus. China's National Laboratory for Quantum Information Sciences, opened in Hefei in 2020 with an estimated \$10 billion budget, has turned quantum computing into a national security priority for every major power. Governments do not defund national security programs the way they defund basic research.

Fourth, the *ecosystem* has matured irreversibly. Qiskit, IBM's open-source quantum development kit, has been downloaded millions of times. AWS Braket, Azure Quantum, and Google Quantum AI each offer cloud access to real quantum hardware. The developer community building quantum applications is orders of magnitude larger than at any previous point in the field's history. This community creates lock-in that prior waves never achieved.

```{admonition} Why Past Winters Are Not Predictive
:class: warning

It is tempting to argue that because quantum computing has disappointed before, it will disappoint again. This reasoning fails to account for structural differences: the current cycle has corporate capital, government security mandates, real (if imperfect) hardware, and a global developer ecosystem. The base case is no longer "wait and see" — it is "prepare while the hardware matures."
```

---

## Three Accelerants

:::{figure} ../images/ch01-three-accelerants.png
:label: fig-ch01-three-accelerants
:alt: Infographic showing three accelerants driving quantum computing adoption: Geopolitics, AI Convergence, and Cryptographic Risk.
:width: 100%
:align: center

**The Three Structural Accelerants.** Geopolitical competition, AI convergence, and cryptographic risk are each individually sufficient to sustain quantum investment. Together, they create a dynamic where the cost of inaction compounds faster than the cost of premature investment.
:::

### Accelerant One: Geopolitics

:::{figure} ../images/ch01-geopolitical-race.png
:label: fig-ch01-geopolitical-race
:alt: World map showing global quantum computing investment race between the United States, China, European Union, and United Kingdom.
:width: 100%
:align: center

**Global Quantum Investment, 2020–2025.** National quantum programs are no longer discretionary research investments — they are strategic infrastructure, treated with the same urgency as semiconductor supply chains and satellite communications.
:::

The geopolitical dimension of quantum computing is perhaps the least appreciated by enterprise strategists and the most consequential for long-term investment trajectories. Governments do not fund quantum research primarily because they expect commercial returns. They fund it because quantum computers offer decisive asymmetric advantages in three national security domains: signals intelligence (breaking adversary communications), materials simulation (nuclear weapons design and advanced conventional weapons), and optimization (logistics superiority in military operations).

The United States National Quantum Initiative Act, signed in 2018, authorized \$1.2 billion over five years. The 2022 CHIPS and Science Act added additional quantum provisions. By 2025, federal quantum commitments exceeded \$3 billion across the Department of Energy, NSF, DARPA, NIST, and the intelligence community. The European Union's Quantum Flagship program committed €1 billion over ten years. The United Kingdom published a £2.5 billion National Quantum Strategy in 2023.

China's investments are harder to audit but by most independent estimates dwarf Western programs. The National Laboratory for Quantum Information Sciences alone reportedly received \$10 billion in initial funding, and Chinese researchers publish more quantum computing papers annually than any other nation. The Micius satellite, which demonstrated quantum key distribution at intercontinental distances in 2017, was a signal — both technical and geopolitical — that China is not a follower in this field.

The enterprise implication is straightforward: when governments treat a technology as a national security priority, the funding does not dry up when commercial timelines slip. The current quantum investment cycle is structurally supported by strategic imperatives that are immune to quarterly earnings pressure.

### Accelerant Two: AI Convergence

The relationship between quantum computing and artificial intelligence is not one of substitution — quantum computers will not replace AI accelerators — but of *synergistic expansion*. Two convergence pathways are worth distinguishing.

**Quantum-enhanced machine learning** (QML) explores whether quantum circuits can provide computational advantages for specific learning tasks. Theoretical results suggest quadratic speedups for certain linear algebra operations that underlie neural network training. Practical demonstrations remain limited to toy problems on NISQ hardware, but the research community is large, well-funded, and making measurable progress. Companies like Quantinuum (the merged entity of Honeywell Quantum Solutions and Cambridge Quantum Computing) have published QML results suggesting genuine near-term applications in drug discovery and materials classification.

**Classical AI accelerating quantum development** is the more immediately impactful pathway. Google DeepMind's AlphaFold demonstrated that transformer architectures could solve protein structure prediction — a problem that quantum simulation might also address but has not yet. More directly relevant: Google's own quantum team used machine learning to optimize qubit calibration, error correction protocols, and circuit compilation, substantially improving the effective performance of their hardware. AI is becoming a critical tool in the quantum engineering toolchain.

The convergence creates a flywheel: better AI tools accelerate quantum hardware development, which enables more ambitious quantum experiments, which generate training data for AI models that further optimize quantum systems. Organizations with deep AI capabilities — including the hyperscalers and large pharmaceutical companies — are positioned to benefit from this flywheel more quickly than organizations without them.

### Accelerant Three: Cryptographic Risk

:::{figure} ../images/ch01-cryptographic-risk.png
:label: fig-ch01-cryptographic-risk
:alt: Infographic showing cryptographic risk from quantum computing, including the harvest-now-decrypt-later threat and the NIST post-quantum cryptography migration path.
:width: 100%
:align: center

**The Cryptographic Threat Timeline.** The "harvest now, decrypt later" attack requires no quantum computer today — only the patience to store encrypted data until one becomes available. Organizations with long data-life assets face a threat that exists in the present, not the future.
:::

Of the three accelerants, cryptographic risk is the only one that creates *current* organizational exposure. It does not require waiting for a quantum computer to become commercially useful.

The mechanism is known as "harvest now, decrypt later" (HNDL). Adversaries — nation-states, primarily — are currently collecting encrypted internet traffic at scale. The data they collect today: diplomatic cables, financial transactions, intelligence communications, medical records, trade secrets. All of it is currently encrypted with public-key algorithms (RSA, ECDH, and similar) that rely on the mathematical difficulty of factoring large integers or solving discrete logarithm problems. Shor's algorithm, running on a sufficiently large fault-tolerant quantum computer, solves both problems in polynomial time.

The adversary does not need the quantum computer today. They need it before the data expires. For diplomatic cables, that might be twenty years. For trade secrets, perhaps ten. For medical records in some jurisdictions, indefinitely.

The National Institute of Standards and Technology (NIST) finalized the first post-quantum cryptography (PQC) standards in August 2024, after a seven-year standardization competition. The winners — CRYSTALS-Kyber for key encapsulation and CRYSTALS-Dilithium for digital signatures — are lattice-based algorithms designed to be resistant to both classical and quantum attacks. NIST's guidance is explicit: organizations should begin migration *now*.

Migration is not trivial. Most enterprise systems have cryptographic dependencies buried in software libraries, hardware security modules, VPN concentrators, IoT firmware, and legacy applications. A comprehensive cryptographic inventory and migration takes, by NIST's own estimate, five to ten years for complex organizations. Banks, healthcare systems, defense contractors, and critical infrastructure operators are effectively already late.

```{admonition} Action Item: Cryptographic Inventory
:class: important

Any organization that handles data with a useful life exceeding five years should initiate a cryptographic inventory — an audit of all systems that use RSA, ECDH, or similar quantum-vulnerable algorithms. This is not a quantum computing project. It is a cybersecurity project that happens to be motivated by quantum computing.
```

---

## The NISQ-to-Fault-Tolerance Roadmap

:::{figure} ../images/ch01-nisq-to-ft-roadmap.png
:label: fig-ch01-nisq-to-ft-roadmap
:alt: Roadmap diagram showing quantum computing progression through three phases: NISQ Now, Early Fault Tolerance Soon, and Mature Fault Tolerant Later.
:width: 100%
:align: center

**From NISQ to Fault-Tolerant Quantum Computing.** The three-phase roadmap translates physics milestones into enterprise planning horizons. "Now" means deployable experiments and cryptographic preparation. "Soon" means narrow commercial quantum advantage in specific domains. "Later" means broad enterprise transformation.
:::

The term *NISQ* — Noisy Intermediate-Scale Quantum — was coined by physicist John Preskill in 2018 to describe the class of quantum computers that exist today and will exist for the near future: real, programmable quantum processors with 50 to 1,000 qubits, but subject to significant error rates that limit the length and complexity of circuits they can reliably execute. Understanding the roadmap from NISQ to fault-tolerant systems is essential for calibrating enterprise expectations.

````{tab-set}
```{tab-item} Now: NISQ Era (2020–2027)
**Hardware:** 50–1,000 physical qubits, error rates of 0.1–1% per gate, circuit depth limited to ~100 layers.

**Capabilities:** Quantum chemistry simulations for small molecules, optimization heuristics for constrained problems, quantum machine learning research, quantum key distribution (already commercially deployed).

**Enterprise posture:** Build expertise, begin cryptographic migration, run proof-of-concept experiments on cloud quantum hardware (IBM Quantum, AWS Braket, Azure Quantum, Google Quantum AI). The goal is not to deploy quantum advantage in production — it is to develop the organizational capability to recognize and deploy it when it arrives.

**Key milestone to watch:** IBM's goal of 100,000 "quantum volume" metric by 2025, and Quantinuum's \#AQ target on trapped-ion hardware.
```

```{tab-item} Soon: Early Fault Tolerance (2027–2032)
**Hardware:** 10,000–1,000,000 physical qubits encoding 100–10,000 *logical* qubits with error rates below the fault-tolerance threshold (~0.1%). Error correction overhead reduces the effective qubit count by a factor of 100–1,000.

**Capabilities:** Narrow commercial quantum advantage in pharmaceutical simulation (specific drug-target binding problems), financial optimization (certain portfolio construction tasks), and materials discovery. These are not general-purpose advantages — they are domain-specific, problem-specific, and require quantum-native algorithm development.

**Enterprise posture:** Organizations with a quantum-ready team and a mapped portfolio of quantum-amenable problems will be positioned to deploy early commercial applications. Those without are entering a 3–5 year catch-up cycle.

**Key milestone to watch:** First peer-reviewed demonstration of quantum advantage on a commercially relevant problem instance — not a synthetic benchmark.
```

```{tab-item} Later: Mature Fault Tolerance (2032+)
**Hardware:** Millions of physical qubits, thousands of logical qubits, error rates low enough to run Shor's algorithm at commercially relevant key sizes.

**Capabilities:** Broad pharmaceutical simulation, full cryptographic threat realization, logistics optimization at supply-chain scale, climate modeling, financial market simulation.

**Enterprise posture:** Organizations that have not prepared face existential competitive and security risks. The asymmetry between prepared and unprepared organizations becomes severe.

**Key milestone to watch:** NIST's post-quantum cryptography migration deadline (currently recommended: 2030 for most federal systems, implying 2030–2033 for critical private sector systems).
```
````

```{prf:definition} NISQ Era
:label: def-nisq-era

A **Noisy Intermediate-Scale Quantum (NISQ)** computer is a quantum processor with 50–1,000 physical qubits operating without full error correction. NISQ devices are capable of running short quantum circuits but accumulate errors that limit circuit depth and problem size. The NISQ era is characterized by *quantum noise* as the primary engineering constraint, as distinct from the *qubit count* constraint that defined earlier experimental systems.
```

```{prf:definition} Fault-Tolerant Quantum Computing
:label: def-ftqc

A **fault-tolerant quantum computer (FTQC)** encodes logical qubits in redundant arrays of physical qubits using quantum error correction codes (e.g., the surface code). When physical error rates fall below a threshold of approximately 1%, error correction suppresses errors exponentially as the code distance increases, enabling arbitrarily long computations. Fault tolerance requires roughly 1,000 physical qubits per logical qubit at current error rates.
```

---

## Flagship Case Study: Google Sycamore and the \$10,000-Year Question

:::{figure} ../images/ch01-google-sycamore-case-study.png
:label: fig-ch01-google-sycamore-case-study
:alt: Case study infographic about Google Sycamore 2019 quantum supremacy experiment, showing the 200-second vs 10,000-year comparison and IBM's rebuttal.
:width: 100%
:align: center

**Google Sycamore vs. IBM Summit: Both Sides Were Right.** The 2019 quantum supremacy dispute is a masterclass in how to read quantum milestone claims — and a preview of the rhetorical landscape enterprises will navigate for the next decade.
:::

### Situation

In early 2019, a draft of Google's quantum supremacy paper briefly appeared on a NASA server before being taken down — an accidental leak that sent quantum industry observers into a frenzy of speculation for nearly two months before the official *Nature* publication in October. The paper described an experiment in which Google's 53-qubit Sycamore processor was tasked with sampling from the output distribution of a random quantum circuit — a task with no obvious commercial application, specifically designed to be easy for quantum hardware and hard for classical simulators.

### Quantum Angle

The specific task — random circuit sampling — was chosen because it sits in a theoretically motivated "sweet spot": quantum computers can generate samples from the output distribution in polynomial time, while classical simulation appears to require exponential resources. Google's claim rested on the assertion that their implementation of this task in 200 seconds would require Summit approximately 10,000 years via known classical simulation methods.

The scientific achievement was genuine. Sycamore demonstrated two-qubit gate fidelities of approximately 99.5% across its 53-qubit array — a hardware engineering feat that represented a decade of progress in superconducting qubit fabrication.

### Decisions Made

IBM's rebuttal, published the day before Google's paper appeared in *Nature*, was technically careful. IBM's team argued that with 2.5 petabytes of disk storage and optimized simulation techniques, Summit could solve the same problem in approximately 2.5 days — not 10,000 years. They were correct that Google's estimate assumed limited classical storage, and that a different classical algorithm could dramatically reduce the runtime.

Google's team acknowledged the rebuttal but maintained that their estimate was based on the classical storage available on Summit at the time. Both claims were honest; they were answering slightly different questions.

### Measured Outcome

The market reaction over the following 18 months revealed something important about how enterprise attention works. IonQ, which went public via SPAC in late 2021, achieved a peak market capitalization exceeding \$6 billion — representing primarily speculative valuation, not revenue. Quantum computing became a fixture of corporate innovation reports, board-level technology briefings, and MBA curriculum. IBM announced its Quantum Roadmap committing to 1,000+ qubit systems by 2023 and 4,000+ qubit systems by 2025. Microsoft, previously quiet on near-term quantum timelines, accelerated its investment in topological qubit research. Venture capital investment in quantum computing reached \$1.4 billion globally in 2021, up from \$400 million in 2019.

None of this was caused directly by Sycamore. But Sycamore was the catalyst that made quantum computing legible to non-physicists. It provided a narrative: "Google did something a supercomputer couldn't."

### Open Question

The deeper question raised by the Sycamore episode is methodological: how should enterprises evaluate future quantum milestone announcements? The lesson is not that Google overstated its results (it did not) or that IBM was being obstructionist (it was not). The lesson is that quantum milestone claims are made about specific, carefully chosen tasks — and the gap between "faster at this benchmark" and "commercially useful" requires domain expertise to evaluate accurately. Every future announcement of "quantum advantage" should prompt the question: *advantage at what, over what classical alternative, for what problem instance size?*

```{admonition} Reading Quantum Headlines
:class: tip

When a quantum computing announcement claims a speedup over classical methods, ask: (1) What is the exact task? (2) What classical algorithm is being compared? (3) Is this a problem instance anyone cares about commercially? (4) Does the advantage persist as problem size scales? Google-IBM was a preview — expect similar debates for every major milestone announcement over the next decade.
```

---

## Industry Snapshots: The Enterprise Vanguard

:::{figure} ../images/ch01-industry-snapshots.png
:label: fig-ch01-industry-snapshots
:alt: Four-quadrant infographic showing JPMorgan Chase, Mercedes-Benz, Airbus, and BMW adopting quantum computing for specific use cases.
:width: 100%
:align: center

**The Enterprise Vanguard.** Four organizations from different sectors illustrate how quantum investment looks in practice: not as a replacement for classical systems, but as a targeted capability for specific high-value problems.
:::

### JPMorgan Chase: Portfolio Optimization at Scale

JPMorgan Chase operates one of the largest quantum research programs in the financial services industry. The bank's quantum group, based primarily in New York and London, has published peer-reviewed research on quantum algorithms for option pricing, portfolio optimization, and Monte Carlo simulation acceleration. Their work on a quantum algorithm for derivative pricing — published in collaboration with IBM in 2019 — demonstrated a theoretically quadratic speedup for a simplified options pricing model.

The practical implication is not that JPMorgan runs options pricing on a quantum computer today. The implication is that their quantitative analysts understand the algorithm landscape well enough to recognize, when early fault-tolerant hardware becomes available, whether a specific portfolio construction or risk calculation problem qualifies for quantum treatment. They are building the organizational antibodies for quantum integration.

Separately, JPMorgan has been a leader in quantum communication, piloting quantum key distribution links between their offices as part of a broader program to evaluate post-quantum cryptographic readiness. Their 2023 annual report acknowledged cryptographic migration as a top-five cybersecurity priority.

### Mercedes-Benz: The Battery Chemistry Frontier

The automotive transition to electric vehicles depends critically on battery chemistry. Current lithium-ion batteries are engineered through a combination of empirical trial-and-error and classical molecular simulation — a process that takes years per material candidate and misses promising compounds because the simulation is too expensive to run at sufficient fidelity.

Quantum simulation offers a fundamentally different approach. The nitrogen fixation reaction — the same reaction at the heart of biological nitrogen fixation in soil bacteria — involves quantum mechanical interactions between electrons and atomic nuclei that cannot be accurately modeled classically for more than about 20 atoms. Lithium-sulfur batteries, which could offer twice the energy density of lithium-ion at lower cost, involve electron transfer dynamics in the same regime.

Mercedes-Benz entered a research partnership with IBM Quantum in 2020 specifically to explore quantum simulation of lithium-sulfur battery chemistry. The program does not expect production-ready quantum simulation capability until the early fault-tolerance era — but beginning the research now means that when the hardware crosses the threshold of utility, Mercedes-Benz researchers already know which problems to run on it, which algorithms to use, and what "quantum advantage" looks like for their specific chemistry questions.

### Airbus: Aerodynamic Optimization in the Skies

Airbus's quantum computing program illustrates a different entry point: combinatorial optimization rather than quantum simulation. Aircraft route optimization, fleet scheduling, and supply chain logistics all involve combinatorial problems that grow exponentially with problem size under classical approaches. These are sometimes called "NISQ-amenable" problems because quantum approximate optimization algorithms (QAOA) offer potential advantages on near-term hardware, even without full error correction.

Airbus has run pilots using QAOA for aircraft loading optimization — determining how to distribute cargo weight across a fleet to minimize fuel consumption while satisfying complex constraint systems. Early results, published in 2021, were honest about the current state: QAOA on 2021-era hardware did not outperform state-of-the-art classical solvers for problem instances of commercial size. But the research established that the algorithm structure is sound, and that as qubit counts and circuit depths improve, the advantage gap narrows.

More significantly, Airbus has integrated quantum computing into its broader digital transformation program. Their internal quantum center of excellence trains engineers across multiple business units, creating organizational literacy that cannot be purchased off the shelf when the technology matures.

### BMW: Hydrogen at the Molecular Level

BMW's quantum computing investment centers on its hydrogen fuel cell vehicle program, one of the most capital-intensive bets in the automotive hydrogen space. Hydrogen fuel cell efficiency depends critically on catalytic reactions at platinum surfaces — reactions that involve quantum mechanical electron exchange between hydrogen molecules, water, and the platinum catalyst lattice. Classical density functional theory (DFT) simulations, the standard tool for modeling such reactions, break down at the quantum mechanical detail level required to engineer significantly better catalysts.

BMW partnered with Quantinuum and Classiq in 2022 to explore quantum simulation of proton exchange membrane (PEM) fuel cell chemistry. The research program is explicitly exploratory — the team acknowledges that current quantum hardware cannot simulate the full catalytic reaction at useful fidelity. But they have identified specific subproblems within the reaction pathway that may be tractable on early fault-tolerant hardware, and they are developing the algorithmic toolkit to exploit quantum simulation when the hardware is ready.

The BMW case illustrates a strategic posture that will likely define the most successful enterprise quantum programs: *targeted investment in problem identification*, not premature deployment. The organization that knows exactly which molecular simulation problem it will run on an early fault-tolerant quantum computer has a significant first-mover advantage over the organization that starts the problem identification process after the hardware arrives.

---

## Unit Economics: Reading the Forecast Landscape

The \$850 billion headline figure deserves structural analysis. How is that number constructed, and what assumptions does it depend on?

McKinsey's 2021 methodology disaggregated the forecast by sector and value type:

| Sector | Low Estimate | High Estimate | Primary Application |
|--------|-------------|---------------|---------------------|
| Pharmaceutical & Chemicals | \$200B | \$340B | Drug discovery, materials simulation |
| Finance | \$110B | \$180B | Portfolio optimization, risk modeling |
| Mobility & Logistics | \$90B | \$150B | Route optimization, fleet scheduling |
| Materials Science | \$50B | \$180B | Battery chemistry, semiconductor design |
| **Total** | **\$450B** | **\$850B** | |

: McKinsey Global Institute quantum value forecast by sector, 2035 horizon. *Source: McKinsey Global Institute (2021). "A Quantum Decade: Navigating the Tradeoffs."* {#tbl-ch01-forecast}

The pharmaceutical number dominates the forecast. This reflects the enormous value of accelerating drug discovery: bringing a single successful drug to market faster by even two years is worth several billion dollars in net present value. Quantum chemistry simulation that enables better target identification or reduces failed clinical trials by improving molecular binding predictions could plausibly generate hundreds of billions in pharmaceutical value over a decade.

```{admonition} What the Forecast Assumes
:class: note

The McKinsey \$450–850B range depends on at least three structural assumptions: **(1)** That early fault-tolerant hardware capable of running useful quantum chemistry simulations arrives in the 2028–2032 window. **(2)** That enterprises can deploy quantum-ready workflows within 3–5 years of hardware availability, requiring that they start building capability now. **(3)** That classical computing does not achieve equivalent breakthroughs (e.g., AI-accelerated molecular simulation) that close the value gap before quantum hardware matures. Each of these can be contested. The honest answer is that the range captures this uncertainty explicitly.
```

---

## Productive-Struggle Problem

```{admonition} Productive Struggle: Load-Bearing Assumptions
:class: important

**Scenario:** You are a strategy analyst at a large healthcare system. Your CTO has shared the following one-paragraph forecast excerpt from a consulting report:

*"Our base case projects that quantum computing will enable healthcare systems to reduce drug discovery costs by 30% and accelerate time-to-market by 2.5 years by 2035, generating approximately \$85 billion in value globally. This projection assumes that early fault-tolerant systems capable of running quantum chemistry simulations at useful fidelity will be commercially available by 2029, that major pharmaceutical partners will adopt quantum-native workflows within 3 years of hardware availability, and that current AI-based drug discovery tools do not achieve equivalent capabilities independently."*

**Your task:** Identify the **three most load-bearing assumptions** in this excerpt. For each assumption:
1. State the assumption explicitly.
2. Assess whether it is high-confidence, medium-confidence, or low-confidence, with a one-sentence justification.
3. Describe what a reasonable bear case looks like if the assumption fails.
4. Suggest one data source or indicator you would monitor to track whether the assumption is holding.

**This is a 45–60 minute exercise.** Work through each assumption methodically before reading the discussion guidance below.
```

::::{dropdown} Discussion Guidance (Open After Completing the Exercise)

**Assumption 1: Fault-tolerant hardware by 2029.**
*Confidence: Low-to-medium.* IBM's public roadmap targets "quantum-centric supercomputing" milestones by 2029, but publicly stated hardware roadmaps in quantum computing have historically slipped by 2–4 years. The 2029 date assumes no major engineering setbacks in error rate reduction or qubit fabrication yield. A bear case in which hardware slips to 2033 pushes the entire value forecast timeline right by 4 years, roughly halving the 2035 NPV.
*Monitor:* IBM Quantum, Google Quantum AI, and Quantinuum annual hardware reports; academic publications on surface code error thresholds.

**Assumption 2: 3-year enterprise adoption lag.**
*Confidence: Low.* Enterprise software adoption timelines routinely exceed projections by a factor of 2–3x. Cloud computing adoption took 7–10 years in most large healthcare systems; AI adoption in clinical workflows has lagged commercial availability by 5–8 years in many organizations. A 3-year adoption lag requires that healthcare systems begin building quantum capability *before* the hardware arrives — which is precisely the argument of this chapter.
*Monitor:* Survey data on enterprise quantum workforce investment; number of quantum-certified developers in target industries; hospital CIO quantum strategy disclosures.

**Assumption 3: Classical AI does not close the gap.**
*Confidence: Medium.* AlphaFold demonstrated that deep learning could solve protein structure prediction — a problem that had been proposed as a quantum use case for a decade. Similar breakthroughs in molecular dynamics simulation are plausible. However, electron correlation problems in quantum chemistry (the specific domain where quantum simulation offers its most fundamental advantage) have been shown to be in computational complexity classes that classical AI cannot efficiently approximate. The risk is domain-specific, not global.
*Monitor:* Publications in *Nature Chemistry* and *Journal of Chemical Theory and Computation* on AI-classical methods for electron correlation; breakthrough preprints on arXiv.

**The meta-lesson:** Every market forecast for a technology with long development timelines rests on assumption chains. The forecast is only as strong as its weakest assumption — and the weakest assumption is usually the one about enterprise readiness, not hardware performance.
::::

---

## Module-Level Outcomes

By the end of this chapter, you should be able to:

::::{grid} 1 1 2 2
:::{grid-item-card} Outcome 1
:class-header: bg-primary text-white
**Economic Impact**

Describe projected economic impact of quantum computing by sector and horizon, citing McKinsey Global Institute (2021) and BCG (2023) as named sources, and explain why forecasts are presented as ranges rather than point estimates.
:::

:::{grid-item-card} Outcome 2
:class-header: bg-primary text-white
**Quantum Winters**

Distinguish the two prior quantum winters from the current investment cycle by identifying at least three structural differences: corporate capital durability, near-term NISQ applications, and geopolitical security mandates.
:::

:::{grid-item-card} Outcome 3
:class-header: bg-primary text-white
**Three Accelerants**

Identify and explain the three structural accelerants (geopolitics, AI convergence, cryptographic risk) and describe why cryptographic risk creates present-day organizational exposure independent of quantum hardware maturity.
:::

:::{grid-item-card} Outcome 4
:class-header: bg-primary text-white
**NISQ-to-FT Roadmap**

Summarize the NISQ-to-fault-tolerance roadmap in executive language, mapping the three phases to "now, soon, later" enterprise planning horizons and articulating the appropriate organizational posture for each phase.
:::

:::{grid-item-card} Outcome 5
:class-header: bg-warning text-white
**Forecast Evaluation**

Given any quantum market-sizing forecast, surface its load-bearing assumptions regarding hardware timeline, enterprise adoption lag, and classical computing alternatives, and assess each assumption's confidence level.
:::
::::

---

## Lab 1 (Regular): Touring IBM Quantum Platform

### Overview

IBM Quantum Experience (quantum.ibm.com) provides cloud access to real quantum processors. This lab introduces you to the platform, its hardware documentation, and the operational realities of quantum computing — error rates, qubit coherence times, and queue dynamics that do not appear in any press release.

### Prerequisites

- A web browser and an email address
- No programming experience required for this lab

### Procedure

**Step 1: Create Your Account**
Navigate to [quantum.ibm.com](https://quantum.ibm.com) and create a free IBM Quantum account. Verify your email. You will have access to IBM's free-tier quantum processors with limited queue priority.

**Step 2: Explore the Hardware Catalog**
Navigate to the "Compute resources" section. You will see a list of available quantum processors: names like *ibm_brisbane*, *ibm_kyiv*, and *ibm_torino*. Each processor card shows:
- **Qubit count** (e.g., 127 qubits for Eagle-class processors)
- **Queue depth** (number of jobs waiting ahead of yours)
- **Status** (operational, maintenance, calibrating)

**Step 3: Read Calibration Data**
Click on any operational processor. You will see a calibration table showing, for each qubit:

| Metric | What It Measures | Typical Value |
|--------|-----------------|---------------|
| **T₁ (relaxation time)** | How long a qubit holds its excited state before decaying | 50–500 µs |
| **T₂ (dephasing time)** | How long a qubit maintains quantum coherence | 30–300 µs |
| **Gate error rate** | Probability of error per two-qubit gate operation | 0.1–1% |
| **Readout error** | Probability of misreading a qubit's final state | 1–5% |

: IBM Quantum calibration metrics and their significance. {#tbl-ch01-calibration}

Note the *variation* across qubits on the same chip. Qubit 4 may have a T₁ of 400 µs while Qubit 17 has a T₁ of 80 µs. This non-uniformity is a defining feature of NISQ hardware and directly impacts circuit design.

**Step 4: Observe Live Jobs**
Navigate to the job queue visualization. Note how many jobs are queued, what their estimated wait times are, and how queue depth varies by time of day. This queue depth is a proxy for global quantum computing research activity.

**Step 5: Submit a Test Job (Optional)**
Using the Circuit Composer (a drag-and-drop interface), build a single Hadamard gate on one qubit followed by a measurement. Submit it to a real backend. Wait for the result. Observe that the output is probabilistic — sometimes 0, sometimes 1, in approximately equal proportion — which is the quantum superposition principle made visible.

### Deliverable

Write a 250-word reflection addressing:
1. What calibration metric surprised you most, and why?
2. What does the queue depth tell you about the current state of quantum research demand?
3. Based on the error rates you observed, what kinds of circuits would be *feasible* on this hardware? What kinds would be *infeasible*?

---

## Lab 1 (Optional Advanced, Python): Quantum Momentum Index

<a href="https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch01-quantum-momentum-index.ipynb" target="_blank">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="margin-bottom: 1rem;"/>
</a>

> **No installation needed.** Click the button above to open this lab instantly in Google Colab — free, browser-based, works on any device. Run the first cell to install all dependencies automatically.

```{admonition} Advanced Lab — Python Required
:class: tip

This lab is optional and intended for students with Python experience. It produces a quantitative artifact (a plot and memo) that can serve as a professional portfolio piece.
```

### Overview

You will build a **Quantum Momentum Index (QMI)** — a composite metric that combines arXiv paper counts, open-source framework activity, and venture capital investment to track the "temperature" of the quantum computing field over time, and overlay it against the Gartner Hype Cycle.

:::{figure} ../images/ch01-quantum-momentum-index.png
:label: fig-ch01-quantum-momentum-index
:alt: Quantum Momentum Index dashboard showing arXiv paper counts, GitHub commit trends, VC funding rounds, and Gartner hype cycle overlay from 2017 to 2025.
:width: 100%
:align: center

**Target Visualization: The Quantum Momentum Index.** Your lab deliverable should produce a dashboard similar to this one, combining four data streams into a single normalized composite index and annotating it against the Gartner Hype Cycle curve.
:::

### Data Sources

| Data Stream | Source | Method |
|------------|--------|--------|
| arXiv paper counts | arXiv API | `GET https://export.arxiv.org/api/query?search_query=quantum+computing&start=0&max_results=100` |
| Qiskit GitHub commits | GitHub API | `GET /repos/Qiskit/qiskit/stats/commit_activity` |
| Cirq GitHub commits | GitHub API | `GET /repos/quantumlib/Cirq/stats/commit_activity` |
| PennyLane GitHub commits | GitHub API | `GET /repos/PennyLaneAI/pennylane/stats/commit_activity` |
| VC funding rounds | CSV provided in `/resources/quantum_funding_2017_2025.csv` | pandas read_csv |

### Procedure

```python
# Step 1: Collect arXiv monthly paper counts
import requests
import pandas as pd
from datetime import datetime

def get_arxiv_counts(year_start=2017, year_end=2025):
    """Query arXiv API for quantum computing papers per month."""
    counts = {}
    for year in range(year_start, year_end + 1):
        for month in range(1, 13):
            query = f"quantum computing"
            date_range = f"submittedDate:[{year}{month:02d}01 TO {year}{month:02d}28]"
            url = f"https://export.arxiv.org/api/query?search_query={query}+AND+{date_range}&max_results=0"
            response = requests.get(url)
            # Parse totalResults from Atom XML response
            counts[f"{year}-{month:02d}"] = parse_total_results(response.text)
    return pd.Series(counts)

# Step 2: Collect GitHub commit activity for each framework
# Step 3: Load VC funding rounds CSV
# Step 4: Normalize all series to 0-100 scale using min-max normalization
# Step 5: Compute QMI as weighted average (equal weights as default)
# Step 6: Overlay Gartner Hype Cycle curve (manual annotation or parameterized sigmoid)
# Step 7: Plot all series plus QMI composite
```

### Deliverable

1. A single plot (PNG or PDF, minimum 1200×800 pixels) showing all four normalized data streams plus the composite QMI, with the Gartner Hype Cycle overlaid as a shaded reference region.
2. A 500-word memo interpreting your findings: Where is quantum computing on the hype cycle today? What does the trajectory suggest about the next 24 months? Which data stream is most predictive of the others?

---

## Discussion Guidelines

This chapter's discussion invites you to apply forecast evaluation skills to a real market-sizing claim. In your main response (400–500 words), choose one quantum market forecast from a named source (McKinsey, BCG, Goldman Sachs, or IBM) and surface its three most load-bearing assumptions. Assess each assumption as high, medium, or low confidence and explain your reasoning. **Include at least one scholarly or credible citation** in your main response — peer-reviewed papers, NIST publications, and named consulting firm reports all qualify.

**You are expected to respond to at least TWO peers with substantial feedback** that goes beyond agreement. Substantive peer responses engage with the specific assumptions your classmate identified, offer alternative confidence assessments, introduce a data point your classmate did not mention, or challenge the choice of forecast source. A response that reads "Great analysis, I agree with your assessment" does not satisfy this requirement.

```{admonition} Discussion Seed Questions
:class: note

- If the hardware timeline assumption in your forecast slips by three years, how does that change the sector-level value estimates?
- Which of the three accelerants (geopolitics, AI convergence, cryptographic risk) do you believe is most likely to independently sustain quantum investment if hardware progress stalls? Why?
- The Google-IBM dispute over Sycamore turned on a difference in classical algorithm choice. What does this suggest about how enterprises should evaluate future "quantum advantage" announcements?
```

---

## Exercises

::::{exercise}
:label: ex-ch01-forecast-range

**Forecasting Under Uncertainty**

The McKinsey (2021) forecast projects \$450–850 billion in quantum value by 2035. The range spans nearly a factor of two. Explain why a factor-of-two range is actually *more honest* than a point estimate for a technology at this stage of development. What specific variables account for the spread between \$450B and \$850B? Name at least three.

:::{dropdown} Solution

A point estimate implies a precision that cannot be justified for a technology whose commercial timeline depends on hardware engineering achievements, enterprise adoption rates, and competitive dynamics from classical computing — all of which have significant uncertainty.

The \$400 billion spread between \$450B and \$850B is driven primarily by:

1. **Hardware timeline uncertainty**: Whether early fault-tolerant hardware becomes commercially available by 2028 (optimistic) or 2033 (conservative) creates an enormous difference in the 2035 value realized, since quantum value compounds as deployment scales.

2. **Enterprise adoption lag**: Historically, enterprises take 3–10 years to deploy transformative technologies from when hardware is commercially available. The shorter end of this range yields \$850B; the longer end yields \$450B.

3. **Classical computing competition**: If AI-classical hybrid methods achieve drug discovery results comparable to quantum simulation in the 2026–2030 window (as AlphaFold demonstrated for protein structure), the pharmaceutical value component — the largest single sector — contracts significantly.

4. **Regulatory and procurement cycles**: Particularly in healthcare and defense, procurement timelines add 2–5 years between technology availability and deployment at scale.

A forecast that acknowledges these uncertainties by presenting a range is more analytically rigorous than one that offers a false-precision point estimate.
:::
::::

::::{exercise}
:label: ex-ch01-quantum-winters

**Distinguishing the Current Cycle**

Identify three structural differences between the current quantum investment cycle and the quantum winters of the 1980s–2000s. For each difference, explain why it makes a sustained winter less likely this time, and name one piece of evidence that supports your claim.

:::{dropdown} Solution

**Difference 1: Corporate capital depth.**
Prior investment cycles were funded primarily by government grants and academic research budgets. Google, IBM, Microsoft, Amazon, and Intel have each committed billions in corporate capital that does not have a grant cycle renewal deadline. Evidence: IBM's \$100 million commitment to the Chicago Quantum Exchange (2021); Google's sustained Quantum AI research headcount of 300+ researchers.

**Difference 2: Near-term NISQ applications.**
Prior cycles required waiting for fault-tolerant hardware before any commercial application was possible. NISQ devices — imperfect but real — already provide quantum chemistry research value for small molecules and optimization heuristics for logistics problems. The field no longer has a pure theory-to-hardware gap. Evidence: JPMorgan's published quantum derivative pricing research (2019); Quantinuum's commercial quantum chemistry service for pharmaceutical partners (launched 2023).

**Difference 3: Geopolitical security mandate.**
The US National Quantum Initiative, China's National Laboratory for Quantum Information Sciences, and the EU Quantum Flagship create investment floors tied to national security objectives that are immune to commercial disappointment. Intelligence agencies' concerns about cryptographic vulnerability ensure sustained classified investment regardless of enterprise timeline. Evidence: NIST's post-quantum cryptography standardization program (finalized 2024); NSA's Commercial National Security Algorithm Suite 2.0 mandate requiring PQC migration.
:::
::::

::::{exercise}
:label: ex-ch01-cryptographic-urgency

**The Harvest-Now-Decrypt-Later Threat**

Your organization manages health records for 4 million patients, all encrypted with RSA-2048. The CIO argues that quantum computers won't threaten RSA until 2035 at the earliest, so there is no urgency to begin post-quantum cryptographic migration today. Construct a counterargument using the harvest-now-decrypt-later threat model. What data about your patient population makes the urgency specific?

:::{dropdown} Solution

The CIO's argument is technically correct but strategically incomplete. The harvest-now-decrypt-later threat model breaks the connection between "when quantum computers can break RSA" and "when the threat begins."

**The counterargument**: Adversaries with access to internet backbone infrastructure (nation-states, sophisticated APT groups) are currently collecting encrypted health records in bulk. They do not need to decrypt them today — they need only store them until quantum computing capability becomes available. Patient records have legal retention requirements of 10–30 years in most US jurisdictions. A patient diagnosed with a chronic condition today will still have protected health information in records being held in 2050.

**Why this patient population is specifically at risk**:
- Patients with sensitive conditions (HIV status, mental health diagnoses, genetic predispositions, substance use treatment) have health records whose sensitivity does not diminish with time.
- Health records are among the most valuable data for targeted phishing, insurance fraud, and coercion — motivating collection even with a long decryption lag.
- HIPAA does not contemplate a retroactive breach mechanism, but the reputational and legal exposure of a future large-scale decryption event would be severe.

**The urgency case**: NIST's post-quantum cryptography migration guidance (2024) is explicit that organizations should begin inventory and migration now, citing exactly this threat model. A comprehensive cryptographic migration of a major health system takes 5–10 years. Starting in 2030 means the system is still partially vulnerable in 2040 — a window that may overlap with quantum cryptographic capability.
:::
::::

::::{exercise}
:label: ex-ch01-nisq-enterprise

**NISQ Posture for a Mid-Market Firm**

A regional bank with \$18 billion in assets and a team of 12 data scientists is evaluating whether to invest in a quantum computing capability. The CTO says the bank is "too small" to justify quantum investment until the technology matures. Using the NISQ-to-fault-tolerance roadmap, construct a phased quantum readiness plan for this bank that is proportionate to its size. What should they do *now*, *soon*, and *later*?

:::{dropdown} Solution

The CTO's instinct to avoid premature hardware investment is correct, but "too small to justify investment" confuses two different activities: *deploying quantum hardware* (expensive, premature) and *building quantum literacy* (low-cost, time-sensitive).

**Now (2025–2027): Awareness and cryptographic hygiene.**
- Assign one data scientist to complete IBM Quantum's free online certification and spend 20% of their time tracking quantum algorithm development relevant to portfolio optimization and fraud detection — two domains where quantum speedups are theoretically motivated.
- Commission a cryptographic inventory: audit all systems using RSA, ECDH, or TLS 1.2 and below. Develop a migration plan to post-quantum algorithms per NIST standards. Budget estimate: 1–2 months of one security engineer.
- Join IBM Quantum Network or a university quantum hub consortium for access to research-grade hardware and peer benchmarking at negligible cost.

**Soon (2027–2032): Targeted experiments and vendor engagement.**
- As early fault-tolerant hardware becomes available via cloud access, identify 2–3 specific portfolio optimization or fraud detection problem instances to benchmark against classical baselines.
- Begin evaluating quantum-safe cryptographic library vendors and test post-quantum TLS in non-production environments.
- Budget for cloud quantum compute credits at AWS Braket or IBM Quantum (\$10,000–50,000/year for meaningful experimentation).

**Later (2030+): Deployment where advantage is demonstrated.**
- If quantum advantage is confirmed for a specific banking application in this window, the bank will have the algorithmic knowledge, the vendor relationships, and the cryptographic infrastructure to deploy quickly — rather than starting from scratch.
- Total investment through the "now" and "soon" phases: approximately \$200,000–\$500,000 in staff time and cloud credits, orders of magnitude less than the competitive cost of being unprepared.
:::
::::

---

## Glossary

```{glossary}
Quantum Supremacy
  The milestone at which a quantum computer executes a specific task faster than any classical computer could in a practical timeframe. Google claimed this milestone in 2019 with the Sycamore processor on a random circuit sampling task. The term is controversial because "supremacy" is benchmark-specific and does not imply general computational superiority.

Quantum Advantage
  The broader and more commercially meaningful milestone at which a quantum computer solves a *practically relevant* problem faster or at lower cost than the best available classical approach. Quantum advantage is the goal; quantum supremacy is a specific, task-bounded demonstration that does not necessarily imply it.

NISQ
  Noisy Intermediate-Scale Quantum. A term coined by John Preskill in 2018 to describe quantum processors with 50–1,000 physical qubits that operate without full error correction. NISQ devices are the current state of quantum hardware and are expected to remain the dominant paradigm through approximately 2027.

Qubit
  A quantum bit — the fundamental unit of quantum information. Unlike a classical bit, which can be in state 0 or 1, a qubit can exist in a superposition of both states simultaneously. When measured, a qubit collapses to either 0 or 1 with probabilities determined by its quantum state.

Superposition
  The quantum mechanical property that allows a quantum system to exist in multiple states simultaneously until measured. For qubits, superposition enables quantum computers to explore many possible solutions to a problem in parallel, which underlies potential quantum speedups.

Entanglement
  A quantum mechanical correlation between two or more qubits such that the state of one qubit cannot be described independently of the others. Entanglement enables quantum parallelism and is a key resource for quantum algorithms that offer speedups over classical methods.

Decoherence
  The process by which a qubit loses its quantum properties due to interaction with the environment. Decoherence is the primary engineering challenge in quantum computing and is characterized by two timescales: T₁ (energy relaxation) and T₂ (phase decoherence).

T₁ (Relaxation Time)
  The characteristic time for a qubit in its excited state to spontaneously decay to its ground state. T₁ limits how long a qubit can hold quantum information. Typical values for superconducting qubits: 50–500 microseconds.

T₂ (Coherence Time)
  The characteristic time for a qubit to lose phase coherence — the quantum mechanical relationship between the two components of its superposition state. T₂ is always less than or equal to 2T₁. T₂ is typically the binding constraint on circuit depth in NISQ hardware.

Fault-Tolerant Quantum Computing (FTQC)
  A quantum computing architecture in which logical qubits are encoded in redundant arrays of physical qubits using error-correcting codes, enabling arbitrary-length computations by continuously detecting and correcting errors. Fault tolerance requires physical error rates below approximately 1% (the threshold theorem).

Surface Code
  The most widely studied quantum error correction code for fault-tolerant quantum computing. The surface code arranges qubits on a 2D lattice and detects errors by measuring stabilizer operators, without measuring the logical qubit state directly. It requires approximately 1,000 physical qubits per logical qubit at current error rates.

Shor's Algorithm
  A quantum algorithm published by Peter Shor in 1994 that factors large integers in polynomial time — compared to the best known classical algorithms, which require exponential (sub-exponential) time. Shor's algorithm, if run on a sufficiently large fault-tolerant quantum computer, would break RSA encryption.

Post-Quantum Cryptography (PQC)
  Cryptographic algorithms designed to be secure against attacks from both classical and quantum computers. NIST finalized the first PQC standards in 2024, based on mathematical problems (lattice problems, hash functions) that are believed to be hard even for quantum computers. Migration to PQC is the primary near-term action item for most organizations.

Harvest Now, Decrypt Later (HNDL)
  An attack strategy in which an adversary collects encrypted data today with the intention of decrypting it in the future when quantum computers become capable of breaking current public-key encryption. HNDL creates present-day urgency for post-quantum cryptographic migration even though quantum computers capable of breaking RSA do not yet exist.

Quantum Error Correction (QEC)
  A set of techniques that protect quantum information from errors by encoding logical qubits in entangled states of multiple physical qubits and measuring error syndromes without collapsing the logical qubit state. QEC is the enabling technology for fault-tolerant quantum computing.

Quantum Volume
  A metric developed by IBM to characterize the overall performance of a quantum computer, accounting for qubit count, connectivity, error rates, and circuit compilation efficiency. Higher quantum volume indicates a more capable device. Quantum volume doubles approximately every year for current leading systems.

Quantum Chemistry Simulation
  The use of quantum computers to model the quantum mechanical behavior of molecules and materials. This is considered the "killer app" of quantum computing because many industrially important problems — drug discovery, battery chemistry, catalyst design — involve electron correlation that cannot be accurately modeled classically for more than ~20 atoms.
```

---

## Leader's Takeaway

```{epigraph}
You don't need to predict when quantum arrives. You need to predict the year your competitors start acting as if it has.
```

The strategic insight of this chapter is not that quantum computers are coming — they already exist, however imperfectly. It is that *enterprise readiness* for quantum computing has a longer lead time than quantum hardware development, and that the asymmetry between preparedness and unpreparedness compounds over time.

The organizations in the enterprise vanguard — JPMorgan Chase, Mercedes-Benz, Airbus, BMW — are not running quantum computers in production. They are building the organizational antibodies: the technical staff, the problem vocabulary, the vendor relationships, and the algorithmic intuition that will allow them to recognize and deploy quantum advantage when it arrives in their specific domain. They are also, critically, addressing cryptographic risk today, before it becomes urgent.

The question for every executive reading this chapter is simpler than the physics suggests: What is your organization's quantum literacy today? Not your hardware investment — your literacy. Do your data scientists understand the difference between NISQ and fault-tolerant capability? Does your CISO have a cryptographic migration plan? Does your R&D function know which of its problems are quantum-amenable?

If the answer to these questions is no, the relevant action is not to purchase quantum hardware. The relevant action is to start building quantum literacy — through education, through pilot experiments on cloud quantum platforms, through a cryptographic inventory, and through a structured assessment of which business processes might benefit from quantum acceleration.

The cost of beginning that process today is modest. The cost of beginning it eighteen months after your competitors is compounding.

```{admonition} Chapter Summary
:class: note

- Quantum computing has crossed from physics experiment to enterprise agenda item, driven by three structural accelerants: geopolitics, AI convergence, and cryptographic risk.
- Market forecasts project \$450–850B in quantum value creation by 2035, with pharmaceuticals and finance as the primary sectors. Treat these as ranges, not point estimates.
- The current quantum investment cycle is structurally different from prior quantum winters: it is funded by corporate capital, supports near-term NISQ applications, and is sustained by national security mandates.
- The NISQ-to-fault-tolerance roadmap translates to three enterprise planning horizons: *now* (build literacy, begin cryptographic migration), *soon* (deploy early commercial experiments), and *later* (broad transformation).
- The cryptographic risk from quantum computing creates present-day organizational exposure through the harvest-now-decrypt-later threat. Organizations should begin post-quantum cryptographic migration regardless of their broader quantum strategy.
- The Google Sycamore episode teaches the essential skill of reading quantum milestone announcements: ask what task, what classical baseline, and what problem size before drawing strategic conclusions.
```
