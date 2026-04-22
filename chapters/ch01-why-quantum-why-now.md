---
title: "Chapter 1: The $850 Billion Question — Why Quantum, Why Now"
subtitle: "From Physics Experiment to Enterprise Agenda"
short_title: "Ch. 1: Why Quantum, Why Now"
description: "Quantum computing has crossed from physics experiment to enterprise agenda item. This chapter explains why — through market forecasts, historical context, three structural accelerants, and a roadmap from NISQ to fault-tolerant systems. Includes the FAU-D-Wave partnership as a landmark case study."
label: ch-01-why-quantum-why-now
tags: [quantum computing, business strategy, NISQ, fault tolerance, market forecasts, quantum winters, D-Wave, FAU, annealing]
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

If you are reading this at Florida Atlantic University, there is a more immediate framing: a production-grade quantum computer is being installed on your campus. Not at MIT. Not at Caltech. Here. The strategic question is no longer abstract.

---

## Opening Scene: Two Moments, Six Years Apart

### October 2019 — Mountain View, California

The paper landed in *Nature* on October 23, 2019, under a title that read like a physics journal article and hit financial news desks like a press release. Google's team, led by researcher John Martinis and his colleagues at the University of California Santa Barbara, announced that their 53-qubit processor — named Sycamore — had performed a specific computational task in approximately 200 seconds. Their estimate: the same task would take the world's fastest classical supercomputer, Summit at Oak Ridge National Laboratory, roughly 10,000 years.

The phrase embedded in the abstract was deliberate: *quantum supremacy*.

Press coverage was immediate and overwhelming. IonQ stock surged when it eventually went public; IBM, Honeywell, and a constellation of quantum startups saw increased investor attention within days. For one news cycle, it felt as though the future had arrived early and was asking for a parking spot.

Then IBM fired back.

Within 24 hours, IBM's research team published a pointed technical rebuttal arguing that Summit could solve the same problem in approximately 2.5 days, not 10,000 years, given optimized classical algorithms and sufficient disk storage. The argument was technically sound. "Quantum supremacy," IBM argued, was a marketing claim dressed as a scientific milestone.

Wall Street, characteristically, called it Monday.

Six years later, the Google-IBM dispute feels less like a conflict and more like a parable. Both sides were correct about different things. What mattered most was not the 10,000-year claim. What mattered was that the largest internet company on Earth had deployed over a billion dollars in quantum hardware research, published in the world's most prestigious scientific journal, and used the word *supremacy*. The enterprise world began paying attention.

### January 2026 — Boca Raton, Florida

On January 27, 2026, Florida Atlantic University President Adam Hasner stood alongside Alan Baratz, CEO of D-Wave Quantum Inc., at the D-Wave Qubits26 conference — held in Boca Raton — and announced a $20 million agreement to install a D-Wave Advantage2 quantum computer on FAU's Boca Raton campus. FAU became the first university in Florida to publicly host a large, dedicated quantum computer on-site.

On the same day, D-Wave announced it would establish its new corporate headquarters at the Boca Raton Innovation Center, four miles from FAU's main campus. South Florida, in a single morning, became one of the most significant quantum computing hubs in the United States.

For students in this course, the implication is concrete: you have access to production-grade quantum hardware that enterprises around the world are paying hundreds of thousands of dollars per year to access through cloud queues. The Advantage2 system — the same class of machine being used by BASF to compress manufacturing scheduling from hours to seconds, by logistics firms to solve vehicle routing problems with millions of constraints, and by defense organizations to run secure optimization at scale — will be available for your coursework.

The $850 billion question is no longer hypothetical. It is a question this university has already answered with a nine-figure investment.

---

:::{note} Plain Language: What Does a Quantum Computer Actually *Do* Differently?

Before we go further, let's answer the question that textbooks often skip: not *that* quantum computers are powerful, but *why* — and what that means for business.

**Start with something familiar.** Imagine you're lost in a massive hedge maze with a trillion branches. A classical computer is like a very fast person who sprints down every path one at a time. Given enough speed, it will find the exit — but for a trillion-branch maze, "enough speed" means billions of years. You can make the sprinter faster, give them better shoes, let them run in parallel with a thousand clones: they still face the same exponentially growing problem. This is why "just build a faster classical computer" doesn't solve it. The number of paths grows faster than any speed improvement can address.

**The bridge.** A quantum computer doesn't run faster through the same maze. It operates on a fundamentally different principle. Each qubit — the quantum equivalent of a classical bit — can exist in a *superposition* of 0 and 1 simultaneously. Not "somewhere in between," but genuinely both, until you measure it. Fifty qubits in superposition can represent 2⁵⁰ possible states (roughly a quadrillion) *all at once*. Quantum algorithms are then carefully designed to use *interference* — the wave-like cancellation and amplification that governs quantum mechanics — to suppress the wrong answers and amplify the right one before measurement.

**Two paradigms, not one.** There are actually two distinct approaches to quantum computing, and both will appear throughout this course. *Gate-model* quantum computers — IBM, Google, IonQ — build computation from sequences of quantum gates, analogous to how classical computers build programs from logic gates. *Quantum annealers* — like FAU's D-Wave Advantage2 — take a different approach: they encode a problem as the lowest-energy configuration of a quantum system and let the system naturally settle toward the answer, exploiting quantum tunneling to escape local minima that trap classical optimizers. Gate-model systems are more general-purpose but more fragile. Annealers are purpose-built for optimization problems and available for production use today.

**Why this matters for business.** Quantum's advantage is *structural*, not just quantitative. For problems where the solution space grows exponentially — drug molecule simulation, portfolio optimization across thousands of correlated assets, logistics routing with millions of constraints, breaking public-key encryption — no amount of classical engineering closes the gap. The organizations investing in quantum today are not betting that classical computers will run out of steam. They are betting that specific high-value problems in their industries belong to the class where quantum's different architecture delivers qualitatively better answers.
:::

---

## The Single Idea

```{epigraph}
Quantum computing has crossed from physics experiment to enterprise agenda item — not because it is finished, but because the cost of being late now exceeds the cost of being early.
```

This idea deserves unpacking, because it runs counter to the usual technology-adoption instinct. Most enterprise technology decisions reward patience. Early adopters of enterprise software, cloud infrastructure, and even artificial intelligence frequently overpaid for immature systems and spent years managing the technical debt. The conventional wisdom — *let the technology mature before committing* — has been empirically validated in dozens of technology waves.

