---
title: "Chapter 8: Quantum + AI — The Hybrid Frontier"
subtitle: "Most Quantum AI Is Hype. The Rest Is Worth Watching Carefully — and One Piece Is Worth Using Right Now."
short_title: "Ch. 8: Quantum + AI"
description: "The intersection of quantum computing and AI is simultaneously overhyped and underexplored. This chapter separates genuine hybrid opportunity from marketing noise — introducing quantum kernels, variational circuits, dequantization, and quantum-enhanced predictive analytics for supply chain and operations. It includes D-Wave Lab 8B, which applies quantum annealing to ML feature selection and ensemble optimization using the same hardware available through FAU's Advantage2 system."
label: ch-08-quantum-ai-hybrid
tags: [quantum machine learning, QML, quantum kernels, dequantization, variational circuits, QAOA, VQE, quantum-inspired, supply chain analytics, D-Wave, QBOOST, annealing, FAU Advantage2, Ocean SDK, governance, AI governance]
---

# Chapter 8: Quantum + AI — The Hybrid Frontier

:::{figure} ../images/ch08-explainer-infographic.png
:label: fig-ch08-explainer
:alt: Chapter 8 explainer infographic showing the spectrum from classical ML through quantum-inspired algorithms and NISQ hybrid QML to full quantum ML, with the D-Wave annealing lane running in parallel for ML optimization tasks.
:width: 100%
:align: center

**The Hybrid Frontier at a Glance.** The spectrum runs from classical ML (production-ready today) through quantum-inspired algorithms and NISQ hybrid QML to full quantum ML (years away). Running alongside the gate-model lane is a separate lane that often gets missed in quantum AI conversations: D-Wave quantum annealing applied to ML optimization tasks — feature selection, ensemble optimization, hyperparameter search. That lane is open today. This chapter covers both.
:::

The previous chapters gave you the two quantum paradigms and their primary applications. Chapter 6 was D-Wave's home territory — optimization. Chapter 7 was the industry verticals where both paradigms generate value. This chapter is where quantum meets the discipline that has absorbed the most enterprise investment over the past decade: artificial intelligence.

The quantum AI conversation is louder than it should be and more substantive than the skeptics admit. Both things are true simultaneously. The loudness comes from vendors attaching "quantum" to classical ML pipelines and calling it innovation. The substance comes from specific, peer-reviewed results in quantum kernel theory, variational hybrid algorithms, and — most immediately actionable — quantum annealing applied to ML optimization problems that businesses are running today.

This chapter teaches you to distinguish between these, to evaluate vendor claims with precision, and to understand which quantum AI applications you can act on now. The governance framework here is not academic. When a vendor charges a premium for "quantum-enhanced AI" and the quantum component is a random number generator, you need to be able to identify that in a 90-minute pitch meeting. This chapter gives you that capability.

---

## Opening Scene: The Panel No One Won

The conference ballroom holds 800 people. The stage holds five panelists: a quantum computing startup CEO, a hyperscaler AI research director, a hedge fund quant, a skeptical academic, and a venture capitalist who has written checks to two of the other four. The moderator opens with the question everyone paid \$3,000 in registration fees to hear answered:

*"Will quantum computers transform artificial intelligence?"*

The CEO says yes, obviously, and the press release is already in your inbox. The AI director says "we're watching closely," which means no, but politely. The quant says the question is wrong — what matters is which specific ML subroutines quantum can accelerate, by how much, and at what error rate. The academic says two recent papers claiming quantum advantage were quietly withdrawn from arXiv after classical baselines were found. The VC says she is betting on the talent, not the timeline.

Nobody wins. Nobody loses. The audience files out in three factions: convinced, confused, and quietly Googling "dequantization."

This chapter is for the third faction.

---

## The Single Idea

```{epigraph}
The intersection of quantum computing and AI is simultaneously overhyped and underexplored. Most of what is sold as quantum AI today is classical ML with quantum marketing. But the genuine opportunities — quantum annealing for ML optimization available today, quantum kernels for high-dimensional classification in the near term, and quantum-native ML algorithms when fault-tolerant hardware arrives — are real, grounded in peer-reviewed theory, and early enough that organizations building competency now will have a meaningful head start. The skill this chapter develops is evaluation: how to tell the difference between quantum marketing and quantum value, and how to act on the latter.
```

---

## Part I: The QML Landscape — What Is Real and What Is Not

### Two Paradigms, Two Roles in the AI Story

As in every chapter of this course, the dual-paradigm distinction matters here — and in the quantum AI conversation, it is almost never made clearly. Gate-model quantum computers (IBM, Google, IonQ) are the platform for quantum kernel methods, variational quantum neural networks, and the long-horizon fault-tolerant QML algorithms. D-Wave's quantum annealer — FAU's Advantage2 — is the platform for quantum optimization applied to ML tasks: feature selection, ensemble weight optimization, hyperparameter combinatorial search.

These are different applications of different machines. Conflating them is a source of enormous confusion in vendor pitches, research papers, and executive briefings.

In this chapter, the gate-model lane covers quantum kernels, variational circuits, quantum sampling, and dequantization — the theoretical and near-term experimental QML story. The annealing lane covers quantum-enhanced ML optimization — the D-Wave application that is accessible today and forms the subject of Lab 8B. Both lanes are real. Neither is a universal solution. Understanding which one applies to which business problem is the chapter's core governance skill.

:::{figure} ../images/ch08-two-paradigms-ai.png
:label: fig-ch08-paradigms
:alt: Two quantum paradigm lanes in the AI context — gate-model for quantum kernels and variational QML, D-Wave annealing for ML optimization tasks — with timeline and readiness level for each.
:width: 100%
:align: center

**Two Paradigms in the AI Story.** The gate-model lane (quantum kernels, variational QML) is the theoretical frontier — real results exist but production readiness is 3–7 years away for most applications. The annealing lane (quantum-enhanced feature selection, ensemble optimization, hyperparameter search via QUBO) is accessible today through D-Wave Leap and FAU's Advantage2.
:::

### What Quantum Machine Learning Is — and What It Isn't

::::{prf:definition} Quantum Machine Learning (QML)
:label: def-qml

**Quantum Machine Learning** is the application of quantum computing to machine learning tasks — running ML algorithms on quantum hardware, using quantum circuits as trainable models, or leveraging quantum effects (superposition, entanglement, interference) to accelerate specific ML subroutines. It is distinct from:
- **Quantum-inspired ML:** Classical algorithms that apply mathematical structures from quantum mechanics but run entirely on classical hardware
- **AI for quantum:** Classical ML used to improve quantum hardware calibration, error correction, or circuit design
- **Quantum-optimization-enhanced ML:** D-Wave annealing applied to ML combinatorial optimization tasks (feature selection, ensemble construction)
::::

The QML hype problem has a precise anatomy. Recognize it in four steps.

**Step 1:** A researcher publishes a quantum algorithm that is theoretically faster than classical algorithms for some ML task. The proof is valid. The speedup is real — under specific assumptions about input data, error rates, and problem structure.

**Step 2:** A startup reads the speedup claim and misses the assumptions. The press release announces: "Quantum computers are X times faster at machine learning."

**Step 3:** The benchmark uses a toy dataset, a quantum simulator (not hardware), compared against a classical algorithm that was not tuned.

