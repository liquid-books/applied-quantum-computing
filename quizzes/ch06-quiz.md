# Chapter 6 Quiz: The Optimization Goldmine — Logistics, Finance, and Energy

> **Instructions:** These exercises are graded separately from the main chapter. Submit your responses per course guidelines.

---

## Exercise 1: Combinatorial Complexity Classification (20 points)

A regional airline is building a quantum-inspired optimization program. They have identified four candidate problems:

- **Problem A:** Assigning 200 flight crews to 800 weekly flights, subject to FAA rest rules, crew qualifications, and base location constraints. Each assignment is a binary variable.
- **Problem B:** Calculating the fuel load for a single Boeing 737 given weather, payload, and route data. This is a standard physics calculation.
- **Problem C:** Sequencing 150 aircraft through a congested hub airport, optimizing for gate assignments, taxiway routing, and on-time departure — simultaneously.
- **Problem D:** Looking up the average on-time performance for a given city pair in a historical database.

**Questions:**
1. (8 points) Classify each problem as (a) combinatorial optimization, (b) deterministic calculation, or (c) database lookup. Justify each classification in one sentence.
2. (6 points) For the combinatorial problems, estimate the approximate number of binary variables in a full QUBO formulation. Show your reasoning.
3. (6 points) Which problem would you recommend as the highest-ROI candidate for a quantum-inspired pilot? Apply the four-step ROI framework from Section 6.10 qualitatively (no numbers required — use reasoning).

### Answer Key

**Q1 Classifications:**
- Problem A: **(a) Combinatorial optimization** — selecting the best assignment of crews to flights from an exponential space of possible assignments; each crew-flight pairing is a binary variable.
- Problem B: **(b) Deterministic calculation** — given the inputs, there is a single correct answer computed via well-defined physics equations; no selection among alternatives.
- Problem C: **(a) Combinatorial optimization** — assigning aircraft to gates, taxiway sequences, and departure slots involves selecting from an astronomical number of possible configurations simultaneously.
- Problem D: **(c) Database lookup** — querying stored historical data; no optimization involved.

**Q2 Variable Count Estimates:**
- Problem A: ~200 crews × 800 flights = 160,000 binary variables (one per crew-flight assignment). Constraints reduce the feasible space but not the variable count.
- Problem C: ~150 aircraft × 30 gates × 20 time slots × 10 taxiway routes ≈ 900,000 binary variables for a fully explicit formulation; a decomposed formulation might use 10,000–50,000 variables effectively.

**Q3 Highest-ROI Candidate:**
Problem A (crew scheduling) is typically the highest-ROI candidate because: (1) the cost envelope is very large (crew costs represent ~25–30% of airline operating costs; for a regional airline, this might be \$500M+ annually); (2) the solution quality gap for classical crew scheduling heuristics is well-documented at 3–8%; (3) the formulation is standard (QUBO crew scheduling has existing templates); (4) the problem recurs weekly, making the annual ROI calculation favorable. Problem C (airport sequencing) is high-value but more operationally complex to deploy safely.

---

## Exercise 2: QUBO Formulation Analysis (25 points)

A hospital cafeteria serves 1,000 meals per day and must decide each morning which combination of dishes to prepare from a menu of 30 possible items. Constraints: total preparation labor ≤ 200 hours, total ingredient cost ≤ \$2,000, at least 1 vegetarian entrée, at least 2 protein options, no more than 15 dishes total. Objective: maximize projected customer satisfaction score (each dish has a historical satisfaction rating).

**Questions:**
1. (10 points) Define the binary variables for this problem. Write the objective function in plain English, then express it as a QUBO term.
2. (10 points) Show how to encode the "at least 1 vegetarian entrée" constraint as a QUBO penalty term. (Hint: express the constraint as an equality, then add a squared penalty.)
3. (5 points) A consultant claims this problem "requires quantum computing" because it has 30 variables. Critically evaluate this claim. What is actually needed, and what tools would you recommend?

### Answer Key

**Q1 Binary Variables and Objective:**
- Let $x_i \in \{0,1\}$ for $i = 1, \ldots, 30$, where $x_i = 1$ means dish $i$ is prepared.
- Objective (plain English): Maximize the total satisfaction score of selected dishes.
- As a QUBO objective term (we minimize negative satisfaction): $-\sum_{i=1}^{30} s_i x_i$, where $s_i$ is dish $i$'s satisfaction score. This is linear, contributing to the diagonal of Q: $Q_{ii} = -s_i$.