Quantum computing appears to be the exception, for three reasons that will occupy the rest of this chapter.

First, the strategic preparation required for quantum advantage is long-lead. Identifying which business processes are genuinely quantum-amenable, retraining technical staff, building vendor relationships, and beginning cryptographic migration all take years. Starting that preparation when quantum hardware matures means starting too late.

Second, the competitive landscape is not waiting. As of 2026, JPMorgan Chase employs a team of quantum researchers. BASF uses D-Wave hybrid solvers in production manufacturing scheduling. Volkswagen has run quantum optimization pilots for logistics routing. The organizations that treat quantum computing as a "2030 problem" are competing against organizations that started treating it as a "2024 investment."

Third, and most urgently: the cryptographic threat is not contingent on quantum computers being useful for optimization or simulation. A quantum computer capable of running Shor's algorithm at scale breaks most of the public-key cryptography currently protecting the internet. Adversaries are harvesting encrypted data today. The migration window has already opened.

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

The headline figure of \$850 billion comes from McKinsey Global Institute's 2021 analysis, projecting that quantum computing could generate between \$450 billion and \$850 billion in value across four sectors by 2035: pharmaceuticals and chemicals, finance, logistics and mobility, and materials science. The range — nearly a factor of two — reflects three genuinely uncertain variables: hardware scaling timelines, application discovery rates, and competitive market dynamics.

BCG's parallel analysis, updated in 2023, projected a more conservative base case of \$450 billion but noted that the pharmaceutical sector alone could see \$50–\$100 billion in value creation from accelerated drug discovery. Goldman Sachs revised its quantum forecast upward in 2023, citing accelerating hardware progress and the post-NIST urgency around cryptographic migration. IBM's market projections suggest a "quantum utility" inflection point arriving in the late 2020s for specific narrow applications.

What do these ranges tell a strategist? Several things:

**The sectors are consistent across forecasters.** Every major analysis identifies the same four domains as primary value capture zones: (1) pharmaceutical simulation, where quantum chemistry can model molecular interactions at a level of fidelity inaccessible to classical computers; (2) financial optimization, where portfolio construction, risk modeling, and derivative pricing involve combinatorial problems that scale poorly classically; (3) logistics and supply chain, where route optimization and scheduling represent tractable near-term quantum applications — including on D-Wave annealing hardware today; and (4) materials science and battery chemistry, where quantum simulation of electron behavior could unlock next-generation energy storage.

**The timelines are wide and honestly so.** The difference between a \$450 billion and \$850 billion outcome by 2035 largely depends on whether certain hardware thresholds are crossed in 2028 or 2032. Nobody knows. Forecasters who offer narrower ranges are making unstated assumptions about hardware progress they cannot fully justify.

**The floor is nonzero and rising.** Even pessimistic scenarios project meaningful quantum value creation. The era when the honest answer was "possibly never" has passed. The question is when and how much, not whether.

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

**The Mid-Cycle Thaw and Second Cooling (1994–2015)** began dramatically when Peter Shor published his polynomial-time quantum algorithm for integer factorization in 1994. The implications were immediate: a sufficiently powerful quantum computer could break RSA encryption. DARPA, NSA, and corporate research labs injected significant funding. But hardware progress was brutally slow. Building a stable qubit required isolating a quantum system from all environmental noise — a challenge that consumed two decades of experimental physics. By the mid-2000s, public and private funding had again contracted, though classified government investment continued.

**The Current Cycle (2015–present)** is structurally different from both predecessors in four distinct ways.

First, it is funded by *corporate capital*, not primarily by government grants. Google, IBM, Microsoft, Amazon, D-Wave, IonQ, and Quantinuum have each invested billions. This capital does not disappear when a five-year grant cycle ends.

Second, there is a clear *near-term application path* — and not just a theoretical one. D-Wave's hybrid quantum-classical solvers are running in production today at companies including BASF, Volkswagen, and Mastercard, solving optimization problems at scales and speeds that classical solvers cannot match. This is not "promising research" — it is deployed enterprise software generating measurable ROI.

Third, the *geopolitical context* has transformed the funding calculus. China's National Laboratory for Quantum Information Sciences, opened in Hefei in 2020 with an estimated \$10 billion budget, turned quantum computing into a national security priority. The United States responded with the National Quantum Initiative Act (2018, renewed 2023), the CHIPS and Science Act (2022), and a constellation of DOE, DARPA, NSF, and intelligence community programs exceeding \$3 billion in federal commitment.

Fourth, the *ecosystem* has matured irreversibly. The International Conference for High Performance Computing (SC — Supercomputing) now features a dedicated quantum computing track, reflecting the consensus that quantum is the natural successor to the high-performance computing paradigm that has driven scientific discovery for four decades. SC26, scheduled for Chicago in November 2026, will feature quantum-HPC hybrid architectures as a primary technical theme — including sessions drawing directly on FAU's on-campus Advantage2 deployment as a case study in institutional quantum integration.

