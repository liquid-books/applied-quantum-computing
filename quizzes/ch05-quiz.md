# Chapter 5 Quiz: The Cryptocalypse — Y2Q and the Security Imperative

*These exercises are for self-assessment and instructor use. This file is NOT included in the book TOC.*

---

## Exercise 1: The Mosca Inequality — Applied Analysis

**Scenario:** A regional hospital network holds electronic health records (EHRs) for 2.3 million patients. Under HIPAA, these records must remain confidential indefinitely, but the system architect conservatively estimates the EHR system will be replaced in 15 years. The hospital's IT team estimates a full PQC migration of their infrastructure would take 6 years given existing legacy systems and limited security staff. Current consensus estimates for Q-Day range from 2030 to 2035.

**Question:**

(a) Apply the Mosca Inequality to classify this hospital's risk posture using a conservative Q-Day estimate of 2035. Is the hospital in deficit or surplus? Show your reasoning.

(b) Apply the same analysis using an aggressive Q-Day estimate of 2030. How does the classification change?

(c) The hospital's CFO says: "We have six years before we need to worry — let's reassess in 2028." Identify the flaw in this reasoning using the Mosca Inequality framework.

(d) What is the **one action** you would recommend the hospital take in the next 90 days, and why?

---

### Answer Key — Exercise 1

**(a) Conservative analysis (Q-Day = 2035, ~11 years from 2024):**

