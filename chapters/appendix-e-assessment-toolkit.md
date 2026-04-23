---
title: "Appendix E: Assessment Toolkit"
subtitle: "Complete rubrics, exam structure, and peer-review framework for instructors"
short_title: "Appendix E: Assessment Toolkit"
description: "Complete instructor assessment toolkit: discussion rubric, lab rubrics (regular and advanced), case study rubric, capstone rubric, midterm exam structure, and peer-review framework."
label: appendix-e-assessment-toolkit
tags: [assessment, rubrics, grading, instructor resources, capstone, midterm]
---

# Appendix E: Assessment Toolkit

This appendix collects every grading instrument used in the course. All rubrics are designed to be printed, annotated, and returned to students. Instructors are encouraged to share rubrics with students before each assignment — transparency about expectations improves both performance and trust.

---

## Section 1: Discussion Post Rubric

**Applies to:** All 9 chapter discussion posts  
**Format:** 400-word original post + 2 peer responses (minimum 150 words each)  
**Total Points:** 20 per discussion (each dimension scored 1–4, plus 4 points for peer responses scored as a unit)

### Scoring Grid

```{list-table} Discussion Post Rubric
:header-rows: 1
:widths: 20 20 20 20 20

* - Dimension
  - 4 — Exemplary
  - 3 — Proficient
  - 2 — Developing
  - 1 — Insufficient
* - **Conceptual Accuracy**
  - Applies chapter concepts precisely and correctly; no misattributions; demonstrates command of terminology
  - Applies core concepts correctly with minor imprecision; terminology mostly accurate
  - Applies some concepts but conflates terms or oversimplifies key ideas
  - Misapplies or ignores chapter concepts; relies on vague generalities
* - **Original Analysis**
  - Offers a distinct, reasoned perspective not found in the readings; advances the conversation meaningfully
  - Goes beyond summary; includes a clear personal argument or interpretation
  - Partially summarizes the reading with limited original contribution
  - Restates assigned content with no discernible original thought
* - **Evidence Quality**
  - Cites 2+ credible, specific sources; citations are relevant and correctly attributed
  - Cites 1 credible source; citation is relevant and reasonably formatted
  - References a source vaguely or without proper attribution
  - No sources cited, or sources are non-credible (e.g., vendor marketing, Wikipedia alone)
* - **Professional Communication**
  - Writing is clear, well-organized, and at graduate level; no significant errors
  - Writing is clear and organized; minor grammatical or structural issues
  - Writing is understandable but choppy, informal, or inconsistently organized
  - Writing impedes understanding; frequent errors or inappropriate register
```

**Peer Responses (4 points total, scored as a unit):**

- **4** — Both responses are substantive (150+ words each), directly engage the peer's argument, ask a follow-up question or introduce a counterpoint, and advance the thread
- **3** — Both responses engage meaningfully but one is thinner than expected; or one response is excellent and the other is developing
- **2** — Responses acknowledge the peer's post but do not meaningfully engage with the argument; "great post" syndrome
- **1** — One or both responses are absent, one-sentence, or purely social

### Grade Conversion Table

```{list-table} Discussion Post Grade Conversion
:header-rows: 1
:widths: 40 30 30

* - Total Points (out of 20)
  - Letter Grade
  - Notes
* - 18–20
  - A
  - Exemplary work; peer-share worthy
* - 15–17
  - B
  - Solid graduate-level contribution
* - 12–14
  - C
  - Meets minimum expectations
* - 9–11
  - D
  - Substantially below expectations; feedback required
* - Below 9
  - F
  - Non-submission or academic integrity concern
```

### Sample Post Excerpts

**Exemplary Post (scored 4/4 on Conceptual Accuracy and Original Analysis):**

> "The Chapter 3 reading frames quantum annealing as a heuristic optimizer — useful for combinatorial problems but not a general-purpose speedup. What the case doesn't address is the cost structure: D-Wave's annealers require cryogenic infrastructure that most enterprises cannot amortize over a short planning horizon. I'd argue the real business question isn't whether quantum annealing beats classical solvers on benchmark problems, but whether the total cost of ownership makes sense before 2028. Farhi et al. (2014) demonstrated quadratic speedup for certain NP-hard problems, but the literature is silent on operational overhead. My position: companies should treat annealers as a hedge, not a core platform, until lease-access pricing matures."