```{admonition} Why Past Winters Are Not Predictive
:class: warning

It is tempting to argue that because quantum computing has disappointed before, it will disappoint again. This reasoning fails to account for structural differences: the current cycle has corporate capital, government security mandates, real production deployments on D-Wave hardware, and a global developer ecosystem. The base case is no longer "wait and see" — it is "prepare while the hardware matures."
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

**Global Quantum Investment, 2020–2026.** National quantum programs are no longer discretionary research investments — they are strategic infrastructure, treated with the same urgency as semiconductor supply chains and satellite communications.
:::

The geopolitical dimension of quantum computing is perhaps the least appreciated by enterprise strategists and the most consequential for long-term investment trajectories. Governments fund quantum research because quantum computers offer decisive asymmetric advantages in three national security domains: signals intelligence (breaking adversary communications), materials simulation (advanced weapons design), and optimization (logistics superiority in military operations).

The United States National Quantum Initiative Act, signed in 2018 and renewed in 2023, has channeled over \$3 billion in federal quantum commitments across the Department of Energy, NSF, DARPA, NIST, and the intelligence community. The European Union's Quantum Flagship program committed €1 billion over ten years. The United Kingdom published a £2.5 billion National Quantum Strategy in 2023. Australia, Canada, Japan, South Korea, and India each launched national quantum programs between 2021 and 2024.

China's investments are harder to audit but by most independent estimates dwarf Western programs. The National Laboratory for Quantum Information Sciences alone reportedly received \$10 billion in initial funding. Chinese researchers publish more quantum computing papers annually than any other nation. The Micius satellite, which demonstrated quantum key distribution at intercontinental distances in 2017, was a signal — both technical and geopolitical — that China is not a follower in this field.

**The HPC-Quantum connection.** For readers coming from a high-performance computing background — including those who have followed SC (Supercomputing) conferences over the years — the quantum investment story is the next chapter of a familiar narrative. The argument for national HPC leadership in the 1990s was the same: computing power is strategic infrastructure, not just a research tool. The organizations and governments that led in HPC built decades-long competitive advantages in weather modeling, nuclear simulation, financial modeling, and drug discovery. Quantum computing is following the same trajectory, with the same national security underpinning and the same commercial spillover potential. SC26's quantum track is a recognition that the HPC community — the people who built and ran supercomputing centers for three decades — is now the natural workforce for quantum-HPC hybrid systems.

The enterprise implication is straightforward: when governments treat a technology as a national security priority, the funding does not dry up when commercial timelines slip. The current quantum investment cycle is structurally supported by strategic imperatives that are immune to quarterly earnings pressure.

### Accelerant Two: AI Convergence

The relationship between quantum computing and artificial intelligence is not one of substitution — quantum computers will not replace AI accelerators — but of *synergistic expansion*. Two convergence pathways matter for business strategy.

**Quantum-enhanced machine learning** (QML) explores whether quantum circuits can provide computational advantages for specific learning tasks. Theoretical results suggest quadratic speedups for certain linear algebra operations that underlie neural network training. Practical demonstrations remain limited to near-term hardware, but companies like Quantinuum have published QML results suggesting near-term applications in drug discovery and materials classification.

**Classical AI accelerating quantum development** is the more immediately impactful pathway. Google DeepMind's work on protein structure prediction demonstrated that transformer architectures could tackle problems previously proposed as quantum use cases. More directly: Google's quantum team used machine learning to optimize qubit calibration, error correction protocols, and circuit compilation. IBM uses AI to predict qubit decoherence events and schedule circuit execution accordingly. AI is becoming a critical tool in the quantum engineering toolchain.

The convergence creates a flywheel: better AI tools accelerate quantum hardware development, which enables more ambitious quantum experiments, which generate training data for AI models that further optimize quantum systems. Organizations with deep AI capabilities — the hyperscalers, large pharmaceutical companies, and research universities — are positioned to benefit from this flywheel more quickly than organizations without them. FAU's dual investment in AI and quantum computing is a direct bet on this flywheel.

### Accelerant Three: Cryptographic Risk

:::{figure} ../images/ch01-cryptographic-risk.png
:label: fig-ch01-cryptographic-risk
:alt: Infographic showing cryptographic risk from quantum computing, including the harvest-now-decrypt-later threat and the NIST post-quantum cryptography migration path.
:width: 100%
:align: center

**The Cryptographic Threat Timeline.** The "harvest now, decrypt later" attack requires no quantum computer today — only the patience to store encrypted data until one becomes available. Organizations with long data-life assets face a threat that exists in the present, not the future.
:::

Of the three accelerants, cryptographic risk is the only one that creates *current* organizational exposure. It does not require waiting for a quantum computer to become commercially useful.

The mechanism is known as "harvest now, decrypt later" (HNDL). Adversaries — nation-states, primarily — are currently collecting encrypted internet traffic at scale: diplomatic cables, financial transactions, intelligence communications, medical records, trade secrets. All of it is currently encrypted with public-key algorithms (RSA, ECDH) that rely on the mathematical difficulty of factoring large integers. Shor's algorithm, running on a sufficiently large fault-tolerant quantum computer, solves that problem in polynomial time.

The adversary does not need the quantum computer today. They need it before the data expires. For diplomatic cables, that might be twenty years. For trade secrets, perhaps ten. For medical records, indefinitely.

NIST finalized the first post-quantum cryptography (PQC) standards in August 2024. The winners — ML-KEM (formerly CRYSTALS-Kyber) for key encapsulation and ML-DSA (formerly CRYSTALS-Dilithium) for digital signatures — are lattice-based algorithms designed to resist both classical and quantum attacks. NIST's guidance is explicit: organizations should begin migration *now*. Most complex organizations need five to ten years for a full cryptographic migration.

```{admonition} Action Item: Cryptographic Inventory
:class: important

Any organization that handles data with a useful life exceeding five years should initiate a cryptographic inventory — an audit of all systems using RSA, ECDH, or similar quantum-vulnerable algorithms. This is not a quantum computing project. It is a cybersecurity project motivated by quantum computing.
```

---

## The NISQ-to-Fault-Tolerance Roadmap

:::{figure} ../images/ch01-nisq-to-ft-roadmap.png
:label: fig-ch01-nisq-to-ft-roadmap
:alt: Roadmap diagram showing quantum computing progression through three phases: NISQ Now, Early Fault Tolerance Soon, and Mature Fault Tolerant Later.
:width: 100%
:align: center

**From NISQ to Fault-Tolerant Quantum Computing.** The three-phase roadmap translates physics milestones into enterprise planning horizons.
:::

The term *NISQ* — Noisy Intermediate-Scale Quantum — was coined by physicist John Preskill in 2018. Understanding the roadmap from NISQ to fault-tolerant systems is essential for calibrating enterprise expectations. Note that *two* quantum paradigms live in this roadmap simultaneously: gate-model hardware (IBM, Google, IonQ) progressing from NISQ toward fault tolerance, and quantum annealing hardware (D-Wave) which has a different maturity profile — D-Wave's Advantage2 is already production-grade for optimization workloads, while gate-model fault tolerance remains years away.

````{tab-set}
```{tab-item} Now: NISQ + Production Annealing (2024–2028)
**Gate-model hardware:** 100–1,000+ physical qubits, error rates of 0.1–1% per gate, circuit depth limited to ~100 layers. IBM's Eagle, Heron, and Condor series; Google's Willow (105 qubits, demonstrated below-threshold error correction in December 2024); IonQ Forte.

**Annealing hardware (production-ready):** D-Wave Advantage2 — 7,000+ qubits, production-grade hybrid solver (Stride), available on-premises (FAU) and via D-Wave Leap cloud. Enterprise deployments running today at BASF, Volkswagen, Mastercard, and others.

