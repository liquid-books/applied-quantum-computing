---
title: "Chapter 5: The Cryptocalypse — Y2Q and the Security Imperative"
subtitle: "The Attack Is Already Happening. The Question Is Whether You Finish Before They Decrypt."
short_title: "Ch. 5: The Cryptocalypse"
description: "The cryptographic layer protecting every contract, payment, and medical record is on a migration clock that most organizations have not yet started. This chapter explains Shor's algorithm, NIST PQC standards, the Mosca Inequality, and how to build a crypto-agility roadmap before Q-Day arrives."
label: ch-05-cryptocalypse-y2q
tags: [post-quantum cryptography, Shor's algorithm, NIST PQC, crypto-agility, Mosca Inequality, Y2Q, cybersecurity, RSA]
---

# Chapter 5: The Cryptocalypse — Y2Q and the Security Imperative

:::{figure} ../images/ch05-explainer-infographic.png
:name: fig-ch05-explainer-infographic
:alt: Chapter 5 explainer infographic showing the road from today's RSA encryption to Q-Day, with the Mosca Inequality, NIST PQC standards, and crypto-agility framework.
:width: 100%

**The Cryptocalypse at a Glance.** Today's RSA encryption is protected by a math problem that classical computers cannot solve in any reasonable timeframe. Shor's algorithm — running on a sufficiently powerful quantum computer — dissolves that protection in minutes. The organizations that will survive Q-Day are the ones migrating now, while the clock is still ticking in their favor.
:::

> *"The first trillion dollars of quantum value will come not from a new drug or a new battery but from the silent, unglamorous work of replacing the locks on every door before someone else gets a key."*

The internet you used this morning to check your bank balance, send a contract, or access a patient record was secured by mathematics invented in the 1970s. That mathematics works beautifully — until it doesn't. Quantum computing doesn't bend those locks. It evaporates them. This chapter is the story of what that means for every organization on earth, why the threat is not hypothetical, and what leaders must do right now.

---

## 5.1 Opening Scene: The Theft That Already Happened

Somewhere right now, a nation-state actor is harvesting encrypted traffic it cannot yet read. It isn't wasting disk space. It is waiting.

The operation is methodical and patient. Automated systems tap fiber backbones, mirror TLS handshakes, copy encrypted API calls between hospital systems, intercept the SSL-wrapped PDFs of merger agreements, and quietly vacuum up the encrypted transactions flowing between financial clearing houses. The data is stored in cold storage at pennies per gigabyte. None of it is readable today. None of it needs to be.

This is **Harvest Now, Decrypt Later** — and it is almost certainly happening to your company.

The attackers are not guessing. They know that quantum computers capable of running Shor's algorithm at scale are coming. The intelligence community's best estimates cluster around a window beginning in the early 2030s, with some assessments pulling that forward. The attackers also know something else: your organization's migration to post-quantum cryptography will take years. Every year you delay is one more year of sensitive data they can add to the archive.

The question is not whether your data is being harvested. The question is whether you will finish your migration before they get the key.

---

## 5.2 The Single Idea

::::{admonition} The Single Idea of This Chapter
:class: important

The cryptographic layer beneath nearly every modern contract, payment, medical record, and supply chain is on a multi-year migration clock. Organizations that finish late will not know they were early targets until five years after the fact. The first obligation of any leader who understands quantum computing is to start that migration — today.
::::

---

## 5.3 How Encryption Works Today — and Why It Is Brilliant

### The Padlock Model

You already understand combination locks. You set a combination and tell nobody. Anyone can snap the lock shut — only you can open it. RSA encryption is the same idea, but with a mathematical twist so clever it borders on sorcery.

Here is the bridge: RSA's security rests on a simple asymmetry. Multiplying two large prime numbers together is trivially easy. A computer does it in microseconds. But starting from the *product* and working backwards to find those two original primes — that is called **prime factorization**, and for numbers with 2,048 binary digits (RSA-2048), it is computationally intractable for any classical machine. The best classical algorithms would require more operations than there are atoms in the observable universe, running for longer than the current age of the universe. In practice: unbreakable.

So the padlock is a number — a very large product of two primes. Your **public key** is that product, shared with the world. Your **private key** is one of the two primes, kept secret. Anyone can encrypt data to you using the product. Only you can decrypt it, because only you know the prime.

:::{figure} ../images/ch05-rsa-encryption-analogy.png
:name: fig-rsa-encryption-analogy
:alt: RSA encryption illustrated as a padlock secured by two prime numbers, with classical computers unable to factor large products.
:width: 90%

**RSA Encryption: The Padlock Whose Strength Is a Math Problem.** The product of two large primes is easy to compute but nearly impossible to reverse. Classical computers would take longer than the age of the universe to crack RSA-2048 by brute force.
:::

Where the analogy breaks down: real padlocks can be physically cut. RSA cannot be "cut" — it can only be mathematically solved. This matters because it means a future mathematical breakthrough, not a physical tool, is the threat.

::::{admonition} 🔥 The Weight of This
:class: warning

Right now, every HTTPS connection you make, every banking transaction, every encrypted email, every signed software update is protected by this padlock model. RSA and its cousin ECC (Elliptic Curve Cryptography) underpin essentially all of the internet's trust infrastructure. When that foundation cracks — not if, when — the consequences will not be a data breach at one company. They will be systemic. The entire trust layer of the digital economy dissolves simultaneously, unless we replace it first.
::::

---

## 5.4 Shor's Algorithm: The Master Key

### The Quantum Shortcut

You understand the problem Shor's algorithm solves — factoring large numbers. Now imagine someone hands you not a better calculator, but a fundamentally different kind of machine: one that can try all possible factor combinations simultaneously, then uses a phenomenon called **quantum interference** to amplify the correct answer and cancel out the wrong ones.

That is Shor's algorithm. Published by Peter Shor in 1994, it doesn't try harder than classical computers. It uses quantum superposition to explore an astronomically large solution space in parallel, then exploits interference to concentrate probability on the right answer. The mathematical result: a quantum computer running Shor's algorithm finds the prime factors of a large number in **polynomial time** — meaning the time required grows modestly with the size of the number, not exponentially. Instead of longer than the age of the universe, a fault-tolerant quantum computer running Shor's on RSA-2048 would take on the order of hours.

:::{figure} ../images/ch05-shors-algorithm-effect.png
:name: fig-shors-algorithm-effect
:alt: Shor's algorithm effect showing quantum computer using quantum interference to break RSA encryption that would take classical computers billions of years.
:width: 90%

**Shor's Algorithm: From Intractable to Polynomial.** Classical computers must try factor combinations sequentially. Shor's algorithm uses quantum interference to find prime factors exponentially faster — reducing RSA-2048's "age of the universe" protection to hours on a fault-tolerant quantum machine.
:::

Where the analogy breaks down: Shor's requires a fault-tolerant quantum computer with thousands of logical qubits — something we do not yet have. Current quantum computers have too much noise to run Shor's at meaningful scale. But that engineering barrier is narrowing, year by year, with billions of dollars of investment.

::::{admonition} 🔥 The Weight of This
:class: danger

Every RSA-protected system on earth — banking infrastructure, healthcare records, military communications, supply chain software, the certificate authorities that tell your browser which websites to trust — becomes breakable the day a fault-tolerant quantum computer runs Shor's at scale. This is not theoretical risk management. This is a known vulnerability with a known countdown clock. The only uncertainty is the exact date of detonation.
::::

::::{admonition} Grover's Algorithm: The Symmetric Threat
:class: note

Shor's algorithm breaks *asymmetric* cryptography (RSA, ECC) completely. **Grover's algorithm** — a different quantum algorithm — poses a more moderate but real threat to *symmetric* cryptography (AES, SHA). Grover's provides a quadratic speedup for searching unstructured data. In practical terms: AES-128, considered impervious today, effectively becomes AES-64 against a quantum attacker using Grover's — a key length that current classical computers can brute-force. The fix is straightforward: double your key length. AES-256 becomes the new AES-128. But this requires finding every AES-128 deployment in your organization and upgrading it — which, in large enterprises, is non-trivial.

| Algorithm | Threat Type | Effect on Current Crypto | Mitigation |
|-----------|-------------|--------------------------|------------|
| Shor's | Asymmetric (RSA, ECC) | Completely broken | Migrate to PQC |
| Grover's | Symmetric (AES, SHA) | Security halved | Double key length |

::::

---

## 5.5 Harvest Now, Decrypt Later: The Theft Already in Progress

### The Patient Burglar

You already know what a burglar is. A burglar breaks in, takes your valuables, and leaves. Now imagine a different kind of burglar — one who doesn't need to break in at all. This burglar walks past your building every day, photographs every safe through the window, and stores those photographs in a warehouse. Today, the burglar cannot open the safes. But they know a tool is coming — a tool that will open every safe in those photographs with trivial effort. So they wait.

This is **Harvest Now, Decrypt Later**. The "photographs" are encrypted data packets. The warehouse is cold storage. The safe-cracking tool is the quantum computer.

:::{figure} ../images/ch05-harvest-now-decrypt-later.png
:name: fig-harvest-now-decrypt-later
:alt: Harvest Now Decrypt Later attack diagram showing nation-state actors storing encrypted traffic today to decrypt with quantum computers tomorrow.
:width: 90%

**Harvest Now, Decrypt Later: The Theft in Progress.** Adversaries are collecting encrypted traffic today — TLS sessions, VPN tunnels, encrypted file transfers — and storing it for future quantum decryption. The encryption protecting that data is today's RSA and ECC, which Shor's algorithm will dissolve.
:::

Where the analogy breaks down: a burglar takes physical objects, which are then missing. Harvest Now, Decrypt Later is entirely invisible — you have no idea your data has been copied. The logs show nothing unusual. Your security team has nothing to alert on.

::::{admonition} 🔥 The Weight of This
:class: danger

Your most sensitive data from the past five years may already be in adversarial hands — a government intelligence service, a sophisticated criminal organization, a geopolitical rival — sitting in cold storage, waiting. Mergers-and-acquisitions strategy that hasn't been announced yet. Patient genomic data with a 30-year relevance horizon. Defense procurement specifications. Long-term supply contracts. Every byte of encrypted traffic you have sent over the past five years is a candidate. The attack is not coming. It has already happened. Only the decryption is in the future.
::::

---

## 5.6 NIST PQC Standards: The New Locks

The good news: the world's cryptographic community recognized this threat two decades ago. The National Institute of Standards and Technology (NIST) ran a multi-year, global competition to identify encryption algorithms that are secure against *both* classical and quantum computers. In 2024, after eight years of rigorous cryptanalysis, NIST finalized the first three post-quantum cryptography (PQC) standards.

### The Three Standards

`````{tab-set}
````{tab-item} ML-KEM (Key Encapsulation)
**ML-KEM** (Module Lattice Key Encapsulation Mechanism) — formerly CRYSTALS-Kyber — is the primary algorithm for **key exchange**. It replaces the RSA and ECC key exchange mechanisms used to establish secure TLS connections.

**What it does:** When your browser connects to a bank's website over HTTPS, ML-KEM is the algorithm that securely establishes a shared secret between the two parties — a secret that quantum computers cannot intercept or derive.

**Why it won:** ML-KEM is based on the hardness of problems in **lattice mathematics** — specifically, the "Learning With Errors" (LWE) problem. No known quantum algorithm provides a meaningful speedup for this problem.

**Performance:** ML-KEM is fast — faster than RSA for key encapsulation — with modest bandwidth overhead. It is already deployed in Google Chrome, Cloudflare, and AWS experimental TLS configurations.
````
````{tab-item} ML-DSA (Digital Signatures)
**ML-DSA** (Module Lattice Digital Signature Algorithm) — formerly CRYSTALS-Dilithium — handles **digital signatures**. It replaces ECDSA and RSA signatures used to authenticate software, documents, certificates, and messages.

**What it does:** When your operating system verifies a software update hasn't been tampered with, or when a certificate authority vouches for a website's identity, ML-DSA is the signature algorithm that provides that assurance against a quantum adversary.

**Why it won:** Also lattice-based, with strong security proofs and excellent performance. Signature generation and verification are both fast.

**Enterprise implication:** Every code-signing pipeline, every PKI infrastructure, every certificate issuance system needs to be updated to support ML-DSA. This is not a configuration change — it is an infrastructure migration.
````
````{tab-item} SLH-DSA (Hash-Based Signatures)
**SLH-DSA** (Stateless Hash-Based Digital Signature) — formerly SPHINCS+ — provides a **hash-based alternative** for digital signatures. It relies on completely different mathematics from ML-DSA, providing algorithmic diversity.

**What it does:** SLH-DSA is designed for scenarios requiring high assurance that no future mathematical breakthrough will compromise the signature scheme. Because it relies only on hash functions (not lattice problems), it provides a hedge against unforeseen attacks on lattice mathematics.

**Why it matters:** Cryptographic monocultures are dangerous. If a breakthrough attack on lattice problems is discovered, organizations that deployed *only* lattice-based PQC would be exposed. SLH-DSA provides the fallback.

**Trade-off:** Signature sizes are significantly larger than ML-DSA, making SLH-DSA impractical for high-frequency, bandwidth-constrained applications. It is best suited for root certificate signing, long-term archives, and critical infrastructure attestation.
````
`````

:::{figure} ../images/ch05-nist-pqc-standards.png
:name: fig-nist-pqc-standards
:alt: NIST PQC standards infographic showing ML-KEM, ML-DSA, and SLH-DSA with their mathematical foundations and use cases.
:width: 90%

**NIST's 2024 PQC Standards.** After an 8-year global competition, NIST standardized three post-quantum algorithms. ML-KEM and ML-DSA are lattice-based (Learning With Errors problem). SLH-DSA provides hash-based diversity. All three are resistant to Shor's algorithm.
:::

### Why Lattice-Based Schemes Won

::::{admonition} The 9th-Grader Explanation: Lattice Cryptography
:class: tip

**What you already know:** Finding something in a haystack is hard. Finding something in a multi-dimensional haystack — imagine a haystack with thousands of dimensions, where "distance" works differently than in physical space — is nearly impossible.

**The bridge:** Lattice cryptography is built on mathematical problems that live in these high-dimensional spaces. The hardest of these problems — finding the shortest vector in a lattice with thousands of dimensions — has been studied for decades, and no known algorithm (classical *or* quantum) solves it efficiently.

**The concept:** A **lattice** is a regular grid of points in multi-dimensional space. Lattice-based crypto hides secrets in the geometry of these structures. The "Learning With Errors" problem adds noise to lattice equations, making them look like random data to an attacker — but the legitimate party, who knows the structure, can easily decode them.

**Where the analogy breaks down:** Physical jungle gyms have three dimensions. Lattice problems operate in thousands of dimensions where our physical intuition completely fails. The mathematical hardness is qualitatively different from anything in everyday experience.

**Why this matters — urgently:** The Shor's algorithm breakthrough that destroys RSA works by exploiting the specific periodic structure of prime factorization problems. Lattice problems have no such periodic structure to exploit. The quantum speedup that makes RSA breakable simply does not apply to lattice mathematics. NIST chose lattice-based schemes because they are quantum-resistant by mathematical structure — not just by current computational limits. This is as close to "future-proof" as mathematics can offer.
::::

:::{figure} ../images/ch05-lattice-cryptography.png
:name: fig-lattice-cryptography
:alt: Lattice-based cryptography visualization showing multi-dimensional grid structures that are hard for both classical and quantum computers to solve.
:width: 90%

**Lattice Mathematics: Quantum-Resistant by Structure.** Unlike RSA's prime factorization problem (which Shor's algorithm exploits via periodicity), the Shortest Vector Problem in high-dimensional lattices has no known quantum speedup. Both classical and quantum computers find it equally hard.
:::

