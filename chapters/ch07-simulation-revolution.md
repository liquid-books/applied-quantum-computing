---
title: "Chapter 7: Quantum Industry Verticals — Finance, Supply Chain, Healthcare, and Energy"
subtitle: "The Industries That Understand Quantum First Will Lead. The Industries That Don't Will Follow."
short_title: "Ch. 7: Quantum Industry Verticals"
description: "Quantum computing's commercial value is not uniformly distributed. This chapter maps four industry verticals — financial services, supply chain and logistics, healthcare and pharma, and energy and materials — against the quantum techniques that reshape them: optimization via D-Wave annealing, simulation via VQE, and hybrid quantum-classical analytics. For each vertical, you will find the business case, the leading enterprise deployments, and a hands-on framework for evaluating quantum opportunity in your own sector."
label: ch-07-simulation-revolution
tags: [quantum finance, quantum supply chain, quantum healthcare, quantum pharma, quantum energy, VQE, D-Wave, annealing, quantum simulation, industry verticals, JPMorgan, Goldman, Volkswagen, DHL, Boehringer Ingelheim, ExxonMobil, FAU Advantage2, Ocean SDK, molecular simulation]
---

# Chapter 7: Quantum Industry Verticals — Finance, Supply Chain, Healthcare, and Energy

:::{figure} ../images/ch07-explainer-infographic.png
:label: fig-ch07-explainer
:alt: Chapter 7 explainer infographic showing four industry quadrants — financial services, supply chain, healthcare and pharma, and energy and materials — each with leading quantum techniques and enterprise case studies.
:width: 100%
:align: center

**Chapter 7 at a Glance.** Quantum computing's commercial impact is concentrated in four industry verticals, each with a distinct problem class and a distinct quantum technique. Financial services and supply chain are the early commercial frontier — optimization-heavy, near-term, and accessible today through D-Wave's annealing hardware. Healthcare and pharma represent the highest long-term NPV. Energy and materials hold civilization-scale stakes. This chapter maps the landscape of all four.
:::

The previous chapters established the two quantum paradigms — gate-model and annealing — and their core algorithms: QUBO optimization on D-Wave annealers, VQE simulation on gate-model hardware, and the security migration tools of Chapter 5. This chapter is where those tools meet actual industries.

Quantum computing's value is not spread evenly across the economy. It concentrates in industries where the computationally hard problems are also the economically significant ones — where the gap between "good enough" and "optimal" is measured in billions of dollars or human lives. This chapter maps four of those industries in depth: the problem each faces, the quantum technique that addresses it, the enterprises already acting, and the business case you can bring to your own organization.

The two paradigms continue to play distinct roles. **D-Wave annealing** — the technology behind FAU's Advantage2 and the subject of Lab 7B — is the production tool for optimization-heavy problems: portfolio construction, supply chain routing, grid scheduling. It is accessible today. **Gate-model simulation via VQE** — the subject of Labs 7A and 7C — addresses the molecular problems of drug discovery and materials science. It is in the research-to-commercial transition, with the highest long-term economic stakes of any quantum application.

Understanding both, and knowing which to reach for in which context, is the strategist's advantage.

---

## Opening Scene: Four Rooms, One Technology

### Room One — A Trading Floor, Lower Manhattan, 2025

A portfolio risk manager at a major investment bank stares at a screen showing 3,000 correlated securities, 200 active constraints, and a 3-minute window to rebalance before the market opens. The classical optimization engine that has served the desk for a decade is producing solutions. Feasible solutions. Not necessarily optimal ones.

In the next room, the bank's quantum team has spent eighteen months formulating the same portfolio optimization as a QUBO. Today they are submitting it to D-Wave's Stride hybrid solver. The result comes back in 90 seconds — a portfolio allocation that their quantum solution benchmarks against the classical baseline. The difference: 0.3% better risk-adjusted return on a \$4 billion portfolio. That is \$12 million.

### Room Two — A Logistics Control Center, Hamburg, 2025

A fleet operations manager at a logistics company oversees 400 delivery vehicles serving 6,000 daily stops across Northern Europe. Every day, the classical routing algorithm finds *a* solution. Vehicle routing with 400 vehicles is a combinatorial explosion — the number of possible route combinations exceeds the atoms in the observable universe. The algorithm finds one of billions of locally good routes. Nobody knows how far from optimal it is.

Down the hall, a pilot team has reformulated a 50-vehicle subset of the routing problem as a QUBO. D-Wave's hybrid solver has been running against the classical baseline for three weeks. Average improvement: 8% reduction in total distance. On a 400-vehicle fleet at current fuel costs, 8% is \$3.2 million per year.

### Room Three — A Drug Discovery Lab, Ingelheim, Germany, 2024

A computational chemist at Boehringer Ingelheim is staring at a protein structure on her screen. It is the binding site of a kinase implicated in a rare form of leukemia. She has a list of 12,000 candidate drug fragments, ranked by classical DFT calculations of binding affinity. Classical DFT gets the ranking roughly right — most of the time. But it systematically misses electron correlation effects in strongly bound fragments, producing false positives that consume years of wet lab synthesis and testing.

Her team has been running VQE calculations on small fragments using IBM's quantum hardware. For fragments with 8-12 electrons — small enough for today's NISQ devices — the quantum calculations match experimental binding data significantly better than DFT. The application is narrow but the implication is not: if quantum simulation can improve the top-20 ranking accuracy for drug fragments, the number of false positives that advance to costly synthesis drops by an estimated 30%.

### Room Four — An Energy Research Center, Houston, 2024

An energy company's research team is designing the next generation of MOF (metal-organic framework) materials for post-combustion carbon capture. The challenge is quantum mechanical: the CO₂ binding energy to the MOF surface is governed by electron correlation effects that classical DFT calculations disagree on by 20–30% — a margin large enough to make a viable material look unviable and vice versa.

On a whiteboard behind the team: a timeline. Three years to find a viable MOF chemistry. Five years to scale it to pilot plant. The quantum calculation that would narrow the error margin from 30% to 5% requires 50 logical qubits and low error rates. Hardware projections suggest that capability arrives in 2027–2028. The research team is building the workflow now.

---

## The Single Idea

```{epigraph}
Quantum computing's commercial value concentrates where the computational problem and the economic problem are the same problem. In financial services, supply chain, healthcare, and energy, the gap between classical approximation and quantum accuracy is measured in billions of dollars, millions of tons of CO₂, and human lives. This chapter maps those gaps — and the quantum techniques, timelines, and enterprise actions that close them.
```

---

## Part I: Financial Services — Optimization at the Speed of Markets

### The Problem Financial Services Has Always Had

Finance runs on one fundamental operation: finding the best allocation of resources under constraints. Which portfolio of securities maximizes risk-adjusted return given 200 investment policy constraints? Which set of trades minimizes market impact while rebalancing a \$10 billion fund? Which combination of derivatives hedges a complex exposure while satisfying capital requirements?

These are combinatorial optimization problems. And the defining characteristic of combinatorial optimization is that the solution space grows exponentially with the number of variables. A portfolio of 500 securities has more possible allocations than atoms in the observable universe. Classical optimization engines solve these problems brilliantly — for reasonable definitions of "solve." They find feasible solutions. Good ones, often. But provably optimal? Rarely, for problems at production scale.

The gap between "good" and "optimal" in financial optimization is not a theoretical curiosity. It is a measurable, quarterly, dollar-denominated gap that shows up in portfolio performance, in trading costs, in capital allocation efficiency. For institutions running trillions in assets, closing that gap by even a fraction of a percent per year is worth more than the entire current quantum computing industry.

