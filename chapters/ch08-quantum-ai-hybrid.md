---
title: "Chapter 8: Quantum + AI — The Hybrid Frontier"
subtitle: "Most Quantum AI Is Hype. The Rest Is Worth Watching Carefully."
short_title: "Ch. 8: Quantum + AI"
description: "The intersection of quantum computing and artificial intelligence is simultaneously overhyped and underexplored. This chapter separates genuine hybrid opportunity from marketing noise, introduces the critical concept of dequantization, and builds the governance instincts needed to evaluate any quantum-AI vendor claim."
label: ch-08-quantum-ai-hybrid
tags: [quantum machine learning, QML, quantum kernels, dequantization, variational circuits, QAOA, VQE, AI governance]
---

# Chapter 8: Quantum + AI — The Hybrid Frontier

:::{figure} ../images/ch08-explainer-infographic.png
:name: fig-ch08-explainer
:alt: Illustrated explainer infographic showing quantum circuit connected to neural network via a hybrid frontier bridge, with zones for QML, quantum kernels, dequantization warning, and governance checklist
:width: 100%

**The Hybrid Frontier at a Glance.** Quantum computing and AI are converging — but the map is uneven. Genuine hybrid opportunities exist in quantum kernels, variational algorithms, and quantum sampling. Most of what is sold as "Quantum AI" today lives in the marketing zone. This chapter gives you the tools to tell the difference.
:::

> *"The most important questions of life are indeed, for the most part, really only problems of probability."*
> — Pierre-Simon Laplace

> *"Anyone who is not shocked by quantum theory has not understood it."*
> — Niels Bohr

Two technologies. Two decades of hype cycles. One stage, and an audience that wants answers.

This chapter is for that audience — and for anyone who needs to make real decisions about quantum AI investments, talent pipelines, and vendor contracts before the hype resolves itself into history.

---

## 8.1 Opening Scene: The Panel No One Won

The ballroom holds 800 people. The stage holds five panelists: a quantum computing startup CEO, a hyperscaler AI research director, a hedge fund quant, a skeptical academic, and a venture capitalist who has written checks to two of the other four. The moderator opens with the question everyone paid \$3,000 in conference registration fees to hear answered:

*"Will quantum computers transform artificial intelligence?"*

The CEO says yes, obviously, and the press release is in your inbox. The AI director says "we're watching closely," which means no, but politely. The quant says the question is wrong — what matters is which specific ML subroutines quantum can accelerate, and by how much, and at what error rate. The academic says two recent papers claiming quantum advantage were quietly withdrawn from arXiv after classical baselines were found. The VC says she's betting on the talent, not the timeline.

Nobody wins. Nobody loses. The audience files out in three factions: convinced, confused, and quietly Googling "dequantization."

This chapter is for the third faction. And for anyone who wants to arrive at the next panel already knowing the answer.

---

## 8.2 The Single Idea

The intersection of quantum computing and artificial intelligence is **simultaneously overhyped and underexplored.**

That is not a hedge. It is a precise description of the current state.

*Overhyped* because: most products marketed as "quantum AI" are classical ML pipelines with quantum decoration — a quantum random number generator here, a quantum-inspired optimization heuristic there, and a press release that does not distinguish between them. The genuinely quantum components, when they exist, typically run on simulators, not hardware. The benchmarks rarely include optimized classical comparisons.

*Underexplored* because: the genuine hybrid opportunities — quantum kernels for high-dimensional classification, quantum sampling for generative models, quantum-enhanced optimization inside ML training loops — are real, grounded in peer-reviewed theory, and early enough that organizations building competency today will have a meaningful head start when the hardware matures.

The skill this chapter develops is not the ability to predict when quantum AI will arrive. It is the ability to **evaluate claims** — to read a vendor pitch, a research paper, or a board-level briefing and ask the right questions. That skill, applied consistently, is worth more than any single technology investment decision.

:::{figure} ../images/ch08-qml-landscape.png
:name: fig-qml-landscape
:alt: QML landscape map showing spectrum from classical ML to full quantum, with NISQ hybrid zone highlighted
:width: 100%

**The QML Landscape.** The spectrum runs from purely classical ML (production-ready today) through NISQ-era hybrid algorithms (limited but real) to full quantum ML (decades away). Most commercial "quantum AI" claims live closer to the left than the marketing suggests. Understanding where a specific technology sits on this spectrum is the first governance skill this chapter teaches.
:::

---

## 8.3 What QML Is — and What It Isn't

### The Hype Problem

::::{prf:definition} Quantum Machine Learning (QML)
:label: def-qml

**Quantum Machine Learning** is the application of quantum computing to machine learning tasks — either by running ML algorithms on quantum hardware, using quantum circuits as trainable models, or leveraging quantum effects (superposition, entanglement, interference) to accelerate specific ML subroutines. It is distinct from *quantum-inspired* ML, which applies mathematical structures derived from quantum mechanics to classical algorithms, and from *AI for quantum*, which uses classical ML to improve quantum hardware calibration or error correction.
::::

The QML hype problem has a precise anatomy. Here is how to recognize it:

**Step 1:** A researcher publishes a quantum algorithm that is theoretically faster than classical algorithms for some ML task. The proof is valid. The speedup is real — under specific assumptions about the input data, the error rates, and the problem structure.

**Step 2:** A startup reads the paper, understands the speedup claim, and misses the assumptions. The press release announces: "Quantum computers are X times faster at machine learning."

**Step 3:** The benchmark they use to demonstrate this advantage is a toy dataset, run on a quantum simulator (not hardware), compared against a classical algorithm that was not tuned.

**Step 4:** Eighteen months later, someone publishes a classical algorithm that matches the speedup, the original paper's assumptions turn out to exclude every real-world dataset of interest, or a dequantization result invalidates the theoretical foundation entirely.

This cycle has repeated, with variations, approximately a dozen times in the QML literature since 2017.

:::{figure} ../images/ch08-hype-vs-reality.png
:name: fig-hype-vs-reality
:alt: Hype vs reality matrix for quantum AI claims showing 2x2 grid of vendor claim strength vs peer-reviewed evidence
:width: 100%

**The Quantum AI Hype-vs-Reality Matrix.** Most commercial quantum AI claims cluster in the upper-right danger zone: high claim strength, limited peer-reviewed evidence. The governance challenge is to identify the upper-left quadrant — genuine opportunities backed by rigorous evidence — and route procurement decisions accordingly. This chapter's five-question filter operationalizes that identification.
:::

### The 9th Grader Test: The QML Hype Problem

**Start with something familiar:** Remember when "big data" meant putting the word "big" in front of any database project? Or when "blockchain" was the answer to every supply chain problem, regardless of whether a shared ledger solved anything? Every powerful technology goes through a phase where the marketing outpaces the reality by years, and the easiest way to sound sophisticated is to attach the hot word to whatever you were already doing.

**The bridge:** QML is in exactly that phase right now. Every classical ML paper is getting a quantum rewrite. Every optimization problem is being pitched as a candidate for "quantum speedup." The tell-tale sign of hype-mode QML is a paper or pitch that claims quantum advantage without comparing against an optimized classical baseline — because the moment you add a well-tuned classical comparison, the advantage often disappears.

**The concept:** This is called the **baseline problem** in QML research. A genuine quantum advantage means the quantum algorithm outperforms the best available classical algorithm — not the obvious classical algorithm, not the naive baseline, but the best. Most QML papers published between 2017 and 2023 did not do this comparison. Some were retracted after independent researchers ran the classical baselines and found parity.

**Where the analogy breaks down:** Unlike "big data" and "blockchain," QML has a genuine theoretical foundation. There are provable quantum speedups for specific problems. The issue is not that quantum ML is fake — it is that the problems where it is provably faster are narrow, and the problems being sold as quantum ML opportunities are usually not in that narrow set.

