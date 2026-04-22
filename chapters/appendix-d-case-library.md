---
title: "Appendix D: Supplementary Case Library"
subtitle: "22 additional mini-cases across 8 sectors for discussion, assignments, and deeper exploration"
short_title: "Appendix D: Case Library"
description: "22 supplementary mini-cases beyond the nine flagship cases — covering financial services, pharma, energy, logistics, automotive, aerospace, telecom, and government. Each case follows the Situation → Quantum Angle → Decisions Made → Measured Outcome → Open Question format."
label: appendix-d-case-library
tags: [case studies, financial services, pharma, energy, logistics, automotive, aerospace, telecom, government]
---

# Appendix D: Supplementary Case Library

This appendix contains 22 additional mini-cases organized by industry sector. Each case follows the same five-part structure used throughout the main text: **Situation → Quantum Angle → Decisions Made → Measured Outcome → Open Question**. These cases are designed for discussion board prompts, make-up assignments, or supplementary reading. Each case is grounded in publicly documented events; where outcomes were mixed or disappointing, they are presented honestly.

---

## Section D.1 — Financial Services

### Case D-1: JPMorgan Chase Quantum Research Program

**Situation**

JPMorgan Chase is one of the largest financial institutions in the world, processing trillions of dollars in trades and derivative contracts every day. By 2017, the bank's research division had begun exploring whether quantum computers could solve problems in derivatives pricing and portfolio optimization faster than classical hardware. The core challenge: pricing complex financial instruments requires simulating thousands of possible future market paths simultaneously — a computationally expensive task even with modern GPUs.

**Quantum Angle**

JPMorgan researchers published academic papers describing how quantum amplitude estimation — a technique that can speed up Monte Carlo simulations — might reduce the time needed to price options and other derivatives. Their 2020 paper with IBM outlined a pathway toward a quadratic speedup over classical Monte Carlo methods, meaning a problem that takes one million simulation steps classically might take only one thousand on a quantum computer. That would be transformative for real-time trading desks.

**Decisions Made**

The bank joined IBM's Q Network, giving researchers access to IBM's cloud-based quantum hardware. They hired a dedicated team of quantum computing researchers and published their work openly, building academic credibility while recruiting talent. Crucially, JPMorgan chose a research-first posture: no production deployment targets were set, and the work remained in the lab rather than being integrated with trading systems.

**Measured Outcome**

As of 2024, no JPMorgan quantum algorithm has entered production trading. The published research demonstrated that quantum amplitude estimation works in theory and on small test cases, but current quantum hardware — with its noise, limited qubit counts, and short coherence times — cannot yet handle the scale needed for real derivatives books. The gap between a clean academic result and a production-grade trading system remains wide.

**Open Question**

JPMorgan chose to publish its quantum research openly, which helped recruit talent but also shared its intellectual work with competitors. Was that the right strategic call? At what point should financial firms shift from open research to proprietary development in quantum computing?

---

### Case D-2: Goldman Sachs Monte Carlo Acceleration

**Situation**

Goldman Sachs faces a similar challenge to JPMorgan: pricing exotic financial derivatives requires running millions of Monte Carlo simulations, and faster pricing can mean better margins and lower risk. By 2020, Goldman's quantitative research team was investigating whether quantum computers could outperform the GPU clusters already in use for this purpose. GPUs had already delivered meaningful speedups over CPU-based Monte Carlo — the question was whether quantum could beat GPUs.

**Quantum Angle**

Goldman Sachs researchers, working with QC Ware, published a 2021 analysis of quantum amplitude estimation for options pricing. Their central finding was nuanced: yes, quantum could theoretically achieve a quadratic speedup over classical Monte Carlo, but the crossover point — where quantum becomes faster than a well-optimized GPU cluster — required fault-tolerant quantum hardware with roughly one million physical qubits. No such hardware exists today or is expected within the near term.

**Decisions Made**

Goldman invested in QC Ware as a strategic partner and continued publishing research while also maintaining its GPU infrastructure. Unlike some firms that framed quantum as an imminent disruption, Goldman's public communications were measured: their researchers explicitly noted that quantum advantage for Monte Carlo would require hardware advances not yet on the horizon.

**Measured Outcome**

The research collaboration produced credible academic work that sharpened the field's understanding of when quantum would actually beat classical hardware. Goldman's honest accounting of the crossover point is now widely cited as a benchmark. In the meantime, the firm continued investing in GPU-based acceleration, which delivered real, immediate performance gains. Quantum remains a future option, not a current tool.

**Open Question**

Goldman Sachs was unusually candid about how far away practical quantum advantage actually is. Should more firms adopt this kind of transparency, or does public honesty about quantum limitations reduce the pressure to keep investing in the technology before it matures?

---

### Case D-3: HSBC Post-Quantum Cryptography Pilot

**Situation**

HSBC operates in more than 60 countries, running payment systems that handle hundreds of billions of dollars per day. Like all major banks, its security infrastructure relies on public-key cryptography — the mathematical locks that protect transactions, customer data, and interbank communications. In 2022, following NIST's announcement of its post-quantum cryptography (PQC) finalists, HSBC began assessing its exposure to the quantum cryptography threat and launched one of the earliest PQC pilot programs in global banking.

**Quantum Angle**

The threat is not theoretical but is also not immediate. A sufficiently powerful quantum computer running Shor's algorithm could break RSA and elliptic curve encryption — the two algorithms that underpin most of HSBC's cryptographic security. While that hardware does not exist today, encrypted data stolen now could be decrypted later once it does exist. Banks with long-lived secrets — trade finance documents, regulatory filings, client data with decades of sensitivity — face a harvest-now, decrypt-later risk that demands action before quantum computers arrive.

**Decisions Made**

