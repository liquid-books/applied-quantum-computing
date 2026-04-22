---
title: "Appendix A: Glossary for the Non-Physicist"
subtitle: "Every quantum term you will encounter, defined in plain English"
short_title: "Appendix A: Glossary"
description: "~80 quantum computing terms defined in 40 words or fewer, organized by topic, written for business leaders with no physics background."
label: appendix-a-glossary
tags: [glossary, quantum computing, terminology, reference]
---

# Appendix A: Glossary for the Non-Physicist

This glossary covers the terms you will encounter in quantum computing news, vendor proposals, and research briefs. Every definition is written for a business leader with no physics background — no equations, no prerequisite jargon.

---

## Quantum Fundamentals

:::{glossary}
Qubit
  The basic unit of quantum information — the quantum version of a classical bit. Unlike a classical bit, which is always 0 or 1, a qubit can be in a combination of both states at the same time until it is measured.

Superposition
  A qubit's ability to represent 0 and 1 simultaneously before it is measured. Think of a coin spinning in the air — it is neither heads nor tails until it lands. Superposition lets quantum computers explore many possibilities at once.

Entanglement
  A special link between two or more qubits so that the state of one instantly influences the others, no matter how far apart they are. Entanglement is a key resource for quantum computing and quantum communication — it has no classical equivalent.

Interference
  A technique used in quantum algorithms to amplify paths that lead to correct answers and cancel paths that lead to wrong ones — similar to how noise-canceling headphones eliminate unwanted sound. Interference is how quantum computers steer toward solutions.

Decoherence
  The loss of a qubit's quantum properties when it interacts with its environment (heat, vibration, stray electromagnetic fields). Decoherence is the primary enemy of quantum computing — it causes errors and limits how long calculations can run.

Coherence Time
  How long a qubit can maintain its quantum state before decoherence degrades it. Longer coherence time means more computation is possible before errors accumulate. Measured in microseconds to milliseconds on most hardware today.

Quantum Gate
  A basic operation that changes the state of one or more qubits — the quantum equivalent of a logic gate in classical computing (like AND, OR, NOT). Quantum algorithms are built by stringing gates together into circuits.

Circuit Depth
  The number of sequential layers of gates in a quantum program. Deeper circuits require longer run time and accumulate more errors. Shallow circuits run faster and are more reliable on today's noisy hardware.

Shot
  A single run of a quantum circuit, ending with a measurement that produces one classical outcome (a string of 0s and 1s). Because quantum results are probabilistic, a program is run many shots to build up a statistical picture of the answer.

Error Rate
  The probability that a gate or measurement produces the wrong result. Expressed as a percentage or fraction — for example, a 0.1% error rate means one mistake per thousand operations. Lower is always better.

Error Mitigation
  Software techniques that reduce the effect of hardware errors without fixing them at the physical level. Think of it like noise filtering — you cannot silence the noise, but you can partially cancel it out in post-processing.

Error Correction
  A method of protecting quantum information by spreading it across many physical qubits so that errors can be detected and fixed automatically. Requires significant overhead but is essential for fault-tolerant computing.

Logical Qubit
  A reliable, error-corrected qubit built from many physical qubits working together. A logical qubit behaves as a near-perfect qubit even when its constituent physical qubits are noisy. Current estimates suggest hundreds to thousands of physical qubits per logical qubit.

Physical Qubit
  The actual hardware qubit on a chip — imperfect, noisy, and prone to errors. Multiple physical qubits are combined to create one logical qubit. When vendors advertise qubit counts, they mean physical qubits.

NISQ
  Stands for Noisy Intermediate-Scale Quantum. Describes today's quantum computers — 50 to ~1,000 qubits, no error correction, and limited circuit depth. NISQ machines can run experiments but cannot yet outperform classical computers on practical business problems.

Fault-Tolerant Quantum Computing
  A future generation of quantum computing where logical qubits and error correction allow arbitrarily long, reliable calculations. Fault tolerance is the threshold at which quantum computers become genuinely transformative — most experts place it a decade or more away.

Quantum Supremacy
  A one-time milestone: a quantum computer completing a specific task that no classical computer could finish in a reasonable time. Google claimed this in 2019. The task was narrow and had no practical application — it was a proof of principle.