**Step 4:** Eighteen months later, someone publishes a classical algorithm that matches the speedup, the original assumptions turn out to exclude every real-world dataset, or a dequantization result invalidates the theoretical foundation.

This cycle has repeated approximately a dozen times in the QML literature since 2017. The governance skill is recognizing it before step 4.

::::{admonition} The Baseline Rule
:class: warning

Any QML benchmark that does not include a comparison against a well-tuned, state-of-the-art classical algorithm is not a benchmark. It is a demonstration. Treat it accordingly. The single most impactful question in any quantum AI vendor meeting: "What is your optimized classical baseline, and who tuned it?"
::::

---

## Part II: The Gate-Model QML Toolkit

### Variational Quantum Circuits: The NISQ Bridge

Before quantum computers are fault-tolerant enough to run the full theoretical algorithms that produce provable speedups, they contribute through **variational hybrid algorithms** — the architecture that underpins almost everything genuinely useful in gate-model QML today.

A **Parameterized Quantum Circuit (PQC)** works like a quantum neural network: a sequence of adjustable quantum gates whose rotation angles are trained by a classical optimizer. You run the circuit, measure the output, compute a loss function, and use gradient descent to update the gate angles. The loop repeats until convergence. The quantum layer provides expressive power in a high-dimensional Hilbert space; the classical optimizer does what classical computers do well.

::::{prf:definition} Variational Quantum Circuit (PQC)
:label: def-pqc

A **Parameterized Quantum Circuit** is a quantum circuit with trainable parameters — rotation angles of quantum gates — optimized by a classical optimizer to minimize a loss function. The foundation of VQE (Chapter 7), QAOA (Chapters 6 and 7), and quantum neural networks. The NISQ era's most versatile tool for extracting value from noisy quantum hardware.
::::

The critical challenge: **barren plateaus.** For randomly initialized PQCs with many qubits, the gradient of the loss function vanishes exponentially with circuit depth — the classical optimizer receives essentially zero training signal. Training deep quantum neural networks is a known open problem, not a minor limitation.

The practical takeaway for leaders: variational QML on current hardware is useful for small circuits (up to ~20 qubits) with careful initialization and problem-specific ansatz design. For larger-scale ML applications, it remains research-stage.

`````{tab-set}
````{tab-item} VQE in the ML Context
VQE (Variational Quantum Eigensolver) was designed for molecular chemistry (Chapter 7). In the ML context, its relevance is architectural: VQE demonstrated that a quantum circuit can be trained by a classical optimizer to solve a hard optimization problem. Every quantum neural network design inherits this architecture. When a vendor claims a "quantum neural network," the circuit is almost certainly a VQE-style parameterized structure.
````
````{tab-item} QAOA in the ML Context
QAOA (Quantum Approximate Optimization Algorithm) targets combinatorial optimization — the same category as hyperparameter search, neural architecture search, and feature selection in ML. A bank using quantum optimization to select the best feature subset for a credit model, or a logistics company using it to prune a neural architecture, is running QAOA-variants. Current QAOA hardware limits practical advantage to small instances — but the principle is sound and the hardware is improving.
````
````{tab-item} Barren Plateaus
The **barren plateau** problem (McClean et al., 2018): for randomly initialized variational circuits with many qubits, the loss gradient vanishes exponentially. Training effectively becomes impossible for circuits beyond ~15–20 qubits. Active research in structured initialization, layerwise training, and problem-specific ansatz design is narrowing this limitation. It is not solved.
````
`````

### Quantum Kernels: The Most Theoretically Grounded Near-Term Case

**Quantum kernels** are the most experimentally validated QML method available on today's gate-model hardware. The concept builds on the classical kernel trick that powers Support Vector Machines: instead of finding a separating boundary in the original feature space, you lift data into a higher-dimensional space where the boundary becomes a hyperplane.

A quantum kernel uses a quantum circuit — the **feature map** — to lift data into Hilbert space, whose dimension grows exponentially with qubit count. A 50-qubit quantum kernel maps data into a feature space with 2⁵⁰ dimensions. For classification problems with the right mathematical structure, the boundary that no classical kernel finds efficiently may exist in that space.