HSBC partnered with IBM Quantum Safe and PQShield to inventory its cryptographic assets: every certificate, every encrypted connection, every protocol that would need to be replaced in a migration. This certificate discovery phase revealed that HSBC had thousands of cryptographic dependencies spread across legacy systems, cloud environments, and third-party integrations. The bank chose to prioritize high-sensitivity, long-lived data first, and to begin hybrid deployments — running both classical and PQC algorithms in parallel during the transition.

**Measured Outcome**

By 2023, HSBC had published findings on its pilot, noting that the discovery phase was harder than expected. Many legacy systems had no documentation of where encryption was applied, and some third-party vendors had no PQC migration plans at all. The pilot highlighted a systemic problem across the industry: the technical work of replacing cryptographic algorithms is tractable, but the organizational challenge of inventorying and coordinating across thousands of systems is enormous.

**Open Question**

HSBC found that third-party vendors — not its own internal systems — were the hardest part of the migration. Should banks require PQC readiness as a condition of vendor contracts today, even though the quantum threat is still years away? What is the right timeline to impose such requirements?

---

### Case D-4: A Hedge Fund's Quantum-Inspired Factor Model

**Situation**

A mid-sized quantitative hedge fund managing roughly \$8 billion in assets was searching for an edge in factor selection — the process of identifying which market variables (momentum, value, volatility, etc.) best predict future returns. Classical optimization tools had been used for years to build factor models, but as the number of candidate factors grew into the hundreds, finding the optimal combination became computationally expensive and prone to overfitting. In 2021, the fund began testing quantum-inspired annealing tools as an alternative.

**Quantum Angle**

Quantum-inspired annealing uses algorithms derived from quantum physics — specifically the concept of quantum tunneling — but runs on classical hardware. Companies like Fujitsu (Digital Annealer) and Toshiba (Simulated Bifurcation Machine) offer these tools as cloud services. The fund hypothesized that quantum-inspired annealing might navigate the complex landscape of factor combinations more efficiently than gradient-based optimization, potentially finding better-performing portfolios with less computational effort.

**Decisions Made**

The fund ran a six-month pilot using Fujitsu's Digital Annealer, framing factor selection as a quadratic unconstrained binary optimization (QUBO) problem. They benchmarked the quantum-inspired results against their existing classical optimizer on the same historical data. The pilot was structured as an A/B test: the quantum-inspired model's recommended factor combinations were evaluated against the classical baseline on out-of-sample performance.

**Measured Outcome**

Results were mixed. On some factor universes — particularly those with strong combinatorial structure — the quantum-inspired annealer found marginally better combinations than the classical optimizer. On others, performance was equivalent. The computational speed advantage was real: the annealer solved certain problem sizes faster than the classical tool. However, out-of-sample trading performance showed no statistically significant improvement. The fund concluded that the optimization problem was not the binding constraint on alpha generation, and did not expand the program.

**Open Question**

The fund found that quantum-inspired optimization worked technically but did not improve trading performance, because the optimization step was not the bottleneck. How should firms evaluate quantum or quantum-inspired tools when the technology performs as advertised but the business problem it solves turns out not to be the real constraint?

---

## Section D.2 — Pharmaceutical & Life Sciences

### Case D-5: Pfizer's Quantum Computing Exploration

**Situation**

Drug discovery is fundamentally a chemistry problem: finding molecules that bind to biological targets in exactly the right way to treat disease. Classical computers can simulate small molecules reasonably well, but as molecular complexity increases, the simulation problem grows exponentially. Pfizer, one of the world's largest pharmaceutical companies, began exploring quantum computing partnerships around 2020, motivated by the possibility that quantum simulation could accelerate the early stages of drug discovery.

**Quantum Angle**

Quantum computers are naturally suited to simulating quantum systems — and molecules are quantum systems. A quantum computer running the variational quantum eigensolver (VQE) algorithm can, in theory, calculate the energy states of molecules that are too complex for classical hardware to model accurately. For drug discovery, that means potentially predicting how a candidate molecule will behave before spending money on laboratory synthesis and testing.

**Decisions Made**

Pfizer structured its quantum engagement as a research partnership rather than an internal program. It collaborated with quantum software firms and entered joint research agreements with hardware providers, including IBM. The agreements were structured around specific computational chemistry use cases rather than open-ended exploration. Pfizer also joined industry consortia to share the cost and risk of early-stage quantum research across the pharmaceutical sector.

**Measured Outcome**

By 2023, Pfizer had not reported any drug candidates identified with the help of quantum simulation. The research collaborations produced technical publications and proof-of-concept demonstrations, but the molecular sizes needed for pharmaceutical relevance — proteins with thousands of atoms — remain far beyond what current quantum hardware can simulate. The partnership structure, however, gave Pfizer meaningful insight into the technology's trajectory without requiring large internal investments in hardware.

**Open Question**

Pfizer chose to access quantum capability through partnerships rather than building it internally. Given the early stage of the technology, was this the right governance model? What are the risks of depending on external partners for a technology that could eventually become a core competitive advantage?

---

### Case D-6: Merck KGaA Quantum Chemistry Pipeline

**Situation**

Merck KGaA (the German company, not the US Merck) is a science and technology company spanning pharmaceuticals, life science tools, and specialty chemicals. In 2021, Merck KGaA publicly committed to building a quantum computing capability, with a focus on computational chemistry for drug discovery and materials science. They announced a multi-year program with an internal quantum team and partnerships with IBM and several quantum software companies.

**Quantum Angle**

Merck KGaA's target application was quantum chemistry: using quantum algorithms to calculate molecular properties more accurately than classical density functional theory (DFT) methods. Better molecular property predictions could reduce the number of laboratory experiments needed to validate drug candidates, shortening the discovery pipeline and reducing costs. Their published roadmap envisioned progressing from small-molecule simulations on near-term hardware to pharmaceutical-scale simulations on future fault-tolerant systems.

**Decisions Made**