**Enterprise posture:** Build expertise, begin cryptographic migration, run proof-of-concept experiments on cloud quantum hardware. For optimization problems: serious pilots on D-Wave Stride are appropriate now — not "one day." For simulation, chemistry, and ML: research and prototyping posture.

**Key milestone to watch:** Google Willow's demonstration of below-threshold error correction (December 2024) is the most significant hardware milestone in a decade — it confirms the fault-tolerance pathway is physically real.
```

```{tab-item} Soon: Early Fault Tolerance (2027–2032)
**Hardware:** 10,000–1,000,000 physical qubits encoding 100–10,000 *logical* qubits with error rates below the fault-tolerance threshold. Error correction overhead reduces effective qubit count by 100–1,000x.

**Capabilities:** Narrow commercial quantum advantage in pharmaceutical simulation (specific drug-target binding problems), financial optimization (certain portfolio construction tasks), and materials discovery. These advantages are domain-specific and require quantum-native algorithm development.

**Enterprise posture:** Organizations with a quantum-ready team and a mapped portfolio of quantum-amenable problems will deploy early commercial applications. Those without are entering a 3–5 year catch-up cycle.

**Key milestone to watch:** First peer-reviewed demonstration of quantum advantage on a commercially relevant problem instance — not a synthetic benchmark.
```

```{tab-item} Later: Mature Fault Tolerance (2032+)
**Hardware:** Millions of physical qubits, thousands of logical qubits, error rates low enough to run Shor's algorithm at commercially relevant key sizes.

**Capabilities:** Broad pharmaceutical simulation, full cryptographic threat realization, logistics optimization at supply-chain scale, climate modeling, financial market simulation.

**Enterprise posture:** Organizations that have not prepared face existential competitive and security risks. The asymmetry between prepared and unprepared organizations becomes severe.

**Key milestone to watch:** NIST's post-quantum cryptography migration deadline — 2030 for most federal systems, implying 2030–2033 for critical private sector systems.
```
````

```{prf:definition} NISQ Era
:label: def-nisq-era

A **Noisy Intermediate-Scale Quantum (NISQ)** computer is a quantum processor with 50–1,000 physical qubits operating without full error correction. NISQ devices can run short quantum circuits but accumulate errors that limit circuit depth and problem size.
```

```{prf:definition} Fault-Tolerant Quantum Computing
:label: def-ftqc