*Why it scores well:* The student correctly applies the annealing framing from the chapter, introduces a cost-structure argument not present in the readings, and cites a primary source precisely.

---

**Needs Improvement Post (scored 1–2 on most dimensions):**

> "I thought the chapter was really interesting. Quantum computing is going to change everything in the future. Quantum computers are much faster than regular computers and companies like IBM and Google are working on them. I think businesses should pay attention to this technology because it will be important. I agree with the reading that quantum computing has a lot of potential."

*Why it scores poorly:* Restates general impressions without applying chapter-specific concepts; no sources; no original analysis; no engagement with the productive-struggle question.

---

## Section 2: Lab Rubric (Regular Labs, Chapters 1–9)

**Applies to:** All standard (non-Python) lab deliverables  
**Format:** 1–2 page business memo addressed to a non-technical executive  
**Total Points:** 16 (each dimension scored 1–4)

### Scoring Grid

```{list-table} Regular Lab Rubric
:header-rows: 1
:widths: 20 20 20 20 20

* - Dimension
  - 4 — Exemplary
  - 3 — Proficient
  - 2 — Developing
  - 1 — Insufficient
* - **Technical Execution**
  - All lab steps completed correctly; screenshots or outputs confirm successful execution; no errors present
  - Core steps completed; minor procedural gaps that don't affect conclusions
  - Some steps completed; significant gaps or errors that limit what can be analyzed
  - Lab not meaningfully completed; outputs absent or clearly incorrect
* - **Business Translation**
  - Technical observations are clearly and specifically linked to named business use cases, cost implications, or competitive dynamics; executive reader would understand immediately
  - Business connection is made but somewhat generic ("this could help companies optimize processes")
  - Business connection is attempted but forced or superficial; technical language bleeds through
  - No business connection made; deliverable reads as a technical log only
* - **Analytical Depth**
  - Analysis goes beyond description to interpretation: explains *why* the result matters, identifies constraints, flags assumptions, or compares alternatives
  - Analyzes the result but stays close to the surface; limited "so what?" development
  - Mostly describes what happened rather than analyzing implications
  - No analysis; bullet list of steps or raw outputs with no interpretation
* - **Deliverable Quality**
  - Memo is professionally formatted, audience-appropriate, and polished; correct headers, no spelling errors, concise executive summary
  - Memo is mostly professional with minor formatting or tone inconsistencies
  - Memo has significant formatting issues or inappropriate audience register
  - Not formatted as a memo; missing key structural elements
```

### Grade Conversion

```{list-table} Lab Grade Conversion
:header-rows: 1
:widths: 40 30 30

* - Total Points (out of 16)
  - Letter Grade
  - Notes
* - 14–16
  - A
  - 
* - 11–13
  - B
  - 
* - 8–10
  - C
  - 
* - 5–7
  - D
  - 
* - Below 5
  - F
  - 
```

### Grading Notes: Technical vs. Non-Technical Students

**For non-technical students:** The bar on Technical Execution should reflect effort and accuracy relative to the tools provided, not prior coding or systems knowledge. A non-technical student who completes all IBM Quantum Composer steps correctly and documents them faithfully earns a 4, even if they cannot explain the underlying mathematics. The Business Translation and Analytical Depth dimensions are where non-technical students often outperform their technical peers — reward strong business framing.

**For technical students:** Resist giving automatic 4s on Technical Execution. Technical students sometimes complete the mechanics quickly but write thin memos that assume technical literacy in the reader. Hold them to the same Deliverable Quality standard: if the memo reads like a GitHub README, it is not audience-appropriate for this course. The target audience is always a C-suite executive, not a developer.

**Universal note:** Labs are not graded on whether the quantum circuit produced the "right" answer in a physical sense. Quantum systems are probabilistic. What matters is whether the student ran the circuit, interpreted the probability distribution correctly, and connected it to a business insight.

---

## Section 3: Advanced Lab Rubric (Optional Python Labs)

**Applies to:** Optional advanced Python labs (available for each chapter)  
**Format:** Working Python code + README/memo  
**Total Points:** 20 (each dimension scored 1–4)

### Scoring Grid