**Q2 Vegetarian Constraint:**
- Let $V \subseteq \{1,\ldots,30\}$ be the set of vegetarian dishes.
- Constraint: $\sum_{i \in V} x_i \geq 1$ (at least one vegetarian dish selected).
- Reformulate as equality with slack: $\sum_{i \in V} x_i - s = 1$ where $s \geq 0$ is a non-negative slack variable. Since $\sum_{i \in V} x_i$ can range from 0 to $|V|$, the slack ranges from 0 to $|V|-1$.
- Penalty term: $\lambda \left(\sum_{i \in V} x_i - 1\right)^2$ for violated configurations (where the sum equals 0), with $\lambda$ chosen large enough to dominate the objective. In practice: $\lambda > \max(s_i)$ suffices.

**Q3 Critical Evaluation:**
The consultant's claim is incorrect. With only 30 binary variables ($2^{30} \approx 10^9$ possible states), this problem is trivially solvable by classical brute-force in seconds on a modern CPU. Quantum computing is not needed — nor is quantum-inspired optimization. Classical integer programming solvers (CPLEX, Gurobi, even open-source CBC) solve this problem class instantly. The claim conflates "binary variables" with "quantum required" — a common misrepresentation. For quantum-inspired methods to offer genuine advantage, problems typically need thousands of binary variables where classical exhaustive search is infeasible and classical heuristics leave a measurable quality gap.

---

## Exercise 3: Case Study Analysis — VW Lisbon to Production (30 points)

Re-read Section 6.8 (Volkswagen Flagship Case Study) carefully before answering.

**Questions:**
1. (10 points) VW's Lisbon pilot used a D-Wave quantum annealer. Their 2021 production deployment used a Fujitsu Digital Annealer (quantum-inspired classical). What specific evidence from the Lisbon pilot likely motivated the shift to classical hardware for production? Identify at least three distinct factors.
2. (10 points) VW defined an explicit "kill-switch" — the conditions under which they would migrate production to true quantum hardware. Design a concrete kill-switch specification for a logistics company with a vehicle routing problem involving 5,000 binary variables. Include: what you would measure, what threshold would trigger migration, and who would make the decision.
3. (10 points) A competing automaker reads about VW's Lisbon pilot and immediately purchases a D-Wave quantum system for their own logistics optimization. Evaluate this decision using the ROI framework and the three-pathway comparison table in Section 6.5.4. What should they have done instead?

### Answer Key

**Q1 Factors Motivating the Production Shift:**
Students should identify at least three of the following:
1. **Problem size mismatch:** The Lisbon pilot involved 4 vehicles; VW's production scheduling involves thousands of components and decisions — far exceeding the qubit capacity of available quantum annealers.
2. **Cost per solve:** Cloud quantum annealer access costs significantly more per problem solve than equivalent GPU compute time for quantum-inspired solvers on the same problem class.
3. **Integration complexity:** Quantum hardware requires specialized API integration, cloud connectivity, and formulation expertise not needed for CPU/GPU-based quantum-inspired tools.
4. **Solution quality equivalence:** If the quantum-inspired solver achieves comparable solution quality (within 2–3%) at much lower cost, the economic case for quantum hardware is weak.
5. **Hardware availability/reliability:** Cloud quantum annealers have limited queue times and uptime constraints unsuitable for daily production scheduling requirements.
6. **Risk of vendor dependency:** Single-vendor quantum hardware creates supply chain risk for critical business processes.

**Q2 Kill-Switch Specification:**
A strong answer includes:
- **What to measure:** Solution quality (approximation ratio vs. known optimal or tight classical bound), runtime per solve, cost per solve, on a standardized benchmark set of 5,000-variable VRP instances representing actual production scenarios.
- **Threshold:** Quantum hardware delivers >5% better approximation ratio than quantum-inspired baseline at ≤2x the cost per solve, reproducibly over a 90-day evaluation period.
- **Decision maker:** Cross-functional team including VP Operations (owns cost envelope), CTO/VP Technology (owns infrastructure decision), and Quantum Center of Excellence lead (owns technical assessment). Requires unanimous sign-off.
- **Review cadence:** Annual reassessment of threshold as hardware improves.

**Q3 Competitor Evaluation:**
The competitor made a premature hardware purchase without applying the ROI framework:
- **Should have started with pathway 3 (quantum-inspired):** Given that VW's own production deployment used quantum-inspired classical solvers for the same problem class, the evidence overwhelmingly supports starting there.
- **ROI mismatch:** D-Wave hardware costs hundreds of thousands to millions per year. Quantum-inspired solvers deliver comparable or superior results at a fraction of the cost for problems within current quantum hardware capacity limits.
- **What they should have done:** (1) Formulate one high-value logistics problem as a QUBO; (2) benchmark three quantum-inspired solvers (Fujitsu, D-Wave Leap hybrid, Toshiba SBM) against their current system; (3) deploy the winner in production; (4) set a quantum kill-switch trigger; (5) revisit quantum hardware purchase when the trigger conditions are met. Total cost: <\$500K vs. millions for premature hardware.