Merck KGaA invested in building internal quantum expertise — hiring quantum chemists and software engineers — while simultaneously running external collaborations. They published research benchmarking quantum algorithms against classical methods on small molecules. Their communications were aspirational but relatively honest about timelines: they acknowledged that pharmaceutical-scale quantum advantage was a decade or more away.

**Measured Outcome**

By 2024, Merck KGaA's published results showed quantum algorithms performing comparably to (but not yet better than) classical methods on the small molecules they could simulate. The gap between available qubits and the qubit count needed for drug-relevant simulations remained large. However, the internal expertise built during this period was considered valuable: Merck KGaA positioned itself as one of the more quantum-literate pharmaceutical firms in Europe.

**Open Question**

Merck KGaA's timeline for useful quantum chemistry was measured in decades, not years. Is it rational for a pharmaceutical company to invest meaningfully in a technology that will not improve its core products within a typical strategic planning horizon? What justifies early investment in very-long-horizon technologies?

---

### Case D-7: Roche Quantum Partnership

**Situation**

Roche, the Swiss pharmaceutical and diagnostics giant, operates in one of the most heavily regulated industries in the world. Any computational tool that influences drug development must meet rigorous validation standards — algorithms must be reproducible, auditable, and documented in ways that satisfy regulatory bodies like the FDA and EMA. When Roche began exploring quantum computing in 2020, this regulatory reality shaped how they approached partnerships and what they were willing to commit to.

**Quantum Angle**

Roche's interest centered on quantum simulation for molecular biology and protein folding — areas where classical simulation has known limitations and where better models could accelerate target identification and lead optimization. They also tracked quantum machine learning, though with more skepticism than enthusiasm, given the limited evidence for quantum advantage in ML tasks.

**Decisions Made**

Roche structured its quantum engagement carefully, treating it as exploratory research with clear firewalls between quantum experiments and any validated drug development workflows. They partnered with Cambridge Quantum (now Quantinuum) on specific computational chemistry problems and published results jointly. The key governance decision was to maintain quantum work in a research sandbox, explicitly separated from any pipeline that touched regulatory submissions.

**Measured Outcome**

The Roche-Quantinuum collaborations produced published research on quantum natural language processing and quantum chemistry, but no quantum-assisted molecule entered Roche's development pipeline as of 2024. The regulatory firewall proved both a protection and a constraint: it kept quantum work from contaminating validated processes, but also meant that any eventual transition from research to production would require a full validation cycle — adding years to any practical deployment.

**Open Question**

Roche's regulatory environment forced them to treat quantum as permanently separate from production workflows until validation requirements can be met. Does heavy regulation slow quantum adoption in pharma, or does it actually protect the industry from deploying immature technology prematurely? Is the regulatory firewall a bug or a feature?

---

## Section D.3 — Energy & Utilities

### Case D-8: ExxonMobil Maritime Logistics Optimization

**Situation**

ExxonMobil operates one of the world's largest fleets of liquefied natural gas (LNG) tankers, moving fuel between production facilities, terminals, and customers across six continents. Scheduling these ships — deciding which vessel goes where, when, and carrying what load — is a combinatorial optimization problem with thousands of variables: vessel speeds, port availability windows, fuel costs, contractual obligations, and weather routing. Even with classical optimization software, ExxonMobil's schedulers regularly faced problems too large to solve to true optimality.

**Quantum Angle**

In 2019, ExxonMobil announced a collaboration with IBM to explore quantum optimization for its LNG fleet scheduling. The problem was framed as a variant of the vehicle routing problem (VRP), a class of optimization challenges that quantum annealing and QAOA (Quantum Approximate Optimization Algorithm) are theoretically well-suited to attack. The collaboration was one of the most prominent industrial quantum partnerships announced that year.

**Decisions Made**

ExxonMobil and IBM ran experiments on IBM's quantum hardware, testing quantum optimization approaches against classical benchmarks on representative scheduling scenarios. ExxonMobil's operations research team was involved in defining the problem formulations, ensuring that the quantum experiments addressed real operational constraints rather than simplified toy problems.

**Measured Outcome**

By 2022, ExxonMobil reported that the quantum approaches tested did not outperform classical optimization solvers on their LNG scheduling problems. The classical solvers — running on ordinary computing hardware — found better solutions faster. ExxonMobil's researchers published honest assessments noting that quantum hardware was not yet competitive for this class of problem. However, they also noted that the collaboration gave the company deep familiarity with quantum optimization techniques that would be valuable as hardware matured.

**Open Question**

ExxonMobil's quantum experiment failed to beat classical solvers, yet the company described the collaboration as valuable for organizational learning. How should executives evaluate the ROI of quantum experiments that produce negative technical results but positive learning outcomes? Is "we learned it doesn't work yet" a sufficient return on investment?

---

### Case D-9: Shell Quantum Chemistry for Catalysts

**Situation**

Shell's refining and chemicals business depends on catalysts — substances that speed up chemical reactions without being consumed in the process. Better catalysts can improve the yield and efficiency of refining operations, reducing costs and emissions. Designing better catalysts requires understanding how electrons behave at the molecular level, which is exactly the kind of problem quantum computers are designed to address. Shell began exploring quantum chemistry for catalyst design around 2021.

**Quantum Angle**

Classical computational chemistry tools — density functional theory (DFT) and molecular dynamics simulations — can model catalyst behavior, but with known accuracy limitations, especially for transition-metal complexes commonly used in refining. Quantum computers running VQE or quantum phase estimation algorithms could, in principle, calculate molecular electronic structures with higher accuracy than classical methods, potentially predicting which catalyst designs would perform best before laboratory testing.

**Decisions Made**

Shell partnered with multiple quantum computing providers and joined IBM's quantum network. Rather than pursuing a single vendor relationship, Shell maintained a portfolio approach: tracking developments from IBM, IonQ, and quantum software companies simultaneously. They also invested in building internal quantum literacy, training chemists and engineers on the basics of quantum algorithms so they could meaningfully evaluate vendor claims.