```{list-table} Advanced Lab Rubric
:header-rows: 1
:widths: 20 20 20 20 20

* - Dimension
  - 4 — Exemplary
  - 3 — Proficient
  - 2 — Developing
  - 1 — Insufficient
* - **Code Quality**
  - Code runs without errors; clean structure with logical organization; all non-obvious lines commented; variable names are readable
  - Code runs; mostly clean; comments present but incomplete
  - Code runs with minor modifications; structure is hard to follow; comments sparse
  - Code does not run, or runs only with significant instructor intervention; uncommented
* - **Methodological Rigor**
  - Appropriate algorithm or approach chosen for the problem; edge cases handled or acknowledged; parameters are justified
  - Appropriate approach; edge cases not fully addressed but methodology is sound
  - Approach is workable but suboptimal; methodology is not explained
  - Wrong approach for the problem, or methodology is absent
* - **Results Interpretation**
  - Output is correctly interpreted; probability distributions, circuit depths, or optimization metrics are explained in plain language; limitations acknowledged
  - Output is interpreted correctly with minor gaps; limitations not addressed
  - Output is described but not interpreted; student reports numbers without meaning
  - Output is misinterpreted or absent
* - **Business Application**
  - Technical result is connected to a specific, named business scenario with a clear value proposition; includes an estimated order-of-magnitude impact
  - Business connection is made and plausible, but generic
  - Business connection is mentioned but not developed
  - No business application; deliverable is purely technical
* - **Documentation**
  - README or memo is complete and standalone; a new reader could reproduce the results and understand the business context without instructor guidance
  - README is present and mostly complete; minor gaps in reproduction steps
  - README is present but missing key steps or context
  - No documentation, or documentation is a single sentence
```

### Advanced Lab Grade Conversion

```{list-table} Advanced Lab Grade Conversion
:header-rows: 1
:widths: 40 30 30

* - Total Points (out of 20)
  - Letter Grade
  - Bonus Credit Note
* - 18–20
  - A+
  - Full bonus credit awarded
* - 14–17
  - A
  - Partial bonus credit
* - 10–13
  - B
  - Minimal bonus credit
* - Below 10
  - No bonus credit
  - Standard lab grade applies
```

**Instructor Note:** Because these labs are optional and serve advanced learners, do not penalize students who attempt them and fall short. A student who earns 10/20 on an advanced lab should receive partial bonus credit — attempting it demonstrates initiative that the standard lab cannot assess.

---

## Section 4: Case Study Rubric (Graded Cases: Chapters 2, 4, 6, 8)

**Applies to:** Four graded written case analyses  
**Format:** 1,000–1,500 words, submitted as a Word document or PDF  
**Total Points:** 25 (each dimension scored 1–5)

### Scoring Grid

```{list-table} Case Study Rubric
:header-rows: 1
:widths: 20 16 16 16 16 16

* - Dimension
  - 5 — Exemplary
  - 4 — Proficient
  - 3 — Adequate
  - 2 — Developing
  - 1 — Insufficient
* - **Situation Understanding**
  - Correctly and precisely identifies the core problem, stakeholders, constraints, and industry context; no factual errors about the case
  - Correctly identifies the core problem with minor omissions in context or stakeholder analysis
  - Identifies the general situation but misses key constraints or stakeholder dynamics
  - Partially understands the situation; significant factual gaps or misreadings
  - Misidentifies the core problem or demonstrates unfamiliarity with the case
* - **Quantum Angle Analysis**
  - Accurately and specifically explains how the quantum technology in the case works (at a conceptual level), why it was selected for this problem, and what its theoretical advantage is
  - Explains the quantum angle correctly with minor technical imprecision; advantage is described
  - Explains quantum involvement generally but without precision; "quantum is faster" without specifics
  - Attempts to explain the quantum angle but contains significant technical errors
  - Ignores or fundamentally misunderstands the quantum component
* - **Decision Quality Assessment**
  - Evaluates the decisions made in the case using explicit criteria (e.g., risk tolerance, ROI horizon, strategic fit); distinguishes good decisions from lucky outcomes
  - Evaluates decisions with mostly sound criteria; some conflation of process and outcome
  - Describes decisions but does not evaluate them against clear criteria
  - Lists what decisions were made without any evaluative framework
  - Does not engage with the decision-making dimension of the case
* - **Outcome Evaluation**
  - Assesses results with appropriate skepticism; acknowledges what is unknown, what might be vendor hype, and what the data actually supports
  - Assesses results correctly with minor credulity; mostly acknowledges limitations
  - Reports outcomes as stated without questioning sources or limitations
  - Accepts all claims uncritically; no acknowledgment of uncertainty
  - Does not discuss outcomes, or treats marketing claims as established fact
* - **Strategic Recommendation**
  - Offers a specific, defensible recommendation for the Open Question; grounded in course frameworks; acknowledges tradeoffs; could be acted on by a real executive
  - Offers a clear recommendation with minor gaps in justification or tradeoff acknowledgment
  - Offers a recommendation but it is vague, generic, or not grounded in course tools
  - Offers a recommendation that is not defensible or contradicts the case evidence
  - No recommendation, or recommendation is a restatement of the case conclusion
```