**Sell the revolution:** The ability to read a QML paper critically — checking for proper classical baselines, verifying statistical significance, examining dataset size and structure, asking whether the advantage survives dequantization — is a \$10 million organizational skill. Every procurement decision, every vendor contract, every R&D investment in quantum AI hinges on exactly this capability. By the time you finish this chapter, you will have it.

:::{admonition} The Baseline Rule
:class: warning

Any QML benchmark that does not include a comparison against a well-tuned, state-of-the-art classical algorithm is not a benchmark. It is a demonstration. Treat it accordingly.
:::

---

## 8.4 Variational Quantum Circuits: The NISQ-Era Bridge

### Why Variational Methods Matter Now

Before quantum computers are fault-tolerant enough to run the full theoretical quantum algorithms that produce provable speedups, they can still contribute through a different route: **variational hybrid algorithms.** These are the NISQ era's most practical tool, and they underpin almost everything genuinely useful happening in quantum ML today.

VQE (Variational Quantum Eigensolver) and QAOA (Quantum Approximate Optimization Algorithm) were introduced in Chapter 7 in the context of molecular simulation and optimization. Here they appear in a new context: as the architectural template for quantum neural networks and quantum-kernel methods.

### The 9th Grader Test: Variational Quantum Circuits

**Start with something familiar:** Imagine you're adjusting the equalizer on a stereo — a set of dials, each controlling a different frequency band. You don't know the perfect setting in advance. So you turn the dials, listen to the result, decide whether it sounds better or worse, and adjust again. After enough iterations, the dials converge on a setting that sounds right. This is gradient descent — the engine that trains every neural network.

**The bridge:** A variational quantum circuit works exactly the same way. Instead of a neural network with weights, you have a quantum circuit with adjustable gate angles (called *parameters*). You run the circuit, measure the output, compare it to what you wanted, and use a classical optimizer to update the parameters. Then you run the circuit again. You repeat until the output converges.

**The concept:** This is called a **Parameterized Quantum Circuit (PQC)** or **variational quantum circuit.** The quantum layer provides expressive power that may be hard to replicate classically — because it operates in an exponentially large Hilbert space. The classical optimizer does what classical computers do well: gradient-based parameter updates. The hybrid loop combines both.

**Where the analogy breaks down:** The dial analogy implies smooth, predictable convergence. Variational quantum circuits face a specific problem called **barren plateaus** — regions of the parameter landscape where the gradient vanishes exponentially with the number of qubits, making training effectively impossible for large circuits. This is a known research challenge, not a minor footnote.

**Sell the revolution:** This is why NISQ-era quantum computers can contribute to ML today — not because they're error-free, but because variational methods tolerate a level of noise that purely algorithmic quantum approaches cannot. VQE and QAOA are the first generation of this approach, already being used in drug discovery (Chapter 7) and combinatorial optimization (Chapter 6). Quantum neural networks, being actively developed at Google, IBM, and dozens of startups, are the next generation. The organizations that understand this architecture now will be the ones who evaluate the next generation of products intelligently.

:::{figure} ../images/ch08-variational-circuits.png
:name: fig-variational-circuits
:alt: Variational quantum circuit diagram showing parameterized gates, classical optimizer loop, and VQE and QAOA examples
:width: 100%

**The Variational Hybrid Loop.** A parameterized quantum circuit (left) generates an output. A classical optimizer (center) computes the gradient and updates the circuit parameters. The loop iterates until convergence. This hybrid architecture is the engine behind VQE, QAOA, and quantum neural networks — and the primary mechanism by which NISQ hardware contributes to ML workloads today.
:::

::::{tab-set}

::::{tab-item} VQE in the ML Context
VQE (Variational Quantum Eigensolver) was designed for chemistry — finding the ground state energy of a molecular Hamiltonian. In the ML context, its relevance is architectural: VQE demonstrated that a quantum circuit could be trained by a classical optimizer to solve a hard optimization problem. Every quantum neural network design inherits this insight. When you see a paper claiming a "quantum neural network achieved X accuracy," the circuit is almost certainly a VQE-style parameterized architecture.
::::

::::{tab-item} QAOA in the ML Context
QAOA (Quantum Approximate Optimization Algorithm) targets combinatorial optimization — the same category as hyperparameter search, neural architecture search, and feature selection in classical ML. A bank using quantum optimization to select the best feature subset for a credit model, or a logistics company using it to prune a neural network architecture, is essentially running QAOA or a QAOA-variant. Current QAOA hardware is small and noisy, limiting practical advantage to small instances — but the architectural principle is sound.
::::

::::{tab-item} Barren Plateaus: The Training Problem
The most significant near-term challenge for variational QML is the **barren plateau** problem (McClean et al., 2018). For randomly initialized variational circuits with many qubits, the gradient of the loss function vanishes exponentially with circuit depth and qubit count. In practice, this means the classical optimizer receives essentially zero training signal — the quantum circuit cannot be trained. Active research into structured initialization, layer-wise training, and problem-specific ansatz design is addressing this, but it remains unsolved for large circuits.
::::

::::

---

## 8.5 Quantum Kernels and Feature Maps

### Where Quantum ML Has Its Best Near-Term Case

If variational circuits are the NISQ era's most versatile quantum ML tool, **quantum kernels** are its most theoretically grounded near-term opportunity. And they are the architecture at the center of this chapter's flagship case study.

### The 9th Grader Test: Quantum Kernels

**Start with something familiar:** Imagine you're trying to find a straight line that separates two groups of data points — red dots and blue dots. But they're hopelessly tangled together in 2D. No straight line exists that separates them cleanly. Here's the trick: if you could lift all those dots into three dimensions — add a third axis based on some mathematical function of the first two — the groups might suddenly become separable by a flat plane. A **kernel function** is exactly that mathematical lifting operation. Support Vector Machines (SVMs) have used this trick for decades with classical kernel functions (polynomial, RBF, sigmoid) to separate data that would be inseparable in its original space.

**The bridge:** A **quantum kernel** replaces the classical kernel function with a quantum circuit. Instead of lifting data into polynomial or radial-basis feature space, the quantum kernel maps data into **Hilbert space** — the state space of a quantum system. The dimension of this feature space grows exponentially with the number of qubits. A 50-qubit quantum kernel maps data into a feature space with \$2^{50}\$ dimensions — more dimensions than there are atoms in the human body.

**The concept:** This exponentially high-dimensional feature space is the quantum kernel's claimed advantage. For classification problems with the right mathematical structure, the decision boundary that no classical kernel can find may exist in that high-dimensional quantum feature space. The key formula: the quantum kernel value between two data points $x$ and $x'$ is the inner product of their quantum state representations — $K(x, x') = |\langle\phi(x)|\phi(x')\rangle|^2$ — where $|\phi(x)\rangle$ is the quantum state produced by the **feature map circuit.**

**Where the analogy breaks down:** The lifting analogy implies that more dimensions is always better. It isn't. An exponentially large feature space also means exponentially harder generalization — it is much easier to overfit. For most real-world datasets, the quantum feature space does not contain a better boundary than a well-tuned RBF kernel already finds. The quantum advantage for kernels is real but narrow: it applies to datasets with intrinsic quantum structure or very specific high-dimensional geometries that remain an active research area to characterize precisely.

**Sell the narrow truth:** For certain high-dimensional classification problems with specific mathematical structure, quantum kernels may find separating boundaries that no classical kernel can find efficiently. The key word is *certain* — and identifying which problems qualify is an active research area worth watching. More immediately actionable: quantum kernels are the most experimentally tractable QML method today. IBM, Google, and academic groups have run quantum kernel experiments on real hardware. The results are mixed — but the methodology is sound, the theory is clean, and the experimental program is progressing. Organizations working with high-dimensional feature data in finance, genomics, or materials science should follow this research closely.

:::{figure} ../images/ch08-quantum-kernels.png
:name: fig-quantum-kernels
:alt: Quantum kernel concept diagram showing data lifted from 2D tangled space through quantum feature map to high-dimensional Hilbert space with clear separation boundary
:width: 100%

