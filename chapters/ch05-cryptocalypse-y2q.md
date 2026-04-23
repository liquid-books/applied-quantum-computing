---
title: "Chapter 5: The Cryptocalypse — Y2Q and the Security Imperative"
subtitle: "The Attack Is Already Happening. The Question Is Whether You Finish Before They Decrypt."
short_title: "Ch. 5: The Cryptocalypse"
description: "The cryptographic layer protecting every contract, payment, and medical record is on a migration clock that most organizations have not yet started. This chapter explains Shor's algorithm, NIST PQC standards, the Mosca Inequality, STRIDE threat modeling applied to the quantum era, and how to build a post-quantum cryptography migration roadmap — and optimize it with D-Wave — before Q-Day arrives."
label: ch-05-cryptocalypse-y2q
tags: [post-quantum cryptography, Shor's algorithm, NIST PQC, crypto-agility, Mosca Inequality, Y2Q, cybersecurity, RSA, STRIDE, threat modeling, FAU Advantage2, annealing, gate-model, quantum security, D-Wave, Ocean SDK]
---

# Chapter 5: The Cryptocalypse — Y2Q and the Security Imperative

:::{figure} ../images/ch05-explainer-infographic.png
:label: fig-ch05-explainer-infographic
:alt: Chapter 5 explainer infographic showing the road from today's RSA encryption to Q-Day, with the Mosca Inequality, NIST PQC standards, STRIDE threat model, and crypto-agility framework.
:width: 100%
:align: center

**The Cryptocalypse at a Glance.** Today's RSA encryption is protected by a math problem that classical computers cannot solve in any reasonable timeframe. A fault-tolerant *gate-model* quantum computer running Shor's algorithm dissolves that protection in minutes. The organizations that will survive Q-Day are the ones migrating to post-quantum cryptography now — and using every tool available, including quantum optimization, to execute that migration as efficiently as possible.
:::

Every chapter in this course has asked you to think about quantum computing as an opportunity. This chapter asks you to think about it as an obligation.

The internet you used this morning to check your bank balance, sign a contract, or access a patient record was secured by mathematics invented in the 1970s. That mathematics is brilliant, battle-tested, and ubiquitous — and it has a known expiration date. A specific class of quantum computer, running a specific algorithm discovered in 1994, dissolves the cryptographic foundation of the modern internet. The only question is when that computer will exist — and whether your organization will have finished its migration before it does.

This chapter gives you the technical vocabulary, the governance frameworks, and the practical tools to lead that migration. By the time you reach the labs, you will have formulated both the *threat* — using STRIDE, the structured threat modeling language that security professionals and boards speak — and the *response plan* — optimized on D-Wave's quantum annealer, using the same hardware your campus now hosts.

---

## Opening Scene: Two Conversations, Ten Years Apart

### Conversation One — A War Room in 2015

The National Security Agency's Information Assurance Directorate holds a closed-door briefing for select government contractors. The topic: a classified program code-named **BULLRUN**, and its implications for what comes next. The contractors learn that NSA has spent years and billions of dollars developing capabilities to access encrypted communications — not by breaking mathematics, but by exploiting weak implementations, inserting backdoors into standards, and compromising the random number generators that cryptographic keys depend on.

The takeaway from the briefing is not what NSA has already done. It is the unspoken acknowledgment of what the *next* adversary will be able to do — not in secret, but mathematically, transparently, using published algorithms. A quantum computer running Shor's algorithm does not need backdoors. It does not need implementation flaws. It dissolves the mathematics itself.

A senior official in the room asks how long the agency's analysts believe the window is. The answer is classified. The body language suggests it is shorter than anyone in the private sector believes.

### Conversation Two — A Board Meeting in 2031

The CEO of a regional bank is briefed by outside counsel. An adversary — identity unknown, almost certainly a nation-state — has filed a lawsuit in a foreign jurisdiction claiming to possess evidence that the bank's wire transfer instructions, encrypted at the time of transmission, were unauthorized. The evidence is the decrypted plaintext of transfers the bank executed between 2024 and 2027.

The bank's cryptographic infrastructure was migrated to post-quantum standards in 2029. Two years too late. The transfers in question were encrypted using RSA-2048 key exchange — the standard at the time, the standard everyone used, the standard that took ten years to migrate away from.

The CEO asks the CISO the question that will define the next five years of litigation: *When did we know this was coming, and what did we do about it?*

This chapter is the answer to that question — written in 2026, while the window is still open.

---

## The Single Idea

```{epigraph}
Every other quantum computing application in this course rewards patience — you can wait for hardware to mature before committing. Post-quantum cryptography migration is the exception. The threat does not wait for the hardware to arrive. Nation-state adversaries are harvesting your encrypted data today, storing it for future decryption. The migration clock started the day Shor published his algorithm. The organizations that understand this and start moving now will finish before Q-Day. The ones that treat it as a future problem will not.
```

---

## Part I: Understanding the Threat

### The Paradigm That Matters for Security

Before examining how quantum computing threatens cryptography, it is essential to establish which quantum computer poses that threat — because this course gives you hands-on access to FAU's D-Wave Advantage2, and the distinction changes everything about how you should frame your security conversation.

Throughout this course, you have encountered two fundamentally different quantum computing paradigms. **Gate-model quantum computers** — IBM, Google, IonQ, Quantinuum — build computation from sequences of quantum logic gates, analogous to how classical computers build programs from logic gates. They are general-purpose and capable of running arbitrary quantum algorithms. **Quantum annealers** — FAU's D-Wave Advantage2 — encode optimization problems as energy landscapes and use quantum tunneling to find low-energy solutions. They are purpose-built for combinatorial optimization.

The cryptographic threat comes from gate-model hardware. Shor's algorithm — the algorithm that breaks RSA encryption — requires a gate-model quantum computer. The D-Wave Advantage2 that FAU has installed on its campus, the machine you will use in Lab 5B of this chapter, **cannot run Shor's algorithm**. It is an annealer. It solves optimization problems. It is not the threat.

This distinction is not a technicality. It is the foundation of an accurate security conversation. When a vendor tells your board that "quantum computers threaten your encryption," the informed response is: "A specific class of fault-tolerant gate-model quantum computer will, when hardware at sufficient scale exists. Today's quantum annealers — including the most advanced systems currently deployed — do not pose that threat." What does pose a threat today is something different, and more immediate: the deliberate collection of your encrypted data by adversaries who are waiting for that gate-model machine to arrive.

:::{figure} ../images/ch05-two-paradigms-security.png
:label: fig-ch05-two-paradigms-security
:alt: Two quantum paradigms and their security roles — gate-model as the cryptographic threat, D-Wave annealer as the migration optimization tool.
:width: 100%
:align: center

**Two Paradigms, Two Roles in the Security Story.** Gate-model quantum computers (IBM, Google, IonQ) will eventually run Shor's algorithm and break RSA/ECC encryption. Quantum annealers (FAU's D-Wave Advantage2) cannot run Shor's — but as you will see in Lab 5B, they can be used to *optimize your response* to the threat by solving the migration prioritization problem as a QUBO.
:::

---

### How Encryption Works Today

RSA encryption's security rests on a deceptively simple asymmetry. Multiplying two large prime numbers together takes a computer microseconds. Reversing that operation — starting from the product and recovering the two original primes — is a problem called **prime factorization**, and for numbers with 2,048 binary digits, it is computationally intractable for any classical machine. The best classical algorithms would require more operations than there are atoms in the observable universe, running longer than the current age of the universe. In practice, unbreakable.

Your **public key** is that product — shared freely with the world. Your **private key** is one of the two primes — kept secret. Anyone can encrypt data to you using the product. Only you can decrypt it, because only you know the prime. This asymmetry underpins every HTTPS connection, every banking transaction, every signed software update, every enterprise VPN, every certificate authority that tells your browser which websites to trust.

The genius of RSA is that the same mathematical operation that makes encryption trivially easy — multiplication — makes decryption impossibly hard for anyone without the private key. Classical computers have had fifty years to try to break this. They have not.

::::{admonition} 🔥 The Weight of This
:class: warning

