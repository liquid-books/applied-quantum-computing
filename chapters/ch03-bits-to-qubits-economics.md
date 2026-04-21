---
title: "Chapter 3: From Bits to Qubits — The New Economics of Computation"
subtitle: "Frameworks for Reading Any Quantum Price Sheet, Now and in 2031"
short_title: "Ch. 3: Quantum Economics"
description: "Quantum is not a faster classical computer — it is a different cost curve. This chapter builds an evergreen framework for quantum unit economics, TCO, pricing archetypes, and break-even analysis that survives any vendor change."
label: ch-03-bits-to-qubits-economics
tags: [quantum economics, TCO, pricing, unit economics, break-even, quantum advantage, quantum utility]
---

# Chapter 3: From Bits to Qubits — The New Economics of Computation

::::{figure} ../images/ch03-explainer-infographic.png
:label: fig-ch03-explainer-infographic
:alt: Chapter 3 illustrated explainer infographic showing quantum economics overview, pricing archetypes, TCO framework, and break-even concept
:width: 100%
**Chapter 3 Illustrated Explainer.** Quantum is not a faster classical computer — it is a different cost curve. This chapter gives you the frameworks to read any quantum price sheet that exists today or will exist in 2031.
::::

Quantum computing vendors are excellent at generating excitement. They are less excellent at generating invoices you can actually explain to your board. This chapter fixes that. By the end, you will have a durable framework — not a price sheet — for evaluating quantum economics across any provider, any hardware generation, and any point in the next decade.

## Opening Scene: Moore's Law Is Dead — and Your CFO Doesn't Know It Yet

::::{figure} ../images/ch03-moores-law-end.png
:label: fig-ch03-moores-law-end
:alt: Moore's Law ending chart showing transistor count growth flattening with quantum era beginning
:width: 100%
**Figure 3.2.** Five decades of exponential transistor growth meet a physical wall. The quantum era does not continue this curve — it replaces it with a fundamentally different cost structure.
::::

In 1965, Gordon Moore observed that the number of transistors on a chip doubled roughly every two years. For five decades, that observation functioned as a business plan for the entire technology industry. You could buy a faster server, wait two years, and buy a faster one still. Costs fell. Performance compounded. Strategy was easy.

Moore's Law is dead. Not metaphorically dead — physically dead. Transistors are now measured in atoms. There is no room to shrink further. Nvidia knows this; that is why it sells parallelism at scale rather than raw clock speed. The hyperscalers know it; that is why AWS, Azure, and Google Cloud have all opened quantum divisions. The venture community knows it; quantum startups attracted more than \$2 billion in private investment in a recent twelve-month period.

The reason you are reading this book is that your CFO probably has not yet worked out what replaces the Moore's Law cost curve — and someone in your organization will need to brief her before she sees the first vendor proposal.

Here is what she needs to understand: quantum is not a faster classical computer. It is a machine that operates on a fundamentally different cost curve. Classical computing costs scale with transistor counts and clock rates; quantum computing costs scale with error rates, coherence times, and physical-to-logical qubit ratios. The arithmetic is different. The break-even math is different. The risk profile is different.

This chapter gives you a framework for that math — one built to outlast any single vendor's pricing page.

---

## The Single Idea: Quantum Is a Different Cost Curve — Not Just a Faster One

::::{admonition} The Core Claim
:class: important
Quantum computing does not replace classical computing on the same cost curve. It introduces a *new* cost curve that may intersect the classical curve for specific workloads at specific scales. Your job is not to predict *when* that intersection occurs — it is to build a model that tells you *whether* it occurs for *your* workloads.
::::

Here is the most common and most costly misunderstanding in quantum computing: **quantum is not a faster classical computer.** It is not a turbocharged server. It does not do the same work faster. For certain classes of problems, it does *fundamentally different work* — and that distinction changes everything about how you evaluate it economically.

### The Locksmith vs. the Brute-Force Safe-Cracker

Imagine you need to open a safe and you don't have the combination. A classical computer's approach is brute force: try 0000, then 0001, then 0002 — through every possible combination in sequence (or in large parallel batches). Given enough time and enough machines, it will eventually succeed. This is how classical computers approach hard problems like factoring large numbers: try, check, try again.

A quantum computer doesn't try harder. It uses a fundamentally different technique: *interference*. It puts the problem into superposition — all possible answers simultaneously — and then applies a sequence of operations that constructively reinforces the *correct* answer while destructively canceling the wrong ones. The mechanism is closer to a skilled locksmith listening to the tumblers than a cracker grinding through combinations.

The locksmith doesn't do more work. The locksmith does *different work* — work that is mathematically structured in a way the brute-force approach cannot replicate.

### The GPS Analogy

Before GPS, finding your location required triangulating from landmarks: spot a water tower, spot a church steeple, find where the sight lines cross. It was sequential, imprecise, and slow. Faster triangulation equipment would give you a faster result — but it would still be triangulation.

GPS doesn't do faster triangulation. It uses simultaneous signals from multiple satellites and the mathematics of trilateration to compute position in an entirely different way. The result isn't just quicker — it's more accurate and works in environments where triangulation is impossible.

Quantum computing's relationship to classical computing is analogous. For specific problem classes — factoring, quantum simulation, certain optimization problems — it isn't doing the same calculation faster. It is using a different mathematical structure entirely, one that classical hardware cannot efficiently emulate.

:::{note} Plain Language
**What this means for your budget:** Classical hardware improvements (more cores, faster clock speeds, better parallelism) help with every classical problem. Quantum improvements only matter for problems where the *quantum approach* is applicable. The first question is never "how fast is the quantum computer?" — it is "does a quantum algorithm even exist for this problem?"
:::

### The Shape of the Cost Curve Itself Changes

This isn't a semantic distinction — it has direct economic consequences. On a classical cost curve, throwing more hardware at a problem always helps (until you hit diminishing returns). On certain problems, a quantum computer doesn't just offer a cost advantage at scale — it offers *tractability* where classical hardware offers none.

RSA encryption, for example, is secure because factoring the large primes underlying it would take classical computers millions of years. Not "very expensive" — impossible within any reasonable human timeframe. A sufficiently capable quantum computer running Shor's algorithm would factor those primes in hours. The cost curve doesn't just shift — it changes *shape*. Problems that were infinitely expensive on the classical curve become finite on the quantum curve.

This is why "quantum is X times faster" framing misses the point for the workloads that matter most. For those workloads, the quantum advantage isn't speed — it's existence.

Classical computing has been governed by a predictable economics for fifty years: more transistors, lower cost per operation, better performance per dollar. That predictability made capital planning tractable. You could forecast server refresh cycles, amortize hardware over three to five years, and benchmark performance against a commodity baseline.

Quantum computing breaks that model in three ways:

**First**, the unit of cost is not a clock cycle — it is a *shot* through a quantum circuit, multiplied by depth, error rate, and queue time. A "cheap" shot on paper can become an expensive result in practice when you account for the shots wasted to noise.

**Second**, the hardware you see advertised — the headline qubit count — is almost never the hardware you get to use for real computation. Physical qubits must be converted to logical qubits through error correction, at ratios that today run from hundreds-to-one to thousands-to-one. A 1,000-qubit machine may deliver fewer than ten reliable logical qubits for your workload.

**Third**, quantum hardware is a shared resource accessed over the cloud, which means queue time — the wait before your circuit runs — is itself a cost. In a production environment, that latency has financial consequences.

