---
title: "Appendix H: FAU Research Computing and Quantum Infrastructure"
short_title: "Appendix H: FAU Computing Infrastructure"
description: "A practical reference for students in the FAU Quantum-Enabled Business Strategy course: what computing resources are available, where they live, how to access them, and how they connect to the labs in this book."
label: appendix-h-fau-hpc-quantum
---

# Appendix H: FAU Research Computing and Quantum Infrastructure

This appendix is specific to students enrolled in FAU's **Quantum-Enabled Business Strategy: Optimization, Analytics, and Emerging Applications** course. It describes the two distinct computing resources available to FAU students and researchers — classical HPC and quantum annealing — and explains how each connects to the hands-on labs in this book.

---

## FAU's Two Computing Tiers

FAU operates two categories of advanced computing infrastructure. They are organizationally and physically separate, serve different problem classes, and are managed by different units. Understanding both — and which to reach for when — is itself a practical expression of the dual-paradigm literacy this course develops.

| | Classical HPC | Quantum Annealing |
|---|---|---|
| **System** | OwlCloud / Athene cluster | D-Wave Advantage2 |
| **Location** | Jupiter MacArthur Campus | Boca Raton Campus (deploying 2026) |
| **Managed by** | Office of Information Technology (OIT) | College of Engineering & Computer Science / College of Science |
| **Access** | FAU student/researcher credentials | D-Wave Leap cloud (during deployment) |
| **Best for** | Classical simulation, ML training, CFD, Matlab, Jupyter | Combinatorial optimization (QUBO problems) |
| **Chapter connection** | Background compute for classical baselines in all labs | Labs 6A, 7B, 8B, 9B, and any QUBO optimization pilot |

---

## FAU OwlCloud: Classical HPC