- Data lifetime (Z): 15 years (hospital's operational planning horizon)
- Migration time (Y): 6 years
- Y + Z = 21 years
- Time to Q-Day (X) = 11 years (assuming 2035)
- Y + Z (21) > X (11): **The hospital is in significant deficit.**

Even with the most conservative Q-Day estimate, the sum of migration time and data lifetime exceeds the time available. The hospital's EHR data that will be created in 2026 must remain confidential until at least 2041 — well past any plausible Q-Day estimate.

**(b) Aggressive analysis (Q-Day = 2030, ~6 years from 2024):**

- Time to Q-Day (X) = 6 years
- Y (migration time) = 6 years alone already equals X
- Z (15 years data lifetime) makes the deficit even more severe
- The hospital cannot complete its migration before Q-Day even if it started today and the migration took exactly as long as estimated — because the data lifetime extends well past Q-Day regardless.

**Classification: CRITICAL RED under both scenarios.**

**(c) The 2028 reassessment fallacy:**

The CFO's reasoning assumes the migration clock starts when Q-Day "arrives" — but the migration clock starts when the migration *begins*. If the hospital waits until 2028 to start a 6-year migration, completion is 2034. Under the aggressive estimate (Q-Day = 2030), the hospital would miss Q-Day by 4 years. More critically, Harvest Now, Decrypt Later means the data collected *today* (2024) will be decryptable at Q-Day — waiting until 2028 to start does not protect 2024–2028 data.

**(d) Recommended 90-day action:**

Commission a cryptographic inventory — a systematic catalog of every certificate, key, TLS endpoint, encrypted data store, and cryptographic primitive in the hospital's environment. Cost: typically \$200K–\$500K for a hospital of this size. Output: a Mosca-classified asset map showing RED/YELLOW/GREEN status for every cryptographic asset. This is the prerequisite for everything else and cannot be skipped.

---

## Exercise 2: Shor's Algorithm — Conceptual Explanation

**Question:**

You are presenting to a board of directors who have no technical background. In approximately 200 words, explain:

(a) Why RSA encryption is considered secure today
(b) What Shor's algorithm does, without using any mathematical notation
(c) Why this matters *now*, even though fault-tolerant quantum computers don't yet exist

Your explanation should be accessible to a non-technical audience while being technically accurate.

---

### Answer Key — Exercise 2

**Model answer (200 words):**

"Today's internet encryption — the kind protecting your online banking, medical records, and contracts — works like a padlock that can only be opened by someone who knows two secret numbers multiplied together. Finding those two numbers by trial and error would take a classical computer longer than the age of the universe. So in practice, it's unbreakable.

Shor's algorithm is a procedure for quantum computers that sidesteps the trial-and-error approach entirely. Instead of trying combinations one at a time, it uses quantum physics to explore all possibilities simultaneously and then uses a phenomenon called interference — similar to how noise-canceling headphones work — to zero in on the correct answer. The math that would take classical computers billions of years takes a powerful enough quantum computer a few hours.

Why does this matter now? Because adversaries don't need the quantum computer today to *use* the attack today. They are collecting your encrypted data right now and storing it. When the quantum computer arrives — and most experts believe that's within the next 10–15 years — they'll decrypt everything they've collected. The threat isn't in the future. The collection is happening now."

**Grading criteria:**
- Padlock/prime number analogy or equivalent: 25%
- Quantum interference explained without equations: 25%
- Harvest Now, Decrypt Later dimension addressed: 25%
- Tone appropriate for non-technical board: 25%

---

## Exercise 3: NIST PQC Standards — Decision Matrix

**Scenario:** A financial services firm is upgrading three systems:

1. **System A:** Internet-facing customer portal using HTTPS/TLS for all user connections (high volume: 50 million connections per day)
2. **System B:** Code-signing infrastructure for authenticating software releases to 3 million enterprise clients
3. **System C:** Root certificate authority used to sign 10-year certificates for internal PKI — the authority's own certificate must remain trusted for 20+ years

**Question:**

For each system, recommend the most appropriate NIST PQC algorithm (ML-KEM, ML-DSA, or SLH-DSA) and justify your choice. Specifically address:

(a) Which algorithm should each system adopt?
(b) Why is that algorithm the best fit (consider: performance requirements, data lifetime, algorithmic diversity needs)?
(c) For System A, should the firm deploy pure ML-KEM or hybrid ML-KEM + classical? Justify your answer.

---

### Answer Key — Exercise 3

**(a) Recommendations:**

- **System A (Customer Portal / TLS):** ML-KEM for key encapsulation
- **System B (Code Signing):** ML-DSA for digital signatures
- **System C (Root CA, 20-year certificates):** SLH-DSA for root certificate signing

**(b) Justifications:**

**System A — ML-KEM:** TLS key exchange requires a Key Encapsulation Mechanism (KEM), not a signature scheme. ML-KEM is the NIST standard specifically for this purpose. At 50 million connections per day, performance matters — ML-KEM has minimal latency overhead (< 2% compared to RSA) and is already deployed at scale by Google and Cloudflare. The data lifetime for TLS session keys is short (hours), making the Mosca risk manageable even without immediate migration — but Harvest Now, Decrypt Later means the content of those sessions could be at risk, making migration urgent regardless.

**System B — ML-DSA:** Code signing requires digital signatures, not key exchange. ML-DSA is the primary NIST PQC signature standard — fast, compact signatures, and well-suited for high-frequency operations like signing build artifacts in a CI/CD pipeline. If a quantum attacker could forge code signatures, they could distribute malicious software that appears authentically signed — a critical supply chain risk.

**System C — SLH-DSA:** The 20-year certificate lifetime is the deciding factor. A root CA certificate signed with ML-DSA is secure today — but if a novel attack on lattice mathematics is discovered in Year 15, the root CA's trustworthiness is retroactively compromised, affecting all certificates it signed. SLH-DSA's hash-based construction provides independence from lattice mathematics — it is a hedge against future cryptanalytic developments. For the highest-assurance, longest-lived certificate in the PKI hierarchy, algorithmic diversity is worth the larger signature size.

**(c) System A — Hybrid vs. Pure ML-KEM:**

**Recommendation: Hybrid ML-KEM + ECDH.** Rationale: At scale, some client systems may not yet support ML-KEM. Pure ML-KEM would fail for those connections. Hybrid configuration (simultaneously running ML-KEM and ECDH) ensures quantum resistance for the connection if either algorithm succeeds, while maintaining backward compatibility. The performance overhead of hybrid is minimal. As ML-KEM client support reaches near-universal adoption, the classical component can be deprecated. NIST and leading cloud providers explicitly recommend hybrid deployment as the migration strategy for TLS.

---

## Exercise 4: Crypto-Agility — Strategic Assessment

**Scenario:** You are the Chief Information Security Officer (CISO) of a global logistics company. Your CTO has presented two architectural proposals for the company's next-generation digital freight platform:

**Option A:** A high-performance, monolithic platform with cryptographic algorithms directly integrated into the core libraries for maximum performance. Migration to new algorithms would require "minor refactoring" but the CTO estimates "it's not a big deal."

**Option B:** A service-oriented platform where all cryptographic operations are handled through a dedicated Cryptography Service with a standardized API. Changing algorithms requires updating the Cryptography Service only — the rest of the platform is agnostic. Initial build cost is approximately 15% higher than Option A.

**Question:**

(a) Define crypto-agility in plain language and explain why it matters for this decision.

(b) The CTO says "minor refactoring" for Option A. What is the CISO's counter-argument? Draw on the real-world examples from this chapter.

(c) Quantify the cost difference between the two options over a 10-year horizon, including PQC migration costs. Use the following assumptions:
   - Option A migration cost (without crypto-agility): 8x the initial platform cost
   - Option B migration cost (with crypto-agility): 0.5x the initial platform cost
   - Initial platform cost: \$12 million for both options (Option B costs 15% more: \$13.8M)
   
(d) Recommend Option A or B with a justification a CFO would find persuasive.

---

### Answer Key — Exercise 4

**(a) Crypto-agility definition:**

Crypto-agility is the engineering discipline of building cryptographic infrastructure so that algorithms can be replaced without requiring system-wide redesign. In practical terms: abstracting cryptographic operations behind APIs, avoiding hard-coded algorithm dependencies, and treating cryptographic primitives as interchangeable components rather than embedded implementation details. The goal is to reduce the cost and time of migrating to new algorithms when cryptographic standards change — which they do, and which they will again as post-quantum cryptography itself evolves.

**(b) CISO counter-argument:**

"Minor refactoring" consistently proves to be neither minor nor just refactoring. The global bank case study in this chapter spent six months on inventory alone — and discovered 89 embedded system keys nobody knew existed. These were not complex systems; they were SWIFT gateways that had been running unchanged for 11 years. The "minor refactoring" framing assumes you know where every cryptographic dependency is. You don't. You will discover them during the migration — in vendor black boxes, in embedded firmware, in decade-old code written by engineers who have since left the company. The refactoring estimate for Option A is almost certainly understated by a factor of 5–10x.

**(c) 10-year cost comparison:**

| | Option A | Option B |
|--|--|--|
| Initial build cost | \$12M | \$13.8M (+15%) |
| PQC migration cost | \$12M × 8 = \$96M | \$13.8M × 0.5 = \$6.9M |
| **Total 10-year cost** | **\$108M** | **\$20.7M** |
| **Cost difference** | | **Option B saves \$87.3M** |

The 15% initial premium for crypto-agility (Option B) returns \$87M in avoided migration costs over the platform's life. This does not include the cost of regulatory penalties, audit findings, or the extended Harvest Now, Decrypt Later exposure during a longer Option A migration.

**(d) CFO recommendation:**

"Option B. The 15% initial cost premium — \$1.8 million — is insurance against an \$87 million migration bill we will otherwise pay in Years 5–8. The cryptographic standards our platform will need to support are changing now: NIST finalized new standards in 2024, regulators are mandating migration, and our cyber insurer will ask about our PQC posture at our next renewal. Option A builds debt we will be forced to repay at the worst possible time — when Q-Day is imminent, our competitors are already migrated, and our regulators are asking questions. Option B is the fiscally responsible choice."