Understanding these three dynamics is the prerequisite for every pricing and budgeting conversation that follows.

---

## Four Pricing-Model Archetypes

::::{figure} ../images/ch03-pricing-archetypes.png
:label: fig-ch03-pricing-archetypes
:alt: Four quantum cloud pricing archetypes quadrant diagram
:width: 100%
**Figure 3.3.** The four pricing archetypes used by quantum cloud providers. Providers come and go; these archetypes have persisted across every market generation.
::::

Cloud quantum providers have tried many pricing experiments since the first commercial access was offered in 2016. Beneath the variation, four archetypes recur reliably. Memorize these archetypes — not any specific vendor's current price card.

::::{tab-set}

:::{tab-item} Pay-Per-Shot
**Pay-Per-Shot (Task-Based)**

The provider charges per quantum circuit execution, sometimes called a "job" or "task." Pricing is typically expressed as cost per shot (a single run of the circuit) or cost per second of QPU (quantum processing unit) time.

*Favored by:* Exploratory workloads, research teams, proof-of-concept pilots. Any use case where volume is low and unpredictable.

*Watch for:* Minimum job fees that make very short circuits disproportionately expensive. Shot-rate caps that create queuing even on paid tiers.

*Break-even risk:* Low fixed cost but high marginal cost at scale. Works well for early-stage investigation; becomes uneconomical for production workloads with high shot requirements.
:::

:::{tab-item} Pay-Per-Minute
**Pay-Per-Minute (Time-Based)**

The provider charges for wall-clock time on a quantum processor, regardless of what circuits run during that time. Think of it as renting a quantum computer by the hour.

*Favored by:* Workloads with dense, back-to-back circuit execution — variational algorithms like VQE or QAOA that require thousands of sequential circuit evaluations. Teams that have already validated their workload and want throughput.

*Watch for:* Idle time during calibration cycles that is still billed. Minimum reservation windows (often one hour or more) that inflate costs for short runs.

*Break-even risk:* Efficient for known, dense workloads. Expensive when utilization is low or calibration events interrupt execution.
:::

:::{tab-item} Reserved Capacity
**Reserved Capacity (Committed Use)**

The customer commits to a defined quantum resource — a specific processor, number of qubits, or shot volume — over a fixed term (typically monthly or annually) in exchange for a discounted rate.

*Favored by:* Production workloads with predictable volume. Organizations running quantum in a production pipeline where uptime and throughput guarantees matter. Enterprises with annual budget cycles.

*Watch for:* Utilization thresholds — reserved capacity that goes unused is still paid for. Contractual lock-in to a hardware generation that may be superseded.

*Break-even risk:* Lowest per-shot cost but highest fixed commitment. Requires confidence in volume projections.
:::

:::{tab-item} Free Tier
**Free Tier (Research / Simulator Access)**

Providers offer free access to quantum simulators and, in some cases, limited real-hardware shot allocations through academic or developer programs. IBM Quantum's free tier is the most widely used example.

*Favored by:* Education, algorithm prototyping, skill-building. Any stage where you are validating *whether* a quantum approach is feasible before spending money.

*Watch for:* Queue times on free tiers can be extremely long (hours to days for real hardware). Simulators do not expose noise and are therefore optimistic benchmarks.

*Break-even risk:* Zero marginal cost but significant opportunity cost (queue time = researcher time). Not a production model.
:::

::::

:::{admonition} Archetype Selection Heuristic
:class: tip
Match archetype to workload maturity: **Free Tier** for exploration, **Pay-Per-Shot** for validation, **Pay-Per-Minute** for optimization-intensive algorithms, **Reserved Capacity** for production. Never commit to reserved capacity until you have validated your workload on pay-per-shot.
:::

---

## The True Unit of Quantum Cost

::::{figure} ../images/ch03-true-cost-formula.png
:label: fig-ch03-true-cost-formula
:alt: Quantum true unit cost formula visualization showing the four cost drivers
:width: 100%
**Figure 3.4.** The true unit of quantum cost is not "per qubit" — it is cost per *useful result*, driven by four multiplicative factors.
::::

### The Restaurant Analogy: Stop Counting Pots

You would not judge a restaurant's quality or pricing by counting how many pots are in the kitchen. A restaurant with 200 pots might produce terrible food at high cost, while a restaurant with 20 pots might produce extraordinary meals at half the price. The pots are inputs. What matters is the finished meal: quality, cost, and whether you actually wanted it.

The phrase "cost per qubit" is the restaurant-pot fallacy applied to quantum computing. It counts the inputs (physical qubits) while ignoring everything that determines whether those inputs produce useful output: how many qubits are doing real computation versus error correction, how deep the circuit is, how noisy the hardware, how long you waited in queue.

When a vendor quotes you a "per qubit" price, ask the same question you'd ask a restaurant: *what does the finished meal cost?* In quantum terms: **what is the cost per useful result?**

:::{note} Plain Language
**The analogy's limit:** Unlike restaurant pots, qubit counts *do* set a hard ceiling on what problems you can run. You can't cook a meal for 100 if your kitchen only has 2 burners. Similarly, a 10-qubit machine can't run an algorithm that requires 50 logical qubits. So qubit count matters — but as a *constraint*, not as a *price unit*.
:::

### The True Cost Formula — Five Factors, All Multiplicative

The most dangerous phrase in quantum vendor conversations is "cost per qubit." It is meaningless as a unit of economic analysis because it omits everything that actually determines what you pay for useful computation.

The correct unit is **cost per useful result**, which decomposes as follows:

$$\text{Cost}_{\text{useful}} = \frac{S \cdot D \cdot \epsilon \cdot Q}{Y}$$

Where:
- **S** = Shot count required per experiment
- **D** = Circuit depth factor (deeper circuits accumulate more error)
- **ε** = Error rate per gate (expressed as a multiplier on required shots)
- **Q** = Queue time cost (researcher/compute time waiting for hardware access)
- **Y** = Yield — fraction of shots producing a usable result

Each of these factors is **multiplicative**. A circuit that requires 1,000 shots, runs at depth 100, operates on hardware with 0.1% gate error rate, and sits in a 4-hour queue does not cost "1,000 shots worth of money." It costs a number that reflects the compounding of all four factors — and that number can be orders of magnitude larger than the headline shot price suggests.

### Walking Through the Formula — Plain Language

**S — Shot Count: Why one run is never one run**

Quantum measurement is probabilistic. Unlike a classical computer that returns the same answer every time, a quantum computer returns a sample from a probability distribution. If you run a circuit once, you get one bitstring — one random draw. To know the *likely* answer, you need to run it hundreds or thousands of times and look at the distribution.

Think of it like polling. One poll respondent tells you nothing. A thousand respondents gives you a confidence interval. Shot count is the sample size of your quantum experiment. For typical variational algorithms, you need 1,000 to 10,000 shots per experiment for statistically meaningful results.

**D — Circuit Depth: The longer you run, the more noise accumulates**

Circuit depth is the number of sequential gate operations in your circuit. Think of it like a game of telephone: each person in the chain introduces a small chance of error, and the chain's reliability degrades with every additional person. A quantum circuit of depth 10 is like a 10-person chain. A circuit of depth 100 is like a 100-person chain — errors compound at every step.

On today's hardware, circuits deeper than roughly 50–100 gates often produce outputs dominated by noise rather than signal. This is the primary reason why many theoretically powerful quantum algorithms can't be run on current hardware: they require circuits far deeper than the hardware can reliably execute.