**Portal:** [hpc.fau.edu](https://hpc.fau.edu) / [owlcloud.hpc.fau.edu](https://owlcloud.hpc.fau.edu)

FAU's **OwlCloud** platform provides browser-based access to the university's HPC clusters for researchers and students without requiring command-line experience.

**Available systems:**
- **Athene** — FAU's current primary HPC cluster, accessible via SSH or through the OwlCloud portal. Supports parallel computing jobs, ML workloads, Matlab, Jupyter notebooks, and CFD tools such as Fluent.
- **Koko** — The preceding generation cluster, available for legacy workflows.

**What it is good for in this course:** Running the classical baseline comparisons that all quantum benchmark labs require. The D-Wave labs in Chapters 6, 7, 8, and 9 compare quantum annealing results against classical optimizers. Running those classical baselines on OwlCloud (rather than a laptop) gives you access to more compute for larger classical search jobs, making the benchmarks more credible.

**Access:** FAU student credentials. Request a research computing account through the OIT helpdesk at [helpdesk.fau.edu](https://helpdesk.fau.edu) under the Research Computing / HPC category.

---

## FAU D-Wave Advantage2: Quantum Annealing

On January 27, 2026, FAU announced a $20 million agreement with D-Wave Quantum Inc. (NYSE: QBTS) to acquire and install a **D-Wave Advantage2 annealing quantum computer** on FAU's Boca Raton campus — making FAU the first university in Florida to host a dedicated, on-site quantum computer.

**System specifications (Advantage2):**
- **Architecture:** Quantum annealing (not gate-model — see Chapter 1 and Chapter 4 for the distinction)
- **Qubits:** 7,000+ Pegasus-topology physical qubits
- **Problem type:** Combinatorial optimization formulated as QUBO (Quadratic Unconstrained Binary Optimization)
- **Access method:** D-Wave Ocean SDK via Python; D-Wave Leap cloud interface
- **Stride hybrid solver:** Available through Leap — combines quantum annealing with classical pre/post-processing to handle problems with up to 2 million variables and constraints

**Deployment timeline:** Expected later in 2026. During the pre-deployment period, all course labs use **D-Wave Leap cloud access**, which connects to the same Advantage2 class of hardware through D-Wave's cloud infrastructure.

**The D-Wave + FAU Partnership:**

The FAU/D-Wave partnership goes beyond hardware purchase. It includes:
- **Joint research programs** between FAU faculty and D-Wave researchers
- **Student access and training** — FAU students gain direct hands-on access to production-grade quantum hardware that most business school programs can only access theoretically
- **Hackathons and ideation workshops** targeting real-world use cases in public works, logistics, supply chains, transportation, and emergency management
- **Workforce development** — building the quantum talent pipeline for South Florida

Simultaneously with the FAU announcement, D-Wave announced the **relocation of its U.S. corporate headquarters to the Boca Raton Innovation Center** — the same innovation ecosystem that hosts FAU's research facilities. For students in this course, this means the company whose hardware you use in every D-Wave lab is headquartered in your backyard.

**Why this matters for your career:** FAU is one of a small number of universities globally — and the only university in Florida — where graduate students have hands-on access to production-grade quantum annealing hardware as part of their coursework. The QUBO formulation skills, Ocean SDK experience, and Leap cloud fluency you develop in this course are the exact skills that enterprise quantum teams at BASF, Mastercard, Volkswagen, and Verge Ag use in production.

---

## The HPC + Quantum Connection

Mehran Basiratmand, who designed this course, spent nearly a decade as FAU's Chief Technology Officer overseeing FAU's high-performance computing and supercomputing (SC) initiatives. That background is the reason this course treats quantum computing not as a physics laboratory curiosity but as the next layer of enterprise compute infrastructure — sitting alongside, and increasingly integrated with, classical HPC.

The International Conference for High Performance Computing, Networking, Storage and Analysis — **SC** — is where this integration becomes most visible annually. SC26 convenes in Chicago in November 2026. For students building quantum careers, SC26 is the single most information-dense event for understanding how quantum and HPC are converging in enterprise and research computing infrastructure.

At FAU, that convergence is structural. The OwlCloud/Athene HPC infrastructure and the D-Wave Advantage2 are currently managed by separate organizational units — OIT and the research colleges respectively. The strategic opportunity is their integration: classical HPC for pre-processing, data preparation, and classical baseline computation; quantum annealing for the combinatorial optimization steps where classical methods hit combinatorial walls. This hybrid HPC+quantum architecture is precisely what Chapter 3 describes as the enterprise compute stack of the near-term future.

---

## Quick Access Guide for Course Labs

| Lab | System | Access |
|-----|--------|--------|
| Labs 1A, 3A, 7A | IBM Quantum | [quantum.ibm.com](https://quantum.ibm.com) — free account |
| Labs 1B, 2B, 3B, 6A, 7B, 8B, 9B | D-Wave Leap | [cloud.dwavesys.com](https://cloud.dwavesys.com) — free developer account |
| Lab 5C (liboqs) | Google Colab | [colab.research.google.com](https://colab.research.google.com) — Google account |
| Classical baselines (all labs) | OwlCloud / Athene | [owlcloud.hpc.fau.edu](https://owlcloud.hpc.fau.edu) — FAU credentials |
| On-campus Advantage2 (post-deployment) | D-Wave Advantage2 | Contact FAU Research Computing — access TBD |

**For D-Wave Leap:** Create a free account at [cloud.dwavesys.com](https://cloud.dwavesys.com). Free developer accounts include sufficient QPU time and hybrid solver minutes for all course labs. No credit card required.

**For OwlCloud:** Submit a Research Computing account request through the OIT helpdesk. Approval is typically granted within 1–2 business days for enrolled students.

---

*For questions about FAU's quantum computing program, contact the College of Engineering and Computer Science. For OwlCloud/HPC access, contact the OIT Research Computing helpdesk at [helpdesk.fau.edu](https://helpdesk.fau.edu).*