**Measured Outcome**

Shell's internal assessments concluded that current quantum hardware can simulate catalyst molecules with only a handful of atoms — far smaller than the industrially relevant catalysts they use in actual refining. The capability gap is not marginal: a commercially relevant simulation might require hundreds of logical qubits, while today's hardware provides tens of noisy physical qubits with limited fidelity. Shell's published position is that quantum chemistry for catalysts is a genuine long-term opportunity but is at least ten years from commercial relevance.

**Open Question**

Shell is maintaining a quantum portfolio across multiple vendors rather than committing deeply to one partner. What are the tradeoffs of this diversified approach versus concentrating investment with a single partner who might develop deeper expertise specific to Shell's problems?

---

### Case D-10: A European Grid Operator's Quantum Dispatch

**Situation**

A major European electricity grid operator — responsible for balancing supply and demand across a national power grid in real time — faced a growing optimization challenge. The rise of renewable energy, particularly wind and solar, had made grid dispatch more complex: instead of scheduling a handful of large, controllable power plants, operators now needed to coordinate hundreds of distributed generators with variable and unpredictable output. Classical optimization tools, designed for a simpler grid, were struggling with the new complexity.

**Quantum Angle**

Grid dispatch optimization — deciding which generators to run, at what output level, to meet demand at minimum cost while respecting transmission constraints — is a variant of the unit commitment and economic dispatch problem. It is a known hard combinatorial optimization problem. Quantum annealing, particularly using D-Wave systems, had been proposed as a potential approach, and the grid operator launched a pilot in 2022 to test whether quantum annealing could improve dispatch decisions.

**Decisions Made**

The pilot was structured as a comparison: quantum annealing solutions for a representative dispatch problem versus the operator's existing mixed-integer programming (MIP) solver. The problem was scaled down from full-grid complexity to a test case with approximately 50 generators and a 24-hour scheduling horizon. Results were evaluated on solution quality (total cost of dispatch) and computation time.

**Measured Outcome**

The quantum annealing approach produced feasible solutions but did not match the solution quality of the classical MIP solver on the test case. The quantum results were approximately 3–7% more expensive on average. Computation time was comparable. The operator concluded that quantum annealing was not ready for production dispatch and did not advance the pilot. They noted, however, that the hybrid quantum-classical approaches being developed by D-Wave and others showed more promise and warranted continued monitoring.

**Open Question**

The grid operator's pilot produced a clear answer: not yet. But the grid dispatch problem is growing harder as renewable penetration increases. At what point — in terms of hardware capability or grid complexity — would it make sense to revisit quantum optimization for grid dispatch? How should utilities build quantum monitoring into their long-term planning without over-investing prematurely?

---

## Section D.4 — Logistics & Supply Chain

### Case D-11: DHL Last-Mile Routing Optimization

**Situation**

DHL Express delivers millions of parcels daily across more than 220 countries. The "last mile" — the final leg of delivery from a local depot to the customer's door — is the most expensive part of the logistics chain, accounting for roughly 40–50% of total delivery costs. Optimizing routes for thousands of drivers across dense urban environments, while accounting for time windows, vehicle capacities, and traffic, is a variant of the vehicle routing problem with time windows (VRPTW) — one of the hardest classes of combinatorial optimization.

**Quantum Angle**

DHL's Trend Research division published a quantum computing report in 2021 identifying route optimization as one of the most promising near-term applications for quantum or quantum-inspired computing. The hypothesis was that quantum algorithms — or quantum-inspired classical algorithms derived from quantum physics — might find better routes than conventional heuristic solvers, translating into fewer vehicle miles traveled, lower fuel costs, and faster deliveries.

**Decisions Made**

DHL ran pilots using quantum-inspired optimization tools, including D-Wave's Leap cloud platform, on representative last-mile routing scenarios. They also benchmarked commercial quantum-inspired solvers from companies like Fujitsu against their existing classical routing software. The pilots were focused on realistic urban delivery scenarios — not toy problems — to ensure results were operationally meaningful.

**Measured Outcome**

DHL's pilots showed that quantum-inspired solvers performed comparably to, but did not consistently outperform, state-of-the-art classical solvers on last-mile routing. For some problem instances — particularly those with dense time-window constraints — quantum-inspired methods found marginally better solutions. For others, classical solvers were faster and produced equal or better routes. DHL concluded that quantum-inspired tools were a useful addition to its optimization toolkit but not a step-change improvement. Full quantum hardware remains a future prospect.

**Open Question**

Last-mile routing affects DHL's costs, carbon emissions, and customer satisfaction simultaneously. If a quantum or quantum-inspired solver consistently found routes just 2–3% more efficient, would that be sufficient to justify replacing existing systems? How should logistics firms set the performance threshold for adopting new optimization technology?

---

### Case D-12: Airbus Quantum Route Optimization

**Situation**

Airbus faces optimization challenges at multiple levels of its operations: designing aircraft, manufacturing parts, scheduling assembly lines, and operating flights. By 2020, Airbus's innovation division had identified gate assignment and flight path optimization as particularly promising quantum computing candidates. Gate assignment — deciding which aircraft parks at which gate at an airport — is a combinatorial problem involving hundreds of flights, dozens of gates, turnaround time constraints, and connecting passenger flows.

**Quantum Angle**

Airbus collaborated with quantum computing companies including Zapata Computing, IonQ, and others through its Quantum Computing Challenge program, launched in 2019. The challenge invited teams to formulate Airbus's real operational optimization problems as quantum-ready problem instances and test them on available hardware. Gate assignment was one of the primary use cases, along with wingbox design optimization and aircraft loading.

**Decisions Made**