**ε — Error Rate: The tax on every gate**

Every gate operation in a quantum circuit has a small probability of introducing an error. Current two-qubit gate error rates on leading hardware range from 0.1% to 1%. That sounds small — until you run a circuit with 100 gates, at which point you're compounding errors across every single operation.

The practical consequence: a high-error-rate machine requires more shots to extract the same signal from noisy results, driving up both S and the error mitigation overhead. When hardware vendors announce improved error rates, this is the number that most directly reduces your cost per useful result.

**Q — Queue Time: The cost that hides in plain sight**

Queue time is the wait between submitting your circuit and its execution on hardware. On free tiers, this can be hours to days. On paid tiers, it ranges from minutes to hours. The reason it's a cost isn't just inconvenience — it's that your researchers are waiting, and their time is billable.

As Exercise 3.2 will demonstrate, queue cost frequently dominates the entire cost equation, dwarfing QPU pricing. A 3-hour queue at a \$150/hr researcher rate costs \$450 — before you've paid for a single shot.

**Y — Yield: Not all shots are useful shots**

Even after you've collected your shots, not all of them contribute to a usable result. Noise, decoherence, and measurement errors can corrupt a shot entirely. Yield is the fraction of shots that produce a bitstring you can trust. A 70% yield means 30% of your shots were wasted — effectively increasing the true cost per useful result by 43%.

:::{note} Plain Language
**The punchline:** These five factors multiply together. Improving any single factor helps, but the biggest gains come from attacking the dominant factor. In most near-term quantum workloads, that dominant factor is queue time — not QPU pricing. Securing reserved access that eliminates queue time will often do more for your unit economics than negotiating a 50% discount on per-shot rates.
:::

:::{prf:definition} Shot
:label: def-shot
A **shot** is a single execution of a quantum circuit, from initialization through measurement. The result of a shot is a classical bitstring (e.g., `011010`). Because quantum measurement is probabilistic, useful results require averaging across many shots — typically hundreds to thousands for variational algorithms.
:::

:::{prf:definition} Circuit Depth
:label: def-circuit-depth
**Circuit depth** is the number of sequential layers of quantum gates in a circuit. Deeper circuits run for longer on hardware, accumulating decoherence and gate errors. A circuit of depth 50 on today's hardware may produce outputs dominated by noise rather than signal.
:::

### Why Error Rate Is the Most Important Variable

Error rate is the dominant variable in the true cost formula because quantum hardware is noisy. Every gate operation has a probability of introducing an error. Those errors compound with depth. At current error rates (roughly 0.1–1% per two-qubit gate on leading hardware), a circuit of depth 100 with 50 two-qubit gates will experience significant error accumulation.

The business implication: as hardware improves and error rates fall, the true cost per useful result drops — even if the headline shot price stays constant. A model that locks in today's error rates will overestimate future costs. Build your model to accept error rate as a parameter, not a constant.

---

## Physical-to-Logical Qubit Overhead

::::{figure} ../images/ch03-physical-logical-overhead.png
:label: fig-ch03-physical-logical-overhead
:alt: Physical to logical qubit overhead iceberg diagram showing 1000:1 ratio
:width: 100%
**Figure 3.5.** The physical-to-logical qubit iceberg. The headline qubit count a vendor advertises is the visible tip; the logical qubits available for your computation are the much smaller submerged portion.
::::

### The Skyscraper Scaffolding Analogy

When you build a skyscraper, the scaffolding surrounding the structure can use more steel than the building itself. Workers, safety systems, support beams — all of it exists to make construction of the real thing possible. The scaffolding is essential. It is not the building.

Physical qubits are the scaffolding. The overwhelming majority of them are doing error correction — holding the fragile quantum state together, detecting errors, compensating for noise. The **logical qubits** are the finished floors: the reliable, usable computation space you actually get to work with.

When a quantum hardware vendor announces "1,000 qubits," that number describes physical qubits — individual quantum systems that can hold a superposition state. It does not describe the number of *reliable* qubits available for your computation.

### The Headline Trap — Why Qubit Counts Are Almost Always Misleading

Physical qubits are fragile. They decohere (lose their quantum state) and suffer gate errors. To perform reliable computation, multiple physical qubits must be combined into a single **logical qubit** through quantum error correction. The overhead for this conversion is enormous by current standards.

Here is the arithmetic that every board presentation gets wrong: for fault-tolerant computation using the Surface Code (the most widely researched error correction approach), you currently need roughly **1,000 physical qubits to produce one reliable logical qubit**.

Read that again. A "1,000-qubit processor" — the kind that generates press releases and stock price movements — gives you approximately **one** logical qubit for fault-tolerant computation.

This is not a rounding error or a conservative estimate. It is the state of the technology. The vendors know it. The researchers know it. The gap between headline qubit count and usable logical qubits is the single largest source of overhyped quantum claims in the market.

:::{note} Plain Language
**For your next vendor meeting:** When a vendor says "our 1,000-qubit processor," your response should be: "How many logical qubits does that deliver for fault-tolerant computation at your current physical error rate?" If they don't have an immediate answer, you've found the edge of their honest knowledge.
:::

| Error Correction Code | Physical Qubits per Logical Qubit | Notes |
|---|---|---|
| Surface Code (current hardware) | 1,000–10,000 | Most widely researched; requires very low physical error rates |
| Surface Code (near-term target) | 100–1,000 | Requires ~0.1% physical gate error rate |
| Color Code | 200–2,000 | More efficient in some geometries |
| No correction (NISQ regime) | 1:1 | Noisy results; limited circuit depth |

The table reveals the scale of the problem. A quantum computer advertised with 1,000 physical qubits, running with today's error correction overhead, may deliver fewer than ten logical qubits suitable for fault-tolerant computation.

:::{admonition} Board Briefing Rule
:class: warning
**Never quote the headline qubit count to your board.** The number to quote is the estimated number of *logical qubits* available for your specific workload, given the hardware's current physical error rate and the error correction overhead your algorithm requires. That number is almost always smaller — often by three orders of magnitude.
:::

The overhead ratio is not fixed. As physical error rates improve, the overhead shrinks. The trajectory of hardware progress is toward lower overhead, not higher. A budget model that assumes 1,000:1 overhead in 2024 should be parameterized to accept a lower ratio in 2026 or 2028 — without rebuilding the model.

---

## TCO Framework for Hybrid Workloads

::::{figure} ../images/ch03-tco-framework.png
:label: fig-ch03-tco-framework
:alt: Quantum TCO framework pipeline showing six stages of hybrid workload cost
:width: 100%
**Figure 3.6.** The quantum TCO pipeline. Every stage contributes to total cost; most organizations account for only the quantum submission stage when building budgets.
::::

Quantum computing is never used alone. Every real-world quantum application is a **hybrid workload** — a pipeline that begins and ends with classical computing, with a quantum step in the middle. Total cost of ownership must account for every stage of that pipeline.

The six stages of the quantum TCO framework:

::::{grid} 2

:::{grid-item-card} 1. Data Ingestion
**What happens:** Classical data is collected, cleaned, and formatted for quantum processing. This may include encoding classical data as quantum states (a non-trivial algorithmic step).

**Cost drivers:** Storage, network transfer, engineering time for encoding design.

**Common mistake:** Ignoring encoding cost. Quantum amplitude encoding, for example, can require circuit depth proportional to the data size — eliminating quantum advantage before the algorithm even runs.
:::