RSA and its cousin ECC (Elliptic Curve Cryptography) are not just one layer of the internet's security. They are the *foundation*. Every other security mechanism — two-factor authentication, zero-trust architecture, encrypted databases, signed certificates — ultimately rests on the assumption that these mathematical problems are hard. When that assumption fails, it does not fail at one company. It fails everywhere, simultaneously. The entire trust layer of the digital economy dissolves at once, unless we have already replaced it.
::::

---

### Shor's Algorithm: The Master Key

In 1994, mathematician Peter Shor published an algorithm that runs on a quantum computer and factors large integers in **polynomial time** — meaning the computation grows modestly with the size of the number, not exponentially. For RSA-2048, this is the difference between "longer than the age of the universe" and "several hours."

Shor's algorithm works by transforming the factoring problem into a period-finding problem — finding the repeating pattern in a mathematical function. On a classical computer, finding that period still requires exponential time. On a quantum computer, it can be solved using **quantum superposition** to explore the solution space simultaneously and **quantum interference** to amplify the correct answer and cancel the incorrect ones.

The result is not merely faster factoring. It is a qualitatively different computational process that exploits quantum mechanics in a way classical computers cannot replicate, no matter how many transistors they have.

:::{figure} ../images/ch05-shors-algorithm-effect.png
:label: fig-shors-algorithm-effect
:alt: Shor's algorithm effect showing quantum computer using quantum interference to break RSA encryption that would take classical computers billions of years.
:width: 90%
:align: center

**Shor's Algorithm: From Intractable to Polynomial.** Classical computers face exponential time for prime factorization. Shor's algorithm — running on a fault-tolerant gate-model quantum computer — reduces this to polynomial time, dissolving RSA-2048's protection in hours rather than geological timescales.
:::

Where Shor's algorithm cannot be applied: quantum annealers. D-Wave's Advantage2 is designed to find minimum-energy configurations of optimization problems. It has no gate sequence, no quantum Fourier transform, no mechanism for running Shor's period-finding procedure. The architecture simply does not support it. This is why FAU's investment in D-Wave hardware is not a security liability — it is an optimization asset, used in Chapter 6 for scheduling and logistics, and used later in this chapter for planning your migration.

::::{admonition} Grover's Algorithm: The Symmetric Threat
:class: note

Shor's algorithm breaks *asymmetric* cryptography (RSA, ECC) completely. **Grover's algorithm** — a separate quantum algorithm — poses a more moderate but real threat to *symmetric* cryptography (AES, SHA). Grover's provides a quadratic speedup for searching unstructured data, effectively halving the security of symmetric key lengths. AES-128 becomes effectively AES-64 against a quantum attacker — a key length that current classical machines can attack. The mitigation is straightforward: use AES-256. But finding and upgrading every AES-128 deployment in a large enterprise is a non-trivial operational project that belongs on the same migration checklist as the RSA replacement.

| Algorithm | Threat Type | Effect | Mitigation |
|---|---|---|---|
| Shor's | Asymmetric (RSA, ECC) | Completely broken | Migrate to PQC (ML-KEM, ML-DSA) |
| Grover's | Symmetric (AES, SHA) | Security halved | Double key length (AES-256, SHA-384) |
::::

---

### Harvest Now, Decrypt Later: The Present Threat

Shor's algorithm requires hardware that does not yet exist at scale. This might suggest the threat is a decade away. It is not — because the adversary does not need to decrypt your data today. They only need to collect it today.

**Harvest Now, Decrypt Later (HNDL)** is the attack strategy in which adversaries collect and archive encrypted data today, storing it at negligible cost, to be decrypted when a fault-tolerant gate-model quantum computer becomes available. Nation-state intelligence agencies, sophisticated criminal organizations, and geopolitical rivals have been executing this strategy for years. The NSA's own intelligence assessments — declassified in fragments and referenced in Congressional testimony — confirm that adversary collection of this type is ongoing.

:::{figure} ../images/ch05-harvest-now-decrypt-later.png
:label: fig-harvest-now-decrypt-later
:alt: Harvest Now Decrypt Later attack diagram showing nation-state actors storing encrypted traffic today to decrypt with quantum computers tomorrow.
:width: 90%
:align: center

**Harvest Now, Decrypt Later: The Theft in Progress.** Encrypted traffic is being collected and archived today — TLS sessions, VPN tunnels, API calls, file transfers. None of it is readable now. All of it becomes readable the day a fault-tolerant gate-model quantum computer runs Shor's algorithm at scale.
:::

The data categories with the longest confidentiality horizons face the gravest HNDL risk. Defense specifications with 30-year classification windows. Genomic health data with lifetime confidentiality obligations. Long-term infrastructure plans, merger negotiations still in progress, intelligence sources and methods. For these categories, a Q-Day in 2032 is not a future event — it is a present threat, because the collection is happening now and the decryption will occur before the data's useful life expires.

::::{admonition} 🔥 The Weight of This
:class: danger

Your most sensitive data from the past five years may already be sitting in adversarial cold storage, waiting. The attack is not coming. For the data categories that matter most — the ones with long confidentiality horizons — it has already happened. Only the decryption is in the future. This reframes the entire security conversation: PQC migration is not about protecting against a future threat. It is about limiting the damage from a collection campaign that is already underway.
::::

---

## Part II: The STRIDE Framework — Six Threats, One Governance Language

Security professionals and boards have spoken STRIDE for twenty-five years. It is the threat modeling vocabulary of enterprise security: **Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege**. When quantum computing threatens cryptography, it does not threaten a single category. It threatens all six — in different ways, at different timelines, with different mitigations.

Using STRIDE to map quantum-era security threats accomplishes something that technical briefings alone cannot: it translates Shor's algorithm into the organizational risk language that CISOs, audit committees, regulators, and cyber insurers already speak. The Mosca Inequality (introduced in the next section) tells you *when* you are at risk. STRIDE tells you *what* you are at risk of losing.

:::{figure} ../images/ch05-stride-quantum-threat-model.png
:label: fig-stride-quantum-threat-model
:alt: STRIDE threat model applied to the quantum era, showing six threat categories mapped to quantum attack vectors, PQC mitigations, and migration priority levels.
:width: 100%
:align: center

**STRIDE Applied to the Quantum Era.** Each of the six STRIDE threat categories has a distinct quantum-era manifestation, a specific PQC mitigation, and a migration priority level. The matrix is the starting point for any board-level quantum security governance conversation.
:::