### Case Study Grade Conversion

```{list-table} Case Study Grade Conversion
:header-rows: 1
:widths: 40 30 30

* - Total Points (out of 25)
  - Letter Grade
  - Notes
* - 22–25
  - A
  - 
* - 18–21
  - B
  - 
* - 13–17
  - C
  - 
* - 9–12
  - D
  - 
* - Below 9
  - F
  - 
```

### Word Count Compliance

Submissions under 1,000 words are automatically capped at a maximum of 3/5 on Situation Understanding and Quantum Angle Analysis, regardless of quality, because insufficient length typically indicates under-developed analysis. Submissions over 1,500 words are not penalized but instructors should note whether the excess length reflects genuine depth or unfocused writing — if the latter, reduce the Deliverable Quality score accordingly.

---

## Section 5: Capstone Rubric (Chapter 9 Investment Thesis)

**Applies to:** Final capstone — one-page written investment thesis (8 required sections) + 10-minute live pitch  
**Grading Split:** Written Thesis = 60% of capstone grade | Live Pitch = 40% of capstone grade

**The capstone directly assesses FAU Learning Outcome 6:** *"Produce a multi-year quantum adoption roadmap for a real or chosen enterprise, including use case prioritization by paradigm (annealing vs. gate-model), capability building plan, partner selection, governance structure, and measurable outcomes with pre-defined kill-switch criteria."*

**Required thesis sections (all 8 must be present for full credit):**
1. Executive Summary (2 sentences)
2. Dual-Paradigm Three-Horizon Roadmap (table — distinguishes annealing H1 from gate-model H2/H3)
3. Talent Plan
4. Partnership Recommendation (specific named partner + rationale)
5. Budget Breakdown (3-year, by category)
6. Success Metrics (specific, measurable, time-bound)
7. Kill-Switch Criteria (pre-defined stop conditions)
8. Signatures (business sponsor + financial authority + program owner)

---

### Part A: Written Thesis Rubric (60%)

**Total Points:** 30 (each of 6 dimensions scored 1–5)

```{list-table} Capstone Written Thesis Rubric
:header-rows: 1
:widths: 20 16 16 16 16 16

* - Dimension
  - 5 — Exemplary
  - 4 — Proficient
  - 3 — Adequate
  - 2 — Developing
  - 1 — Insufficient
* - **Executive Summary**
  - Two sentences, maximum; immediately communicates the company, the quantum bet, and the expected payoff; a senior executive could act on this
  - Two sentences; communicates the core bet clearly but payoff is vague
  - Two to three sentences; core bet is present but buried or over-qualified
  - More than three sentences; fails to distill the thesis
  - Absent, or so vague as to communicate nothing
* - **Dual-Paradigm Three-Horizon Roadmap**
  - Three horizons with explicit paradigm distinction: H1 includes annealing pilot (D-Wave/QUBO) AND PQC migration; H2 includes gate-model experimentation; milestones are specific, timelines realistic; kill-switch criteria pre-defined
  - Three horizons present; paradigm distinction present but one horizon is underdeveloped
  - Three horizons present but no paradigm distinction — treats "quantum" as monolithic
  - Roadmap is present but has only one or two horizons, or milestones are generic
  - No roadmap, or a single timeline bar with no horizon structure
* - **Talent Plan**
  - Specific roles named (e.g., "one quantum algorithms engineer + two classical ML engineers for Year 1"); proportionate to stated org size; includes a build/buy/partner decision
  - Specific roles named; build/buy/partner is mentioned; minor proportionality issues
  - Roles are categories rather than specifics ("quantum talent"); no build/buy/partner
  - Talent plan is one sentence or a generic hiring intention
  - No talent plan
* - **Budget Breakdown**
  - Line-item budget with justified figures; cloud access, talent, and infrastructure are separated; total is realistic for stated org size; sources for estimates are cited or clearly derivable
  - Budget has line items with reasonable figures; minor justification gaps
  - Budget is present but figures are round numbers with no justification ("\$500K for quantum")
  - Single total figure with no breakdown
  - No budget
* - **Kill-Switch Criteria**
  - Three or more specific, measurable criteria that would trigger program termination; criteria are non-trivial (not "if it doesn't work"); includes a timeline trigger
  - Two or more criteria; specific and measurable; timeline trigger present or implied
  - Criteria present but vague ("if ROI is not achieved") or only one criterion listed
  - Kill-switch section present but criteria are circular or untestable
  - No kill-switch criteria
* - **Course Concept Integration + LO Alignment**
  - Explicitly references at least four distinct course tools from Chapters 1–8 (e.g., Mosca Inequality/STRIDE from Ch5, QUBO formulation from Ch6, industry vertical map from Ch7, five-question governance filter from Ch8); dual-paradigm lens is evident throughout; references substantive, not name-dropping
  - References three course tools; substantive; dual-paradigm lens partially applied
  - References two course tools; or references are superficial; paradigm distinction absent
  - References one course tool or concept
  - No course concepts referenced; thesis could have been written without taking the course
```