:::{figure} ../images/ch07-finance-optimization-landscape.png
:label: fig-finance-optimization
:alt: Financial services quantum optimization map showing portfolio optimization, Monte Carlo risk, derivatives pricing, and fraud detection with classical vs quantum approaches.
:width: 100%
:align: center

**The Financial Services Quantum Opportunity Map.** Portfolio optimization and Monte Carlo risk acceleration are near-term applications accessible through D-Wave annealing and quantum-inspired methods today. Derivatives pricing and fraud graph optimization sit in the hybrid zone. Full quantum advantage for the most complex financial models requires fault-tolerant hardware.
:::

### Portfolio Optimization as QUBO

The connection between portfolio optimization and quantum annealing is more direct than it first appears. Modern portfolio construction — selecting weights for N securities to maximize expected return subject to risk and constraint bounds — can be reformulated as a QUBO problem. Binary variables represent inclusion or exclusion decisions; quadratic terms capture the covariance structure; penalties encode constraints.

This reformulation is not trivial engineering. But it is exactly the skill developed in Chapter 6 — and the same D-Wave Ocean SDK that BASF uses for manufacturing scheduling is the tool that financial services firms use for portfolio construction. The hardware is the same. The formulation is different.

JPMorgan Chase's quantum computing research team — one of the most active in global finance — has published extensively on this approach. Their QUBO formulations for portfolio optimization show that for constrained portfolios with 50–200 securities, D-Wave's hybrid solver produces solutions competitive with state-of-the-art classical optimizers while exploring a broader solution space. The improvement is not dramatic at current scale. But the trajectory of hardware improvement suggests that the advantage grows as problem size increases — exactly the regime that matters most for institutional asset management.

### Monte Carlo Risk Acceleration

Risk management in financial services runs on Monte Carlo simulation: generating millions of scenarios for how a portfolio, a loan book, or a derivatives position might behave under different market conditions, then aggregating the distribution of outcomes. Classical Monte Carlo is computationally expensive — banks spend hundreds of millions of dollars on compute infrastructure for risk calculations alone.

Quantum computing offers two distinct paths to Monte Carlo acceleration. **Quantum amplitude estimation** — a gate-model algorithm — provides a quadratic speedup over classical Monte Carlo for certain calculation structures, meaning that a calculation requiring one million classical simulations might be achievable with one thousand quantum operations. This advantage requires fault-tolerant hardware; the benefit on NISQ devices is limited.

**Quantum-inspired sampling** — algorithms that use the mathematical structure of quantum mechanics while running on classical hardware — offers more near-term practical gains. Goldman Sachs has published work on quantum-inspired algorithms for option pricing that achieve 10–100x speedup over classical Monte Carlo for specific derivative structures, running on conventional hardware with no quantum device required.

### Fraud Detection as Graph Optimization

Mastercard's deployment of D-Wave's hybrid solver for transaction graph analysis — introduced in Chapter 6 as part of the optimization case studies — represents one of the most commercially deployed quantum applications in financial services. The fraud detection problem is fundamentally a graph problem: a transaction network where nodes are accounts and edges are transactions, and the goal is to identify subgraph patterns consistent with fraudulent behavior.

Classical graph algorithms for this problem scale poorly with network size. Mastercard's QUBO formulation of the fraud graph optimization runs on D-Wave's hybrid solver in production, scanning transaction networks for anomalous patterns at a scale that classical clustering algorithms cannot match. The reported result: improvement in fraud detection precision that reduces both false positive rates (legitimate transactions incorrectly blocked) and false negatives (fraudulent transactions that slip through).

### The Quantum Finance Timeline

::::{grid} 3

:::{card} 🟢 Now — Accessible Today
**QUBO portfolio optimization** via D-Wave Stride (50–500 securities, constrained allocation)

**Quantum-inspired Monte Carlo** on classical hardware (Goldman Sachs approach)

**Fraud graph optimization** via D-Wave hybrid solver (in production at Mastercard)
:::

:::{card} 🟡 Near-Term (2026–2029)
**Full production portfolio optimization** at institutional scale (1,000+ securities)

**Quantum amplitude estimation** for risk calculations on early fault-tolerant hardware

**Credit scoring kernels** via quantum machine learning (see Chapter 8)
:::

:::{card} 🔵 Long-Horizon (2030+)
**Real-time derivatives pricing** at full market complexity

**Portfolio optimization across correlated global asset classes** at trillion-dollar scale

**Quantum-native risk models** for systemic risk scenarios
:::

::::

---

## Part II: Supply Chain and Logistics — Routing the World's Complexity

### The Routing Problem That Never Gets Old

The vehicle routing problem was first formalized in 1959. Sixty-five years of operations research, millions of person-years of algorithmic effort, and petaflops of computing power have produced extraordinary classical routing solvers. They have not solved the routing problem. They have found excellent approximations.

The reason is fundamental: vehicle routing with 400 vehicles and 6,000 stops is a combinatorial problem whose solution space grows faster than any exponential. Classical solvers find locally optimal routes — the best solution in their algorithmic neighborhood. They cannot prove global optimality, because exhaustive search is computationally impossible. The gap between the locally optimal solution and the global optimum is invisible to the solver and unmeasurable by the operator.

For global logistics networks, that invisible gap is expensive. A 5% improvement in routing efficiency across DHL's global delivery network — 600 million shipments per year — is worth hundreds of millions of dollars annually. For ExxonMobil's marine logistics, a 3% reduction in fleet routing cost is worth tens of millions per year. The economics of supply chain optimization are not academic. They are among the most financially significant quantum computing applications available today.

:::{figure} ../images/ch07-supply-chain-quantum-map.png
:label: fig-supply-chain-map
:alt: Supply chain quantum opportunity map showing vehicle routing, multi-echelon inventory, demand forecasting, and resilience modeling with quantum approach and readiness level.
:width: 100%
:align: center

**The Supply Chain Quantum Opportunity Map.** Vehicle routing and scheduling are the most near-term accessible applications — QUBO-formulated and D-Wave-ready today. Multi-echelon inventory optimization and resilience modeling follow closely. Demand forecasting under uncertainty benefits from quantum machine learning approaches covered in Chapter 8.
:::

### Volkswagen: From Pilot to Production Methodology

Volkswagen's quantum routing pilot — run in Lisbon in 2019 with four conference buses and a D-Wave annealer — was the first public demonstration of quantum optimization on a real urban routing problem. The results were directionally positive: the quantum formulation produced better routes than the classical baseline for the specific four-vehicle problem. The hardware limitation was also immediately clear: 2019 D-Wave hardware could not handle Volkswagen's production problem (thousands of vehicles, millions of constraints) in a single QPU submission.

Volkswagen's response to that limitation is the more instructive story. Rather than waiting for larger quantum hardware, their team took the QUBO mathematical framework they had developed and ported it to quantum-inspired classical solvers — Fujitsu's Digital Annealer and other QUBO-compatible classical optimizers. The result: documented efficiency improvements of 3–8% in parts logistics routing and 2–5% in factory scheduling throughput at their Wolfsburg and Zwickau plants. The quantum pilot had generated not just a routing improvement but a mathematical formulation — a QUBO — that delivered production value immediately, on classical hardware, while quantum hardware matures.

This is the "quantum-inspired bridge" pattern that will appear across multiple industries: the value of learning to formulate problems as QUBOs is not contingent on having quantum hardware capable of solving them. The formulation itself transfers to near-term classical solutions and positions the organization for production quantum deployment when hardware scales.

### DHL: Supply Chain Resilience as Optimization

