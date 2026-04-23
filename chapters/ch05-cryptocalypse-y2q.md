---
title: "Chapter 5: The Cryptocalypse — Y2Q and the Security Imperative"
subtitle: "The Attack Is Already Happening. The Question Is Whether You Finish Before They Decrypt."
short_title: "Ch. 5: The Cryptocalypse"
description: "The cryptographic layer protecting every contract, payment, and medical record is on a migration clock that most organizations have not yet started. This chapter explains Shor's algorithm, NIST PQC standards, the Mosca Inequality, and STRIDE threat modeling applied to the quantum era — giving leaders the governance tools and technical vocabulary to lead a post-quantum cryptography migration before Q-Day arrives."
label: ch-05-cryptocalypse-y2q
tags: [post-quantum cryptography, Shor's algorithm, NIST PQC, crypto-agility, Mosca Inequality, Y2Q, cybersecurity, RSA, STRIDE, threat modeling, FAU, annealing, gate-model, quantum security]
---

# Chapter 5: The Cryptocalypse — Y2Q and the Security Imperative

:::{figure} ../images/ch05-explainer-infographic.png
:label: fig-ch05-explainer-infographic
:alt: Chapter 5 explainer infographic showing the road from today's RSA encryption to Q-Day, with the Mosca Inequality, NIST PQC standards, STRIDE threat model, and crypto-agility framework.
:width: 100%
:align: center

**The Cryptocalypse at a Glance.** Today's RSA encryption is protected by a math problem that classical computers cannot solve in any reasonable timeframe. Shor's algorithm — running on a sufficiently powerful *gate-based* quantum computer — dissolves that protection in minutes. The organizations that will survive Q-Day are the ones migrating now, while the clock is still ticking in their favor.
:::

This chapter covers the one quantum computing topic where the timeline is not speculative — where the strategic obligation is not "watch and wait" but "begin immediately." Every other application in this course rewards patience. This one penalizes it.

The internet you used this morning to check your bank balance, send a contract, or access a patient record was secured by mathematics invented in the 1970s. That mathematics works beautifully — until it doesn't. A specific class of quantum computer doesn't bend those locks. It evaporates them. This chapter is the story of what that means for every organization on earth, why the threat is not hypothetical, and what leaders must do right now.

---

## Opening Scene: The Theft That Already Happened

Somewhere right now, a nation-state actor is harvesting encrypted traffic it cannot yet read. It isn't wasting disk space. It is waiting.

The operation is methodical and patient. Automated systems tap fiber backbones, mirror TLS handshakes, copy encrypted API calls between hospital systems, intercept the SSL-wrapped PDFs of merger agreements, and quietly vacuum up the encrypted transactions flowing between financial clearing houses. The data is stored in cold storage at pennies per gigabyte. None of it is readable today. None of it needs to be.

This is **Harvest Now, Decrypt Later** — and it is almost certainly happening to your company.

The attackers are not guessing. They know that quantum computers capable of running Shor's algorithm at scale are coming. The intelligence community's best estimates cluster around a window beginning in the early 2030s. The attackers also know something else: your organization's migration to post-quantum cryptography will take years. Every year you delay is one more year of sensitive data they can add to the archive.

The question is not whether your data is being harvested. The question is whether you will finish your migration before they get the key.

---

## The Single Idea

```{epigraph}
The cryptographic layer beneath nearly every modern contract, payment, medical record, and supply chain is on a multi-year migration clock. Organizations that finish late will not know they were early targets until five years after the fact. The first obligation of any leader who understands quantum computing is to start that migration — today.
```

---

## 5.1 Which Quantum Computer Is the Threat? (The Paradigm Distinction That Changes Everything)

Before examining *how* quantum computing threatens cryptography, it is essential to establish *which* quantum computer poses that threat — because this course gives you hands-on access to FAU's D-Wave Advantage2, and the answer matters enormously for how you frame your security strategy.

::::{admonition} The Paradigm Clarification Every Leader Needs
:class: important

There are two fundamentally different types of quantum computers covered in this course:

**Gate-model quantum computers** (IBM, Google, IonQ, Quantinuum) build computation from sequences of quantum logic gates, analogous to classical logic circuits. They are general-purpose but fragile — noise limits what they can do at scale today. Shor's algorithm, which breaks RSA encryption, runs on gate-model hardware.

**Quantum annealers** (FAU's D-Wave Advantage2) encode optimization problems as energy landscapes and use quantum tunneling to find low-energy solutions. They are purpose-built for combinatorial optimization — scheduling, routing, portfolio optimization, logistics. They are *not* general-purpose quantum computers.

**The security implication:** FAU's D-Wave Advantage2 — the machine you will use in Lab 6 — **cannot run Shor's algorithm**. Annealing quantum computers are not the cryptographic threat. The threat comes from a future fault-tolerant *gate-model* quantum computer with thousands of error-corrected logical qubits. That machine does not yet exist.

This distinction matters for your board conversations. When a security vendor says "quantum computers threaten your encryption," the precise answer is: "A specific class of gate-model quantum computer will, when fault-tolerant hardware at sufficient scale exists. Today's quantum annealers, including the largest systems currently deployed, do not pose that threat."

What does pose a threat *today* is Harvest Now, Decrypt Later — adversaries storing your encrypted traffic for future decryption. That is a present operational risk, regardless of which quantum paradigm arrives first.
::::

---

## 5.2 How Encryption Works Today — and Why It Is Brilliant

### The Padlock Model

RSA encryption's security rests on a simple asymmetry. Multiplying two large prime numbers together is trivially easy. A computer does it in microseconds. But starting from the *product* and working backwards to find those two original primes — that is called **prime factorization**, and for numbers with 2,048 binary digits (RSA-2048), it is computationally intractable for any classical machine. The best classical algorithms would require operations exceeding the number of atoms in the observable universe. In practice: unbreakable.

So the padlock is a number — a very large product of two primes. Your **public key** is that product, shared with the world. Your **private key** is one of the two primes, kept secret. Anyone can encrypt data to you using the product. Only you can decrypt it, because only you know the prime.

:::{figure} ../images/ch05-rsa-encryption-analogy.png
:label: fig-rsa-encryption-analogy
:alt: RSA encryption illustrated as a padlock secured by two prime numbers, with classical computers unable to factor large products.
:width: 90%
:align: center

**RSA Encryption: The Padlock Whose Strength Is a Math Problem.** The product of two large primes is easy to compute but nearly impossible to reverse. Classical computers would take longer than the age of the universe to crack RSA-2048 by brute force.
:::

Where the analogy breaks down: real padlocks can be physically cut. RSA cannot be "cut" — it can only be mathematically solved. This matters because it means a future mathematical breakthrough, not a physical tool, is the threat.

::::{admonition} 🔥 The Weight of This
:class: warning

Right now, every HTTPS connection you make, every banking transaction, every encrypted email, every signed software update is protected by this padlock model. RSA and its cousin ECC (Elliptic Curve Cryptography) underpin essentially all of the internet's trust infrastructure. When that foundation cracks — not if, when — the consequences will not be a data breach at one company. They will be systemic. The entire trust layer of the digital economy dissolves simultaneously, unless we replace it first.
::::

---

## 5.3 Shor's Algorithm: The Master Key

### The Quantum Shortcut

Shor's algorithm, published by Peter Shor in 1994, transforms prime factorization from an exponentially hard problem to a polynomial-time one on a quantum computer. It uses quantum superposition to explore an astronomically large solution space in parallel, then exploits **quantum interference** to amplify the correct answer and cancel out the wrong ones. The result: a fault-tolerant gate-model quantum computer running Shor's on RSA-2048 would take on the order of hours — not the age of the universe.

:::{figure} ../images/ch05-shors-algorithm-effect.png
:label: fig-shors-algorithm-effect
:alt: Shor's algorithm effect showing quantum computer using quantum interference to break RSA encryption that would take classical computers billions of years.
:width: 90%
:align: center

**Shor's Algorithm: From Intractable to Polynomial.** Classical computers must try factor combinations sequentially. Shor's algorithm uses quantum interference to find prime factors exponentially faster — reducing RSA-2048's "age of the universe" protection to hours on a fault-tolerant gate-model machine.
:::

Where the analogy breaks down: Shor's requires a fault-tolerant quantum computer with thousands of logical qubits — something we do not yet have. Current gate-model quantum computers have too much noise to run Shor's at meaningful scale. The engineering barrier is narrowing, year by year, with billions of dollars of investment. But the barrier is real, and today's devices — including the largest cloud-accessible systems — cannot break production RSA.

::::{admonition} 🔥 The Weight of This
:class: danger

Every RSA-protected system on earth — banking infrastructure, healthcare records, military communications, supply chain software, the certificate authorities that tell your browser which websites to trust — becomes breakable the day a fault-tolerant gate-model quantum computer runs Shor's at scale. This is not theoretical risk management. This is a known vulnerability with a known countdown clock. The only uncertainty is the exact date of detonation.
::::

::::{admonition} Grover's Algorithm: The Symmetric Threat
:class: note

Shor's algorithm breaks *asymmetric* cryptography (RSA, ECC) completely. **Grover's algorithm** — a different quantum algorithm — poses a more moderate but real threat to *symmetric* cryptography (AES, SHA). Grover's provides a quadratic speedup for searching unstructured data. In practical terms: AES-128 effectively becomes AES-64 against a quantum attacker using Grover's — a key length that current classical computers can brute-force. The fix is straightforward: double your key length. AES-256 becomes the new AES-128. But this requires finding every AES-128 deployment in your organization and upgrading it — which, in large enterprises, is non-trivial.

| Algorithm | Threat Type | Effect on Current Crypto | Mitigation |
|-----------|-------------|--------------------------|------------|
| Shor's | Asymmetric (RSA, ECC) | Completely broken | Migrate to PQC |
| Grover's | Symmetric (AES, SHA) | Security halved | Double key length |

::::

---

## 5.4 Harvest Now, Decrypt Later: The Theft Already in Progress

### The Patient Burglar

**Harvest Now, Decrypt Later** (HNDL) is the attack strategy where adversaries collect and store encrypted data today with the intention of decrypting it once a fault-tolerant gate-model quantum computer becomes available.

:::{figure} ../images/ch05-harvest-now-decrypt-later.png
:label: fig-harvest-now-decrypt-later
:alt: Harvest Now Decrypt Later attack diagram showing nation-state actors storing encrypted traffic today to decrypt with quantum computers tomorrow.
:width: 90%
:align: center

**Harvest Now, Decrypt Later: The Theft in Progress.** Adversaries are collecting encrypted traffic today — TLS sessions, VPN tunnels, encrypted file transfers — and storing it for future quantum decryption. The encryption protecting that data is today's RSA and ECC, which Shor's algorithm will dissolve when run on a fault-tolerant gate-model quantum computer.
:::

Where the analogy breaks down: a burglar takes physical objects, which are then missing. Harvest Now, Decrypt Later is entirely invisible — you have no idea your data has been copied. The logs show nothing unusual. Your security team has nothing to alert on.

::::{admonition} 🔥 The Weight of This
:class: danger

Your most sensitive data from the past five years may already be in adversarial hands — sitting in cold storage, waiting. Mergers-and-acquisitions strategy. Patient genomic data. Defense procurement specifications. Long-term supply contracts. Every byte of encrypted traffic you have sent over the past five years is a candidate. The attack is not coming. It has already happened. Only the decryption is in the future.
::::

---

## 5.5 NIST PQC Standards: The New Locks

In 2024, after eight years of rigorous global cryptanalysis competition, NIST finalized the first three post-quantum cryptography (PQC) standards — algorithms secure against both classical and quantum computers.

### The Three Standards

`````{tab-set}
````{tab-item} ML-KEM (Key Encapsulation)
**ML-KEM** (Module Lattice Key Encapsulation Mechanism) — formerly CRYSTALS-Kyber — is the primary algorithm for **key exchange**. It replaces the RSA and ECC key exchange mechanisms used to establish secure TLS connections.

Based on the **Learning With Errors (LWE)** problem in high-dimensional lattice mathematics. No known quantum algorithm provides a meaningful speedup for this problem — not Shor's, not Grover's, not any algorithm currently known.

Already deployed in Google Chrome, Cloudflare, and AWS experimental TLS configurations.
````
````{tab-item} ML-DSA (Digital Signatures)
**ML-DSA** (Module Lattice Digital Signature Algorithm) — formerly CRYSTALS-Dilithium — handles **digital signatures**. It replaces ECDSA and RSA signatures used to authenticate software, documents, certificates, and messages.

Every code-signing pipeline, every PKI infrastructure, every certificate issuance system needs to be updated to support ML-DSA. This is not a configuration change — it is an infrastructure migration.
````
````{tab-item} SLH-DSA (Hash-Based Signatures)
**SLH-DSA** (Stateless Hash-Based Digital Signature) — formerly SPHINCS+ — provides a **hash-based alternative** for digital signatures. It relies only on hash functions rather than lattice problems, providing algorithmic diversity.

Best suited for root certificate signing, long-term archives, and critical infrastructure attestation where maximum assurance is required. Signature sizes are larger than ML-DSA, making it impractical for high-frequency applications.
````
`````

:::{figure} ../images/ch05-nist-pqc-standards.png
:label: fig-nist-pqc-standards
:alt: NIST PQC standards infographic showing ML-KEM, ML-DSA, and SLH-DSA with their mathematical foundations and use cases.
:width: 90%
:align: center

**NIST's 2024 PQC Standards.** After an 8-year global competition, NIST standardized three post-quantum algorithms. ML-KEM and ML-DSA are lattice-based (Learning With Errors problem). SLH-DSA provides hash-based diversity. All three are resistant to Shor's algorithm.
:::

::::{admonition} The 9th-Grader Explanation: Why Lattice Math Is Quantum-Resistant
:class: tip

**What you already know:** Finding something in a haystack is hard. Finding something in a multi-dimensional haystack — imagine a haystack with thousands of dimensions, where "distance" works differently than in physical space — is nearly impossible.

**The bridge:** Lattice cryptography is built on mathematical problems that live in these high-dimensional spaces. The hardest of these problems — finding the shortest vector in a lattice with thousands of dimensions — has been studied for decades, and no known algorithm (classical *or* quantum) solves it efficiently.

**Why Shor's doesn't apply:** Shor's algorithm works by exploiting the *periodic structure* of the prime factorization problem. Lattice problems have no such periodic structure to exploit. The quantum speedup that makes RSA breakable simply does not apply to lattice mathematics.

**Where the analogy breaks down:** Physical jungle gyms have three dimensions. Lattice problems operate in thousands of dimensions where our physical intuition completely fails. The mathematical hardness is qualitatively different from anything in everyday experience.
::::

---

## 5.6 The Mosca Inequality: Are You Already Late?

The **Mosca Inequality** — formulated by quantum cryptographer Michele Mosca — applies visa-application logic to cryptographic migration:

::::{prf:definition} The Mosca Inequality
:label: def-mosca-inequality

Let:
- **X** = time until a quantum computer capable of breaking current public-key cryptography exists (time to Q-Day)
- **Y** = time your organization needs to complete a full migration to post-quantum cryptography
- **Z** = time the data you are protecting today must remain confidential

**If Y + Z > X, you are already late.**
::::

:::{figure} ../images/ch05-mosca-inequality.png
:label: fig-mosca-inequality
:alt: Mosca Inequality diagram with three timeline bars showing data lifetime, migration time, and time to Q-Day, with red danger zone highlighted.
:width: 90%
:align: center

**The Mosca Inequality in Practice.** If your data must stay secret for 10 years and your migration will take 7 years, you need Q-Day to be at least 17 years away — and it almost certainly isn't.
:::

::::{admonition} Apply It Right Now
:class: tip

For each major category of sensitive data your organization holds, ask three questions:

1. **How long must this data remain confidential?** (Medical records: 50+ years. Mergers strategy: 2–5 years. Customer PII: 7–10 years. Defense specifications: 25+ years.)
2. **How long will your complete PQC migration take?** (Average large enterprise: 5–7 years. Complex financial institution: 7–10 years.)
3. **When do analysts estimate Q-Day?** (Conservative: 2035. Aggressive: 2030.)

Add 1 + 2. If the sum exceeds question 3, you are operating in deficit by the Mosca Inequality.
::::

::::{admonition} 🔥 The Weight of This
:class: danger

Most large organizations have migration timelines of 5–10 years. If Q-Day arrives in 8 years and your migration takes 7, you needed to start last year. Leadership that understands the Mosca Inequality and fails to act is making a documented, affirmative choice to leave sensitive data exposed.
::::

---

## 5.7 Crypto-Agility: Building the Migration Infrastructure

**Crypto-agility** is the engineering discipline of building cryptographic infrastructure with standard, swappable abstraction layers — so you can replace one algorithm with another without rebuilding the entire system.

:::{figure} ../images/ch05-crypto-agility-framework.png
:label: fig-crypto-agility-framework
:alt: Crypto-agility framework showing four pillars — Algorithm Discovery, Inventory and Classification, Hybrid Deployment, and Migration Execution.
:width: 90%
:align: center

**The Crypto-Agility Framework.** Organizations that built algorithm abstraction layers into their systems can migrate to PQC in 18 months. Organizations that hard-coded cryptographic dependencies will take 7+ years.
:::

### The Four Pillars of Crypto-Agility

::::{grid} 2

:::{card} 🔍 Pillar 1: Algorithm Discovery
Build an automated inventory of every cryptographic primitive in use across your organization. Every certificate. Every TLS configuration. Every code-signing key. Every VPN tunnel. Every HSM. Every embedded system firmware.
:::

:::{card} 📋 Pillar 2: Classification & Prioritization
Classify each asset by algorithm type, data sensitivity, data lifetime, and system replaceability. Apply the Mosca Inequality to each category. Generate a prioritized migration backlog.
:::

:::{card} 🔀 Pillar 3: Hybrid Deployment
Deploy **hybrid TLS** configurations that run both classical (RSA/ECC) and post-quantum (ML-KEM) key exchange simultaneously. Provides immediate quantum resistance for new traffic while maintaining backward compatibility.
:::

:::{card} ✅ Pillar 4: Migration Execution
Systematically replace classical algorithms with PQC equivalents, starting with highest-risk assets. Build PQC requirements into all new procurement contracts.
:::

::::

---

## 5.8 Regulatory and Fiduciary Exposure: The Compliance Clock

:::{figure} ../images/ch05-regulatory-timeline.png
:label: fig-regulatory-timeline
:alt: Regulatory compliance timeline showing CNSA 2.0, EU NIS2, financial sector, and cyber insurance PQC deadlines from 2024 to 2035.
:width: 90%
:align: center

**The Regulatory Compliance Countdown.** CNSA 2.0 mandates PQC transition timelines for U.S. national security systems. EU NIS2 creates PQC obligations for critical infrastructure operators. Cyber insurers are adding PQC maturity to underwriting questionnaires.
:::

::::{dropdown} CNSA 2.0 — U.S. National Security Systems
**Commercial National Security Algorithm Suite 2.0** (NSA, 2022) mandates the transition of all U.S. national security systems to post-quantum cryptography:
- **2025:** New systems must support CNSA 2.0 algorithms (ML-KEM, ML-DSA)
- **2030:** Legacy national security systems must complete migration
- **2035:** All NSS must exclusively use CNSA 2.0 algorithms

Any organization in the federal supply chain is implicitly on this timeline.
::::

::::{dropdown} EU NIS2 — Critical Infrastructure
EU NIS2, effective October 2024, covers energy, transport, health, water, digital infrastructure, financial markets, and public administration. Organizations failing NIS2 compliance face fines up to €10 million or 2% of global annual turnover. ENISA increasingly interprets "state-of-the-art" cybersecurity to require a credible PQC migration plan.
::::

::::{dropdown} Financial Sector and Cyber Insurance
- **DORA:** EU financial sector regulation explicitly addresses quantum risk in ICT risk management requirements
- **SEC Cybersecurity Disclosure Rules:** Material quantum risk arguably meets the disclosure threshold for organizations with long-lived sensitive data
- **Cyber insurers:** Adding PQC migration maturity to underwriting questionnaires; draft policy forms include quantum-specific exclusion language
::::

---

## 5.9 STRIDE Threat Modeling in the Quantum Era

STRIDE is one of the most widely used structured threat modeling frameworks in enterprise security. Developed at Microsoft, it categorizes security threats into six classes: **Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, and Elevation of Privilege**. It is the framework Mehran Basiratmand identified as the governance bridge between quantum-era technical risks and board-level security obligations.

In this course, STRIDE serves a specific function: it gives business leaders a structured vocabulary for translating quantum computing's cryptographic threats into the organizational risk management language that CISOs, compliance officers, boards, and regulators already speak.

:::{figure} ../images/ch05-stride-quantum-threat-model.png
:label: fig-stride-quantum-threat-model
:alt: STRIDE threat model applied to quantum era showing six threat categories mapped to quantum attack vectors and PQC mitigations.
:width: 100%
:align: center

**STRIDE Applied to the Quantum Era.** Each of the six STRIDE threat categories has a distinct quantum-era manifestation. The PQC standards finalized by NIST in 2024 address five of the six directly — the exception (DoS) requires complementary controls. Understanding this mapping is the foundation of a quantum-era security governance conversation.
:::

### Applying STRIDE: Category by Category

`````{tab-set}
````{tab-item} S — Spoofing
**Classical definition:** An attacker impersonates a legitimate entity — forging a user identity, device credential, or system certificate.

**Quantum-era manifestation:** Digital signatures are the technical foundation of identity verification on the internet. RSA and ECDSA signatures — which underpin TLS certificates, code signing, email authentication (DKIM), and software supply chain integrity — are vulnerable to Shor's algorithm. A fault-tolerant gate-model quantum computer that can factor RSA keys can forge any RSA or ECDSA signature. At scale, this means an adversary could impersonate any website, any software publisher, any email sender, or any enterprise identity provider whose certificates rely on RSA or ECC.

**Specific vectors:**
- Forging TLS certificates → impersonating bank websites, enterprise VPNs, cloud APIs
- Forging code-signing certificates → distributing malware that appears to come from trusted software publishers
- Forging DKIM signatures → sending email that bypasses spam filters while appearing to originate from legitimate domains
- Forging PKI credentials → bypassing enterprise identity and access management

**PQC mitigation:** ML-DSA (CRYSTALS-Dilithium) replaces ECDSA for digital signatures. ML-DSA provides quantum-resistant signature generation and verification. Every certificate authority, PKI system, code-signing pipeline, and identity provider must be migrated to ML-DSA.

**Governance implication:** The "Spoofing" category of STRIDE reveals that quantum-era identity risk is not limited to your organization's own encrypted data. It extends to your ability to trust *any* external party's digital identity. A quantum adversary that can forge certificates can place itself invisibly inside any authenticated communication channel.
````
````{tab-item} T — Tampering
**Classical definition:** An attacker modifies data in transit or at rest — altering a message, corrupting a database, or injecting malicious content into a data stream.

**Quantum-era manifestation:** Data integrity protection on the internet relies on two mechanisms: digital signatures (addressed above under Spoofing) and cryptographic hashing (SHA-256, SHA-3). Grover's algorithm provides a quadratic speedup for searching unstructured data, which has specific implications for hash functions.

**SHA-256 under Grover's:** The security of SHA-256 against birthday attacks is approximately 128 bits classically. Grover's algorithm reduces this effective security to approximately 85 bits — still considered acceptable, but meaningfully degraded. SHA-256 collision resistance is not immediately broken, but organizations using SHA-256 for long-lived integrity guarantees (code signing, certificate pinning, long-term document authentication) face increased risk.

**The more immediate tampering threat:** A quantum adversary that can forge digital signatures (via Shor's on RSA/ECDSA) can also tamper with signed data without detection — because the signature that would normally detect the tampering can itself be forged.

**PQC mitigation:** SHA-384 or SHA-3-512 for hash functions (doubling effective quantum security). ML-DSA for signed data integrity. For highest-assurance applications (root certificate signing, long-term archive authentication), SLH-DSA provides hash-based signature diversity.

**Governance implication:** Data integrity programs that rely on cryptographic signatures — code review attestations, audit logs, regulatory filings, contract archives — must be reviewed against the timeline of signature scheme quantum vulnerability.
````
````{tab-item} R — Repudiation
**Classical definition:** An entity denies having performed an action — claiming a transaction was not authorized, a document was not signed, or a communication was not sent.

**Quantum-era manifestation:** Non-repudiation in digital systems relies on digital signatures. If RSA or ECDSA signatures can be forged by a quantum adversary, then the entire legal and regulatory framework built on digital non-repudiation becomes vulnerable. A party could plausibly claim that a digitally signed contract, transaction, or communication was forged — and under a quantum attack scenario, that claim becomes impossible to definitively refute.

**High-stakes examples:**
- Financial transaction authorization — "I didn't authorize that wire transfer; the signature was forged"
- Contract disputes — "My signature on that agreement was computationally fabricated"
- Regulatory filings — "That compliance attestation bearing our ECDSA signature was not generated by us"
- Healthcare consent forms — "That treatment authorization was not authentically signed by the patient"

**The timeline problem:** Long-lived legal obligations (contracts, deeds, wills, regulatory certifications) signed today with RSA or ECDSA may face repudiation challenges in 10–15 years — when Q-Day has potentially passed and signature forgery becomes feasible.

**PQC mitigation:** Migrating to ML-DSA for new signatures addresses future repudiation risk. For existing long-lived signed documents, organizations should consider timestamping services that create a cryptographic chain of custody under multiple signature schemes — so that even if one scheme is broken, the record's authenticity can be established through complementary means.

**Governance implication:** Legal and compliance teams must be part of the PQC migration conversation — not just information security teams. The repudiation implications of quantum signature forgery extend into contract law, regulatory enforcement, and fiduciary accountability.
````
````{tab-item} I — Information Disclosure
**Classical definition:** Sensitive information is exposed to parties not authorized to see it — a data breach, an eavesdropped communication, an unauthorized database access.

**Quantum-era manifestation:** This is the most direct and well-understood quantum cryptographic threat. Shor's algorithm breaks RSA and ECC key exchange, meaning any data encrypted under RSA or ECC key exchange can be decrypted by a quantum adversary with access to a fault-tolerant gate-model machine.

**Harvest Now, Decrypt Later (HNDL)** makes this threat *present*, not future. Nation-state adversaries are collecting and archiving encrypted data today for future quantum decryption. The Information Disclosure threat is therefore already occurring — the decryption is deferred, but the capture is happening now.

**Data categories with highest quantum-era Information Disclosure risk:**
| Data Category | Confidentiality Lifetime | Quantum Risk Level |
|---|---|---|
| Defense specifications | 25–50 years | 🔴 Critical |
| Healthcare genomic data | 50+ years | 🔴 Critical |
| Financial transaction records (regulatory retention) | 10–25 years | 🔴 High |
| Client relationship data | 7–15 years | 🟠 High |
| M&A strategy and negotiations | 2–5 years | 🟡 Moderate |
| General business communications | 1–3 years | 🟢 Lower |

**PQC mitigation:** ML-KEM (CRYSTALS-Kyber) for key encapsulation — replacing RSA and ECC in TLS key exchange. Hybrid TLS (running ML-KEM alongside classical key exchange) provides immediate quantum resistance for new connections while migrating existing systems.

**Governance implication:** Every data classification program must include "quantum confidentiality horizon" — assessing how long data must remain confidential and whether the Mosca Inequality puts it at risk.
````
````{tab-item} D — Denial of Service
**Classical definition:** A system is made unavailable to legitimate users — through resource exhaustion, flooding, or disruption.

**Quantum-era manifestation:** Denial of Service is the STRIDE category where quantum computing's direct threat is most limited. Quantum computers do not provide a meaningful speedup for network flooding, resource exhaustion attacks, or most classical DoS vectors. However, two quantum-adjacent DoS risks warrant attention:

**PKI collapse scenario:** If a quantum adversary forges root certificate authority certificates, browsers and operating systems worldwide would reject all digital certificates signed under that CA chain. This could trigger a cascading denial of service across the entire HTTPS internet — not because of bandwidth flooding, but because trust anchors have been compromised. The "DoS" is the loss of authentication infrastructure.

**PQC migration disruption:** Poorly executed PQC migrations can themselves cause service disruptions. Hybrid TLS configurations with mismatched algorithm support cause TLS handshake failures. Certificate renewals that introduce PQC algorithms not yet supported by legacy clients break connectivity. The migration process is itself a DoS risk if managed without careful rollout discipline.

**Governance implication:** DoS risk in the quantum era is primarily an availability risk arising from cryptographic infrastructure failure — not from quantum computers being used as attack tools directly. Business continuity planning for PQC migration should include rollback procedures and staged deployment to avoid self-inflicted availability incidents.
````
````{tab-item} E — Elevation of Privilege
**Classical definition:** An attacker gains capabilities or access rights beyond what they were authorized — escalating from a standard user to an administrator, or from an unprivileged process to a system-level process.

**Quantum-era manifestation:** Authentication and authorization systems rely on cryptographic foundations. If those foundations are broken, the entire privilege hierarchy they enforce becomes manipulable.

**Specific quantum-era privilege escalation vectors:**
- **Certificate forgery → administrator impersonation:** An adversary who can forge digital certificates can impersonate any system administrator, domain controller, or cloud IAM principal — gaining full administrative access to any system that trusts certificate-based authentication
- **Kerberos ticket forgery:** Kerberos authentication (ubiquitous in Windows enterprise environments) uses RSA and ECC for ticket encryption. A quantum adversary could forge Kerberos golden tickets — the highest level of Windows domain credential — for any enterprise whose domain controllers have not migrated to PQC
- **JWT/OAuth token forgery:** Modern web applications use RSA-signed JSON Web Tokens (JWTs) for authorization. Quantum signature forgery enables fabrication of arbitrary JWTs, granting any claimed authorization scope
- **HSM key extraction:** Some hardware security modules use RSA-protected key wrapping. A quantum adversary with captured key-wrapping ciphertext could eventually extract master keys, gaining access to all secrets protected by that HSM

**PQC mitigation:** ML-DSA for all authentication token signing. PQC-capable Kerberos configurations (NIST and Microsoft are developing standards). PQC key wrapping for HSMs. Zero-trust architecture as a defense-in-depth measure that reduces blast radius even if authentication mechanisms are compromised.

**Governance implication:** Identity and access management teams must be included in PQC migration programs alongside network security and certificate management. The Elevation of Privilege category reveals that quantum cryptographic threats are ultimately threats to the entire authorization hierarchy — not just data confidentiality.
````
`````

### STRIDE → PQC Migration Priority Matrix

The power of STRIDE as a governance tool is that it maps security threats to organizational functions and then to specific mitigation priorities. The matrix below translates the six STRIDE categories into a quantum-era migration priority framework:

| STRIDE Threat | Quantum Vector | Migration Priority | Primary PQC Control |
|---|---|---|---|
| Spoofing | RSA/ECDSA signature forgery | 🔴 Critical | ML-DSA |
| Tampering | Signature forgery + hash weakening | 🔴 Critical | ML-DSA + SHA-384 |
| Repudiation | Long-lived signature validity | 🟠 High | ML-DSA + timestamping |
| Information Disclosure | Shor's on key exchange + HNDL | 🔴 Critical (now) | ML-KEM (hybrid TLS) |
| Denial of Service | PKI cascade failure | 🟠 High | Migration risk management |
| Elevation of Privilege | Auth token + Kerberos forgery | 🔴 Critical | ML-DSA + IAM migration |

::::{admonition} Using STRIDE as a Board Communication Tool
:class: tip

The Mosca Inequality tells you *when* you are at risk. STRIDE tells you *what* you are at risk of losing. Together, they form the complete governance argument:

1. **Apply the Mosca Inequality** to your most sensitive data categories → tells you whether you are already in deficit
2. **Apply STRIDE** to your security architecture → tells you exactly which systems face which threats and in what priority order
3. **Map STRIDE findings to your cryptographic inventory** (from the crypto-agility framework) → produces a defensible, prioritized migration backlog that any CISO, audit committee, or regulator can evaluate

This is the framework that turns "quantum is a future problem" into "we have six specific categories of present and near-term risk, prioritized by impact and migration cost."
::::

---

## 5.10 Flagship Case Study: A Global Bank's Four-Year PQC Migration

*The following case study is a composite based on publicly disclosed PQC migration programs at major financial institutions, including JPMorgan Chase, BNY Mellon, and HSBC, combined with patterns observed in financial sector PQC readiness assessments.*

:::{figure} ../images/ch05-bank-migration-case.png
:label: fig-bank-migration-case
:alt: Global bank PQC migration four-year roadmap showing inventory, hybrid TLS pilot, vendor coercion, and full migration phases.
:width: 90%
:align: center

**A Global Bank's Four-Year PQC Migration Roadmap.** Phase 1 (months 1–6): Cryptographic inventory — which revealed hundreds of forgotten long-lived keys in embedded systems. Phase 2 (months 7–18): Hybrid TLS pilot. Phase 3 (months 19–30): Vendor coercion campaign. Phase 4 (months 31–48): Full migration and ongoing monitoring.
:::

### Situation

A Tier-1 global investment bank with operations in 40 countries, \$2.8 trillion in assets under custody, and approximately 12,000 software systems commissioned a quantum risk assessment in 2022. The assessment concluded:

- The bank held financial transaction records with regulatory retention requirements of 10–25 years
- Estimated migration timeline: 5–7 years given legacy system complexity
- Applying the Mosca Inequality with a conservative Q-Day estimate of 2032: the bank was **already in deficit** for its longest-lived data categories

A STRIDE analysis of the bank's security architecture identified Information Disclosure (via HNDL of transaction data) and Elevation of Privilege (via Kerberos ticket forgery in its Windows domain) as the two highest-priority threat categories, followed by Spoofing (certificate forgery affecting its client-facing banking portals).

### Quantum Angle

The board received a briefing that quantified the risk in business terms. The STRIDE framing proved decisive: instead of "quantum computers might break encryption someday," the CISO presented: "We have six specific threat categories. Three are critical priority. Here is the Mosca deficit for each data category. Here is what an adversary could do to us in each STRIDE category when Q-Day arrives." The board authorized a \$340 million four-year migration program the same quarter.

### Decisions Made

**Phase 1 — The Inventory (Months 1–6):** The six-month inventory revealed:
- **4,847 certificates** using RSA-2048 or below
- **1,203 cryptographic endpoints** using TLS 1.2 with deprecated cipher suites
- **89 embedded systems** — primarily SWIFT messaging gateways and ATM firmware — using long-lived RSA keys, some not rotated in 11 years
- **23 vendor systems** with cryptographic algorithms hardcoded in closed-source software, with no PQC roadmap

**Phase 2 — Hybrid TLS Pilot (Months 7–18):** The bank deployed hybrid TLS 1.3 with ML-KEM-768 key exchange for its highest-volume internal service mesh — approximately 3.2 billion TLS connections per day. Performance impact: less than 2% latency increase. Immediate quantum resistance for new connections while maintaining backward compatibility.

**Phase 3 — Vendor Coercion (Months 19–30):** Of 23 vendors with no PQC roadmap, 14 published credible timelines after receiving contractual notices that procurement renewals would require PQC certification. Five were replaced. Four received time-limited exceptions with financial penalties for non-compliance.

**Phase 4 — Board Reporting:** Quarterly board reporting using the Mosca Inequality — RED/YELLOW/GREEN classification for each cryptographic asset category, migration progress, and revised Mosca risk profile. This cadence kept the migration funded across three CEO transitions.

### Measured Outcome

By the end of Year 4:
- 96% of cryptographic endpoints migrated to PQC or hybrid configurations
- All 89 embedded system long-lived keys replaced with automated rotation policies
- All vendor contracts updated to require PQC certification for renewals
- Migration cost: \$340 million over four years
- Regulatory benefit: favorable examination findings from three regulators citing the PQC program as a model for the sector

### Open Question

The 4% not yet migrated remained in mainframe COBOL applications — systems whose source code had been partially lost. The open question: rewrite the application (\$80M, 12–18 months), replace the hardware (24-month cycle), or deploy a quantum-secure proxy layer (faster, cheaper, but adds an architectural layer)?

---

## 5.11 Industry Snapshots

### Snapshot A: Energy Grid SCADA — The 30-Year Key Problem

A North American electric utility's SCADA systems were found to be using RSA-1024 keys provisioned in the mid-2000s. Their documented operational lifespans extended to 2045. Applying the Mosca Inequality: key lifetime to 2045, SCADA migration requiring 5–8 years (99.999% uptime requirement), Q-Day potentially early 2030s. The utility was already late.

A STRIDE analysis mapped the exposure: Elevation of Privilege (forged SCADA authentication tokens enabling direct control of power generation equipment) and Information Disclosure (operational technology network traffic revealing grid topology to adversaries) were classified as national security risks. The migration program began immediately.

### Snapshot B: Government Agency — CNSA 2.0 + STRIDE Governance

A U.S. federal defense agency received CNSA 2.0 mandate requirements in 2022 and conducted a parallel STRIDE analysis across its 3,200 cryptographic endpoints. The STRIDE framework revealed that Spoofing (forged contractor credentials) and Repudiation (plausible deniability of signed intelligence reports) were the two threat categories most critical to mission integrity — and both mapped directly to the agency's most heavily used ECDSA signature infrastructure.

The agency's "Never deploy new classical" policy (from January 2023, no new system could use classical-only cryptography) was justified to leadership using the STRIDE matrix: the six-row table of quantum-era threats, mapped to operational mission risk, was the document that secured both budget and executive commitment. By 2025, 40% of endpoints were PQC or hybrid — on pace for 100% completion by 2029, one year ahead of the CNSA 2.0 mandate.

---

## 5.12 Productive-Struggle Problem

::::{admonition} The Challenge: One Page for the CFO
:class: tip

**Scenario:** Your CFO has just told you: "I've got inflation, three regulatory audits, a \$200 million system modernization program, and a board asking about AI strategy. Quantum cryptography is someone else's problem."

**Your task:** Draft a one-page PQC business case that changes their mind. You have 300 words and 90 seconds to present it.

**Constraints:**
- No technical jargon (no RSA, no lattices, no qubits)
- Apply the STRIDE framework — identify the top two threat categories for your organization and quantify their business impact
- Apply the Mosca Inequality — are you in deficit?
- Lead with financial or regulatory consequence, not technical threat
- Include one concrete competitor action or regulatory requirement
- End with a specific ask: the cryptographic inventory (Phase 1)

**Hints:** What is the cost of *not* migrating, in terms the CFO already cares about? What regulatory deadlines create fiduciary obligation? What does your cyber insurer's next renewal questionnaire look like?
::::

::::{dropdown} 💡 Sample Solution Framework (Reveal After Attempting)

**THE QUANTUM RISK BRIEF — ONE PAGE**

**The Risk (STRIDE summary, plain language):** The encryption protecting our most sensitive operations is vulnerable to a known attack arriving in 8–12 years. We have already identified two priority threat categories for our organization using the STRIDE framework: (1) our clients' transaction data faces Information Disclosure risk — adversaries are collecting and archiving it today — and (2) our identity and authentication infrastructure faces Elevation of Privilege risk if our certificate infrastructure is compromised when quantum computers arrive. Three of our six STRIDE threat categories have critical-priority mitigations that take 5–7 years to implement.

**The Mosca Deficit:** Our most sensitive client data has a regulatory confidentiality requirement of [X] years. Our migration will take [Y] years. By the Mosca Inequality, we are [in deficit / approaching deficit] — meaning we cannot complete migration before Q-Day unless we start now.

**The Regulatory Reality:** CNSA 2.0 mandates PQC adoption in the federal supply chain by 2030. EU NIS2 requires state-of-the-art cryptography for covered entities. Our cyber insurer's renewal questionnaire now includes PQC maturity questions.

**What Peers Are Doing:** JPMorgan Chase began a PQC migration program in 2022. Organizations that started in 2022 are finishing now. We are starting in [year].

**The Ask:** \$[X]M for a six-month cryptographic inventory (Phase 1). Deliverable: a complete asset map, STRIDE risk classification, Mosca deficit calculation, and board-ready migration roadmap. Cost of inaction: [regulatory fine exposure + insurance premium trajectory + competitive risk].

::::

---

## 5.13 Module-Level Outcomes

By the end of this chapter, you should be able to:

::::{card-carousel} 1

:::{card} Outcome 1
**Distinguish quantum paradigms for security purposes.**

Explain why gate-model quantum computers (IBM, Google, IonQ) pose the cryptographic threat via Shor's algorithm, while quantum annealers (FAU's D-Wave Advantage2) do not run Shor's and are not the encryption threat vector. Apply this distinction accurately in board-level security conversations.
:::

:::{card} Outcome 2
**Explain Shor's and Grover's cryptographic consequences without notation.**

Describe how Shor's algorithm breaks RSA and ECC, how Grover's halves symmetric key security, and how Harvest Now, Decrypt Later makes both threats present — not future — operational risks.
:::

:::{card} Outcome 3
**Apply STRIDE threat modeling to quantum-era security risks.**

Map each of the six STRIDE categories to its quantum-era manifestation, identify the primary PQC controls for each, and produce a priority matrix for a given organization's security architecture. Use STRIDE as the governance vocabulary for communicating quantum security risk to non-technical leadership.
:::

:::{card} Outcome 4
**Evaluate NIST PQC standards and enterprise implications.**

Distinguish ML-KEM, ML-DSA, and SLH-DSA by purpose, mathematical foundation, and deployment context. Explain why lattice-based cryptography is resistant to quantum attacks and what the transition means for certificates, TLS, code signing, and PKI infrastructure.
:::

:::{card} Outcome 5
**Apply the Mosca Inequality and design a crypto-agility migration plan.**

Given a data asset with a defined confidentiality lifetime and estimated migration timeline, determine whether the organization is in deficit relative to Q-Day estimates. Outline the four phases of a crypto-agility program and specify what a prioritized migration backlog should contain.
:::

:::{card} Outcome 6
**Assess regulatory, insurance, and fiduciary exposure for delay.**

Identify the key regulatory frameworks (CNSA 2.0, EU NIS2, DORA, financial sector guidance) that create PQC obligations, describe the emerging cyber insurance implications, and frame quantum risk delay as a fiduciary accountability issue.
:::

::::

---

## 5.14 Lab 5A — Breaking Something Small (Quantum Period Finding)

**Duration:** ~45 minutes
**Tools:** [IBM Quantum Composer](https://quantum.ibm.com/composer) or [Quirk Quantum Circuit Simulator](https://algassert.com/quirk)
**No coding required**

### Background

You cannot run Shor's algorithm at real RSA scale on current quantum hardware — we don't yet have a fault-tolerant gate-model machine with enough logical qubits. But you *can* run the core mathematical operation — **quantum period finding** — at a tiny scale. The smallest meaningful example uses the number **15** (= 3 × 5).

### Instructions

::::{tab-set}
````{tab-item} Step 1: Set Up the Circuit
Navigate to IBM Quantum Composer or Quirk. Build a 7-qubit circuit:
- **4 input qubits** (the quantum register for period finding)
- **3 work qubits** (the function evaluation register for f(x) = 2^x mod 15)

Apply Hadamard gates to the 4 input qubits to create equal superposition of all 16 states.
````
````{tab-item} Step 2: Modular Exponentiation
Apply controlled operations implementing f(x) = 2^x mod 15 to the work register. In IBM Composer, use the pre-built template. In Quirk, search for "Modular Exponentiation" for N=15, a=2.

The work register now contains the values of 2^x mod 15 for all superposed values of x simultaneously.
````
````{tab-item} Step 3: Quantum Fourier Transform
Apply the Quantum Fourier Transform (QFT) to the input register. This is where quantum interference amplifies the period and suppresses everything else. Available as a circuit block in IBM Composer; build from H gates, controlled-phase rotations, and SWAPs in Quirk.
````
````{tab-item} Step 4: Measure and Interpret
Measure the input register. Run the simulation 1,000 times. You should see probability concentrated at multiples of 1024/r, where r is the period.

For f(x) = 2^x mod 15, the period is r=4. Spikes at 0, 256, 512, 768. From r=4: gcd(2^(r/2) - 1, 15) = gcd(3, 15) = 3; gcd(2^(r/2) + 1, 15) = gcd(5, 15) = 5. You have factored 15 = 3 × 5 using quantum period finding.
````
````{tab-item} Step 5: Scale Reflection
RSA-2048 uses 617-digit numbers. This circuit used 7 qubits for the number 15. Shor's on RSA-2048 requires ~4,000–10,000 logical qubits, each requiring 1,000+ physical qubits for error correction — 4–10 million physical qubits total. Today's best gate-model machines have ~1,000 noisy physical qubits. The mathematics works. The engineering gap is real but narrowing.
````
`````

### Deliverable

Write a **400-word explanation** for a non-technical board member that:
1. Describes what you observed in the simulation (plain English, no equations)
2. Explains the connection between quantum interference and why the correct period appeared
3. Explains why the same mechanism scales to break real RSA encryption
4. Concludes with a specific recommendation the board should act on

---

## 5.15 Lab 5B — PQC Key Generation: Building the New Locks

**Duration:** ~60 minutes
**Tools:** Python 3.9+, `liboqs-python` library (Open Quantum Safe project)
**Platform:** [Google Colab](https://colab.research.google.com) (no local install required)

<a href="https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch05-pqc-key-generation.ipynb" target="_blank">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="margin-bottom: 1rem;"/>
</a>

### Background

The NIST PQC standards (ML-KEM, ML-DSA, SLH-DSA) are not theoretical. They are implemented, tested, and production-deployable today. This lab takes you from abstract standards to working code — generating real post-quantum keypairs, encrypting a message with ML-KEM, signing it with ML-DSA, and simulating a hybrid TLS handshake that runs both classical and post-quantum cryptography simultaneously.

The Open Quantum Safe (OQS) project, maintained by the University of Waterloo and partners, provides `liboqs` — the reference implementation of NIST PQC algorithms. It is the same codebase used by Cloudflare, AWS, and Google in their PQC deployment experiments.

### Lab Architecture

```{mermaid}
flowchart LR
    A[Generate ML-KEM Keypair] --> B[Encapsulate: Sender encrypts shared secret]
    B --> C[Decapsulate: Receiver recovers shared secret]
    C --> D[Verify shared secrets match]
    
    E[Generate ML-DSA Keypair] --> F[Sign message with private key]
    F --> G[Verify signature with public key]
    G --> H[Tamper with message — verify detection]
    
    D --> I[Hybrid TLS Simulation]
    H --> I
    I --> J[Benchmark: Classical vs PQC performance]
    
    style A fill:#e3f2fd
    style E fill:#e8f5e9
    style I fill:#fff3e0
    style J fill:#fce4ec
```

### Part 1: ML-KEM Key Encapsulation

```python
import oqs

# Generate ML-KEM-768 keypair (the primary NIST standard)
with oqs.KeyEncapsulation('ML-KEM-768') as kem:
    public_key = kem.generate_keypair()
    
    # Sender: encapsulate a shared secret using the recipient's public key
    ciphertext, shared_secret_sender = kem.encap_secret(public_key)
    
    # Recipient: decapsulate to recover the same shared secret
    shared_secret_recipient = kem.decap_secret(ciphertext)
    
    assert shared_secret_sender == shared_secret_recipient, "Key exchange failed"
    print(f"✅ ML-KEM-768 key exchange successful")
    print(f"   Public key size:  {len(public_key):,} bytes")
    print(f"   Ciphertext size:  {len(ciphertext):,} bytes")
    print(f"   Shared secret:    {len(shared_secret_sender)} bytes")
    
    # Compare to classical RSA-2048
    # RSA-2048 public key: 256 bytes | ML-KEM-768 public key: 1,184 bytes
    # The size overhead is the cost of quantum resistance
```

### Part 2: ML-DSA Digital Signatures

```python
import oqs
import hashlib

message = b"This contract authorizes payment of $10,000,000 to vendor XYZ."

# Generate ML-DSA-65 keypair (NIST standard for general-purpose signing)
with oqs.Signature('ML-DSA-65') as signer:
    public_key = signer.generate_keypair()
    
    # Sign the message
    signature = signer.sign(message)
    
    # Verify the signature
    is_valid = signer.verify(message, signature, public_key)
    print(f"✅ Signature valid: {is_valid}")
    print(f"   Public key size: {len(public_key):,} bytes")
    print(f"   Signature size:  {len(signature):,} bytes")
    
    # Tamper with the message — verify detection
    tampered_message = b"This contract authorizes payment of $99,999,999 to vendor XYZ."
    is_valid_tampered = signer.verify(tampered_message, signature, public_key)
    print(f"🚨 Tampered message signature valid: {is_valid_tampered}")
    # Expected: False — ML-DSA detects any modification
```

### Part 3: Hybrid TLS Handshake Simulation

The hybrid approach — running both classical and post-quantum cryptography simultaneously — is how Google Chrome and Cloudflare are deploying PQC today. If *either* algorithm is secure, the connection is secure. This provides immediate quantum resistance without requiring the entire ecosystem to upgrade at once.

```python
import oqs, time
from cryptography.hazmat.primitives.asymmetric import rsa, padding
from cryptography.hazmat.primitives import hashes, serialization

def classical_key_exchange():
    """Simulate RSA-2048 key exchange (classical baseline)"""
    start = time.time()
    private_key = rsa.generate_private_key(public_exponent=65537, key_size=2048)
    public_key = private_key.public_key()
    # Encrypt a 32-byte session key
    session_key = os.urandom(32)
    ciphertext = public_key.encrypt(session_key, padding.OAEP(
        mgf=padding.MGF1(algorithm=hashes.SHA256()),
        algorithm=hashes.SHA256(), label=None))
    elapsed = time.time() - start
    return elapsed, len(ciphertext)

def pqc_key_exchange():
    """ML-KEM-768 key exchange"""
    start = time.time()
    with oqs.KeyEncapsulation('ML-KEM-768') as kem:
        public_key = kem.generate_keypair()
        ciphertext, _ = kem.encap_secret(public_key)
    elapsed = time.time() - start
    return elapsed, len(ciphertext)

# Run both and compare
rsa_time, rsa_ct_size = classical_key_exchange()
pqc_time, pqc_ct_size = pqc_key_exchange()

print(f"\n📊 Key Exchange Performance Comparison")
print(f"{'':20} {'RSA-2048':>12} {'ML-KEM-768':>12}")
print(f"{'Time (ms)':20} {rsa_time*1000:>12.2f} {pqc_time*1000:>12.2f}")
print(f"{'Ciphertext (bytes)':20} {rsa_ct_size:>12,} {pqc_ct_size:>12,}")
print(f"\n✅ ML-KEM is typically faster than RSA-2048 for key encapsulation")
print(f"   Size overhead is acceptable for the quantum resistance gained")
```

### Part 4: STRIDE Mapping Exercise

For each cryptographic operation you just implemented, complete the STRIDE mapping:

| Operation | STRIDE Threat Addressed | Classical Algorithm Replaced | PQC Algorithm Used |
|---|---|---|---|
| Key encapsulation | ? | RSA key exchange / ECDH | ML-KEM-768 |
| Message signing | ? | ECDSA / RSA-PSS | ML-DSA-65 |
| Signature verification | ? | ECDSA verify | ML-DSA-65 verify |
| Hybrid handshake | ? | TLS 1.3 with ECDH only | TLS 1.3 with ML-KEM + ECDH |

### Deliverable

1. **Working notebook:** Complete all four parts in the Colab notebook. Capture all output.
2. **Performance comparison table:** Fill in actual timing results from your environment.
3. **500-word CISO briefing:** If you were presenting this lab's outputs to your organization's CISO as evidence that PQC is ready to deploy, what would you say? Address: (a) the performance overhead, (b) which STRIDE threat categories are now addressed, (c) what the immediate next step for your organization should be.

---

## 5.16 Lab 5C (Optional Advanced) — The PQC Migration Scanner

**Duration:** ~90 minutes
**Tools:** Python 3.9+, `cryptography` library, any directory with SSL/TLS certificates or PEM keys

<a href="https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch05-pqc-migration-scanner.ipynb" target="_blank">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="margin-bottom: 1rem;"/>
</a>

### Background

The most expensive phase of any PQC migration program is the inventory — because most organizations do not know where all their cryptographic assets are. This lab builds a **PQC Migration Scanner**: a Python tool that walks a directory tree, finds every certificate and key, extracts the cryptographic metadata, applies the Mosca Inequality, and outputs a prioritized CSV migration report with GREEN/YELLOW/RED STRIDE-aligned classification.

### Core Logic

```python
def stride_mosca_classification(algorithm, key_size, cert_lifetime_years,
                                  migration_years_remaining, qday_estimate_years):
    """
    Apply STRIDE threat mapping + Mosca Inequality to classify a cryptographic asset.
    Returns (stride_threats, mosca_status, buffer_years)
    """
    # STRIDE threat mapping
    stride_threats = []
    if algorithm in ['RSA', 'EC', 'DSA']:
        stride_threats = ['Spoofing', 'Tampering', 'Repudiation',
                          'Information Disclosure', 'Elevation of Privilege']
    elif algorithm in ['AES', 'SHA'] and key_size < 256:
        stride_threats = ['Information Disclosure', 'Tampering']
    
    # Mosca Inequality
    total_exposure = cert_lifetime_years + migration_years_remaining
    buffer = qday_estimate_years - total_exposure
    
    if buffer > 2:
        mosca_status = "GREEN"
    elif buffer > 0:
        mosca_status = "YELLOW"
    else:
        mosca_status = "RED"
    
    return stride_threats, mosca_status, buffer
```

### Sample Output

| File | Algorithm | Key Size | Expires | STRIDE Threats | Mosca Status | Priority |
|------|-----------|----------|---------|----------------|--------------|----------|
| /etc/ssl/server.crt | RSA | 2048 | 2026-03 | S,T,R,I,E | YELLOW | HIGH |
| /etc/ssl/legacy.crt | RSA | 1024 | 2028-06 | S,T,R,I,E | RED | CRITICAL |
| /etc/ssl/client.crt | ECDSA | 256 | 2025-11 | S,T,R,I,E | GREEN | LOW |
| /var/keys/signing.key | RSA | 4096 | N/A | S,T,R,I,E | RED | CRITICAL |

### Deliverable

1. **Working scanner** from the Colab notebook
2. **Sample output CSV** with at least 5 entries classified across GREEN/YELLOW/RED, with STRIDE threat columns populated
3. **500-word CISO summary** interpreting the output: What did you find? What is the priority migration order? What is the Mosca deficit? Which STRIDE categories have the most critical exposures?

---

## 5.17 Discussion Guidelines

**Post a substantive response (minimum 300 words) citing at least two sources. Reply meaningfully to TWO peers' posts.**

### Discussion Prompt

You are the Chief Information Security Officer of a mid-size regional bank (\$15 billion in assets, 1,200 employees). The board has asked you to brief them on quantum cryptographic risk at their next quarterly meeting — in 15 minutes.

Prepare your board briefing outline addressing:

1. **STRIDE mapping for your institution** — which of the six threat categories are highest priority for a regional bank, and why? (Think: what data does a bank hold, what authentication systems does it use, what regulatory obligations govern data confidentiality?)

2. **The Mosca Inequality applied** — given that bank customer data has confidentiality requirements of 7–10 years and PQC migration for a \$15B bank would take approximately 4–6 years, where does this bank sit on the Mosca risk spectrum?

3. **The immediate recommendation** — what is the one thing you ask the board to authorize today?

4. **The narrative hook** — boards respond to stories, not frameworks. What is the one concrete scenario — drawn from the STRIDE categories — that makes the risk viscerally real without triggering dismissal as a technology alarmist?

**Peer response guidelines:** Challenge one assumption in their STRIDE priority ordering, propose an alternative Mosca calculation based on different data lifetime assumptions, or extend their analysis with a regulatory angle they may not have considered.

---

## Glossary

```{glossary}
Post-Quantum Cryptography (PQC)
  Cryptographic algorithms designed to be secure against both classical and quantum computer attacks. NIST finalized the first three PQC standards in 2024: ML-KEM, ML-DSA, and SLH-DSA.

Shor's Algorithm
  A quantum algorithm published by Peter Shor in 1994 that factors large integers in polynomial time on a gate-model quantum computer, breaking RSA and ECC encryption. Does not run on quantum annealers such as the D-Wave Advantage2.

Grover's Algorithm
  A quantum algorithm that provides a quadratic speedup for searching unstructured data. Halves the effective security of symmetric encryption algorithms.

Gate-Model Quantum Computer
  A quantum computing architecture (IBM, Google, IonQ, Quantinuum) that builds computation from sequences of quantum logic gates. General-purpose and capable of running Shor's algorithm on a future fault-tolerant device. Distinct from quantum annealers.

Quantum Annealer
  A quantum computing architecture (D-Wave Advantage2) purpose-built for combinatorial optimization problems. Uses quantum tunneling to find low-energy solutions. Cannot run Shor's algorithm and is not the cryptographic threat vector.

STRIDE
  A structured threat modeling framework categorizing security threats as Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, and Elevation of Privilege. Applied in this chapter to map quantum-era cryptographic threats to governance-level risk categories.

RSA (Rivest–Shamir–Adleman)
  A widely used public-key cryptographic algorithm whose security depends on the difficulty of prime factorization. Vulnerable to Shor's algorithm running on a fault-tolerant gate-model quantum computer.

ECC (Elliptic Curve Cryptography)
  A family of public-key cryptographic algorithms based on elliptic curve mathematics. Also vulnerable to Shor's algorithm via quantum algorithms for the discrete logarithm problem.

Q-Day
  The anticipated date when a fault-tolerant gate-model quantum computer capable of running Shor's algorithm at RSA scale becomes operational. Most analyst estimates cluster in the 2030–2035 window.

Harvest Now, Decrypt Later (HNDL)
  An attack strategy in which adversaries collect and store encrypted data today with the intention of decrypting it when sufficient quantum computing capability becomes available.

Mosca Inequality
  The inequality formulated by Michele Mosca stating that an organization is at quantum cryptographic risk if the lifetime of its sensitive data plus its migration time exceeds the time until Q-Day.

ML-KEM (Module Lattice Key Encapsulation Mechanism)
  The primary NIST PQC standard for key exchange, based on the hardness of lattice problems. Formerly CRYSTALS-Kyber. Replaces RSA and ECC in TLS key exchange.

ML-DSA (Module Lattice Digital Signature Algorithm)
  The primary NIST PQC standard for digital signatures, based on lattice mathematics. Formerly CRYSTALS-Dilithium. Replaces ECDSA in code signing and PKI.

SLH-DSA (Stateless Hash-Based Digital Signature)
  A NIST PQC standard for digital signatures based on hash functions rather than lattice problems. Formerly SPHINCS+. Provides algorithmic diversity as a hedge against future lattice attacks.

Lattice Cryptography
  A family of cryptographic schemes based on mathematical problems in high-dimensional lattice structures. No known quantum algorithm (including Shor's) provides a meaningful speedup for the core lattice problems.

Learning With Errors (LWE)
  A mathematical problem underlying ML-KEM and ML-DSA. Involves solving noisy linear equations over a lattice — computationally hard for both classical and quantum computers.

Crypto-Agility
  The engineering design principle of building cryptographic systems with abstraction layers that allow algorithms to be swapped without requiring full system redesign.

Hybrid Cryptography
  A deployment strategy that runs both classical and post-quantum cryptographic algorithms simultaneously for the same operation. Provides quantum resistance immediately while maintaining backward compatibility.

CNSA 2.0 (Commercial National Security Algorithm Suite 2.0)
  NSA's mandate requiring U.S. national security systems to migrate to post-quantum cryptography, with deadlines from 2025 (new systems) to 2035 (all systems).

NIS2 Directive
  The EU's Network and Information Security Directive 2, effective 2024, requiring critical infrastructure operators to maintain "state-of-the-art" cybersecurity — increasingly interpreted to include PQC migration planning.

Open Quantum Safe (OQS)
  An open-source project providing reference implementations of NIST PQC algorithms, including the liboqs library used in Lab 5B. The same codebase used in Cloudflare, AWS, and Google PQC experiments.

PKI (Public Key Infrastructure)
  The framework of certificates, certificate authorities, and trust chains enabling public-key cryptography at internet scale. Must be completely re-engineered to support PQC algorithms.

TLS (Transport Layer Security)
  The cryptographic protocol securing internet communications (HTTPS, VPNs, email). The most pervasive deployment of RSA and ECC, and thus the primary target of PQC migration.
```

---

## 5.18 Leader's Takeaway

::::{admonition} The Leader's Takeaway
:class: important

The first trillion dollars of quantum value will come not from a new drug or a new battery but from the silent, unglamorous work of replacing the locks on every door before someone else gets a key.

This chapter has given you the complete security governance toolkit. The paradigm distinction tells you what to worry about — gate-model quantum computers, not the annealer your university owns. The Mosca Inequality tells you whether you are already late. The NIST PQC standards tell you what the new locks look like. The STRIDE framework gives you the vocabulary to make every one of these risks legible to a CFO, a board, a regulator, and an insurer. The crypto-agility framework tells you how to build infrastructure that can keep pace with a cryptographic landscape that will change multiple times in your career.

What no framework can give you is the decision to start. The organizations that made it in 2020 and 2021 are finishing their migrations now. The window is not closed. But it is closing.

The adversaries collecting your encrypted traffic today are patient, well-funded, and operating with a ten-year time horizon. They are counting on you to delay. They are counting on the CFO to have bigger problems. They are counting on quantum computing to seem abstract and distant until it isn't.

Apply the STRIDE framework to your organization. Calculate your Mosca deficit. Start the inventory. Bring it to the board.

Do not give them the gift of your inaction.
::::

---

## Cross-References

- **See {ref}`ch-01-why-quantum-why-now`** for the FAU/D-Wave Advantage2 context and the distinction between gate-model and annealing quantum computers that grounds this chapter's paradigm clarification.
- **See {ref}`ch-04-hardware-race`** for current fault-tolerant quantum computer timelines and why the Q-Day window estimate matters.
- **See {ref}`ch-06-optimization-goldmine`** for how FAU's D-Wave Advantage2 (an annealer, not the crypto threat) is actually used — for optimization, not cryptographic attacks.
- **See {ref}`ch-09-quantum-ready-enterprise`** for the full enterprise quantum readiness framework, of which PQC migration is one pillar, and the organizational governance structures that make STRIDE-based security programs sustainable.