---

## 5.7 The Mosca Inequality: Are You Already Late?

### The Visa Application

You already know how visas work. If you need a visa to travel, and visa processing takes six months, and your trip is in four months — you are already too late to apply. The correct time to apply was two months ago. The deadline does not move to accommodate your delay.

The **Mosca Inequality** — formulated by quantum cryptographer Michele Mosca — applies the same logic to cryptographic migration:

::::{prf:definition} The Mosca Inequality
:label: def-mosca-inequality

Let:
- **X** = the time until a quantum computer capable of breaking current public-key cryptography exists (time to Q-Day)
- **Y** = the time your organization needs to complete a full migration to post-quantum cryptography (migration time)
- **Z** = the time the data you are protecting today must remain confidential (data lifetime)

**If Y + Z > X, you are already late.**

Your migration must be complete *before* Q-Day arrives. Your data must remain secure for the entire duration of its useful life. If the sum of those two timelines exceeds the time until Q-Day, every day you delay compounds your exposure.
::::

:::{figure} ../images/ch05-mosca-inequality.png
:name: fig-mosca-inequality
:alt: Mosca Inequality diagram with three timeline bars showing data lifetime, migration time, and time to Q-Day, with red danger zone highlighted.
:width: 90%

**The Mosca Inequality in Practice.** If your data must stay secret for 10 years and your migration will take 7 years, you need Q-Day to be at least 17 years away — and it almost certainly isn't. Most analysts estimate Q-Day in the 2030–2035 window, meaning organizations need to have started yesterday.
:::