DHL has explored quantum optimization for supply chain resilience modeling — a problem that goes beyond routing to ask: given a disruption (a port closure, a supplier failure, a weather event), what is the optimal reallocation of inventory and routing across the supply network to minimize service level degradation?

This is a harder combinatorial problem than routing alone, because it involves simultaneous optimization of inventory positions, transportation modes, and supplier selections across a multi-echelon network. Classical approaches either simplify the problem (optimizing one layer at a time) or use heuristics that cannot guarantee near-optimal solutions at global scale.

The QUBO formulation of supply chain resilience optimization maps naturally to D-Wave's hybrid solver: binary variables represent allocation decisions (route this shipment through Frankfurt hub vs. Amsterdam), quadratic terms capture the cost interactions between decisions, and penalty terms enforce service level constraints. DHL's research has shown that hybrid quantum-classical approaches to resilience modeling explore a broader solution space than classical heuristics, finding allocations that better maintain service levels during disruption scenarios.

### ExxonMobil: Marine Logistics and LNG Routing

ExxonMobil's quantum computing program spans two application areas: materials science (carbon capture sorbents, addressed in Part IV) and marine logistics optimization. Their LNG (liquefied natural gas) shipping operations involve scheduling a fleet of specialized vessels across complex port networks, subject to weather routing, port availability, contractual delivery windows, and vessel-specific capacity constraints.

The LNG scheduling problem has more constraints than most routing problems — LNG vessels cannot wait in port beyond specific windows, weather routing significantly changes fuel and time estimates, and multi-charter contracts create complex dependency structures between voyages. Classical operations research tools find feasible schedules reliably; they miss significant optimization value in complex constraint combinations.

ExxonMobil's partnership with IBM Quantum has explored QAOA (Quantum Approximate Optimization Algorithm) formulations of LNG scheduling. While QAOA on current hardware delivers limited advantage over classical approaches, the formulation work — developing the mathematical structure of the scheduling problem as a quantum-compatible model — is itself the durable output. When hardware scales, the model is ready.

### Verge Ag: Quantum Optimization in the Field

Verge Ag's partnership with D-Wave represents one of the more unexpected enterprise quantum deployments: autonomous agricultural fleet routing. Managing autonomous tractors and harvesting equipment across large-scale agricultural operations involves real-time routing decisions with complex constraints — field boundaries, crop maturity schedules, equipment fuel states, and dynamic weather conditions.

Verge Ag formulated their fleet coordination problem as a QUBO and deployed D-Wave's Stride hybrid solver for real-time route optimization. The production deployment enables autonomous fleets to replan routes dynamically as conditions change — a problem class where classical routing algorithms required human intervention for the dynamic replanning decisions that actually occur in field operations. D-Wave's hybrid solver handles the replanning computation at operational speed.

---

## Part III: Healthcare and Pharma — The Highest-NPV Vertical

### Why Molecules Are Quantum Systems

Before mapping pharmaceutical quantum applications, it is worth establishing the foundational point that makes this vertical unique: the problem that quantum computers were literally invented to solve is a molecular problem.

In 1982, Richard Feynman delivered a lecture at MIT articulating a simple and profound observation: if you want to simulate a quantum system, you need a quantum machine. A molecule — any molecule — is a quantum system. Its electrons do not orbit the nucleus in fixed paths. They exist in quantum probability distributions, entangled with each other, interfering with each other, tunneling through energy barriers that classical physics says are impenetrable. Every bond angle, every reaction rate, every binding affinity — the property that determines whether a drug molecule heals or harms — is the output of these quantum interactions.

Classical computers cannot accurately simulate these interactions at the scale of drug-relevant molecules. The computational cost grows exponentially with the number of electrons in the system. Classical approximation methods — Hartree-Fock, Density Functional Theory, coupled-cluster methods — have been refined over decades into extraordinarily useful tools. But they are approximations. Quantum computers, running algorithms like VQE (Variational Quantum Eigensolver), compute these interactions directly — the way nature computes them — at polynomial rather than exponential cost.

This is not a near-term hardware limitation waiting to be engineered away. It is a mathematical fact about the structure of quantum mechanics. Quantum computers are not faster classical computers for molecular simulation. They are the right kind of computer for the problem.

:::{figure} ../images/ch07-molecular-simulation-advantage.png
:label: fig-molecular-advantage
:alt: Comparison of classical simulation exponential scaling vs quantum simulation polynomial scaling for molecular systems, with drug molecule size on x-axis.
:width: 100%
:align: center

**Why Quantum Simulation Is Inevitable for Pharma.** Classical simulation cost grows exponentially with molecular size. Quantum simulation scales polynomially. The crossover point — where quantum beats classical — moves progressively toward drug-relevant molecule sizes as hardware matures. For computational drug discovery, this is not a question of whether but when.
:::

### The Drug Development Economics

The economics of quantum simulation in pharmaceuticals follow a logic that holds even under conservative assumptions. The average new drug costs \$2.6 billion to develop and takes more than a decade. Approximately 90% of drug candidates that enter Phase I clinical trials fail to receive FDA approval. A significant fraction of those failures occur because classical molecular simulation predicted properties — binding affinity, selectivity, metabolic stability — that experimental testing did not confirm.

Quantum simulation addresses this failure mode directly. It improves the accuracy of molecular property prediction in the early discovery stage, before the expensive synthesis and testing phases begin. Better prediction means fewer false positives advancing to synthesis. Fewer false positives means a higher probability of success for the candidates that do advance. And a higher probability of success, compounded across a pipeline of 10-15 drug candidates, is worth billions in risk-adjusted NPV.

The R&D acceleration model is equally compelling. For a drug expected to generate \$500 million per year in peak revenue, every year shaved from the development timeline is worth approximately \$400–600 million in discounted NPV. Two years of acceleration, across a 12-drug pipeline, creates \$10–24 billion in shareholder value — a number that dwarfs even a substantial quantum computing investment.

### VQE: The Algorithm at the Heart of Quantum Pharma

**VQE — the Variational Quantum Eigensolver** — is the algorithm that makes quantum simulation tractable on today's noisy hardware. It works as a hybrid loop: a parameterized quantum circuit (the "ansatz") prepares a trial quantum state encoding a guess about the molecule's electronic structure; the quantum processor measures the energy of that state; a classical optimizer adjusts the circuit parameters to lower the energy; the loop repeats until convergence.

The key physical insight behind VQE is the **Variational Principle**: any trial quantum state has energy equal to or greater than the true ground-state energy. Minimizing the energy of trial states therefore converges on the true ground state — the electronic configuration molecules actually occupy, and the configuration that determines all chemical properties.

VQE's practical advantage on today's hardware is that it is noise-tolerant in a specific way: quantum noise shifts the energy estimates but does not prevent convergence. This makes VQE the bridge algorithm for the NISQ-to-fault-tolerant transition — useful now for small molecules, increasingly powerful as hardware matures.

::::{prf:definition} VQE (Variational Quantum Eigensolver)
:label: def-vqe

A hybrid classical-quantum algorithm for finding the ground-state energy of a molecular system. A parameterized quantum circuit prepares a trial state; the quantum hardware measures its energy; a classical optimizer minimizes that energy over the circuit parameters. The result is the ground-state energy and wavefunction of the molecule — the foundation of all molecular property prediction in quantum chemistry.
::::

### Pharmaceutical Vertical: The Leading Deployments