**Quantum Kernels: Lifting Data into Hilbert Space.** A classical kernel lifts data into higher-dimensional polynomial or radial-basis space. A quantum kernel uses a quantum circuit — the **feature map** — to lift data into Hilbert space, whose dimension grows exponentially with qubit count. For problems with the right mathematical structure, this enables decision boundaries that classical kernels cannot efficiently approximate. The challenge: most real-world datasets do not have that structure.
:::

### Quantum Kernels in Practice: What the Experiments Show

The experimental record on quantum kernels is instructive precisely because it is mixed.

In 2021, Havlíček et al. published a landmark paper in *Nature* demonstrating that quantum feature maps can generate kernel functions that are hard to compute classically — a necessary (though not sufficient) condition for quantum advantage. The result was theoretically sound and widely cited.

In 2022, Kübler et al. published a sobering follow-up showing that for typical ML datasets, quantum kernels exhibit **concentration** — their values cluster around a constant, providing essentially no discriminative signal. The exponential feature space turns out to be a curse as much as a blessing when the data structure doesn't match it.

In 2023, multiple groups demonstrated quantum kernel experiments on real IBM and IonQ hardware, reporting modest accuracy improvements on small synthetic datasets. Every paper included the same caveat: the advantage disappeared when the dataset grew beyond a few hundred samples.

The pattern is consistent: quantum kernels work on small, structured datasets that may be specifically designed to showcase them. On standard ML benchmarks — UCI repository datasets, real financial time series, genomic data at production scale — the best classical kernels are competitive or superior.

This is not a dismissal of quantum kernels. It is the honest experimental record as of 2025. Watch for papers that change this pattern.

---

## 8.6 Quantum Sampling and Generative Models

### A Different Kind of Quantum Advantage

While quantum kernels target classification, quantum sampling targets a different ML workload: **generative modeling.** The question here is not "which class does this data point belong to?" but "how do I generate new samples that look like the training data?"

Classical generative models — GANs, VAEs, diffusion models — are among the most computationally intensive workloads in ML. Training a large diffusion model can consume millions of dollars of GPU compute. The training bottleneck is the repeated computation of complex probability distributions over high-dimensional spaces.

Quantum computers have a natural affinity for sampling. A quantum circuit, when measured, naturally samples from a probability distribution that is exponentially difficult to compute classically — this is the foundational claim behind Google's quantum supremacy experiments (Chapter 1). If that sampling capability can be harnessed to accelerate the estimation of probability distributions inside generative model training loops, a genuine hybrid speedup becomes plausible.

The proposed architecture — a **Quantum Boltzmann Machine (QBM)** or a **Quantum Generative Adversarial Network (QGAN)** — uses quantum circuits to represent the latent distribution of a generative model, with classical layers handling the output generation.

The honest assessment: as of 2025, this remains largely theoretical. The circuits required for meaningful quantum advantage in generative modeling exceed current NISQ hardware by significant margins. But the theoretical case is stronger here than in most other QML domains — because the application directly leverages quantum sampling, which is the most defensible near-term quantum capability.

The hedge fund experiment in Section 8.9 explores what an early attempt at quantum-enhanced generative modeling actually looked like in practice.

:::{admonition} Quantum Sampling vs. Quantum Speedup
:class: note

These are not the same thing. A quantum computer can naturally sample from distributions that are hard to compute classically — this is a **sampling advantage.** Whether that sampling advantage translates into a practical ML speedup depends on whether the hard-to-sample distribution is actually the bottleneck in the ML training loop. For most current generative models, it is not. For future architectures specifically designed around quantum sampling, it may be.
:::

---

## 8.7 An Honest Assessment of the QML Literature

### What Survived Peer Review, What Didn't

The QML research literature, evaluated honestly, looks like most nascent fields: a mix of genuine advances, incremental results dressed as breakthroughs, methodological mistakes made in good faith, and a small number of papers that did not survive contact with rigorous replication.

:::{figure} ../images/ch08-qml-literature-audit.png
:name: fig-literature-audit
:alt: QML literature audit scorecard showing percentage of papers passing basic rigor checks including classical baseline, statistical significance, dataset size, and independent replication
:width: 100%

**The QML Literature Audit.** A 2023 meta-analysis of 100 QML papers found that fewer than 40% included a comparison against a well-tuned classical baseline. Fewer than 20% reported results with confidence intervals. Independent replication rates are lower still. This is not evidence that QML is fraudulent — it is evidence that the field is young, the publication incentives favor positive results, and the governance instinct to demand rigorous baselines has not yet been institutionalized.
:::

The key methodological failures that recur across the retracted and heavily criticized papers are:

**1. Unfair classical baselines.** Comparing a quantum algorithm to a naive classical implementation instead of the best available. A quantum SVM that outperforms a linear SVM does not demonstrate quantum advantage over a tuned RBF kernel SVM.

**2. Small synthetic datasets.** Quantum circuits currently handle tens to low hundreds of features. Experiments on 2D or 4D synthetic datasets are existence proofs, not scalability demonstrations.

**3. Missing statistical rigor.** Single-run results reported as definitive. No confidence intervals. No cross-validation. No multiple seeds. Results that would not pass a standard ML peer review.

**4. Simulator vs. hardware gap.** Experiments run on classical simulators of quantum circuits, not actual quantum hardware. Simulators do not have noise — they're classical computers pretending to be quantum. Results on simulators are not evidence of hardware performance.

**5. Ignoring barren plateaus.** Training curves that look clean on 4 qubits scale catastrophically on 20 qubits due to the barren plateau problem — a problem some papers acknowledge in footnotes and many do not address at all.

The notable retractions and corrections in the QML space as of 2025 include several papers on quantum neural networks claiming image classification advantages over CNNs, where subsequent analysis showed the quantum architecture was trained on the same image classes it was tested on (data leakage), and a series of quantum reinforcement learning claims where the benchmark environments were designed specifically to have the mathematical structure quantum circuits could exploit.

:::{admonition} The Rigorous QML Papers Worth Reading
:class: tip

The following papers represent the honest end of the QML literature: Havlíček et al. (2019) on quantum kernel estimation (*Nature*), Cerezo et al. (2021) on variational quantum algorithms (*Nature Reviews Physics*), Huang et al. (2021) on quantum advantage in learning from experiments (*Science*), and Kübler et al. (2022) on the concentration problem for quantum kernels (*NeurIPS*). Each acknowledges limitations explicitly. Each includes classical baselines. Read the limitations sections first.
:::

---

## 8.8 Dequantization: The Term Every Leader Must Know

### When Classical Algorithms Catch Up

::::{prf:definition} Dequantization
:label: def-dequantization

**Dequantization** is the process of developing classical algorithms that match the asymptotic performance of quantum algorithms, eliminating the claimed quantum speedup. A dequantized result does not mean the quantum algorithm was wrong — it means the quantum advantage was not fundamental, because the classical algorithm's earlier inefficiency was not inherent but algorithmic. The term was popularized following Ewin Tang's 2019 result showing that a classical algorithm with \$\tilde{O}(\sqrt{n})\$ complexity could match the quantum recommendation system algorithm of Kerenidis and Prakash (2016), which had claimed an exponential speedup.
::::

### The 9th Grader Test: Dequantization

**Start with something familiar:** Imagine a magician claims he can produce a rabbit from a hat using a secret quantum trick. The audience is amazed. Nobody can figure out how he did it. He charges a premium for his quantum hat performances. Then a skeptical graduate student named Ewin sits in the front row, watches very carefully, and realizes: the trick does not require quantum magic at all. She goes home and reproduces the rabbit using a completely classical method — a new way of sampling from probability distributions that is fast enough to match what the quantum circuit was doing. The magician's act still works. The rabbit still appears. But the quantum advantage claim is gone.

