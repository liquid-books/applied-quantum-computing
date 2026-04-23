---
title: "Chapter 9: The Quantum-Ready Enterprise — Strategy, Talent, and Timing"
subtitle: "The Organizations That Win the Quantum Decade Are Building Their Reflexes Right Now"
short_title: "Ch. 9: The Quantum-Ready Enterprise"
description: "Quantum readiness is not a technology project — it is a strategy, talent, and governance project. This capstone chapter synthesizes the entire course into a dual-paradigm three-horizon roadmap, a talent architecture for building quantum-literate organizations, a governance framework covering ethics and regulation, and a one-page quantum investment thesis every leader can defend. The chapter covers SC26 as the annual quantum strategy pulse, FAU's Advantage2 as the on-ramp for Horizon 1 optimization, and Lab 9B: formulating your own organization's optimization problem as a QUBO on D-Wave Leap."
label: ch-09-quantum-ready-enterprise
tags: [quantum strategy, quantum readiness, three-horizon, talent, governance, capstone, investment thesis, D-Wave, FAU Advantage2, SC26, QUBO, dual-use, export controls, ethics, organizational strategy, Centers of Excellence]
---

# Chapter 9: The Quantum-Ready Enterprise — Strategy, Talent, and Timing

:::{figure} ../images/ch09-explainer-infographic.png
:label: fig-ch09-explainer
:alt: Chapter 9 overview infographic showing the quantum-ready enterprise as a central hub connected to four spokes — Strategy, Talent, Governance, and Partnerships — each feeding into organizational readiness, with the dual-paradigm lens running through the center.
:width: 100%
:align: center