**Written Thesis Score → Grade (out of 30):**

```{list-table} Written Thesis Grade Conversion
:header-rows: 1
:widths: 50 50

* - Total Points (out of 30)
  - Letter Grade
* - 27–30
  - A
* - 22–26
  - B
* - 16–21
  - C
* - 10–15
  - D
* - Below 10
  - F
```

---

### Part B: Live Pitch Rubric (40%)

**Total Points:** 25 (each of 5 dimensions scored 1–5)  
**Format:** 10 minutes presentation + 5 minutes Q&A

```{list-table} Capstone Live Pitch Rubric
:header-rows: 1
:widths: 20 16 16 16 16 16

* - Dimension
  - 5 — Exemplary
  - 4 — Proficient
  - 3 — Adequate
  - 2 — Developing
  - 1 — Insufficient
* - **Opening Hook**
  - First 60 seconds earns the room: specific problem, specific stakes, clear reason to listen; no "today I will be presenting about..."
  - Opening is purposeful and relevant; minor reliance on throat-clearing
  - Opening takes 90+ seconds to reach the point; stakes are not communicated
  - Opening is a restatement of the assignment or a slide title read aloud
  - No discernible opening structure; presentation begins without orientation
* - **Quantum Value Proposition**
  - Can articulate in plain language why quantum (not classical) is the right approach for this use case, what the expected advantage is, and when it becomes commercially relevant
  - Value proposition is clear; timing or advantage magnitude is underspecified
  - States that quantum provides an advantage without explaining the mechanism
  - Value proposition is vague or relies on "quantum is the future" framing
  - Cannot articulate a value proposition; relies entirely on slides
* - **Q&A Handling**
  - Handles skeptical questions with composure and substance; acknowledges uncertainty honestly; does not oversell; redirects unanswerable questions appropriately
  - Handles most questions well; one instance of overselling or deflection
  - Handles easy questions; struggles with skeptical or technical follow-ups
  - Becomes defensive or evasive under questioning; or agrees with all challenges without engaging
  - Cannot engage with Q&A; defers all questions without substantive response
* - **Demo Effectiveness**
  - Lab output is directly integrated into the pitch narrative; demo moment is prepared, functional, and interpreted for the audience in real time
  - Lab output is present and explained; minor preparation gaps
  - Lab output is shown but not explained or connected to the thesis
  - Lab is referenced but not shown; or demo fails and no contingency is available
  - No lab integration
* - **Executive Presence**
  - Eye contact, pacing, and confidence are consistent throughout; language is crisp and non-hedging; dress and affect are appropriate for a C-suite presentation
  - Mostly strong presence with 1–2 moments of uncertainty or filler language
  - Adequate delivery; noticeable reliance on notes; some filler language
  - Reads from notes or slides throughout; limited audience engagement
  - Delivery significantly impedes comprehension or engagement
```

**Live Pitch Score → Grade (out of 25):**

```{list-table} Live Pitch Grade Conversion
:header-rows: 1
:widths: 50 50

* - Total Points (out of 25)
  - Letter Grade
* - 22–25
  - A
* - 18–21
  - B
* - 13–17
  - C
* - 8–12
  - D
* - Below 8
  - F
```