:::{grid-item-card} 2. Pre-Processing
**What happens:** Classical preprocessing that reduces the problem size or reformulates it for quantum hardware. May include dimensionality reduction, problem decomposition, or compilation of the quantum circuit.

**Cost drivers:** Classical compute time, software licensing, compiler optimization passes.

**Common mistake:** Underestimating compilation overhead. A circuit designed for a 100-qubit abstract machine may require 10x more gates when compiled for a specific hardware topology.
:::

:::{grid-item-card} 3. Quantum Submission
**What happens:** The compiled circuit is submitted to the quantum processor via cloud API. The processor executes the circuit for the specified number of shots and returns bitstring results.

**Cost drivers:** Shot count × QPU rate + queue time. This is the stage most organizations focus on — and it is typically the *minority* of total TCO.

**Common mistake:** Treating QPU cost as total cost. In early-stage workloads, engineering time around the QPU submission often exceeds the QPU cost itself.
:::

:::{grid-item-card} 4. Error Mitigation
**What happens:** Post-processing techniques are applied to raw shot results to reduce the impact of noise. Zero-noise extrapolation, probabilistic error cancellation, and symmetry verification are common methods.

**Cost drivers:** Additional shots required for error mitigation (often 2–10× the base shot count), classical compute for post-processing, algorithm design time.

**Common mistake:** Budgeting only for base shots without error mitigation overhead. For near-term hardware, error mitigation routinely multiplies the effective shot count by a factor of 3–5.
:::

:::{grid-item-card} 5. Post-Processing
**What happens:** Quantum measurement results (bitstrings) are decoded back into classical outputs. Statistical analysis, result aggregation, and comparison to classical baselines.

**Cost drivers:** Classical compute, storage, statistical validation time.

**Common mistake:** Treating this as negligible. For optimization workloads, post-processing to extract the best solution from a distribution of results can be non-trivial.
:::

:::{grid-item-card} 6. Validation
**What happens:** The quantum result is verified against a classical baseline or domain benchmark. For novel workloads, validation itself is a research problem.

**Cost drivers:** Classical simulation for small-scale validation (exponentially expensive as problem size grows), domain expert time for result interpretation.

**Common mistake:** Skipping validation. Without a validated result, the quantum output has no business value regardless of its theoretical correctness.
:::

::::

:::{admonition} TCO Rule of Thumb
:class: note
For early-stage quantum projects, budget the following allocation: 20% QPU time, 30% engineering and integration, 25% error mitigation and post-processing, 25% validation and iteration. Adjust as the workload matures and QPU costs decline.
:::

---

## Quantum Advantage, Utility, and Supremacy: Three Terms You Must Not Conflate

::::{figure} ../images/ch03-advantage-vs-utility.png
:label: fig-ch03-advantage-vs-utility
:alt: Quantum advantage vs utility vs supremacy comparison diagram with three zones
:width: 100%
**Figure 3.7.** Advantage, utility, and supremacy occupy distinct positions on the quantum capability spectrum. Conflating them is the fastest way to lose credibility in a board presentation.
::::

Quantum computing vendors, press releases, and even peer-reviewed papers use the terms *advantage*, *utility*, and *supremacy* interchangeably. They are not interchangeable. Each describes a different threshold, a different kind of claim, and a different standard of evidence. Confusing them is the fastest route to a credibility-destroying board presentation.

### The Rubik's Cube Analogy

Imagine a competition with three levels of achievement:

**Level 1 — Supremacy:** You are the fastest person alive at solving a Rubik's cube *blindfolded in one hand while reciting the alphabet backwards*. Nobody has ever been faster. Nobody else can even attempt it. This is an extraordinary technical feat. It is also a task nobody pays for.

**Level 2 — Utility:** You are faster than most humans at solving a normal Rubik's cube in a normal way. People genuinely pay for fast Rubik's cube solvers in certain contexts. You're commercially relevant, even if dedicated machines can eventually do it faster.

**Level 3 — Advantage:** You are faster than any human *and* any machine at *brain surgery*. You are better than the best available alternative at a task that matters profoundly and generates significant commercial value. This is the holy grail.

Google's 2019 Sycamore experiment achieved Level 1. It was blindfolded Rubik's cube solving — technically extraordinary, practically useless. IBM's 2023 utility demonstration approached Level 2. Level 3 — quantum advantage on a commercially meaningful problem — remains largely unachieved as of this writing.

:::{note} Plain Language
**Why this matters for procurement:** Vendors almost never tell you which level they're claiming. "Our quantum computer achieved a breakthrough" could mean Level 1, Level 2, or (rarely) approaching Level 3. Your due diligence is to identify which level applies — because only Level 3 generates a positive ROI for a production investment.
:::

:::{prf:definition} Quantum Supremacy
:label: def-quantum-supremacy
**Quantum supremacy** (sometimes called *quantum advantage over classical simulation*) is achieved when a quantum computer performs a specific computation faster than any classical computer could, even in principle, within a practical timeframe. The canonical claim is Google's 2019 Sycamore experiment. Critically: the task in a supremacy demonstration is typically **not useful** — it is chosen precisely because it is hard for classical computers, not because anyone wants the answer.
:::

:::{prf:definition} Quantum Advantage
:label: def-quantum-advantage
**Quantum advantage** describes the condition where a quantum computer solves a *practically useful* problem faster, cheaper, or more accurately than the best available classical alternative. This is the threshold that matters for business. As of the time of writing, demonstrated quantum advantage for commercially relevant problems remains limited and contested.
:::

:::{prf:definition} Quantum Utility
:label: def-quantum-utility
**Quantum utility** is a lower bar introduced by IBM in 2023: a quantum computer produces results that are difficult or impossible to verify by classical simulation at scale, even if it is not yet faster than the best classical algorithm. A quantum computer in the utility regime is *useful for research* — it explores regimes inaccessible to classical computers — without necessarily being the best tool for any production task.
:::

The practical consequence of these distinctions:

| Claim Type | Vendor Usually Means | What to Actually Verify |
|---|---|---|
| "Quantum supremacy" | We ran a benchmark faster than classical | Was the benchmark useful? Is the comparison fair? |
| "Quantum advantage" | We solved a real problem better | What is the best classical alternative? Over what problem size? |
| "Quantum utility" | Our machine produces novel results | Is this relevant to your workload? Does it translate to production value? |

:::{admonition} Due-Diligence Checklist
:class: tip
When a vendor claims quantum advantage for your workload: (1) Ask for the classical baseline algorithm and its performance. (2) Ask at what problem size the advantage emerges. (3) Ask whether the advantage is in time, cost, accuracy, or all three. (4) Ask whether the advantage survives error correction overhead. Four questions. Most vendor claims fail at least one.
:::

---

## The Evergreen Break-Even Template

::::{figure} ../images/ch03-break-even-template.png
:label: fig-ch03-break-even-template
:alt: Quantum break-even analysis template showing cost curve intersection
:width: 100%
**Figure 3.8.** The break-even template. The intersection point of the classical and quantum cost curves defines the problem scale at which quantum becomes economically rational. Build your model so the pricing parameters live in a single configuration block.
::::

A break-even analysis for quantum computing must survive vendor changes, hardware generations, and pricing revisions. The template below achieves this by separating **workload parameters** (stable, determined by your problem) from **vendor parameters** (volatile, determined by the market).

### Template Structure