Quantum Advantage
  The point at which a quantum computer solves a practically useful problem faster or cheaper than any classical alternative. This is the real goal for business. Quantum advantage on commercially relevant problems has not yet been convincingly demonstrated.

Quantum Utility
  IBM's term for the threshold at which quantum computers contribute useful scientific or business insights — even if not definitively faster than all classical methods. A deliberately lower bar than quantum advantage, intended to motivate near-term use.

Bloch Sphere
  A visual model used to represent the state of a single qubit as a point on the surface of a sphere. Useful for intuition and education — you will see it in vendor diagrams and textbooks. It is a picture, not a physical object.

Bell State
  One of four specific two-qubit states that are maximally entangled — meaning the two qubits are as correlated as quantum mechanics allows. Bell states are the building blocks of quantum communication and cryptography protocols.

Bell Inequality
  A mathematical test that reveals whether two particles share true quantum entanglement or are just classically correlated. Violating the inequality proves the correlation is quantum in nature — it cannot be explained by any hidden classical mechanism.

CHSH Test
  A specific version of the Bell Inequality test (named for Clauser, Horne, Shimony, Holt) used to verify quantum entanglement in lab experiments. Results exceeding the classical limit confirm genuine quantum behavior and are used to certify quantum devices.
:::

---

## Hardware & Architecture

:::{glossary}
Superconducting Qubit
  A qubit made from tiny electrical circuits cooled to near absolute zero (-273°C) so that electricity flows without resistance. Used by IBM, Google, and Rigetti. Fast gate operations but requires expensive refrigeration and is sensitive to vibration and heat.

Trapped-Ion Qubit
  A qubit made from a single electrically charged atom held in place by magnetic fields and manipulated with lasers. Used by IonQ and Quantinuum. Slower than superconducting but achieves very high gate fidelity and longer coherence times.

Neutral-Atom Qubit
  A qubit made from individual uncharged atoms held in place by laser "tweezers." Companies like Atom Computing and QuEra use this approach. Atoms can be rearranged to create connectivity between any pair — a hardware advantage for certain algorithms.

Photonic Qubit
  A qubit encoded in a single particle of light (a photon). Does not need extreme cooling. Naturally suited for quantum communication and networking. Current photonic computers face challenges with efficient photon generation and detection.

Topological Qubit
  A theoretical qubit type that encodes information in a special braided pattern of quantum states, making it inherently resistant to errors. Microsoft is pursuing this approach. Not yet demonstrated at scale — remains a research frontier.

Dilution Refrigerator
  The specialized refrigerator used to cool superconducting quantum processors to temperatures colder than outer space (about 15 millikelvin). A critical piece of infrastructure — large, expensive (\$500,000–\$2 million), and required for every superconducting system.

T1 Time
  The time it takes for a qubit to spontaneously "relax" from its excited state (representing 1) to its ground state (representing 0). A measure of energy decay. Longer T1 means the qubit can hold information longer before losing it.

T2 Time
  The time it takes for a qubit to lose its phase coherence — the precise timing relationship that makes superposition useful. T2 is usually shorter than T1. Together, T1 and T2 set the practical limit on how long a computation can run.

Gate Time
  How long it takes to execute a single quantum gate operation. Faster gate times allow more operations within the coherence window. Superconducting gates run in nanoseconds; trapped-ion gates take microseconds but tend to be more accurate.

1Q Gate
  A single-qubit gate — an operation that changes the state of one qubit. Examples include flipping a qubit (like a NOT gate) or putting it into superposition. Generally fast and accurate; typical error rates are below 0.1%.

2Q Gate
  A two-qubit gate — an operation that acts on two qubits simultaneously and creates entanglement between them. Slower and noisier than 1Q gates. The CNOT gate is the most common example. 2Q gate fidelity is the key quality benchmark.

Gate Fidelity
  A measure of how accurately a gate performs its intended operation, expressed as a percentage. A 99.9% fidelity means the gate produces the correct output 999 times out of 1,000. High fidelity is essential for reliable computation.

Entanglement Fidelity
  A measure of how well a two-qubit entanglement operation preserves the quantum state. Lower entanglement fidelity means the resulting entangled state is noisier and less useful for computation or communication.