A **fault-tolerant quantum computer (FTQC)** encodes logical qubits in redundant arrays of physical qubits using quantum error correction codes. When physical error rates fall below approximately 1%, error correction suppresses errors exponentially as code distance increases, enabling arbitrarily long computations.
```

:::{note} Plain Language: NISQ vs. Fault-Tolerant vs. Annealing — Three Stages, One Story

These terms describe different stages and paradigms of quantum hardware. Mixing them up is the most common source of confusion in quantum strategy discussions.

**Think of three vehicle types, not three generations of the same car.**

A **NISQ gate-model computer** is the Formula 1 car under development: blindingly fast at specific tasks, but fragile, expensive to run, requires a specialist crew, and breaks down frequently. It can lap an ordinary car on a closed circuit. You wouldn't use it for a road trip.

A **production quantum annealer** (like FAU's D-Wave Advantage2) is more like a specialized off-road vehicle purpose-built for a specific terrain — optimization problems with millions of variables. It handles that terrain better than anything else available today. It is not trying to be a Formula 1 car. For its intended problem class, it wins. You can rent one right now.

A **fault-tolerant quantum computer** is the autonomous vehicle that doesn't exist yet but is clearly coming: a general-purpose quantum system reliable enough to run any quantum algorithm without errors accumulating. When it arrives, it changes everything. For now, it lives on roadmaps.

**The enterprise implication.** The mistake most strategy documents make is treating quantum computing as a single, monolithic technology that is either "ready" or "not ready." In reality: quantum annealing for optimization is ready now (D-Wave Advantage2). Gate-model experiments are viable now for research and narrow applications. Fault-tolerant quantum computing is not ready and won't be for years. Each paradigm has its own readiness timeline, its own problem class, and its own enterprise action items.
:::

---

## Flagship Case Study: FAU and D-Wave — Quantum Comes to Boca Raton

:::{figure} ../images/ch01-google-sycamore-case-study.png
:label: fig-ch01-fau-dwave-case-study
:alt: Case study infographic about FAU's $20 million D-Wave Advantage2 partnership announced January 2026.
:width: 100%
:align: center

**FAU and D-Wave: A Landmark Institutional Quantum Investment.** The January 2026 agreement positions FAU as Florida's first university to host an on-premises production quantum computer — and Boca Raton as a national quantum hub.
:::

### Situation

On January 27, 2026, Florida Atlantic University signed a $20 million agreement with D-Wave Quantum Inc. (NYSE: QBTS) to acquire and install a D-Wave Advantage2 annealing quantum computer on the Boca Raton campus. The announcement was made at D-Wave's Qubits26 conference, held locally — a choice of venue that was itself a signal. On the same day, D-Wave announced it would relocate its corporate headquarters to the Boca Raton Innovation Center, cementing South Florida as a major U.S. quantum technology hub.

FAU became the first university in Florida — and one of a small number of universities in the world — to publicly host a large, dedicated quantum computer on-site. The distinction matters: most university quantum programs access hardware through cloud queues, waiting hours or days for computation time on shared systems. FAU's on-premises deployment means priority access, direct system integration, and the ability to run experiments at the depth and iteration speed that real research and real coursework require.

### Quantum Angle

The D-Wave Advantage2 is an annealing quantum computer, not a gate-model system. It contains over 7,000 qubits connected in D-Wave's proprietary Pegasus topology, and it is paired with D-Wave's Stride hybrid solver — a classical-quantum hybrid system that decomposes large optimization problems into subproblems suitable for the quantum annealer, then coordinates the results using a classical optimizer. The combination enables problems with millions of variables and constraints to be solved in seconds to minutes — problem scales that exceed what pure-quantum or pure-classical approaches can match today.

The Advantage2 is the same class of machine currently used in production by:
- **BASF** — compressing manufacturing scheduling from hours to seconds
- **Volkswagen** — optimizing paint-shop sequencing in automotive production
- **Mastercard** — fraud pattern detection across transaction graphs
- **Verge Ag** — real-time routing for autonomous agricultural equipment
- **Defense organizations** — classified optimization applications

This is not a research demonstration. These are production deployments generating operational ROI.

### Decisions Made

FAU's decision to acquire the Advantage2 rather than relying on cloud access reflects several strategic calculations. First, on-premises access eliminates latency and queue delays that make iterative research impractical in a cloud model. Second, the presence of the physical hardware attracts industry partnerships — companies with quantum optimization problems will partner with the university that has the machine they need. Third, the co-location of D-Wave's headquarters in Boca Raton creates a direct pipeline for student placement, joint research, and curriculum development. FAU is not buying a computer; it is buying an ecosystem position.

The decision also reflects FAU's broader trajectory in advanced computing. The university has operated high-performance computing (HPC) infrastructure for research for over a decade, providing the organizational experience — computational support staff, research computing governance, industry partnership frameworks — that makes the quantum transition operationally feasible. For universities without that HPC foundation, hosting production quantum hardware would be significantly more complex.

### Measured Outcome

At the time of this writing, the Advantage2 installation is pending — expected later in 2026. The outcomes measurable today are organizational: D-Wave's local headquarters presence, the Qubits26 conference held in Boca Raton, and the curricular programs (including this course) being developed around the hardware. The operational outcomes — research publications, industry partnerships, student placements, optimization use cases solved — will accumulate over a 5–10 year horizon.

What is already measurable is competitive positioning. No other university in Florida offers students hands-on access to production quantum hardware. No other MBA program in the Southeast can claim coursework that runs on a real quantum computer — not a simulator, not a cloud queue — and connects to a corporate ecosystem co-located with the institution.

### Open Question

FAU's Advantage2 deployment raises a question that every organization considering quantum investment must answer: *What is the right problem to run first?* The Advantage2 excels at combinatorial optimization — vehicle routing, scheduling, portfolio construction, logistics sequencing. FAU's research strengths span engineering, business, ocean science, and medicine. Which of these domains has an optimization problem worth solving at quantum scale?

This is not a rhetorical question. Part of your work in this course is to formulate that answer — to identify a real problem, model it for the Advantage2, and evaluate whether quantum treatment produces results that matter. The hardware is not a demonstration. It is a tool. Your job is to use it well.

---

## Industry Snapshots: The Enterprise Vanguard

:::{figure} ../images/ch01-industry-snapshots.png
:label: fig-ch01-industry-snapshots
:alt: Four-quadrant infographic showing JPMorgan Chase, Mercedes-Benz, Airbus, and BASF adopting quantum computing for specific use cases.
:width: 100%
:align: center

**The Enterprise Vanguard.** Four organizations from different sectors illustrate how quantum investment looks in practice: not as a replacement for classical systems, but as a targeted capability for specific high-value problems.
:::

### JPMorgan Chase: Portfolio Optimization at Scale

JPMorgan Chase operates one of the largest quantum research programs in the financial services industry. The bank's quantum group has published peer-reviewed research on quantum algorithms for option pricing, portfolio optimization, and Monte Carlo simulation acceleration. Their work on a quantum algorithm for derivative pricing — published in collaboration with IBM in 2019 — demonstrated a theoretically quadratic speedup for a simplified options pricing model.

The practical implication is not that JPMorgan runs options pricing on a quantum computer today. It is that their quantitative analysts understand the algorithm landscape well enough to recognize, when early fault-tolerant hardware becomes available, whether a specific portfolio construction or risk calculation qualifies for quantum treatment. They are building the organizational antibodies for quantum integration.

Separately, JPMorgan has piloted quantum key distribution links between offices as part of post-quantum cryptographic readiness evaluation. Their annual reports have acknowledged cryptographic migration as a top-five cybersecurity priority since 2023.

### BASF: Manufacturing Scheduling in Seconds

BASF, the world's largest chemical company, has deployed D-Wave's hybrid quantum-classical solver in production for chemical plant scheduling — one of the most operationally complex optimization problems in industrial manufacturing. A single BASF plant runs thousands of interdependent processes with timing constraints, feedstock availability windows, equipment maintenance schedules, and regulatory compliance requirements. Classical scheduling algorithms, even well-tuned heuristics, require hours to generate a feasible schedule for a large plant.

D-Wave's Stride hybrid solver — the same system available on FAU's Advantage2 — reduced BASF's scheduling computation from hours to seconds. The operational impact: the ability to replan in real time when disruptions occur (equipment failures, supply delays, demand spikes), rather than running overnight batch optimization. BASF has described the deployment as a competitive differentiator, not a research experiment.

The BASF case is the most important enterprise quantum case study of the current era because it is unambiguous: quantum hardware running in production, solving a commercial problem, delivering measurable operational ROI. Not a proof of concept. Not a benchmark. A deployed system.

### Airbus: Aerodynamic Optimization

Airbus's quantum computing program illustrates a different entry point: gate-model QAOA for combinatorial optimization. Aircraft loading optimization, fleet scheduling, and supply chain logistics involve combinatorial problems that grow exponentially with problem size under classical approaches.

Airbus has run pilots using QAOA for aircraft loading optimization — determining how to distribute cargo weight across a fleet to minimize fuel consumption while satisfying complex constraints. Early results were honest about the current state: QAOA on today's hardware does not yet outperform state-of-the-art classical solvers for production problem sizes. But the research established that the algorithm structure is sound, and that as qubit counts and circuit depths improve, the advantage gap narrows. Airbus has integrated quantum computing into its digital transformation program, training engineers across multiple business units.

### Mercedes-Benz: The Battery Chemistry Frontier

Mercedes-Benz entered a research partnership with IBM Quantum specifically to explore quantum simulation of lithium-sulfur battery chemistry. Lithium-sulfur batteries could offer twice the energy density of lithium-ion at lower cost — but the electron transfer dynamics involve quantum mechanical interactions that classical simulation cannot model accurately for more than ~20 atoms.

The program does not expect production-ready quantum simulation capability until the early fault-tolerance era. But beginning the research now means that when the hardware crosses the threshold of utility, Mercedes-Benz researchers already know which problems to run on it, which algorithms to use, and what "quantum advantage" looks like for their specific chemistry questions. The organization that knows exactly which molecular simulation problem it will run on early fault-tolerant hardware has a significant first-mover advantage over the organization that starts problem identification after the hardware arrives.

---

## Unit Economics: Reading the Forecast Landscape

The \$850 billion headline deserves structural analysis.

| Sector | Low Estimate | High Estimate | Primary Application |
|--------|-------------|---------------|---------------------|
| Pharmaceutical & Chemicals | \$200B | \$340B | Drug discovery, materials simulation |
| Finance | \$110B | \$180B | Portfolio optimization, risk modeling |
| Mobility & Logistics | \$90B | \$150B | Route optimization, fleet scheduling |
| Materials Science | \$50B | \$180B | Battery chemistry, semiconductor design |
| **Total** | **\$450B** | **\$850B** | |

: McKinsey Global Institute quantum value forecast by sector, 2035 horizon. *Source: McKinsey Global Institute (2021). "A Quantum Decade."* {#tbl-ch01-forecast}

The pharmaceutical number dominates the forecast — bringing a single successful drug to market two years faster is worth several billion dollars in NPV. The logistics number is relevant today: D-Wave's Stride solver is already delivering measurable ROI in routing and scheduling deployments, suggesting the low end of the mobility/logistics estimate may prove conservative.

```{admonition} What the Forecast Assumes
:class: note