```python
# ============================================================
# QUANTUM BREAK-EVEN TEMPLATE — UPDATE VENDOR PARAMS ANNUALLY
# ============================================================

# --- WORKLOAD PARAMETERS (stable — your problem defines these) ---
PROBLEM_SIZE = 100          # e.g., number of assets in portfolio
SHOTS_REQUIRED = 10_000     # shots per experiment for acceptable statistics
CIRCUIT_DEPTH = 50          # gate layers in your compiled circuit
EXPERIMENTS_PER_RUN = 20    # variational iterations or problem instances
CLASSICAL_COST_PER_RUN = 0.85  # USD — best classical alternative (benchmark this!)

# --- VENDOR PARAMETERS (volatile — update this block annually) ---
VENDOR_COST_PER_SHOT = 0.00001      # USD per shot — check vendor pricing page
GATE_ERROR_RATE = 0.005             # fractional error per two-qubit gate
QUEUE_OVERHEAD_HOURS = 2.0          # average queue wait on your tier
RESEARCHER_HOURLY_COST = 150        # USD — your team's fully-loaded hourly rate
ERROR_MITIGATION_MULTIPLIER = 3.0   # shots multiplier for error mitigation

# --- DERIVED CALCULATIONS (do not modify) ---
effective_shots = SHOTS_REQUIRED * ERROR_MITIGATION_MULTIPLIER
qpu_cost = effective_shots * EXPERIMENTS_PER_RUN * VENDOR_COST_PER_SHOT
queue_cost = QUEUE_OVERHEAD_HOURS * RESEARCHER_HOURLY_COST
total_quantum_cost = qpu_cost + queue_cost

classical_total = CLASSICAL_COST_PER_RUN * EXPERIMENTS_PER_RUN

break_even_ratio = total_quantum_cost / classical_total

print(f"Quantum cost per run: ${total_quantum_cost:.4f}")
print(f"Classical cost per run: ${classical_total:.4f}")
print(f"Quantum/Classical ratio: {break_even_ratio:.2f}x")
print(f"Status: {'QUANTUM ADVANTAGE' if break_even_ratio < 1 else 'CLASSICAL PREFERRED'}")
```

The key design principle: every volatile assumption lives in the **VENDOR PARAMETERS** block. When a provider changes its pricing, when hardware improves error rates, or when a new vendor enters the market, you update eight lines — not the entire model.

:::{admonition} Break-Even Template Golden Rule
:class: important
The classical baseline cost (`CLASSICAL_COST_PER_RUN`) is the most important parameter in the model — and the one most organizations get wrong. It must represent the **best available classical algorithm**, not legacy infrastructure. If you benchmark quantum against a poorly optimized classical approach, your break-even analysis is theater.
:::

---

## Flagship Case Study: A Mid-Cap Pharma CFO Builds the First Quantum Budget Line

::::{figure} ../images/ch03-pharma-cfo-case.png
:label: fig-ch03-pharma-cfo-case
:alt: Pharma CFO quantum budget case study infographic
:width: 100%
**Figure 3.9.** The mid-cap pharma quantum budget case. The CFO's key insight: structure the model so the vendor layer is a swappable parameter, not a structural assumption.
::::

### Situation

The CFO of a \$4B specialty pharmaceutical company — call her Dr. Chen — received a proposal from a quantum computing vendor in late 2023. The proposal promised "quantum-accelerated molecular simulation" that could reduce drug discovery cycle time by 30%. The ask was a \$2.1M pilot contract, with a \$12M three-year committed-use agreement as the follow-on.

Dr. Chen had no quantum computing expertise on staff. Her CTO was enthusiastic. Her head of computational chemistry was skeptical. Her board was asking whether the company was "keeping up with quantum."

### Quantum Angle

The vendor's target workload was variational quantum eigensolver (VQE) for small-molecule simulation — a genuinely quantum-relevant application. The promise of quantum for molecular simulation is well-grounded in theory; the question is always whether the available hardware is mature enough to deliver practical advantage over classical density functional theory (DFT) or coupled-cluster methods.

### Decisions Made

Dr. Chen hired a quantum computing consultant for four weeks — not to evaluate the science, but to build a vendor-agnostic cost model. The deliverables she requested:

1. **A TCO spreadsheet** structured around the six-stage framework, with all vendor-specific parameters isolated in a single tab labeled "Vendor Assumptions."
2. **A break-even analysis** benchmarked against the company's existing DFT pipeline (not generic classical compute).
3. **A milestone framework** defining what hardware capability (expressed in logical qubits and error rates) would need to exist before the committed-use agreement made economic sense.

The outcome of the four-week engagement: the pilot was approved at a reduced budget of \$400,000 — reframed as a "quantum readiness" investment rather than a production deployment. The \$12M committed-use agreement was declined. The decision to decline was based on the break-even model showing that the workload required approximately 50 error-corrected logical qubits to demonstrate advantage over the classical baseline — a threshold no available hardware met.

**What she funded:** A proof-of-concept using the pay-per-shot tier to validate that the company's chemists could formulate their molecules as quantum circuits. A six-month internal capability-building program. A vendor-monitoring cadence (quarterly pricing and hardware review).

**What she cut:** The committed-use contract. A \$300,000 line item for "quantum-ready infrastructure upgrades" that the vendor had included in the proposal (the consultants identified this as unnecessary for cloud-based access). A headcount request for a "quantum applications engineer" that predated a validated use case.

**What she got wrong:** She underestimated queue time as a cost. Her team's first three months of the pilot were dominated by hardware queue waits averaging 18 hours, which consumed researcher time and compressed the timeline for producing results. In retrospect, the TCO model should have included a queue-time sensitivity analysis as a mandatory table, not a footnote.

### Measured Outcome

At the end of the \$400,000 pilot, Dr. Chen's team had:
- Validated two molecular simulation circuits on quantum hardware
- Confirmed that the company's target molecules required more logical qubits than any available hardware could provide
- Built a reusable cost model that her team could update when hardware improved
- Trained three computational chemists in quantum circuit formulation
- Established a quarterly review cadence tied to specific hardware capability milestones

The quantum spend was not wasted — it bought readiness. The \$11.6M that was *not* spent on the committed-use contract was the real return on the four-week consulting engagement.

### Open Question

Dr. Chen's model projects that her target workload becomes economically rational when hardware achieves 50 fault-tolerant logical qubits with error rates below 0.01%. Multiple vendors have roadmaps suggesting this milestone could be reached within this decade. The open question: when that threshold is crossed, will the company's chemists be ready to exploit it — or will they be starting from scratch?

---

## Industry Snapshots

### Snapshot 1: The Hyperscaler's Internal TCO Framework

A major cloud provider's internal quantum product team, preparing to price a new hardware generation, built a TCO framework that the external sales team was explicitly *not* allowed to use in customer conversations. The reason: the framework made clear that for workloads under a certain problem size, the honest recommendation was to use the provider's classical high-performance computing (HPC) service instead.

The framework's key insight was what the team called the "quantum premium curve" — the ratio of quantum TCO to classical TCO, plotted against problem size. Below a threshold they called the "breakover point," quantum was always more expensive. Above it, quantum could be competitive. The breakover point shifted left (toward smaller problem sizes) as hardware improved — which meant the framework had to be re-run every hardware generation.

The business lesson: cloud providers know the breakover exists. The best ones build it into their internal planning. You should build it into yours.

### Snapshot 2: The Bank That Skipped the Early Contract