Randomized Benchmarking
  A standard testing protocol for measuring average gate error rates by running long sequences of random gates and measuring how quickly the results degrade. Provides a reliable, vendor-agnostic quality score for quantum hardware.

Quantum Volume
  IBM's single-number quality metric for a quantum computer. It combines qubit count, connectivity, gate fidelity, and circuit depth into one score. Higher is better. A Quantum Volume of 64 means the system reliably runs circuits of a certain complexity.

CLOPS
  Stands for Circuit Layer Operations Per Second. A speed benchmark measuring how many quantum circuit layers a system can execute per second, including all classical overhead. High CLOPS means faster sampling — important for hybrid algorithms and variational methods.
:::

---

## Algorithms & Software

:::{glossary}
Hadamard Gate
  A single-qubit gate that puts a qubit into equal superposition — giving it a 50/50 chance of measuring as 0 or 1. Think of it as the quantum equivalent of flipping a fair coin. It is one of the most frequently used gates in quantum circuits.

CNOT Gate
  Short for Controlled-NOT. A two-qubit gate that flips the second qubit (the "target") if and only if the first qubit (the "control") is in state 1. The CNOT gate is the standard way to create entanglement between two qubits.

Ansatz
  A template quantum circuit with adjustable parameters — used as the starting structure in variational algorithms. The algorithm tunes the parameters to find the best solution. The word is German for "initial approach" or "educated guess."

Variational Quantum Eigensolver (VQE)
  A hybrid algorithm that uses a quantum computer to evaluate candidate solutions while a classical computer adjusts the parameters to improve them. Designed to find the lowest energy state of molecules — useful for drug discovery and materials science.

QAOA
  Stands for Quantum Approximate Optimization Algorithm. A hybrid algorithm designed to solve combinatorial optimization problems (finding the best arrangement among many options). Runs part on quantum hardware, part on classical computers. Results are approximate, not guaranteed-optimal.

Quantum Annealing
  A hardware approach for solving optimization problems by gradually "cooling" a quantum system toward its lowest-energy configuration, which corresponds to the best solution. D-Wave's machines use this method. Different from gate-based quantum computing.

QUBO
  Stands for Quadratic Unconstrained Binary Optimization. A mathematical problem format used with quantum annealers and quantum-inspired solvers. Many business optimization problems — logistics, scheduling, finance — can be reformulated as QUBO problems.

Ising Model
  A mathematical framework from physics that describes how interacting binary variables (up/down spins) find their lowest-energy configuration. Quantum annealers implement a physical version of the Ising model, making it the natural language for optimization on those machines.

Quantum Sampling
  Using a quantum computer to generate samples from a probability distribution that is hard for classical computers to simulate. Useful for Monte Carlo simulations (financial risk modeling), generative AI, and certain optimization tasks.

Quantum Speedup
  The degree to which a quantum algorithm outperforms the best known classical algorithm for the same problem. Speedups can be polynomial (modest) or exponential (dramatic). Shor's algorithm offers exponential speedup for factoring large numbers.

BQP
  Stands for Bounded-error Quantum Polynomial time — the class of problems a quantum computer can solve efficiently (in reasonable time with high probability). If a problem is in BQP, a quantum computer can handle it. Most classical easy problems are also in BQP.

NP-Hard
  A category of problems so computationally difficult that no known algorithm — classical or quantum — can solve all cases efficiently. Includes many real-world optimization challenges. Quantum computers offer approximate or heuristic improvements, not guaranteed solutions.

Combinatorial Optimization
  Finding the best selection or arrangement from a large but finite set of options — for example, the optimal delivery route, investment portfolio, or staff schedule. A key target for quantum computing and quantum-inspired algorithms.

Quantum Error Correction (QEC)
  The full system of encoding, monitoring, and correcting qubit errors in real time without disturbing the computation. QEC is the foundational requirement for fault-tolerant quantum computing — it trades many physical qubits for one reliable logical qubit.

Surface Code
  The most widely studied quantum error correction scheme. Qubits are arranged in a 2D grid; neighboring qubits constantly check each other for errors. Requires roughly 1,000 physical qubits per logical qubit but tolerates relatively high physical error rates.

Steane Code
  An early quantum error correction code that encodes one logical qubit in seven physical qubits. Less resource-efficient than the surface code for large systems but historically important and used in some trapped-ion architectures.