`````{tab-set}
````{tab-item} S — Spoofing
**What spoofing means classically:** An attacker impersonates a legitimate entity — forging a user identity, a device credential, or a system certificate.

**The quantum-era vector:** Digital signatures are the technical foundation of identity verification on the internet. RSA and ECDSA signatures — which underpin TLS certificates, code signing, email authentication (DKIM), and software supply chain integrity — are broken by Shor's algorithm. A fault-tolerant gate-model quantum computer that can factor RSA keys can forge any RSA or ECDSA signature.

At scale, this means an adversary could impersonate any website, any software publisher, any enterprise identity provider, or any email sender whose infrastructure relies on RSA or ECC signatures. Every HTTPS padlock. Every "this software is from Microsoft." Every authentication token your organization issues.

**Migration priority:** 🔴 Critical
**PQC control:** ML-DSA (CRYSTALS-Dilithium) replaces ECDSA for all digital signatures. Every certificate authority, code-signing pipeline, PKI system, and identity provider must be migrated.

**The governance implication:** Quantum spoofing risk is not limited to your own data. It extends to your ability to trust any external party's digital identity. A quantum adversary who can forge certificates can insert themselves invisibly into any authenticated communication channel — supplier portals, regulatory filings, partner APIs, patient record systems.
````
````{tab-item} T — Tampering
**What tampering means classically:** An attacker modifies data in transit or at rest — altering a message, corrupting a database, injecting content into a data stream.

**The quantum-era vector:** Data integrity on the internet relies on two mechanisms: digital signatures (addressed under Spoofing) and cryptographic hashing (SHA-256, SHA-3). Grover's algorithm provides a quadratic speedup for hash collision attacks, reducing SHA-256's effective collision resistance from 128 bits to approximately 85 bits — still acceptable for most uses today, but meaningfully degraded for long-lived integrity guarantees.

More immediately: a quantum adversary who can forge digital signatures can tamper with *signed* data — contracts, audit logs, regulatory filings, code repositories — without detection, because the signature that would normally reveal the tampering can itself be fabricated.

**Migration priority:** 🔴 Critical
**PQC controls:** SHA-384 or SHA-3-512 for hash functions. ML-DSA for signed data integrity. SLH-DSA for highest-assurance long-term archives.

**The governance implication:** Any compliance program, audit process, or legal framework that relies on the integrity of cryptographically signed records must be reviewed against the quantum tamper timeline.
````
````{tab-item} R — Repudiation
**What repudiation means classically:** An entity denies having performed an action — claiming a transaction was not authorized, a document was not signed, a communication was not sent.

**The quantum-era vector:** Non-repudiation in digital systems rests entirely on digital signatures. If RSA and ECDSA signatures can be forged, then the entire legal and regulatory architecture of digital non-repudiation becomes fragile. A party could plausibly claim that a digitally signed contract, transaction, or communication was fabricated by a quantum adversary — and in a post-Q-Day world, that claim becomes impossible to definitively refute for records signed before the migration.

Long-lived legal obligations are particularly vulnerable: contracts signed today with ECDSA may face repudiation challenges in 2033, when Q-Day has potentially passed and the signatures on those documents can no longer be trusted as unforgeable.

**Migration priority:** 🟠 High
**PQC controls:** ML-DSA for new signatures. Cryptographic timestamping under multiple signature schemes for existing long-lived signed documents, creating a chain of custody that survives the failure of any single algorithm.

**The governance implication:** Legal and compliance teams must be in the room for PQC migration planning — not just information security. The repudiation implications extend into contract law, regulatory enforcement, and fiduciary accountability in ways that technical teams alone will not anticipate.
````
````{tab-item} I — Information Disclosure
**What information disclosure means classically:** Sensitive information is exposed to parties not authorized to see it — a data breach, an eavesdropped communication, an unauthorized access.

**The quantum-era vector:** This is the most direct quantum cryptographic threat. Shor's algorithm breaks RSA and ECC key exchange, meaning any data encrypted under those schemes can be decrypted by a quantum adversary with sufficient hardware. Combined with HNDL, this threat is present today: the collection is ongoing, the decryption is deferred.

The data categories with the longest confidentiality requirements face the most acute exposure. Healthcare genomic data. Defense specifications. Long-term infrastructure contracts. Regulatory correspondence. Client relationship data with decade-long confidentiality obligations.

**Migration priority:** 🔴 Critical — and uniquely *present*, not future
**PQC control:** ML-KEM (CRYSTALS-Kyber) replaces RSA and ECC in TLS key exchange. Hybrid TLS — running both ML-KEM and classical ECDH simultaneously — provides immediate quantum resistance for new connections while the ecosystem migrates.

**The governance implication:** Every data classification program must include a "quantum confidentiality horizon" — assessing how long each data category must remain confidential and whether the Mosca Inequality (next section) puts it in deficit.
````
````{tab-item} D — Denial of Service
**What denial of service means classically:** A system is made unavailable to legitimate users through resource exhaustion, flooding, or disruption.

**The quantum-era vector:** Quantum computers do not provide a meaningful speedup for traditional DoS attack vectors. However, two quantum-adjacent availability risks are real.

First, a **PKI collapse scenario**: if a quantum adversary forges root certificate authority certificates, every browser and operating system that trusts that CA chain begins rejecting all HTTPS connections signed under it. The result is a cascading availability failure across the HTTPS internet — not from bandwidth flooding, but from the destruction of trust infrastructure.

Second, a **migration disruption scenario**: poorly executed PQC migrations themselves cause availability incidents. Hybrid TLS misconfigurations cause handshake failures. PQC certificates not supported by legacy clients break connectivity. The migration is itself a DoS risk if managed without disciplined rollout procedures and rollback capabilities.

**Migration priority:** 🟠 High — via infrastructure risk, not direct attack
**PQC controls:** CA infrastructure migration to ML-DSA. Staged hybrid TLS deployment with rollback procedures. Migration testing in pre-production environments with legacy client simulation.

**The governance implication:** Business continuity planning for the PQC migration must be treated as seriously as the migration itself. The organizations that have experienced self-inflicted availability incidents during certificate migrations — and there are many — know that the operational risk is not the adversary. It is the remediation process.
````
````{tab-item} E — Elevation of Privilege
**What elevation of privilege means classically:** An attacker gains capabilities or access rights beyond what they are authorized — escalating from a user to an administrator, from an application process to a system process.

**The quantum-era vector:** The entire privilege hierarchy in modern enterprise infrastructure is enforced by cryptographic mechanisms. If those mechanisms can be forged, the hierarchy collapses.

Specific vectors: Kerberos golden ticket forgery (Kerberos uses RSA/ECC ticket encryption — a quantum adversary with captured Kerberos traffic could eventually forge tickets granting full domain administrator access to any enterprise network). JWT and OAuth token forgery (most modern web applications use RSA-signed JSON Web Tokens for authorization — a quantum adversary can fabricate tokens claiming any authorization scope). HSM key extraction (hardware security modules that use RSA key wrapping to protect master secrets could be compromised by a quantum adversary with captured key-wrapping ciphertext, yielding access to every secret the HSM protects).

**Migration priority:** 🔴 Critical
**PQC controls:** ML-DSA for all authentication token signing. PQC-capable Kerberos configurations. PQC key wrapping for HSMs. Zero-trust architecture as defense-in-depth that limits blast radius even when authentication mechanisms are compromised.

**The governance implication:** Identity and access management teams must be included in PQC migration programs from the beginning. Elevation of Privilege reveals that quantum cryptographic risk is ultimately a risk to the entire authorization hierarchy — every system that grants access based on a cryptographic credential is exposed.
````
`````

### The STRIDE-to-Migration Priority Matrix

STRIDE's power as a governance tool is that it maps threats to organizational functions — and then to specific migration actions. This matrix is the starting point for translating a quantum risk assessment into a defensible migration backlog:

| Threat | Quantum Vector | Priority | Primary PQC Control | Org Function Responsible |
|---|---|---|---|---|
| Spoofing | RSA/ECDSA signature forgery | 🔴 Critical | ML-DSA | PKI / Certificate Management |
| Tampering | Signature forgery + hash weakening | 🔴 Critical | ML-DSA + SHA-384 | Security Engineering |
| Repudiation | Long-lived signature validity | 🟠 High | ML-DSA + timestamping | Legal / Compliance |
| Information Disclosure | Shor's key exchange + HNDL | 🔴 Critical (now) | ML-KEM hybrid TLS | Network Security |
| Denial of Service | PKI cascade / migration risk | 🟠 High | Staged rollout + rollback | Operations / BCP |
| Elevation of Privilege | Kerberos / JWT / HSM forgery | 🔴 Critical | ML-DSA + IAM migration | Identity / IAM |

---

## Part III: The New Locks — NIST PQC Standards

In 2024, after an eight-year global cryptanalysis competition that began in 2016, NIST finalized the first three post-quantum cryptography standards. These are not experimental algorithms. They are the result of the most rigorous public cryptographic evaluation process in history — reviewed by hundreds of researchers across dozens of countries, with the explicit goal of identifying schemes that resist both classical and quantum attacks.

The reason these algorithms are quantum-resistant where RSA is not comes down to the nature of the mathematical problem each relies on. RSA's prime factorization problem has a periodic structure that Shor's algorithm exploits through quantum interference. The NIST PQC standards are built on problems — particularly in high-dimensional lattice mathematics — that have no such periodic structure for Shor's to exploit.