A large retail bank's innovation team was presented with an early quantum contract from a hardware vendor in 2021. The application was portfolio optimization — a genuinely quantum-relevant domain. The contract was structured as a \$3.5M two-year research partnership with the vendor.

The bank's decision committee declined on a single basis: the TCO model, built by the quant team, showed that the optimization problem sizes that mattered to the bank required hardware that did not yet exist. Not "would cost too much" — did not exist. The logical qubit count required was two orders of magnitude beyond what any hardware offered.

The bank instead allocated \$200,000 to an internal quantum literacy program and established a vendor-agnostic monitoring process. In 2024, the same quant team ran the analysis again with updated hardware parameters. The breakover point had moved significantly. The team is now in active evaluation — but with two years of internal expertise that the teams who signed early contracts spent on vendor-specific integrations that had to be rebuilt.

The lesson: knowing *when not to invest* is itself a quantum strategy. The cheapest quantum path is the one that does not commit before the hardware is ready.

---

## Productive-Struggle Problem: Build a Break-Even for Portfolio Optimization

::::{dropdown} Problem Statement (click to expand)

**Scenario:** Your firm runs a classical mean-variance portfolio optimization on a universe of 150 assets. The current classical solution uses a commercial solver that costs \$0.12 per optimization run and returns a solution in 45 seconds. You are evaluating whether quantum optimization (specifically, a QAOA-based approach) could reduce cost or improve solution quality at this scale.

**Your Task:** Build a two-page break-even analysis following these constraints:

1. **All pricing lives in a single parameter block** — structure your spreadsheet or code so that updating vendor pricing requires changing exactly one section.
2. **Use the TCO six-stage framework** — account for all six stages, not just QPU cost.
3. **Include a sensitivity table** showing cost per useful result if:
   - Error rates drop by 10×
   - Required shots drop by half
   - Queue time doubles
4. **State your break-even condition** explicitly: what hardware capability (logical qubits, error rate) must exist for quantum to match classical cost?
5. **Use current pricing from the Market Snapshot appendix** — but write your model so any reader can substitute next year's prices in under 30 seconds.

**Deliverable:** A two-page document (one page model, one page narrative) structured as a memo to your CFO.

::::

::::{dropdown} Solution Framework (click to reveal after attempting)

**Break-Even Parameter Setup**

```
WORKLOAD PARAMETERS (do not change annually)
- Problem size: 150 assets
- Classical cost per run: \$0.12
- Classical solution time: 45 seconds
- Required optimization quality: Sharpe ratio ≥ classical baseline

QUANTUM PARAMETERS (update annually — single block)
- Shots per experiment: 8,000
- Circuit depth (QAOA, p=2): ~300 gates
- Two-qubit gate error rate: [from Market Snapshot]
- QPU cost per shot: [from Market Snapshot]
- Error mitigation multiplier: 3×
- Queue time (hours): [from current tier]
- Researcher rate ($/hr): your value

DERIVED: Cost per useful result
= (8,000 shots × 3× mitigation) × QPU_rate
  + queue_hours × researcher_rate
```

**Sensitivity Table**

| Scenario | Shots | Error Rate | Queue (hr) | Quantum Cost | vs Classical |
|---|---|---|---|---|---|
| Baseline | 8,000 | Current | 2h | Calculated | Ratio |
| Error ÷10 | 8,000 | Current/10 | 2h | Lower | Better |
| Shots ÷2 | 4,000 | Current | 2h | Lower | Better |
| Queue ×2 | 8,000 | Current | 4h | Higher | Worse |

**Break-Even Condition**
Quantum matches classical when:
`QPU_rate × 24,000 + queue_cost = 0.12`

Solve for QPU_rate: this gives you the price at which quantum becomes competitive *today*, with today's error rates and shot requirements. Then compute the logical qubit count needed: 150-asset QAOA at p=2 requires approximately 150+ qubits. Compare to hardware roadmaps.

**CFO Memo Guidance**
- Lead with the break-even condition, not the current cost comparison
- State the hardware milestone required (qubits + error rate)
- Give a timeline confidence range, not a point estimate
- Recommend a specific monitoring trigger (re-run this analysis when hardware reaches X)

::::

---

## Module-Level Outcomes

By completing this chapter and its labs, you should be able to:

1. **Compare pricing-model archetypes** and match each to workload characteristics — distinguishing pay-per-shot, pay-per-minute, reserved-capacity, and free-tier models, and explaining why archetype choice depends on workload maturity and volume predictability.

2. **Calculate a break-even** using a template that survives provider change — building a model with a single, updatable vendor-parameter block and validating it against a classical baseline benchmark.

3. **Decompose true computation cost** into its four drivers — shot count, circuit depth, error rate, and queue time — and explain how each factor compounds in the cost-per-useful-result formula.

4. **Assess error-correction overhead** on cost-per-useful-qubit — explaining the physical-to-logical qubit conversion, current overhead ratios, and how overhead reduction changes break-even economics.

5. **Distinguish advantage, utility, and supremacy** and use each correctly in vendor evaluation, board presentations, and investment decisions.

---

## Lab 3 (Regular): Running Your First Quantum Circuit and Reading the Bill

**Duration:** ~45 minutes  
**Tool:** IBM Quantum Composer (free tier at quantum.ibm.com)  
**Deliverable:** One-page memo to a CFO using the TCO framework

### Instructions

**Part 1: Build Your Circuit (~10 minutes)**

1. Create a free IBM Quantum account at quantum.ibm.com
2. Open the Quantum Composer (visual circuit editor)
3. Build a 3-qubit circuit with the following structure:
   - Apply a Hadamard gate to qubit 0
   - Apply a CNOT gate with qubit 0 as control, qubit 1 as target
   - Apply a CNOT gate with qubit 1 as control, qubit 2 as target
   - Measure all three qubits
4. This creates a 3-qubit GHZ state — a maximally entangled state that should produce only `000` and `111` outcomes with equal probability.

**Part 2: Run on Simulator (~5 minutes)**

1. Select the **ibmq_qasm_simulator** backend
2. Set shots = 1,024
3. Run the circuit. Record:
   - Result distribution (what fraction of shots returned `000`? `111`? Other states?)
   - Execution time
   - Cost (should be zero on free tier simulator)
4. An ideal GHZ state should show approximately 50% `000` and 50% `111`. Note any deviation.

**Part 3: Submit to Real Hardware (~15 minutes including queue)**

1. Select a real quantum backend (any available 5+ qubit device)
2. Use the same circuit and shot count
3. Submit and **record the queue time** — the time from submission to execution start
4. Once complete, record:
   - Result distribution (compare to simulator)
   - Which states appeared that shouldn't (these are noise artifacts)
   - Total elapsed time from submission to result

**Part 4: Fill the Unit Economics Worksheet**

| Metric | Simulator | Real Hardware |
|---|---|---|
| Shots submitted | 1,024 | 1,024 |
| Circuit depth | ___ | ___ |
| Queue time | ~0 sec | ___ min |
| Cost (USD) | \$0 | \$0 (free tier) |
| % correct results (000 or 111) | ~100% | ___% |
| Effective yield | 1.0 | ___ |
| Cost per useful result | \$0 | Calculate |

**Part 5: Write the CFO Memo (~15 minutes)**

Write a one-page memo addressed to a fictional CFO with the following structure:
- **Subject:** Quantum Circuit Pilot — Unit Economics Summary
- **What we did:** (one paragraph)
- **What it cost:** (use the TCO framework — all six stages)
- **What the noise means for production:** (one paragraph interpreting the hardware results)
- **Recommendation:** (one paragraph on whether to proceed to next phase)

