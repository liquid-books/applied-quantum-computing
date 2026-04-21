# Chapter 1 Quiz: The \$850 Billion Question — Why Quantum, Why Now
*Instructor resource — not published in the book.*

---

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