**The Quantum-Ready Enterprise at a Glance.** Quantum readiness is the intersection of strategy, talent, governance, and partnerships. This chapter builds a complete organizational framework anchored in the dual-paradigm lens that runs through this entire course: annealing hardware (FAU's Advantage2, D-Wave Leap) is accessible in Horizon 1 *today*; gate-model hardware provides the long-horizon advantage. The capstone deliverable — a one-page quantum investment thesis — integrates both paradigms, every chapter's tools, and a defense-ready plan for any C-suite.
:::

Eight chapters built your vocabulary. This chapter is where you use it.

You know the difference between a quantum annealer and a gate-model quantum computer — and you know which one is on FAU's campus, which one can run Shor's algorithm, and why that distinction governs every security, optimization, and simulation conversation in your organization. You know how Shor's algorithm dissolves RSA encryption, how QUBO formulation turns logistics and finance problems into quantum-solvable models, how VQE simulates molecular ground states, and how to tell genuine quantum advantage from quantum marketing.

What remains is the organizational question that all of those technical tools exist to serve: *What does your organization actually do about it?*

This chapter gives you a structured, specific, defensible answer — not a generic "watch the space" recommendation but a three-horizon roadmap split by paradigm, a talent architecture sequenced by organizational maturity, a governance framework built for boards and regulators, and a capstone deliverable that synthesizes every framework in this course into one page that a CFO, a board member, or an investment committee can evaluate.

SC26 — the International Conference for High Performance Computing, Networking, Storage and Analysis — will convene in Chicago in November 2026. Mehran Basiratmand, who designed this course, attended SC for close to a decade as FAU's CTO and watched quantum and HPC converge from inside the room. SC26 is the annual signal event where the frontier of quantum enterprise capability becomes visible. This chapter ends with you prepared to walk into SC26 — or any equivalent strategic moment — and know exactly where your organization stands, what it needs, and what argument to make for the resources to close the gap.

---

## Opening Scene: Three Companies, One Briefing

It is 1995. Three companies receive the same document. A consultant slides a presentation across the conference table. The title reads: *"The World Wide Web: Commercial Implications."*

The first company's CEO skims the summary, nods thoughtfully, and authorizes a study. Six months later, a report recommends a steering committee. The committee meets for two years. By 1999, a pilot exists. By 2001, the dot-com crash kills the initiative. They revisit in 2004 — five years behind their industry.

The second company's CIO assigns the topic to a task force. The task force is thorough. They produce a risk analysis: regulatory uncertainty, security vulnerabilities, unclear ROI. Their recommendation: monitor and revisit in eighteen months. They revisit in 1998, then again in 1999. By then, their competitors have online storefronts and they are explaining to the board why they do not.

The third company's CEO reads the briefing, hands it to an engineer on a Thursday afternoon, and says: *"Build something and report back in ninety days."* By 1996, they have a website. By 1998, an e-commerce pilot. By 2005, digital is their primary growth channel.

Same briefing. Same year. Three completely different outcomes — not because the technology was different, but because the *organizational reflexes* were different.

This chapter is about being the third company.

---

## The Single Idea

```{epigraph}
Quantum readiness is not a technology project. It is a strategy project, a talent project, and a governance project. The organizations that win the quantum decade will not necessarily have the deepest research budgets. They will have the clearest decision frameworks, the most strategically placed human capital, and the governance structures that let them move when the moment arrives. And they will already know, from the dual-paradigm lens in this course, that one part of that moment — quantum annealing for optimization — has already arrived.
```

---

## Part I: The Dual-Paradigm Three-Horizon Roadmap

The Three-Horizon Framework is the primary strategic tool for quantum readiness planning. But the version most organizations encounter is paradigm-blind — it treats "quantum computing" as a monolithic technology arriving at some future date and says little about what is available now.

This course has been insistent on the distinction between the two paradigms: gate-model quantum computers (IBM, Google, IonQ) and quantum annealers (D-Wave Advantage2, the hardware on FAU's campus). That distinction does not disappear at the strategy layer. It is the most important lens for a quantum readiness roadmap — because the two paradigms are on different timelines, serve different problem classes, and require different organizational preparation.

:::{figure} ../images/ch09-three-horizon-roadmap.png
:label: fig-ch09-three-horizons
:alt: Dual-paradigm three-horizon quantum strategy roadmap showing Horizon 1 with D-Wave annealing accessible now and gate-model awareness track, Horizon 2 with optimization pilots expanding and gate-model experimentation beginning, Horizon 3 with full quantum-classical integration across both paradigms.
:width: 100%
:align: center

**The Dual-Paradigm Three-Horizon Roadmap.** The most important insight this course adds to the standard three-horizon framework: you do not wait for Horizon 2 to use quantum computing for optimization. D-Wave annealing — the paradigm behind FAU's Advantage2 — is a Horizon 1 tool for organizations with optimization-heavy problems. Gate-model quantum computing is primarily a Horizon 2 and 3 play. Conflating the two produces a strategy that is either too conservative (by waiting for gate-model maturity) or too aggressive (by expecting gate-model performance from NISQ hardware).
:::

### Horizon 1 (Now — Years 0 to 2): Protect and Position

**The central question:** What do we need to secure right now, and where can we already act?

Horizon 1 is the most action-dense horizon. Two things are true simultaneously: the most urgent quantum risk (cryptographic exposure to Harvest Now, Decrypt Later) is already present, and the most accessible quantum opportunity (optimization via D-Wave annealing) is already deployable.

**Horizon 1, Annealing Paradigm — Act Now:**

For organizations with optimization-heavy operations — logistics routing, production scheduling, financial portfolio construction, workforce allocation — Horizon 1 is not a "wait and watch" horizon. The D-Wave Advantage2 that FAU hosts on its Boca Raton campus (and D-Wave's Leap cloud, which this course's labs have used throughout) is a production-grade optimization tool available today. The case studies in {ref}`ch-06-optimization-goldmine` are not forecasts. They are current deployments: BASF manufacturing scheduling, Mastercard fraud graph optimization, Verge Ag autonomous fleet routing.

The Horizon 1 question for the annealing paradigm is not "when will this be ready?" It is: "Which of our highest-value optimization problems can we formulate as a QUBO this quarter, run on D-Wave Leap, and benchmark against our classical baseline before the end of the fiscal year?" Lab 9B — the capstone D-Wave lab — is designed to answer exactly this question for your organization.

FAU's on-campus Advantage2 access is a unique Horizon 1 resource for this course's students. It is the same hardware class used in every enterprise deployment in Chapter 6, located at your own institution, connected to a D-Wave corporate partner whose headquarters has relocated to the Boca Raton Innovation Center. The on-ramp to Horizon 1 annealing capability is, for FAU students, shorter than at any comparable institution in the region.

**Horizon 1, Gate-Model Paradigm — Awareness and Security:**

Gate-model quantum computing is not a Horizon 1 production tool for most organizations. Its Horizon 1 role is preparation: building awareness, managing the cryptographic risk it will eventually create, and establishing the vendor relationships and pilot infrastructure that Horizon 2 requires.

The critical Horizon 1 gate-model action is PQC migration. The Mosca Inequality analysis from {ref}`ch-05-cryptocalypse-y2q` applies to gate-model hardware — specifically, to the fault-tolerant gate-model computer that will eventually run Shor's algorithm. The D-Wave annealer on FAU's campus cannot run Shor's. But the IBM, Google, and IonQ machines whose capabilities are improving each year are on a trajectory toward the hardware that will. PQC migration is a Horizon 1 obligation for every organization with long-lived sensitive data — not because the threat has arrived, but because the migration will take 5–10 years and the adversarial collection (Harvest Now, Decrypt Later) is already underway.

**Horizon 1 Action Checklist:**

::::{grid} 2

:::{card} 🔐 Cryptographic Inventory + PQC Migration Start
Map every cryptographic system. Run the Mosca Inequality for each data category. Begin PQC migration for Tier 1 (Critical) assets. Budget 3–5 years for full migration. Start this quarter.
:::

:::{card} ⚡ Annealing Pilot (if optimization-heavy)
Identify your organization's top optimization problem. Formulate it as a QUBO (Chapter 6 skills apply directly). Run it on D-Wave Leap. Benchmark against your classical baseline. This is the fastest path to a credible, internally funded Horizon 1 quantum result.
:::

:::{card} 📚 Quantum Literacy Program
Train every senior leader who makes technology investment decisions to the level of this course. Target: 3–5 Quantum-Literate Managers in Year 1. Cost: \$5,000–\$15,000 per person in structured programs, or the equivalent of this course.
:::

:::{card} 👁️ Monitoring Infrastructure
Establish a process for tracking quantum developments: NIST standards updates, hardware milestones, SC26 proceedings, competitor announcements. Assign ownership and a quarterly review cadence. SC26 (November annually) is the single most information-dense annual event for quantum enterprise strategy.
:::

:::{card} 🤝 Platform Access
Get accounts on IBM Quantum, AWS Braket, and D-Wave Leap. Not for production workloads — for familiarity. The organization that has never touched a quantum circuit is not ready to evaluate a quantum vendor pitch. The exploration cost is low. The ignorance cost is not.
:::

:::{card} 💰 Budget Envelope
Establish an annual quantum readiness budget. The mid-cap reference envelope: \$1–\$2M annually funds a Translator hire, consortium membership, two cloud platform subscriptions, PQC migration tooling, and one active pilot. This is Horizon 1. It is not a research budget. It is an organizational readiness investment.
:::

::::

---

### Horizon 2 (Years 2 to 5): Experiment and Partner

**The central question:** Where does quantum create measurable advantage for us, and who do we need to get there?

Horizon 2 is where the organization moves from observer and early deployer to systematic experimenter. The foundation built in Horizon 1 — cryptographic hygiene, literacy, platform access, and the annealing pilot — now becomes the launchpad for structured investment in both paradigms.

**Horizon 2, Annealing Paradigm:**

If the Horizon 1 annealing pilot produced measurable improvement (even modest — 2–3% in a routing or scheduling problem), Horizon 2 is where that pilot scales to production. This means: moving from D-Wave Leap cloud access to potentially direct on-site access or reserved capacity agreements, formalizing the QUBO formulation capability as an organizational competency (not a one-time experiment), and expanding the application portfolio from one problem to two or three.

The Volkswagen lesson from {ref}`ch-07-simulation-revolution` is the Horizon 2 template: the QUBO formulation language developed in the quantum pilot transfers to quantum-inspired classical solvers when hardware limitations constrain scale. The skill is the durable asset. The hardware is interchangeable.

**Horizon 2, Gate-Model Paradigm:**

Horizon 2 is when gate-model quantum computing enters serious organizational experimentation for most industries. By 2027–2029, IBM, Google, and IonQ hardware roadmaps converge on early fault-tolerant capabilities that are relevant to specific problem classes: quantum kernel methods for high-dimensional classification, early VQE for small molecular fragments in pharma and materials, and QAOA for optimization problems that exceed D-Wave's current problem size limits.

Horizon 2 gate-model activities: run 2–3 structured pilots with external partners (hyperscaler, academic lab, or native quantum startup); build the Quantum Translator capability described in Part II of this chapter; evaluate vendor claims using the five-question governance filter from {ref}`ch-08-quantum-ai-hybrid`; and establish board-level quantum reporting using the framework in Part III.

**Horizon 2 Action Table:**

```{list-table} Horizon 2 Action Plan
:header-rows: 1

* - Action
  - Owner
  - Success Criterion
  - Kill-Switch
* - Scale annealing pilot to production
  - Quantum Translator + operations lead
  - Measurable production improvement vs. classical baseline
  - No improvement after 12 months at production scale; revert to classical
* - Run 2 gate-model pilots in priority use cases
  - Quantum Translator + R&D sponsor
  - At least one pilot shows measurable improvement over optimized classical baseline
  - Neither pilot beats baseline after 18 months; redirect budget to annealing or PQC
* - Formalize one external partnership
  - Business development + Translator
  - Partnership agreement signed, joint working group active
  - No joint prototype after 12 months
* - Complete PQC migration for all Tier 1 assets
  - CISO + IT
  - All critical cryptographic endpoints migrated
  - Migration falls >12 months behind schedule; escalate to board
* - Institutionalize board quantum reporting
  - CIO/CISO + Translator
  - Board receives semi-annual quantum briefing
  - No board engagement after 4 quarters; escalate to CEO
```

---

### Horizon 3 (Years 5 to 10): Integrate and Lead

**The central question:** How does quantum become a source of sustained competitive advantage?

Horizon 3 is the harvest. Fault-tolerant gate-model hardware arrives. Quantum simulation becomes commercially relevant for pharma, materials, and chemistry. Quantum ML begins to demonstrate genuine advantage for specific high-dimensional classification and sampling problems. The organizations that built Horizons 1 and 2 correctly are positioned to move from experiment to production. The ones that did not are in the same position as the first two companies in the 1995 opening scene.

**Horizon 3 characteristics of the quantum-ready enterprise:**
- Annealing-based optimization is integrated into core operations (not a pilot, not a special project — the standard way the organization routes, schedules, and allocates)
- Gate-model quantum workflows are live for at least one strategic application: molecular simulation for pharma/materials, quantum kernel methods for high-dimensional classification, or quantum-native risk models for financial services
- The quantum talent pipeline is deep enough that it is self-sustaining — internal training, academic partnerships, and a recognizable employer brand in the quantum talent market
- PQC migration is complete; the organization is running forward-secure cryptographic infrastructure
- Board quantum reporting is a standard governance process, not a special briefing
- SC26 attendance (or equivalent) is part of the annual strategy calendar — the organization sends people to read the frontier, not to learn what the frontier is

```{admonition} The Non-Linearity Warning
:class: warning

Quantum payoffs are not linear with time or investment. Organizations that are "80% ready" in Horizon 2 may capture 20% of the available Horizon 3 advantage — because the remaining 20% of readiness (talent depth, proprietary quantum know-how, problem formulation IP) is what creates differentiation. The valley of disillusionment — when early pilots underperform initial expectations — is real and must be budgeted for explicitly. Organizations that have not pre-planned for this valley will kill programs at exactly the wrong moment: right before the hardware improvement that would have made the pilot work. Build the valley into the roadmap. Survive it deliberately.
```

---

## Part II: Talent and Organizational Design

### The Translator at the Center

Every organization that has successfully deployed AI at scale credits one kind of person. Not the researchers. Not the C-suite champion. The translator — the person who could explain gradient descent to the CFO *and* explain IRR constraints to the data scientists, and have both conversations be genuinely useful.

Quantum will be identical. The most important organizational decision any company makes in Horizon 1 is not which quantum platform to buy access to or which vendor to partner with. It is who becomes the quantum translator. The organizations that have their translator in place before they need them will run better pilots, make better vendor decisions, avoid more expensive mistakes, and communicate more effectively to boards and investors.

The translator is not the person you hire after you understand what you need. The translator is the person who helps you understand what you need.

:::{figure} ../images/ch09-talent-architecture.png
:label: fig-ch09-talent
:alt: Quantum talent architecture pyramid showing four roles — Quantum-Literate Managers at the base (train in Year 1), Quantum Translator in the center (hire first), Quantum Specialist at upper tier (Year 3+), and External Research Partners as a parallel track — with FAU Advantage2 and D-Wave ecosystem highlighted as a unique talent pipeline resource.
:width: 100%
:align: center

**The Quantum Talent Architecture.** The recommended hire sequence is clear: Translator first, Specialist third. The base of Quantum-Literate Managers (trained, not hired) is what makes the Translator's work land with the organization. FAU's Advantage2 partnership with D-Wave creates an unusual talent pipeline resource: graduates of this course have hands-on hardware experience that most corporate quantum programs do not yet offer.
:::

### The Four Roles

**Role 1: The Quantum-Literate Manager**

A business leader who understands enough quantum computing to make informed decisions — not a specialist, but someone who can evaluate vendor claims, assess pilot proposals, interpret progress reports, and ask the right questions when specialists use unfamiliar language. The target literacy level is this course. Every senior leader in technology, operations, finance, and R&D should achieve this level within Horizon 1.

*Signal:* Can they pass a 20-question quantum readiness assessment? Can they explain the difference between annealing and gate-model? Can they identify the three most relevant quantum use cases for their business unit?

**Role 2: The Quantum Translator**

The most important and most undervalued hire in quantum readiness. Sits at the intersection of quantum science and business strategy — genuinely fluent in both. Runs the quantum pilot program, evaluates vendor proposals, briefs the board, manages academic partner relationships, serves as the internal anchor for all quantum activity.

Most organizations need exactly one Translator to start. Hire them before Horizon 1 pilots begin — not after.

*Where to find them:* PhD physicists or quantum engineers who spent time in consulting or business development; MBA graduates from programs with quantum computing curricula; quantum startup alumni who have held both product and research roles; science policy professionals with quantum portfolios. FAU students who completed this course and Lab 9B have the kind of hands-on quantum hardware experience that makes them credible translator candidates.

*Cost:* \$180,000–\$280,000 total compensation in 2026 markets.

*Signal:* Give them a real business problem and a quantum vendor pitch deck. Ask for a one-page recommendation. If they can identify what is real, what is hype, what the business case requires, and what the technical risks are — they are your Translator.

**Role 3: The Quantum Specialist**

A quantum scientist or engineer with deep technical expertise in a specific domain: algorithms, error correction, quantum chemistry simulation, quantum cryptography. Appropriate only in late Horizon 2 or Horizon 3 — after pilots have validated that a specific technical area is genuinely strategic and requires depth beyond what the Translator can provide.

Hiring a Specialist too early is one of the most common expensive mistakes in quantum talent strategy. Without a Translator to bridge their work to business problems, a Specialist will spend their time on technically interesting but organizationally irrelevant problems.

*Cost:* \$250,000–\$500,000+ total compensation depending on specialization.

**Role 4: The External Research Partner**

Academic laboratories, national quantum research centers, and quantum consortia provide cutting-edge expertise without full-time hire costs. A structured university partnership costs \$50,000–\$200,000 per year and provides PhD-level access, early research visibility, and talent pipeline.

For FAU students: the FAU/D-Wave Advantage2 partnership is not only a hardware resource — it is a model for external research partnership. The same structure (institutional access to production-grade quantum hardware, faculty research programs, student internship pipelines) is what your organization should seek to build with a university partner in your region.

*The SC26 Connection:* Mehran's decade of attending SC created a network of relationships with HPC and quantum researchers at national labs and research universities that no corporate program could replicate by writing checks. Annual attendance at SC26 is how organizations build the research partner network that makes external partnerships productive rather than transactional. Send your Translator to SC26.

### Hiring Sequence by Horizon

```{list-table} Quantum Talent Sequence
:header-rows: 1

* - Horizon
  - First Priority
  - Second Priority
  - Third Priority
* - Horizon 1 (0–2 yr)
  - Train 3–5 Quantum-Literate Managers
  - Hire one Quantum Translator
  - Establish one External Research Partnership
* - Horizon 2 (2–5 yr)
  - Deepen Translator role; expand manager training to 10+
  - Add Specialist in validated use-case domain
  - Expand external partnerships to 2–3; attend SC26 annually
* - Horizon 3 (5–10 yr)
  - Build quantum team of 5–10 specialists across paradigms
  - Develop internal quantum training pipeline
  - Consider founding a quantum Center of Excellence
```

### Building a Quantum Center of Excellence

Organizations that reach Horizon 3 with sustained quantum investment often formalize their capability in a **Quantum Center of Excellence (QCoE)** — a dedicated organizational unit that owns quantum strategy, manages vendor relationships, runs the talent pipeline, and serves as the internal resource for all quantum-related business unit questions.

The QCoE model has precedents: the AI Centers of Excellence that became standard at major enterprises in the 2018–2022 period followed exactly this pattern. The organizations that built AI CoEs in 2018 captured disproportionate advantage in the 2020–2024 AI deployment wave. The organizations that built them in 2023 are still catching up.

A QCoE for quantum should include, at minimum: the Quantum Translator (Director level in Horizon 3), two to three Specialists in the organization's primary use-case domains, a dedicated research partnership manager, a governance and compliance function (covering dual-use risk and export controls), and a talent development program that trains the next generation of Quantum-Literate Managers from within the organization.

---

## Part III: Ethics, Governance, and the Regulatory Landscape

Quantum computing creates governance challenges that classical technology governance has not addressed. Two new risk categories — dual-use risk and export controls — require explicit organizational attention. Three regulatory landscapes — United States, European Union, and Asia-Pacific — are converging toward quantum-specific requirements with material consequences for non-compliance.

This governance layer is not academic. It is the legal and reputational environment in which every quantum investment decision is made.

:::{figure} ../images/ch09-governance-framework.png
:label: fig-ch09-governance
:alt: Quantum governance framework diagram showing four layers — Board, Executive Team, Quantum Working Group, Technical Teams — with dual-use risk flag, export controls checklist, and regulatory jurisdiction panel showing US CNSA/EAR, EU NIS2/Chips Act, and Asia-Pacific signals.
:width: 100%
:align: center

**The Quantum Governance Framework.** Quantum governance is not a separate governance structure — it is an extension of existing technology governance. The additions are: quantum-specific risk taxonomy (cryptographic exposure, dual-use risk, export controls), a Quantum Working Group with executive sponsorship, and a board-level reporting cadence in the language of risk and opportunity rather than technical specification.
:::

### Dual-Use Risk: The Hardest Governance Question

Quantum algorithms capable of breaking encryption can also be used defensively — to audit your own cryptographic vulnerabilities before adversaries exploit them — or offensively, to break cryptographic systems that others depend on. An organization that develops meaningful quantum cryptanalysis capability, even for purely internal defensive purposes, may find itself subject to dual-use technology regulations and, if the capability is ever misused, to significant legal and reputational exposure.

The governance principle: any quantum activity that touches cryptographic systems — vulnerability scanning, algorithm benchmarking, key recovery research — requires legal review before execution. This is not a technicality. The U.S. Department of Commerce, the EU's ENISA, and multiple national security agencies have explicitly identified quantum cryptography tools as dual-use. The consequences of misclassifying a quantum project as "purely internal" when it falls under dual-use regulations are not hypothetical.

**Ethics of cryptographic disruption:** An organization that achieves meaningful quantum cryptographic capability faces ethical obligations beyond legal compliance. The ability to break encryption that others rely on for privacy, financial security, or intellectual property is not a competitive advantage to be deployed silently — it is a capability that carries disclosure obligations, industry coordination responsibilities, and reputational risks that no financial model captures. The standard should be: if you discover a quantum vulnerability in widely used cryptographic infrastructure, you disclose it to the affected parties and to NIST, you do not exploit it. Build this standard into the quantum governance framework from the start.

### Export Controls: The International Partnership Trap

Quantum hardware, quantum software, and quantum technical expertise are subject to export control regulations that are expanding rapidly. The most relevant frameworks:

**United States — EAR and ITAR:** The Export Administration Regulations (EAR) and International Traffic in Arms Regulations (ITAR) both have quantum components. The Department of Commerce has identified quantum computing as a critical and emerging technology subject to enhanced export control scrutiny. Key quantum hardware (superconducting qubits, ion trap systems above certain specifications), quantum software with specific cryptographic applications, and technical expertise shared with certain foreign nationals may require export licenses.

**The practical consequence:** Any international quantum partnership — academic collaboration, technology licensing, joint research, cloud service provisioning to foreign entities — requires export control review before execution. The review is not burdensome in most cases. Failing to conduct it is a federal compliance risk that can result in penalties, debarment from government contracts, and reputational damage.

### The Three Regulatory Landscapes

`````{tab-set}
````{tab-item} United States
**CNSA 2.0:** NSA's Commercial National Security Algorithm Suite 2.0 mandates PQC migration in the federal supply chain by 2030–2035. Organizations with any federal contract exposure are implicitly on this timeline.

**NIST PQC Standards:** The three algorithms standardized in 2024 (ML-KEM, ML-DSA, SLH-DSA) are the legally operative PQC standards for federal agencies and their suppliers. Private sector adoption is strongly signaled but not yet mandatory for non-federal entities.

**SEC Cybersecurity Disclosure Rules:** Material quantum cryptographic exposure — particularly HNDL risk for companies holding long-lived sensitive data — may meet the disclosure threshold under SEC cybersecurity disclosure rules. Any publicly traded company should evaluate this with securities counsel.

**EAR / BIS Quantum Controls:** The Bureau of Industry and Security has added quantum computing capabilities to the emerging technology control list. International partnerships and technology transfers require EAR review.

**Key signal:** The U.S. is moving from guidance to requirements. CNSA 2.0 was guidance in 2022; it is becoming compliance in 2025–2030.
````
````{tab-item} European Union
**NIS2 Directive:** In force since October 2024. Covers energy, transport, health, water, digital infrastructure, financial markets, and public administration. Requires "state-of-the-art" cybersecurity, increasingly interpreted by ENISA to include a credible PQC migration roadmap. Non-compliance fines: up to €10M or 2% of global annual turnover.

**DORA (Digital Operational Resilience Act):** EU financial sector regulation that explicitly addresses quantum risk in ICT risk management requirements. Banks, insurance companies, and investment firms covered by DORA must demonstrate ICT resilience against "emerging and anticipated technology risks" — language that ENISA guidance has explicitly connected to quantum computing.

**EU Chips Act and Quantum Flagship:** The EU has designated quantum computing as a strategic technology under the EU Chips Act and committed €1B+ through the Quantum Flagship program. For organizations operating in the EU, this creates both regulatory signals (quantum capability may become a procurement criterion) and partnership opportunities (EU-funded research programs).

**GDPR Quantum Implications:** The GDPR's requirement to protect personal data using "appropriate technical measures" may, as Q-Day approaches, require PQC for any personal data with long-term processing or retention requirements.
````
````{tab-item} Asia-Pacific
**China:** Has designated quantum computing a national strategic priority under the 14th Five-Year Plan, with reported investment exceeding \$15B. China's National Cryptography Administration has published PQC migration guidance for state-owned enterprises. For organizations with operations or partnerships in China, both the PQC migration risk and the competitive intelligence implications of Chinese quantum investment are material governance considerations.

**Japan:** The Quantum Flagship program under the Ministry of Education, Culture, Sports, Science and Technology (MEXT) and the Quantum Innovation Initiative Consortium (Q-STAR) have structured Japan's enterprise quantum engagement. Japanese industrial partners (Toyota, NEC, Toshiba, Fujitsu) are active in both quantum hardware and quantum-inspired optimization — creating both partnership opportunities and competitive pressure.

**Australia:** Actively developing quantum export control frameworks aligned with the U.S. EAR. The Australia-U.S. Quantum Cooperation framework (2023) creates preferential conditions for quantum technology transfer but also extends export control discipline to Australian entities.

**South Korea and Taiwan:** Both have announced national quantum programs with semiconductor-industry linkages. For organizations in the electronics supply chain, monitoring these programs is part of the competitive intelligence obligation.

**The governance implication for multinational organizations:** The regulatory landscape is fragmenting along geopolitical lines. A quantum governance framework that works in the United States may not be compliant in the EU or permissible in Asia-Pacific jurisdictions. Multinationals should build jurisdiction-specific compliance review into their quantum governance process, with annual updates as the regulatory landscape evolves.
````
`````

### The Governance Structure

**Board Layer:** Quantum risk and opportunity appear on the board agenda at minimum annually, quarterly for organizations with significant cryptographic exposure. The board needs three things: what is our quantum risk exposure, what are we spending, and what opportunity are we pursuing?

**Executive Team:** CIO, CISO, and CFO should have quarterly quantum reviews. The CTO or Chief Science Officer is the executive sponsor. That sponsorship is not ceremonial — it is the mechanism by which quantum program priorities get resolved when they conflict with other organizational priorities.

**The Quantum Working Group:** Cross-functional, with representatives from IT/security, R&D, legal/compliance, finance, and the most quantum-relevant business units. Meets monthly. Owns the Horizon roadmap, manages vendor relationships, produces the quarterly executive briefing. The Quantum Translator is the group's technical spine.

**Technical Teams:** Pilots and technical work live here. Report to the Quantum Working Group on progress, blockers, and budget needs.

---

## Part IV: Partnership Models

:::{figure} ../images/ch09-partnership-models.png
:label: fig-ch09-partnerships
:alt: Partnership model quadrant showing risk tolerance on x-axis and quantum maturity on y-axis, with four partnership types positioned — hyperscaler low risk/low maturity, consortium medium/medium, native quantum startup high/high, academic lab low risk/variable maturity — with FAU Advantage2 highlighted as a unique academic partnership asset.
:width: 100%
:align: center

**Quantum Partnership Models.** The right partnership model depends on your organization's risk tolerance and quantum maturity. For FAU students, the Advantage2 partnership already provides an academic lab partnership at the institutional level — a resource most organizations must build from scratch.
:::

**The Hyperscaler Model (IBM, AWS, Google, Microsoft):** The fastest Horizon 1 on-ramp. Pay-per-use quantum access, developer documentation, enterprise support, certification programs. Right for: any Horizon 1 organization. Essential starting point.

**The Native Quantum Startup Model (IonQ, Quantinuum, Rigetti, etc.):** More specialized access and flexible partnership terms. Higher risk due to startup volatility. Right for: Horizon 2 organizations with validated use cases requiring hardware specificity not available from hyperscalers.

**The Consortium Model (Chicago Quantum Exchange, QED-C, European Quantum Flagship):** Shared research infrastructure, pre-competitive knowledge exchange, regulatory engagement, talent network access. Annual fees: \$50,000–\$500,000 depending on tier. One of the highest-ROI quantum investments available today. Right for: all Horizon 1 and 2 organizations.

**The Academic Lab Model:** University partnerships provide specialized expertise, talent pipeline, and credibility at \$50,000–\$200,000 per year. For FAU students specifically: the FAU/D-Wave Advantage2 relationship is the institutional version of this model. When you leave this course and join an organization building a quantum program, you understand what an academic quantum partnership looks like from the inside — because you have been its beneficiary.

**The SC26 Signal:** Mehran Basiratmand attended the SC (supercomputing) conference for close to a decade as FAU's CTO. SC26 in Chicago (November 2026) is where quantum and HPC converge. Every major hardware vendor, national lab, and academic quantum program has a presence. Partnership discussions that would take 12 months of email happen in hallways at SC26. If your organization's quantum program has a Translator, that Translator should attend SC26 annually — not as a passive audience member but as an active network builder. The intelligence gathered and the relationships formed at SC26 are worth more than most consulting reports.

---

## Part V: Governance Tools and Budget Frameworks

### Kill-Switch Discipline

:::{figure} ../images/ch09-kill-switch-framework.png
:label: fig-ch09-kill-switch
:alt: Kill-switch discipline framework showing quantum pilot lifecycle decision gates at 90 days, 180 days, 12 months, and 18 months with green continue and red stop paths, and the pre-commitment checklist showing that kill-switch criteria must be written before the investment begins.
:width: 100%
:align: center

**The Kill-Switch Framework.** Every quantum investment needs pre-defined stop conditions established before the investment begins. The kill-switch is not pessimism — it is the discipline that keeps organizations in the quantum game long enough to win, by preventing sunk-cost thinking from extending bad investments at the expense of better ones.
:::

Every quantum pilot needs kill-switch criteria established *before* the pilot begins. This is the pre-commitment that makes honest evaluation possible when emotions and organizational pride have accumulated.

```{list-table} Quantum Pilot Kill-Switch Template
:header-rows: 1

* - Gate
  - Timing
  - Continue Criterion
  - Stop Criterion
* - Problem Validation
  - 90 days
  - Problem is quantum-amenable; classical baseline established
  - Better classical solution found; hardware rubric score below 50/100
* - Technical Proof of Concept
  - 180 days
  - Circuit/QUBO runs on real hardware; correct output on small test case
  - No functional output on real hardware after 6 months
* - Business Case Validation
  - 12 months
  - Measurable improvement over optimized classical baseline
  - No measurable improvement; cost-per-improvement exceeds TCO threshold 2×
* - Scale Decision
  - 18 months
  - Results reproducible; scale path technically clear
  - Results not reproducible; scale requires hardware not yet available
```

### Budgeting Non-Linear Payoffs

Quantum investments behave differently from conventional technology investments in three ways:

**The valley of disillusionment is real and must be budgeted.** Early pilots will frequently fail to demonstrate classical superiority. This is not evidence that the technology is fraudulent — it is evidence that NISQ-era hardware has real limitations. Organizations that have not pre-planned for this valley will kill programs at the wrong moment.

**The option value is significant.** A pilot that does not immediately produce classical advantage still produces: team learning, vendor relationships, problem decomposition skills, and hardware familiarity. A governance framework that evaluates quantum investments purely on primary objective achievement will systematically underinvest.

**The payoff distribution is fat-tailed.** Most quantum investments in Horizons 1 and 2 produce modest returns. A small number produce enormous returns. Make enough diversified bets to be statistically likely to hit at least one fat-tail outcome.

**The \$1.5M Annual Reference Envelope:** A mid-cap organization (\$500M–\$3B revenue) can fund a Translator hire, consortium membership, two cloud platform subscriptions, and one active pilot for approximately \$1–\$2M annually. This is the right Horizon 1 budget for most mid-cap organizations — enough to build real capability without over-committing to outcomes that are not yet predictable.

---

## Part VI: Synthesis — Every Tool From Every Chapter

:::{figure} ../images/ch09-quantum-readiness-synthesis.png
:label: fig-ch09-synthesis
:alt: Synthesis diagram showing all nine chapters as interconnected nodes feeding into the quantum investment thesis at the center, with the dual-paradigm lens labeled as the unifying thread connecting annealing tools (Chapters 6, 7, 8 Lab 8B, 9 Lab 9B) to gate-model tools (Chapters 3, 4, 5, 7, 8).
:width: 100%
:align: center

**The Course in One Diagram.** The dual-paradigm lens is the organizing thread: annealing tools (Chapters 6, 7 supply chain and finance, Chapter 8 Lab 8B, Chapter 9 Lab 9B) map to Horizon 1 and early Horizon 2. Gate-model tools (VQE from Chapter 7, quantum kernels from Chapter 8, the hardware roadmap from Chapter 4) map to Horizon 2 and 3. The capstone investment thesis deploys all of them in the right horizon.
:::

Every chapter gave you one or more analytical tools. The capstone asks you to use all of them together. The connections:

**{ref}`ch-01-why-quantum-why-now` — Market Context:** The FAU/D-Wave Advantage2 deal, D-Wave's HQ relocation to Boca Raton, and the geopolitical quantum race provide the urgency framing for your investment thesis. The window is real, the competition is real, and the timing is not arbitrary.

**{ref}`ch-02-thinking-in-probabilities` — Mental Models:** The ability to evaluate vendor claims accurately — and to explain quantum concepts to non-technical audiences — is the communication foundation of every board briefing, every partner conversation, and every pilot proposal.

**{ref}`ch-03-bits-to-qubits-economics` — TCO Framework:** The total cost of ownership framework is the analytical backbone of your budget section. Cost of quantum cloud, classical alternative, transition cost, operational overhead, expected value of improvement. The budget is a TCO analysis, not a spreadsheet of hopes.

**{ref}`ch-04-hardware-race` — Hardware Rubric:** The rubric (gate fidelity, qubit count, connectivity, coherence time, error correction overhead, cloud accessibility) makes pilot platform selection disciplined. Apply it to your Horizon 2 pilot candidates.

**{ref}`ch-05-cryptocalypse-y2q` — Mosca Inequality + STRIDE:** The Mosca Inequality determines whether PQC migration is a Horizon 1 obligation. STRIDE provides the governance vocabulary for communicating cryptographic quantum risk to boards. Both belong in the security section of your investment thesis.

**{ref}`ch-06-optimization-goldmine` — QUBO Formulation:** The annealing optimization toolkit is the primary Horizon 1 action tool for optimization-heavy organizations. Your investment thesis should name the specific QUBO candidate problem that your Horizon 1 pilot will target.

**{ref}`ch-07-simulation-revolution` — Industry Verticals:** The vertical opportunity maps (finance, supply chain, healthcare, energy) provide the context for which quantum applications are relevant to your industry — and which are Horizon 2 vs. Horizon 3 targets based on hardware requirements.

**{ref}`ch-08-quantum-ai-hybrid` — Hype Filter + Annealing ML:** The five-question governance filter protects your investment thesis from quantum AI marketing. The QUBO feature selection and quantum-inspired classical analytics from Chapter 8 extend the Horizon 1 annealing toolkit to ML applications.

---

## Flagship Case Study: The Mid-Cap CEO's \$1.5M Quantum Readiness Program

:::{figure} ../images/ch09-ceo-case-study.png
:label: fig-ch09-ceo-case
:alt: Mid-cap CEO quantum readiness case study dashboard showing three-year timeline, Year 1 budget allocation pie chart, the Translator hire timeline, annealing pilot results, PQC migration progress, and board reporting cadence.
:width: 100%
:align: center

**The \$1.5M Quantum Readiness Envelope.** Three years of structured quantum investment by a mid-cap operations CEO — what was bought, what was paused, what was regretted, and how it was reported to the board when the technology's vocabulary changed twice during the engagement.
:::

*A composite based on documented enterprise quantum programs.*

A regional logistics company (\$2.1B revenue, 4,800 employees) whose CEO had an engineering background authorized a \$1.5M annual quantum readiness budget in 2023. Her primary hypothesis: route optimization for 14,000+ daily shipments. Her Mosca calculation placed the organization at the edge of the danger zone for its EDI partner communication infrastructure (RSA-2048, 7-year data sensitivity, 7-year estimated migration timeline, Q-Day estimate 10–12 years). Both hypotheses required action.

**Year 1 allocation:** \$240K Translator hire; \$180K cryptographic inventory tooling; \$75K consortium membership; \$120K IBM Quantum Premium access; \$90K manager training (8 leaders); \$795K route optimization pilot development (including classical baseline optimization as the first deliverable, before a single quantum circuit was written).

**What was paused:** A \$500K equity offer in a logistics quantum startup. "We didn't know enough to evaluate them on Day Sixty," the CEO noted. "The Translator needed 90 days before I trusted her judgment on a venture investment." The startup raised significant VC from investors without technical due diligence requirements. One subsequently pivoted away from quantum. The decline is considered a governance success.

**Year 2 shift:** The cryptographic inventory revealed 14 priority systems. Year 2 budget shifted \$600K toward PQC migration — work that had been underestimated in Year 1. The route optimization pilot continued at reduced funding as the migration became the more urgent Horizon 1 deliverable.

**Three-year outcome:** PQC migration 60% complete. Route optimization pilot: 2.1% fuel efficiency improvement on 500 daily routes — below the 4–7% hypothesis but statistically significant. The Translator had become a recognized internal authority; three business units had requested quantum assessments. Board quantum reporting institutionalized: annual detailed briefing, quarterly two-slide update.

**The CEO's regret:** "I should have hired the Translator twelve months earlier. We spent the first year trying to make quantum decisions without her, which meant we bought one tool that turned out to be quantum-inspired classical software at a quantum price. \$80,000, gone. The Translator is not the person you hire after you understand what you need. She is the person who helps you understand what you need."

**The open question:** Whether to take the equity stake in the logistics quantum startup, now that the Translator has two years to evaluate the landscape. The CEO is deliberating. The deliberation itself is a governance success — it is a considered investment decision, not a reactive one.

---

## Board-Level Quantum Reporting

:::{figure} ../images/ch09-board-reporting.png
:label: fig-ch09-board
:alt: Board quantum reporting dashboard showing five-section annual report structure — threat landscape, regulatory posture, investment portfolio, talent status, competitive intelligence — with traffic light status indicators and 15-minute presentation timing guide.
:width: 100%
:align: center

**The Board Quantum Reporting Dashboard.** Boards need three things: threat clarity, investment transparency, and progress visibility. The five-section quantum report delivers all three in 15 minutes. Build the vocabulary before the crisis requires it.
:::

Board quantum reporting should follow the cybersecurity reporting model that became standard after a decade of refinement. Five sections, 15 minutes total:

**Section 1: Threat Landscape (3 min)** — Current hardware milestone status, consensus Q-Day estimate update, any significant changes in the quantum competitive landscape. Anchor: {ref}`ch-01-why-quantum-why-now` and {ref}`ch-04-hardware-race`.

**Section 2: Regulatory and Compliance Posture (3 min)** — PQC migration status, NIST compliance posture, export control review status, quantum-related regulatory developments. For financial services, healthcare, and critical infrastructure, this section may require more time.

**Section 3: Investment Portfolio Status (4 min)** — Active pilots against kill-switch criteria, budget vs. actual, partnership status, talent status. Organizing framework: the dual-paradigm Three-Horizon roadmap.

**Section 4: Talent and Organization Status (2 min)** — Translator in seat? Specialist gaps? Training completion? Academic partnership active?

**Section 5: Competitive Intelligence (3 min)** — Competitor quantum announcements, patent filings, talent moves, SC26 or equivalent signal events. This section should use the monitoring infrastructure built in Horizon 1.

---

## The Capstone Deliverable: One-Page Quantum Investment Thesis

:::{figure} ../images/ch09-capstone-template.png
:label: fig-ch09-capstone
:alt: One-page quantum investment thesis template showing eight structured sections — executive summary, three-horizon roadmap, talent plan, partnership recommendation, budget breakdown, success metrics, kill-switch criteria, signatures — with the dual-paradigm lens explicitly incorporated in the three-horizon section.
:width: 100%
:align: center

**The One-Page Quantum Investment Thesis Template.** Every section connects to a specific chapter and analytical tool. The dual-paradigm three-horizon roadmap is the structural spine: it answers both "what do we do now with annealing hardware?" and "what do we prepare for with gate-model hardware?" The one-page constraint is not arbitrary — it forces the clarity that makes a board presentation credible.
:::

**Eight Sections on One Page:**

**Section 1: Executive Summary (2 sentences)**
Organization, quantum opportunity/risk, and why now. What you are asking for and what you will deliver.

**Section 2: Three-Horizon Roadmap (table)**
Three rows, four columns (Timeframe, Paradigm Focus, Key Activities, Success Metric). The Paradigm Focus column distinguishes: H1 = annealing optimization + PQC security; H2 = annealing at scale + gate-model experimentation; H3 = integrated quantum-classical operations across both paradigms.

**Section 3: Talent Plan**
Translator hire (timeline, profile, cost); Quantum-Literate Manager training (number, program, timeline); External Research Partnership (institution, focus area, annual cost).

**Section 4: Partnership Recommendation**
Specific partnership model and rationale. Anchor in the partnership model framework. Name the specific hyperscaler, consortium, or academic partner.

**Section 5: Budget Breakdown**
Three years by category: talent, platform access, tools, pilots, partnerships, governance. Apply the TCO methodology from {ref}`ch-03-bits-to-qubits-economics`.

**Section 6: Success Metrics**
Specific, measurable, time-bound. Include at least one annealing metric (pilot improvement vs. classical baseline), one security metric (PQC migration progress), and one organizational metric (board reporting institutionalized).

**Section 7: Kill-Switch Criteria**
Pre-defined stop conditions for each major investment. Specific, time-bound, with explicit reallocation plan.

**Section 8: Signatures**
Business sponsor + financial authority + Quantum Translator (or the executive who will own the program before the Translator is hired). Three signatures = three owners.

---

## Productive-Struggle Problem: The Capstone

::::{admonition} Your One-Page Quantum Investment Thesis
:class: important

**This is the capstone deliverable for the course.** It synthesizes every chapter, every lab, every case study. It is what quantum readiness leadership looks like on paper.

**Your task:** Draft, present, and defend a one-page quantum investment thesis for a *named* real organization — your own, a publicly traded company in your industry, or an organization from the cases in this book.

**The deliverable must include all eight sections.** One page (11-point font, standard margins). Supporting analysis — TCO calculations, Mosca Inequality workings, hardware rubric scores, pilot proposal — may be appendices.

**Presentation (10 minutes):**
1. Organization and quantum opportunity/risk (2 min)
2. Walk through each section (5 min)
3. Field C-suite objections: "Why now?" "Why not wait two years?" "What does success look like at 18 months?" "Why annealing and not gate-model?" (3 min)
::::

::::{dropdown} Scaffolding: Step-by-Step
:open:

1. **Choose your organization. Name it.** Vague organizations produce vague theses.
2. **Run the Mosca Inequality.** Calculate X + Y for your primary data categories. If X + Y > Z, PQC migration is a Horizon 1 obligation regardless of all other analysis.
3. **Identify your primary annealing candidate.** What is the highest-value optimization problem in your organization that can be formulated as a QUBO today? Use Chapter 6 and Lab 9B as your reference.
4. **Apply the hardware rubric to your primary gate-model candidate.** Apply the Chapter 4 rubric to your Horizon 2 gate-model use case. If no platform scores above 50/100, that use case is Horizon 3.
5. **Build the TCO analysis** for both your annealing pilot and your gate-model experiment.
6. **Write kill-switch criteria first.** Before writing the budget.
7. **Write the executive summary last.** After everything else is clear.
8. **Rehearse the "Why not wait?" objection.** Your answer anchors in: Mosca Inequality (PQC cannot wait), Three-Horizon framework (H1 builds H2 optionality), talent market (Translators are already scarce), and annealing accessibility (the opportunity is open today, not in 3 years).
::::

---

## Module-Level Outcomes

::::{card-carousel} 1

:::{card} Outcome 1
**Construct a dual-paradigm three-horizon quantum roadmap.**
Distinguish between Horizon 1 annealing applications (D-Wave, accessible now) and gate-model applications (Horizon 2–3), and build a roadmap that deploys both paradigms in the right sequence.
:::

:::{card} Outcome 2
**Design a quantum talent strategy.**
Sequence the four talent roles correctly (Quantum-Literate Manager, Translator, Specialist, External Research Partner), identify where to find a Translator, and articulate why the Translator is always the first hire.
:::

:::{card} Outcome 3
**Evaluate partnership models.**
Match the appropriate partnership model (hyperscaler, consortium, native startup, academic lab) to an organization's quantum maturity and risk tolerance, and name the specific partner most relevant to the organization's use case.
:::

:::{card} Outcome 4
**Build a quantum governance framework.**
Design a governance structure covering dual-use risk, export controls, the US/EU/APAC regulatory landscape, and a board reporting cadence that builds vocabulary before it is urgently required.
:::

:::{card} Outcome 5
**Defend a one-page quantum investment thesis.**
Present and defend all eight sections of the quantum investment thesis to a C-suite audience, including quantified success metrics, pre-defined kill-switch criteria, and a credible answer to "why not wait?"
:::

:::{card} Outcome 6
**Run a D-Wave optimization pilot for your own organization.**
Formulate your organization's highest-priority optimization problem as a QUBO, execute it on D-Wave Leap, interpret the results against a classical baseline, and incorporate the findings into the Horizon 1 section of your investment thesis.
:::

::::

---

## Lab 9A (Regular): The Quantum Pilot Pitch

**Duration:** ~90 minutes
**Tools:** IBM Quantum Platform + all labs completed in Chapters 1–8
**Format:** Deliverable + 10-minute live pitch

Look back at the labs you completed in Chapters 5 through 8. Choose the one that most directly maps to a real problem in your organization. Extend that lab into a full quantum pilot proposal including: problem statement, quantum approach (with hardware rubric score), success metrics (vs. optimized classical baseline), budget (TCO framework), kill-switch criteria, and a 90-second IBM Quantum or D-Wave Leap demo that makes the quantum approach visible to a non-technical sponsor.

**The live pitch:** 10 minutes. Lead with the demo. Walk through the pilot proposal. Field objections using the frameworks in this chapter.

---

## Lab 9B (Applied): Your Organization's QUBO on D-Wave Leap

**Duration:** 60–75 minutes
**Tools:** D-Wave Leap — [cloud.dwavesys.com](https://cloud.dwavesys.com)
**Deliverable:** Working QUBO + 400-word investment thesis excerpt

<a href="https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch09-lab-org-qubo.ipynb" target="_blank">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="margin-bottom: 1rem;"/>
</a>

### Why This Lab

This lab is the capstone of every D-Wave lab in this course. Chapter 6 gave you QUBO formulation. Chapter 7 applied it to supply chain and logistics. Chapter 8 applied it to ML feature selection. Chapter 9 asks you to formulate *your own organization's* most valuable optimization problem as a QUBO and run it on D-Wave Leap — the same hardware class as FAU's Advantage2.

The output is not a toy example. It is the working technical foundation of the Horizon 1 annealing pilot section of your capstone investment thesis.

### Step 1: Identify Your QUBO Candidate

Using the optimization opportunity framework from {ref}`ch-06-optimization-goldmine`, identify your organization's highest-priority combinatorial optimization problem. Candidates: vehicle routing, production scheduling, resource allocation, portfolio construction, inventory allocation, feature selection, network design.

Write a 100-word problem statement before opening a code editor. What is the business problem? What are the variables? What are the constraints? What does "better" look like, and how will you measure it?

### Step 2: Formulate the QUBO

```python
import dimod
from dwave.system import LeapHybridSampler

# YOUR PROBLEM HERE
# Replace the template below with your organization's actual optimization problem

# Example: shift scheduling for 6 employees, 4 shifts, coverage constraints
# Binary variable x_{i,j} = 1 if employee i works shift j
employees = ['Alice', 'Bob', 'Carol', 'David', 'Eve', 'Frank']
shifts = ['Morning', 'Afternoon', 'Evening', 'Night']

# REPLACE WITH YOUR VARIABLES:
# - What are the binary decisions?
# - What are the costs/benefits of each decision?
# - What constraints must be satisfied?

Q = {}

# OBJECTIVE: Minimize cost / Maximize value
# (your formulation here)

# CONSTRAINTS: Penalty for violations
# (your formulation here)

# Submit to D-Wave Leap
sampler = LeapHybridSampler()
sampleset = sampler.sample_qubo(Q, label='Ch9 Capstone — My Org QUBO', time_limit=10)

best = sampleset.first
print("Solution:")
print(best.sample)
print(f"Energy: {best.energy:.2f}")
print(f"QPU timing: {sampleset.info.get('timing', {})}")
```

### Step 3: Benchmark Against Classical

Run the same problem using:
- Classical greedy heuristic (your organization's current approach, or a simple greedy algorithm)
- `dimod.SimulatedAnnealingSampler` (quantum-inspired classical)
- D-Wave Leap (quantum annealing)

Compare solution quality and compute time across all three.

### Step 4: Write the Investment Thesis Excerpt

Write a **400-word excerpt** for the Horizon 1 section of your capstone investment thesis:
1. The business problem and its current cost (what does the gap between classical and optimal cost annually?)
2. Why this problem maps to QUBO formulation (specifically — using the language of Chapter 6)
3. What the D-Wave result showed — improvement, time, and what it implies at production scale
4. What the next step is: scale the pilot to your full production problem size, benchmark against your fully optimized classical baseline, and if improvement holds, present to your board as a Horizon 1 quantum win

---

## Lab 9C (Optional Advanced): The Quantum Evaluation Toolkit

**Duration:** 3–5 hours
**Language:** Python
**Output:** Working GitHub repository + 500-word design writeup

<a href="https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch09-quantum-eval-toolkit.ipynb" target="_blank">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="margin-bottom: 1rem;"/>
</a>

Build a Python library that integrates three quantitative frameworks from this course into a single command-line interface:

**Module 1: TCO Analyzer** — Input: problem parameters. Output: quantum vs. classical cost comparison, break-even analysis.

**Module 2: Hardware Rubric Scorer** — Input: use case parameters. Output: rubric score for each supported platform, ranked recommendation.

**Module 3: Mosca Inequality Classifier** — Input: data sensitivity lifetime, migration time estimate, threat timeline. Output: classification (Safe/Danger Zone/Critical), recommended action.

**Module 4: Summary Report Generator** — Produces a one-page text output suitable for inclusion in a quantum investment thesis appendix.

**Deliverable:** Working tool on GitHub (public repository), README, and 500-word design writeup.

---

## Discussion Guidelines

**Post 350–500 words. Cite at least two sources from the last 24 months. Reply substantively to TWO peers.**

**Prompt:** Choose a real industry and defend a specific quantum readiness posture: *aggressive early mover, disciplined fast follower, or informed observer.* Your argument must address: (1) which paradigm (annealing, gate-model, or both) is most relevant for your industry and horizon; (2) the Mosca Inequality implications for your industry's cryptographic exposure; (3) the talent market realities for your industry; (4) at least one governance consideration from Part III; and (5) what SC26 or an equivalent signal event tells you about where your industry is heading.

---

## Glossary

```{glossary}
quantum organizational readiness
  The capacity of an organization to perceive, evaluate, and act on quantum computing opportunities and risks within an 18-month window of when those opportunities and risks become commercially material. A function of strategy clarity, talent depth, governance maturity, and partnership positioning.

dual-paradigm three-horizon roadmap
  A quantum strategy planning framework that distinguishes between annealing applications (D-Wave, accessible in Horizon 1 today for optimization problems) and gate-model applications (Horizon 2–3 for simulation, QML, and fault-tolerant algorithms), and sequences organizational actions in both paradigms appropriately.

quantum translator
  A professional genuinely fluent in both quantum computing and business strategy. The recommended first hire for any quantum readiness program. Runs pilots, briefs boards, evaluates vendors, manages academic partners.

quantum-literate manager
  An executive with sufficient quantum literacy to evaluate vendor claims, oversee pilots, and participate in board-level quantum discussions — achieved through structured training, not specialized hiring.

quantum specialist
  A quantum scientist or engineer with deep technical expertise in a specific quantum domain. Appropriate for late Horizon 2 or Horizon 3 organizations with validated technical needs.

quantum Center of Excellence (QCoE)
  A dedicated organizational unit that owns quantum strategy, manages vendors, runs the talent pipeline, and serves as the internal resource for all quantum-related business unit questions. The Horizon 3 formalization of organizational quantum capability.

kill-switch criteria
  Pre-defined, specific, measurable conditions established before a quantum investment begins that would cause the organization to stop funding it. The structural mechanism that prevents sunk-cost rationalization from extending bad investments.

dual-use risk
  The risk that quantum computing capabilities developed for defensive or commercial purposes could be applied offensively or harmfully — including breaking encryption others rely on for privacy and security. Requires legal review and ethics governance.

export controls
  Regulations governing the transfer of quantum hardware, software, and technical expertise across national borders. Includes EAR (U.S.), ITAR (U.S.), and equivalent EU and Asia-Pacific frameworks. Material compliance obligation for any organization with international quantum partnerships.

quantum investment thesis
  A structured one-page argument for quantum investment including executive summary, dual-paradigm three-horizon roadmap, talent plan, partnership recommendation, budget breakdown, success metrics, and kill-switch criteria.

SC26
  The International Conference for High Performance Computing, Networking, Storage and Analysis, convening in Chicago in November 2026. The annual signal event where quantum and HPC converge and where the frontier of enterprise quantum capability becomes visible. Recommended annual attendance for any organization's Quantum Translator.

valley of disillusionment
  The period when early quantum pilots underperform initial expectations due to hardware limitations, leading to program cancellation just before the technology would have delivered value. Must be explicitly budgeted and planned for in any quantum roadmap.

non-linear quantum payoff
  The characteristic of quantum investment in which most Horizon 1–2 investments produce modest returns while a small number produce very large returns, requiring portfolio-style investment discipline.

option value
  The strategic value of a quantum investment beyond its immediate financial return — team learning, vendor relationships, problem formulation skills, and the organizational right to capture larger quantum payoffs when hardware matures.

CNSA 2.0
  NSA's Commercial National Security Algorithm Suite 2.0 mandate requiring PQC migration in U.S. national security systems by 2030–2035.

Quantum Working Group
  A cross-functional internal team — IT/security, R&D, legal/compliance, finance, business units — that owns the quantum readiness roadmap, manages vendor relationships, and produces the quarterly executive briefing. The Quantum Translator is the group's technical spine.
```

---

## Going Deeper (Optional): Quantum Error Correction and the Path to Fault Tolerance

*This section bridges the gap between the NISQ hardware you have used in this course and the fault-tolerant quantum computers that will enable Horizon 3 in your three-horizon roadmap. Not required for course assessments.*

### Why NISQ Is Not Enough — and What Fault Tolerance Requires

Every qubit in a NISQ processor has an error rate of approximately 0.1–1% per gate operation. For algorithms requiring millions of gate operations (Shor's algorithm at commercial key sizes, full molecular simulation for drug discovery, quantum-exact fluid dynamics), NISQ hardware produces outputs that are dominated by noise — not useful computation. **Quantum error correction (QEC)** solves this by encoding one **logical qubit** into many **physical qubits**, using redundancy to detect and correct errors without measuring (and thus collapsing) the logical qubit state.

### The Surface Code: The Leading QEC Architecture

The **surface code** is the most experimentally practical QEC code for superconducting qubits. It arranges physical qubits on a 2D grid, with alternating data qubits and syndrome measurement qubits. Errors (bit-flips and phase-flips) are detected by measuring stabilizer operators — multi-qubit Pauli measurements that reveal error syndromes without revealing the logical qubit state.

The key metric is the **code distance** $d$: a surface code with distance $d$ can correct up to $\lfloor (d-1)/2 \rfloor$ arbitrary errors. The number of physical qubits required is $d^2$ data qubits + $(d^2 - 1)$ syndrome qubits $\approx 2d^2$.

The **threshold theorem** establishes that if the physical error rate $p$ is below a threshold $p_{\text{th}} \approx 1\%$ (for surface code), then increasing $d$ exponentially suppresses the logical error rate:

$$p_L \approx \left(\frac{p}{p_{\text{th}}}\right)^{\lceil d/2 \rceil}$$

For $p = 0.1\%$ and $d = 15$: $p_L \approx (0.1)^7 = 10^{-7}$ logical errors per gate cycle. This is the suppression required for a billion-gate algorithm to succeed with high probability.

### The Physical-to-Logical Qubit Overhead

To run Shor's algorithm on a 2,048-bit RSA key requires approximately 4,000 logical qubits and $3 \times 10^9$ logical gate operations. At $d = 15$, each logical qubit requires ~450 physical qubits. Total physical qubit requirement: $\sim 4{,}000 \times 450 = 1{,}800{,}000$ physical qubits. IBM's current Heron processors have 133 qubits. This is the engineering gap that defines your Horizon 3 timeline.

### Implications for Your Three-Horizon Roadmap

This mathematics explains why the dual-paradigm roadmap in this chapter puts fault-tolerant gate-model applications in Horizon 3 (2030+): the physical qubit count required for fault-tolerant RSA-breaking or full molecular simulation exceeds any system in existence or announced roadmap through 2029. D-Wave's annealing hardware bypasses this overhead because it implements an analog optimization process — not a digital gate circuit — that is inherently error-robust at the algorithm level. This is not a workaround; it is a genuinely different computational model that operates today because it makes different (and tractable) trade-offs than gate-model fault tolerance requires.

---

## Leader's Takeaway

::::{admonition} The Leader's Takeaway — and a Course Closing
:class: important

This course began with a question: is quantum computing real or hype? The answer is the same as the answer to every technology question about a transformative technology in its early deployment phase. Both. Depending on the layer.

The hype layer is loud and well-funded. Vendors are attaching "quantum" to classical algorithms, to marketing materials, to investment prospectuses, and to startup pitch decks where the quantum component is a random seed. The governance tools in this course — the dequantization test, the five-question procurement filter, the classical baseline optimization requirement, the hardware rubric — are what protect your organization from spending real money on imaginary quantum advantages.

The real layer is quieter and more consequential. D-Wave's Advantage2 is on FAU's campus. It is the same hardware class that BASF uses for manufacturing scheduling, that Mastercard uses for fraud detection, that Verge Ag uses for autonomous fleet routing. It runs today. The QUBO formulation skills you developed in Chapter 6 and deployed in Labs 6, 7B, 8B, and 9B are the production skills that enable those deployments. The gap between "we have heard about quantum optimization" and "we have run a quantum optimization job and benchmarked it against our classical system" is a gap that almost no organization's leadership team has crossed. You have crossed it.

The PQC migration obligation is not hype. NIST finalized three post-quantum cryptography standards in 2024. Nation-state adversaries have been collecting encrypted traffic for future quantum decryption for years. The Mosca Inequality calculation is not a thought experiment — for many organizations, it is a calculation that has already turned negative, meaning the migration must be complete before Q-Day to protect their longest-lived sensitive data. This is a present obligation, not a future concern.

The talent gap is not hype. Quantum translators — the professionals who can genuinely bridge quantum science and business strategy — are in short supply and growing scarcer as organizations that understand this begin building programs. The students who completed this course, who ran QUBO formulations on D-Wave Leap and VQE simulations on IBM Quantum and PQC key generation with liboqs, have a measurable head start. That head start has a half-life. Use it.

The dual-paradigm lens that this course has insisted on — distinguishing annealing from gate-model, distinguishing what is accessible today from what is coming in 5–8 years — is the strategic lens that makes quantum investment rational rather than speculative. Most organizations are either too early on the annealing track (waiting for gate-model maturity before doing anything quantum, including the optimization applications that are accessible now) or too late on the gate-model track (waiting for certainty before building the literacy and talent that takes years to develop).

The quantum-ready enterprise is neither. It is deploying D-Wave annealing for optimization today, migrating its cryptographic infrastructure now, building its talent pipeline in parallel, and watching the gate-model frontier with the literacy to evaluate it honestly when the hardware matures.

SC26 is in Chicago this November. The quantum track is there. The researchers who will shape the next five years of quantum enterprise capability will be in those rooms. If you are building a quantum program, send your Translator. If you do not have a Translator yet, put one in the hiring pipeline before you go.

The window to be early is not infinite. Act accordingly.
::::

---

## Cross-References

- **{ref}`ch-01-why-quantum-why-now`** — FAU/D-Wave Advantage2 anchor case and the dual-paradigm framing that runs through this chapter's Three-Horizon roadmap
- **{ref}`ch-05-cryptocalypse-y2q`** — Mosca Inequality calculation and STRIDE framework for the security section of the investment thesis
- **{ref}`ch-06-optimization-goldmine`** — QUBO formulation and D-Wave Ocean SDK skills deployed in Lab 9B
- **{ref}`ch-07-simulation-revolution`** — Industry vertical opportunity maps that inform Horizon 2 and 3 pilot candidate selection
- **{ref}`ch-08-quantum-ai-hybrid`** — Five-question governance filter and quantum-inspired classical analytics for the governance and hype-filtering sections of the investment thesis