`````{tab-set}
````{tab-item} Boehringer Ingelheim
**The Program:** The deepest and most publicly documented pharmaceutical quantum program in the industry. Boehringer's multi-year partnership with Google Quantum AI targets quantum simulation of molecular systems directly relevant to their drug discovery pipeline — not as a research curiosity, but as a systematic upgrade to their computational chemistry infrastructure.

**What They Have Done:** Published joint research demonstrating VQE calculations on drug-relevant molecular fragments (4–12 electrons) with accuracy competitive with high-level classical coupled-cluster methods. Developed error mitigation techniques for VQE that benefit the entire field. Built in-house quantum chemistry expertise — not outsourcing scientific understanding to the hardware vendor.

**The Structure:** Milestone-based, not access-based. The partnership is organized around scientific deliverables at defined accuracy thresholds, giving Boehringer optionality: if quantum simulation reaches targets, the company has embedded expertise to scale; if it doesn't, the published science is still real capital.

**The Open Question:** The accuracy-scalability trade-off. VQE achieves high accuracy on small systems today. Drug-relevant molecules require 100–1,000 logical qubits with low error rates — approximately 5–8 years ahead on hardware roadmaps. Boehringer's bet: the investment in expertise today positions them to capture disproportionate value when hardware arrives.
````
````{tab-item} Roche
**The Focus:** Protein-ligand binding prediction — the foundational problem in drug design. Roche's computational chemistry team has run VQE calculations on small molecular fragments relevant to their oncology pipeline, targeting improved prediction of binding affinity in kinase inhibitors. Small structural changes in kinase inhibitors produce large efficacy differences that classical DFT systematically mispredicts.

**Current Scope:** Publicly framed as a "10-year horizon" technology while running internal pilots on 2–3 year timelines. The gap between public positioning and internal activity is characteristic of pharmaceutical companies managing investor expectations while building competitive capabilities.

**The Opportunity:** Kinase inhibitor development has one of the highest false positive rates in drug discovery — classical methods get the rough ranking of candidates right but miss the fine-structure binding predictions that separate successful drugs from Phase II failures. Quantum improvement at this step has particularly high NPV leverage.
````
````{tab-item} Pfizer
**The Focus:** Excited-state molecular calculations — how drug molecules behave when energized, critical for understanding phototoxicity and metabolic pathways. Pfizer entered a research collaboration with IBM Quantum to explore quantum simulation for molecular dynamics in their pipeline.

**The Target:** Reducing late-stage toxicity failures. Approximately 30% of drug candidates that fail in Phase II–III trials fail due to metabolic issues — liver toxicity, off-target binding — that current classical simulation missed in preclinical development. Each late-stage failure costs \$800M–\$1.5B in sunk cost. Avoiding one such failure through better quantum simulation more than pays for any conceivable quantum computing investment.

**Near-Term Contribution:** Pfizer's IBM partnership has generated methodological advances in quantum algorithms for excited-state calculations, contributing to the public scientific literature on quantum chemistry methods.
````
````{tab-item} Menten AI + D-Wave
**The Protein Design Angle:** While most pharmaceutical quantum programs focus on gate-model VQE for molecular simulation, Menten AI represents a different approach: using D-Wave's quantum annealing hardware for protein engineering — the inverse problem of designing proteins with desired properties rather than discovering their natural structure.

**The Connection:** Protein design involves finding optimal amino acid sequences given a target function — a combinatorial optimization problem that maps naturally to QUBO. Menten AI's partnership with D-Wave applies quantum annealing to the sequence optimization step of protein engineering, identifying candidate protein sequences for therapeutic applications faster than classical evolutionary algorithms.

**The Significance:** This is the dual-paradigm pattern in action within a single vertical. Gate-model VQE simulates the quantum chemistry of small molecular fragments. D-Wave annealing optimizes the combinatorial search through protein sequence space. Both paradigms contribute to pharmaceutical discovery — through different mechanisms, at different problem scales, on today's available hardware.
::::
`````

### The NPV Model: Calculating the Value of Better Simulation

The financial case for quantum simulation in pharmaceuticals does not require heroic assumptions. The core model has five inputs and one formula:

| Input | Variable | Typical Range |
|---|---|---|
| Peak annual revenue | R | \$200M – \$5B |
| Years accelerated | ΔT | 1–3 years |
| Discount rate | r | 8–12% |
| Probability of success (adjusted for quantum) | p | Baseline + improvement |
| Investment required | I | \$10M – \$100M |

**NPV ≈ p × R × ΔT / r − I**

For a \$500M peak-revenue drug with a 10% baseline success probability, a quantum simulation investment that raises success probability by 5 percentage points (plausible for improved fragment screening accuracy) and accelerates timeline by 1 year adds approximately **\$500M–\$900M in risk-adjusted NPV** — against an investment cost typically under \$50M. The ratio is not close. The question for pharmaceutical executives is not whether the expected value is positive. The question is whether the hardware matures on the timeline required.

---

## Part IV: Energy and Materials — Civilization-Scale Stakes

### The Problem That Runs on Quantum Physics

The energy and materials industries face molecular problems of a different character than pharmaceuticals. The molecules are smaller. The required accuracy is higher. And the consequences of getting it right — or failing to — are measured not in individual drug approvals but in gigatons of CO₂ and billions of people with access to affordable energy.

Three molecular problems stand at the intersection of quantum computing and the energy transition:

**The nitrogen fixation problem** — how *Azotobacter* bacteria convert atmospheric nitrogen to ammonia at room temperature while the Haber-Bosch industrial process requires 400°C and 200 atmospheres of pressure, consuming 1-2% of global energy and emitting 450 million tons of CO₂ annually. The enzyme responsible — nitrogenase — has an active site (FeMoco) containing approximately 54 strongly correlated electrons. Classical simulation breaks down completely at this complexity. Quantum simulation of FeMoco is a stated target of active programs at IBM, Google, and Microsoft. The required hardware: thousands of logical qubits. The prize: potentially eliminating one of the largest single sources of industrial CO₂.

**The battery materials problem** — designing next-generation solid-state electrolytes for lithium-ion batteries with 2–3x the energy density of current cells. The quantum mechanical behavior of lithium ions at solid electrolyte interfaces determines charging speed, capacity, and cycle lifetime. Classical molecular dynamics simulations introduce 20–30% errors in calculated ion migration rates — enough to make viable materials appear nonviable and vice versa.

**The carbon capture materials problem** — designing metal-organic framework (MOF) sorbents with optimal CO₂ binding properties for post-combustion carbon capture. The binding energy between CO₂ and the MOF surface is governed by electron correlation effects that classical DFT methods disagree on by 20–30%, making computational materials screening unreliable for identifying production-viable sorbents.

:::{figure} ../images/ch07-energy-materials-targets.png
:label: fig-energy-targets
:alt: Three energy transition quantum targets showing nitrogen fixation, battery materials, and carbon capture with hardware requirements and timeline estimates.
:width: 100%
:align: center

**Three Quantum Targets in the Energy Transition.** Each problem has a defined target molecule or material, a known quantum algorithm (VQE for near-term fragments, quantum phase estimation for production-scale simulation), and a hardware requirement. The timeline runs from near-term fragment calculations today to full molecular simulation within 5–10 years on current hardware trajectories.
:::

### Mercedes-Benz: The Range Problem

Mercedes-Benz's quantum battery research — conducted with IBM Quantum — targets a consumer problem: range anxiety. The company has identified solid-state electrolyte interface chemistry as the foundational bottleneck in next-generation EV batteries. Current lithium-ion batteries are approaching their theoretical energy density limits; the next generation requires materials whose quantum mechanical behavior at electrode-electrolyte interfaces cannot be accurately modeled classically.