Logical Error Rate
  The error rate of a logical qubit — after error correction has been applied. The whole point of error correction is to drive the logical error rate far below the physical error rate. Lower logical error rates enable longer, more reliable calculations.
:::

---

## Quantum AI & Machine Learning

:::{glossary}
Quantum Machine Learning (QML)
  The field exploring whether quantum computers can speed up or improve machine learning tasks — pattern recognition, classification, clustering, and optimization. Most QML claims are still theoretical or demonstrated only on tiny datasets. Promising but unproven at scale.

Quantum Kernel
  A technique that uses a quantum computer to calculate how similar two data points are — a computation that may be hard for classical computers on certain data types. Kernels are a core component of support vector machines (a classical machine learning method).

Feature Map
  A transformation that encodes classical data (numbers, text, images) into the quantum state of qubits so a quantum algorithm can process it. Designing a good feature map is critical — a poor one can erase any potential quantum advantage.

Dequantization
  The process of developing a classical algorithm that matches the performance of a proposed quantum machine learning algorithm. When dequantization succeeds, it shows the quantum algorithm offered no real advantage. A healthy skeptical check on QML claims.

Quantum-Inspired Solver
  A classical algorithm that borrows ideas from quantum computing (such as tensor networks or simulated annealing) to solve optimization problems faster on ordinary hardware. No quantum computer required. Often competitive with near-term quantum hardware for practical problems today.
:::

---

## Cryptography & Security

:::{glossary}
RSA
  The most widely used public-key encryption system, securing most of today's internet traffic. RSA's security depends on the difficulty of factoring very large numbers — a task that Shor's algorithm running on a fault-tolerant quantum computer could break.

ECC (Elliptic Curve Cryptography)
  A modern form of public-key cryptography used in TLS (web security), mobile devices, and blockchain systems. More efficient than RSA but also vulnerable to Shor's algorithm on a sufficiently powerful quantum computer.

Shor's Algorithm
  A quantum algorithm that can factor large numbers exponentially faster than any known classical algorithm. If run on a fault-tolerant quantum computer with thousands of logical qubits, it would break RSA and ECC encryption. Currently impractical — requires hardware decades away.

Grover's Algorithm
  A quantum algorithm that searches an unsorted database quadratically faster than classical methods. It weakens (but does not break) symmetric encryption like AES — doubling key lengths (e.g., AES-256 instead of AES-128) restores security against Grover's attack.

Post-Quantum Cryptography (PQC)
  New encryption algorithms designed to resist attacks from both classical and quantum computers. They use mathematical problems quantum computers cannot solve efficiently. PQC runs on today's classical hardware — no quantum computer needed to use or deploy it.

ML-KEM
  Short for Module-Lattice Key Encapsulation Mechanism. NIST's standardized post-quantum algorithm for securely exchanging encryption keys (replacing RSA and ECC key exchange). Based on lattice mathematics. Previously known as CRYSTALS-Kyber.

ML-DSA
  Short for Module-Lattice Digital Signature Algorithm. NIST's standardized post-quantum algorithm for digital signatures (replacing RSA and ECDSA signatures). Based on lattice mathematics. Previously known as CRYSTALS-Dilithium.

SLH-DSA
  Short for Stateless Hash-Based Digital Signature Algorithm. A post-quantum digital signature scheme based on the security of cryptographic hash functions — a very conservative, well-understood foundation. Slower but highly trusted.

Lattice Cryptography
  A family of cryptographic techniques whose security is based on the difficulty of solving certain geometric problems involving lattices (grids of points in high-dimensional space). Believed to be resistant to quantum attacks. The basis of ML-KEM and ML-DSA.

Mosca Inequality
  A risk framework by cryptographer Michele Mosca: if (years until a quantum threat) is less than (migration time + shelf life of your data), you are already at risk. Used to assess urgency for post-quantum migration planning.

Crypto-Agility
  The ability of a system to quickly swap out one cryptographic algorithm for another without redesigning the whole system. A key goal of post-quantum migration — organizations with crypto-agile infrastructure can update defenses as standards evolve.