### Applying the Mosca Inequality: A Self-Assessment

::::{admonition} Apply It Right Now
:class: tip

For each major category of sensitive data your organization holds, ask three questions:

1. **How long must this data remain confidential?** (Medical records: 50+ years. Mergers strategy: 2–5 years. Customer PII: 7–10 years. Defense specifications: 25+ years.)
2. **How long will your complete PQC migration take?** (Average large enterprise: 5–7 years. Complex financial institution with legacy systems: 7–10 years. Global supply chain: 8–12 years.)
3. **When do most analysts think Q-Day will arrive?** (Conservative estimate: 2035. Aggressive estimate: 2030. Intelligence community: classified, but the behavior of nation-state actors implies they believe it is sooner.)

Add questions 1 and 2. If the sum exceeds question 3, you are — by the Mosca Inequality — already operating in deficit. Every quarter you delay is a quarter of your most sensitive data that will be unprotected when Q-Day arrives.
::::

Where the analogy breaks down: visa deadlines are known in advance. Q-Day has a range of estimates, not a precise date. This uncertainty cuts both ways — it might buy more time, or it might mean Q-Day arrives earlier than expected.

::::{admonition} 🔥 The Weight of This
:class: danger

Most large organizations have migration timelines of 5–10 years. If Q-Day arrives in 8 years and your migration takes 7, you needed to start last year. Many of the organizations reading this chapter have data — patient records, long-term contracts, government secrets — with lifetimes exceeding 20 years. For those organizations, even a 2040 Q-Day is too late if migration hasn't started. The Mosca Inequality is not a theoretical framework. It is a fiduciary accountability tool. Leadership that understands it and fails to act is making a documented, affirmative choice to leave sensitive data exposed.
::::

---

## 5.8 Crypto-Agility: Building the Migration Infrastructure

### The Standard Door Frame

You already understand home renovation. If every door in your house has a custom-sized frame — two inches too wide here, three inches too short there — replacing even one door requires tearing out the frame, rebuilding the wall, refinishing the drywall, and repainting. If every door has a standard frame size, you can replace any door in an afternoon. The difference is not the doors. It is the **infrastructure** around the doors.

