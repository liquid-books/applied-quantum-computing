# Chapter 9 Quiz: The Quantum-Ready Enterprise — Strategy, Talent, and Timing

*Not in the book TOC. For instructor use and self-assessment.*

---

## Exercise 1: Three-Horizon Identification (Scenario Analysis)

A regional bank with \$8B in assets is evaluating its quantum readiness posture. Their CISO has identified that 40% of their internal certificate infrastructure uses RSA-2048. Their head of quantitative finance believes that quantum optimization could improve their loan portfolio allocation by 3–5%. Their CEO wants to understand what to do *now*, what to do *in three years*, and what to do *in seven years*.

**Questions:**

a) Apply the Mosca Inequality to the bank's cryptographic exposure. Assume: the bank's transaction records have a 10-year confidentiality requirement (X = 10), migration will take 5 years (Y = 5), and cryptographically relevant quantum computers are 10–12 years away (Z = 11). What does the inequality tell you? Is PQC migration a Horizon 1 priority?

b) Where does the loan portfolio optimization opportunity belong — Horizon 1, 2, or 3? Justify using the hardware rubric framework from Chapter 4.

c) Write a one-sentence summary for each horizon that the CEO could use in a board presentation.

**Answer Key:**

a) X + Y = 10 + 5 = 15. Z = 11. Since 15 > 11, the Mosca Inequality is triggered. The bank is in the danger zone — they need to begin PQC migration *now* as a Horizon 1 priority. The migration timeline exceeds the estimated quantum threat arrival. Every year of delay narrows the window.

b) Loan portfolio optimization belongs in Horizon 2 (2–5 years). Current NISQ hardware lacks the qubit counts and fidelity required for production-scale financial portfolio optimization at the scale an \$8B bank requires. However, the problem is genuinely quantum-amenable (combinatorial optimization, fits Chapter 6 framework), and pilots on near-term hardware can begin building the organizational capability and benchmarks that make Horizon 3 deployment possible. A hardware rubric assessment should confirm that no current platform scores above 50/100 for production-scale portfolio optimization — placing full deployment in Horizon 3 but exploration in Horizon 2.

c) Horizon 1: "We are mapping our cryptographic exposure and beginning the multi-year migration to quantum-resistant encryption that regulators will require." Horizon 2: "We are running controlled pilots of quantum optimization for portfolio allocation and building the talent and vendor relationships that will let us move quickly when hardware matures." Horizon 3: "Quantum optimization is integrated into our core loan underwriting and portfolio management workflows, delivering measurable efficiency advantages that our competitors are still studying."

---

## Exercise 2: Talent Architecture Design

A \$500M pharmaceutical company is beginning a quantum readiness program. They have no existing quantum expertise and a modest technology budget. They are considering three hiring options:

**Option A:** Hire a quantum physicist from a university lab (\$320,000/year total compensation) to lead the quantum program.

**Option B:** Hire a "quantum translator" — a PhD chemist who spent four years at a quantum computing startup doing business development and algorithm development (\$230,000/year total compensation).

**Option C:** Join a pharmaceutical quantum consortium (\$80,000/year membership fee) and train three existing R&D managers in quantum literacy (\$45,000 training investment).

**Questions:**

a) Which option is most appropriate for a Horizon 1 pharmaceutical organization? Justify.

b) What is the risk of Option A for a Horizon 1 organization?

c) Could Option C alone be sufficient for Horizon 1? What does it lack?

d) Design an optimal Horizon 1 talent strategy that could be implemented within a \$400,000 total annual budget.

**Answer Key:**

a) Option B is most appropriate. A Horizon 1 organization needs a Quantum Translator — someone who can bridge quantum technical work and business value, evaluate vendor claims, run the quantum readiness program, and brief executives. The profile described in Option B (quantum startup business development + algorithm background) matches the Translator archetype precisely. The chemistry background is especially valuable for a pharmaceutical context.