The specific target: lithium ion migration rates across solid electrolyte interfaces, a process governed by quantum tunneling that classical molecular dynamics approximates poorly with 20–30% error. An accurate quantum simulation of small interface fragments — tractable with near-term hardware using VQE — could narrow this error to a few percent, significantly accelerating the selection of viable electrolyte chemistries and shortening the path to batteries with 2–3x the range of current vehicles.

### ExxonMobil: Catalysts and Carbon

ExxonMobil's quantum computing research spans two verticals: MOF carbon capture sorbent design and LNG shipping logistics (covered in Part II). On the materials science side, their IBM Quantum partnership explores VQE calculations on small MOF fragments — establishing baseline quantum accuracy and developing the workflow for systematic MOF screening.

The longer-term goal: a quantum-assisted materials discovery pipeline that reduces experimental synthesis screening from thousands of materials to dozens, by filtering candidates computationally before any laboratory synthesis is required. The quantum calculation that would enable this — accurate simulation of CO₂ binding energetics on MOF surfaces — requires approximately 50 logical qubits with low error rates. Current hardware trajectories suggest this capability within 3–5 years.

### The FeMoco Problem: The Longest Bet

Quantum simulation of nitrogenase's FeMoco active site represents the intersection of the most computationally ambitious quantum chemistry target and the most consequential potential outcome. FeMoco — iron-molybdenum cofactor — contains iron, molybdenum, sulfur, and carbon atoms whose electronic structure involves approximately 54 strongly correlated electrons in a complex spin state. Full configuration interaction calculation of FeMoco on classical hardware would require more memory than exists on Earth.

Quantum simulation of FeMoco using quantum phase estimation — the algorithm required for fault-tolerant simulation accuracy — is estimated to require 4,000–10,000 logical qubits with millisecond coherence times. That is hardware that does not yet exist. The research programs at IBM, Google, and Microsoft tracking toward this target are not betting on a 2025 outcome. They are building the algorithmic and hardware infrastructure that makes a 2032–2035 outcome plausible.

The prize: understanding how nitrogenase fixes nitrogen could enable the design of synthetic catalysts that replicate the process at industrial scale — eliminating 1–2% of global energy consumption and hundreds of millions of tons of annual CO₂ from the Haber-Bosch process. No other single quantum computing application has this potential impact on the energy transition.

### ESG Implications: The Board-Level Conversation

Energy and materials quantum applications intersect with corporate ESG strategy in ways that are increasingly material to boards and investors. Organizations investing in quantum computing for materials discovery — battery chemistry, carbon capture, green hydrogen production — can legitimately frame those investments as ESG-aligned R&D.

The framing matters for three reasons. First, quantum materials research investments may qualify for R&D tax incentives and green technology funding programs in multiple jurisdictions. Second, demonstrated quantum capabilities in climate technology attract partnership interest from sovereign wealth funds, development finance institutions, and corporate partners with explicit decarbonization mandates. Third, the board conversation about quantum risk and readiness (Chapter 9) is more tractable when quantum investment can be connected to existing ESG commitments rather than requiring a standalone technology budget justification.

---

## Part V: Manufacturing — Scheduling, Quality, and the Factory of the Future

Manufacturing sits at a distinctive intersection in the quantum landscape. Its most valuable quantum applications are not molecular simulation or financial risk modeling — they are combinatorial optimization problems: scheduling thousands of machines and workers across a production floor, routing parts through a complex factory network, allocating capacity across multi-plant systems under changing demand and supply constraints. These are problems the D-Wave paradigm addresses today, in production, at scale. Manufacturing is where the annealing lane of this course is most commercially mature.

:::{figure} ../images/ch07-manufacturing-quantum-map.png
:label: fig-manufacturing-map
:alt: Manufacturing quantum opportunity map showing production scheduling, quality control optimization, predictive maintenance, and supply chain resilience with readiness levels and leading enterprise cases.
:width: 100%
:align: center

**The Manufacturing Quantum Opportunity Map.** Production scheduling and factory routing are the most near-term accessible applications — QUBO-formulated and D-Wave-ready today, as BASF's deployment demonstrates. Quality control optimization and predictive maintenance sit in the hybrid zone. Digital twin simulation for process optimization is the longer-horizon gate-model play.
:::

### Production Scheduling: The Problem That Defines Manufacturing Efficiency

Every manufacturing operation faces a version of the same problem: given a set of machines, a set of jobs, a set of workers, a set of constraints (due dates, machine capabilities, setup times, maintenance windows), and a set of objectives (minimize makespan, maximize throughput, minimize energy consumption) — what is the optimal schedule?

Classical scheduling algorithms — including the best academic operations research methods — find good schedules. For real manufacturing systems with hundreds of machines, thousands of jobs, and dozens of constraint types, they cannot guarantee optimality. The combinatorial space is simply too large for exhaustive search, and classical heuristics explore only a local neighborhood around their starting point.

The QUBO formulation of production scheduling maps directly to D-Wave's annealing hardware. Binary variables represent job-machine-time-slot assignments; quadratic terms encode conflict constraints (one machine, one job at a time); objective terms encode the makespan or throughput goal. The same Ocean SDK pipeline used in Chapter 6 and Lab 7B applies here, with manufacturing-specific problem structure.

**BASF: The Most Documented Manufacturing Quantum Deployment**

BASF's production scheduling deployment — introduced in Chapter 6 as the flagship optimization case study — is worth revisiting through the manufacturing vertical lens. BASF operates chemical production facilities where scheduling decisions involve simultaneous optimization of reactor assignments, feedstock logistics, cleaning cycles, and delivery commitments. The classical scheduling system found feasible schedules consistently; optimal schedules rarely.

D-Wave's Stride hybrid solver, applied to a reformulated QUBO of BASF's scheduling problem, reduced production scheduling computation time from hours to seconds — not as a benchmark exercise but as a production deployment. The operational implication: schedulers could run what-if scenarios (a reactor goes offline, a customer requests an urgent order change) in real time, rather than waiting hours for the classical optimizer to rerun. The competitive implication: BASF's ability to respond to supply chain disruptions faster than classical-scheduler competitors is a direct operational advantage generated by quantum optimization.

### Quality Control and Defect Optimization

Manufacturing quality control involves decisions that are fundamentally combinatorial: which sensor readings to monitor, which inspection stations to staff, which defect patterns require immediate line stoppage vs. statistical process control adjustment. At scale — high-speed production lines generating thousands of data points per second — the real-time optimization of these decisions exceeds what rule-based classical systems handle efficiently.

**Volkswagen's Digital Annealer Bridge** — documented in Part II of this chapter — established a QUBO formulation for manufacturing that VW subsequently applied to factory floor routing at their Wolfsburg and Zwickau plants. The quantum-inspired classical solver that VW deployed delivered 3–8% efficiency improvements in parts logistics routing and 2–5% gains in factory scheduling throughput. This is the "quantum-inspired bridge" in manufacturing: the QUBO mathematical structure, developed in a quantum pilot, delivers production value on classical hardware while quantum hardware scales.

### Airbus: Aerospace Manufacturing Optimization

Airbus's quantum computing program — conducted in partnership with both IBM Quantum and D-Wave — targets two distinct manufacturing problems. For aircraft assembly scheduling (a gate-model QAOA application), Airbus has explored quantum-assisted optimization of assembly line sequencing where the constraint complexity — safety certifications, regulatory inspection windows, component delivery dependencies — creates a combinatorial problem that classical scheduling tools handle only approximately.

For supply chain and parts routing optimization (a D-Wave annealing application), Airbus has run QUBO formulations of their component logistics problem, where thousands of parts must be routed from hundreds of suppliers through assembly stations with just-in-time delivery constraints. The dual-paradigm pattern appears again: assembly sequencing maps better to gate-model QAOA (medium-term); parts routing maps better to D-Wave annealing (accessible today).