The McKinsey \$450–850B range depends on at least three structural assumptions: **(1)** Early fault-tolerant hardware capable of useful quantum chemistry simulations arrives in the 2028–2032 window. **(2)** Enterprises deploy quantum-ready workflows within 3–5 years of hardware availability — requiring they start building capability now. **(3)** Classical computing does not achieve equivalent breakthroughs (e.g., AI-accelerated molecular simulation) that close the value gap before quantum hardware matures. Each can be contested. The range captures this uncertainty explicitly.
```

---

## Productive-Struggle Problem

```{admonition} Productive Struggle: Load-Bearing Assumptions
:class: important

**Scenario:** You are a strategy analyst at a large healthcare system. Your CTO has shared the following one-paragraph forecast excerpt:

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
*Confidence: Low-to-medium.* IBM's public roadmap targets "quantum-centric supercomputing" milestones by 2029, and Google's December 2024 Willow result demonstrated below-threshold error correction — the most significant hardware milestone in a decade. However, the jump from demonstrating error correction in a controlled benchmark to running commercially useful quantum chemistry at scale requires further engineering progress that has historically taken longer than projected. A bear case in which hardware slips to 2033 pushes the entire value forecast timeline right by 4 years, roughly halving the 2035 NPV.
*Monitor:* IBM Quantum, Google Quantum AI, and Quantinuum annual hardware reports; academic publications on surface code error thresholds.

**Assumption 2: 3-year enterprise adoption lag.**
*Confidence: Low.* Enterprise software adoption timelines routinely exceed projections by 2–3x. Cloud computing adoption took 7–10 years in most large healthcare systems; AI adoption in clinical workflows has lagged commercial availability by 5–8 years in many organizations. A 3-year adoption lag requires that healthcare systems begin building quantum capability *before* the hardware arrives — which is precisely the argument of this chapter.
*Monitor:* Survey data on enterprise quantum workforce investment; number of quantum-certified developers in target industries.

**Assumption 3: Classical AI does not close the gap.**
*Confidence: Medium.* AlphaFold demonstrated that deep learning could solve protein structure prediction — a problem proposed as a quantum use case for a decade. However, electron correlation problems in quantum chemistry involve computational complexity classes that classical AI cannot efficiently approximate. The risk is domain-specific, not global.
*Monitor:* Publications in *Nature Chemistry* and *Journal of Chemical Theory and Computation* on AI-classical methods for electron correlation.

**The meta-lesson:** Every market forecast for a long-lead technology rests on assumption chains. The weakest assumption is usually the one about enterprise readiness, not hardware performance.
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

Distinguish the two prior quantum winters from the current investment cycle by identifying at least three structural differences: corporate capital durability, production D-Wave deployments, and geopolitical security mandates.
:::

:::{grid-item-card} Outcome 3
:class-header: bg-primary text-white
**Three Accelerants**

Identify and explain the three structural accelerants (geopolitics, AI convergence, cryptographic risk) and describe why cryptographic risk creates present-day organizational exposure independent of quantum hardware maturity.
:::

:::{grid-item-card} Outcome 4
:class-header: bg-primary text-white
**NISQ-to-FT Roadmap**

Summarize the NISQ-to-fault-tolerance roadmap in executive language, distinguishing gate-model and annealing paradigms, and mapping the three phases to "now, soon, later" enterprise planning horizons.
:::

:::{grid-item-card} Outcome 5
:class-header: bg-warning text-white
**Forecast Evaluation**

Given any quantum market-sizing forecast, surface its load-bearing assumptions regarding hardware timeline, enterprise adoption lag, and classical computing alternatives, and assess each assumption's confidence level.
:::
::::

---

## Lab 1A (Regular): Touring IBM Quantum Platform

### Overview

IBM Quantum (quantum.ibm.com) provides cloud access to real gate-model quantum processors. This lab introduces you to the platform and the operational realities of quantum computing — error rates, qubit coherence times, and queue dynamics that do not appear in any press release.

### Prerequisites

- A web browser and an email address
- No programming experience required

### Procedure