The quantum kernel value between data points x and x' is: **K(x, x') = |⟨φ(x)|φ(x')⟩|²** — where |φ(x)⟩ is the quantum state the feature map circuit produces.

:::{figure} ../images/ch08-quantum-kernels.png
:label: fig-quantum-kernels
:alt: Quantum kernel diagram showing data lifted from 2D tangled space through quantum feature map circuit into high-dimensional Hilbert space with clear separation boundary.
:width: 90%
:align: center

**Quantum Kernels: Lifting Data into Hilbert Space.** Classical kernel functions lift data into polynomial or radial-basis space. Quantum kernels use a quantum circuit to lift data into exponentially high-dimensional Hilbert space. For problems with the right mathematical structure, this enables decision boundaries that no classical kernel finds efficiently — but that specific mathematical structure is narrow and actively researched.
:::

The experimental record is instructive precisely because it is honest. In 2021, Havlíček et al. demonstrated that quantum feature maps generate kernel functions that are classically hard to compute — a necessary condition for advantage. In 2022, Kübler et al. showed that for typical ML datasets, quantum kernel values concentrate around a constant — providing no discriminative signal. The exponential feature space is a curse for generic data, not just a blessing. The pattern across 2022–2025 experiments: quantum kernels are competitive with classical kernels on small, structured datasets. On standard production-scale benchmarks, well-tuned classical RBF kernels are competitive or superior.

This is not dismissal. It is the honest experimental record as of 2026. Organizations with high-dimensional classification problems in genomics, drug discovery, or financial factor spaces should track this research actively.

### Quantum Sampling and Generative Models

Quantum computers have a natural affinity for sampling: a quantum circuit, when measured, samples from a probability distribution that is exponentially difficult to compute classically. If that sampling capability can accelerate the estimation of complex probability distributions inside generative model training loops, a genuine hybrid speedup becomes plausible.

Proposed architectures — **Quantum Boltzmann Machines (QBMs)** and **Quantum GANs (QGANs)** — use quantum circuits to represent latent distributions in generative models. As of 2026, this remains largely theoretical for gate-model hardware. The sampling advantage is real in principle; the circuits required for meaningful advantage exceed current NISQ devices significantly.

The most immediately relevant deployment: D-Wave's quantum annealer, which naturally samples from Boltzmann distributions, has been explored by financial firms (including the hedge fund case study later in this chapter) for generating synthetic financial time series with heavy-tail properties. The results are preliminary but represent the nearest-term production candidate for quantum-enhanced generative modeling.

---

## Part III: Dequantization — The Term Every Leader Must Know

::::{prf:definition} Dequantization
:label: def-dequantization

**Dequantization** is the development of classical algorithms that match the asymptotic performance of quantum algorithms, eliminating the claimed speedup. A dequantized result does not mean the quantum algorithm was wrong — it means the advantage was not fundamental, because the classical algorithm's earlier inefficiency was algorithmic, not inherent. The term was popularized by Ewin Tang's 2019 result showing a classical algorithm matched the quantum recommendation system algorithm of Kerenidis and Prakash (2016), which had claimed exponential speedup.
::::

The dequantization story begins with a celebrated result: in 2016, a quantum algorithm for recommendation systems claimed an exponential speedup over classical approaches. The result was rigorous. The speedup was real. It helped launch the quantum ML field. In 2019, an MIT graduate student named Ewin Tang showed that a classical algorithm using **sampling-based low-rank approximation** matched the quantum speedup — making it the first major dequantization result. The quantum advantage had depended on an unexplored corner of classical algorithm design, not a fundamental quantum property.

:::{figure} ../images/ch08-dequantization-concept.png
:label: fig-dequantization
:alt: Dequantization timeline showing Kerenidis-Prakash 2016 quantum recommendation algorithm, Tang 2019 classical match, and the wave of dequantization results through 2023 with summary of what survived and what didn't.
:width: 90%
:align: center

**The Dequantization Filter.** Tang (2019) established that quantum advantage requires proof that no efficient classical sampling algorithm exists — not just evidence that the obvious classical approach is slow. The diagram shows which quantum ML speedup claims have survived dequantization scrutiny and which have not.
:::

**Where dequantization stands today:**

| Quantum ML Claim | Dequantization Status |
|---|---|
| Quantum recommendation systems | 🔴 Dequantized (Tang 2019) |
| Quantum PCA | 🔴 Dequantized (Tang 2021) |
| HHL linear systems | 🟡 Partial — retains speedup in narrow conditions |
| Quantum kernel methods | 🟢 Not dequantized — but advantage requires specific data structure |
| Quantum Boltzmann sampling | 🟢 Not dequantized — strongest near-term case |
| Variational QML (VQE, QAOA, QNN) | 🟢 Not applicable — heuristic methods, no provable speedup claimed |

The leadership value of understanding dequantization is not theoretical. Every quantum AI vendor pitching an ML speedup implicitly claims the advantage has survived the dequantization test. Most have not checked. The right procurement question: *"Has your algorithm been compared against optimal classical randomized baselines, and has anyone attempted to dequantize the speedup?"* The vendor who can answer this fluently has done serious work. The vendor who has not heard of Tang (2019) has not.

---

## Part IV: Quantum-Inspired Classical Algorithms — What You Can Deploy First

Before any quantum hardware enters your ML pipeline, there is a class of algorithms you can deploy today that deliver real performance improvements on classical hardware — derived from the mathematical structures of quantum mechanics.

These are **quantum-inspired algorithms**, and they represent the most immediately actionable outcome of the quantum ML research program for most organizations. They are not a consolation prize. They are a genuine contribution of quantum computing theory to classical algorithm design, available right now.

### The Quantum-Inspired Taxonomy

`````{tab-set}
````{tab-item} Tensor Network Methods
Tensor networks — particularly Matrix Product States (MPS) and Projected Entangled Pair States (PEPS) — were developed in quantum physics to efficiently represent quantum many-body states. They have been adapted to classical ML as a way to compress and manipulate high-dimensional data with structured correlations.

**Applications:** Sequence modeling for time series (financial, supply chain, sensor data), image compression for high-dimensional vision tasks, efficient Bayesian inference over structured models.

**Production readiness:** High. TensorLy (Python) provides production-grade tensor network implementations. Used in production at several financial institutions for time-series decomposition.

**Connection to supply chain:** Tensor network methods have been applied to multi-echelon demand forecasting, where the correlations between demand signals across distribution centers have the structured form that MPS represents efficiently. A 15–30% improvement in forecast accuracy has been documented for SKUs with high inter-DC demand correlation.
````
````{tab-item} Quantum-Inspired Sampling
Classical algorithms using **randomized sampling techniques** derived from quantum amplitude estimation — particularly **Monte Carlo Tree Search variants** informed by quantum walk theory and **Gibbs sampling algorithms** inspired by quantum Boltzmann machine architectures.

**Applications:** Scenario generation for Monte Carlo risk models (financial services), synthetic data generation for model training, reinforcement learning exploration strategies.

**Production readiness:** Medium-high. Goldman Sachs's published quantum-inspired derivative pricing algorithms (which match quantum amplitude estimation performance on classical hardware) are the best-documented production case. These algorithms are available in open-source form.

**Connection to supply chain:** Quantum-inspired Gibbs sampling has been used for demand scenario generation in supply chain risk modeling — generating synthetic demand shocks with heavy-tail statistics that classical normal-distribution models miss. Documented improvement in safety stock optimization accuracy when tail scenarios are modeled correctly.
````
````{tab-item} QUBO-Inspired Combinatorial Optimization for ML
The QUBO formulation language from D-Wave applications (Chapters 6 and 7) applies to ML optimization problems as well as logistics and scheduling. Feature selection, neural architecture search, and ensemble construction are combinatorial optimization problems — they can be formulated as QUBOs and solved by either quantum annealers (on D-Wave hardware) or by **quantum-inspired solvers** running on classical hardware (Fujitsu Digital Annealer, Toshiba SQBM+, simulated bifurcation machines).

**Applications:** Feature subset selection for high-dimensional ML models, ensemble member selection (QBOOST), hyperparameter combinatorial search, neural network pruning.

**Production readiness:** High for quantum-inspired classical solvers. High for D-Wave hardware (Lab 8B). Fujitsu's Digital Annealer is in production use at Mizuho Bank and several Japanese manufacturers for QUBO-structured combinatorial problems.

**The key insight:** Learning to formulate ML optimization problems as QUBOs — the skill developed in Chapter 6 — transfers directly to both quantum hardware (D-Wave) and quantum-inspired classical hardware (digital annealers). The formulation is the durable skill. The hardware is interchangeable.
````
`````

### Why Quantum-Inspired Algorithms Matter for Supply Chain and Operations

The Mehran Basiratmand course that this book accompanies dedicates Week 4b specifically to **quantum-enhanced predictive analytics for supply chain and operations.** Quantum-inspired classical algorithms are the primary technology for that week — not because quantum hardware is not ready, but because quantum-inspired methods deliver production value today in exactly the supply chain domains that MBA students and operations executives care about.

Three quantum-inspired applications with documented enterprise deployments:

**1. Tensor-network demand forecasting.** The multi-echelon inventory problem — forecasting demand at 20 distribution centers with correlated demand signals across 500 SKUs — has the structured correlation form that Matrix Product State tensor networks represent efficiently. Classical time-series models (ARIMA, LSTM) treat each DC-SKU combination independently or with simple pairwise correlations. MPS models capture the full correlation structure across the network, improving forecast accuracy for correlated SKUs by 15–30% in documented deployments.

**2. Quantum-inspired scenario generation for resilience.** Supply chain risk models require generating realistic scenarios for demand shocks, supplier failures, and logistics disruptions. Classical Monte Carlo sampling from normal distributions systematically underestimates tail events. Quantum-inspired Gibbs samplers — which sample from Boltzmann distributions without requiring a quantum computer — generate scenarios with heavier tails and more realistic extreme events, improving the accuracy of safety stock calculations and resilience planning.

**3. QUBO feature selection for operations analytics.** Predictive models for supply chain operations — demand forecasting, equipment failure prediction, order fulfillment risk — often have hundreds of candidate features. Feature selection is a combinatorial problem: finding the subset of features that maximizes model performance while minimizing correlation and complexity. QUBO formulation of the feature selection problem — with binary variables for inclusion/exclusion and quadratic penalties for feature correlation — enables D-Wave or quantum-inspired solvers to explore a broader feature subset space than classical greedy or backward elimination methods.

:::{figure} ../images/ch08-supply-chain-analytics.png
:label: fig-supply-chain-analytics
:alt: Three quantum-inspired supply chain analytics applications showing tensor network demand forecasting, Gibbs sampler scenario generation, and QUBO feature selection, each with documented enterprise deployment and performance improvement range.
:width: 100%
:align: center

**Quantum-Enhanced Supply Chain Analytics: Three Production Applications.** All three applications use quantum-inspired methods — no quantum hardware required. Tensor network demand forecasting: 15–30% forecast accuracy improvement for correlated multi-DC SKUs. Gibbs sampler scenario generation: more accurate tail risk modeling for safety stock. QUBO feature selection: broader feature space exploration than classical greedy methods.
:::

---

## Part V: Industry Cases — When QML Met the Real World

### The Credit-Scoring Pilot and Its Most Important Lesson

A mid-sized regional bank ran a quantum kernel credit-scoring pilot in 2023. The quantum kernel SVM, using an IBM ZZFeatureMap circuit on 6 qubits, achieved 89.3% accuracy on 1,200 historical loan applications. The classical SVM baseline achieved 87.2%. A 2.1-percentage-point advantage was reported to the CTO, presented at a fintech conference, and picked up by three trade publications.

Eighteen months later, a new ML engineer audited the baseline. The original classical SVM had been tuned with a 1D hyperparameter grid that did not jointly optimize the kernel bandwidth parameter γ. A proper joint grid search on the same data achieved 89.1% — within measurement noise of the quantum result.

The quantum advantage was 0.2 percentage points on a 1,200-sample dataset with no confidence interval reported. It was not statistically distinguishable from zero.

:::{figure} ../images/ch08-credit-scoring-case.png
:label: fig-credit-scoring
:alt: Timeline case study of bank quantum kernel credit scoring pilot showing 2023 initial quantum advantage claim and 2025 classical catch-up after proper baseline tuning, with cost comparison.
:width: 90%
:align: center

**The Credit-Scoring Timeline.** 2023: quantum kernel achieves 89.3%, 2.1 points above the under-tuned classical baseline. 2025: properly tuned classical RBF kernel achieves 89.1% — within noise. The experiment cost \$340,000. The classical re-tuning cost \$8,000. The lesson: the quantum experiment was not fraudulent. The baseline was incomplete. This is the structural failure mode of most enterprise QML pilots.
:::

This case study is not told to embarrass the bank. The team did serious, careful work. The lesson is structural: **quantum advantage comparisons require classical baselines that are not merely competent but optimal.** The classical baseline is not the starting point you beat — it is the result you spend 80% of your engineering effort optimizing before you write a single line of quantum code. Most enterprise QML pilots skip this step.

### The Hedge Fund's D-Wave Generative Model Experiment

In 2024, a quantitative hedge fund attempted to use D-Wave's quantum annealer to improve synthetic financial time series generation for backtesting. Their classical VAE generative model produced synthetic price series that underrepresented tail events — an important flaw for risk modeling.

The hypothesis: D-Wave's Advantage system naturally samples from Boltzmann distributions through quantum annealing. Financial return distributions have heavy tails. Perhaps quantum annealing would capture that tail behavior more naturally than classical VAE sampling.

The experiment ran four months. D-Wave-generated samples showed slightly heavier tails than the classical VAE. Statistical tests found the difference significant at the 5% level. The internal report recommended further investigation.

The conclusion they did not reach — but that a dequantization-aware reviewer would raise — is that D-Wave samples from a Boltzmann distribution defined by the hardware's **Pegasus graph structure**, not by financial return distributions. The tail behavior improvement was likely a hardware sampling artifact, not a principled model of equity returns. The experiment was genuine exploration. The interpretation required more precision.

What the experiment actually demonstrated: D-Wave's Advantage system does produce interesting sampling properties for certain structured distributions. That is a real finding — worth further investigation with explicit comparison to classical Boltzmann sampling and careful analysis of whether the hardware graph structure maps to the problem's correlation structure. This is exactly the kind of result that the annealing-for-ML lane — the subject of Lab 8B — is designed to explore.

### A Supply Chain Team's Quantum-Inspired Forecasting Pilot

A consumer goods company's supply chain analytics team implemented tensor-network demand forecasting across 12 distribution centers and 340 high-velocity SKUs in 2024. The problem: highly correlated demand across DCs (a promotional campaign in one region predictably lifts demand in adjacent regions), which classical LSTM and ARIMA models handled poorly because they were trained per-DC without capturing cross-DC correlation structure.

The tensor-network implementation used TensorLy with a Matrix Product State decomposition of the multi-DC demand tensor. Training time was comparable to the LSTM baseline. Forecast accuracy improved 22% for the 40 highest-correlation SKU-DC pairs. Inventory carrying cost reduction for those SKUs: approximately \$1.2 million annually, on an implementation cost of \$180,000.

No quantum hardware was required. The mathematical insight came from quantum physics — tensor networks were developed to efficiently represent entangled quantum states. The computation ran on classical CPUs. This is the quantum-inspired bridge: the theory is quantum, the implementation is classical, the value is immediate.

---

## Part VI: The Governance Framework — Evaluating Any Quantum-AI Claim

### The Five-Question Filter

Every quantum-AI vendor claim can be evaluated with five questions. Organizations that make these questions part of standard procurement practice will eliminate the vast majority of quantum AI marketing noise before it reaches the decision stage.

:::{figure} ../images/ch08-governance-checklist.png
:label: fig-governance-checklist
:alt: Five-question governance filter flowchart for evaluating quantum AI vendor claims, with examples of passing and failing responses for each question.
:width: 90%
:align: center

**The Five-Question Quantum AI Governance Filter.** Any claim that cannot pass all five is unvalidated marketing until evidence is provided. The filter takes approximately 20 minutes to apply to any vendor pitch. Organizations that institutionalize it save significant R&D budget and avoid the baseline problem that cost the regional bank \$340,000.
:::

```{list-table} The Five-Question Governance Filter
:header-rows: 1

* - #
  - Question
  - What to Look For
  - Red Flag
* - 1
  - Is there peer-reviewed evidence?
  - Paper in Nature, Science, Physical Review, NeurIPS, ICML, or equivalent — not a blog post or press release.
  - "Our internal benchmarks show..." without a citable paper.
* - 2
  - Was the classical baseline optimized?
  - Evidence of hyperparameter tuning, cross-validation, and state-of-the-art classical algorithms — not just the obvious baseline.
  - Classical baseline described in one sentence with no tuning methodology.
* - 3
  - Has dequantization been considered?
  - Vendor can explain why no efficient classical sampling algorithm achieves the same result. They know who Ewin Tang is.
  - Vendor has not heard of the dequantization literature.
* - 4
  - Is the statistical evidence sufficient?
  - Multiple seeds, confidence intervals, adequate dataset size, paired significance tests.
  - Single result, no confidence interval, dataset under 1,000 samples.
* - 5
  - Has it been independently replicated?
  - At least one independent group has reproduced the core result.
  - "We are the only ones who have run this experiment."
```

### Extending the Filter: Gate-Model vs. Annealing Claims

A critical governance addition for this course: quantum AI claims involving **D-Wave annealing** and **gate-model QML** require different evaluation frameworks. The five-question filter applies to both — but the specific questions differ.

For **gate-model QML claims** (quantum kernels, variational networks, quantum advantage for ML):
- Does the speedup survive dequantization? (Apply questions 2 and 3 most aggressively)
- Was the experiment run on real hardware, not a simulator?
- Does the dataset have the mathematical structure the quantum approach requires?

For **D-Wave annealing for ML optimization** (feature selection, ensemble construction, hyperparameter search):
- Is the ML optimization problem formulated as a QUBO? (If not, D-Wave cannot help)
- Does the QUBO formulation correctly encode the ML objective — not just "run fast" but "find better feature subsets"?
- Was the D-Wave result compared against classical combinatorial optimization baselines (simulated annealing, genetic algorithms) — not just the greedy classical approach?

The annealing-for-ML lane is more experimentally mature than gate-model QML for most production ML optimization tasks. It is also more susceptible to a different kind of hype: claims that D-Wave "does ML" when the actual contribution is optimizing one combinatorial step in the ML pipeline. The distinction matters for setting expectations.

### The Procurement Decision Tree

```{mermaid}
flowchart LR
    A[Vendor quantum AI claim] --> B{Gate-model or\nannealing?}
    B -- Gate-model --> C{Peer-reviewed\nevidence?}
    B -- Annealing --> D{QUBO formulation\ncorrect?}
    C -- No --> E[Marketing only\ndo not fund]
    C -- Yes --> F{Classical baseline\noptimized?}
    F -- No --> E
    F -- Yes --> G{Dequantization\nchecked?}
    G -- No --> H[Require\ndequantization test\nbefore proceeding]
    G -- Yes --> I[Pilot eligible\nwith conditions]
    D -- No --> J[Reformulate\nor reject]
    D -- Yes --> K{Classical combinatorial\nbaseline compared?}
    K -- No --> L[Add baseline\nbefore approval]
    K -- Yes --> I
    I --> M[Require Classical\nBaseline Optimization\nPlan as condition\nof pilot approval]
```

---

## Flagship Case Study: A Financial Services Firm's Quantum Kernel Credit Pilot

### The Full Anatomy of the FinCorp Capital Experiment

FinCorp Capital (a composite of documented industry cases) is a mid-sized regional bank whose ML-driven credit underwriting team had 14 engineers and a strong culture of experimentation. In early 2023, the Chief Analytics Officer read the Havlíček et al. (2019) quantum kernel paper and scheduled a vendor meeting. The pitch: quantum kernels could improve credit classification accuracy for borderline cases, reducing default rates. Projected value: \$2.3 million in annual default cost reduction for a 2-percentage-point accuracy improvement.

**The setup:** The secondary SVM model for borderline applications — 15% of loan volume — was the pilot target. The feature set had 14 engineered credit variables. The quantum kernel used IBM Qiskit ML with a ZZFeatureMap on 6 qubits, run on IBM Falcon hardware. Implementation: 12 weeks, two engineers.

**Three consequential decisions:**

1. The classical baseline used the production model's hyperparameters — tuned 18 months earlier, with regularization C grid-searched but kernel bandwidth γ set to scikit-learn default, not jointly optimized.
2. The dataset had 1,200 training samples — sufficient for an SVM but small for drawing robust conclusions about a 2-point accuracy gap.
3. Results were reported to the CTO without confidence intervals. The 2.1-point advantage was treated as a point estimate.

**The outcome:** Quantum kernel: 89.3%. Classical SVM (production settings): 87.2%. Result reported as a validated quantum advantage. Total cost: \$340,000 in compute, engineering, and consulting. Then — 18 months later — a new engineer ran a joint grid search on γ and C. Tuned classical SVM: 89.1%. The advantage closed to 0.2 points — statistically indistinguishable from zero on a 1,200-sample dataset.

**The governance lesson:** The experiment was not fraudulent. It was incomplete in the most common way — the classical baseline was competent but not optimal. The remedy is simple and cheap: a **Classical Baseline Optimization Plan** required before any quantum pilot is approved, specifying which classical algorithms will be compared, what tuning methodology will be used, what compute budget will be allocated to classical optimization, and what minimum performance gap is required to declare advantage.

---

## Productive-Struggle Problem

::::{admonition} Three Vendor Claims: Rank by Credibility
:class: tip

A procurement team receives three executive summaries from quantum AI vendors. Rank from most to least credible. For each, name the **single experiment** that would definitively falsify the advantage claim.

**Vendor A — QuantumKernelCo:** "Our quantum kernel SVM achieves 94.3% on credit default prediction vs. 91.7% for the best classical SVM, on 1,500 samples with 8 features. IBM Quantum hardware, single seed, no confidence interval, scikit-learn default hyperparameters for the classical baseline."

**Vendor B — QuantumGenAI:** "Our quantum Boltzmann machine generates synthetic financial time series with tail statistics matching S&P 500 returns, outperforming classical VAE and GAN on KL-divergence and tail index. D-Wave Advantage hardware. Validated by three independent financial statisticians. Paper under review at *Journal of Computational Finance.* 20 years of daily returns, 5 seeds, full confidence intervals."

**Vendor C — VariationalVentures:** "Our variational quantum optimizer reduces hyperparameter search time for deep neural network training by 37% versus random search, 28% versus Bayesian optimization, using QAOA on a 12-qubit *simulator.* Three neural network architectures. Published in *Physical Review Applied* (2024). No hardware experiments."

**After ranking:** Apply the five-question governance filter to each vendor. What additional information would move a lower-ranked vendor up?
::::

---

## Module-Level Outcomes

::::{card-carousel} 1

:::{card} Outcome 1
**Distinguish the two quantum AI paradigms.**
Accurately differentiate gate-model QML (quantum kernels, variational circuits) from D-Wave annealing for ML optimization (QBOOST, feature selection, ensemble construction), and identify which applies to a given ML business problem.
:::

:::{card} Outcome 2
**Explain variational QML and its NISQ-era limitations.**
Describe how parameterized quantum circuits are trained, what the barren plateau problem is, and why variational QML delivers value on small circuits today but faces fundamental scaling challenges.
:::

:::{card} Outcome 3
**Apply the dequantization test to a quantum ML claim.**
Explain what dequantization means, describe the Tang (2019) result, and apply the test to evaluate whether a specific quantum ML speedup claim has a plausible classical match.
:::

:::{card} Outcome 4
**Deploy quantum-inspired algorithms for supply chain analytics.**
Identify the supply chain and operations applications of tensor network demand forecasting, quantum-inspired scenario generation, and QUBO feature selection — and explain why these deliver production value today without quantum hardware.
:::

:::{card} Outcome 5
**Apply the five-question governance filter to any quantum AI vendor claim.**
Distinguish between a validated quantum advantage and a quantum AI marketing claim using the five-question filter, with specific application to both gate-model and annealing-based QML vendor pitches.
:::

:::{card} Outcome 6
**Run a D-Wave quantum annealing ML optimization job.**
Formulate a feature selection or ensemble construction problem as a QUBO, submit it to D-Wave Leap, interpret the results against a classical baseline, and assess whether the quantum-annealing approach found a better solution.
:::

::::

---

## Lab 8A (Regular): Quantum Kernels vs. Classical Kernels

**Duration:** ~60 minutes
**Tools:** Qiskit Machine Learning, IBM Quantum (free tier)
**Platform:** [Google Colab](https://colab.research.google.com) — no local install required

<a href="https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch08-lab-quantum-kernels.ipynb" target="_blank">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="margin-bottom: 1rem;"/>
</a>

### Why This Lab

The FinCorp Capital case study teaches the lesson intellectually. This lab teaches it experientially. You will run the same experiment — quantum kernel SVM vs. classical SVM — but you will do what FinCorp's team did not: you will implement the **Classical Baseline Optimization Plan** first and run the quantum kernel against an optimally tuned classical baseline.

### The Dataset

A synthetic credit classification dataset with 14 features (mimicking credit variables: payment history length, DTI ratio, behavioral signals, macro indicators) and 2 classes (default/non-default). 2,000 samples, class-balanced.

### Instructions

```python
from qiskit.circuit.library import ZZFeatureMap
from qiskit_machine_learning.kernels import FidelityQuantumKernel
from qiskit_machine_learning.algorithms import QSVC
from sklearn.svm import SVC
from sklearn.model_selection import GridSearchCV, cross_val_score
from sklearn.preprocessing import StandardScaler
import numpy as np

# Load dataset (from Colab notebook)
X_train, X_test, y_train, y_test = load_credit_dataset()
scaler = StandardScaler()
X_train_s = scaler.fit_transform(X_train)
X_test_s = scaler.transform(X_test)

# STEP 1: Classical Baseline Optimization Plan
# Jointly optimize C and gamma (the FinCorp team's mistake was optimizing only C)
param_grid = {
    'C': [0.01, 0.1, 1, 10, 100, 1000],
    'gamma': ['scale', 'auto', 0.001, 0.01, 0.1, 1.0],
    'kernel': ['rbf', 'poly', 'sigmoid']
}
classical_svm = GridSearchCV(SVC(), param_grid, cv=5, scoring='accuracy', n_jobs=-1)
classical_svm.fit(X_train_s, y_train)
classical_acc = classical_svm.score(X_test_s, y_test)
print(f"Optimized classical SVM accuracy: {classical_acc:.4f}")
print(f"Best params: {classical_svm.best_params_}")

# STEP 2: Quantum Kernel (6-qubit ZZFeatureMap on 6 features — reduce dimensionality first)
from sklearn.decomposition import PCA
pca = PCA(n_components=6)
X_train_pca = pca.fit_transform(X_train_s)
X_test_pca = pca.transform(X_test_s)

feature_map = ZZFeatureMap(feature_dimension=6, reps=2)
qkernel = FidelityQuantumKernel(feature_map=feature_map)
qsvc = QSVC(quantum_kernel=qkernel)
qsvc.fit(X_train_pca[:200], y_train[:200])  # Note: quantum kernel is slow — use subset
quantum_acc = qsvc.score(X_test_pca[:50], y_test[:50])
print(f"Quantum kernel SVM accuracy (200 train / 50 test): {quantum_acc:.4f}")

# STEP 3: Compare and assess statistical significance
# Is the difference larger than the confidence interval?
n_test = 50
ci_width = 1.96 * np.sqrt(quantum_acc * (1 - quantum_acc) / n_test)
print(f"95% CI width for quantum result: ±{ci_width:.4f}")
print(f"Gap vs. classical: {quantum_acc - classical_acc:.4f}")
print(f"Is gap > CI? {'Yes — statistically significant' if abs(quantum_acc - classical_acc) > ci_width else 'No — within noise'}")
```

### Deliverable

Write a **400-word analysis** applying the five-question governance filter to your own experiment:
1. Did you observe quantum advantage?
2. Was the classical baseline properly optimized? (Show your hyperparameter grid results)
3. Is the difference statistically significant, given the dataset size?
4. What additional experiment would be needed before recommending a quantum kernel procurement decision?

---

## Lab 8B (Applied): Quantum Annealing for ML Feature Selection

**Duration:** 60–75 minutes
**Tools:** D-Wave Leap — [cloud.dwavesys.com](https://cloud.dwavesys.com) (free developer account)
**Deliverable:** Feature selection results + 300-word ML engineering memo

<a href="https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch08-lab-qboost-feature-selection.ipynb" target="_blank">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="margin-bottom: 1rem;"/>
</a>

### Why This Lab

Gate-model QML (Lab 8A) is the research frontier — promising but not yet production-ready for most ML applications. D-Wave annealing for ML optimization is a different story. Feature selection is a combinatorial optimization problem: given N candidate features, find the subset of K features that maximizes predictive accuracy while minimizing redundancy. For N = 50 features, there are 2⁵⁰ possible subsets — a combinatorial space that classical greedy or backward elimination methods explore only locally.

This lab formulates feature selection as a QUBO and submits it to D-Wave Leap — the same hardware class as FAU's Advantage2. The objective: find a feature subset that produces better model performance than classical greedy forward selection on the same ML task.

### The Problem: Supply Chain Demand Forecasting Feature Selection

You are building a demand forecast model for a regional distribution network. You have 20 candidate features: 5 lag features, 4 seasonal indicators, 3 competitor price signals, 4 macroeconomic variables, and 4 operational metrics. You need to select the best 8 for a lean production model.

Classical greedy selection evaluates features one at a time, adding the best single feature at each step. It cannot back up or evaluate subset combinations. The QUBO formulation explores the full combinatorial space.

```python
import dimod
import numpy as np
from dwave.system import LeapHybridSampler
from sklearn.ensemble import GradientBoostingRegressor
from sklearn.model_selection import cross_val_score

# Load supply chain dataset (from Colab notebook)
X, y, feature_names = load_supply_chain_dataset()  # 20 features, demand target

# Pre-compute feature importances and correlations for QUBO construction
from sklearn.ensemble import RandomForestRegressor
rf = RandomForestRegressor(n_estimators=100, random_state=42)
rf.fit(X, y)
importances = rf.feature_importances_

correlations = np.corrcoef(X.T)
n_features = X.shape[1]
target_size = 8  # we want 8 features
lambda_size = 5  # penalty for wrong subset size
lambda_corr = 3  # penalty for correlated features

Q = {}

# Objective: maximize importance score for selected features
for i in range(n_features):
    Q[(i, i)] = Q.get((i, i), 0) - importances[i] * 10  # reward important features

# Penalty: correlated feature pairs (don't select both highly correlated features)
for i in range(n_features):
    for j in range(i + 1, n_features):
        if abs(correlations[i, j]) > 0.7:  # high correlation threshold
            Q[(i, j)] = Q.get((i, j), 0) + lambda_corr * abs(correlations[i, j])

# Constraint: select exactly target_size features
# Penalty: lambda_size * (sum(x_i) - target_size)^2
for i in range(n_features):
    Q[(i, i)] = Q.get((i, i), 0) + lambda_size * (1 - 2 * target_size)
    for j in range(i + 1, n_features):
        Q[(i, j)] = Q.get((i, j), 0) + 2 * lambda_size

# Submit to D-Wave Leap
sampler = LeapHybridSampler()
sampleset = sampler.sample_qubo(Q, label='Demand Forecast Feature Selection', time_limit=10)
best = sampleset.first

# Extract selected features
quantum_features = [i for i, selected in best.sample.items() if selected == 1]
print(f"Quantum-selected features ({len(quantum_features)}):")
for f in quantum_features:
    print(f"  {feature_names[f]:30} importance: {importances[f]:.4f}")

# Evaluate: train model on quantum-selected vs. greedy-selected features
from sklearn.feature_selection import SelectKBest, f_regression

# Classical baseline: greedy forward selection (SelectKBest as proxy)
classical_selector = SelectKBest(f_regression, k=target_size)
X_classical = classical_selector.fit_transform(X, y)
classical_features = np.where(classical_selector.get_support())[0]

X_quantum = X[:, quantum_features]
X_classical_sel = X[:, classical_features]

model = GradientBoostingRegressor(n_estimators=100, random_state=42)
quantum_score = cross_val_score(model, X_quantum, y, cv=5, scoring='r2').mean()
classical_score = cross_val_score(model, X_classical_sel, y, cv=5, scoring='r2').mean()

print(f"\nModel performance (5-fold CV R²):")
print(f"  Quantum-selected features: {quantum_score:.4f}")
print(f"  Classical-selected features: {classical_score:.4f}")
print(f"  Difference: {quantum_score - classical_score:+.4f}")
print(f"  QPU timing: {sampleset.info.get('timing', {})}")
```

### Step 2: Experiment

- Change `lambda_corr` to 0 (no correlation penalty). Does the solver still avoid selecting correlated features?
- Change the target size from 8 to 5. Which features survive the tighter constraint?
- Compare against simulated annealing (`dimod.SimulatedAnnealingSampler`) instead of D-Wave. Does classical simulated annealing find the same feature set?

### Deliverable

Write a **300-word ML engineering memo** to your data science team lead:
1. Which features did the D-Wave solver select vs. the classical baseline — and do the differences make intuitive sense given your domain knowledge?
2. Did the D-Wave-selected features produce better or worse model performance? Why might the result have gone either way?
3. Under what conditions would you recommend this QUBO feature selection approach for a production ML pipeline — and when would you stick with classical methods?

---

## Lab 8C (Optional Advanced): Honest QML Benchmarking

**Duration:** ~90 minutes
**Tools:** Qiskit ML, PennyLane, scikit-learn

<a href="https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch08-lab-honest-benchmarks.ipynb" target="_blank">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="margin-bottom: 1rem;"/>
</a>

### Why This Lab

Most QML benchmarks in the academic literature and vendor materials fail the five-question filter. This lab runs a QML experiment the right way — applying the complete Classical Baseline Optimization Plan, statistical significance testing, and the dequantization check to your own quantum kernel result.

### Core Protocol

1. **Classical Baseline Optimization:** Full joint grid search over C, γ, and kernel type. Document the tuning budget.
2. **Quantum Kernel Implementation:** ZZFeatureMap + FidelityQuantumKernel on IBM Quantum hardware (not simulator).
3. **Statistical Testing:** Bootstrap confidence intervals on the accuracy difference. Minimum 5 seeds. Report the interval, not just the point estimate.
4. **Dequantization Check:** Implement a Nyström approximation of the quantum kernel on classical hardware. Does the approximation match quantum kernel performance?
5. **Honest Conclusion:** Given your results, write the summary that the FinCorp team should have written — including what the result actually supports and what it does not.

### Deliverable

A reproducible benchmarking report following the structure of a rigorous QML paper: dataset description, classical baseline methodology, quantum implementation details, statistical results with confidence intervals, dequantization analysis, and limitations. Maximum 800 words plus figures.

---

## Discussion Guidelines

**Post a substantive response (minimum 300 words) citing at least two sources. Reply meaningfully to TWO peers.**

### Discussion Prompt

You are advising the Chief Analytics Officer of a \$10 billion logistics company. Their ML team has been pitched by two quantum AI vendors in the past month. The CAO wants a recommendation.

**Vendor A** offers a quantum kernel SVM for predicting shipment delay risk. Their demo shows 3-point accuracy improvement over the company's current gradient-boosted model, on a 5,000-sample subset of the company's data. No information provided about classical SVM baseline tuning. Pricing: \$1.2M annual cloud contract.

**Vendor B** offers a QUBO-based feature selection and route optimization service using D-Wave hardware, applied to the company's 200-vehicle fleet routing model. They have not published peer-reviewed results but can demonstrate a working pilot on a 20-vehicle subset of the company's actual data. Pricing: \$400K annual contract + \$150K implementation.

1. **Apply the five-question filter** to both vendors. Where does each fail or pass?
2. **Make a recommendation.** Which vendor, if either, should the logistics company pilot — and under what conditions?
3. **Design the pilot.** What would the Classical Baseline Optimization Plan look like for Vendor A? What would proper success criteria look like for Vendor B?

**Peer response:** Challenge one assumption in your classmate's recommendation. What would change your recommendation?

---

## Glossary

```{glossary}
Quantum Machine Learning (QML)
  The application of quantum computing to machine learning tasks — running ML algorithms on quantum hardware, using quantum circuits as trainable models, or leveraging quantum effects to accelerate ML subroutines. Distinct from quantum-inspired ML (classical algorithms using quantum math) and quantum-optimization-enhanced ML (D-Wave annealing applied to ML combinatorial tasks).

Quantum Kernel
  A kernel function implemented as a quantum circuit that maps data into Hilbert space — an exponentially high-dimensional feature space — for use in kernel-based classifiers such as SVMs. The quantum kernel value between two data points is the overlap of their quantum state representations.

Feature Map Circuit
  The quantum circuit that implements a quantum kernel by mapping classical data points to quantum states. The ZZFeatureMap (IBM Qiskit) is the most widely used experimental feature map circuit.

Parameterized Quantum Circuit (PQC)
  A quantum circuit with trainable parameters (gate rotation angles) optimized by a classical optimizer to minimize a loss function. The architectural foundation of variational QML — VQE, QAOA, and quantum neural networks.

Barren Plateau
  The problem (McClean et al., 2018) in which the gradient of the loss function for a randomly initialized variational quantum circuit vanishes exponentially with circuit depth and qubit count. The primary training challenge for deep quantum neural networks.

Dequantization
  The development of classical algorithms that match the asymptotic performance of quantum algorithms, eliminating the claimed speedup. Ewin Tang's 2019 result dequantizing the quantum recommendation system algorithm is the canonical example.

Quantum-Inspired Algorithms
  Classical algorithms applying mathematical structures from quantum mechanics — tensor networks, sampling methods, QUBO formulations — to deliver improved performance on classical hardware. Distinct from quantum algorithms running on quantum hardware. Production-ready today.

Tensor Networks (MPS, PEPS)
  Mathematical structures from quantum physics — Matrix Product States, Projected Entangled Pair States — adapted for classical ML to efficiently represent structured high-dimensional data correlations. Applied to multi-DC demand forecasting, sequential modeling, and Bayesian inference.

QBOOST
  D-Wave's quantum annealing approach to ensemble classifier optimization — formulating the problem of selecting and weighting binary classifiers as a QUBO to find optimal ensemble compositions. A production-accessible application of quantum annealing to ML.

QUBO Feature Selection
  The reformulation of ML feature selection as a Quadratic Unconstrained Binary Optimization problem — binary variables for feature inclusion, quadratic penalties for correlation — enabling D-Wave or quantum-inspired classical solvers to search the combinatorial feature space more broadly than greedy classical methods.

Quantum Boltzmann Machine (QBM)
  A generative model that uses quantum circuits (or D-Wave annealing) to represent latent probability distributions. The nearest-term production candidate for quantum-enhanced generative modeling, particularly for sampling from heavy-tailed distributions.

Quantum GAN (QGAN)
  A generative adversarial network in which the generator is a quantum circuit. Largely theoretical as of 2026 for gate-model hardware; D-Wave annealing provides the most experimentally tractable near-term version.

Classical Baseline Optimization Plan
  The governance document required before any QML pilot — specifying which classical algorithms will be compared, what hyperparameter tuning methodology will be used, what compute budget is allocated to classical optimization, and what performance gap is required to declare quantum advantage. The structural remedy for the FinCorp Capital failure mode.

Simulated Annealing
  A classical metaheuristic optimization algorithm that mimics the annealing process in metallurgy. Often used as a classical baseline for comparison against D-Wave quantum annealing in QUBO optimization problems.
```

---

## Going Deeper (Optional): Quantum Kernels, QBOOST, and the Dequantization Theorem

*This section is for readers with a machine learning background who want to understand the mathematical basis for quantum advantage (and its limits) in AI. Not required for course assessments.*

### Quantum Kernel Methods

Classical Support Vector Machines (SVMs) find optimal decision boundaries by computing inner products (kernels) between data points in a high-dimensional feature space. **Quantum kernel methods** replace the classical kernel with a quantum circuit: data point $x$ is encoded as a quantum state $|\phi(x)\rangle$ via a parameterized encoding circuit $U(x)$, and the kernel function becomes:

$$k(x_i, x_j) = |\langle \phi(x_i) | \phi(x_j) \rangle|^2 = |\langle 0|U^\dagger(x_i) U(x_j)|0\rangle|^2$$

The computational advantage: for certain encoding circuits, $|\phi(x)\rangle$ lives in an exponentially large Hilbert space ($2^n$ dimensional), making the effective feature map exponentially expressive. Classical computers cannot efficiently compute this inner product when $n$ is large, creating a potential quantum advantage — but only if the high-dimensional structure of $k$ is useful for the specific learning task. For most practical tabular business data, standard classical kernels (RBF, polynomial) are equally expressive, which is why quantum kernel advantage has been difficult to demonstrate empirically on real data.

### QBOOST: D-Wave for Ensemble Learning

**QBOOST** (Neven et al., 2012) formulates the boosting ensemble construction problem as a QUBO. In classical AdaBoost, weak classifiers are selected greedily (one at a time). QBOOST selects them jointly by minimizing the total ensemble prediction error:

$$\min_{w \in \{0,1\}^T} \left\| \sum_{t=1}^T w_t h_t(x) - y \right\|^2 + \lambda \|w\|_0$$

Where $h_t$ are pre-trained weak classifiers, $w_t \in \{0,1\}$ indicates selection, and $\lambda$ controls sparsity (regularization). The $\ell_0$ norm (count of selected classifiers) makes this NP-hard classically, but the quadratic binary structure maps directly to QUBO. D-Wave selects the optimal ensemble across all $2^T$ classifier subsets simultaneously, rather than greedily one at a time. At $T = 50$ classifiers, the classical exhaustive search has $2^{50} \approx 10^{15}$ candidates; D-Wave evaluates the energy landscape of all simultaneously.

### The Dequantization Theorem (Tang, 2019)

The most important limiting result for quantum ML: Ewin Tang showed that for several proposed quantum ML algorithms (quantum recommendation systems, quantum PCA, quantum linear systems) that claimed exponential speedups, classical algorithms with **sample-and-query access** (the ability to sample from the input in the same way a quantum computer can) match the quantum speedup. This "dequantization" result implies that the quantum speedup in these algorithms came not from quantum mechanics per se, but from a specific model of data access — and classical algorithms can use the same access model.

The practical implication: quantum ML advantage is real, but it requires genuine quantum effects (interference, entanglement in the computation) not just quantum-like data access patterns. The D-Wave QUBO approach for feature selection and ensemble construction uses quantum tunneling in the optimization process — a genuine quantum mechanical effect with no classical equivalent — which is why it is more robust against dequantization arguments than circuit-based quantum ML approaches.

---

## Leader's Takeaway

::::{admonition} The Leader's Takeaway
:class: important

Three things are simultaneously true about quantum AI, and holding all three at once is the senior leader's advantage.

**First:** Most of what is sold as quantum AI today is classical ML with quantum marketing. The dequantization test, the five-question governance filter, and the Classical Baseline Optimization Plan requirement will protect your organization from the 80% of quantum AI pitches that do not meet the standard of a validated advantage. Apply them. Teach them to your procurement team. Make them non-negotiable.

**Second:** The genuine near-term quantum AI opportunity is in the annealing lane. D-Wave's Advantage2 — the machine on FAU's campus, the hardware you used in Lab 8B — is not a gate-model quantum computer and does not run quantum neural networks. What it does is solve combinatorial optimization problems that appear inside ML pipelines: feature selection, ensemble construction, hyperparameter search. For organizations with large-scale ML operations, quantum annealing for ML optimization is accessible today, QUBO-formulated with the same skills from Chapter 6, and delivers measurable value when the classical greedy baseline is the bottleneck. This is not theoretical. It is running in production at Fujitsu's financial services clients, in D-Wave's QBOOST implementations, and in the pilot programs of any ML team that has thought carefully about which steps in their pipeline are combinatorial.

**Third:** The gate-model QML story is real but early. Quantum kernels may eventually find decision boundaries in high-dimensional spaces that classical methods cannot. Variational quantum circuits, once the barren plateau problem is solved for large circuits, may outperform classical neural networks on specific problem structures. Quantum sampling for generative models may produce distributions that classical samplers cannot efficiently match. Watch the dequantization literature. Monitor the experimental results. Build the literacy in your ML team to evaluate these results honestly when they arrive. The organizations that understand what a quantum advantage claim actually requires — peer review, optimized classical baselines, statistical rigor, dequantization testing — will be the ones that capture the genuine value when the hardware matures.

The FinCorp Capital case study cost \$340,000 to learn a lesson that this chapter teaches in a morning. Make sure your organization learns it here.
::::

---

## Cross-References

- **See {ref}`ch-06-optimization-goldmine`** for the QUBO formulation skills and D-Wave Ocean SDK used in Lab 8B — feature selection and ML optimization are combinatorial problems that use the same formulation language as manufacturing scheduling and logistics routing.
- **See {ref}`ch-07-simulation-revolution`** for quantum-enhanced supply chain optimization (Part II) and quantum kernel applications in financial services (Part I) — the industry context for the ML techniques in this chapter.
- **See {ref}`ch-05-cryptocalypse-y2q`** for the dequantization-aware governance mindset applied to security vendor claims — the same critical evaluation framework used here for QML claims.
- **See {ref}`ch-09-quantum-ready-enterprise`** for the enterprise talent architecture required to build and sustain quantum ML literacy, and the governance structures that make the five-question filter part of standard procurement practice.