**Crypto-agility** is the engineering discipline of building cryptographic infrastructure with standard, swappable "door frames" — abstraction layers that let you replace one cryptographic algorithm with another without rebuilding the entire system.

:::{figure} ../images/ch05-crypto-agility-framework.png
:name: fig-crypto-agility-framework
:alt: Crypto-agility framework showing four pillars: Algorithm Discovery, Inventory and Classification, Hybrid Deployment, and Migration Execution.
:width: 90%

**The Crypto-Agility Framework.** Organizations that built algorithm abstraction layers into their systems can migrate to PQC in 18 months. Organizations that hard-coded cryptographic dependencies will take 7+ years. The difference is architectural discipline, not budget.
::::

### The Four Pillars of Crypto-Agility

::::{grid} 2

:::{card} 🔍 Pillar 1: Algorithm Discovery
Build an automated inventory of every cryptographic primitive in use across your organization. Every certificate. Every TLS configuration. Every code-signing key. Every VPN tunnel. Every HSM. Every embedded system firmware. This is the six-month phase nobody wants to fund — and the phase that always reveals surprises.
:::

:::{card} 📋 Pillar 2: Classification & Prioritization
Not all cryptography carries the same risk. Classify each asset by: (a) algorithm type and key length, (b) data sensitivity, (c) data lifetime, (d) system replaceability. Apply the Mosca Inequality to each category. Generate a prioritized migration backlog.
:::

:::{card} 🔀 Pillar 3: Hybrid Deployment
Do not wait for perfect PQC implementations. Deploy **hybrid TLS** configurations that run both classical (RSA/ECC) and post-quantum (ML-KEM) key exchange simultaneously. If either succeeds, the connection is secure. This provides immediate quantum resistance for new traffic while maintaining backward compatibility with systems that haven't migrated yet.
:::

:::{card} ✅ Pillar 4: Migration Execution
Systematically replace classical algorithms with PQC equivalents, starting with the highest-risk assets identified in Pillar 2. Establish ongoing monitoring to detect cryptographic regressions (systems that revert to classical-only configurations). Build PQC requirements into all new procurement contracts.
:::

::::

Where the analogy breaks down: standard door frames are a visible, physical infrastructure choice. Cryptographic abstraction layers are invisible — you have to deliberately build them in. Most enterprise software was built without them, which is precisely why migration timelines are measured in years rather than months.

::::{admonition} 🔥 The Weight of This
:class: danger

Organizations that built crypto-agility into their systems in 2020 will complete their PQC migration in 18 months. Organizations that didn't will take 7 years and spend 10 times more — not because PQC is expensive, but because discovering, inventorying, and replacing cryptographic dependencies embedded in decade-old code, in vendor black boxes, in embedded device firmware, in legacy mainframe applications, is brutally expensive work. Every year of delay increases the remediation cost. Every year of delay also extends the Harvest Now, Decrypt Later exposure window.
::::

---

## 5.9 Regulatory and Fiduciary Exposure: The Compliance Clock

The migration imperative is not only technical. It is becoming legally mandatory — and organizations that delay face not just security exposure but regulatory sanction, insurance exclusion, and board-level fiduciary liability.

:::{figure} ../images/ch05-regulatory-timeline.png
:name: fig-regulatory-timeline
:alt: Regulatory compliance timeline showing CNSA 2.0, EU NIS2, financial sector, and cyber insurance PQC deadlines from 2024 to 2035.
:width: 90%

**The Regulatory Compliance Countdown.** CNSA 2.0 mandates PQC transition timelines for U.S. national security systems. EU NIS2 creates PQC obligations for critical infrastructure operators. Financial regulators and cyber insurers are establishing their own deadlines. Organizations that treat PQC as optional are accumulating regulatory liability.
:::

### Key Regulatory Frameworks

::::{dropdown} CNSA 2.0 — U.S. National Security Systems
**Commercial National Security Algorithm Suite 2.0** (NSA, 2022) mandates the transition of all U.S. national security systems to post-quantum cryptography on an aggressive timeline:

- **2025:** New systems must support CNSA 2.0 algorithms (ML-KEM, ML-DSA)
- **2030:** Legacy systems in national security applications must complete migration
- **2035:** All NSS must exclusively use CNSA 2.0 algorithms

While CNSA 2.0 technically applies only to national security systems, it sets the tone for federal procurement, defense contractor requirements, and critical infrastructure standards. Any organization in the federal supply chain is implicitly on this timeline.
::::

::::{dropdown} EU NIS2 Directive — Critical Infrastructure
The **EU Network and Information Security Directive 2 (NIS2)**, effective October 2024, significantly expands the scope of organizations required to maintain "state-of-the-art" cybersecurity measures — including, by implication, quantum-resistant cryptography. NIS2 covers:

- Energy, transport, health, and water infrastructure
- Digital infrastructure (cloud providers, DNS, data centers)
- Financial market infrastructure
- Public administration