`````{tab-set}
````{tab-item} ML-KEM
**ML-KEM** (Module Lattice Key Encapsulation Mechanism), formerly CRYSTALS-Kyber, is the primary standard for **key exchange**. It replaces the RSA and ECC key encapsulation used in TLS to establish shared secrets between a browser and a server, between two enterprise services, or between a client application and a cloud API.

Its security rests on the **Learning With Errors (LWE)** problem: given a set of linear equations with small amounts of intentional noise added, recovering the original system is computationally hard for both classical and quantum computers. Unlike RSA, there is no known quantum algorithm that provides a meaningful speedup for LWE.

ML-KEM is already deployed experimentally in Google Chrome, Cloudflare's edge network, and AWS's post-quantum TLS configurations. Performance overhead compared to RSA: minimal — ML-KEM key encapsulation is typically *faster* than RSA-2048, with a modest increase in key and ciphertext size.
````
````{tab-item} ML-DSA
**ML-DSA** (Module Lattice Digital Signature Algorithm), formerly CRYSTALS-Dilithium, is the primary standard for **digital signatures**. It replaces ECDSA and RSA signatures in TLS certificates, code signing, document authentication, email signing (DKIM), and the entire PKI infrastructure.

Also lattice-based (LWE), ML-DSA addresses the Spoofing, Tampering, Repudiation, and Elevation of Privilege categories from the STRIDE matrix simultaneously — because all four ultimately depend on the unforgeability of digital signatures.

The enterprise implication: every certificate authority, every code-signing pipeline, every PKI system, every identity provider that issues signed credentials must be migrated to support ML-DSA. This is infrastructure migration, not configuration change — and it is the reason PQC timelines are measured in years.
````
````{tab-item} SLH-DSA
**SLH-DSA** (Stateless Hash-Based Digital Signature), formerly SPHINCS+, provides a **hash-based alternative** for digital signatures. Unlike ML-KEM and ML-DSA, which rest on lattice mathematics, SLH-DSA depends only on the security of hash functions — a completely different mathematical foundation.

This algorithmic diversity is a deliberate design choice. If a future mathematical breakthrough attacks lattice problems, organizations that deployed *only* lattice-based PQC would be exposed. SLH-DSA provides the fallback — if lattice cryptography falls, hash-based signatures remain standing.

The trade-off: SLH-DSA signature sizes are significantly larger than ML-DSA, making it impractical for high-frequency applications. It is best suited for root certificate signing, long-term archive authentication, and critical infrastructure attestation — exactly the categories where the Repudiation risk from the STRIDE matrix is highest.
````
`````

:::{figure} ../images/ch05-nist-pqc-standards.png
:label: fig-nist-pqc-standards
:alt: NIST PQC standards infographic showing ML-KEM, ML-DSA, and SLH-DSA with their mathematical foundations, use cases, and STRIDE threat categories addressed.
:width: 90%
:align: center

**NIST's 2024 PQC Standards Mapped to STRIDE.** ML-KEM addresses Information Disclosure (key exchange). ML-DSA addresses Spoofing, Tampering, Repudiation, and Elevation of Privilege (signature forgery). SLH-DSA provides hash-based algorithmic diversity for the highest-assurance Repudiation scenarios.
:::

---

## Part IV: The Mosca Inequality — Calculating Your Deficit

The technical threat is established. The standards are available. The remaining question is urgency — and the Mosca Inequality provides the framework for calculating it with precision.

::::{prf:definition} The Mosca Inequality
:label: def-mosca-inequality

Formulated by quantum cryptographer Michele Mosca, the Mosca Inequality states:

Let **X** = the time until a quantum computer capable of breaking current public-key cryptography exists (time to Q-Day).
Let **Y** = the time your organization needs to complete a full migration to post-quantum cryptography.
Let **Z** = the time the data you are protecting today must remain confidential.

**If Y + Z > X, you are already late.**

Your migration must be complete before Q-Day. Your data must remain protected for the full duration of its required confidentiality. If the sum of those two timelines exceeds the time until Q-Day, every day you delay compounds your HNDL exposure.
::::

:::{figure} ../images/ch05-mosca-inequality.png
:label: fig-mosca-inequality
:alt: Mosca Inequality diagram with three timeline bars showing data lifetime, migration time, and time to Q-Day, with the red danger zone where Y plus Z exceeds X.
:width: 90%
:align: center

**The Mosca Inequality in Practice.** For each category of sensitive data, the sum of migration time and data lifetime must be less than time-to-Q-Day. Most large enterprises, applied honestly, find themselves already in deficit for their longest-lived data categories.
:::

Applied to realistic enterprise parameters: a major financial institution with 7-year data retention requirements and a 6-year migration timeline needs Q-Day to be at least 13 years away. Intelligence community estimates for Q-Day cluster between 7 and 12 years from today. For that institution's regulatory-retention-period data, the Mosca Inequality is already negative — they are in deficit today.

The Mosca Inequality is not a theoretical framework. It is a fiduciary accountability tool. Leadership teams that understand it and choose not to act are making a documented, affirmative decision to leave sensitive data exposed — and creating a paper trail that future litigation, regulatory examination, or board inquiry will have no difficulty reading.

---

## Part V: Crypto-Agility — Building the Infrastructure for Migration

The most expensive word in PQC migration is *discovery*. Most large organizations do not know where all their cryptographic dependencies are. Legacy applications, embedded firmware, vendor black boxes, mainframe integrations, certificates issued years ago and forgotten — every one of these is a cryptographic dependency that must be found, assessed, prioritized, and replaced.

**Crypto-agility** is the engineering discipline that makes that replacement tractable. It is the practice of building cryptographic systems with abstraction layers — standardized "interfaces" between the application and the cryptographic primitive — so that replacing one algorithm with another does not require rebuilding the entire system.

The analogy: a house with standard doorframe dimensions can have any door replaced in an afternoon. A house where every door is custom-fitted requires tearing out walls. Crypto-agility is the discipline of building standard doorframes before you need to replace the doors.

:::{figure} ../images/ch05-crypto-agility-framework.png
:label: fig-crypto-agility-framework
:alt: Crypto-agility framework showing four phases — Discover, Classify, Deploy Hybrid, Migrate — with timeline and key activities at each phase.
:width: 90%
:align: center

**The Four-Phase Crypto-Agility Program.** Phase 1 (Discovery) is the phase no one wants to fund — and the one that always reveals the most surprises. Phase 4 (Migration) is where STRIDE priorities and Mosca deficit calculations determine the sequencing.
:::

::::{grid} 2

:::{grid-item-card} 🔍 Phase 1: Discovery
Automated inventory of every cryptographic primitive in use: certificates, TLS configurations, code-signing keys, VPN tunnels, HSMs, embedded firmware, third-party APIs. Typically 4–6 months. Always reveals surprises — long-lived keys provisioned years ago and never rotated, vendor systems with hardcoded algorithms, embedded devices with no documented key management.
:::

:::{grid-item-card} 📋 Phase 2: Classification
Apply the STRIDE threat matrix to each discovered asset. Apply the Mosca Inequality to each data category it protects. Generate a RED/YELLOW/GREEN risk classification and a prioritized migration backlog. RED items (Mosca in deficit + Critical STRIDE category) move to Phase 3 immediately.
:::

:::{grid-item-card} 🔀 Phase 3: Hybrid Deployment
Deploy hybrid configurations — running both classical and PQC algorithms simultaneously. Hybrid TLS with ML-KEM provides immediate quantum resistance for new connections. Hybrid signatures provide backward compatibility while migrating relying parties. This phase delivers security value before the migration is complete.
:::

:::{grid-item-card} ✅ Phase 4: Migration Execution
Systematic replacement of classical algorithms with PQC equivalents, starting with the highest-risk assets from Phase 2. Ongoing monitoring for cryptographic regressions. PQC requirements in all new procurement contracts. Board reporting on migration progress using the Mosca risk profile.
:::

::::

---

## Part VI: Regulatory and Fiduciary Exposure

The quantum cryptographic migration is not only a security obligation. It is becoming a legal and regulatory one — with specific, published deadlines.

::::{dropdown} CNSA 2.0 — U.S. National Security Systems
The **Commercial National Security Algorithm Suite 2.0** (NSA, 2022) mandates the transition of all U.S. national security systems to post-quantum cryptography:
- **2025:** New national security systems must support CNSA 2.0 algorithms
- **2030:** Legacy systems in national security applications must complete migration
- **2035:** All national security systems must exclusively use CNSA 2.0 algorithms

