---
title: "Appendix F: Market Snapshot"
subtitle: "Version 1.0 — April 2026 | Instructor-refreshed annually"
short_title: "Appendix F: Market Snapshot"
description: "The one place in the book where current-state facts live. Leading vendors by modality, qubit counts and fidelity benchmarks, cloud pricing, NIST PQC adoption timeline, regulatory deadlines, and M&A activity — as of April 2026. Designed for annual instructor refresh."
label: appendix-f-market-snapshot
tags: [market snapshot, quantum vendors, pricing, NIST PQC, regulatory, M&A, current state]
---

# Appendix F: Market Snapshot

**Version 1.0 — April 2026 | Instructor-refreshed annually**

---

## A Note to Instructors (Read First)

This appendix exists because quantum computing is moving too fast for a textbook to keep up — but not so fast that an entire textbook becomes worthless after twelve months. The solution is isolation: everything in the main chapters is written to be **evergreen**. Principles of superposition, entanglement, error correction, and quantum algorithms do not change year to year. What does change — rapidly — is who is building what, how many qubits they have, what they charge, and which government deadline just moved.

**This appendix is the only place those fast-moving facts live.** If this appendix ages, the chapters remain valid. If a student reads this in 2028 and the qubit counts are outdated, the conceptual framework in the chapters still teaches them everything they need to reason about whatever the 2028 landscape looks like.

**How to read the data here:**

- Ranges are honest; point estimates are suspect. When you see "99.5%," read it as "approximately 99.5% at the time of writing, verify before citing."
- Numbers marked **(verify current)** are the most volatile — check the vendor's website before each course offering.
- Numbers marked **(confirmed, Aug 2024)** or similar are regulatory or standards milestones that are unlikely to change retroactively.

**When to refresh this appendix:** Once per year, at the start of each course offering. Sections 1–3 (vendors, qubit counts, pricing) and Section 6 (M&A) change most frequently. Sections 4–5 (NIST standards, regulatory deadlines) are more stable but should still be spot-checked. See Section 7 for the full refresh procedure.

**Time investment:** A thorough refresh takes approximately 2–4 hours. That is a reasonable annual investment to ensure students receive accurate market context.

---

## Section 1: Leading Vendors by Hardware Modality

*As of April 2026. Vendor landscape changes frequently; new entrants and consolidations are expected.*

### 1.1 Superconducting Qubits

Superconducting qubit systems remain the most commercially mature modality as of 2026, with the largest installed base and the broadest cloud access ecosystem.

**IBM Quantum**
IBM's quantum program is organized around the Heron, Eagle, and Flamingo processor families. The Heron r2 processor (133 qubits) represents IBM's current flagship for gate-based computation, with improved cross-resonance gate fidelities over prior generations. IBM has publicly committed to a roadmap targeting fault-tolerant quantum computing via its Condor/Flamingo/Kookaburra architecture series. Commercial access is provided through the IBM Quantum Platform, with a free Open Plan tier for educational and research use and premium (pay-per-second) access for higher-priority backends. IBM Quantum Network members — a consortium of enterprises, universities, and research labs — receive dedicated access and co-development opportunities. (Verify current qubit counts and roadmap milestones at research.ibm.com/quantum-computing.)

**Google Quantum AI**
Google's Willow processor (105 qubits, announced December 2024) demonstrated below-threshold error correction — a landmark result published in *Nature* — showing that adding more qubits reduced rather than compounded error rates under a surface code. This was widely interpreted as a critical proof point for the viability of fault-tolerant quantum computing. Google's hardware is not broadly commercially available; access is primarily through research partnerships and the Google Quantum AI program. Limited access is available via Google Cloud for qualified research collaborators. (Verify current access program details at quantumai.google.)

**Amazon Web Services — Amazon Braket**
AWS Braket is a hardware-agnostic cloud marketplace rather than a hardware manufacturer. It provides unified API access to multiple quantum hardware backends including IonQ, Rigetti, IQM, and QuEra systems, as well as classical simulation environments. Braket's significance is as a distribution channel: it lowers the barrier for enterprises to experiment across modalities without vendor lock-in. Braket charges per-task and per-shot fees that vary by hardware provider. (Current rates: see Section 3.)

---

### 1.2 Trapped-Ion Qubits