b) The primary risk of Option A is strategic misalignment. A quantum physicist hired to lead a Horizon 1 pharmaceutical quantum program will likely gravitate toward technically interesting research problems rather than the organizationally necessary work: cryptographic inventory, vendor evaluation, manager training, pilot scoping, and board reporting. Without a Translator bridging between the physicist and the business, the physicist's work may produce publications rather than organizational capability. Additionally, at \$320,000, Option A consumes 64% of a reasonable Horizon 1 budget.

c) Option C alone is insufficient for Horizon 1 because it lacks the translation capability. The consortium provides peer network access and research visibility, and the manager training builds literacy, but neither produces a person who can run pilots, evaluate vendors, or provide technical depth when needed. Option C is excellent infrastructure but cannot replace the Translator role.

d) Optimal Horizon 1 strategy within \$400,000: Hire the Translator (Option B: \$230,000). Join the pharmaceutical quantum consortium (\$80,000). Train three R&D managers in quantum literacy (\$45,000). Allocate remaining \$45,000 to IBM Quantum Platform access and initial pilot scoping. Total: \$400,000. This provides translation capability, peer network, executive literacy, and platform access — the four Horizon 1 essentials.

---

## Exercise 3: Kill-Switch Design

A healthcare technology company has just approved a \$750,000 quantum machine learning pilot. The objective is to use variational quantum circuits (VQCs) to improve diagnostic image classification accuracy for radiology. The pilot team is enthusiastic, the vendor is promising, and the CMO is an executive sponsor.

**Questions:**

a) Using the kill-switch template from Section 9.11, design Gate 1 (90-day), Gate 2 (180-day), and Gate 3 (12-month) criteria for this pilot.

b) What is the "sunk cost" risk in this specific scenario, and how does the kill-switch design mitigate it?

c) The pilot team reports at 180 days that their circuit is running on a simulator but not yet on real hardware due to "hardware availability issues." Should this trigger the Gate 2 kill-switch? Justify using the Chapter 8 dequantization principle.

**Answer Key:**

a) **Gate 1 (90 days):** Success: Problem confirmed quantum-amenable — hardware rubric score >50/100 for VQC-based classification; classical baseline accuracy established on the same dataset; vendor has demonstrated working circuit on at least one real quantum device (not simulator only). Kill: Rubric score below 40/100; hardware not available; a classical ML model already matches the claimed quantum target accuracy without quantum hardware.

**Gate 2 (180 days):** Success: VQC circuit runs on real quantum hardware (IBM Quantum or equivalent); demonstrates correct classification on a small-scale test dataset (500+ images); accuracy within 5% of the classical baseline (proving the circuit is functioning, even if not yet superior). Kill: Circuit only functional on simulator after 180 days; team blames hardware availability rather than identifying a simulator-to-hardware migration plan.

**Gate 3 (12 months):** Success: Measurable accuracy improvement over optimized classical baseline on a clinical-scale dataset; improvement is statistically significant; scale path to production is technically articulated. Kill: No measurable improvement over optimized classical CNN after 12 months; or cost-per-classification-improvement exceeds TCO threshold by 2×.

b) The sunk cost risk: the CMO is an executive sponsor, which creates organizational pressure to continue the pilot regardless of results — because admitting the pilot is not working feels like a personal failure for the sponsor. With \$750,000 committed and a visible executive sponsor, the social pressure to rationalize continued investment is intense. The kill-switch mitigates this by separating the evaluation criterion from the human relationships: the question at each gate is not "Is the team working hard?" or "Is the CMO embarrassed?" but "Did we meet this specific criterion by this specific date?" Pre-commitment depersonalizes the evaluation.

c) This should trigger serious scrutiny and likely trigger the Gate 2 kill-switch. The Chapter 8 dequantization principle warns explicitly: if the only evidence of quantum advantage comes from simulators — not real hardware — then there is no demonstrated quantum advantage. Simulators do not have noise, decoherence, or connectivity constraints; they are ideal quantum computers. A circuit that works on a simulator but not on real hardware after 180 days of a funded pilot is not a technical delay — it is evidence that the circuit may not be viable on real hardware. The team should be asked to demonstrate a working circuit on real hardware (even with reduced problem size) within 30 days or the kill-switch should be activated.