---

## Exercise 4: Pilot Design and ROI Projection (25 points)

You are a strategy consultant advising a US regional grocery chain (\$3.2 billion annual revenue, 180 stores, private fleet of 400 delivery trucks). Their current routing software is seven years old. Management suspects they are leaving efficiency on the table but has no data. They have asked you to design a quantum-inspired routing optimization pilot.

**Your deliverable:** A structured pilot proposal covering:

1. (8 points) **Problem formulation:** Describe the vehicle routing problem in terms of binary variables, objective function, and at least three real-world constraints that must be encoded. Estimate the variable count for the full problem.
2. (8 points) **ROI projection:** Using the four-step framework from Section 6.10, project the annual value of a successful quantum-inspired deployment. Use reasonable assumptions for solution quality gap and recovery factor; show all calculations.
3. (9 points) **Three-phase pilot plan:** Define Phase 1 (formulation and baseline), Phase 2 (solver evaluation), and Phase 3 (shadow deployment) with specific deliverables, timelines, and go/no-go criteria for each phase. Define the kill-switch for escalating to true quantum hardware.

### Answer Key

**Q1 Problem Formulation:**
- **Binary variables:** $x_{ijk} = 1$ if truck $i$ travels from stop $j$ to stop $k$. With 400 trucks, 1,000 daily stops, and considering routing structure: effective variable count ≈ 400 trucks × 300 routes × average 20 stops/route ≈ 2.4 million variables in a full explicit formulation. A decomposed formulation (one routing problem per region) reduces this to ~50,000–100,000 variables per solve.
- **Objective:** Minimize total distance traveled (or equivalently, total fuel cost + driver time cost) across all routes.
- **Constraints (at least 3):**
  1. Each delivery stop must be visited exactly once (assignment constraint)
  2. Each truck's total load must not exceed vehicle capacity
  3. Each stop must be served within its time window (customer preference)
  4. Driver hours must not exceed regulatory limits per shift
  5. Trucks must return to depot before end of day

**Q2 ROI Projection (sample calculation):**
- Annual logistics spend: \$3.2B × 8% logistics ratio = \$256M (or use a more specific estimate; graders should accept reasonable assumptions)
- Solution quality gap: Vehicle routing heuristics typically 8–12% above optimal; use 10% as midpoint
- Gap value: \$256M × 10% = \$25.6M/year
- Quantum-inspired recovery: 70% of gap (conservative)
- Annual improvement: \$25.6M × 70% = \$17.9M
- Pilot cost: \$400K (formulation + licensing + integration + measurement)
- Payback: \$400K / (\$17.9M / 52 weeks) ≈ 1.2 weeks of improvement value
- 3-year NPV (10% discount rate): ~\$44M net

**Q3 Three-Phase Pilot Plan:**
- **Phase 1 (Weeks 1–4): Formulation and Baseline**
  - Deliverable: QUBO formulation validated on 50-store, 50-truck sub-problem
  - Activities: Data extraction from current routing system, constraint mapping, QUBO matrix construction, classical brute-force validation on small instances
  - Go/no-go: QUBO solution matches classical optimum on validation instances within 1%
- **Phase 2 (Weeks 5–12): Solver Evaluation**
  - Deliverable: Benchmarked comparison of quantum-inspired solver vs. current system on 8 weeks of historical routing data
  - Activities: Run Fujitsu Digital Annealer, D-Wave Leap hybrid, and one additional solver; compare solution quality and runtime; calculate improvement vs. baseline
  - Go/no-go: At least one solver achieves >5% improvement vs. baseline on historical data with statistical significance (p < 0.05)
- **Phase 3 (Weeks 13–24): Shadow Deployment**
  - Deliverable: 12 weeks of parallel operation data; CFO-ready business case
  - Activities: Run quantum-inspired solver in parallel with current system; compare actual miles driven, fuel costs, delivery times; document improvement; build financial model
  - Go/no-go: Confirmed improvement ≥4% with positive NPV over 3-year horizon
- **Kill-switch for true quantum:** When a quantum annealing system (D-Wave or successor) can solve the full 400-truck routing problem (50,000+ variables) with >10% better solution quality than quantum-inspired baseline at ≤2x the compute cost, measured over a standardized benchmark set and validated by independent benchmarker.

---

*Chapter 6 Quiz — Applied Quantum Computing: A Leader's Guide to the Next Computing Revolution*
*Total: 100 points*