**Final Capstone Grade Calculation:**

Written Thesis score (out of 30) × 0.60 = weighted written score  
Live Pitch score (out of 25) × 0.40 = weighted pitch score  
Sum → convert to 100-point scale for gradebook entry

---

## Section 6: Midterm Exam Structure

**Coverage:** Chapters 1–5  
**Recommended Time:** 90 minutes  
**Total Points:** 100

### Format Overview

```{list-table} Midterm Exam Format
:header-rows: 1
:widths: 30 20 20 30

* - Section
  - Weight
  - Points
  - Recommended Time
* - Part A: Multiple-Choice Concept Checks (20 questions)
  - 40%
  - 40 pts (2 pts each)
  - 25 minutes
* - Part B: Short-Answer Framework Applications (3 questions)
  - 30%
  - 30 pts (10 pts each)
  - 35 minutes
* - Part C: Integrative Scenario
  - 30%
  - 30 pts
  - 30 minutes
```

---

### Part A: Multiple-Choice (40 points)

Each question tests a single concept from Chapters 1–5. Write questions at the application level (not recall). Avoid "all of the above" and double-negative constructions.

**Sample Question (Chapter 2 — Quantum Hardware Landscape):**

> A pharmaceutical company is evaluating quantum hardware vendors for a molecular simulation use case. Their chemistry team needs to simulate molecules with more than 50 active electrons. Based on current hardware constraints, which of the following is the most accurate assessment?
>
> A) Gate-based superconducting processors can reliably simulate 50-electron systems today with sufficient error correction.  
> B) Quantum annealers are the preferred platform for molecular simulation because of their low qubit error rates.  
> C) Current NISQ-era hardware lacks the fault-tolerant qubit counts needed for this use case; classical approximation methods remain competitive.  
> D) Photonic quantum computers have already demonstrated commercial viability for molecular simulation at this scale.
>
> **Correct Answer: C**  
> *Rationale: As of the current NISQ era, fault-tolerant quantum simulation of large molecular systems remains beyond available hardware. The question tests students' ability to apply the NISQ constraints framework from Chapter 2 to a realistic business scenario.*

**Grading Guidance (Part A):** Autogradeable. No partial credit. If administering on paper, use a Scantron-style answer sheet. Provide an answer key after all sections are submitted.

---

### Part B: Short-Answer Framework Applications (30 points)

Each question asks students to apply a specific course framework to a brief scenario. Answers should be 150–250 words. Partial credit is appropriate.

**Scoring per question (10 points):**
- **8–10:** Framework correctly identified and applied; answer is specific and grounded in the scenario
- **5–7:** Framework identified; application is partially correct or missing one key element
- **2–4:** Framework is referenced but not applied; answer is generic
- **0–1:** Framework absent; answer is purely factual recall or off-topic

**Sample Question (Chapter 4 — Quantum Optimization):**

> A global airline is considering using quantum annealing to optimize its crew scheduling problem, which involves roughly 50,000 binary decision variables. Using the Technology Readiness Level (TRL) framework discussed in Chapter 4, assess whether this is a near-term (1–3 year), mid-term (3–7 year), or long-term (7+ year) opportunity. Justify your assessment with at least two specific TRL criteria.

**Sample Strong Answer:**

> "This is a mid-term opportunity (3–7 year horizon). Under the TRL framework, a technology earns TRL 4–5 when it has been validated in a relevant environment — not just a lab. Current quantum annealers have demonstrated advantage on problems with fewer than 10,000 binary variables in controlled settings, which places crew scheduling at roughly TRL 3: proof of concept exists, but scaling to 50,000 variables has not been demonstrated in an operationally relevant environment. Additionally, TRL 6 requires a system prototype demonstration — no major airline has yet completed a full-scale production trial. The airline should invest in a scoped pilot (perhaps a regional fleet of 200 aircraft) to advance the TRL, while maintaining its classical optimization infrastructure. A 7-year horizon assumes Moore's Law-like improvement in annealer qubit counts, which is plausible but not guaranteed."

---

### Part C: Integrative Scenario (30 points)

One scenario that spans multiple chapters. Students must identify the relevant quantum concept, assess readiness, identify a business risk, and make a recommendation.