---

## Exercise 4: Board Reporting Design

You are the CIO of a \$15B energy utility company. You have just completed the first year of a quantum readiness program. You need to present an annual quantum update to the 14-member board of directors. Most board members have no technical background; two have deep finance backgrounds; one is a former defense contractor executive.

**Questions:**

a) Design a 15-minute board presentation using the five-section format from Section 9.12. What specific content goes in each section, given the energy utility context?

b) The former defense contractor board member asks: "Should we be concerned about quantum cyberattacks on our grid control systems?" How do you answer in two sentences using concepts from this course?

c) A finance-background board member asks: "We've spent \$1.2M on quantum in year one with no measurable return. Why should we continue?" Construct a two-part answer: (1) reframe using option value and the TCO framework, and (2) use the three-horizon framework to explain when measurable returns are expected and what the kill-switch criteria are.

**Answer Key:**

a) **Section 1 – Threat Landscape (3 min):** Update on quantum hardware milestones relevant to energy: no fault-tolerant quantum computer yet, but NIST PQC standards are finalized. Energy grid control systems (SCADA, ICS) use cryptographic protocols; quantum risk is real within 10–15 years. Current hardware is NISQ-era; genuinely quantum advantage for commercial applications is 5–10 years out for most use cases. **Section 2 – Regulatory Posture (3 min):** NERC CIP compliance implications of PQC migration; status of our cryptographic inventory (how many systems, which protocols, which migration priority tier); Department of Energy quantum guidance updates; any export control implications for vendor partnerships. **Section 3 – Investment Portfolio (4 min):** Status of Year 1 pilots — grid optimization pilot (Gate 1 passed, Gate 2 in progress), PQC migration roadmap (40% of priority systems identified), quantum literacy training (8 managers certified). Budget vs. actual. **Section 4 – Talent Status (2 min):** Quantum Translator in seat since Month 2; consortium membership active (Quantum Economic Development Consortium); two academic partnerships under evaluation. **Section 5 – Competitive Intelligence (3 min):** Three energy utilities have announced quantum partnerships publicly; one peer company is running a demand-forecasting quantum pilot; no announced production deployments yet in the sector.

b) "The most immediate quantum cyberattack risk to grid control systems is not an attack on our operational technology directly — it is the risk that cryptographic protocols securing grid communications and authentication become vulnerable when cryptographically relevant quantum computers arrive, which current estimates place at 10–15 years out. Our Year 1 PQC migration program is specifically designed to migrate those protocols before that window closes, and our current Mosca Inequality calculation shows we are on track if we maintain the current migration pace."

c) **Part 1 — Option Value Reframe:** "\$1.2M in Year 1 purchased something that does not appear on a balance sheet: the organizational capability to act on quantum opportunities within 18 months of when they become commercially material, rather than spending those 18 months forming a steering committee. We bought a Translator who now gives us the ability to evaluate quantum opportunities with expert judgment rather than vendor marketing. We bought a cryptographic inventory that quantified a risk we did not know we carried. These are option-value investments — they do not produce cash flow today; they produce the right to capture value tomorrow. The TCO analysis shows that the alternative — beginning this program two years from now — would cost \$3–\$4M more to achieve equivalent organizational maturity, because the talent market is tightening and the migration work will be under greater regulatory pressure."

**Part 2 — Three-Horizon Return Timeline:** "Under our three-horizon roadmap, Year 1 is a Horizon 1 investment: its success criteria were building the foundation, not generating revenue. We passed every Gate 1 kill-switch criterion on schedule. Horizon 2 investments — beginning Year 2 — are where we expect to see measurable technical results from pilots. Our 18-month kill-switch criterion is clear: if no quantum pilot demonstrates measurable improvement over its classical baseline by Month 18 of Year 2, we will redirect \$500,000 of the Year 3 pilot budget to accelerate PQC migration instead. We are not asking for unlimited commitment — we are asking the board to evaluate us against the milestones we pre-committed to, not against a standard of immediate financial return that no legitimate quantum investment can currently meet."