**Step 1: Create Your Account**
Navigate to [quantum.ibm.com](https://quantum.ibm.com) and create a free IBM Quantum account. Verify your email. You will have access to IBM's free-tier processors.

**Step 2: Explore the Hardware Catalog**
Navigate to "Compute resources." You will see processors — *ibm_brisbane*, *ibm_kyiv*, *ibm_torino* — each showing qubit count, queue depth, and operational status.

**Step 3: Read Calibration Data**
Click on any operational processor. The calibration table shows:

| Metric | What It Measures | Typical Value |
|--------|-----------------|---------------|
| **T₁ (relaxation time)** | How long a qubit holds its excited state | 50–500 µs |
| **T₂ (dephasing time)** | How long a qubit maintains coherence | 30–300 µs |
| **Gate error rate** | Probability of error per two-qubit gate | 0.1–1% |
| **Readout error** | Probability of misreading a qubit's state | 1–5% |

: IBM Quantum calibration metrics. {#tbl-ch01-calibration}

Note the *variation across qubits* on the same chip. This non-uniformity defines NISQ hardware and directly impacts circuit design.

**Step 4: Observe Live Jobs**
Navigate to the queue visualization. Note jobs queued, wait times, and how queue depth varies by time of day. This is a proxy for global quantum research activity.

**Step 5: Submit a Test Job (Optional)**
Using Circuit Composer, build a single Hadamard gate on one qubit followed by a measurement. Submit to a real backend. Observe probabilistic output — sometimes 0, sometimes 1 — quantum superposition made visible.

### Deliverable

A 250-word reflection addressing:
1. What calibration metric surprised you most, and why?
2. What does queue depth tell you about current research demand?
3. Based on error rates observed, what kinds of circuits are *feasible* on this hardware? What kinds are *infeasible*?

---

## Lab 1B (Regular): First Look at D-Wave Leap

### Overview

D-Wave Leap (cloud.dwavesys.com) provides cloud access to D-Wave's annealing quantum hardware and hybrid solvers — the same system class as FAU's Advantage2. This lab introduces you to the Leap dashboard, the problem submission interface, and D-Wave's publicly available sample problems.

### Prerequisites

- A web browser and an email address
- D-Wave Leap offers free developer accounts with initial time credits

### Procedure

**Step 1: Create a Leap Account**
Navigate to [cloud.dwavesys.com](https://cloud.dwavesys.com) and register for a free developer account. D-Wave provides initial compute time credits sufficient for this lab.

**Step 2: Explore the Dashboard**
After logging in, review the dashboard. Note:
- **Available solvers** — you will see both QPU (direct quantum processing unit) and hybrid solver options
- **Compute time used vs. remaining** — Leap tracks time in microseconds for QPU access and seconds for hybrid solver jobs
- **Problem history** — jobs you have submitted and their results

**Step 3: Run a Sample Problem**
D-Wave's code examples repository includes a map coloring problem, a job scheduling problem, and a bin packing problem — all formulated as QUBO (Quadratic Unconstrained Binary Optimization) problems ready to run on the hybrid solver. Navigate to the examples, pick any one, and execute it.

**Step 4: Compare QPU and Hybrid Solver**
If your time budget allows, run the same problem on both the QPU (direct quantum hardware) and the Leap hybrid solver. Note the difference in solution time and problem size capacity.

### Deliverable

A 250-word reflection addressing:
1. What problem did you run, and what was the output?
2. How does the problem formulation (QUBO) differ conceptually from how you would describe the same problem in plain English?
3. What does the compute time measurement (microseconds for QPU) tell you about the difference between quantum and classical problem-solving?

---

## Lab 1 (Optional Advanced, Python): Quantum Momentum Index

<a href="https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch01-quantum-momentum-index.ipynb" target="_blank">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="margin-bottom: 1rem;"/>
</a>

> **No installation needed.** Click the button above to open this lab in Google Colab. Run the first cell to install all dependencies automatically.

```{admonition} Advanced Lab — Python Required
:class: tip

This lab is optional and intended for students with Python experience. It produces a quantitative artifact (a plot and memo) suitable as a professional portfolio piece.
```

### Overview

You will build a **Quantum Momentum Index (QMI)** — a composite metric combining arXiv paper counts, open-source framework activity, and venture capital investment to track the "temperature" of the quantum computing field over time, overlaid against the Gartner Hype Cycle.

:::{figure} ../images/ch01-quantum-momentum-index.png
:label: fig-ch01-quantum-momentum-index
:alt: Quantum Momentum Index dashboard showing arXiv paper counts, GitHub commit trends, VC funding rounds, and Gartner hype cycle overlay from 2017 to 2026.
:width: 100%
:align: center

**Target Visualization: The Quantum Momentum Index.** Your lab deliverable should produce a dashboard combining four normalized data streams into a composite index, annotated against the Gartner Hype Cycle.
:::

### Data Sources

| Data Stream | Source | Method |
|------------|--------|--------|
| arXiv paper counts | arXiv API | `GET https://export.arxiv.org/api/query?search_query=quantum+computing` |
| Qiskit GitHub commits | GitHub API | `/repos/Qiskit/qiskit/stats/commit_activity` |
| Cirq GitHub commits | GitHub API | `/repos/quantumlib/Cirq/stats/commit_activity` |
| D-Wave Ocean commits | GitHub API | `/repos/dwavesystems/dwave-ocean-sdk/stats/commit_activity` |
| VC funding rounds | CSV provided in `/resources/quantum_funding_2017_2026.csv` | pandas read_csv |

### Procedure

```python
# Step 1: Collect arXiv monthly paper counts
import requests, pandas as pd

def get_arxiv_counts(year_start=2017, year_end=2026):
    counts = {}
    for year in range(year_start, year_end + 1):
        for month in range(1, 13):
            date_range = f"submittedDate:[{year}{month:02d}01 TO {year}{month:02d}28]"
            url = f"https://export.arxiv.org/api/query?search_query=quantum+computing+AND+{date_range}&max_results=0"
            response = requests.get(url)
            counts[f"{year}-{month:02d}"] = parse_total_results(response.text)
    return pd.Series(counts)

# Step 2: Collect GitHub commit activity for Qiskit, Cirq, and D-Wave Ocean SDK
# Step 3: Load VC funding rounds CSV
# Step 4: Normalize all series to 0-100 scale (min-max normalization)
# Step 5: Compute QMI as weighted average
# Step 6: Overlay Gartner Hype Cycle curve
# Step 7: Annotate key events: Google Sycamore (2019), NIST PQC finalization (2024),
#          FAU-D-Wave agreement (Jan 2026), Google Willow error correction (Dec 2024)
```

### Deliverable

1. A single plot (PNG or PDF, minimum 1200×800 pixels) showing all normalized data streams plus the composite QMI, with the Gartner Hype Cycle overlaid and key events annotated.
2. A 500-word memo: Where is quantum computing on the hype cycle today? What does the trajectory suggest about the next 24 months? Which data stream is most predictive of the others?

---

## Discussion Guidelines

In your main response (400–500 words), choose one quantum market forecast from a named source (McKinsey, BCG, Goldman Sachs, or IBM) and surface its three most load-bearing assumptions. Assess each assumption as high, medium, or low confidence and explain your reasoning. **Include at least one scholarly or credible citation** — peer-reviewed papers, NIST publications, and named consulting firm reports all qualify.

**Respond to at least TWO peers** with substantive feedback that goes beyond agreement. Engage with the specific assumptions your classmate identified, offer alternative confidence assessments, introduce a data point they did not mention, or challenge their forecast source choice.

```{admonition} Discussion Seed Questions
:class: note

- If the hardware timeline assumption in your forecast slips by three years, how does that change the sector-level value estimates?
- Which of the three accelerants (geopolitics, AI convergence, cryptographic risk) do you believe is most likely to independently sustain quantum investment if hardware progress stalls? Why?
- The Google-IBM dispute over Sycamore turned on a difference in classical algorithm choice. What does this suggest about how enterprises should evaluate future "quantum advantage" announcements?
- FAU is investing $20M in on-premises quantum hardware. What problem would you prioritize running on it first, and why?
```

---

## Glossary

**Quantum Supremacy** — The milestone at which a quantum computer executes a specific task faster than any classical computer could in a practical timeframe. Google claimed this in 2019 with the Sycamore processor. The term is benchmark-specific and does not imply general computational superiority.

**Quantum Advantage** — The broader milestone at which a quantum computer solves a *practically relevant* problem faster or at lower cost than the best available classical approach. Quantum advantage for optimization is argued today on D-Wave hardware for specific problem classes.

**Quantum Utility** — IBM's term for the threshold at which quantum computers produce scientifically or commercially useful results, even if classical methods might eventually match them. A deliberately lower bar than quantum advantage, intended to motivate near-term use.

**NISQ** — Noisy Intermediate-Scale Quantum. Quantum processors with 50–1,000 physical qubits operating without full error correction. The current state of gate-model quantum hardware.

**Quantum Annealing** — A hardware approach for solving optimization problems by encoding them as the lowest-energy state of a quantum system and letting the system settle toward the solution. D-Wave's technology. Different paradigm from gate-model computing; optimized for combinatorial optimization problems.

**D-Wave Advantage2** — D-Wave's current flagship quantum annealing processor, containing 7,000+ qubits in a Pegasus topology. The system being installed at FAU's Boca Raton campus. Pairs with the Stride hybrid solver for production-scale enterprise optimization.

**Stride Hybrid Solver** — D-Wave's cloud-based hybrid quantum-classical solver that decomposes large optimization problems into subproblems suitable for the Advantage2, coordinates results classically, and enables problem sizes with millions of variables. Production-ready today.

**QUBO** — Quadratic Unconstrained Binary Optimization. The mathematical problem format used to express optimization problems for quantum annealers. Most real-world optimization problems — logistics, scheduling, portfolio construction — can be reformulated as QUBO problems.

**Qubit** — The fundamental unit of quantum information. Unlike a classical bit, a qubit can exist in superposition of 0 and 1 simultaneously until measured.

**Superposition** — The quantum property allowing a system to exist in multiple states simultaneously. Enables quantum computers to explore many possible solutions in parallel.

**Entanglement** — A quantum correlation between qubits such that the state of one cannot be described independently of the others. A key resource for quantum algorithms.

**Decoherence** — The process by which a qubit loses quantum properties due to environmental interaction. The primary engineering challenge in gate-model quantum computing.

**Fault-Tolerant Quantum Computing (FTQC)** — A quantum architecture encoding logical qubits in redundant arrays of physical qubits. When physical error rates fall below ~1%, error correction suppresses errors exponentially. Enables arbitrarily long computations.

**Shor's Algorithm** — A quantum algorithm that factors large integers in polynomial time, threatening RSA encryption. Requires fault-tolerant hardware to run at commercially relevant key sizes.

**Post-Quantum Cryptography (PQC)** — Cryptographic algorithms designed to resist quantum attacks. NIST finalized ML-KEM and ML-DSA as standards in 2024.

**Harvest Now, Decrypt Later (HNDL)** — An attack where adversaries collect encrypted data today to decrypt it when quantum computers become capable of breaking public-key encryption. Creates present-day urgency for PQC migration.

**SC (Supercomputing Conference)** — The International Conference for High Performance Computing, Networking, Storage, and Analysis. The premier annual HPC event, now featuring a dedicated quantum computing track. SC26 is scheduled for Chicago, November 2026.

---

## Leader's Takeaway

```{epigraph}
You don't need to predict when quantum arrives. You need to predict the year your competitors start acting as if it has.
```

The strategic insight of this chapter is not that quantum computers are coming — they already exist, in two distinct paradigms, with different maturity profiles and different problem domains. D-Wave annealing systems are running in production today. Gate-model systems are in serious research deployment. Fault-tolerant systems are on a credible hardware roadmap for the late 2020s.

The enterprise vanguard — JPMorgan Chase, BASF, Airbus, Mercedes-Benz — is not waiting. And as of January 2026, Florida Atlantic University is not waiting either. The question for every executive and every student reading this chapter is the same: *What is your organization's quantum literacy today?*

Not your hardware investment. Your literacy. Do your data scientists understand the difference between annealing and gate-model systems? Does your CISO have a cryptographic migration plan? Does your R&D function know which of its problems are quantum-amenable, and on which hardware paradigm?

If the answer to these questions is no, the relevant action is not to purchase quantum hardware. The relevant action is to start building quantum literacy — through education, through pilot experiments on cloud platforms and on FAU's Advantage2, through a cryptographic inventory, and through a structured assessment of which business processes might benefit from quantum acceleration.

The cost of beginning that process today is modest. The cost of beginning it eighteen months after your competitors is compounding.

```{admonition} Chapter Summary
:class: note

- Quantum computing has crossed from physics experiment to enterprise agenda item, driven by three structural accelerants: geopolitics, AI convergence, and cryptographic risk.
- Two distinct quantum paradigms matter for enterprise strategy: gate-model systems (IBM, Google, IonQ) on a NISQ-to-fault-tolerance roadmap, and quantum annealing (D-Wave) which is already production-ready for optimization.
- FAU's $20M D-Wave Advantage2 deployment — the first on-campus quantum computer in Florida — makes this course unique: students work on production-grade hardware, not simulators.
- Market forecasts project \$450–850B in quantum value creation by 2035, with logistics and optimization value (the annealing domain) potentially arriving sooner than pharmaceutical simulation value (the gate-model domain).
- The current investment cycle is structurally different from prior quantum winters: corporate capital, production deployments, geopolitical mandates, and an HPC community transitioning to quantum-HPC hybrid systems.
- Cryptographic risk creates present-day organizational exposure through HNDL attacks. PQC migration should begin regardless of broader quantum strategy.
- Reading quantum milestone announcements requires asking: what task, what classical baseline, what problem size, what paradigm?
```