**Scoring (30 points):**
- **Concept identification (8 pts):** Did the student identify the correct quantum approach? Is the identification justified?
- **Readiness assessment (8 pts):** Did the student use a course framework (TRL, NISQ constraints, hardware landscape) to assess feasibility?
- **Risk identification (7 pts):** Did the student identify at least one substantive risk (not just "it might not work")?
- **Recommendation (7 pts):** Is the recommendation specific, actionable, and grounded in the scenario?

**Sample Scenario:**

> FinCorp is a mid-sized investment bank with \$40B AUM. Their CTO has proposed a \$12M investment to build an in-house quantum computing capability, beginning with a focus on portfolio optimization using variational quantum eigensolvers (VQE). The CTO argues that being a "first mover" in quantum finance will yield competitive advantage within 3 years. You are an outside advisor. Write a 300–400 word assessment that: (1) evaluates whether VQE is the appropriate quantum approach for portfolio optimization at this scale, (2) assesses the 3-year timeline claim using at least one course framework, (3) identifies the single greatest risk in this proposal, and (4) offers a specific alternative recommendation.

**Grading Guidance (Part C):** Use the four-part scoring breakdown above. A student who writes a strong risk identification but a weak recommendation should earn partial credit accordingly. Do not penalize students for reaching different conclusions as long as the reasoning is grounded in course frameworks.

---

## Section 7: Peer Review Framework

**Applies to:** Peer responses in all 9 discussion posts  
**When to distribute:** Share with students at the start of the course; remind them before each post is due

Students use this checklist when writing each of their two required peer responses. The checklist should take 5–10 minutes to complete and drives a more substantive response than students would otherwise write.

---

### Peer Review Checklist

Before writing your peer response, read your classmate's post completely. Then work through the following questions. Your response should address at least three of the five items.

**Comprehension Check:**
- [ ] Did the post correctly apply the chapter's core concept? If not, where did it go astray?

**Evidence Check:**
- [ ] Did the post cite at least one credible source? Was the citation relevant and accurately represented?

**Build-On:**
- [ ] What is one thing the post got right that you would build on? Explain *how* you would extend it — not just that it was good.

**Gap Identification:**
- [ ] What is one important question the post left unanswered? This should be a genuine intellectual gap, not a nitpick.

**Your Own Position:**
- [ ] What is *your* position on the chapter's productive-struggle problem? Briefly state where you agree, disagree, or see a third option — and why.

---

### Peer Response Quality Standards

A **strong peer response** (earning full credit on the Peer Engagement dimension):
- Directly quotes or paraphrases the peer's argument before responding to it
- Advances the conversation rather than restarting it
- Introduces new evidence or a counterexample
- Ends with a question that invites further engagement

A **weak peer response** (earning 1–2 on the Peer Engagement dimension):
- Summarizes what the peer said without adding anything
- Offers only affirmation ("I completely agree with your analysis")
- Responds to a peripheral point while ignoring the peer's core argument
- Is under 100 words

---

### Instructor Note on Peer Review Calibration

During Week 1 or Week 2, consider running a live calibration exercise: post two anonymized sample peer responses (one strong, one weak) and ask students to score them using the rubric before class. Discuss the scores. This single exercise dramatically improves the quality of peer engagement throughout the course and eliminates most grade disputes about discussion scoring.

---

## Quick Reference: Assignment Weights

```{list-table} Course Assessment Summary
:header-rows: 1
:widths: 35 20 20 25

* - Assignment Type
  - Number
  - Points Each
  - Total Weight
* - Discussion Posts (with peer responses)
  - 9
  - 20 pts
  - ~180 pts
* - Regular Labs (Chapters 1–9)
  - 9
  - 16 pts
  - ~144 pts
* - Graded Case Studies (Chs. 2, 4, 6, 8)
  - 4
  - 25 pts
  - 100 pts
* - Midterm Exam (Chapters 1–5)
  - 1
  - 100 pts
  - 100 pts
* - Capstone (Written + Pitch)
  - 1
  - 55 pts
  - 110 pts
* - Advanced Labs (Optional Bonus)
  - Up to 9
  - 20 pts
  - Bonus only
```

*Final grading scale is at instructor's discretion. Suggested scale: A = 90–100%, B = 80–89%, C = 70–79%, D = 60–69%, F = below 60%.*

---

*Appendix E prepared for instructor use. All rubrics may be reproduced for course distribution.*