**The bridge:** This is literally what happened in 2019. Kerenidis and Prakash published a quantum algorithm for recommendation systems (like Netflix's "you might also like...") in 2016 claiming exponential speedup — a celebrated result that helped launch the quantum ML field. In 2019, Tang showed that a classical algorithm using a technique called **sampling-based low-rank approximation** matched the quantum speedup. The quantum algorithm's advantage had depended on a classical algorithm that was inefficient not because of fundamental limits, but because nobody had thought carefully enough about classical sampling methods.

**The concept:** Dequantization. The formal insight is this: many proposed quantum speedups work by efficiently sampling from a probability distribution. If a classical algorithm can also efficiently sample from that distribution — using clever randomized algorithms — the quantum advantage evaporates. The lesson is not that quantum algorithms are useless. It is that **quantum advantage claims require proof that no efficient classical algorithm exists** — not just proof that the obvious classical algorithm is slow.

**Where the analogy breaks down:** The magician analogy implies deliberate deception. Most dequantized quantum algorithms were published in good faith. The researchers genuinely believed no fast classical algorithm existed. The problem was incomplete knowledge of classical algorithm capabilities, not dishonesty. The Tang result was a genuine scientific contribution — it advanced both quantum computing theory (by tightening the conditions for quantum advantage) and classical algorithm design (by creating new randomized sampling techniques).

**Sell the leadership value:** Every executive who knows the word "dequantization" has a superpower in vendor meetings. When a vendor claims quantum advantage, the right question is not "how fast is your quantum algorithm?" It is: **"Has anyone tried matching it classically?"** This question alone will filter 80% of quantum AI marketing claims. The vendor who cannot answer it either has not read the dequantization literature (a problem) or has, and knows the answer is no (a much stronger signal). After Tang's 2019 result, IBM and Google researchers published updated assessments of which quantum ML speedups survived the dequantization test. The list is shorter than the marketing materials suggest — and it is the list that matters.

:::{figure} ../images/ch08-dequantization-concept.png
:name: fig-dequantization
:alt: Dequantization concept diagram showing quantum algorithm speedup claim on left, classical algorithm matching performance on right, with magnifying glass labeled dequantization check and Tang 2019 reference
:width: 100%

**Dequantization: The Quantum Advantage Filter.** The Tang (2019) result on recommendation systems demonstrated that a celebrated quantum speedup could be matched by a classical algorithm using randomized sampling. The lesson for procurement: quantum advantage claims require proof that no efficient classical sampling algorithm exists — not just evidence that the obvious classical approach is slow. "Has this been tested against modern classical baselines?" is the \$10 million question.
:::

### The Dequantization Literature: Where Things Stand

After Tang's result, a wave of dequantization research examined the quantum ML speedup claims most actively marketed. The findings, as of 2025:

- **Quantum recommendation systems:** Dequantized. Classical randomized algorithms match asymptotic performance.
- **Quantum principal component analysis (qPCA):** Dequantized. Tang (2021) extended the approach.
- **Quantum linear systems (HHL algorithm):** Partially — the HHL algorithm retains a speedup in specific regimes, but the practical conditions (quantum RAM access, specific matrix structure) severely limit real-world applicability.
- **Quantum kernel methods:** Not dequantized, but with important caveats — the quantum advantage requires specific data structure that may not apply to standard ML datasets.
- **Quantum sampling for generative models:** No general dequantization result — the strongest near-term case for quantum ML advantage.
- **Variational QML (VQE, QAOA, QNN):** Not a dequantization target — these are heuristic methods, not provable speedup algorithms.

The pattern: the most theoretically rigorous quantum speedup claims (HHL, qPCA, recommendation systems) are the ones most vulnerable to dequantization. The messier, more heuristic NISQ methods are not dequantizable in principle because they never claimed provable speedups to begin with.

---

## 8.9 Industry Snapshots

### Snapshot 1: The Credit-Scoring Quantum Kernel Experiment

In 2023, a mid-sized regional bank piloting quantum computing in its risk analytics division ran what it described internally as its "quantum kernel proof of concept." The team had read the Havlíček et al. (2019) paper, had access to an IBM Quantum Premium instance through a cloud agreement, and had a real credit-scoring problem: classifying loan applicants into default and non-default categories using 14 engineered features.

The classical baseline was an SVM with an RBF kernel, trained on a dataset of approximately 8,000 historical applications. The baseline achieved 87.2% accuracy with a well-tuned hyperparameter grid search. The quantum kernel model — using a ZZFeatureMap circuit with 6 qubits on IBM Falcon hardware — achieved 89.3% accuracy on the same train/test split after 12 weeks of implementation work.

The 2.1-percentage-point improvement was real. The team wrote an internal memo calling it a "validated quantum advantage in a production-relevant financial classification task." The memo went to the CTO. The CTO presented at a fintech conference. The story was picked up by three trade publications.

Eighteen months later, a machine learning engineer on the same team — who had joined the bank six months after the original experiment — ran a routine audit of the baseline comparison. She noticed the RBF kernel in the original experiment had been tuned with a grid of 12 values for the regularization parameter C, but had not tuned the kernel bandwidth γ jointly with C. She ran a proper joint grid search. The tuned RBF kernel achieved 89.1% accuracy — within noise of the quantum kernel result.

The gap had closed. Not because the quantum kernel got worse, but because the classical baseline had been under-tuned. The quantum advantage was not a property of quantum mechanics. It was a property of an incomplete hyperparameter search.

:::{figure} ../images/ch08-credit-scoring-case.png
:name: fig-credit-scoring
:alt: Timeline case study of bank quantum kernel credit scoring pilot showing initial quantum advantage claim and later classical catch-up after proper baseline tuning
:width: 100%

**The Credit-Scoring Timeline.** 2023: quantum kernel achieves 89.3% accuracy, 2.1 points above the classical baseline. 2025: properly tuned classical RBF kernel achieves 89.1% — within measurement noise of the quantum result. The lesson: quantum advantage comparisons require optimized classical baselines, not merely competent ones.
:::

This story is not told to embarrass the bank or dismiss the experiment. The team did serious, careful work. The 2023 experiment was not fraudulent — it was incomplete in a way that is extremely common in both the academic and enterprise QML literature. The lesson is structural: **quantum advantage comparisons require classical baselines that are not merely competent but optimal.** And optimal classical baselines take as much engineering rigor as the quantum implementation itself.

The bank's experiment, honestly described, is a success: it produced a valuable result (the quantum kernel is competitive), it generated institutional knowledge about quantum kernel implementation, and the follow-up classical tuning exercise revealed a tuning gap in the team's classical ML practice. That is useful intelligence — if the organization learns from it correctly.

### Snapshot 2: Retracted QML Papers and the Lessons They Leave

The QML literature's retraction record is sparse by the standards of a field attracting billions in investment — which is itself a governance concern, suggesting insufficient replication pressure rather than exceptional rigor. The most instructive cases involve not formal retractions but substantial post-publication corrections and follow-ups that reversed the main conclusion.

**Case A: Quantum neural networks vs. CNNs on image classification (2022).** A paper claiming that a quantum convolutional neural network (QCNN) outperformed a classical CNN on a small image classification task was challenged by three independent groups within six months of publication. The challenges identified data preprocessing that inadvertently leakage-encoded class labels into the quantum feature map — the quantum circuit was essentially reading the answer from the preprocessing, not learning it. The original authors published a correction acknowledging the leakage. The advantage disappeared.

**Case B: Quantum reinforcement learning with exponential speedup (2021).** A paper claiming exponential speedup in reinforcement learning used an environment specifically constructed to have the mathematical structure quantum circuits exploit efficiently. Independent researchers who tested the quantum algorithm on standard OpenAI Gym benchmarks found no advantage. The paper was not retracted — its theoretical claims are technically correct for the environments it studied — but it produced zero practical guidance for real RL applications.

The pattern in both cases: the advantage was real in a narrow experimental context that was chosen to favor the quantum approach. The generalization to practical ML was not tested and did not hold.

### Snapshot 3: A Hedge Fund's Quantum Generative Model Experiment

In 2024, a quantitative hedge fund with a substantial ML research team attempted to use a quantum-enhanced generative model to improve the quality of synthetic financial time series for backtesting. The motivation was sound: the fund's classical generative models produced synthetic price series with statistical properties that diverged from historical data in tail behavior, creating biased backtests. They hypothesized that a quantum Boltzmann machine, running on a D-Wave Advantage system (which specializes in sampling from Boltzmann distributions through quantum annealing), might capture the fat-tailed behavior of financial returns more naturally.

The experiment ran for four months. The D-Wave system did produce samples with slightly heavier tails than the classical VAE baseline. Statistical tests found the difference significant at the 5% level. The team prepared an internal report recommending further investigation.

The conclusion they did not reach — but which a dequantization-aware reviewer would have raised immediately: quantum annealing on D-Wave hardware samples from a specific class of Boltzmann distributions defined by the hardware graph structure. The hardware's native distribution does not cleanly correspond to the distribution of financial returns. The tail behavior improvement was likely a sampling artifact of the hardware's connectivity structure, not a principled modeling of financial return distributions.

The experiment was valuable exploration. The conclusion it supports is: "quantum annealing may produce interesting sampling properties for certain financial distributions — investigate further with explicit comparison to classical Boltzmann sampling methods." It does not support: "quantum generative models outperform classical generative models for financial time series."

---

## 8.10 Talent Implications for AI-Mature Organizations

### The Orchestra Analogy

::::{prf:definition} Quantum ML Literacy
:label: def-qml-literacy

**Quantum ML literacy** is the organizational capability to understand, evaluate, implement, and critically assess quantum machine learning methods. It is distinct from quantum computing expertise (hardware, error correction, circuit design) and from classical ML expertise (deep learning, statistical modeling, production ML systems), though it draws on both. An organization with quantum ML literacy can read a QML research paper critically, evaluate vendor claims, identify which internal ML workloads are candidates for quantum acceleration, and build the talent pipeline to act on those opportunities when hardware matures.
::::

### The 9th Grader Test: Why AI-Mature Orgs Should Care

**Start with something familiar:** Imagine you've just hired the world's best classical orchestra. They're extraordinary — they can play anything in the classical repertoire with flawless precision. The question arrives: there is a new instrument called the quantum violin. Nobody fully knows how to play it yet. Some people say it will eventually produce sounds no classical instrument can. Others say it's just a very expensive prototype. The question for your conductor is not "do we replace the orchestra?" It is: "Do we need at least one person on staff who can tune this instrument and tell us whether it's ready to join the performance?"

**The bridge:** Quantum ML is not a replacement for classical ML. Your GPU cluster, your data pipelines, your ML engineers, your model deployment infrastructure — none of that becomes obsolete when quantum ML matures. What changes is that certain ML workloads — high-dimensional kernel methods, combinatorial optimization of ML training loops, sampling for generative models — may become significantly faster on quantum hardware. The organizations that will capture that advantage are the ones that already understand which of their ML workloads are candidates, and have people who know how to evaluate whether a quantum ML solution is genuine.

**The concept:** This is the **quantum literacy pipeline problem.** Quantum ML talent is trained in quantum mechanics, quantum information theory, variational algorithms, and ML — a combination that takes 3–5 years to develop from a classical ML foundation. The universities producing this talent are still small and concentrated. The companies with this talent now will have structural advantages in the 2027–2030 window when NISQ hardware becomes reliable enough for production quantum ML pilots.

**Where the analogy breaks down:** The orchestra analogy implies you can simply hire one quantum specialist and be covered. Organizational quantum literacy requires depth: at minimum, a quantum ML specialist who can evaluate vendor claims, at least two to three classical ML engineers with quantum literacy enough to collaborate on hybrid implementations, and leadership that can ask the right questions when a vendor pitches "quantum advantage."

**Sell the revolution:** The organizations that will win the quantum-AI decade are the ones building quantum literacy into their ML teams NOW — not because quantum ML is ready for production, but because the talent takes years to develop and the window for being early is closing. The cost of building this capability today is a fraction of the cost of being caught flat-footed when the hardware matures. The hedge fund that understood D-Wave's sampling properties before running a \$500K experiment would have designed a better experiment. The bank that understood dequantization risk before its 2023 QML pilot would have included a proper classical baseline from day one.

:::{figure} ../images/ch08-talent-framework.png
:name: fig-talent-framework
:alt: Three-tier talent pyramid for quantum ML showing quantum literacy for all ML engineers at base, quantum ML specialists in middle, quantum research leads at top with timeline showing 3-5 years to develop each tier
:width: 100%

**The Quantum ML Talent Framework.** Three tiers of quantum competency, each requiring substantial development time. The base tier — quantum literacy for all ML engineers — is achievable in 6–12 months and provides immediate governance value. The upper tiers require years of development. Organizations that start now will have meaningful competitive advantages in the 2027–2030 production-readiness window.
:::

### Tooling Landscape for QML in 2025

::::{tab-set}

::::{tab-item} Qiskit Machine Learning (IBM)
IBM's open-source quantum ML framework, built on Qiskit. Provides quantum kernel estimators, quantum neural networks, variational quantum classifiers, and integration with scikit-learn. Most experimentally validated QML library as of 2025. Actively maintained. Best for: quantum kernel experiments, hybrid variational models, academic research. **Limitation:** Circuit depth constraints from current IBM hardware limit practical feature dimensions.
::::

::::{tab-item} PennyLane (Xanadu)
Framework-agnostic QML library supporting Qiskit, Cirq, TensorFlow Quantum, and multiple hardware backends. Notable for its automatic differentiation through quantum circuits — enables gradient-based training of quantum circuits using familiar ML tooling. Best for: quantum neural networks, variational algorithms, hardware-agnostic research. **Limitation:** More complex API than Qiskit ML; steeper learning curve.
::::

::::{tab-item} TensorFlow Quantum (Google)
Google's integration of quantum circuits with TensorFlow. Enables hybrid quantum-classical models using TensorFlow's training infrastructure. Best for: organizations already using TensorFlow with Google Cloud; quantum ML research on Cirq backend. **Limitation:** Google-specific; less hardware flexibility than PennyLane.
::::

::::{tab-item} Classical Baselines: Your First Stop
Before any QML experiment, implement and tune classical baselines using scikit-learn, XGBoost, or PyTorch. The classical baseline is not the starting point you beat — it is the result you spend 80% of your engineering effort optimizing before you even write quantum code. This is the single most important practical lesson from the QML literature. If you cannot beat a properly tuned classical baseline with quantum, you have not demonstrated quantum advantage. You have demonstrated that your classical baseline needed more work.
::::

::::

---

## 8.11 Governance Framework: Evaluating Quantum-AI Vendor Claims

### The Five-Question Filter

Every quantum-AI vendor claim can be evaluated with five questions. Organizations that make these questions part of their standard procurement process will eliminate the vast majority of quantum AI marketing noise before it reaches the decision stage.

:::{figure} ../images/ch08-governance-checklist.png
:name: fig-governance-checklist
:alt: Governance checklist flowchart showing five procurement checkpoints: peer-reviewed benchmarks, optimized classical baseline, dequantization test, statistical significance, and independent replication
:width: 100%

**The Quantum AI Procurement Filter.** Five questions that filter quantum AI vendor claims from genuine quantum advantage evidence. Any claim that cannot pass all five filters should be treated as unvalidated marketing until evidence is provided. Organizations that make this filter part of standard procurement practice will save significant R&D budget and avoid the baseline problem that affected the credit-scoring case study.
:::

```{list-table} The Five-Question Governance Filter
:header-rows: 1
:widths: 5 30 35 30

* - #
  - Question
  - What to Look For
  - Red Flag
* - 1
  - Is there peer-reviewed evidence?
  - Paper in Nature, Science, Physical Review, NeurIPS, ICML, or equivalent. Not a blog post, not a press release, not a conference poster.
  - "Our internal benchmarks show..." without a citable paper.
* - 2
  - Was the classical baseline optimized?
  - Evidence that the classical comparison used hyperparameter tuning, cross-validation, and state-of-the-art algorithms — not the obvious baseline.
  - Classical baseline described in one sentence with no tuning details.
* - 3
  - Has dequantization been considered?
  - Vendor can explain why no efficient classical sampling algorithm achieves the same result.
  - Vendor has not heard of Tang (2019) or the dequantization literature.
* - 4
  - Is the statistical evidence sufficient?
  - Multiple seeds, confidence intervals, dataset size adequate for the feature dimensionality, paired significance tests.
  - Single result, no confidence interval, dataset of fewer than 1,000 samples.
* - 5
  - Has it been replicated independently?
  - At least one independent group (different university, different lab) has reproduced the core result.
  - "We're the only ones who have run this experiment."
```

### The Governance Process in Practice

The five questions are necessary but not sufficient. They filter out bad claims. A governance process for evaluating genuine quantum-AI opportunities also needs a **positive** component: a framework for identifying which internal ML workloads are legitimate candidates for quantum acceleration.

```{mermaid}
flowchart LR
    A[Identify ML workload] --> B{Feature dimension\n> 20?}
    B -- No --> C[Classical ML only\nno quantum case]
    B -- Yes --> D{Optimization\nbottleneck?}
    D -- No --> E{Kernel method\ncurrently used?}
    D -- Yes --> F[QAOA/VQE\nwatch list]
    E -- No --> G[Low priority\nfor QML]
    E -- Yes --> H[Quantum kernel\ncandidate — pilot eligible]
    F --> I{Hardware available\nfor pilot?}
    H --> I
    I -- No --> J[Monitor hardware\nprogress quarterly]
    I -- Yes --> K[Run pilot with\noptimized classical\nbaseline first]
```

The workflow above reflects a key governance principle: **the quantum pilot does not begin until the classical baseline is maximally optimized.** This is the lesson of the credit-scoring case study. Maximally optimized classical baselines serve two functions: they raise the bar the quantum approach must beat (filtering marginal advantages), and they improve the organization's classical ML practice regardless of the quantum outcome.

:::{admonition} The Governance Mandate
:class: important

Any quantum AI pilot proposal submitted to leadership should include, as a required attachment, a document titled "Classical Baseline Optimization Plan" that specifies: which classical algorithms will be compared, what hyperparameter tuning methodology will be used, what compute budget will be allocated to the classical optimization, and what minimum performance gap is required to declare quantum advantage. If this document cannot be written before the pilot begins, the pilot is not ready to begin.
:::

---

## 8.12 Flagship Case Study: A Financial Services Firm's Quantum Kernel Credit-Scoring Pilot

*This case study is graded. See assessment criteria in the course syllabus.*

### Situation

FinCorp Capital (a composite based on documented public and industry cases) is a mid-sized regional bank with a mature ML-driven credit underwriting operation. Its classical credit scoring pipeline, built on gradient-boosted decision trees with a secondary SVM model for edge cases, processes approximately 3,000 loan applications per month. The ML team has 14 engineers and a solid culture of experimentation.

In early 2023, the Chief Analytics Officer read IBM's quantum kernel white paper and scheduled a meeting with the quantum computing team at the bank's primary cloud vendor. The vendor's pitch: quantum kernels could improve classification accuracy for high-dimensional credit features, reducing default rates. Projected value: \$2.3 million in annual default cost reduction for a 2-percentage-point accuracy improvement.

### The Quantum Angle

The team identified the secondary SVM model — which handled the 15% of applications that the gradient-boosted model flagged as borderline — as the pilot target. The SVM was already using a kernel method, making it a natural quantum kernel candidate. The feature set for these borderline cases included 14 engineered features: credit history length, debt-to-income ratio, payment volatility metrics, macro indicators, and behavioral signals.

The quantum kernel implementation used IBM Qiskit Machine Learning with a ZZFeatureMap circuit on 6 qubits, run on an IBM Falcon processor through the IBM Quantum Premium service. Implementation took 12 weeks and required two engineers who had completed IBM's Qiskit certification.

### Decisions Made

The team made three consequential decisions that shaped the outcome:

1. **Baseline comparison:** The classical SVM baseline used the hyperparameter settings from the existing production model, which had been tuned 18 months earlier but not recently re-tuned. The regularization parameter C was tuned over a 1D grid; the bandwidth γ was set to the scikit-learn default of `scale` rather than jointly optimized.

2. **Dataset size:** The pilot used 1,200 training samples (the borderline cases from 12 months of applications). This was considered sufficient for an SVM model but is a relatively small sample for drawing robust conclusions about a 2.1-percentage-point difference.

3. **Reporting:** The positive result was reported to the CTO without a confidence interval on the accuracy difference. The 2.1-percentage-point advantage was treated as a point estimate, not a range.

### Measured Outcome

- Classical SVM (production settings): 87.2% accuracy
- Quantum kernel SVM: 89.3% accuracy
- 18-month follow-up, tuned classical SVM: 89.1% accuracy
- The quantum advantage of 2.1 percentage points reduced to a statistically non-significant 0.2 percentage points after classical re-tuning

The pilot cost \$340,000 in cloud quantum compute credits, engineering time, and external consulting. The classical re-tuning exercise cost approximately \$8,000.

### Open Questions for Analysis

:::{admonition} Graded Analysis Questions
:class: important

1. **Was the bank's quantum kernel pilot a failure, a success, or a source of useful intelligence?** Defend your classification with specific reference to the decisions made and the outcomes measured.

2. **What governance process should have been required before the pilot was approved?** Design the "Classical Baseline Optimization Plan" (see Section 8.11) that this pilot needed.

3. **The vendor who sold the quantum compute access knew that the classical baseline had not been jointly optimized. What disclosure obligations, if any, should quantum AI vendors have regarding dequantization risk and baseline optimization requirements?**

4. **How should the bank's procurement team evaluate the next quantum AI vendor that pitches a similar architecture?** Write the five questions they should ask before approving any budget.

5. **What does a 0.2-percentage-point accuracy difference on a 1,200-sample dataset with no confidence interval actually tell you?** Calculate the approximate confidence interval using a standard binomial proportion test, and assess whether the original 89.3% vs. 87.2% comparison was statistically significant.
:::

---

## 8.13 Productive-Struggle Problem

### Three Vendor Claims: Rank by Credibility

A procurement team receives three one-page executive summaries from quantum AI vendors, each claiming to accelerate a specific ML workload. Your task: rank these claims from most to least credible, and for each, name the **single experiment** that would definitively falsify the advantage claim.

**Vendor A — QuantumKernelCo:** "Our quantum kernel SVM achieves 94.3% accuracy on credit default prediction, compared to 91.7% for the best classical SVM, on a dataset of 1,500 samples with 8 features. Experiment run on IBM Quantum hardware, single seed, no confidence interval provided. Classical baseline used scikit-learn default hyperparameters."

**Vendor B — QuantumGenAI:** "Our quantum Boltzmann machine generates synthetic financial time series with tail statistics matching historical S&P 500 returns, outperforming classical VAE and GAN baselines on KL-divergence and tail index metrics. Experiment run on D-Wave Advantage hardware. Results validated by three independent financial statisticians. Paper under review at *Journal of Computational Finance.* Dataset: 20 years of daily returns, 5 seeds, full confidence intervals provided."

**Vendor C — VariationalVentures:** "Our variational quantum optimizer reduces hyperparameter search time for deep neural network training by 37% versus random search, 28% versus Bayesian optimization, using a QAOA-based approach on a 12-qubit simulator. Results on three different neural network architectures. Paper published in *Physical Review Applied* (2024). No hardware experiments — simulator only."

:::{dropdown} Analysis and Answers

**Ranking (most to least credible): B > C > A**

**Vendor B (Most credible):** Despite operating on specialized hardware (D-Wave), the Vendor B claim has the strongest methodological foundation. The experiment uses a real hardware backend (not a simulator), a meaningful dataset (20 years of historical returns), multiple seeds, confidence intervals, and independent validation. The paper is under peer review. Key weaknesses: D-Wave's native distribution may not match financial return distributions for principled reasons (the Snapshot 3 issue), and KL-divergence on marginal distributions can look favorable even when joint temporal structure is wrong. **Falsification experiment:** Run the same quantum Boltzmann machine against a classical Boltzmann machine (restricted or full, tuned for the same distribution) using exact same hardware and identical statistical methodology. If the classical Boltzmann machine matches on tail index and KL-divergence, the advantage is not quantum.

**Vendor C (Middle):** The QAOA hyperparameter search result is plausible — QAOA targets exactly this combinatorial optimization type. The methodology is above average: three architectures, comparison against Bayesian optimization, published paper. The critical weakness is **simulator only.** QAOA on real hardware with noise performs significantly worse than on a simulator, and 12 qubits is small enough that the classical optimizer may be doing most of the work. **Falsification experiment:** Run the same QAOA optimizer on real quantum hardware (IBM or IonQ, comparable qubit count) on the same three architectures, same hyperparameter spaces. If the advantage disappears or reverses on hardware, the simulator result does not justify production investment.

**Vendor A (Least credible):** Multiple red flags stack. Single seed (no confidence intervals). Default classical hyperparameters (not tuned). 8-feature dataset is small enough that the quantum kernel is only marginally in its regime of potential advantage. No paper cited. The 2.6-percentage-point gap is suspiciously similar to the credit-scoring case study — it could easily disappear with proper classical tuning. **Falsification experiment:** Re-run the classical SVM with joint grid search over C and γ, cross-validated, five seeds. If the gap closes to under 1 percentage point, the quantum advantage claim fails the minimum credibility threshold.

**The overarching lesson:** Credibility correlates with methodological rigor, not with boldness of claim. Vendor B makes a more conservative claim and provides more evidence. Vendor A makes a stronger-sounding claim and provides less. The procurement team that confuses claim strength with claim credibility will consistently make poor quantum AI investment decisions.
:::

---

## 8.14 Module-Level Outcomes

By completing this chapter, you can:

::::{card-carousel} 2

:::{card} Outcome 1
:class-body: text-center

**Distinguish QML from Classical ML with Quantum Sampling**

Explain the difference between genuine quantum machine learning (quantum circuits as model components), quantum-augmented classical ML (quantum sampling in classical training loops), and quantum-inspired ML (classical algorithms using quantum-derived math). Identify which category a given product or paper represents.
:::

:::{card} Outcome 2
:class-body: text-center

**Evaluate VQE, QAOA, and Near-Term Value**

Describe the variational hybrid loop and explain why NISQ-era quantum computers can contribute to ML through parameterized circuits despite high error rates. Identify the barren plateau problem and explain its practical implications for trainable quantum circuits.
:::

:::{card} Outcome 3
:class-body: text-center

**Analyze Talent and Tooling Implications**

Design a three-tier quantum ML talent development roadmap for an AI-mature organization. Recommend a tooling strategy (Qiskit ML, PennyLane, or TensorFlow Quantum) appropriate to a given organizational context and identify the classical baseline rigor required before any quantum pilot.
:::

:::{card} Outcome 4
:class-body: text-center

**Critique QML Claims Against the Literature**

Apply the baseline rule, the statistical rigor checklist, and the dequantization test to evaluate any QML claim. Identify the methodological failures that produced the most cited QML retractions and apply that knowledge to novel vendor claims.
:::

:::{card} Outcome 5
:class-body: text-center

**Recommend a Governance Process**

Design and defend a five-question quantum AI procurement filter. Write a Classical Baseline Optimization Plan for a given ML workload. Apply the flowchart governance model to determine whether a specific internal ML workload is a legitimate candidate for a quantum pilot.
:::

::::

---

## 8.15 Lab 8 — Quantum Kernels vs. Classical Kernels

**Format:** Hosted Qiskit Machine Learning notebook — no local installation required  
**Time:** ~60 minutes  
**Access:** Qiskit Learning Platform (quantum-computing.ibm.com/learning) or IBM Quantum Lab

### Lab Instructions

**Part 1: Baseline Classical Kernel (20 min)**

1. Load the provided synthetic 2D dataset (Dataset A: two interleaved moons, 200 samples)
2. Train an SVM with an RBF kernel using scikit-learn
3. Use a 5-fold cross-validated grid search over C = [0.1, 1, 10, 100] and γ = [0.01, 0.1, 1, 10]
4. Record: best hyperparameters, mean cross-validation accuracy, test set accuracy

**Part 2: Quantum Kernel SVM (25 min)**

1. Implement a ZZFeatureMap quantum kernel using Qiskit Machine Learning's `QuantumKernel` class (2 qubits, 2 repetitions)
2. Train an SVM using the quantum kernel on Dataset A
3. Record: training time, test set accuracy
4. Compare to the classical RBF result

**Part 3: Dataset Swap (15 min)**

1. Swap to Dataset B (provided): a large-sample dataset (800 samples) with 8 features, no intrinsic quantum structure
2. Re-run both the classical SVM (with the same tuning methodology) and the quantum kernel SVM
3. Record: accuracy, training time
4. Observe: the quantum kernel likely performs at or below the classical result

**Deliverable:** A one-page critical analysis answering: Was the quantum kernel's performance on Dataset A a genuine quantum advantage, a contrived example, or a tie? What does the Dataset B result tell you about the generalizability of quantum kernel advantages? If a vendor showed you only the Dataset A result, what questions would you ask?

---

## 8.16 Lab 8 — Optional Advanced: Benchmarking QML Honestly

**Format:** Python 3 notebook, local installation or Google Colab  
**Time:** ~3 hours  
**Prerequisites:** scikit-learn, Qiskit Machine Learning, numpy, scipy  

<a href="https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch08-qml-benchmark.ipynb" target="_blank">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="margin-bottom: 1rem;"/>
</a>

### Lab Instructions

**Dataset:** UCI Breast Cancer Wisconsin dataset (569 samples, 30 features) — available via `sklearn.datasets.load_breast_cancer()`

**Task 1: Classical SVM Pipeline (45 min)**
1. Implement a scikit-learn pipeline: StandardScaler → SVM with RBF kernel
2. Use `GridSearchCV` with 5-fold CV over C = [0.1, 1, 10, 100, 1000] and γ = [1e-4, 1e-3, 0.01, 0.1, 1]
3. Run with five random seeds (random_state = 0, 1, 2, 3, 4), each with a different stratified train/test split
4. Record mean ± standard deviation of test accuracy across seeds

**Task 2: Quantum Kernel SVM Pipeline (90 min)**
1. Implement a ZZFeatureMap with 6 qubits and 2 repetitions using PCA to reduce to 6 features first
2. Use `QuantumKernel` from Qiskit Machine Learning with statevector simulator backend
3. Run with the same five seeds and train/test splits as Task 1
4. Record mean ± standard deviation of test accuracy
5. Record: training time per seed, total GPU/CPU time

**Task 3: Statistical Analysis (30 min)**
1. Run a paired t-test (`scipy.stats.ttest_rel`) on the per-seed accuracy vectors
2. Compute Cohen's d for practical significance
3. Fill in the results table (provided in the notebook)
4. Decision rule: quantum advantage is claimed only if (a) p < 0.05 AND (b) Cohen's d > 0.2 AND (c) mean accuracy difference > 0.5 percentage points

**Deliverable 1:** Working notebook with all cells executed and results visible  
**Deliverable 2:** Results table (provided template)  
**Deliverable 3:** 600-word memo titled "What I Would Tell a Vendor Who Claims Quantum Advantage on This Problem"

The memo must address: the statistical result, the practical significance, the dataset size and feature dimensionality limitations, the simulator vs. hardware gap, and a recommendation on whether to pursue a hardware pilot.

---

## 8.17 Discussion

**Prompt:** Using the five-question governance filter from Section 8.11 and the dequantization framework from Section 8.8, evaluate the following claim:

> *"Our quantum reinforcement learning system reduces compute time for portfolio optimization by 40% versus classical deep RL, validated on three years of live trading data. The experiment was run on a 20-qubit trapped-ion processor with 99.5% two-qubit gate fidelity."*

Identify the strongest evidence in favor of this claim, the most significant missing information, and the single most important question you would ask before recommending procurement of this system.

**Citing sources:** Support your analysis with at least two peer-reviewed sources from the QML literature. Acceptable sources include Tang (2019), Havlíček et al. (2019), Kübler et al. (2022), Cerezo et al. (2021), or any peer-reviewed paper published in Physical Review, Nature, Science, NeurIPS, ICML, or ICLR.

**Peer responses:** Provide substantive responses to **two** of your classmates' posts. A substantive response engages with the specific evidence or logic in the original post — it agrees or disagrees with reasons, adds a counter-example, or identifies a missing consideration. Responses of fewer than 75 words or consisting primarily of agreement without analytical content will not receive peer response credit.

**Length:** 250–400 words for the original post; 75–150 words per peer response.

---

## 8.18 Glossary

```{glossary}
Quantum Machine Learning (QML)
  The application of quantum computing to machine learning tasks, including running ML algorithms on quantum hardware, using quantum circuits as trainable models, or leveraging quantum effects to accelerate specific ML subroutines. Distinct from quantum-inspired ML and from AI for quantum.

Quantum Kernel
  A kernel function computed using a quantum circuit. The quantum circuit (feature map) maps classical data into Hilbert space; the kernel value is the inner product of two quantum state representations. May enable classification boundaries in exponentially high-dimensional feature spaces inaccessible to classical kernels.

Feature Map Circuit
  A quantum circuit that encodes classical data into a quantum state, mapping input features into a quantum Hilbert space. The ZZFeatureMap (used in Qiskit ML) encodes data through Hadamard and controlled-phase gates, creating entangled state representations of input feature pairs.

Hilbert Space
  The mathematical space of all possible quantum states for a quantum system. For n qubits, the Hilbert space has dimension 2ⁿ. Quantum kernel methods leverage this exponentially large space to find classification boundaries that classical kernels operating in lower-dimensional spaces cannot efficiently compute.

Variational Quantum Circuit (VQC)
  A quantum circuit with adjustable gate parameters, trained by a classical optimizer to minimize a loss function. The hybrid loop — quantum circuit forward pass, classical gradient computation, parameter update — is the basis for VQE, QAOA, and quantum neural networks.

Parameterized Quantum Circuit (PQC)
  Synonym for variational quantum circuit. Emphasizes the parameterized (trainable) nature of the gate operations. Parameters are typically rotation angles for single-qubit and two-qubit gates.

Barren Plateau
  A pathological region in the variational parameter landscape of a quantum circuit where gradients vanish exponentially with circuit depth and qubit count. Barren plateaus make training of deep quantum circuits computationally intractable — the classical optimizer receives essentially zero gradient signal.

VQE (Variational Quantum Eigensolver)
  A hybrid quantum-classical algorithm for finding ground state energies of quantum systems. In the QML context, relevant as the architectural prototype for variational quantum circuits — demonstrating that parameterized quantum circuits can be trained by classical optimizers to solve hard optimization problems.

QAOA (Quantum Approximate Optimization Algorithm)
  A variational quantum algorithm for combinatorial optimization. Applies alternating unitary operations (problem Hamiltonian and mixing Hamiltonian) with classically optimized parameters to produce approximate solutions to combinatorial problems. Relevant to ML as a potential hyperparameter search and neural architecture search accelerator.

Dequantization
  The development of classical algorithms that match the asymptotic performance of quantum algorithms, eliminating the claimed quantum speedup. Popularized by Tang (2019), who showed that the quantum recommendation system algorithm of Kerenidis and Prakash (2016) could be matched classically via efficient sampling.

Quantum Boltzmann Machine (QBM)
  A generative model that uses a quantum circuit to represent the latent probability distribution. Samples from the quantum circuit are used to generate new data. Proposed as a quantum-enhanced alternative to classical restricted Boltzmann machines for generative modeling.

Quantum Neural Network (QNN)
  A parameterized quantum circuit used as a machine learning model, analogous to a classical neural network. Input encoding, quantum processing layers with trainable parameters, and measurement constitute the forward pass. Subject to barren plateau training challenges for deep circuits.

Sampling Advantage
  The ability of quantum computers to efficiently sample from probability distributions that are computationally hard for classical computers to sample from. The foundational claim behind Google's quantum supremacy experiments and the most defensible near-term quantum capability for ML applications.

NISQ (Noisy Intermediate-Scale Quantum)
  Characterizes current quantum hardware: 50–1000+ qubits with significant gate error rates, no fault tolerance, and limited coherence times. NISQ devices can run short-depth circuits but not the long, deep circuits required by most provably-speedup quantum algorithms.

ZZFeatureMap
  A specific quantum feature map circuit used in Qiskit Machine Learning. Encodes classical features through Hadamard gates (superposition) and controlled-Z-Z (CZZ) rotation gates (entanglement). Produces a quantum state whose inner products with other states constitute a quantum kernel. Commonly used in quantum SVM experiments.

Quantum Advantage
  A regime in which a quantum algorithm solves a problem faster than any classical algorithm. Distinguished from quantum supremacy (demonstrating a task quantum computers can do faster than classical computers, even if the task has no practical value). Genuine quantum advantage in ML remains undemonstrated for practically relevant dataset sizes as of 2025.

Dequantization Test
  The governance question: "Has anyone tried to match this quantum algorithm's performance with a classical sampling-based algorithm?" A necessary (though not sufficient) test for quantum advantage claims. Vendor claims that cannot answer this question with a clear "yes, and the classical approach is significantly slower" fail this test.

Classical Baseline Optimization
  The process of maximally tuning a classical algorithm before comparing it to a quantum counterpart. Requires full hyperparameter grid search (or Bayesian optimization), cross-validation, and comparison against state-of-the-art classical algorithms — not merely the obvious or default implementation. The single most important methodological safeguard in QML benchmarking.
```

---

## 8.19 Leader's Takeaway

The companies that win the quantum-AI decade will not be the ones that bet biggest on quantum AI. They will be the ones that bet *smartest* — which means building the organizational instinct to distinguish between a breakthrough and a press release.

That instinct has a name: **quantum AI governance.** It is not exotic. It is the same critical thinking your procurement team already applies to any technology claim, adapted for the specific failure modes of quantum ML: the baseline problem, the dequantization risk, the simulator-hardware gap, the barren plateau issue, and the incentive structure of a field where "quantum advantage" headlines generate funding regardless of methodological rigor.

The five-question filter in this chapter is a starting point, not a ceiling. Organizations that use it consistently will save millions in premature quantum AI investments. Organizations that go further — building quantum literacy into ML teams, running quantum pilots with rigorous classical baselines, and contributing to the peer-reviewed literature — will have structural advantages that compound as the hardware matures.

The quantum-AI decade has already begun. The window for building the literacy and the governance instincts to navigate it is now. Not because the technology is ready — but because the talent pipeline takes years, and the organizations that started three years ago are already ahead.

The question for every leader reading this chapter: *are you in the audience that left the panel convinced, confused, or Googling?*

This chapter was written for the third option. The search is over.

---

*Next Chapter → Chapter 9: Quantum Security in Practice — From Post-Quantum Standards to Zero-Trust Architecture*