### The Manufacturing Quantum Readiness Timeline

::::{grid} 3

:::{card} 🟢 Now — Accessible Today
**Production scheduling as QUBO** via D-Wave Stride (BASF model, directly deployable)

**Factory routing optimization** via D-Wave hybrid (Volkswagen QUBO bridge pattern)

**Parts logistics optimization** via quantum-inspired classical solvers (Digital Annealer)
:::

:::{card} 🟡 Near-Term (2026–2029)
**Real-time quality control optimization** integrating sensor streams with hybrid quantum-classical decision engines

**Assembly line sequencing** via QAOA on early fault-tolerant hardware for high-constraint aerospace and automotive applications

**Predictive maintenance scheduling** via quantum ML for anomaly detection in complex multi-machine environments
:::

:::{card} 🔵 Long-Horizon (2030+)
**Materials discovery for manufacturing** — quantum simulation of advanced alloys, composites, and industrial catalysts via VQE

**Full digital twin optimization** — quantum-native simulation of manufacturing processes at molecular-to-system scale

**End-to-end supply chain quantum optimization** at full network complexity
:::

::::

---

## Productive-Struggle Problem

::::{admonition} The Challenge: Choose Your Vertical
:class: tip

You are the Chief Strategy Officer of a \$5 billion company. Your board has asked you to present a one-page "quantum opportunity assessment" for your industry vertical. Choose any of the four verticals in this chapter — or your own industry if it is not represented.

**Your deliverable:**

1. **The problem.** Identify one specific computational problem in your vertical that maps to a quantum technique (optimization for D-Wave, simulation for VQE, or a combination). Be specific — not "supply chain optimization" but "last-mile delivery routing for 300 vehicles serving 4,500 daily stops in Southeast Asia."

2. **The technique.** Identify which quantum approach (QUBO/annealing, VQE, hybrid) addresses your problem and why. Cite the chapter sections and enterprise cases that support your choice.

3. **The business case.** Quantify the value of improvement. Apply the NPV model (for pharma) or estimate cost savings (for logistics/finance). Show your math. Make your assumptions explicit.

4. **The timeline.** Map your problem to the hardware era it requires — NISQ today, early fault-tolerant (2027–2029), or full fault-tolerant (2030+). Is there a "quantum-inspired bridge" available that delivers value before the hardware matures?

5. **The recommendation.** What should your company do in the next 12 months? Do not recommend "monitor the situation." Recommend a specific action with a specific budget and a specific deliverable.

**The constraint:** 300 words. If you cannot make the case in 300 words, you cannot make it to a board.
::::

---

## Module-Level Outcomes

::::{card-carousel} 1

:::{card} Outcome 1
**Map quantum techniques to industry verticals.**
Accurately identify which quantum approach — D-Wave annealing for optimization, VQE for molecular simulation, hybrid quantum-classical — is most appropriate for a given business problem in financial services, supply chain, healthcare, or energy.
:::

:::{card} Outcome 2
**Evaluate enterprise quantum deployments critically.**
Distinguish between what has been announced, what has been published, and what has been commercially deployed in each vertical — applying the framework to assess the maturity and credibility of specific quantum-industry programs.
:::

:::{card} Outcome 3
**Construct an R&D acceleration NPV model.**
Build and defend an R&D acceleration NPV model for a pharmaceutical or materials science quantum application, with explicit assumptions about success probability improvement, timeline acceleration, peak revenue, and discount rate.
:::

:::{card} Outcome 4
**Apply QUBO formulation to a supply chain problem.**
Formulate a vehicle routing or inventory optimization problem as a QUBO, submit it to D-Wave Leap, and interpret the results against a classical baseline — demonstrating that optimization-heavy supply chain applications are accessible today.
:::

:::{card} Outcome 5
**Run a VQE simulation on a real quantum device.**
Execute a VQE calculation for the hydrogen molecule on IBM Quantum hardware, observe convergence, and connect the result to the molecular simulation problem in drug discovery or materials research.
:::

:::{card} Outcome 6
**Identify the quantum-inspired bridge for your vertical.**
For any given industry application, identify whether a quantum-inspired classical algorithm provides near-term value before quantum hardware scales — and articulate the difference between the bridge value and the eventual full quantum advantage.
:::

::::

---

## Lab 7A (Regular): Simulating the Hydrogen Molecule with VQE