Harvest Now Decrypt Later
  An attack strategy where adversaries collect encrypted data today with the intent of decrypting it once a powerful enough quantum computer exists. Long-lived sensitive data (health records, government secrets, financial data) is already at risk from this strategy.

Hybrid TLS
  A version of TLS (the protocol that secures web connections) that combines a classical algorithm (like ECDH) and a post-quantum algorithm (like ML-KEM) simultaneously. Hybrid mode ensures security even if one algorithm turns out to be breakable.

CNSA 2.0
  Commercial National Security Algorithm Suite version 2.0. The U.S. National Security Agency's mandatory cryptography standards for national security systems. Requires adoption of post-quantum algorithms (ML-KEM, ML-DSA, SLH-DSA) by 2030–2035.

NIST PQC
  The NIST Post-Quantum Cryptography standardization project. NIST (the U.S. standards body) evaluated 69 candidate algorithms starting in 2016 and finalized three standards in 2024: ML-KEM, ML-DSA, and SLH-DSA. The global reference for quantum-resistant cryptography.

Q-Day
  The hypothetical future date when a quantum computer becomes powerful enough to break widely used public-key encryption (RSA, ECC). No consensus on timing — estimates range from 10 to 30+ years. Organizations should act now regardless, because migration takes years.

Quantum Key Distribution (QKD)
  A method of exchanging encryption keys using quantum physics (specifically, properties of individual photons). Any eavesdropping attempt physically disturbs the photons and is detectable. Provides information-theoretic security — not based on computational hardness.

Quantum Network
  A communications network that transmits quantum information (entangled particles or qubits) between locations. Enables applications like quantum key distribution, distributed quantum computing, and ultimately the quantum internet. Short-range networks exist today in research settings.

Quantum Internet
  A future global network that interconnects quantum computers and quantum devices using quantum communication channels. Would enable perfectly secure communication, distributed quantum computing, and quantum sensor networks. Currently in early research and prototype stages.

Quantum Teleportation
  A protocol that transfers the exact quantum state of one qubit to another distant qubit using entanglement and a classical communication channel. No physical matter is transmitted — just the quantum information. A foundational primitive for quantum networks.
:::

---

## Economics & Strategy

:::{glossary}
Pay-Per-Shot
  A quantum cloud pricing model where customers are billed per individual circuit execution (shot). Common on platforms like IBM Quantum and Amazon Braket. Cost scales with the number of repetitions needed to get statistically reliable results.

Pay-Per-Minute
  A quantum cloud pricing model where customers are billed for the total time their jobs occupy the quantum processor, regardless of shot count. Typical on systems with longer setup overhead, such as trapped-ion machines.

Reserved Capacity
  A pricing arrangement where an organization pays upfront to reserve dedicated access to a quantum processor for a set number of hours per month. Offers cost predictability and priority access but requires commitment before knowing actual usage.

Cost Per Useful Result
  A practical metric for evaluating quantum computing value: total cost divided by the number of actionable, correct answers produced. Useful results require enough shots to beat noise, classical post-processing, and reliable hardware — making this metric much higher than raw shot cost suggests.

TCO (Total Cost of Ownership)
  The full cost of using quantum computing over time — including cloud access fees, personnel (quantum engineers are expensive), software licensing, classical co-processing, and integration costs. TCO is almost always far higher than the quoted hardware price alone.

Quantum Speedup
  See entry in Algorithms & Software section. In a business context: the ratio of classical run time to quantum run time for the same problem. Even a modest speedup on a high-value problem can justify significant investment — but speedup must be demonstrated on real problem sizes.

Quantum-Inspired Solver
  See entry in Algorithms & Software section. In a strategy context: classical software that applies quantum-like optimization techniques without needing quantum hardware. Often the fastest path to optimization ROI today, while organizations prepare for genuine quantum advantage.

BQP
  See entry in Algorithms & Software section. In a strategy context: understanding which business problems fall inside BQP (accessible to quantum) vs. outside it (quantum-resistant problems) helps executives allocate R&D resources and set realistic expectations.

NP-Hard
  See entry in Algorithms & Software section. In a strategy context: many high-value business problems (supply chain, portfolio optimization, drug discovery) are NP-Hard. Quantum computers may offer better heuristics, but do not promise perfect solutions — manage vendor claims accordingly.
:::