Organizations in the federal defense supply chain — government contractors, defense technology vendors, critical infrastructure operators — face these timelines whether or not their own counsel has flagged them.
::::

::::{dropdown} EU NIS2 — Critical Infrastructure
**EU NIS2**, effective October 2024, requires covered organizations to maintain "state-of-the-art" cybersecurity. ENISA's evolving guidance increasingly interprets this to include a credible PQC migration plan. Covered sectors: energy, transport, health, water, digital infrastructure, financial markets, public administration. Non-compliance fines: up to €10 million or 2% of global annual turnover.
::::

::::{dropdown} Financial Sector Signals
**DORA** (Digital Operational Resilience Act): EU financial sector regulation explicitly addresses quantum risk in ICT risk management requirements. **SEC Cybersecurity Disclosure Rules**: material quantum cryptographic exposure arguably meets the disclosure threshold for public companies with long-lived sensitive data. **Cyber insurance**: major insurers are adding PQC migration maturity to underwriting questionnaires; draft policy language in Lloyd's syndicate forms includes quantum-specific exclusion clauses.
::::

---

## Flagship Case Study: A Global Bank's Four-Year Migration

*A composite of publicly disclosed PQC programs at JPMorgan Chase, BNY Mellon, and HSBC, combined with financial sector readiness assessment patterns.*

:::{figure} ../images/ch05-bank-migration-case.png
:label: fig-bank-migration-case
:alt: Global bank PQC migration roadmap showing four phases across four years, with key milestones, STRIDE classification by phase, and Mosca risk profile evolution.
:width: 90%
:align: center

**Four-Year PQC Migration Roadmap.** The bank's STRIDE analysis in the first month classified Information Disclosure and Elevation of Privilege as the two critical-priority categories — driving the decision to begin hybrid TLS deployment and IAM migration simultaneously rather than sequentially.
::::

A Tier-1 global investment bank commissioned a quantum risk assessment in 2022. The assessment applied both the Mosca Inequality and the STRIDE framework. The Mosca calculation: the bank held financial transaction records with 10–25 year regulatory retention requirements; migration timeline estimated at 5–7 years; Q-Day conservative estimate 2032. For its longest-lived data categories, the bank was already in deficit.

The STRIDE analysis identified Information Disclosure (HNDL of transaction data) as the most immediately urgent threat, and Elevation of Privilege (Kerberos golden ticket forgery across its 40-country Windows domain) as the highest-consequence threat if Q-Day arrived without migration complete. The board authorized a \$340 million four-year program the same quarter the STRIDE brief was presented — not because of the technical framing, but because the STRIDE language mapped quantum risk onto categories the audit committee, the general counsel, and the regulators in the room already understood.

**Phase 1 — Discovery (Months 1–6):** The cryptographic inventory revealed 4,847 RSA-2048 or weaker certificates; 89 embedded SWIFT gateway and ATM firmware systems using RSA keys provisioned in 2013, never rotated; and 23 vendor systems with hardcoded classical algorithms and no PQC roadmap. The 89 embedded systems were the shock — nobody knew those keys existed. All 89 were immediately classified RED under the STRIDE/Mosca matrix.

**Phase 2 — Hybrid TLS (Months 7–18):** The bank deployed hybrid TLS 1.3 with ML-KEM-768 for its highest-volume internal service mesh — 3.2 billion TLS connections per day. Latency impact: under 2%. Immediate Information Disclosure protection for new connections while legacy systems were queued for migration.

**Phase 3 — Vendor Coercion (Months 19–30):** Of the 23 vendors with no PQC roadmap, 14 published credible timelines within six months of receiving contractual PQC certification requirements. Five were replaced. Four received time-limited exceptions with contractual milestones and financial penalties.

**Phase 4 — Board Reporting:** Quarterly board reports used the Mosca risk profile — RED/YELLOW/GREEN asset counts, migration progress, and revised deficit calculation against updated Q-Day estimates. This cadence kept the migration funded across three CEO transitions.

**Outcome:** 96% of cryptographic endpoints migrated in four years. All 89 embedded system long-lived keys replaced with automated rotation. Migration cost: \$340 million. Regulatory benefit: favorable examination findings from three regulators, citing the STRIDE-grounded PQC program as a sector model.

---

## Productive-Struggle Problem

::::{admonition} The Challenge: The CFO Who Has Bigger Problems
:class: tip

Your CFO has just told you: "I have inflation, three regulatory audits, a \$200 million system modernization program, and a board demanding an AI strategy. Quantum cryptography is someone else's problem."

Draft a one-page PQC business case that changes their mind. You have 300 words and 90 seconds.

**Constraints:**
- No technical jargon — no RSA, no lattices, no qubits
- Use STRIDE language — identify the top two threat categories for your organization and quantify their financial consequence
- Apply the Mosca Inequality — calculate whether you are in deficit given your data's confidentiality requirements
- Lead with a regulatory or insurance consequence already in your CFO's world
- End with one specific ask: the cryptographic inventory budget

**The hardest part:** Making HNDL feel real without triggering dismissal. How do you describe an attack that is invisible, already in progress, and will not be detected for years — in a way that prompts action rather than paralysis?
::::

::::{dropdown} 💡 Sample Framework (Reveal After Attempting)

**THE QUANTUM RISK BRIEF**

**The threat (plain language):** Nation-state adversaries are collecting our encrypted data today and storing it to decrypt when quantum computers arrive in 8–12 years. This is documented in NSA advisories and implicit in the behavior of intelligence services globally. Two categories of our data are directly exposed: [client transaction records — Information Disclosure risk] and [our authentication infrastructure — Elevation of Privilege risk if our identity systems are not migrated before Q-Day].

**Our Mosca deficit:** Our most sensitive client data has a [X]-year retention requirement. Our migration will take [Y] years. Q-Day is estimated at [Z] years. We are [in deficit / approaching deficit] — we cannot complete migration before Q-Day unless we start this year.

**The regulatory reality:** CNSA 2.0 mandates PQC adoption in the federal supply chain by 2030. EU NIS2 requires state-of-the-art cryptography for covered entities. Our cyber insurer's renewal questionnaire now includes PQC migration maturity questions. These are current obligations, not future ones.

**The competitive signal:** JPMorgan Chase began its PQC migration in 2022 and will finish in 2026. We are starting in [year]. That gap is quantifiable competitive and regulatory risk.

**The ask:** \$[X]M for a six-month cryptographic inventory — Phase 1 of the migration program. Deliverable: a complete asset map, STRIDE classification, Mosca deficit calculation by data category, and a board-ready migration roadmap. We cannot manage what we cannot see. This is the investment that tells us exactly how exposed we are.
::::

---

## Module-Level Outcomes

::::{grid} 1 1 2 2

:::{grid-item-card} Outcome 1
**Distinguish quantum paradigms for security purposes.**
Accurately explain why gate-model quantum computers (IBM, Google, IonQ) pose the cryptographic threat via Shor's algorithm, while quantum annealers (FAU's D-Wave Advantage2) cannot run Shor's and are not the encryption threat vector. Apply this distinction correctly in board-level conversations.
:::

:::{grid-item-card} Outcome 2
**Explain the cryptographic threat in plain language.**
Describe Shor's algorithm's effect on RSA and ECC, Grover's effect on symmetric encryption, and how Harvest Now, Decrypt Later makes both threats operationally present today — for audiences with no physics background.
:::

:::{grid-item-card} Outcome 3
**Apply STRIDE to map quantum-era security threats.**
Complete a STRIDE analysis for a given organization's cryptographic architecture, identify the highest-priority quantum-era threat categories, specify the PQC control for each, and produce a STRIDE-to-migration priority matrix that any CISO, audit committee, or regulator can evaluate.
:::

:::{grid-item-card} Outcome 4
**Apply the Mosca Inequality to calculate migration urgency.**
Given a data asset's confidentiality lifetime and an organization's estimated migration timeline, calculate whether the organization is in Mosca deficit relative to Q-Day estimates, and articulate the implication for migration timeline and HNDL risk.
:::