Airbus structured the program as an open innovation contest rather than a closed vendor negotiation. Teams from universities and startups competed to develop the best quantum formulations for each problem. Airbus provided real problem data — sanitized but representative of actual operational complexity. Winners received prize money and the opportunity to develop their solutions further with Airbus teams.

**Measured Outcome**

The contest results, published in 2020 and 2021, demonstrated that the quantum formulations were technically sound — the problems could be expressed as quantum optimization tasks — but that current hardware could not solve them at operational scale. The best-performing solutions used hybrid quantum-classical approaches, where quantum processors handled subcomponents of the optimization while classical solvers handled the full problem. Airbus documented modest efficiency gains in simulation, but nothing that could be deployed in an actual operations center today.

**Open Question**

Airbus used an open innovation model — a public contest — to accelerate quantum formulation of its problems. What are the risks of this approach compared to confidential partnerships? Does crowdsourcing quantum problem formulation give competitors useful information about Airbus's operational constraints?

---

### Case D-13: A Retail Chain's Cold Chain Scheduling

**Situation**

A large European grocery retailer operates hundreds of distribution centers and thousands of stores, moving temperature-sensitive products — fresh produce, dairy, frozen foods — through a cold chain network that must maintain strict temperature bands while minimizing delivery costs and reducing food waste. Scheduling refrigerated vehicles and warehouse operations involves thousands of variables and hard constraints. When the retailer's operations research team began exploring quantum-inspired optimization in 2022, they made a deliberate choice: they would use cloud-based quantum-inspired tools and spend \$0 on quantum hardware.

**Quantum Angle**

The retailer's team recognized that fully quantum hardware was not ready for their problem scale. Instead, they investigated quantum-inspired annealing — specifically Toshiba's Simulated Bifurcation Machine (SBM), accessible as a cloud API — as a potential improvement over their existing classical integer programming solver. The cold chain scheduling problem was formulated as a QUBO and submitted to the SBM in batches.

**Decisions Made**

The \$0 hardware decision was conscious and strategic: by using cloud APIs, the retailer avoided capital expenditure while still accessing state-of-the-art optimization technology. The team built a comparison framework — running the same scheduling scenarios through the classical solver and the quantum-inspired solver and measuring solution cost, constraint violations, and computation time. The pilot ran for four months across three distribution regions.

**Measured Outcome**

For high-complexity scenarios — distribution days with many overlapping time windows and multiple temperature zones — the quantum-inspired solver found solutions with approximately 4% lower estimated cost than the classical solver, within comparable computation time. The retailer expanded the pilot to two additional regions and began integrating the quantum-inspired solver as a parallel option in its scheduling system. This is one of the clearer documented cases of quantum-inspired tools delivering measurable operational value without any quantum hardware investment.

**Open Question**

The retailer achieved real improvement by using quantum-inspired tools on classical hardware, with no quantum investment at all. Does this outcome argue for or against investing in actual quantum hardware? Is "quantum-inspired without quantum" a permanent strategy or a stepping stone?

---

## Section D.5 — Automotive & Manufacturing

### Case D-14: BMW Hydrogen Fuel Cell Chemistry

**Situation**

BMW is investing heavily in hydrogen fuel cell vehicles as one potential path to zero-emission transportation, alongside battery electric vehicles. Hydrogen fuel cells convert hydrogen gas to electricity through a chemical reaction, with water as the only byproduct. The efficiency and durability of a fuel cell depend critically on the materials used in its membrane electrode assembly — particularly the catalyst layer, which typically relies on expensive platinum. Finding cheaper, equally effective catalyst materials is a central challenge in making hydrogen vehicles commercially viable.

**Quantum Angle**

Identifying better catalyst materials requires simulating how candidate molecules interact at the quantum mechanical level — how electrons are shared, how bonds form and break, how energy flows through the reaction. These are precisely the calculations that quantum computers, running chemistry algorithms like VQE, are theoretically better suited to perform than classical hardware. BMW partnered with quantum software and hardware companies to explore whether quantum simulation could accelerate catalyst discovery for its hydrogen program.

**Decisions Made**

BMW joined IBM's quantum network and also partnered with quantum chemistry specialists to formulate the catalyst discovery problem in quantum-ready terms. The partnership structure was carefully designed: BMW contributed domain knowledge about fuel cell chemistry requirements while quantum partners contributed algorithmic expertise. BMW also joined the Quantum Technology and Application Consortium (QUTAC), a German industry group that shares quantum research costs across multiple companies.

**Measured Outcome**

As of 2024, no new fuel cell catalyst material has been identified or developed with quantum simulation at BMW. Current quantum hardware can simulate the electronic structure of molecules with a handful of atoms — far smaller than the complex organometallic compounds relevant to fuel cell catalysis. BMW's public communications acknowledge this gap honestly while maintaining the partnerships as a strategic investment in future capability.

**Open Question**

BMW is pursuing both battery and hydrogen vehicle strategies simultaneously, with quantum computing as a potential tool for the hydrogen path. If quantum chemistry tools don't mature in time to accelerate hydrogen development, does the hydrogen program face a compounding timeline risk? How should automakers account for dependent technology risks — where one emerging technology (quantum) is needed to accelerate another (hydrogen)?

---

### Case D-15: Volkswagen Production Scheduling

**Situation**

Volkswagen's quantum computing journey is best known for its 2019 Lisbon traffic optimization demonstration, but the company's ambitions extended beyond traffic into its own manufacturing operations. Volkswagen produces vehicles across dozens of plants globally, each running complex assembly lines where sequencing decisions — the order in which vehicles of different configurations move through the line — have major implications for cost, efficiency, and quality. Production scheduling at this scale is a combinatorial problem that classical tools solve heuristically, never optimally.

**Quantum Angle**