### Learning Objectives
- Experience the gap between simulator and real-hardware results
- Calculate cost-per-useful-result on actual hardware
- Apply the TCO framework to a real (if tiny) quantum workload

---

## Lab 3 (Optional Advanced): Build Your Own Quantum TCO Calculator

**Duration:** ~2–3 hours  
**Tools:** Python 3, pandas, (optional) streamlit  
**Deliverable:** Working calculator + README + 400-word memo

### Overview

Build a reusable quantum TCO calculator that accepts workload parameters, loads vendor pricing from an external configuration file, and outputs a cost comparison table across provider archetypes.

### Starter Code

```python
#!/usr/bin/env python3
"""
quantum_tco.py — Quantum TCO Calculator
Update vendor_config.json annually; workload params stay stable.
"""

import json
import pandas as pd
from dataclasses import dataclass
from typing import Dict

# ── Workload Parameters (stable — your problem defines these) ──────────────
@dataclass
class WorkloadParams:
    shots_per_experiment: int = 10_000
    experiments_per_run: int = 20
    circuit_depth: int = 50
    logical_qubits_required: int = 10
    classical_cost_per_run_usd: float = 0.85
    researcher_hourly_rate_usd: float = 150.0
    
# ── Vendor Config (load from file — update annually) ──────────────────────
def load_vendor_config(path: str = "vendor_config.json") -> Dict:
    """Load vendor pricing. All volatile params live here."""
    try:
        with open(path) as f:
            return json.load(f)
    except FileNotFoundError:
        # Default config — replace with current vendor pricing annually
        return {
            "pay_per_shot": {
                "cost_per_shot_usd": 0.00001,
                "avg_queue_hours": 2.0,
                "min_job_fee_usd": 0.50,
                "notes": "Update from vendor pricing page"
            },
            "pay_per_minute": {
                "cost_per_minute_usd": 0.10,
                "avg_queue_hours": 0.5,
                "min_reservation_minutes": 60,
                "notes": "Assumes dense circuit packing"
            },
            "reserved_capacity": {
                "monthly_fee_usd": 5000.0,
                "included_shots": 5_000_000,
                "overage_per_shot_usd": 0.000008,
                "notes": "Amortized over typical monthly volume"
            },
            "hardware": {
                "physical_error_rate": 0.005,
                "physical_to_logical_ratio": 1000,
                "error_mitigation_multiplier": 3.0
            }
        }

# ── Cost Calculation ───────────────────────────────────────────────────────
def calculate_tco(
    workload: WorkloadParams,
    vendor: Dict,
    archetype: str
) -> Dict:
    """Calculate TCO for a given archetype."""
    hw = vendor["hardware"]
    em_multiplier = hw["error_mitigation_multiplier"]
    effective_shots = workload.shots_per_experiment * em_multiplier
    total_shots = effective_shots * workload.experiments_per_run
    
    if archetype == "pay_per_shot":
        cfg = vendor["pay_per_shot"]
        qpu_cost = max(
            total_shots * cfg["cost_per_shot_usd"],
            cfg["min_job_fee_usd"]
        )
        queue_cost = cfg["avg_queue_hours"] * workload.researcher_hourly_rate_usd
        
    elif archetype == "pay_per_minute":
        cfg = vendor["pay_per_minute"]
        # Estimate circuit time: ~100 microseconds per depth layer per shot
        circuit_time_min = (
            total_shots * workload.circuit_depth * 0.0001 / 60
        )
        billed_minutes = max(circuit_time_min, cfg["min_reservation_minutes"])
        qpu_cost = billed_minutes * cfg["cost_per_minute_usd"]
        queue_cost = cfg["avg_queue_hours"] * workload.researcher_hourly_rate_usd
        
    elif archetype == "reserved_capacity":
        cfg = vendor["reserved_capacity"]
        # Amortize monthly fee over runs per month (assume 200 runs/month)
        runs_per_month = 200
        qpu_cost = cfg["monthly_fee_usd"] / runs_per_month
        if total_shots > cfg["included_shots"] / runs_per_month:
            overage = total_shots - cfg["included_shots"] / runs_per_month
            qpu_cost += overage * cfg["overage_per_shot_usd"]
        queue_cost = 0  # Reserved capacity = minimal queue
    else:
        raise ValueError(f"Unknown archetype: {archetype}")
    
    total_quantum = qpu_cost + queue_cost
    classical = workload.classical_cost_per_run_usd * workload.experiments_per_run
    
    return {
        "archetype": archetype,
        "qpu_cost_usd": round(qpu_cost, 4),
        "queue_cost_usd": round(queue_cost, 4),
        "total_quantum_usd": round(total_quantum, 4),
        "classical_baseline_usd": round(classical, 4),
        "quantum_vs_classical": round(total_quantum / classical, 2),
        "effective_shots": int(total_shots),
        "status": "QUANTUM ADVANTAGE" if total_quantum < classical else "CLASSICAL PREFERRED"
    }

# ── Sensitivity Analysis ───────────────────────────────────────────────────
def sensitivity_table(workload: WorkloadParams, vendor: Dict) -> pd.DataFrame:
    """Show how cost changes under optimistic/pessimistic scenarios."""
    scenarios = {
        "Baseline": {},
        "Error rate ÷10": {"error_multiplier_override": 
                           vendor["hardware"]["error_mitigation_multiplier"] / 10},
        "Shots ÷2": {"shots_override": workload.shots_per_experiment // 2},
        "Queue ×2": {"queue_multiplier": 2.0},
    }
    
    rows = []
    for scenario_name, overrides in scenarios.items():
        for archetype in ["pay_per_shot", "pay_per_minute", "reserved_capacity"]:
            # Apply overrides (simplified for illustration)
            result = calculate_tco(workload, vendor, archetype)
            result["scenario"] = scenario_name
            rows.append(result)
    
    df = pd.DataFrame(rows)[
        ["scenario", "archetype", "total_quantum_usd", "quantum_vs_classical", "status"]
    ]
    return df

# ── Main ───────────────────────────────────────────────────────────────────
if __name__ == "__main__":
    workload = WorkloadParams()
    vendor = load_vendor_config()
    
    print("=" * 60)
    print("QUANTUM TCO CALCULATOR")
    print("=" * 60)
    print(f"Classical baseline: ${workload.classical_cost_per_run_usd * workload.experiments_per_run:.2f} per run\n")
    
    for archetype in ["pay_per_shot", "pay_per_minute", "reserved_capacity"]:
        result = calculate_tco(workload, vendor, archetype)
        print(f"[{archetype.upper()}]")
        print(f"  QPU cost:        ${result['qpu_cost_usd']:.4f}")
        print(f"  Queue cost:      ${result['queue_cost_usd']:.4f}")
        print(f"  Total quantum:   ${result['total_quantum_usd']:.4f}")
        print(f"  vs Classical:    {result['quantum_vs_classical']}x")
        print(f"  Status:          {result['status']}\n")
    
    print("\nSENSITIVITY ANALYSIS:")
    print(sensitivity_table(workload, vendor).to_string(index=False))
```

### vendor_config.json Template