:::{grid-item-card} Outcome 5
**Evaluate NIST PQC standards and their organizational implications.**
Distinguish ML-KEM, ML-DSA, and SLH-DSA by purpose, mathematical foundation, and STRIDE threat category addressed. Explain what the transition to each standard means for certificates, TLS, code signing, PKI, and identity infrastructure.
:::

:::{grid-item-card} Outcome 6
**Design and optimize a crypto-agility migration program.**
Outline the four phases of a crypto-agility program, identify the STRIDE/Mosca inputs that drive Phase 2 prioritization, and explain how quantum annealing (Lab 5B) can be used to optimize the migration sequencing problem itself.
:::

::::

---

## Lab 5A (Regular): Breaking Something Small — Quantum Period Finding

**Duration:** ~45 minutes
**Tools:** [IBM Quantum Composer](https://quantum.ibm.com/composer) or [Quirk](https://algassert.com/quirk)
**No coding required — circuit simulation only**

### Why This Lab

Shor's algorithm runs on gate-model quantum hardware. FAU's D-Wave Advantage2 cannot run it. Before understanding why, it helps to see what the algorithm actually does — at the smallest possible scale. This lab runs the core mathematical operation behind Shor's algorithm on a simulator: quantum period finding for the number 15 = 3 × 5.

### The Operation in Plain Language

Shor's algorithm converts prime factorization into a different problem: finding the period of a mathematical function. A quantum computer can find that period exponentially faster than a classical machine, because it can explore all possible periods simultaneously through superposition, then use quantum interference to amplify the correct answer. This lab makes that interference visible in a probability histogram.

### Instructions

::::{tab-set}
````{tab-item} Step 1: Build the Circuit
In IBM Quantum Composer or Quirk, create a 7-qubit circuit:
- **4 input qubits** — the register that holds the period-finding state
- **3 work qubits** — sized for f(x) = 2^x mod 15

Apply Hadamard gates to all 4 input qubits. This creates equal superposition of all 16 states (|0⟩ through |15⟩) simultaneously.
````
````{tab-item} Step 2: Modular Exponentiation
Apply controlled operations implementing f(x) = 2^x mod 15 to the work register. Use the pre-built template in IBM Composer (search "Modular Exponentiation, N=15, a=2") or the corresponding block in Quirk.

After this step, the work register contains the values of 2^x mod 15 for all 16 superposed input states — simultaneously.
````
````{tab-item} Step 3: Quantum Fourier Transform
Apply the Quantum Fourier Transform (QFT) to the input register. This is the step that makes quantum interference do its work. The QFT amplifies the amplitudes at multiples of 1024/r (where r is the period) and suppresses all others.

Available as a block in IBM Composer. In Quirk, build it from H gates, controlled-phase rotations, and SWAP gates.
````
````{tab-item} Step 4: Measure and Interpret
Measure the input register. Run 1,000 shots. Observe the histogram.

For f(x) = 2^x mod 15, the period is r = 4. You should see probability concentrated at 0, 256, 512, and 768 — multiples of 1024/4.

From r = 4, derive the factors: gcd(2^2 - 1, 15) = gcd(3, 15) = 3; gcd(2^2 + 1, 15) = gcd(5, 15) = 5. You have factored 15 = 3 × 5 using quantum interference.
````
````{tab-item} Step 5: Scale Reflection
RSA-2048 uses 617-digit numbers. Your circuit used 7 qubits for 15. Running Shor's on RSA-2048 requires an estimated 4,000–10,000 *logical* qubits, each requiring ~1,000 physical qubits for error correction — 4–10 million physical qubits total. Today's best gate-model machines have ~1,000 noisy physical qubits.

The mathematics works. The engineering gap is real, active, and narrowing.
````
`````

### Deliverable

Write a **400-word explanation** for a non-technical board member:
1. What you observed in the simulation — what the histogram showed and what it means
2. Why quantum interference caused the correct period to appear and incorrect ones to vanish
3. Why this same mechanism — scaled up — breaks RSA encryption in hours
4. One specific recommendation the board should authorize as a result

---

## Lab 5B (Applied): Optimizing Your PQC Migration with D-Wave Leap

**Duration:** 60–75 minutes
**Tools:** D-Wave Leap — [cloud.dwavesys.com](https://cloud.dwavesys.com) (free developer account)
**Deliverable:** Migration prioritization output + 300-word CISO memo

### Why This Lab

This lab inverts the security narrative in a way that is unique to this course. Lab 5A showed you the *threat* — a gate-model quantum computer running Shor's algorithm. Lab 5B uses the *other* quantum paradigm — D-Wave's quantum annealer — to help solve the *response*. The PQC migration prioritization problem is a combinatorial optimization problem. Given limited budget, limited migration team bandwidth, and a set of cryptographic assets with different risk levels (from your STRIDE analysis) and different migration costs, which assets should you migrate first to minimize your HNDL exposure?

This is a QUBO problem. And the same FAU Advantage2 system used in Chapter 6 for manufacturing scheduling and logistics routing can be used here to find the optimal sequencing of your PQC migration.

<a href="https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch05-lab-migration-optimizer.ipynb" target="_blank">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="margin-bottom: 1rem;"/>
</a>

### The Problem: Migration Portfolio Optimization

You are the CISO of a regional bank. Your cryptographic inventory (Phase 1 of your crypto-agility program) has identified 8 asset categories requiring migration. You have a migration team with capacity to handle 3 asset categories per quarter. Your goal: sequence the migration to minimize total HNDL exposure given the constraints.

| Asset | STRIDE Priority | Mosca Deficit (yrs) | Migration Cost (team-weeks) | Data Lifetime (yrs) |
|---|---|---|---|---|
| Customer TLS endpoints | Critical (I) | −2.1 | 4 | 8 |
| Code signing certificates | Critical (S) | −1.8 | 2 | 5 |
| Kerberos domain controllers | Critical (E) | −0.9 | 6 | N/A |
| SWIFT gateway RSA keys | Critical (I) | −3.2 | 8 | 12 |
| Email signing (DKIM) | High (S) | +0.4 | 1 | 2 |
| VPN gateway certificates | High (I) | +0.8 | 3 | 6 |
| Internal API signing keys | High (S,E) | −0.5 | 2 | 4 |
| ATM firmware RSA keys | Critical (I) | −4.1 | 12 | 15 |

### Step 1: Formulate the QUBO

```python
import dimod
from dwave.system import LeapHybridSampler

# Binary variable x_i = 1 if asset i is in the first migration wave
# Objective: maximize total Mosca deficit reduction for selected assets
# (minimize negative: assets with larger deficits get higher weight)

assets = {
    'tls_endpoints':      {'stride_weight': 10, 'mosca_deficit': 2.1,  'cost': 4},
    'code_signing':       {'stride_weight': 10, 'mosca_deficit': 1.8,  'cost': 2},
    'kerberos_dc':        {'stride_weight': 10, 'mosca_deficit': 0.9,  'cost': 6},
    'swift_gateway':      {'stride_weight': 10, 'mosca_deficit': 3.2,  'cost': 8},
    'email_dkim':         {'stride_weight': 7,  'mosca_deficit': -0.4, 'cost': 1},
    'vpn_gateway':        {'stride_weight': 7,  'mosca_deficit': -0.8, 'cost': 3},
    'internal_api_keys':  {'stride_weight': 8,  'mosca_deficit': 0.5,  'cost': 2},
    'atm_firmware':       {'stride_weight': 10, 'mosca_deficit': 4.1,  'cost': 12},
}

# Capacity constraint: first migration wave ≤ 12 team-weeks
capacity = 12
lambda_capacity = 20  # penalty weight for exceeding capacity

Q = {}

# Objective: maximize (stride_weight × mosca_deficit) for selected assets
for asset, data in assets.items():
    score = -(data['stride_weight'] * max(data['mosca_deficit'], 0.1))
    Q[(asset, asset)] = score

# Constraint: total cost of selected assets ≤ capacity
# Penalty for exceeding: lambda * (sum(cost_i * x_i) - capacity)^2
asset_list = list(assets.keys())
costs = [assets[a]['cost'] for a in asset_list]

for i, ai in enumerate(asset_list):
    Q[(ai, ai)] = Q.get((ai, ai), 0) + lambda_capacity * costs[i] * (costs[i] - 2 * capacity)
    for j, aj in enumerate(asset_list):
        if j > i:
            Q[(ai, aj)] = Q.get((ai, aj), 0) + 2 * lambda_capacity * costs[i] * costs[j]

# Submit to D-Wave Leap Hybrid Solver
sampler = LeapHybridSampler()
sampleset = sampler.sample_qubo(Q, label='PQC Migration Wave 1 Optimizer', time_limit=10)

# Extract results
best = sampleset.first
wave_1 = [asset for asset, selected in best.sample.items() if selected == 1]
total_cost = sum(assets[a]['cost'] for a in wave_1)
total_score = sum(assets[a]['stride_weight'] * max(assets[a]['mosca_deficit'], 0.1)
                  for a in wave_1)

print("Wave 1 Migration Priorities:")
for asset in wave_1:
    d = assets[asset]
    print(f"  {asset:25} | STRIDE weight: {d['stride_weight']} | "
          f"Mosca deficit: {d['mosca_deficit']:+.1f} yrs | Cost: {d['cost']} wks")

print(f"\nTotal team-weeks: {total_cost} / {capacity}")
print(f"Risk reduction score: {total_score:.1f}")
print(f"QPU timing: {sampleset.info.get('timing', {})}")
```

### Step 2: Run and Interpret

Submit to Leap. Record:
- Which assets the solver selected for Wave 1
- Total team-weeks consumed vs. capacity constraint
- Verify: were all Critical-priority Mosca-deficit assets prioritized?
- Compare to a simple classical greedy heuristic: rank by deficit, add until capacity filled. Does D-Wave find a better combination?

### Step 3: Experiment

- Add an asset with a very high cost but extreme Mosca deficit (e.g., ATM firmware at 12 weeks, deficit 4.1 years). How does the solver handle the capacity tradeoff?
- Change the capacity to 8 team-weeks. Which assets are deprioritized first?
- Adjust the STRIDE weights: set Elevation of Privilege to 15 (reflecting that a Kerberos compromise would affect every user in the organization). Does the selection change?

### Deliverable

Write a **300-word CISO memo** to the board's audit committee:
1. Which assets the solver selected for Wave 1, and why the prioritization is defensible in STRIDE and Mosca terms
2. What capacity constraint drove the hardest tradeoff, and how you would present that tradeoff to a non-technical committee
3. How this quantum-optimized migration sequencing approach scales to an enterprise with hundreds of cryptographic assets

---

## Lab 5C (Optional Advanced): The PQC Key Generation Lab

**Duration:** ~75 minutes
**Tools:** Python 3.9+, `liboqs-python` (Open Quantum Safe project)
**Platform:** [Google Colab](https://colab.research.google.com) — no local install required

<a href="https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch05-lab-pqc-keygen.ipynb" target="_blank">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="margin-bottom: 1rem;"/>
</a>

### Why This Lab

The NIST PQC standards are not theoretical constructs. They are implemented, tested, and production-deployable today. The Open Quantum Safe project's `liboqs` library provides the reference implementations — the same codebase used in Cloudflare, AWS, and Google's experimental PQC deployments. This lab moves from standards to working code: generating real ML-KEM keypairs, encrypting with post-quantum key exchange, signing with ML-DSA, and running a hybrid TLS handshake simulation that executes both classical and PQC cryptography simultaneously.

### Core Implementation

```python
import oqs, time, os

# Part 1: ML-KEM Key Encapsulation
with oqs.KeyEncapsulation('ML-KEM-768') as kem:
    public_key = kem.generate_keypair()
    ciphertext, shared_secret_sender = kem.encap_secret(public_key)
    shared_secret_recipient = kem.decap_secret(ciphertext)
    assert shared_secret_sender == shared_secret_recipient
    print(f"✅ ML-KEM-768 key exchange successful")
    print(f"   Public key: {len(public_key):,} bytes  |  Ciphertext: {len(ciphertext):,} bytes")

# Part 2: ML-DSA Digital Signatures
message = b"Board resolution: authorize PQC migration program — $340M over 4 years."
with oqs.Signature('ML-DSA-65') as signer:
    public_key = signer.generate_keypair()
    signature = signer.sign(message)
    valid = signer.verify(message, signature, public_key)
    tampered = signer.verify(message + b"[amended]", signature, public_key)
    print(f"✅ Signature valid: {valid}")
    print(f"🚨 Tampered message signature valid: {tampered}")  # Expected: False

# Part 3: Performance benchmark vs. classical RSA
# (Full implementation in Colab notebook — compares key generation,
# encapsulation, and signature times for RSA-2048 vs. ML-KEM-768 / ML-DSA-65)
```

### Deliverable

1. **Working notebook** with all three parts completed and output captured
2. **Performance comparison table** — ML-KEM and ML-DSA timing vs. RSA-2048 baseline
3. **500-word CISO briefing:** If you were presenting this lab's outputs to your organization's CISO as evidence that PQC is production-ready, what would you say? Address the performance overhead, which STRIDE categories are now addressed by each algorithm, and what the immediate next organizational step should be

---

## Discussion Guidelines

**Post a substantive response (minimum 300 words) citing at least two sources. Reply meaningfully to TWO peers.**

### Discussion Prompt

You are the CISO of a mid-size regional bank (\$15 billion in assets, 1,200 employees, operations in three states). The board has asked for a 15-minute quantum security briefing at the next quarterly meeting.

Prepare your briefing outline addressing:

1. **Your STRIDE analysis** — which of the six threat categories are highest priority for a regional bank, and why? What does your cryptographic architecture look like today, and what is each layer's quantum exposure?

2. **Your Mosca calculation** — given bank customer data requiring 7–10 years of confidentiality and a PQC migration of approximately 4–6 years, what is your Mosca position?

3. **The narrative that makes it real** — boards respond to stories. Which STRIDE scenario do you open with, and how do you describe a Harvest Now, Decrypt Later attack to an audience of non-technical executives without losing their confidence that you have this under control?

4. **The single ask** — what do you ask the board to authorize today, and what do you promise to deliver in return?

**Peer response guidelines:** Challenge one assumption in their STRIDE prioritization, propose an alternative Mosca calculation using different data lifetime assumptions, or extend their analysis with a regulatory angle they did not address.

---

## Glossary

```{glossary}
Post-Quantum Cryptography (PQC)
  Cryptographic algorithms designed to be secure against both classical and quantum computer attacks. NIST finalized the first three PQC standards in 2024: ML-KEM, ML-DSA, and SLH-DSA.
Shor's Algorithm
  A quantum algorithm published by Peter Shor in 1994 that factors large integers in polynomial time on a fault-tolerant gate-model quantum computer, breaking RSA and ECC encryption. Requires gate-model hardware — does not run on quantum annealers such as the D-Wave Advantage2.
Gate-Model Quantum Computer
  A quantum computing architecture (IBM, Google, IonQ, Quantinuum) that builds computation from sequences of quantum logic gates. General-purpose and capable of running Shor's algorithm on a future fault-tolerant device. The cryptographic threat paradigm.
Quantum Annealer
  A quantum computing architecture (D-Wave Advantage2) purpose-built for combinatorial optimization. Uses quantum tunneling to find low-energy solutions. Cannot run Shor's algorithm and is not the cryptographic threat vector — but can be used to optimize the PQC migration response (Lab 5B).
STRIDE
  A structured threat modeling framework categorizing security threats as Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, and Elevation of Privilege. Applied in this chapter to map quantum-era cryptographic threats to the governance vocabulary that CISOs, audit committees, and regulators speak.
Harvest Now, Decrypt Later (HNDL)
  An attack strategy in which adversaries collect and store encrypted data today with the intention of decrypting it when a fault-tolerant gate-model quantum computer becomes available. Makes the quantum cryptographic threat operationally present today, not merely future.
Mosca Inequality
  The inequality formulated by Michele Mosca: if the data lifetime plus the migration time exceeds the time until Q-Day, the organization is already in deficit. The primary tool for calculating migration urgency with precision.
Q-Day
  The anticipated date when a fault-tolerant gate-model quantum computer capable of running Shor's algorithm at RSA scale becomes operational. Most analyst estimates cluster in the 2030–2035 window.
ML-KEM (Module Lattice Key Encapsulation Mechanism)
  The primary NIST PQC standard for key exchange. Formerly CRYSTALS-Kyber. Based on the Learning With Errors lattice problem. Replaces RSA and ECC in TLS key exchange. Addresses the Information Disclosure STRIDE category.
ML-DSA (Module Lattice Digital Signature Algorithm)
  The primary NIST PQC standard for digital signatures. Formerly CRYSTALS-Dilithium. Replaces ECDSA in code signing, PKI, and identity infrastructure. Addresses Spoofing, Tampering, Repudiation, and Elevation of Privilege STRIDE categories.
SLH-DSA (Stateless Hash-Based Digital Signature)
  A NIST PQC standard for digital signatures based on hash functions rather than lattice mathematics. Formerly SPHINCS+. Provides algorithmic diversity as a hedge against future lattice attacks. Best suited for root certificates and long-lived archive authentication.
Lattice Cryptography
  A family of cryptographic schemes based on mathematical problems in high-dimensional lattice structures. No known quantum algorithm — including Shor's — provides a meaningful speedup for core lattice problems such as Learning With Errors.
Crypto-Agility
  The engineering discipline of building cryptographic systems with abstraction layers that allow algorithms to be replaced without rebuilding the entire system. The organizational capability that determines whether a PQC migration takes 18 months or 7 years.
Hybrid Cryptography
  A deployment strategy running both classical and post-quantum cryptographic algorithms simultaneously for the same operation. Provides quantum resistance for new traffic immediately while legacy systems complete migration.
CNSA 2.0
  NSA's Commercial National Security Algorithm Suite 2.0 (2022), mandating the transition of U.S. national security systems to PQC by 2030–2035 depending on system type.
Open Quantum Safe (OQS)
  An open-source project providing reference implementations of NIST PQC algorithms via the liboqs library. The same codebase used in experimental PQC deployments at Cloudflare, AWS, and Google.
```

---

## Going Deeper (Optional): Shor's Algorithm and the Mosca Inequality Formalized

*This section is for readers with a STEM or cybersecurity engineering background. Not required for course assessments.*

### How Shor's Algorithm Breaks RSA

RSA encryption's security rests on a simple asymmetry: multiplying two large primes $p$ and $q$ is fast, but factoring their product $N = p \cdot q$ back into $p$ and $q$ is computationally infeasible for classical computers when $N$ is 2,048+ bits. The best classical factoring algorithm (General Number Field Sieve) runs in sub-exponential time:

$$O\!\left(\exp\!\left(c \cdot (\ln N)^{1/3} (\ln \ln N)^{2/3}\right)\right)$$

For a 2,048-bit key, this is effectively intractable — approximately $10^{34}$ operations on a classical computer.

Shor's algorithm replaces factoring with **period finding** in a modular arithmetic function $f(x) = a^x \bmod N$, exploiting the fact that this function is periodic with period $r$ where $r$ divides $\phi(N) = (p-1)(q-1)$. The algorithm uses the **Quantum Fourier Transform (QFT)** — a quantum circuit implementation of the discrete Fourier transform — to find $r$ in polynomial time $O((\log N)^3)$. Once $r$ is known, the factors $p$ and $q$ are recovered with high probability via:

$$\gcd(a^{r/2} \pm 1, N) \in \{p, q\}$$

The exponential speedup comes entirely from the QFT's ability to extract periodicity from a superposition of $2^n$ function evaluations simultaneously. A fault-tolerant quantum computer with approximately 4,000 logical qubits (translating to millions of physical qubits with current error correction overhead) could factor a 2,048-bit RSA key in hours.

### The Mosca Inequality: Formal Statement

The Mosca Inequality frames the urgency of PQC migration as a sum of three time variables:

$$x + y > z \implies \text{act now}$$

Where:
- $x$ = **shelf life** of data that must remain confidential (years from now)
- $y$ = **migration time** to deploy post-quantum cryptography across your infrastructure (years)
- $z$ = **threat timeline** — the estimated years until a cryptographically relevant quantum computer exists (current estimates: 10–15 years, per NIST and NSA)

If $x + y > z$, your data will be harvested before you finish migrating — even if you start today. For a hospital with 30-year patient privacy obligations ($x = 30$) and a 5-year IT migration cycle ($y = 5$), the sum is 35 — well above any credible $z$ estimate. The hospital is already late.

### NIST PQC Algorithms: Mathematical Foundations

The three standardized NIST PQC algorithms are built on mathematical problems believed to be hard for quantum computers:

| Algorithm | Security Basis | Problem | Key Operation |
|-----------|---------------|---------|---------------|
| **ML-KEM** (Kyber) | Module Learning With Errors (MLWE) | Find short vectors in a lattice | Key encapsulation |
| **ML-DSA** (Dilithium) | Module Learning With Errors | Lattice short vector problem | Digital signatures |
| **SLH-DSA** (SPHINCS+) | Hash function security | One-way function preimage resistance | Digital signatures |

The Lattice problems (MLWE) are believed hard for quantum computers because the best known quantum algorithms for lattice problems (including quantum-accelerated sieve algorithms) provide only modest speedups — insufficient to break appropriately sized keys. SPHINCS+ is the most conservative choice: its security depends only on the cryptographic hash function being one-way, a property that survives Grover's algorithm when key sizes are doubled.

---

## Leader's Takeaway

::::{admonition} The Leader's Takeaway
:class: important

Two paradigms appear in this chapter, and they play opposite roles in the security story. The gate-model quantum computer — IBM, Google, IonQ — is the threat. Running Shor's algorithm at scale, it dissolves the cryptographic foundation of the modern internet. The quantum annealer — FAU's D-Wave Advantage2, the machine you used in Lab 5B — is part of the response. It cannot run Shor's algorithm. What it can do is solve the optimization problem of sequencing your migration, finding the combination of cryptographic assets to prioritize in each wave given your STRIDE risk weights, your Mosca deficits, and your team's capacity.

That inversion — using quantum computing to respond to the quantum cryptographic threat — is the most sophisticated version of the argument for quantum readiness. You are not just preparing to defend against quantum computers. You are using them to sharpen your own organizational response.

The rest of this chapter's toolkit is equally practical. STRIDE gives you the governance vocabulary to translate Shor's algorithm into the language of audit committees and regulators. The Mosca Inequality gives you the calculation to determine whether you are already late. The NIST PQC standards give you the specific algorithms — ML-KEM, ML-DSA, SLH-DSA — that replace the ones being retired. Crypto-agility gives you the architectural discipline to make migration tractable rather than catastrophic.

What none of these tools supply is the decision to begin. The organizations that started PQC migration programs in 2020 and 2021 are finishing now. The window for an unhurried, well-resourced migration is closing. The organizations that will face the scenario in this chapter's opening — a board meeting in 2031, an adversary with decrypted plaintext, a CISO explaining what we knew and when we knew it — are the ones that are reading this chapter and deciding to act next quarter.

Act this quarter.
::::

---

## Cross-References

- **See {ref}`ch-01-why-quantum-why-now`** for the FAU/D-Wave Advantage2 context and the gate-model vs. annealing paradigm distinction introduced in Chapter 1.
- **See {ref}`ch-04-hardware-race`** for the technical architecture of gate-model quantum computers and why the fault-tolerance gap narrows the Q-Day estimate.
- **See {ref}`ch-06-optimization-goldmine`** for the D-Wave Ocean SDK and Stride hybrid solver used in Lab 5B — the same QUBO formulation skills applied here to migration optimization.
- **See {ref}`ch-09-quantum-ready-enterprise`** for the full enterprise quantum readiness framework, of which PQC migration is one pillar, and the governance structures that sustain a multi-year migration program through leadership transitions and competing priorities.