Volkswagen extended its quantum optimization work, initially done with D-Wave for the Lisbon traffic project, into factory scheduling research. The core idea was the same: express the sequencing problem as a QUBO, submit it to a quantum annealer or gate-based quantum processor, and compare results to classical heuristics. The specific challenge in auto manufacturing is the "car sequencing problem" — finding the order that minimizes constraint violations as different vehicle configurations require different assembly resources.

**Decisions Made**

Volkswagen established an internal quantum computing team and partnered with D-Wave, IBM, and later Google on different aspects of the manufacturing optimization problem. Rather than committing to a single hardware platform, they maintained a portfolio of experiments across annealing and gate-based systems. They also published research on hybrid quantum-classical approaches for scheduling, contributing to the academic literature while building internal capability.

**Measured Outcome**

Volkswagen's factory scheduling quantum experiments, as of 2024, showed results similar to the traffic project: quantum approaches could find feasible solutions, but classical solvers — particularly modern MIP solvers and heuristic algorithms — matched or outperformed quantum results on problem sizes relevant to actual production lines. The company has not deployed quantum scheduling in any production plant. The work contributed to Volkswagen's reputation as a quantum-engaged manufacturer, with accumulated expertise that positions them well for future hardware improvements.

**Open Question**

Volkswagen has now run quantum optimization experiments in two domains — traffic and manufacturing scheduling — and neither has reached production. At what point does continued investment in quantum optimization become hard to justify internally? How should manufacturing executives frame quantum investments to boards and shareholders when results consistently lag classical solvers?

---

### Case D-16: Ford Battery Materials Simulation

**Situation**

Ford's transition to electric vehicles depends critically on battery technology. The cost, range, and longevity of an EV battery are determined by its chemistry — specifically the materials used in the cathode, anode, and electrolyte. Ford's strategy required either sourcing battery cells from established suppliers (primarily Korean and Chinese manufacturers) or developing proprietary battery chemistry that could differentiate its vehicles. By 2022, Ford was exploring whether quantum simulation could accelerate its materials research program.

**Quantum Angle**

Battery materials research is a quantum chemistry problem at its core: understanding how lithium ions move through electrode materials, how materials degrade over charge cycles, and how new chemistries might store more energy requires modeling electron behavior at the molecular scale. Classical DFT simulations can model these systems approximately, but with known accuracy limits — particularly for the complex transition-metal oxides used in advanced cathode materials. Quantum computers running more accurate algorithms could, in principle, provide better predictions.

**Decisions Made**

Ford invested in quantum computing exploration through its Ford Pro division and via strategic partnerships with national laboratories and quantum hardware companies. The company also joined a Department of Energy quantum computing initiative that provided access to advanced hardware at national labs. Ford's approach was to fund quantum chemistry research as part of a broader battery R&D portfolio, treating quantum as one of several parallel paths toward better battery materials.

**Measured Outcome**

Ford has not announced any battery material breakthrough attributable to quantum simulation. The technical barriers are identical to those facing other automotive companies: current hardware cannot simulate the relevant molecular systems at useful accuracy. However, Ford's participation in DOE quantum programs gave the company access to some of the most advanced quantum hardware available, and the collaborative model reduced the direct cost of the exploration.

**Open Question**

Ford is simultaneously licensing battery technology from partners and investing in long-horizon quantum-assisted materials research. Is this an appropriate hedge, or are the two strategies fundamentally in tension — one providing near-term capability while the other distracts from it? How should legacy automakers balance immediate competitive needs against very long-term technology bets?

---

## Section D.6 — Aerospace & Defense

### Case D-17: Lockheed Martin Quantum Sensing

**Situation**

Lockheed Martin is one of the largest defense contractors in the world, building fighter jets, satellites, missile systems, and navigation equipment. In the quantum domain, Lockheed attracted attention not for quantum computing, but for quantum sensing — a related but distinct application of quantum physics. Quantum sensors exploit the extreme sensitivity of quantum systems to measure physical quantities — magnetic fields, acceleration, gravity — with far greater precision than classical sensors. For navigation, this matters enormously: quantum inertial sensors could allow submarines and aircraft to navigate without GPS signals that can be jammed or spoofed.

**Quantum Angle**

Lockheed Martin invested in quantum sensing research through its own labs and via acquisition of quantum technology companies. Quantum accelerometers and quantum gyroscopes use the behavior of atoms cooled to near absolute zero to measure motion with extraordinary precision. Unlike GPS-dependent navigation, quantum inertial navigation requires no external signal — it works underground, underwater, in GPS-denied environments, and cannot be electronically jammed.

**Decisions Made**

Lockheed funded internal quantum sensing R&D and also invested in quantum sensing startups through its venture arm, Lockheed Martin Ventures. The company distinguished clearly in its public communications between quantum sensing (near-term, hardware-ready) and quantum computing (longer-term), allocating different risk profiles and timelines to each. This distinction was important for communicating credibly with both technical staff and government customers.

**Measured Outcome**

Quantum sensing moved closer to deployment than quantum computing for Lockheed. By 2023, quantum inertial navigation systems were being tested in laboratory environments and in limited field trials. While not yet fielded in production military platforms, the technology was significantly more mature than quantum computing for the company's use cases. Lockheed's ability to separate the two quantum domains — sensing vs. computing — and communicate honestly about their different readiness levels was noted as a model for technology portfolio management.

**Open Question**

Lockheed's experience suggests that "quantum sensing" and "quantum computing" are often conflated in media coverage and executive briefings, but have very different near-term utility. How should organizations ensure that quantum sensing opportunities are not missed while waiting for quantum computing to mature — and vice versa? Who in an organization should own the distinction?

---

### Case D-18: NASA Quantum Optimization for Mission Planning

**Situation**

NASA's mission planning challenges are uniquely complex: calculating optimal trajectories for spacecraft involves navigating gravitational fields of multiple bodies, fuel constraints, mission objective tradeoffs, and timing windows that may only open once per decade. Classical trajectory optimization is computationally intensive, and some mission planning scenarios — particularly those involving multiple flybys, gravity assists, and dynamic retargeting — push the limits of classical solvers. NASA's Ames Research Center began collaborating with D-Wave on quantum optimization for these problems in the early 2010s, making it one of the longest-running enterprise quantum experiments.