```json
{
  "pay_per_shot": {
    "cost_per_shot_usd": 0.00001,
    "avg_queue_hours": 2.0,
    "min_job_fee_usd": 0.50,
    "notes": "Update from vendor pricing page — current as of [date]"
  },
  "pay_per_minute": {
    "cost_per_minute_usd": 0.10,
    "avg_queue_hours": 0.5,
    "min_reservation_minutes": 60,
    "notes": "Assumes dense circuit packing"
  },
  "reserved_capacity": {
    "monthly_fee_usd": 5000.0,
    "included_shots": 5000000,
    "overage_per_shot_usd": 0.000008,
    "notes": "Amortized over 200 runs/month"
  },
  "hardware": {
    "physical_error_rate": 0.005,
    "physical_to_logical_ratio": 1000,
    "error_mitigation_multiplier": 3.0
  }
}
```

### Deliverable Requirements

1. **Working calculator:** The script must run with `python quantum_tco.py` and produce a cost comparison table and sensitivity analysis
2. **README.md:** Explain how to update `vendor_config.json` with current pricing, how to modify `WorkloadParams` for a new workload, and what each output metric means
3. **400-word memo:** Addressed to a CFO; explain what the model shows, what assumptions drive the result most, and what hardware milestone would change the recommendation

---

## Discussion Guidelines

The economics of quantum computing sit at the intersection of technology assessment and strategic finance — a domain where most participants have expertise in one but not both.

**Prompt 1:** IBM's 2023 "quantum utility" demonstration (reported in *Nature*, Kim et al., 2023) claimed results on a 127-qubit processor that were difficult to verify by classical simulation at the same scale. Critics argued the results did not demonstrate *advantage* for a commercially useful task. Using the three-term framework from this chapter (supremacy, advantage, utility), evaluate whether IBM's claim was accurate — and whether it was appropriate to publicize in the way it was. Cite at least one scholarly or technical source in your response.

**Prompt 2:** A colleague argues that quantum pricing models are pointless because "quantum costs will just follow the same exponential decline as classical hardware — we'll figure it out when the time comes." Using the physical-to-logical overhead concept and the TCO framework, construct a specific, evidence-based rebuttal. What makes quantum cost decline structurally different from classical Moore's Law scaling?

**Peer Response Guidelines:**
- Respond substantively to at least **two** peers' posts — not just agreement or disagreement, but engagement with their reasoning. Challenge an assumption, extend their argument with a scenario they did not consider, or offer a counter-example from a different industry.
- Peer responses should be at minimum 150 words and should reference specific claims from the original post.
- Shallow responses ("Great point!") do not count toward the participation requirement.

---


## Glossary

```{glossary}
Shot
  A single execution of a quantum circuit from initialization through measurement, producing one classical bitstring result. Useful quantum results require averaging across many shots.

Circuit Depth
  The number of sequential layers of quantum gate operations in a circuit. Deeper circuits accumulate more error due to decoherence and gate noise.

Physical Qubit
  An individual quantum system (superconducting, trapped ion, photonic, etc.) capable of holding a superposition state. Subject to noise and decoherence.

Logical Qubit
  An error-corrected qubit constructed from multiple physical qubits. Provides reliable quantum computation at the cost of significant physical-qubit overhead.

Physical-to-Logical Ratio
  The number of physical qubits required to implement one logical qubit under a given error correction code. Currently ranges from hundreds to thousands.

Error Mitigation
  Classical post-processing techniques applied to noisy quantum results to reduce the impact of hardware errors without full error correction. Includes zero-noise extrapolation and probabilistic error cancellation.

Zero-Noise Extrapolation (ZNE)
  An error mitigation technique that runs the circuit at multiple artificially scaled noise levels and extrapolates to the zero-noise limit. Requires additional shots (typically 2–5×).

Quantum Supremacy
  The condition in which a quantum computer performs a specific computation faster than any classical computer could within a practical timeframe. The task is typically not practically useful.

Quantum Advantage
  The condition in which a quantum computer solves a practically useful problem faster, cheaper, or more accurately than the best available classical alternative.

Quantum Utility
  A condition (lower bar than advantage) in which a quantum computer produces results that are difficult or impossible to verify by classical simulation, enabling novel research even without demonstrated speedup.

Total Cost of Ownership (TCO)
  The complete cost of a quantum workload across all six pipeline stages: ingestion, pre-processing, quantum submission, error mitigation, post-processing, and validation.

Pay-Per-Shot
  A quantum cloud pricing archetype where cost is charged per circuit execution (shot or job). Optimal for low-volume, exploratory workloads.

Pay-Per-Minute
  A quantum cloud pricing archetype where cost is charged for wall-clock time on a quantum processor. Optimal for dense, back-to-back circuit execution.

Reserved Capacity
  A quantum cloud pricing archetype where a defined quantum resource is committed for a fixed term at a discounted rate. Optimal for production workloads with predictable volume.

Break-Even Point
  The problem scale or hardware capability threshold at which quantum cost equals classical cost. The business-relevant frontier for quantum investment decisions.

Variational Quantum Eigensolver (VQE)
  A hybrid quantum-classical algorithm for finding the ground-state energy of a quantum system. A primary candidate workload for near-term quantum advantage in chemistry and materials science.

QAOA (Quantum Approximate Optimization Algorithm)
  A hybrid quantum-classical algorithm for combinatorial optimization problems. A candidate workload for quantum advantage in logistics, finance, and scheduling.

Queue Time
  The wait between submitting a quantum circuit job and its execution on hardware. A significant and often underestimated cost driver in quantum TCO.

NISQ (Noisy Intermediate-Scale Quantum)
  The current era of quantum computing, characterized by devices with 50–1,000 physical qubits operating without full error correction. Results are noisy and circuit depth is limited.

Surface Code
  The most widely researched quantum error correction code. Requires a 2D grid of physical qubits and achieves high fault tolerance at the cost of large physical-to-logical overhead.
```

---

## Leader's Takeaway

::::{figure} ../images/ch03-sensitivity-analysis.png
:label: fig-ch03-sensitivity-analysis
:alt: Quantum TCO sensitivity analysis table showing how cost changes under different scenarios
:width: 100%
**Figure 3.10.** Sensitivity analysis reveals which cost driver to attack first. In most near-term quantum workloads, queue time dominates — not QPU pricing. That changes the operational decision from "negotiate a better rate" to "secure reserved access."
::::

The lesson every executive takes away from their first quantum vendor meeting is the wrong one. They walk out thinking: *quantum is expensive, so we need a better price.*

The lesson this chapter teaches is different: quantum is expensive in a specific way, for specific reasons, that are changing at different rates. QPU pricing is falling. Error rates are improving. Queue times on premium tiers are decreasing. Physical-to-logical overhead is on a long but measurable improvement trajectory.

The correct executive question is not "what does quantum cost today?" It is: "which of my workloads will cross the break-even line first, and what hardware milestone triggers that crossing?"

Build your model around that question. Put vendor pricing in one swappable block. Benchmark against the best classical alternative, not legacy systems. Account for all six TCO stages. Distinguish advantage from utility from supremacy so you can evaluate vendor claims correctly.

And remember the most durable insight from this chapter: **the cheapest quantum strategy is the one that knows which of your workloads *shouldn't* go quantum.** The bank that declined the 2021 contract did not lose two years — it bought two years of optionality. The pharma CFO who built the vendor-agnostic model did not waste \$400,000 — she bought the right to act decisively when the hardware matures.

Quantum economics rewards preparation more than commitment. Prepare the model. Monitor the milestones. Commit when the numbers say so — not when the vendor does.