Organizations that fail NIS2 compliance face fines up to €10 million or 2% of global annual turnover. As ENISA (EU's cybersecurity agency) updates its guidance to reflect PQC as a "state-of-the-art" requirement, NIS2 compliance increasingly requires a credible PQC migration plan.
::::

::::{dropdown} Financial Sector — Regulatory Signals
- **DORA (Digital Operational Resilience Act):** EU financial sector regulation explicitly addresses quantum risk in its ICT risk management requirements
- **FFIEC (U.S.):** Examination guidance increasingly references quantum risk as a category requiring management assessment
- **Basel III/IV operational risk:** Quantum-induced cryptographic failure would qualify as an operational risk event — with potential capital implications
- **SEC Cybersecurity Disclosure Rules:** Public companies must disclose material cybersecurity risks; for organizations with long-lived sensitive data, quantum risk arguably meets the materiality threshold
::::

::::{dropdown} Cyber Insurance — The Underwriter's View
The cyber insurance market is beginning to respond to quantum risk:

- Several major reinsurers have added quantum-specific exclusion language in draft policy forms
- Insurers are adding PQC migration maturity to their underwriting questionnaires
- Early signals from Lloyd's syndicates suggest quantum-related claims may face coverage disputes if insureds had "known and foreseeable" exposure and failed to act

The insurance market has historically moved slowly on emerging risks. But the pattern with cyber insurance generally is that by the time exclusions are formalized and widely enforced, organizations that haven't already migrated face both coverage gaps and sharp premium increases simultaneously.
::::

---

## 5.10 Flagship Case Study: A Global Bank's Four-Year PQC Migration

*The following case study is a composite based on publicly disclosed PQC migration programs at major financial institutions, including JPMorgan Chase, BNY Mellon, and HSBC, combined with patterns observed in financial sector PQC readiness assessments.*

:::{figure} ../images/ch05-bank-migration-case.png
:name: fig-bank-migration-case
:alt: Global bank PQC migration four-year roadmap showing inventory, hybrid TLS pilot, vendor coercion, and full migration phases.
:width: 90%

**A Global Bank's Four-Year PQC Migration Roadmap.** Phase 1 (months 1–6): Cryptographic inventory — the phase nobody wanted to fund, but which revealed hundreds of forgotten long-lived keys in embedded systems. Phase 2 (months 7–18): Hybrid TLS pilot. Phase 3 (months 19–30): Vendor coercion campaign. Phase 4 (months 31–48): Full migration and ongoing monitoring.
:::

### Situation

A Tier-1 global investment bank with operations in 40 countries, \$2.8 trillion in assets under custody, and approximately 12,000 software systems in its production environment commissioned a quantum risk assessment in 2022. The assessment concluded:

- The bank held financial transaction records with regulatory retention requirements of 10–25 years
- Client trade data was subject to strict confidentiality obligations for the lifetime of client relationships
- Estimated migration timeline: 5–7 years given the complexity of legacy systems
- Applying the Mosca Inequality with a conservative Q-Day estimate of 2032: the bank was **already in deficit** for its longest-lived data categories

### Quantum Angle

The board received a briefing that quantified the risk in business terms. Rather than framing the issue as "quantum computing might break our encryption someday," the briefing asked a single question: *"If an adversary had been collecting our TLS traffic for the past three years and decrypts it in 2032, what would they have?"* The answer included: client positions that could enable front-running; counterparty negotiations still ongoing; regulatory correspondence about pending investigations; and proprietary trading algorithms. The board authorized a \$340 million four-year migration program the same quarter.

### Decisions Made

**Phase 1 — The Inventory (Months 1–6):** The bank deployed automated cryptographic discovery tools across its entire environment. The six-month inventory revealed:

- **4,847 certificates** using RSA-2048 or below
- **1,203 cryptographic endpoints** using TLS 1.2 with deprecated cipher suites
- **89 embedded systems** — primarily SWIFT messaging gateways and ATM firmware — using long-lived RSA keys with no documented rotation schedule. Some had not been rotated in 11 years.
- **23 vendor systems** with cryptographic algorithms hardcoded in closed-source software, for which the vendors had no PQC roadmap

The embedded system discovery was the shock. Nobody had known these keys existed. They had been provisioned during original system deployment and never inventoried as cryptographic assets. Applying the Mosca Inequality: keys provisioned in 2013, expected to persist until hardware replacement in 2028, protecting transaction authentication data — they were red. All 89 were flagged for emergency priority.

**Phase 2 — Hybrid TLS Pilot (Months 7–18):** The bank deployed hybrid TLS 1.3 with ML-KEM-768 key exchange for its highest-volume internal service mesh — approximately 3.2 billion TLS connections per day. Performance impact: less than 2% latency increase. The hybrid configuration provided immediate quantum resistance for new connections while maintaining interoperability with systems awaiting migration.

**Phase 3 — Vendor Coercion (Months 19–30):** Of the 23 vendors with no PQC roadmap, 14 published credible timelines within six months of receiving contractual notices that procurement renewals would require PQC certification. Five were replaced entirely. Four received time-limited exceptions with contractual remediation milestones and financial penalties for non-compliance.

**Phase 4 — Board Reporting Cadence:** The bank established quarterly board reporting on PQC migration progress, framed using the Mosca Inequality. Each quarterly report showed the number of cryptographic assets remaining in RED/YELLOW/GREEN classification, the assets migrated in the quarter, and the revised Mosca risk profile assuming current Q-Day estimates. This cadence proved essential: it kept the migration funded across three CEO transitions and one merger negotiation.

### Measured Outcome

By the end of Year 4:
- 96% of cryptographic endpoints migrated to PQC or hybrid configurations
- All 89 embedded system long-lived keys replaced, with automated rotation policies
- All vendor contracts updated to require PQC certification for renewals
- Migration cost: \$340 million over four years — approximately \$0.00001 per dollar of assets under custody
- Regulatory benefit: The bank received favorable examination findings from three regulators citing its PQC program as a model for the sector

### Open Question

The 4% of cryptographic endpoints not yet migrated at Year 4 remained in mainframe COBOL applications — systems whose source code had been partially lost, running on hardware with no vendor PQC support path. The open question for the next phase: do you rewrite the application (12–18 month project, \$80M estimate), replace the hardware (requires 24-month hardware lifecycle), or deploy a quantum-secure proxy layer that encrypts mainframe traffic before it reaches the network (faster, cheaper, but adds an architectural layer with its own maintenance burden)?

This is the question every organization will eventually face. The organizations that start their inventory now will face it in Year 4 or 5. The organizations that start in 2028 will face it in Year 4 or 5 — with Q-Day potentially already here.

---

## 5.11 Industry Snapshots

### Snapshot A: Energy Grid SCADA — The 30-Year Key Problem

A North American electric utility operating 14 power generation facilities conducted a PQC readiness assessment in 2023. Its SCADA (Supervisory Control and Data Acquisition) systems — the software that controls actual physical infrastructure — were found to be using RSA-1024 keys. Some of these keys had been provisioned in the mid-2000s. The systems controlling them had documented operational lifespans extending to 2045.

Applying the Mosca Inequality: key lifetime extending to 2045, migration requiring 3–5 years on SCADA systems (which must maintain 99.999% uptime), Q-Day potentially in the early 2030s. The utility was already late.

The complication: SCADA systems typically cannot be patched like enterprise software. Firmware updates require vendor coordination, regulatory notification under NERC CIP (North American Electric Reliability Corporation Critical Infrastructure Protection) standards, and often physical access to geographically dispersed substations. A PQC migration of SCADA infrastructure is a 5–8 year program by default.

The utility began its migration program immediately upon receiving the assessment. Its CISO's summary to the board: "If we had started in 2020, we would be finishing now. If we start today, we will be finishing in 2028 or 2029. Every year we waited was a year we cannot get back."

### Snapshot B: Government Agency — CNSA 2.0 Mandate Response

A U.S. federal agency in the defense sector received CNSA 2.0 mandate requirements in 2022. Its internal assessment identified 3,200 cryptographic endpoints across classified and unclassified systems. The mandated timeline: core systems to PQC by 2030, all systems by 2035.

The agency's approach became a reference model for the federal sector:

1. **Tiered migration by classification level:** Classified systems first, because the threat to those systems is highest and the regulatory deadline most stringent
2. **Zero-trust as a forcing function:** The agency's concurrent zero-trust architecture initiative created a natural point to inject PQC requirements — every new zero-trust boundary was built with PQC from day one
3. **NSA Commercial Solutions for Classified (CSfC) coordination:** For systems using commercial cryptography in classified environments, the agency worked with NSA to obtain CNSA 2.0-compliant CSfC solutions from approved vendors
4. **"Never deploy new classical" policy:** From January 2023, no new system or service could be deployed using classical-only cryptography. PQC was the default for all new deployments, with exceptions requiring CISO approval

By 2025, 40% of the agency's endpoints were PQC or hybrid. The agency projected 100% completion by 2029 — one year ahead of the CNSA 2.0 mandate.

---

## 5.12 Productive-Struggle Problem

::::{admonition} The Challenge: One Page for the CFO
:class: tip

**Scenario:** Your CFO has just told you: "I've got inflation, three regulatory audits, a \$200 million system modernization program, and a board asking about AI strategy. Quantum cryptography is someone else's problem."

**Your task:** Draft a one-page PQC business case that changes their mind. You have 300 words on the page and 90 seconds to present it.

**Constraints:**
- No technical jargon (no RSA, no lattices, no qubits)
- Lead with financial or regulatory consequence, not technical threat
- Quantify the risk (use the Mosca Inequality framework)
- Include one concrete competitor action or regulatory requirement
- End with a specific ask: budget, headcount, or decision

**Hints to consider:**
- What is the cost of *not* migrating, quantified in terms the CFO already cares about?
- What is the smallest first step that proves the problem is real? (Answer: the inventory)
- What regulatory deadlines already exist that create fiduciary obligation?
- What do cyber insurers and rating agencies think about quantum risk?
::::

::::{dropdown} 💡 Sample Solution Framework (Reveal After Attempting)

**THE QUANTUM RISK BRIEF — ONE PAGE**

**The Risk (in plain language):** The encryption protecting our most sensitive data — client records, financial transactions, IP — is vulnerable to a known attack that will become feasible within 8–12 years. Nation-state adversaries are already collecting our encrypted data today, storing it to decrypt when quantum computers arrive. This is documented in NSA advisories, FBI threat briefings, and is why NIST finalized new encryption standards in 2024.

**The Financial Exposure:** Our data has an average confidentiality requirement of [X] years. Our migration will take [Y] years. By the Mosca Inequality, if Q-Day arrives before [X+Y] years from now, we are exposed — and we will not know it until years after the fact. The reputational, legal, and regulatory consequences of a quantum-enabled breach of [client records / trade data / patient data] are comparable to a conventional major breach — except we cannot detect it, respond to it, or report it on the timeline our regulators require.

**The Regulatory Reality:** CNSA 2.0 mandates PQC adoption in federal supply chain by 2030. EU NIS2 requires "state-of-the-art" cryptography for critical infrastructure operators. Our cyber insurer's renewal questionnaire now includes PQC maturity questions. These are not future risks — they are current compliance obligations.

**What Peers Are Doing:** [JPMorgan / HSBC / Competitor] began PQC migration programs in 2022. The organizations that started in 2022 will finish in 2026. We are starting in [year]. That gap is measurable competitive and regulatory risk.

**The Ask:** \$[X]M to conduct a six-month cryptographic inventory (Phase 1). Cost: \$[X]M. Deliverable: a complete asset map, Mosca risk classification, and board-ready migration roadmap. We cannot manage what we cannot see. This buys us the visibility to manage the risk.

::::

---

## 5.13 Module-Level Outcomes

By the end of this chapter, you should be able to:

::::{card-carousel} 1

:::{card} Outcome 1
**Explain Shor's and Grover's cryptographic consequences without notation.**

You can describe, in plain language, how Shor's algorithm exploits quantum interference to factor large numbers in polynomial time — destroying RSA and ECC security — and how Grover's algorithm halves the effective key length of symmetric encryption. You can explain both to a non-technical board member in two minutes.
:::

:::{card} Outcome 2
**Evaluate NIST PQC standards and enterprise implications.**

You can distinguish ML-KEM, ML-DSA, and SLH-DSA by purpose, mathematical foundation, and deployment context. You can explain why lattice-based cryptography is resistant to quantum attacks, and what the transition to these standards means for certificates, TLS, code signing, and PKI infrastructure.
:::

:::{card} Outcome 3
**Design a crypto-agility migration plan.**

You can outline the four phases of a crypto-agility program (inventory, classification, hybrid deployment, migration execution), identify the organizational and technical barriers at each phase, and specify what a prioritized migration backlog should contain.
:::

:::{card} Outcome 4
**Apply the Mosca Inequality to a specific organizational data asset.**

Given a data asset with a defined confidentiality lifetime and an estimated migration timeline, you can determine whether the organization is in deficit or surplus relative to Q-Day estimates, and articulate the implications for migration urgency.
:::

:::{card} Outcome 5
**Assess regulatory, insurance, and fiduciary exposure for delay.**

You can identify the key regulatory frameworks (CNSA 2.0, EU NIS2, DORA, financial sector guidance) that create PQC obligations, describe the emerging cyber insurance implications, and frame quantum risk delay as a fiduciary accountability issue for boards and executives.
:::

::::

---

## 5.14 Lab 5 (Regular): Breaking Something Small

**Duration:** ~45 minutes  
**Tools:** [IBM Quantum Composer](https://quantum.ibm.com/composer) or [Quirk Quantum Circuit Simulator](https://algassert.com/quirk)  
**No coding required**

### Background

You cannot run Shor's algorithm at real RSA scale on current quantum hardware — we don't yet have a fault-tolerant machine with enough logical qubits. But you *can* run the core mathematical operation — **quantum period finding** — at a tiny scale. The smallest meaningful example uses the number **15** (= 3 × 5).

Period finding works like this: Shor's algorithm transforms the factoring problem into finding the period of a mathematical function. Quantum interference amplifies the quantum states that correspond to the correct period and cancels the wrong ones. When you measure the quantum circuit, the correct period appears with high probability — from which the prime factors can be derived classically.

### Instructions

::::{tab-set}
````{tab-item} Step 1: Set Up the Circuit
Navigate to IBM Quantum Composer or Quirk. You will build a 7-qubit circuit:

- **4 input qubits** (the quantum register that holds the period-finding state)
- **3 work qubits** (the function evaluation register, sized for f(x) = 2^x mod 15)

Initialize all qubits to |0⟩. Apply Hadamard gates to the 4 input qubits to create equal superposition of all 16 states (|0⟩ through |15⟩).
````
````{tab-item} Step 2: Apply the Modular Exponentiation
Apply controlled operations implementing f(x) = 2^x mod 15 to the work register. In IBM Composer, you can use a pre-built template for this. In Quirk, search for the "Modular Exponentiation" circuit block for N=15, a=2.

Observe: the work register now contains the *values* of 2^x mod 15 for all superposed values of x simultaneously.
````
````{tab-item} Step 3: Apply the Quantum Fourier Transform
Apply the Quantum Fourier Transform (QFT) to the input register. This is the step where quantum interference does its work — the QFT amplifies the quantum amplitudes corresponding to the period r (the number after which the function repeats) and suppresses all others.

In IBM Composer, the QFT is available as a circuit block. In Quirk, build it from H gates, controlled-phase rotations, and SWAP gates.
````
````{tab-item} Step 4: Measure and Interpret
Measure the input register. Run the simulation 1,000 times. Observe the probability histogram: you should see probability concentrated at multiples of 1024/r, where r is the period.

For f(x) = 2^x mod 15, the period is r=4. The histogram should show spikes at 0, 256, 512, and 768 (= 0/4, 1/4, 2/4, 3/4 of 1024).

From r=4, compute the factors: gcd(2^(r/2) - 1, 15) = gcd(3, 15) = 3; gcd(2^(r/2) + 1, 15) = gcd(5, 15) = 5. You have factored 15 = 3 × 5 using quantum period finding.
````
````{tab-item} Step 5: Scale Reflection
Now consider: RSA-2048 uses numbers with 617 decimal digits. The circuit you just built used 7 qubits for the number 15. The number of physical qubits required to run Shor's on RSA-2048 is estimated at 4,000–10,000 *logical* qubits, each requiring 1,000+ *physical* qubits for error correction — totaling 4–10 million physical qubits. Today's best machines have ~1,000 noisy physical qubits. The mathematics works. The engineering gap is vast — but it is narrowing.
````
`````

### Deliverable

Write a **400-word explanation** for a non-technical board member that:
1. Describes what you observed in the simulation (in plain English, no equations)
2. Explains the connection between quantum interference and why the correct period appeared
3. Explains why the same mechanism scales to break real RSA encryption
4. Concludes with a specific recommendation the board should act on

---

## 5.15 Lab 5 (Optional Advanced): The PQC Migration Scanner

**Duration:** ~90 minutes  
**Tools:** Python 3.9+, `cryptography` library, any directory with SSL/TLS certificates or PEM keys

<a href="https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch05-pqc-migration-scanner.ipynb" target="_blank">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="margin-bottom: 1rem;"/>
</a>

### Background

The most expensive phase of any PQC migration program is the inventory — because most organizations do not know where all their cryptographic assets are. This lab builds a **PQC Migration Scanner**: a Python tool that walks a directory tree, finds every certificate and key, extracts the cryptographic metadata, applies the Mosca Inequality, and outputs a prioritized CSV migration report with GREEN/YELLOW/RED classification.

### What the Scanner Does

```{mermaid}
flowchart LR
    A[Directory Tree] --> B[Certificate/Key Discovery]
    B --> C[Metadata Extraction]
    C --> D[Algorithm Classification]
    D --> E[Mosca Inequality Engine]
    E --> F[GREEN / YELLOW / RED]
    F --> G[Prioritized CSV Report]
    
    style A fill:#e3f2fd
    style F fill:#fff3e0
    style G fill:#e8f5e9
```

### Core Logic

```python
def mosca_classification(cert_lifetime_years, migration_years_remaining, 
                          qday_estimate_years):
    """
    Apply Mosca Inequality to classify a cryptographic asset.
    
    GREEN: cert_lifetime + migration_remaining < qday_estimate
    YELLOW: cert_lifetime + migration_remaining is within 2 years of qday
    RED: cert_lifetime + migration_remaining >= qday_estimate
    """
    total_exposure = cert_lifetime_years + migration_years_remaining
    buffer = qday_estimate_years - total_exposure
    
    if buffer > 2:
        return "GREEN", buffer
    elif buffer > 0:
        return "YELLOW", buffer
    else:
        return "RED", buffer
```

The full scanner implementation is in the Colab notebook. It handles X.509 certificates, PEM-encoded private keys, PKCS#12 bundles, and SSH public keys — extracting algorithm, key size, validity period, and subject information for each.

### Sample Output

| File | Algorithm | Key Size | Expires | Lifetime (yrs) | Mosca Status | Priority |
|------|-----------|----------|---------|----------------|--------------|----------|
| /etc/ssl/server.crt | RSA | 2048 | 2026-03 | 1.2 | YELLOW | HIGH |
| /etc/ssl/legacy.crt | RSA | 1024 | 2028-06 | 3.5 | RED | CRITICAL |
| /etc/ssl/client.crt | ECDSA | 256 | 2025-11 | 0.8 | GREEN | LOW |
| /var/keys/signing.key | RSA | 4096 | N/A | 15.0 | RED | CRITICAL |

### Deliverable

1. **Working script:** The completed scanner from the Colab notebook, tested against a sample certificate directory
2. **Sample output:** The CSV report from your scan, with at least 5 entries classified across GREEN/YELLOW/RED
3. **500-word executive summary** interpreting the output as if presenting to a CISO: What did you find? What is the priority order for migration? What is the headline Mosca risk exposure?

---

## 5.16 Discussion Guidelines

**Post a substantive response (minimum 300 words) citing at least two sources from this week's readings or external research. Reply meaningfully to TWO peers' posts.**

### Discussion Prompt

Your organization is a mid-size regional bank (\$15 billion in assets, 1,200 employees, operations in three states) with no formal PQC program. The board has asked you to brief them on quantum cryptographic risk in their next quarterly meeting — in 15 minutes.

Prepare your board briefing outline. Your response should address:

1. **The business risk** — not the technical risk. How do you quantify the exposure in terms the board already understands (regulatory liability, insurance, competitive position, reputational risk)?

2. **The Mosca Inequality applied** — given that bank customer data has confidentiality requirements of 7–10 years and PQC migration for a \$15B bank would take approximately 4–6 years, where does this bank sit on the Mosca risk spectrum?

3. **The immediate recommendation** — what is the one thing you ask the board to authorize today? (Hint: it is almost certainly the inventory, not the full migration program.)

4. **The narrative hook** — boards respond to stories, not frameworks. What is the one concrete scenario you use to make the risk viscerally real? How do you avoid being dismissed as a technology alarmist?

**Peer response guidelines:** When responding to peers, challenge one assumption in their briefing, propose an alternative framing of the risk, or extend their analysis with a regulatory angle they may not have considered. Responses of "I agree" or "great post" do not count as substantive replies.

---

## Glossary

```{glossary}
Post-Quantum Cryptography (PQC)
  Cryptographic algorithms designed to be secure against both classical and quantum computer attacks. NIST finalized the first three PQC standards in 2024: ML-KEM, ML-DSA, and SLH-DSA.

Shor's Algorithm
  A quantum algorithm published by Peter Shor in 1994 that factors large integers in polynomial time, breaking RSA and ECC encryption. Requires a fault-tolerant quantum computer to run at meaningful scale.

Grover's Algorithm
  A quantum algorithm that provides a quadratic speedup for searching unstructured data. Halves the effective security of symmetric encryption algorithms (AES-128 effectively becomes AES-64).

RSA (Rivest–Shamir–Adleman)
  A widely used public-key cryptographic algorithm whose security depends on the computational difficulty of factoring large numbers. Vulnerable to Shor's algorithm running on a fault-tolerant quantum computer.

ECC (Elliptic Curve Cryptography)
  A family of public-key cryptographic algorithms based on the algebraic structure of elliptic curves. Also vulnerable to Shor's algorithm via quantum algorithms for the discrete logarithm problem.

Q-Day
  The anticipated date when a fault-tolerant quantum computer capable of running Shor's algorithm at RSA scale becomes operational. Most analyst estimates cluster in the 2030–2035 window.

Harvest Now, Decrypt Later (HNDL)
  An attack strategy in which adversaries collect and store encrypted data today with the intention of decrypting it when sufficient quantum computing capability becomes available.

Mosca Inequality
  The inequality, formulated by Michele Mosca, stating that an organization is at quantum cryptographic risk if the lifetime of its sensitive data plus its migration time exceeds the time until Q-Day.

ML-KEM (Module Lattice Key Encapsulation Mechanism)
  The primary NIST PQC standard for key exchange, based on the hardness of lattice problems. Formerly known as CRYSTALS-Kyber. Replaces RSA and ECC in TLS key exchange.

ML-DSA (Module Lattice Digital Signature Algorithm)
  The primary NIST PQC standard for digital signatures, based on lattice mathematics. Formerly known as CRYSTALS-Dilithium. Replaces ECDSA in code signing and PKI.

SLH-DSA (Stateless Hash-Based Digital Signature)
  A NIST PQC standard for digital signatures based on hash functions rather than lattice problems. Formerly known as SPHINCS+. Provides algorithmic diversity as a hedge against future attacks on lattice mathematics.

Lattice Cryptography
  A family of cryptographic schemes based on mathematical problems defined over multi-dimensional lattice structures. The computational hardness of problems like Shortest Vector Problem (SVP) and Learning With Errors (LWE) provides quantum resistance.

Learning With Errors (LWE)
  A mathematical problem underlying ML-KEM and ML-DSA. It involves solving noisy linear equations over a lattice — computationally hard for both classical and quantum computers.

Crypto-Agility
  The engineering design principle of building cryptographic systems with abstraction layers that allow algorithms to be swapped without requiring full system redesign or code rewrites.

Hybrid Cryptography
  A deployment strategy that runs both classical and post-quantum cryptographic algorithms simultaneously for the same operation. Provides quantum resistance immediately while maintaining backward compatibility.

CNSA 2.0 (Commercial National Security Algorithm Suite 2.0)
  NSA's mandate requiring U.S. national security systems to migrate to post-quantum cryptography, with deadlines ranging from 2025 (new systems) to 2035 (all systems).

NIS2 Directive
  The EU's Network and Information Security Directive 2, effective 2024, requiring critical infrastructure operators and digital service providers to maintain "state-of-the-art" cybersecurity — increasingly interpreted to include PQC migration planning.

Quantum Fourier Transform (QFT)
  The quantum analog of the classical Discrete Fourier Transform. The core mathematical operation in Shor's algorithm that uses quantum interference to find the period of a modular function.

PKI (Public Key Infrastructure)
  The framework of certificates, certificate authorities, and trust chains that enables public-key cryptography at internet scale. PKI must be completely re-engineered to support PQC algorithms.

TLS (Transport Layer Security)
  The cryptographic protocol securing internet communications (HTTPS, VPNs, email). The most pervasive deployment of RSA and ECC, and thus the primary target of PQC migration.
```

---

## 5.17 Leader's Takeaway

::::{admonition} The Leader's Takeaway
:class: important

The first trillion dollars of quantum value will come not from a new drug or a new battery but from the silent, unglamorous work of replacing the locks on every door before someone else gets a key.

This chapter has given you the frameworks. The Mosca Inequality tells you whether you are already late. The NIST PQC standards tell you what to replace your current locks with. Crypto-agility tells you how to build infrastructure that can keep pace with a cryptographic landscape that will change multiple times in your career. The case study tells you what the migration actually looks like — the surprise embedded keys, the vendor coercion, the board reporting, the COBOL systems nobody wanted to touch.

What no framework can give you is the decision to start. That is a leadership choice. The organizations that made it in 2020 and 2021 — the forward-looking banks, the defense contractors who read the NSA advisories carefully, the technology companies who noticed what Google and Cloudflare were deploying in their experimental TLS stacks — they are finishing their migrations now. The window is not closed. But it is closing.

The adversaries collecting your encrypted traffic today are not sophisticated hackers in hoodies. They are patient, well-funded, and operating with a ten-year time horizon. They are counting on you to delay. They are counting on quantum computing to seem abstract and distant until it isn't. They are counting on the CFO to have bigger problems.

Do not give them the gift of your inaction.

Start the inventory. Understand where your cryptographic risk lives. Apply the Mosca Inequality to your most sensitive data categories. Put a number on the exposure. Bring it to the board.

The first trillion dollars of quantum value is waiting for the leaders who act before the deadline, not the ones who react after it.
::::

---

## Cross-References

- **See {ref}`ch-04-hardware-race`** for context on current fault-tolerant quantum computer timelines and why the Q-Day window estimate matters.
- **See {ref}`ch-09-quantum-ready-enterprise`** for the full enterprise quantum readiness framework, of which PQC migration is one pillar.