**Quantum Angle**

NASA used D-Wave's quantum annealer — one of the first industrial quantum systems commercially available — to test optimization problems including mission scheduling, communication network routing for deep space assets, and machine learning classification tasks for image analysis. The NASA-Ames research program was part of the Quantum Artificial Intelligence Laboratory (QuAIL), a partnership with Google and USRA.

**Decisions Made**

NASA committed to a long-term research posture, treating the D-Wave system as a research instrument rather than an operational tool. The QuAIL program ran controlled experiments comparing D-Wave results to classical optimization benchmarks, publishing findings in academic journals. This gave the program scientific credibility but also documented, in peer-reviewed literature, the cases where D-Wave did not outperform classical solvers.

**Measured Outcome**

QuAIL's published research over a decade showed a nuanced picture: for some problem structures, D-Wave found competitive solutions; for others, classical solvers performed better. The most honest summary of the research is that D-Wave's quantum annealer showed no consistent, reliable advantage over well-tuned classical algorithms for the problems NASA tested. However, the research program contributed significantly to the scientific understanding of quantum annealing's capabilities and limitations — a genuine contribution even without a production deployment.

**Open Question**

NASA's decade-long quantum experiment produced scientific insight but no operational deployment. Is a decade an appropriate timescale for evaluating an emerging technology? How should government agencies set patience thresholds for long-horizon technology investments compared to commercial firms?

---

## Section D.7 — Telecommunications

### Case D-19: BT Group Post-Quantum Cryptography Migration

**Situation**

BT Group (formerly British Telecom) is one of the UK's largest telecommunications providers, operating networks that carry government communications, financial transactions, and critical infrastructure data. As a regulated provider of national infrastructure, BT faced pressure from the UK National Cyber Security Centre (NCSC) to assess its quantum vulnerability and begin post-quantum cryptography planning earlier than most commercial enterprises. By 2022, BT had launched one of the more structured PQC migration programs in the telecom sector.

**Quantum Angle**

The quantum threat to BT is immediate in one sense and deferred in another. Harvest-now, decrypt-later attacks — where adversaries record encrypted traffic today to decrypt once quantum computers are available — are a present risk for data that retains sensitivity for decades. BT's network carries traffic for government clients, financial institutions, and critical infrastructure operators, all of whom have long-lived secrets. The NCSC's guidance explicitly called out this risk and encouraged early migration planning.

**Decisions Made**

BT's approach centered on a structured inventory: cataloging every cryptographic protocol, certificate, and VPN tunnel in use across its network, then prioritizing them by sensitivity and data longevity. BT partnered with Toshiba's quantum research division (which has a significant UK presence) and participated in NCSC working groups on PQC standards adoption. They also began testing hybrid TLS — connections that use both classical and post-quantum algorithms simultaneously — in live network environments.

**Measured Outcome**

BT's hybrid TLS pilots showed that PQC algorithms could be layered onto existing infrastructure with manageable performance overhead. The inventory process revealed, as it had for HSBC, that third-party and legacy systems were the hardest dependencies to migrate. BT published a public report in 2023 summarizing its migration framework, which became a reference document for other UK telecoms. Full migration across BT's network was estimated to take seven to ten years.

**Open Question**

BT estimated its full PQC migration at seven to ten years. Given that cryptographically relevant quantum computers could theoretically arrive within that window, is seven to ten years too slow? Who bears responsibility for accelerating the migration — the telecom company, its enterprise customers, or government regulators?

---

### Case D-20: A Mobile Network Operator's Quantum Key Distribution Pilot

**Situation**

A European mobile network operator with operations in three countries was exploring quantum key distribution (QKD) as a method of securing the fiber links between its core data centers. QKD uses the properties of individual photons to distribute cryptographic keys in a way that is theoretically unbreakable: any attempt to intercept the photons changes their quantum state, alerting both parties. The operator partnered with a QKD hardware vendor to pilot the technology on a live inter-datacenter fiber route in 2021.

**Quantum Angle**

QKD is a hardware-based security technology, not a software algorithm. It requires dedicated fiber runs (or precise free-space optical links), specialized photon emitters and detectors at each end, and infrastructure to manage the key exchange process. Unlike PQC, which runs as software on existing hardware, QKD requires physical deployment of new equipment. It offers a different security model: rather than hardening encryption algorithms against quantum attack, it uses quantum physics to make eavesdropping physically detectable.

**Decisions Made**

The operator deployed QKD hardware on a 40-kilometer fiber run between two data centers, using equipment from a European QKD vendor. The pilot included a parallel comparison with PQC-based key exchange to assess the relative security assurance and operational complexity of each approach. A dedicated project team managed the pilot for twelve months, including integration with the operator's existing key management infrastructure.

**Measured Outcome**

The pilot confirmed that QKD worked as advertised on the test route: keys were exchanged securely and eavesdropping attempts were detectable. However, the cost-benefit analysis was unfavorable. QKD hardware for the pilot route cost approximately \$800,000, required ongoing maintenance by specialized technicians, and could not scale to the operator's full network without investment in the hundreds of millions of dollars. PQC, by comparison, could be deployed as a software update across the same infrastructure at a fraction of the cost. The operator paused the QKD program and redirected its security investment to PQC migration.

**Open Question**

QKD offers a theoretically stronger security guarantee than PQC — it is information-theoretically secure, not just computationally hard to break — but it costs orders of magnitude more to deploy. Is the marginal security benefit of QKD over PQC worth the cost for commercial telecoms? For which use cases, if any, does QKD's stronger guarantee justify its price tag?

---

## Section D.8 — Government & Public Sector