**Duration:** ~60 minutes
**Tools:** IBM Quantum (cloud account — free tier), Qiskit
**Platform:** [Google Colab](https://colab.research.google.com) — no local install required

<a href="https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch07-vqe-h2-simulation.ipynb" target="_blank">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="margin-bottom: 1rem;"/>
</a>

### Why This Lab

The same quantum physics that makes electron simulation hard for classical computers makes it natural for quantum computers. VQE — the Variational Quantum Eigensolver — is the algorithm that bridges today's noisy hardware and tomorrow's molecular drug discovery. This lab runs a real VQE calculation on the simplest molecule in chemistry: hydrogen (H₂). You will see the algorithm converge in real time, plot the energy curve that is the foundational tool of computational chemistry, and connect what you observe directly to the pharmaceutical applications in Part III.

### The Molecule and What You're Measuring

Hydrogen is two protons and two electrons. Small enough to simulate on a 2-qubit quantum circuit. Large enough to exhibit the electron correlation effects — the quantum entanglement between electrons — that classical Hartree-Fock misses and VQE captures.

The quantity you are calculating: the **ground-state energy** of H₂ as a function of the distance between the two hydrogen atoms. Plot energy vs. bond distance, and you get the **potential energy surface** — the foundational tool that tells computational chemists which molecular configurations are stable, what reaction barriers look like, and how a drug molecule binds to a protein.

### Instructions

```python
from qiskit_nature.second_q.drivers import PySCFDriver
from qiskit_nature.second_q.mappers import JordanWignerMapper
from qiskit_nature.second_q.algorithms import GroundStateEigensolver
from qiskit_algorithms import VQE
from qiskit_algorithms.optimizers import COBYLA
from qiskit.circuit.library import TwoLocal
from qiskit.primitives import Estimator
import numpy as np
import matplotlib.pyplot as plt

# Bond distance sweep: from compressed (0.3 Å) to stretched (3.0 Å)
distances = np.linspace(0.3, 3.0, 20)
vqe_energies = []

for d in distances:
    # Define H2 at this bond distance
    driver = PySCFDriver(atom=f"H .0 .0 .0; H .0 .0 {d}", basis="sto3g")
    problem = driver.run()
    
    # Map to qubit Hamiltonian via Jordan-Wigner transformation
    mapper = JordanWignerMapper()
    qubit_op = mapper.map(problem.second_q_ops()[0])
    
    # VQE ansatz and optimizer
    ansatz = TwoLocal(qubit_op.num_qubits, ['ry', 'rz'], 'cx', reps=2)
    vqe = VQE(estimator=Estimator(), ansatz=ansatz, optimizer=COBYLA(maxiter=500))
    
    # Solve
    solver = GroundStateEigensolver(mapper, vqe)
    result = solver.solve(problem)
    vqe_energies.append(result.total_energies[0].real)

# Plot the potential energy surface
plt.figure(figsize=(10, 6))
plt.plot(distances, vqe_energies, 'b-o', label='VQE (Quantum)')
plt.xlabel('Bond Distance (Å)')
plt.ylabel('Energy (Hartree)')
plt.title('H₂ Potential Energy Surface: VQE on Quantum Hardware')
plt.axvline(x=0.735, color='red', linestyle='--', label='Equilibrium bond length (0.735 Å)')
plt.legend()
plt.show()
print(f"Minimum energy: {min(vqe_energies):.6f} Hartree at {distances[vqe_energies.index(min(vqe_energies))]:.3f} Å")
```

### What to Look For

- The minimum of your energy curve should appear near 0.735 Å — the known equilibrium bond length of H₂
- The minimum energy should be approximately −1.137 Hartree — the known ground-state energy
- Observe the convergence: at each bond distance, VQE iterates from a random starting point toward the minimum. The number of iterations required varies with the landscape complexity

### Deliverable

Write a **400-word memo** titled "What This Simulation Means for Drug Discovery":
1. What the energy curve represents in molecular terms and why it matters for predicting molecular properties
2. Why electron correlation — the quantum entanglement between the two electrons — makes H₂ an interesting test case for a quantum computer
3. How this same approach, scaled to 50-electron drug-relevant molecules, would change the early discovery process at a pharmaceutical company
4. One hardware limitation you observed (noise, convergence variability, or circuit depth) and what hardware improvement would address it

---

## Lab 7B (Applied): D-Wave for Industry Vertical Optimization

**Duration:** 60–75 minutes
**Tools:** D-Wave Leap — [cloud.dwavesys.com](https://cloud.dwavesys.com) (free developer account)
**Deliverable:** QUBO results + 300-word strategic memo

<a href="https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch07-lab-industry-qubo.ipynb" target="_blank">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="margin-bottom: 1rem;"/>
</a>

### Why This Lab

Parts I and II of this chapter covered financial services and supply chain optimization — both D-Wave territory. This lab takes the QUBO skills from Chapter 6 and applies them to a new domain: multi-site inventory allocation across a supply chain. The problem is structurally similar to the scheduling problems in Chapter 6 but involves the tradeoff logic specific to supply chain operations — distribution center capacity, service level constraints, and holding cost optimization.

This is the D-Wave application that connects directly to the DHL and ExxonMobil cases in Part II. You are running the same type of solver they are using — the same FAU Advantage2 class of hardware, accessible through Leap.

### The Problem: Inventory Allocation Across 3 Distribution Centers

You are the head of supply chain optimization at a regional retailer. You have 6 high-demand SKUs that need to be allocated across 3 distribution centers (DCs) for the upcoming peak season. Each DC has limited capacity. Each SKU has a different demand profile and holding cost. Your goal: allocate SKUs to DCs to maximize service level coverage while staying within capacity constraints.

| SKU | Demand Score | Holding Cost/wk | Units |
|---|---|---|---|
| A (Electronics) | 9 | \$120 | 200 |
| B (Apparel) | 6 | \$40 | 350 |
| C (Home Goods) | 7 | \$60 | 280 |
| D (Sporting) | 5 | \$35 | 400 |
| E (Seasonal) | 8 | \$90 | 150 |
| F (Grocery) | 4 | \$15 | 500 |

| DC | Capacity (units) | Coverage Region |
|---|---|---|
| DC-East | 600 | NY, NJ, CT, MA |
| DC-Central | 700 | OH, IN, IL, MI |
| DC-West | 500 | CA, OR, WA, NV |

### Step 1: Formulate the QUBO

```python
import dimod
from dwave.system import LeapHybridSampler

# Binary variable x_{i,j} = 1 if SKU i is primarily stocked at DC j
skus = {'A': {'demand': 9, 'cost': 120, 'units': 200},
        'B': {'demand': 6, 'cost': 40,  'units': 350},
        'C': {'demand': 7, 'cost': 60,  'units': 280},
        'D': {'demand': 5, 'cost': 35,  'units': 400},
        'E': {'demand': 8, 'cost': 90,  'units': 150},
        'F': {'demand': 4, 'cost': 15,  'units': 500}}

dcs = {'East': 600, 'Central': 700, 'West': 500}

Q = {}
lambda_assign = 15   # penalty: each SKU must be assigned to exactly one DC
lambda_cap = 20      # penalty: DC capacity must not be exceeded

variables = [(sku, dc) for sku in skus for dc in dcs]

# Objective: maximize demand coverage, minimize holding cost
# (minimize negative value: high-demand, low-cost SKUs get priority)
for (sku, dc) in variables:
    score = -(skus[sku]['demand'] * 2 - skus[sku]['cost'] / 50)
    Q[((sku, dc), (sku, dc))] = Q.get(((sku, dc), (sku, dc)), 0) + score

# Constraint: each SKU assigned to exactly one DC
for sku in skus:
    sku_vars = [(sku, dc) for dc in dcs]
    for i, vi in enumerate(sku_vars):
        Q[(vi, vi)] = Q.get((vi, vi), 0) + lambda_assign * (1 - 2)
        for vj in sku_vars[i+1:]:
            Q[(vi, vj)] = Q.get((vi, vj), 0) + 2 * lambda_assign

# Constraint: DC capacity not exceeded
for dc, capacity in dcs.items():
    dc_vars = [(sku, dc) for sku in skus]
    dc_units = [skus[s]['units'] for s in skus]
    for i, vi in enumerate(dc_vars):
        Q[(vi, vi)] = Q.get((vi, vi), 0) + lambda_cap * dc_units[i] * (dc_units[i] - 2 * capacity)
        for j, vj in enumerate(dc_vars):
            if j > i:
                Q[(vi, vj)] = Q.get((vi, vj), 0) + 2 * lambda_cap * dc_units[i] * dc_units[j]

# Submit to D-Wave Leap
sampler = LeapHybridSampler()
sampleset = sampler.sample_qubo(Q, label='Supply Chain Inventory Allocation', time_limit=10)

# Interpret results
best = sampleset.first
allocation = {var: val for var, val in best.sample.items() if val == 1}
print("Optimal Inventory Allocation:")
for (sku, dc), assigned in allocation.items():
    print(f"  SKU {sku} → {dc} DC  (demand: {skus[sku]['demand']}, cost: ${skus[sku]['cost']}/wk)")
print(f"\nEnergy: {best.energy:.2f}")
print(f"QPU timing: {sampleset.info.get('timing', {})}")
```

### Step 2: Verify and Experiment

- Check: is each SKU assigned to exactly one DC?
- Check: does each DC's total units stay within capacity?
- Experiment: add a constraint that SKU E (Seasonal) must be in DC-West. How does the allocation change?
- Experiment: reduce DC-Central's capacity to 400 units. Which SKU gets reallocated and why?

### Deliverable

Write a **300-word strategic memo** to your VP of Supply Chain:
1. What allocation did the solver produce, and is it intuitively reasonable?
2. What tradeoffs did the solver navigate (high demand SKUs vs. capacity constraints)?
3. How does this approach scale to a real supply chain with 500 SKUs and 20 DCs — and what would need to change in the formulation?

---

## Lab 7C (Optional Advanced): LiH and the Limits of Today's Hardware

**Duration:** ~90 minutes
**Tools:** Python 3, Qiskit, Qiskit Nature

<a href="https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch07-vqe-lih-advanced.ipynb" target="_blank">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="margin-bottom: 1rem;"/>
</a>

### Why This Lab

H₂ is two electrons. LiH is four. Drug-relevant molecules have 50–200. This lab extends the VQE approach to lithium hydride, revealing exactly where today's hardware creates limits — and what hardware improvement would be required to cross into pharmaceutical relevance.

### Core Steps

1. **Define LiH geometry** using Qiskit Nature's PySCF driver
2. **Compare two ansatz choices:** UCCSD (chemistry-motivated, high accuracy, deep circuit) vs. hardware-efficient (shallower circuit, more noise-tolerant)
3. **Benchmark against classical Hartree-Fock** — which method produces the lower energy? What does that tell you?
4. **Attempt water (H₂O) simulation** — document where the state vector simulation of the quantum circuit exhausts RAM. This is the computational wall that quantum hardware must cross

### Deliverable

600-word analysis: "What hardware improvement — in qubit count, error rate, or circuit depth — would extend VQE from LiH to a 50-atom drug-like molecule? Use specific numbers from the hardware roadmaps in Chapter 4."

---

## Discussion Guidelines

**Post a substantive response (minimum 300 words) citing at least two sources. Reply meaningfully to TWO peers.**

### Discussion Prompt

Apply the vertical framework from this chapter to your own organization (or a publicly traded company of your choice).

1. **Identify the quantum-suited problem.** Based on the industry vertical mapping, what is the one specific computational problem in your organization that is most likely to be addressed by quantum computing — optimization (D-Wave), simulation (VQE), or hybrid?

2. **Map it to a technique.** Explain why your chosen problem maps to that quantum approach — using the logic from the chapter sections, not just naming the technique.

3. **Time it.** Is your problem solvable with NISQ hardware today, or does it require early fault-tolerant or full fault-tolerant hardware? What is the implication for investment timing?

4. **Bridge it.** Is there a quantum-inspired classical approach (like Volkswagen's Digital Annealer pivot) that delivers value while quantum hardware matures?

**Peer response guidelines:** Challenge the hardware timing assumption — is your peer's problem actually accessible sooner (or later) than they estimate? Extend their business case with a financial estimate they did not include.

---

## Glossary

```{glossary}
VQE (Variational Quantum Eigensolver)
  A hybrid classical-quantum algorithm for finding the ground-state energy of a molecular system. Used in pharmaceutical drug discovery and materials science to compute molecular properties more accurately than classical approximation methods.

Variational Principle
  A theorem from quantum mechanics stating that any trial quantum state has energy equal to or greater than the true ground-state energy. The foundation of VQE: minimizing energy over trial states converges to the exact ground state.

Ground State
  The lowest-energy quantum state of a molecule. The ground-state energy determines all chemical properties — bond strength, reaction rates, binding affinity, and drug-protein interaction geometry.

Ansatz
  A parameterized quantum circuit used in VQE to prepare trial quantum states. Common choices: UCCSD (physically motivated, high accuracy, deep circuit) and hardware-efficient (shallower, more noise-tolerant).

Jordan-Wigner Transformation
  A mathematical mapping from a molecular electronic Hamiltonian (describing electrons) to a qubit Hamiltonian that a quantum computer can process.

Electron Correlation
  The quantum mechanical interaction between electrons that classical mean-field methods (Hartree-Fock, DFT) approximate. Electron correlation governs binding affinity, reaction barriers, and drug-protein interaction strength — the specific properties that classical simulation gets wrong.

DFT (Density Functional Theory)
  The workhorse classical computational chemistry method — efficient but approximate, especially for strongly correlated electron systems relevant to drug-protein binding and materials science.

Potential Energy Surface
  A map of molecular energy as a function of atomic configuration. The foundational output of molecular simulation: its minimum identifies equilibrium geometries, its shape determines reaction pathways, its accuracy determines the reliability of drug design predictions.

FeMoco (Iron-Molybdenum Cofactor)
  The active site of the nitrogenase enzyme, containing approximately 54 strongly correlated electrons. The canonical hard target for quantum simulation — its accurate modeling would enable design of room-temperature nitrogen fixation catalysts.

Nitrogenase
  The enzyme used by nitrogen-fixing bacteria to convert atmospheric nitrogen to ammonia at room temperature. Its industrial equivalent — the Haber-Bosch process — consumes 1–2% of global energy and emits ~450 million tons of CO₂ annually.

MOF (Metal-Organic Framework)
  A class of porous crystalline materials with high internal surface area used for carbon capture, gas storage, and catalysis. MOF CO₂ binding energetics are governed by electron correlation effects that classical DFT calculates with 20–30% error.

QUBO (Quadratic Unconstrained Binary Optimization)
  The mathematical formulation language for D-Wave quantum annealers. Expresses optimization problems — portfolio construction, supply chain routing, inventory allocation — as minimization of a quadratic function of binary variables.

Quantum-Inspired Algorithms
  Classical algorithms that apply mathematical structures derived from quantum mechanics. Deliver near-term optimization value on conventional hardware while quantum hardware matures — the "bridge" strategy demonstrated by Volkswagen's Digital Annealer deployment.

Vehicle Routing Problem (VRP)
  The combinatorial optimization problem of assigning routes to a fleet of vehicles to minimize total distance or cost subject to vehicle capacity, time window, and depot constraints. A canonical D-Wave application in supply chain and logistics.
```

---

## Leader's Takeaway

::::{admonition} The Leader's Takeaway
:class: important

Four industries. Two quantum paradigms. One strategic insight.

Financial services and supply chain are the near-term commercial frontier. The problems — portfolio optimization, vehicle routing, inventory allocation, fraud detection — are combinatorial optimization problems that map directly to QUBO and D-Wave annealing. The hardware is deployed today. The case studies are not pilots. BASF's manufacturing scheduler, Mastercard's fraud detection, Verge Ag's autonomous fleet routing — these are production deployments. The organizations waiting for quantum computing to "prove itself" in these verticals are waiting for something that already happened.

Healthcare and pharma represent the highest long-term NPV of any quantum application. The molecular simulation problem — drug binding affinity, protein folding, enzyme active site chemistry — is the problem quantum computers were literally invented to solve. VQE is the bridge algorithm that delivers value on today's NISQ hardware for small molecular fragments. The fault-tolerant hardware required for drug-sized molecules is 5–8 years out on current roadmaps. The pharmaceutical companies building quantum chemistry expertise today will have 5-8 years of head start when that hardware arrives. The ones that wait will be licensing technology from the ones that invested.

Energy and materials hold civilization-scale stakes. Quantum simulation of nitrogen fixation chemistry — one enzyme's active site — could eliminate 1–2% of global energy consumption. Battery interface simulation could unlock 2–3x range improvements for electric vehicles. Carbon capture materials discovery could accelerate the deployment of post-combustion capture at industrial scale. These outcomes are not certain. They are plausible — and plausible at this scale is worth enormous investment.

The dual-paradigm lens is the leader's practical tool for this chapter. Ask two questions of every quantum business case you encounter: Is this an optimization problem? Then it maps to D-Wave annealing, QUBO formulation, and the approach available today. Is this a simulation problem? Then it maps to VQE and gate-model hardware, with near-term value for molecular fragments and full value 5–8 years out. Most quantum vendor pitches do not distinguish. Most boards do not know to ask. Now you do.
::::

---

## Cross-References

- **See {ref}`ch-03-bits-to-qubits-economics`** for the QaaS ecosystem comparison — which cloud platforms serve which vertical applications.
- **See {ref}`ch-06-optimization-goldmine`** for the QUBO formulation skills and D-Wave Ocean SDK used in Lab 7B — the foundation of financial services and supply chain quantum optimization.
- **See {ref}`ch-08-quantum-ai-hybrid`** for quantum machine learning applications in financial services (quantum kernels for credit scoring) and supply chain (demand forecasting) that complement the optimization approaches in this chapter.
- **See {ref}`ch-09-quantum-ready-enterprise`** for the enterprise readiness framework that translates the vertical applications in this chapter into organizational strategy, talent architecture, and investment thesis.