Trapped-ion systems offer the highest gate fidelities commercially available as of 2026, at the cost of slower gate speeds compared to superconducting systems. They are particularly well-suited to applications requiring high-accuracy circuits on moderate qubit counts.

**IonQ**
IonQ (NASDAQ: IONQ) operates the Forte and Aria commercial systems, with Forte representing their current flagship. IonQ publishes an "Algorithmic Qubit" (AQ) metric — a compressed measure of effective computational power — in addition to physical qubit counts. IonQ systems are accessible via AWS Braket, Azure Quantum, and Google Cloud, making them one of the most broadly distributed quantum hardware providers. (Verify current AQ ratings and system availability at ionq.com/systems.)

**Quantinuum**
Quantinuum (a merger of Honeywell Quantum Solutions and Cambridge Quantum) operates the H-series trapped-ion systems. As of April 2026, the H2 system (56 qubits) holds the record for highest two-qubit gate fidelity commercially available — reported at approximately 99.9% (verify current at quantinuum.com). Quantinuum's commercial model is primarily enterprise contracts rather than broad public cloud access, though access is available through Azure Quantum. Quantinuum also develops InQuanto (quantum chemistry software) and TKET (compiler/optimization toolchain), positioning it as a full-stack vendor.

**Oxford Ionics**
Oxford Ionics is developing a chip-scale trapped-ion architecture designed to be manufacturable using semiconductor fabrication processes. Unlike most trapped-ion systems that require large vacuum chambers, Oxford Ionics' approach integrates ion traps onto silicon chips. As of April 2026, the company is in the hardware scaling phase with no public cloud access. Their differentiated value proposition is compatibility with existing chip manufacturing infrastructure, which could enable cost-effective scaling. (Verify current system status at oxionics.com.)

---

### 1.3 Neutral-Atom Qubits

Neutral-atom (also called neutral-atom arrays or Rydberg atom) systems have emerged as a competitive modality for both analog quantum simulation and gate-based computation. They offer native long-range connectivity — a structural advantage over superconducting systems where coupling is nearest-neighbor.

**QuEra Computing**
QuEra's Aquila system (256 physical qubits) is the largest commercially accessible quantum processor by physical qubit count as of April 2026. Aquila operates primarily in analog mode for quantum simulation. QuEra has demonstrated a hybrid digital-analog approach and has published results on utility-scale quantum simulations of magnetic systems. Commercial access is available via AWS Braket. QuEra has received investment from the Defense Advanced Research Projects Agency (DARPA) and venture capital. (Verify current qubit count and access at quera.com.)

**Pasqal**
Pasqal (France) operates the Fresnel neutral-atom processor and is pursuing vertical integration into specific industry verticals including logistics optimization and energy grid simulation. Pasqal is one of the flagship companies of the European quantum computing ecosystem and has received funding through the French government's quantum plan and EU Horizon programs. Limited cloud access is available for research collaborators. (Verify current system and access at pasqal.com.)

**Atom Computing**
Atom Computing announced a 1,180 physical qubit neutral-atom system in 2023, the largest announced physical qubit count for any modality at the time. The company's focus is fault-tolerant quantum computing — using large physical qubit counts to encode logical qubits with high redundancy under quantum error correction. As of April 2026, commercial cloud access has not been broadly launched. (Verify current system status at atom-computing.com.)

---

### 1.4 Photonic Qubits

Photonic quantum computing encodes qubits in photons (particles of light). Key advantages include room-temperature operation and natural compatibility with fiber-optic quantum networking. The primary challenge is the difficulty of deterministic photon-photon interactions required for universal gate-based computation.