### Case D-21: NIST's Post-Quantum Cryptography Standardization Process

**Situation**

The National Institute of Standards and Technology (NIST) is a US government agency responsible for setting technical standards used across industry, government, and academia. In 2016, NIST launched a formal competition to standardize post-quantum cryptographic algorithms — replacement encryption methods that would remain secure even against attacks from quantum computers. The competition was a public process: any team in the world could submit an algorithm, and submissions would be evaluated through open peer review over multiple rounds. The process ran for eight years, concluding with the publication of the first four PQC standards in August 2024.

**Quantum Angle**

The NIST competition was driven by a specific quantum threat: Shor's algorithm, which can break RSA and elliptic curve cryptography on a sufficiently powerful quantum computer. Current encryption protects virtually all internet traffic, government communications, and financial systems. If quantum computers powerful enough to run Shor's algorithm at scale are built — estimates range from ten to thirty years away — the encryption infrastructure of the modern world becomes vulnerable. NIST's goal was to have replacement algorithms standardized and widely deployed well before that point.

**Decisions Made**

NIST structured the competition to maximize transparency and global participation. Sixty-nine algorithms were submitted in 2017. Through three rounds of public cryptanalysis — where researchers worldwide attempted to find weaknesses — the field was narrowed to four finalists: CRYSTALS-Kyber (for key encapsulation), CRYSTALS-Dilithium, FALCON, and SPHINCS+ (for digital signatures). Notably, one highly regarded finalist — SIKE — was broken by a classical computer attack in 2022, one weekend's work by a researcher using a standard laptop. This served as a dramatic reminder that cryptographic security is hard to predict.

**Measured Outcome**

The NIST process produced four published standards (FIPS 203–206) in 2024 — a concrete, deployable output after eight years of work. The process also generated significant learning: SIKE's failure showed that algorithms can appear secure for years before a critical vulnerability is found, reinforcing the importance of long public review periods. The standards are now being adopted by government agencies under a mandate from the White House's 2022 National Security Memorandum, and commercial technology companies are rapidly integrating them into products.

**Open Question**

The NIST process took eight years from call-for-proposals to published standards. Critics argue this was too slow; defenders argue that rushing cryptographic standards is dangerous, as SIKE's failure demonstrated. Given that similar standardization processes will likely be needed for future quantum-era security challenges, is eight years the right model? Should NIST build a standing post-quantum cryptography review body rather than running ad-hoc competitions?

---

### Case D-22: UK National Quantum Strategy Implementation

**Situation**

In March 2023, the UK government published its National Quantum Strategy, committing £2.5 billion over ten years to make the UK a global leader in quantum technologies. The strategy built on a decade of prior investment through the UK Quantum Technology Hubs program (launched in 2014), which had funded university-based research centers in quantum communications, sensing, imaging, and computing. The 2023 strategy went further: it aimed to translate research leadership into commercial quantum industry, with explicit goals for the number of quantum companies, jobs, and export revenue to be created by 2033.

**Quantum Angle**

The UK's quantum strategy spans four domains: quantum computing, quantum communications (including QKD networks), quantum sensing and timing, and quantum navigation. The government's position was that the UK had strong academic foundations in all four areas — particularly in quantum photonics and ion trap computing, where UK universities had produced world-leading research — but was at risk of seeing commercial value captured elsewhere as global competition intensified, particularly from the US and China.

**Decisions Made**

The strategy was organized around a National Quantum Computing Centre (NQCC) near Harwell in Oxfordshire, intended to serve as a national resource for companies and researchers developing quantum applications. Funding was distributed through Innovate UK grants, UKRI research programs, and direct government procurement. The strategy also included plans for a UK quantum network testbed and coordination with NATO allies on quantum security standards. A dedicated quantum mission team within the Department for Science, Innovation and Technology (DSIT) was created to oversee implementation.

**Measured Outcome**

Eighteen months into the strategy's implementation (by late 2024), early results were mixed. The NQCC became operational and began accepting industry users. Several UK quantum startups — including Quantinuum (majority UK-founded), Oxford Quantum Circuits, and ORCA Computing — raised significant private investment. However, critics noted that the \$2.5 billion commitment spread over ten years was modest compared to US CHIPS Act-level investments and China's estimated quantum spending. There were also concerns that the strategy's commercial targets — specific numbers of companies and jobs — were aspirational without clear mechanisms to achieve them.

**Open Question**

The UK's strategy explicitly aims to convert academic research leadership into commercial quantum industry — but this transition has historically been difficult for the UK across multiple technology waves, from semiconductors to the internet. Is a government strategy and funding commitment sufficient to change this pattern? What structural changes — in IP policy, startup funding, or talent retention — would be necessary to ensure that UK quantum research creates UK quantum companies rather than ideas that commercialize elsewhere?

---

## Instructor Notes

These 22 cases are designed to be used flexibly. Each "Open Question" is genuinely arguable — there is no single correct answer, and reasonable people with different priors about technology adoption, risk tolerance, and corporate strategy will reach different conclusions.

**Suggested pairings for comparison discussions:**

- Cases D-1 and D-2 (JPMorgan vs. Goldman Sachs) — compare research transparency strategies in the same industry
- Cases D-3 and D-19 (HSBC vs. BT Group) — compare PQC migration approaches across financial services and telecom
- Cases D-8 and D-11 (ExxonMobil vs. DHL) — compare quantum optimization outcomes across two logistics-adjacent industries
- Cases D-17 and D-18 (Lockheed vs. NASA) — compare quantum sensing vs. quantum computing readiness in aerospace
- Cases D-20 and D-21 (QKD Pilot vs. NIST Standards) — compare hardware-based and algorithm-based approaches to quantum security

**For make-up assignments:** Ask students to select any case, extend the "Measured Outcome" section with at least two additional developments from public sources published after 2023, and revise the "Open Question" to reflect what is now known.