**PsiQuantum**
PsiQuantum is pursuing a fault-tolerant photonic quantum computer at scale, with a manufacturing partnership with GlobalFoundries (one of the world's largest semiconductor fabs). The company's thesis is that photonic qubits can be manufactured using existing silicon photonics processes at the scale required for fault-tolerant operation — potentially millions of physical qubits. As of April 2026, PsiQuantum has no publicly accessible cloud system; the company is in the hardware development and fab integration phase. Notable government contracts include partnerships with Australia and the US government. (Verify current status at psiquantum.com.)

**Xanadu**
Xanadu's Borealis system demonstrated photonic quantum advantage in 2022 (*Nature*, June 2022) on a Gaussian boson sampling task. Xanadu provides cloud access via Xanadu Cloud and is the primary developer of PennyLane, a widely-used open-source quantum machine learning framework. Xanadu's commercial strategy combines hardware access with software tooling. (Verify current system and pricing at cloud.xanadu.ai.)

---

### 1.5 Topological Qubits

Topological qubits are theorized to offer intrinsic error protection by encoding quantum information non-locally in the topology of the system, potentially reducing the overhead required for error correction. As of April 2026, this modality remains the most pre-commercial of those listed here.

**Microsoft**
Microsoft announced a topological qubit milestone in February 2025, published in *Nature*: the demonstration of a topological superconducting phase in a semiconductor nanowire device, a prerequisite for the Majorana-based topological qubit design. This was an important scientific milestone, though commercial topological quantum hardware remains multi-year away. Microsoft's Azure Quantum platform currently provides access to IonQ and Quantinuum hardware, as well as the Azure Quantum Elements research program. Microsoft has stated a long-term goal of integrating topological qubits into Azure Quantum. (Verify current roadmap at azure.microsoft.com/quantum.)

---

## Section 2: Qubit Counts and Fidelity Benchmarks

*As of April 2026. **These numbers change quarterly.** The table structure is evergreen; the specific values are not. Verify all figures at vendor websites before citing in research or course materials.*

*2Q Fidelity = best reported two-qubit gate fidelity. Coherence Time = T2 (dephasing time), approximate. QV = Quantum Volume where published. "—" = not published or not applicable for the modality.*

| Vendor | System | Physical Qubits | Best 2Q Fidelity | Coherence Time | Quantum Volume | Cloud Access |
|--------|--------|----------------|-----------------|----------------|---------------|--------------|
| IBM Quantum | Heron r2 | 133 | ~99.5% (verify) | ~300 µs (verify) | — (new metric) | Yes (IBM Quantum Platform) |
| Google Quantum AI | Willow | 105 | ~99.7% (verify) | ~100 µs (verify) | — | Limited (research) |
| IonQ | Forte | 36 (AQ 35+) | ~99.9% (verify) | >1 hour (verify) | — | Yes (Braket, Azure, GCP) |
| Quantinuum | H2 | 56 | ~99.9% (verify) | >1 second (verify) | — | Yes (Azure Quantum) |
| Oxford Ionics | Undisclosed | TBD | ~99.9% claimed | TBD | — | No |
| QuEra | Aquila | 256 | N/A (analog) | ~1 ms (verify) | — | Yes (AWS Braket) |
| Pasqal | Fresnel | 100+ (verify) | ~99% (verify) | ~1 ms (verify) | — | Limited |
| Atom Computing | Gen 2 | 1,180 announced | TBD | TBD | — | No |
| Xanadu | Borealis | 216 squeezed modes | N/A (photonic) | N/A | — | Yes (Xanadu Cloud) |
| PsiQuantum | Pre-commercial | N/A | N/A | N/A | — | No |
| Microsoft | Topological (dev) | Pre-commercial | N/A | N/A | — | No (Azure: IonQ/Quantinuum backends) |

**Notes on this table:**
- IBM retired the Quantum Volume metric for their newer processors, replacing it with CLOPS (Circuit Layer Operations Per Second) and other benchmarks. Expect metric evolution across vendors.
- Trapped-ion coherence times are orders of magnitude longer than superconducting systems but gate speeds are slower (~milliseconds vs ~nanoseconds). Raw coherence time is not a direct performance comparator across modalities.
- "Physical qubits" is not a fair cross-modality comparison: 56 high-fidelity trapped-ion qubits can outperform 1,000 noisy superconducting qubits on many algorithms.
- Neutral-atom qubit counts include both "storage" and "gate" qubits in some systems; definitions vary.

---

## Section 3: Cloud Quantum Pricing

*As of April 2026. Pricing changes frequently and without notice. Always verify at provider pricing pages before budget planning. The TCO framework in Chapter 3 is designed to accommodate any price update.*

### 3.1 IBM Quantum Platform

IBM offers two primary access tiers:

- **Open Plan (Free):** Access to a selection of IBM Quantum systems (typically 5–27 qubit processors) with no cost. Subject to queue times. Suitable for coursework, exploration, and algorithm development.
- **Pay-as-you-go / Premium:** Access to larger, higher-performance backends billed per runtime second. Premium plans include priority access and dedicated systems for enterprise customers.

IBM Quantum Network membership provides dedicated system access, co-development, and support — pricing is contract-based and not publicly listed. (Verify current Open Plan system list and Premium pricing at quantum.ibm.com/pricing.)

### 3.2 AWS Braket

AWS Braket uses a two-component pricing model: a **per-task fee** (charged each time a circuit is submitted) plus a **per-shot fee** (charged per execution of the circuit). Rates vary by hardware provider:

| Provider | Per-Task Fee | Per-Shot Fee | Notes |
|----------|-------------|-------------|-------|
| IonQ Aria | \$0.30 (verify) | \$0.01 (verify) | Trapped-ion |
| IonQ Forte | \$0.30 (verify) | \$0.01 (verify) | Trapped-ion (higher AQ) |
| Rigetti | \$0.35 (verify) | \$0.00035 (verify) | Superconducting |
| IQM | \$0.30 (verify) | \$0.00145 (verify) | Superconducting (EU) |
| QuEra Aquila | \$0.01/µs (verify) | N/A (analog) | Neutral-atom, time-based |

Classical simulation on Braket (SV1, TN1, DM1) is billed separately by simulation type and circuit size.

Braket charges also apply to classical processing time within quantum tasks. Budget planning should account for shot count × task overhead, not just hardware time. (Verify current rates at aws.amazon.com/braket/pricing.)

### 3.3 Azure Quantum

Azure Quantum offers two models depending on the hardware provider:

- **Azure Quantum Credits:** Microsoft provides free credits (\$500–\$10,000+) for new accounts and research programs. Useful for academic coursework and prototyping.
- **Pay-as-you-go:** After credits are consumed, billing is per-shot or per-eHQC (Quantinuum's unit).

| Provider | Pricing Unit | Approximate Rate | Notes |
|----------|-------------|-----------------|-------|
| IonQ (Aria) | Per shot | \$0.00220 (verify) | |
| IonQ (Forte) | Per shot | \$0.00220 (verify) | |
| Quantinuum H2 | Per eHQC | \$12.50–\$16.00 (verify) | Enterprise; eHQC = H-Series Quantum Credit |
| Microsoft (simulation) | Per hour | Varies | Classical simulation |

Quantinuum's eHQC pricing reflects the high fidelity premium of trapped-ion hardware. A single H2 circuit run can cost more than thousands of Braket IonQ shots; plan budgets accordingly. (Verify current rates at azure.microsoft.com/pricing/details/azure-quantum.)

### 3.4 Google Cloud Quantum AI

As of April 2026, Google has not launched a broadly public pay-per-use quantum hardware service. Access to Google's quantum processors (Willow and predecessors) is through:

- **Research partnerships:** Academic and enterprise researchers apply for access through the Google Quantum AI research program.
- **Google Cloud:** Google has announced integrations with Google Cloud for quantum-classical hybrid workflows, but broad commercial hardware access has not been publicly priced.

(Verify current access model at cloud.google.com/quantum-computing.)

### Pricing Context for Instructors

A typical student exercise running 1,000 shots on a 20-qubit circuit costs approximately \$0.30–\$1.00 on AWS Braket (IonQ or Rigetti), well within IBM Quantum's free Open Plan for comparable circuit depths. For classroom use, the IBM Open Plan is the lowest-friction starting point. For modality comparison exercises requiring trapped-ion or neutral-atom hardware, budget \$5–\$20 per student for a semester's experimentation — but verify current rates, as these have changed multiple times in 2023–2025.

---

## Section 4: NIST Post-Quantum Cryptography Adoption Timeline

*As of April 2026. Standards finalization dates are confirmed; adoption deadlines are regulatory mandates subject to revision.*

### 4.1 NIST PQC Standards — Finalized

After an eight-year standardization process (2016–2024), NIST finalized the first three post-quantum cryptographic standards in August 2024:

| Standard | Algorithm | Type | Finalized |
|----------|-----------|------|-----------|
| FIPS 203 | ML-KEM (Module-Lattice Key Encapsulation) | Key encapsulation / key exchange | August 2024 (confirmed) |
| FIPS 204 | ML-DSA (Module-Lattice Digital Signature) | Digital signatures | August 2024 (confirmed) |
| FIPS 205 | SLH-DSA (Stateless Hash-Based Digital Signature) | Digital signatures | August 2024 (confirmed) |

A fourth standard (FIPS 206, based on FALCON) was in final draft as of April 2026; verify finalization status at csrc.nist.gov/pqc.

These standards replace or supplement:
- RSA-2048, RSA-4096 (key exchange and signatures) → ML-KEM + ML-DSA
- ECDSA, ECDH (elliptic curve) → ML-KEM + ML-DSA
- SHA-based signatures → SLH-DSA (for hash-based use cases)

### 4.2 CNSA 2.0 (NSA Commercial National Security Algorithm Suite 2.0)

The NSA's CNSA 2.0 directive (issued September 2022) mandates migration to post-quantum algorithms for all US National Security Systems (NSS). The mandate covers classified and unclassified NSS, defense contractors, and critical infrastructure operators in the national security supply chain.

Key algorithms mandated under CNSA 2.0:
- **Key exchange / encryption:** CRYSTALS-Kyber (ML-KEM) — minimum 256-bit security
- **Digital signatures:** CRYSTALS-Dilithium (ML-DSA) — minimum 256-bit security
- **Software/firmware signing:** LMS / XMSS (hash-based) — immediate priority
- **Symmetric:** AES-256 (already quantum-resistant for foreseeable future)

### 4.3 EU NIS2 Directive

The EU Network and Information Security 2 Directive (NIS2, effective October 2024) does not mandate specific post-quantum algorithms but requires that covered entities assess and address risks from cryptographic vulnerabilities, including quantum threats. The practical implication: EU critical infrastructure operators and digital service providers must include quantum cryptographic risk in their cybersecurity risk management programs. National transposition into member state law has been ongoing through 2025. (Verify current implementation status per member state at enisa.europa.eu.)

### 4.4 Corporate Adoption Curve (2025–2030 Projection)

*This is a projection based on regulatory mandates, not confirmed market data. Verify with current analyst reports (Gartner, McKinsey Quantum Technology Report, The Quantum Insider).*

| Period | Expected Activity |
|--------|------------------|
| 2025–2026 | Cryptographic inventory completion; identification of "harvest now, decrypt later" exposure. Early adopters (finance, defense contractors) begin PQC pilots. |
| 2026–2027 | First production PQC deployments in US federal systems (CNSA 2.0 Phase 2). TLS 1.3 with hybrid PQC becoming available in major cloud TLS stacks. |
| 2027–2028 | Enterprise software vendors ship PQC-ready libraries (OpenSSL, BoringSSL, AWS SDK). Financial sector PQC pilots become production. |
| 2028–2030 | Broad enterprise migration underway. Legacy system remediation at scale. CNSA 2.0 Phase 3 deadline approaches. |
| Post-2030 | Legacy RSA/ECC deprecated in most regulated sectors. PQC-only mandatory in US NSS and EU critical infrastructure. |

---

## Section 5: Regulatory Deadlines

*As of April 2026. Regulatory timelines are subject to revision by issuing bodies. Verify current status at official government and standards body websites.*

| Deadline | Regulation | Requirement | Sector | Source |
|----------|-----------|-------------|--------|--------|
| Aug 2024 | NIST FIPS 203/204/205 | PQC standards finalized | Global (voluntary adoption) | NIST (confirmed) |
| Oct 2024 | EU NIS2 | Cybersecurity risk management (including quantum) in effect | EU critical infrastructure, digital services | European Commission (confirmed) |
| 2025 | CNSA 2.0 Phase 1 | Cryptographic inventory completion; identify quantum-vulnerable systems | US national security systems | NSA (verify current guidance) |
| 2025 | NIST IR 8547 | Transition away from vulnerable algorithms; planning documentation | US federal agencies | NIST (verify current) |
| 2026 | DORA (EU Digital Operational Resilience Act) | ICT risk management including cryptographic resilience; applies to financial entities | EU financial services | European Parliament (confirmed) |
| 2026 | CNSA 2.0 (software/firmware) | New software/firmware must use LMS/XMSS for signing | US NSS software supply chain | NSA (verify current) |
| 2027 | CNSA 2.0 Phase 2 | New systems and upgrades must be PQC-ready | US national security systems | NSA (verify current) |
| 2028 | NIST transition deadline (proposed) | End of FIPS approval for RSA/ECC in new federal systems | US federal agencies | NIST (verify; subject to update) |
| 2030 | CNSA 2.0 Phase 3 | All national security systems migrated to PQC | US national security systems | NSA (verify current) |
| 2030 | Basel IV / financial sector | Quantum cryptographic risk expected in operational risk frameworks | Global financial institutions | BIS/Basel Committee (verify current guidance) |
| 2033 | CNSA 2.0 (legacy systems) | Final deadline for legacy system migration | US national security systems | NSA (verify current) |

**Instructor note:** The CNSA 2.0 timeline has been subject to clarification since initial publication. Always verify the current NSA CNSA 2.0 FAQ at nsa.gov before citing specific phase deadlines. The 2025 "inventory completion" deadline is widely reported but enforcement mechanisms vary by agency.

---

## Section 6: M&A and Investment Activity

*Covering approximately April 2025 – April 2026. **This section ages fastest.** Refresh at the start of each course offering. Sources: The Quantum Insider (quantuminsider.com), company press releases, and financial filings.*

### 6.1 Notable Government Investment Programs (Active as of April 2026)

**United States**
- **CHIPS and Science Act (2022):** Includes quantum information science funding; National Quantum Initiative reauthorization (2023) extends federal quantum R&D funding through 2028. Department of Energy quantum network centers ongoing.
- **DARPA Quantum Benchmarking Initiative / Underexplored Systems for Utility-Scale Quantum (US2QC):** DARPA programs evaluating which hardware modalities can reach utility-scale computation and by when. PsiQuantum, Microsoft, and others have received contracts under these programs. (Verify current program status at darpa.mil.)
- **NSF Quantum Leap Challenge Institutes:** University-based research centers with multi-year funding commitments.

**European Union**
- **EU Quantum Flagship:** €1 billion+ 10-year program (2018–2028); funding Pasqal, IQM, eleQtron, and other European vendors.
- **French National Quantum Plan (France 2030):** €1.8 billion committed through 2030; supports Pasqal, Alice & Bob, and others.
- **German Quantum Computing Initiative:** DLR and government partnerships with IQM and others.

**Australia**
- **PsiQuantum partnership:** Australian government announced a partnership with PsiQuantum to co-develop a fault-tolerant quantum computer, with significant government funding (verify current status as terms have evolved).

### 6.2 Large Funding Rounds (Approximate; verify at crunchbase.com / The Quantum Insider)

*Note: funding round data in the quantum sector is frequently revised. The figures below are based on publicly announced rounds and should be verified.*

| Company | Round/Event | Approximate Amount | Date | Notes |
|---------|------------|-------------------|------|-------|
| PsiQuantum | Government + private | \$620M+ total raised (verify) | Ongoing | Includes Australian/US government co-investment |
| Quantinuum | Series A equivalent | \$300M (verify) | 2023 (ongoing rounds) | Honeywell retains majority stake |
| IonQ | Public company (IONQ) | Market cap ~\$2–4B (verify) | Ongoing | NYSE-listed; revenue growing |
| QuEra Computing | Series A | \$230M (verify) | 2024 (verify) | Led by Google and others |
| Atom Computing | Series B | \$60M (verify) | 2023 | Focus on fault-tolerant systems |
| Alice & Bob (EU) | Series B | \$104M (verify) | 2024 (verify) | Cat-qubit / superconducting |
| Nord Quantique (CA) | Series A | \$17M (verify) | 2024 (verify) | Bosonic qubits |
| Pasqal | Series B | \$109M (verify) | 2023 (verify) | European neutral-atom leader |

### 6.3 Notable Partnerships and Acquisitions (2025–2026)

- **IBM + enterprise integrations:** IBM has expanded its Quantum Network with new financial services and automotive partners (verify current partner list at ibm.com/quantum/network).
- **Microsoft + Quantinuum:** Deep partnership for Azure Quantum integration and joint research into topological qubits using Quantinuum hardware as a testbed. (Announced 2023; verify current scope.)
- **AWS Braket expansions:** AWS has continued adding hardware providers to Braket; verify current provider list at aws.amazon.com/braket.
- **Google Quantum AI + universities:** Google expanded its quantum research partnership program; verify at quantumai.google.

**Instructor note:** The M&A landscape in quantum computing is consolidating. Several smaller vendors active in 2022–2023 have been acquired or ceased operations. Before adding new companies to this section, verify they are still independent entities.

---

## Section 7: How to Refresh This Appendix

*For instructors updating this appendix at the start of each course offering.*

### 7.1 Estimated Time

**2–4 hours per year** for a thorough refresh. Sections 1–3 and Section 6 will take the most time. Sections 4–5 can typically be verified in 30–45 minutes.

### 7.2 Sources to Check

**Hardware and vendor status:**
- IBM Quantum blog: research.ibm.com/blog (roadmap updates, new processor announcements)
- Google Quantum AI blog: quantumai.google/learn/map (research results and roadmap)
- IonQ investor relations: ionq.com/investors (quarterly earnings include system performance updates)
- Quantinuum blog: quantinuum.com/news
- The Quantum Insider: quantuminsider.com (industry news, funding rounds, market data)
- arXiv quant-ph: arxiv.org/list/quant-ph (preprints on new results; filter by institution)

**Pricing:**
- AWS Braket: aws.amazon.com/braket/pricing
- Azure Quantum: azure.microsoft.com/pricing/details/azure-quantum
- IBM Quantum: quantum.ibm.com/pricing
- Xanadu Cloud: cloud.xanadu.ai (pricing tab)

**Regulatory and standards:**
- NIST PQC: csrc.nist.gov/Projects/post-quantum-cryptography
- NSA CNSA 2.0: nsa.gov/Cybersecurity/CNSA-2-0 (check for updated FAQs and revised timelines)
- EU NIS2 implementation: enisa.europa.eu

**Market analysis:**
- McKinsey Quantum Technology Report (annual, typically Q1–Q2)
- BCG Quantum Advantage report (annual)
- Gartner Hype Cycle for Quantum Computing (annual)
- The Quantum Insider Market Reports: quantuminsider.com/reports

### 7.3 Which Sections Change Most Frequently

**High volatility (check every offering):**
- Section 1: Vendor list (new entrants, acquisitions, system launches)
- Section 2: Qubit counts and fidelity table (update quarterly by vendors)
- Section 3: Pricing (has changed multiple times per year for some providers)
- Section 6: M&A and investment (constant activity)

**Medium volatility (spot-check; likely stable year-to-year):**
- Section 1 narrative descriptions (update when major milestones are hit)
- Section 5: Regulatory deadlines (occasionally revised; verify NSA CNSA 2.0 phases specifically)
- Section 4.2: CNSA 2.0 mandate details

**Low volatility (likely unchanged; verify once):**
- Section 4.1: NIST FIPS 203/204/205 finalization dates (confirmed history)
- Section 4.3: Corporate adoption curve (projection; update framing if market has materially diverged)

### 7.4 Refresh Procedure

1. **Check the version stamp** at the top of this appendix. Confirm you are editing the current version.
2. **Work section by section** in order. Do not skip ahead — each section informs the next.
3. **For each number in Section 2:** Visit the vendor's current product page. Update the figure, change the annotation from "(verify current)" to "(confirmed, [Month Year])," and note the source in a comment or footnote.
4. **For pricing in Section 3:** Screenshot or copy the current pricing page as of your refresh date. Store in the course materials folder for reference. Update the table figures.
5. **For Section 6:** Search The Quantum Insider for "funding rounds [year]" and "acquisitions [year]." Add new significant rounds (\$50M+). Archive old rounds by moving them to a commented block or deleting if more than 2 years old.
6. **For regulatory deadlines in Section 5:** Check NSA CNSA 2.0 and NIST transition pages for any deadline updates. Add new rows for newly enacted regulations.
7. **Update the version stamp** at the top: change the version number (e.g., v1.0 → v2.0) and update the date.
8. **Commit the update** with a descriptive commit message (e.g., "Appendix F: Market Snapshot v2.0 — April 2027") so the version history is preserved in the book repository.

### 7.5 What NOT to Change

Do not modify the chapter text based on information gathered during this refresh. If a chapter contains a statement that you believe is now factually outdated (e.g., "as of this writing, no quantum computer has demonstrated fault-tolerant operation"), flag it for the author rather than editing it. The chapters are intentionally written to be principle-based; apparent conflicts with current facts often reflect a difference in framing rather than an error.

---

*End of Appendix F. Version 1.0 — April 2026.*
*Next scheduled refresh: April 2027.*
*Questions about this appendix: contact the book maintainer or file an issue in the book repository.*
