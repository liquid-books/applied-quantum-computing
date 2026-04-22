---
title: "Chapter 6: The Optimization Engine — QUBO, D-Wave Stride, and Enterprise Results"
subtitle: "Formulate. Submit. Solve. The Production Quantum Workflow That Is Running at BASF, Volkswagen, and Mastercard Today."
short_title: "Ch. 6: The Optimization Engine"
description: "The most commercially mature application of quantum computing is combinatorial optimization — and it is running in production right now. This chapter teaches QUBO formulation from scratch, introduces D-Wave's Ocean SDK and Stride hybrid solver, and builds hands-on skills for submitting real optimization problems to FAU's Advantage2 system."
label: ch-06-optimization-goldmine
tags: [quantum optimization, QUBO, D-Wave, Ocean SDK, Stride, QAOA, combinatorial optimization, logistics, finance, energy, BASF, Volkswagen, FAU Advantage2, annealing]
---

# Chapter 6: The Optimization Engine — QUBO, D-Wave Stride, and Enterprise Results

:::{figure} ../images/ch06-explainer-infographic.png
:label: fig-ch06-explainer
:alt: Chapter 6 explainer infographic showing the optimization engine pipeline from business problem to QUBO formulation to D-Wave Stride solver to enterprise results
:width: 100%
:align: center

**Chapter 6 at a Glance.** The quantum optimization workflow has three steps: translate your business problem into QUBO, submit it to D-Wave's Stride hybrid solver, interpret the result against your classical baseline. This chapter teaches all three — from the mathematics of QUBO formulation through the Ocean SDK to production-grade enterprise results.
:::

There is a question that cuts through most of the noise around quantum computing: *What can I actually run on quantum hardware today, and what does it take to do it?*

For optimization problems, the answer is more concrete than most executives expect. BASF's manufacturing scheduling system runs on D-Wave's hybrid solver in production — not as a pilot, not as a benchmark, but as the operational scheduler for chemical plant production at one of the world's largest industrial companies. The input is a manufacturing problem. The output is a production schedule. The quantum hardware runs in the middle, invisibly. The scheduling computation that previously took 4–6 hours completes in under 90 seconds.

This chapter is about how that works — technically, mathematically, and operationally. It is the most hands-on chapter in this book because quantum optimization is the most hands-on quantum application available today. By the end, you will have formulated a real optimization problem as a QUBO, submitted it to D-Wave's solver, and interpreted the result. Not in a simulator. On real quantum hardware.

---

## Opening Scene: The Night Shift That Disappeared

The BASF plant in Ludwigshafen, Germany — the largest integrated chemical complex in the world — runs 24 hours a day, 365 days a year. Every evening, a scheduling team sits down to plan the next day's production across thousands of interdependent chemical processes, hundreds of pieces of equipment, dozens of feedstock streams, and a web of safety, regulatory, and contract constraints.

The classical scheduling algorithm they had used for years was sophisticated — a commercial operations research platform with decades of refinement. It produced a feasible schedule. Every night. Without fail.

But "feasible" is not the same as "optimal." The classical algorithm made locally good decisions — allocating this reactor to this process, sequencing these steps in this order — without being able to see the full consequences of those choices across the entire plant. The schedule it produced was a good approximation of optimal, not optimal itself.

The gap between "good approximation" and "optimal" in a plant of BASF's scale is not academic. It is hundreds of millions of euros per year in idle equipment, suboptimal feedstock usage, energy waste during off-peak transitions, and missed production windows.

In 2020, BASF began working with D-Wave Systems to reformulate their scheduling problem as a QUBO and run it on D-Wave's hybrid quantum-classical solver. The reformulation took months — not because the math was obscure, but because translating a complex industrial problem into QUBO is genuine engineering work that requires deep domain expertise combined with quantum formulation skill.

The result: scheduling computation reduced from 4–6 hours overnight to under 90 seconds. The schedule quality improved measurably. The night shift dedicated to scheduling review was reassigned to higher-value work. BASF has publicly confirmed the deployment is in production.

This chapter teaches you how to do what BASF's team did — at a scale appropriate for the classroom, on the same hardware they used.

---

## The Single Idea

```{epigraph}
The most commercially ready quantum application is not cryptography, not drug discovery, not quantum AI. It is optimization — and the tool that unlocks it is a mathematical framework called QUBO. Learning to formulate QUBO problems is the most practical quantum skill you can acquire today.
```

Quantum advantage in optimization is not a future event. It is happening right now in production at a small but growing number of enterprises. The bottleneck is not hardware — D-Wave's Advantage2 is available in the cloud via Leap and on FAU's campus. The bottleneck is formulation: translating a real business problem into the mathematical language that the quantum solver speaks.

QUBO — Quadratic Unconstrained Binary Optimization — is that language. It is a mathematical framework that expresses optimization problems as minimizing a quadratic function of binary variables. It is the native format for quantum annealers. It is also, with the right tools and training, learnable in a single course module.

This chapter has two parts. Part I builds the mathematical foundation: what is QUBO, how do you formulate problems in it, and how does the annealer solve it. Part II puts that foundation to work: the D-Wave Ocean SDK, the Stride hybrid solver, and real enterprise cases showing what production quantum optimization looks like.

---

## Part I: The Mathematical Foundation

### The Selection Problem Hiding in Every Business Decision

Most business problems that executives believe are *calculation* problems are actually *selection* problems. A calculation problem has one right answer derived from inputs. A selection problem asks: *which combination of choices, from an exponentially large set of possibilities, produces the best outcome?*

Selecting the best delivery routes for 500 trucks is not a calculation. It is a selection from a number of possible route combinations so large it exceeds the number of atoms in the observable universe. Selecting the optimal portfolio from 3,000 securities under 50 constraints is not a calculation. Scheduling 200 surgeries across 15 operating rooms and 80 surgeons is not a calculation.

These are **combinatorial optimization problems**. And the defining characteristic of combinatorial optimization is the *explosion* of possibilities:

| Problem Size | Possible Combinations | Comparison |
|---|---|---|
| 10 binary decisions | 1,024 | Fast classical search |
| 50 binary decisions | ~10¹⁵ | More than seconds since the Big Bang |
| 100 binary decisions | ~10³⁰ | Exceeds computer science capacity |
| 1,000 binary decisions | ~10³⁰¹ | No classical computer can enumerate |

A chemical plant scheduling 1,000 binary production decisions per day operates in the last row of that table. No classical computer can find the provably optimal solution. The best it can do is find a good approximation — and the gap between "good approximation" and "optimal" is exactly the value that quantum annealing is designed to close.

---

### The Energy Landscape: Turning Problems into Physics

The insight that makes quantum annealing work is surprisingly elegant: *every optimization problem can be reformulated as a physics problem*.

Specifically, every minimization problem can be expressed as finding the lowest-energy configuration of a physical system. In quantum annealing, the energy of a configuration corresponds to the cost of that solution: high energy = bad solution, low energy = good solution. The annealer's job is to find the lowest-energy state — which is the same as finding the optimal solution.

:::{figure} ../images/ch06-qubo-energy-landscape.png
:label: fig-ch06-qubo
:alt: QUBO energy landscape showing classical search trapped in local minima vs quantum tunneling finding global optimum
:width: 100%
:align: center

**The QUBO Energy Landscape.** Classical optimizers move downhill step by step, getting trapped in local minima — good solutions surrounded by worse ones that block the path to the global optimum. Quantum annealers use quantum tunneling to pass through those barriers, probing the true global minimum directly.
:::

**The crumpled paper analogy:** Imagine a large piece of paper crumpled into peaks and valleys. Every point on the paper is one possible solution to your optimization problem. The height of each point is the cost of that solution. The lowest valleys are the best solutions. A classical optimizer is a hiker who moves downhill step by step — and gets trapped in the first valley they reach. A quantum annealer tunnels through the hills, probing multiple valleys simultaneously, finding the lowest one even when it is hidden behind high barriers.

**The mathematical form** of this energy landscape is the **Ising model**:

$$E = -\sum_{i} h_i \sigma_i - \sum_{i < j} J_{ij} \sigma_i \sigma_j$$

where $\sigma_i \in \{-1, +1\}$ are spin variables, $h_i$ are local fields (individual variable costs), and $J_{ij}$ are coupling strengths (interaction costs between pairs of variables). Finding the lowest-energy Ising configuration is equivalent to solving the corresponding optimization problem.

The Ising model maps directly to QUBO through the substitution $x_i = (\sigma_i + 1)/2$, giving binary variables $x_i \in \{0, 1\}$ and the QUBO cost function:

$$\text{QUBO}: \min_{x \in \{0,1\}^n} x^T Q x = \min \sum_{i} Q_{ii} x_i + \sum_{i < j} Q_{ij} x_i x_j$$

The matrix $Q$ encodes both the objective (what you are optimizing) and all constraints (what you must satisfy). The quantum annealer finds the binary vector $x$ that minimizes this expression.

---

### QUBO Formulation: A Step-by-Step Tutorial

Learning QUBO formulation is a skill — like learning SQL or financial modeling. It requires practice on small problems before tackling production-scale ones. This section builds that skill from the ground up.

**The formulation process always has four steps:**

1. **Define binary variables:** What binary decisions does your problem involve? Each yes/no choice becomes one binary variable.
2. **Write the objective:** What are you minimizing or maximizing? Express it as a quadratic function of your binary variables.
3. **Add constraints as penalties:** For each constraint your problem must satisfy, add a penalty term (a positive number multiplied by how much the constraint is violated squared) to the objective.
4. **Set penalty weights:** Choose penalty multipliers large enough to force the solver to satisfy constraints, but not so large that they dominate the objective.

---

#### Example 1: The Knapsack Problem

**Problem:** You have 5 items with weights $[2, 3, 4, 5, 1]$ kg and values $[3, 4, 5, 6, 1]$. Your knapsack holds at most 8 kg. Which items do you take to maximize value?

**Step 1: Binary variables.** Let $x_i = 1$ if item $i$ is taken, 0 otherwise. Five variables: $x_1, x_2, x_3, x_4, x_5$.

**Step 2: Objective.** Maximize total value = $3x_1 + 4x_2 + 5x_3 + 6x_4 + 1x_5$. Since QUBO minimizes, negate: minimize $-3x_1 - 4x_2 - 5x_3 - 6x_4 - x_5$.

**Step 3: Constraints.** Weight constraint: $2x_1 + 3x_2 + 4x_3 + 5x_4 + x_5 \leq 8$. Rewritten as a penalty: $\lambda \cdot \max(0, 2x_1 + 3x_2 + 4x_3 + 5x_4 + x_5 - 8)^2$.

**Step 4: Q matrix.** Combine objective and penalty into one QUBO matrix. The diagonal entries $Q_{ii}$ capture linear terms (values and self-penalty). The off-diagonal entries $Q_{ij}$ capture pair interactions (weight constraint cross-terms).

---

#### Example 2: A 3-City Routing Problem

**Problem:** A delivery driver must visit cities A, B, C in the shortest total distance, starting and ending at the depot.

**Binary variables:** $x_{it} = 1$ if city $i$ is visited at time step $t$.

For 3 cities and 3 time steps: 9 binary variables. The Q matrix encodes:
- Objective: minimize total travel distance (negative reward for short-distance connections)
- Constraint 1: each city visited exactly once (each row sums to 1)
- Constraint 2: each time step has exactly one city (each column sums to 1)

With penalty weight $\lambda$ chosen large relative to maximum edge length, the minimum QUBO solution gives the shortest valid tour.

---

#### Example 3: Portfolio Selection (QUBO for Finance)

**Problem:** Select 3 assets from 6 candidates to maximize expected Sharpe ratio while minimizing pairwise correlation.

**Binary variables:** $x_i = 1$ if asset $i$ is selected. Six variables.

**Objective:** Minimize $-\sum_i r_i x_i + \lambda_1 \sum_{i < j} C_{ij} x_i x_j$

where $r_i$ is the expected return of asset $i$ and $C_{ij}$ is the correlation between assets $i$ and $j$.

**Constraint:** Exactly 3 assets selected: $\sum_i x_i = 3$.

As a penalty: $\lambda_2 (\sum_i x_i - 3)^2 = \lambda_2 (\sum_i x_i^2 + 2\sum_{i < j} x_i x_j - 6\sum_i x_i + 9)$

Since $x_i^2 = x_i$ for binary variables, this simplifies to known quadratic terms that add directly to $Q$.

:::{admonition} The Constraint Penalty Rule
:class: important

Every constraint of the form $g(x) = 0$ adds a penalty $\lambda \cdot g(x)^2$ to the QUBO. The penalty weight $\lambda$ must be large enough that satisfying the constraint is always cheaper than violating it. Rule of thumb: $\lambda > $ maximum possible value of the objective. If in doubt, start with $\lambda = 5 \times \max |Q_{ij}|$ and tune empirically.
:::

---

### The Combinatorial Explosion: Why This Matters at Scale

The knapsack and routing examples above involve 5–9 binary variables. Real production problems involve thousands.

| Problem | Binary Variables | Classical Brute Force | D-Wave Stride |
|---|---|---|---|
| 3-city routing | 9 | Instant | Instant |
| 20-city routing | 400 | Infeasible | Seconds |
| BASF plant scheduling | ~50,000 | Infeasible (forever) | Minutes |
| Portfolio (3,000 assets) | 3,000 | Infeasible | Minutes |

The combinatorial explosion makes classical brute force futile above ~30 variables. Classical heuristics (greedy algorithms, simulated annealing, genetic algorithms) scale better but find solutions that are provably suboptimal. D-Wave's Stride hybrid solver — which decomposes large QUBOs, routes subproblems to the Advantage2 QPU, and coordinates results classically — handles the production-scale problems in the last two rows of that table.

---

## Part II: The D-Wave Ocean SDK

D-Wave's **Ocean SDK** is the Python library for formulating and submitting problems to D-Wave hardware and solvers. It is the tool BASF's engineers used to translate their manufacturing scheduling problem into QUBO. It is what you will use in Lab 6.

Ocean is open-source, well-documented, and installable in one line:

```bash
pip install dwave-ocean-sdk
```

### The Core Workflow

Every Ocean program follows the same structure:

```python
# Step 1: Define the problem as a QUBO dictionary
Q = {
    ('x1', 'x1'): -3,   # diagonal: reward for including item 1 (value = 3)
    ('x2', 'x2'): -4,   # reward for item 2
    ('x3', 'x3'): -5,   # reward for item 3
    ('x1', 'x2'): 6,    # penalty: weight interaction between items 1 and 2
    # ... etc
}

# Step 2: Choose a sampler (solver)
from dwave.system import LeapHybridSampler
sampler = LeapHybridSampler()   # D-Wave Leap hybrid solver (Stride)
# OR:
from dwave.system import DWaveSampler, EmbeddingComposite
sampler = EmbeddingComposite(DWaveSampler())   # Direct QPU access

# Step 3: Submit the problem
sampleset = sampler.sample_qubo(Q, label="Knapsack Problem")

# Step 4: Extract and interpret results
best = sampleset.first
print(f"Best solution: {best.sample}")
print(f"Energy (cost): {best.energy}")
print(f"Timing: {sampleset.info}")
```

### Samplers: Choosing Your Solver

Ocean uses a **sampler** abstraction — every solver (QPU, hybrid, simulator) has the same interface, so you can switch between them by changing one line.

| Sampler | What It Does | When to Use |
|---|---|---|
| `SimulatedAnnealingSampler` | Classical simulated annealing on CPU | Testing formulations locally, no Leap account needed |
| `TabuSampler` | Classical tabu search | Fast local testing, comparison baseline |
| `DWaveSampler` + `EmbeddingComposite` | Direct QPU access on Advantage2 | Small problems (<3,000 variables), research |
| `LeapHybridSampler` | Stride hybrid solver | Production-scale problems, enterprise use |
| `LeapHybridCQMSampler` | Constrained Quadratic Model solver | Problems with explicit constraints (easier formulation) |

### The Constrained Quadratic Model (CQM): A Better Interface

For complex problems with many constraints, Ocean offers a higher-level interface: the **Constrained Quadratic Model (CQM)**. Instead of manually constructing the Q matrix and adding penalty terms, you define the objective and constraints directly in a natural mathematical syntax, and Ocean handles the QUBO conversion internally.

```python
from dimod import ConstrainedQuadraticModel, Binary, quicksum
from dwave.system import LeapHybridCQMSampler

# Define binary variables
items = ['item1', 'item2', 'item3', 'item4', 'item5']
weights = {'item1': 2, 'item2': 3, 'item3': 4, 'item4': 5, 'item5': 1}
values  = {'item1': 3, 'item2': 4, 'item3': 5, 'item4': 6, 'item5': 1}
x = {i: Binary(i) for i in items}

# Build the CQM
cqm = ConstrainedQuadraticModel()

# Objective: maximize total value (minimize negative)
cqm.set_objective(-quicksum(values[i] * x[i] for i in items))

# Constraint: total weight ≤ 8
cqm.add_constraint(
    quicksum(weights[i] * x[i] for i in items) <= 8,
    label='weight_limit'
)

# Submit to Stride
sampler = LeapHybridCQMSampler()
sampleset = sampler.sample_cqm(cqm, label='Knapsack CQM', time_limit=5)

# Extract feasible solutions
feasible = sampleset.filter(lambda s: s.is_feasible)
best = feasible.first
print({i: best.sample[i] for i in items})
```

The CQM interface is the recommended starting point for enterprise problems. It is more readable, less error-prone, and handles constraint penalty weights automatically.

---

### Reading the Results

Every Ocean sampleset contains:

```python
# Sample output structure
sampleset.first          # Best solution found
sampleset.first.sample   # Dict of variable assignments {x1: 0, x2: 1, ...}
sampleset.first.energy   # Cost function value (lower = better)
sampleset.first.num_occurrences  # How many times this solution appeared

sampleset.info           # Timing breakdown
# Example info:
# {'timing': {
#    'qpu_sampling_time': 2680,       # microseconds on QPU
#    'qpu_access_time': 15000,        # total QPU reservation
#    'total_real_time': 1.23          # seconds including classical overhead
# }}
```

The timing breakdown is one of the most instructive outputs. QPU sampling time in *microseconds* vs. total wall time in *seconds* reveals the classical overhead surrounding the quantum computation — problem programming, embedding, communication, and classical post-processing.

---

## Part III: The Stride Hybrid Solver in Depth

For enterprise-scale problems — the BASF scheduling problem, a logistics fleet of 500 vehicles, a portfolio of 3,000 assets — the direct QPU cannot handle the full problem in one submission. D-Wave's **Stride hybrid solver** bridges this gap.

:::{figure} ../images/ch06-stride-architecture.png
:label: fig-ch06-stride
:alt: D-Wave Stride hybrid solver architecture showing problem decomposition, QPU subproblem routing, and classical coordination
:width: 100%
:align: center

**Stride Hybrid Solver Architecture.** Stride operates as a classical orchestration layer around the Advantage2 QPU. Large QUBO problems are decomposed into QPU-tractable subproblems, each solved by the annealer, with results coordinated classically until a stopping criterion is met. The enterprise user sees a single API call; the quantum-classical coordination is invisible.
:::

### How Stride Works

Stride implements a form of **decomposition-based hybrid optimization**:

1. **Problem ingestion:** The full QUBO (potentially millions of variables) is received as input
2. **Subproblem identification:** A classical algorithm identifies high-impact subsets of variables — clusters where improving the solution is most likely to reduce total cost
3. **QPU submission:** Each subproblem (scaled to fit the Advantage2's qubit capacity) is submitted to the annealer
4. **Result integration:** QPU results are integrated back into the full solution, updating the variable assignments
5. **Iteration:** Steps 2–4 repeat until the time limit is reached or convergence is detected
6. **Output:** The best full-problem solution found across all iterations is returned

From the user's perspective, Stride takes one API call and returns one answer. The internal quantum-classical orchestration is abstracted away.

### Stride vs. Direct QPU: When to Use Each

| Criterion | Direct QPU | Stride Hybrid |
|---|---|---|
| Problem size | <3,000 logical variables | Up to millions of variables |
| Latency | Microseconds (QPU only) | Seconds to minutes |
| Cost model | QPU microseconds | Solver seconds |
| Best for | Research, small pilots, benchmarking | Production enterprise workloads |
| FAU coursework | Available on Advantage2 | Available on Advantage2 + Leap |

For all production use cases in this course — BASF-style scheduling, logistics routing, portfolio construction — Stride is the right tool.

### The Time Limit Parameter

Stride accepts a `time_limit` parameter (in seconds) that controls how long the solver runs before returning its best solution. There is a fundamental tradeoff:

- **Short time limit (5–30s):** Fast results, may not reach convergence. Good for interactive exploration and rapid iteration during formulation development.
- **Medium time limit (60–300s):** Balanced quality/speed. Typical for production batch jobs.
- **Long time limit (>300s):** Maximum solution quality. Used for high-value, infrequently-run problems where quality matters more than speed.

```python
# Short run (exploratory)
sampleset = sampler.sample_cqm(cqm, time_limit=10)

# Production run
sampleset = sampler.sample_cqm(cqm, time_limit=180)
```

The BASF production deployment uses a time limit calibrated to complete within the operational scheduling window — the solver runs overnight to maximize quality, but can also run in near-real-time (90 seconds) for disruption response.

---

## Part IV: Enterprise Applications

### Flagship Case Study: BASF — Manufacturing Scheduling from Hours to Seconds

#### Situation

BASF's Ludwigshafen complex, the world's largest integrated chemical site, schedules thousands of production processes across hundreds of interconnected facilities every day. The scheduling problem involves:

- **Equipment assignments:** Which reactor, vessel, or dryer handles which chemical process?
- **Sequencing constraints:** Process A must complete before Process B can start on the same equipment
- **Feedstock timing:** Raw material availability windows that cannot be violated
- **Safety constraints:** Certain chemical combinations cannot be processed simultaneously on adjacent equipment
- **Contract commitments:** Customer delivery schedules that drive hard completion deadlines
- **Energy optimization:** Off-peak electricity rates for energy-intensive processes

The classical OR solver previously used required 4–6 hours of overnight computation to produce a feasible schedule for the following day. The solver found feasible schedules reliably — but "feasible" means constraint-satisfying, not cost-minimizing. The gap between the feasible schedule and the optimal schedule represented meaningful economic waste in equipment utilization, feedstock consumption, and energy cost.

#### QUBO Formulation

BASF's technical team, working with D-Wave, reformulated the scheduling problem as a QUBO. The binary variables represented assignment decisions: $x_{jkt} = 1$ if job $j$ is assigned to equipment $k$ at time slot $t$.

For a representative problem instance with 200 jobs, 30 equipment units, and 50 time slots, this generates $200 \times 30 \times 50 = 300,000$ binary variables — far beyond direct QPU capacity but tractable for Stride.

The Q matrix encoded:
- **Objective terms:** Negative reward for completing high-priority jobs within deadline; positive cost for equipment idle time
- **Assignment constraints:** Each job assigned to exactly one equipment-time slot (constraint penalty)
- **Precedence constraints:** Penalty for violating process sequencing requirements
- **Capacity constraints:** No equipment assigned more than one job per time slot
- **Safety constraints:** Penalty for forbidden equipment-process combinations

Constraint penalty weights were calibrated through iterative testing: too low and the solver violates constraints; too high and the solver ignores the objective. The calibration process took the engineering team several weeks of domain-specific tuning.

#### Results

| Metric | Classical OR Solver | D-Wave Stride |
|---|---|---|
| Solve time | 4–6 hours | 90 seconds |
| Schedule quality | Feasible | Measurably closer to optimal |
| Real-time disruption response | Not feasible | Feasible (re-plan in <2 minutes) |
| Night shift scheduling team | Required | Partially reassigned |

The most operationally significant improvement was not the solve time — it was the capability for **real-time disruption response**. When an equipment failure or feedstock delay disrupts a production plan, the classical overnight batch approach could not re-optimize in real time. The Stride-based system can re-plan in under 2 minutes, allowing production coordinators to respond immediately to disruptions rather than running to the end of the shift with a broken plan.

BASF has publicly confirmed this deployment is in production and has described it as a competitive differentiator.

#### Open Question

The BASF QUBO formulation was built for a specific plant topology and product mix. How should the formulation be updated when plant equipment is added, product formulations change, or new safety constraints are introduced? This is the ongoing formulation maintenance challenge for production quantum deployments — and it is a career opportunity for engineers who understand both the process chemistry and the QUBO math.

---

### Industry Snapshot: Volkswagen and the Quantum-Inspired Pivot

Volkswagen's 2019 Lisbon pilot — routing four conference buses through real Lisbon traffic using a D-Wave annealer — was the first public demonstration of quantum optimization on a real urban routing problem. VW's team formulated the four-vehicle routing problem as a QUBO, submitted it to D-Wave's hardware, and received optimized routes in near-real-time.

What happened next is the more instructive story. VW's post-pilot analysis revealed: the quantum annealing formulation produced better solutions than their classical routing baseline — but the full production problem (thousands of vehicles, millions of constraints) exceeded the direct QPU capacity of the hardware available in 2019. Rather than wait for larger quantum hardware, VW deployed **quantum-inspired classical solvers** using the same QUBO mathematical framework, running on Fujitsu's Digital Annealer, for production logistics optimization at their Wolfsburg and Zwickau plants. Documented efficiency improvements: 3–8% in parts logistics routing, 2–5% in factory scheduling throughput.

**The strategic lesson:** QUBO formulation is a transferable skill. Problems formulated for quantum annealers today run on quantum-inspired classical solvers when the scale exceeds current QPU capacity — and will run on larger QPUs as hardware scales. Investing in QUBO formulation skills today builds capability that pays off across all three generations of hardware.

---

### Industry Snapshot: Verge Ag — Quantum Routing for Autonomous Agriculture

Verge Ag, an Australian agricultural technology company, uses autonomous vehicles to manage large-scale crop operations — planting, spraying, harvesting — across farm fields that can span thousands of hectares. The autonomous vehicle routing problem involves dozens of vehicles, complex field geometries, crop-type constraints, equipment capability limits, and dynamic replanning as weather and soil conditions change.

Verge Ag partnered with D-Wave to reformulate their fleet routing problem as a QUBO and solve it using Stride. The production deployment enables real-time route optimization for autonomous agricultural fleets — a problem class where classical routing algorithms had previously required human intervention to handle the dynamic replanning required in actual field operations.

The Verge Ag case illustrates an important pattern: quantum optimization is showing up earliest in industries where (1) the routing/scheduling problem has high operational complexity, (2) real-time replanning has direct operational value, and (3) the problem naturally maps to binary decisions. Autonomous vehicles, just-in-time manufacturing, and emergency logistics all share these characteristics.

---

### Industry Snapshot: Mastercard — Fraud Detection as a Graph Problem

Mastercard's use of D-Wave's hybrid solver for transaction graph optimization is one of the more surprising enterprise quantum deployments — surprising because fraud detection does not immediately look like a QUBO problem.

Mastercard's approach reformulates fraud ring detection as a **Maximum Clique** problem on a transaction graph: given a graph where nodes are accounts and edges represent suspicious transaction links, find the largest fully connected subgraph (clique) — which corresponds to the most tightly coordinated fraud ring. Maximum Clique is a classic NP-hard graph optimization problem that maps directly to QUBO.

The quantum annealer's ability to search large solution spaces simultaneously makes it particularly well-suited for graph optimization problems where classical algorithms struggle at scale. Mastercard has described the D-Wave deployment as part of their production fraud detection infrastructure.

**The formulation insight:** Many problems that don't look like optimization problems — fraud detection, drug-target matching, supply chain risk identification — reformulate as graph problems that map naturally to QUBO. The QUBO formulation skill extends far beyond traditional "optimization" domains.

---

### The Three Pathways to Optimization Advantage

Not all quantum optimization routes are equally available today. Understanding all three is essential for a complete enterprise strategy.

:::{figure} ../images/ch06-quantum-inspired-gateway.png
:label: fig-ch06-gateway
:alt: Three-pathway quantum optimization diagram showing annealing, QAOA, and quantum-inspired classical routes with readiness levels
:width: 100%
:align: center

**Three Pathways, Different Timelines.** Quantum annealing (D-Wave Stride) is production-ready for optimization today. QAOA on gate-model hardware is viable for research and near-term pilots. Quantum-inspired classical solvers deliver 60–80% of quantum benefit on existing infrastructure — the highest near-term ROI for most enterprises.
:::

**Pathway 1 — Quantum Annealing (Production-Ready Now)**

D-Wave Advantage2 + Stride hybrid solver. The BASF, VW, Mastercard, and Verge Ag deployments. Available on FAU's campus and via D-Wave Leap cloud. Best for QUBO optimization problems with up to millions of variables.

**Pathway 2 — QAOA on Gate-Model Hardware (Research/Near-Term)**

Quantum Approximate Optimization Algorithm running on IBM, Google, or IonQ hardware. The algorithm alternates between quantum cost layers (encoding the problem) and quantum mixer layers (creating superposition over solutions), with a classical optimizer tuning the parameters. QAOA is not yet competitive with D-Wave Stride on production-scale problems, but it is the right tool for research into gate-model optimization and for building familiarity with the algorithm class that will matter most in the fault-tolerance era.

**Pathway 3 — Quantum-Inspired Classical Solvers (High Near-Term ROI)**

Fujitsu Digital Annealer, Toshiba Simulated Bifurcation Machine, Microsoft Azure Quantum-Inspired Optimization, D-Wave's `neal` (simulated annealing) library. These tools use QUBO mathematics on classical hardware. They capture 60–80% of full quantum optimization benefit without quantum hardware. For organizations not yet ready to commit to quantum cloud infrastructure, quantum-inspired solvers are the fastest path to production ROI — and the formulation skills transfer directly to quantum hardware.

| Pathway | Hardware | Problem Scale | Solution Quality | Available |
|---|---|---|---|---|
| Quantum annealing (Stride) | D-Wave Advantage2 | Millions of variables | High | Now |
| QAOA | IBM / Google / IonQ | ~50–200 qubits | Approximate | Now (research) |
| Quantum-inspired | Classical CPU/GPU | Millions of variables | 60–80% of quantum | Now |

---

## Part V: The ROI Framework

### Sizing the Opportunity

Before any pilot, executives need a structured approach to calculating the quantum optimization ROI envelope. The framework has four steps:

**Step 1: Identify the Annual Cost Envelope**
What is the total annual spend directly affected by the optimization problem? For logistics routing: fuel + driver labor + vehicle depreciation. For portfolio optimization: alpha gap × assets under management. For plant scheduling: equipment downtime + feedstock waste + energy cost above minimum.

**Step 2: Estimate the Solution Quality Gap**
How much worse is your current solution than theoretical optimum? Published benchmarks for common problem classes:
- Vehicle routing heuristics: typically 5–15% above optimal
- Portfolio optimization with integer constraints: 3–10% above optimal
- Job shop scheduling: 5–20% above optimal (problem-dependent)
- Grid dispatch: 2–8% above optimal

**Step 3: Apply the Improvement Factor**
D-Wave Stride and quantum-inspired solvers typically recover 50–80% of the solution quality gap on well-formulated problems.

**Step 4: Calculate Pilot Payback**
A bounded Stride pilot — formulation + Leap access + integration + measurement — typically costs \$150,000–\$800,000. Compare against projected annual improvement value.

:::{admonition} ROI Example: Retail Logistics
:class: tip

- Annual logistics spend: **\$180M**
- Solution quality gap (estimated): **10%** → Gap value: \$18M/year
- D-Wave Stride recovery factor: **70%** → Annual improvement: **\$12.6M**
- Pilot cost: **\$400K** | Payback period: **~12 days of improvement value**
- 3-year NPV (10% discount): **~\$31M**

A single retail chain with this profile that does not run a quantum optimization pilot is leaving more than \$10M per year on the table. The pilot pays back in under two weeks of improvement value.
:::

---

## Productive-Struggle Problem

:::{admonition} Formulate a Real QUBO
:class: important

**The Challenge:** You are a strategy consultant hired by a regional hospital network to evaluate quantum optimization for surgery scheduling. The problem involves 100 surgeries per week, 10 operating rooms, 40 surgeons, and 20 time slots per day.

**Part 1 — Binary Variables (20 minutes)**
Define the binary variables for this problem. How many variables are there total? (Hint: How many ways can a surgery be assigned to an OR, a surgeon, and a time slot?)

**Part 2 — Objective Function (30 minutes)**
Write the objective function in plain English, then translate it to a QUBO expression. Consider: you want to maximize OR utilization while minimizing surgeon overtime and respecting priority levels for urgent surgeries.

**Part 3 — Constraints (30 minutes)**
Identify five constraints that must be satisfied. For each, write the constraint in plain English, then express it as a QUBO penalty term. Include: (1) each surgery assigned to exactly one slot, (2) each surgeon performs at most one surgery per time slot, (3) each OR used by at most one surgery per time slot, (4) specialist surgeons assigned only to appropriate surgical types, (5) urgent surgeries completed in the first half of the week.

**Part 4 — Penalty Weight Calibration (15 minutes)**
For constraint (1), what happens to the solution if the penalty weight is set too low? Too high? Write a brief explanation of how you would determine the right penalty weight empirically.

**Part 5 — Solver Selection**
Should this problem use the direct Advantage2 QPU or the Stride hybrid solver? Justify your answer with reference to the variable count.
:::

::::{dropdown} Guidance Notes

**Part 1:** Variables: 100 surgeries × 10 ORs × 40 surgeons × 20 slots = 800,000 binary variables. This is well within Stride's capacity but far beyond the direct QPU. Stride is the right tool.

**Part 2:** Objective: minimize (−1 × OR utilization) + (positive coefficient × surgeon overtime) + (−1 × priority_weight × urgent surgery completion). Each term becomes a linear or quadratic expression in the binary variables.

**Part 3:** Each constraint generates a quadratic penalty. Constraint (1): $\lambda_1 (\sum_{k,m,t} x_{ikmt} - 1)^2$ for each surgery $i$ — penalizes any assignment count other than exactly 1.

**Part 4:** Too-low penalty: solver assigns surgeries to multiple slots to optimize the objective. Too-high penalty: solver satisfies all constraints but ignores the objective (all feasible solutions look equivalent). Calibrate by starting at $\lambda = 5 \times \max|\text{objective coefficient}|$ and testing on small instances.

**Part 5:** 800,000 variables → Stride hybrid solver. Direct QPU handles ~3,000 variables.
::::

---

## Module-Level Outcomes

By completing this chapter and its labs, you should be able to:

::::{grid} 1 1 2 2
:::{grid-item-card} Outcome 1
:class-header: bg-primary text-white
**QUBO Formulation**

Formulate a combinatorial optimization problem as a QUBO from scratch: define binary variables, write the objective function, add constraint penalties, and calibrate penalty weights. Demonstrate on at least one routing, scheduling, or portfolio problem.
:::

:::{grid-item-card} Outcome 2
:class-header: bg-primary text-white
**Ocean SDK**

Use D-Wave's Ocean SDK to build a QUBO or CQM, select an appropriate sampler, submit to D-Wave Leap, and interpret the sampleset output including timing breakdown and solution quality metrics.
:::

:::{grid-item-card} Outcome 3
:class-header: bg-primary text-white
**Stride vs. Direct QPU**

Distinguish when to use the Stride hybrid solver vs. direct QPU access, using problem variable count and solution quality requirements as the primary decision criteria.
:::

:::{grid-item-card} Outcome 4
:class-header: bg-primary text-white
**Enterprise Case Analysis**

Analyze the BASF, Volkswagen, Mastercard, and Verge Ag cases: what problem was solved, how was it formulated, what hardware/solver was used, and what was the measured operational outcome.
:::

:::{grid-item-card} Outcome 5
:class-header: bg-warning text-white
**ROI Framework**

Calculate projected ROI for a quantum optimization pilot using the four-step framework: cost envelope × quality gap × improvement factor vs. pilot cost. Present as a one-page CFO memo with explicit go/no-go criteria.
:::
::::

---

## Lab 6A (Regular): Your First D-Wave Stride Job

**Duration:** 60–75 minutes  
**Tool:** D-Wave Leap — [cloud.dwavesys.com](https://cloud.dwavesys.com) (free developer account + credits)  
**Deliverable:** Results notebook + 300-word operations memo

### Overview

You will formulate a small job scheduling problem as a QUBO, submit it to D-Wave's Leap hybrid solver using Ocean SDK, and interpret the results. This is the same technical workflow used in BASF's production deployment — scaled to a size appropriate for a single lab session.

### Prerequisites

```bash
pip install dwave-ocean-sdk
```

Or use the Google Colab link below (no installation required).

<a href="https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch06-lab-stride-intro.ipynb" target="_blank">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="margin-bottom: 1rem;"/>
</a>

### The Problem: 4-Job Scheduling

You are a hospital operations manager. You have 4 surgeries to schedule across 2 operating rooms, across 2 time slots. Each surgery has a priority (1 = low, 5 = high). Surgery A and Surgery C cannot run simultaneously (shared equipment). Surgery B and Surgery D cannot run simultaneously (shared anesthesiologist).

| Surgery | Priority | Duration |
|---|---|---|
| A | 5 (urgent) | Slot 1 |
| B | 3 | Slot 1 |
| C | 4 | Slot 2 |
| D | 2 | Slot 2 |

### Step 1: Formulate the QUBO

```python
import dimod
from dwave.system import LeapHybridSampler

# Binary variables: x[surgery, OR, time_slot]
# x_A1_1 = Surgery A in OR 1 at Slot 1
# x_A2_1 = Surgery A in OR 2 at Slot 1
# etc.

# Build QUBO dictionary
Q = {}

# Objective: maximize priority scores
# (minimize negative priority score)
priorities = {'A': 5, 'B': 3, 'C': 4, 'D': 2}
variables = ['A_OR1_S1', 'A_OR2_S1', 'A_OR1_S2', 'A_OR2_S2',
             'B_OR1_S1', 'B_OR2_S1', 'B_OR1_S2', 'B_OR2_S2',
             'C_OR1_S1', 'C_OR2_S1', 'C_OR1_S2', 'C_OR2_S2',
             'D_OR1_S1', 'D_OR2_S1', 'D_OR1_S2', 'D_OR2_S2']

# Reward for scheduling high-priority surgeries
for var in variables:
    surgery = var.split('_')[0]
    Q[(var, var)] = -priorities[surgery]

# Penalty: each surgery scheduled exactly once
lambda_assign = 10  # penalty weight
for surgery in 'ABCD':
    surgery_vars = [v for v in variables if v.startswith(surgery + '_')]
    for i, vi in enumerate(surgery_vars):
        Q[(vi, vi)] = Q.get((vi, vi), 0) + lambda_assign * (1 - 2)
        for vj in surgery_vars[i+1:]:
            Q[(vi, vj)] = Q.get((vi, vj), 0) + 2 * lambda_assign

# Penalty: A and C cannot be in same slot (shared equipment)
lambda_conflict = 15
for or_room in ['OR1', 'OR2']:
    for slot in ['S1', 'S2']:
        va = f'A_{or_room}_{slot}'
        vc = f'C_{or_room}_{slot}'
        if va in variables and vc in variables:
            Q[(va, vc)] = Q.get((va, vc), 0) + lambda_conflict

# Submit to Stride
sampler = LeapHybridSampler()
sampleset = sampler.sample_qubo(Q, label='Hospital Scheduling Lab', time_limit=10)

# Display results
best = sampleset.first
scheduled = {var: val for var, val in best.sample.items() if val == 1}
print("Scheduled:", scheduled)
print("Energy:", best.energy)
print("Timing:", sampleset.info.get('timing', {}))
```

### Step 2: Run and Record

Submit to Leap. Record:
- Which surgeries were scheduled, in which ORs, at which times
- The energy (cost) of the best solution
- The QPU access time from the timing breakdown
- Were all constraints satisfied? (No A+C conflict, no B+D conflict?)

### Step 3: Experiment

Try changing the penalty weights:
- Reduce `lambda_conflict` to 1. What happens to the solution?
- Increase `lambda_conflict` to 100. Does it affect solution quality?

### Deliverable

Write a 300-word operations memo to the hospital CMO:
1. What schedule did the solver produce?
2. Were all constraints satisfied?
3. How does this approach scale to a real hospital scheduling problem with 200 surgeries?
4. What would need to change in the formulation to add a constraint for surgeon lunch breaks?

---

## Lab 6B (Optional Advanced): BASF Scheduling in Miniature

<a href="https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch06-lab-basf-mini.ipynb" target="_blank">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="margin-bottom: 1rem;"/>
</a>

**Duration:** 90–120 minutes  
**Tool:** D-Wave Ocean SDK + Leap (Python)  
**Deliverable:** Complete QUBO formulation + results analysis + CFO memo

Build a miniature version of BASF's manufacturing scheduling problem using Ocean's CQM interface. You are given 10 chemical processes, 4 reactors, 3 time shifts, and a set of precedence constraints (process A must complete before process B). Your objective: maximize throughput (processes completed per shift) while satisfying all safety and sequencing constraints.

The notebook provides the process data, constraint list, and starter CQM code. Your task:
1. Complete the CQM formulation (objective + all constraints)
2. Submit to Stride with time limits of 10s, 30s, and 120s — compare solution quality
3. Compare Stride results against a classical greedy baseline (provided)
4. Write a 500-word CFO memo: what would this approach look like at BASF's scale? What is the one-year ROI projection?

---

## Discussion Guidelines

**Prompt:** BASF's production deployment of D-Wave Stride for manufacturing scheduling is the most well-documented enterprise quantum optimization deployment as of 2026. Drawing on the case study in this chapter and at least two additional sources (D-Wave's published application notes, academic papers on quantum annealing for scheduling, or industry reports), analyze:

1. What made BASF's formulation work? What were the three most critical technical decisions their team made?
2. What is the single most significant constraint on replicating BASF's results at a different industrial facility — and how would you address it?
3. At what problem scale does quantum annealing on the Advantage2 definitively outperform the best available classical solver for job shop scheduling? Cite evidence.

**Requirements:** 400+ words. Cite at least two sources (APA 7). Respond substantively to two classmates — engage with their specific claims, add evidence they haven't cited, or challenge a conclusion.

---

## Glossary

**QUBO (Quadratic Unconstrained Binary Optimization)** — The mathematical problem format for quantum annealers. A minimization over binary variables with a quadratic cost function encoding both the objective and all constraints as penalty terms.

**Ising Model** — The physics energy model equivalent to QUBO, using spin variables {−1, +1} instead of binary {0, 1}. The native language of D-Wave's Advantage2 hardware.

**Energy Landscape** — A geometric representation of an optimization problem where solution cost corresponds to physical energy. The annealer finds the lowest-energy (best) configuration.

**Quantum Tunneling** — The quantum mechanical phenomenon that allows the annealer to pass through energy barriers, escaping local minima that trap classical hill-climbing algorithms.

**Ocean SDK** — D-Wave's open-source Python library for formulating and submitting QUBO problems to D-Wave hardware and solvers. Available at `pip install dwave-ocean-sdk`.

**Sampler** — Ocean's abstraction for any quantum or classical solver. Common samplers: `LeapHybridSampler` (Stride), `DWaveSampler` (direct QPU), `SimulatedAnnealingSampler` (classical baseline).

**LeapHybridSampler** — Ocean's interface to D-Wave's Stride hybrid solver. The recommended sampler for enterprise-scale problems.

**Constrained Quadratic Model (CQM)** — A higher-level Ocean problem formulation that accepts explicit constraints without manual penalty construction. Handled by `LeapHybridCQMSampler`.

**Sampleset** — The result object returned by an Ocean sampler. Contains all solutions found, their energies, timing information, and metadata.

**Stride Hybrid Solver** — D-Wave's production classical-quantum hybrid solver that decomposes large QUBO problems into QPU-tractable subproblems, coordinates results classically, and returns the best solution found. Handles millions of variables.

**Embedding** — The process of mapping a QUBO's logical variable graph onto the Advantage2's physical Pegasus qubit topology. Handled automatically by `EmbeddingComposite` in Ocean.

**Penalty Weight (λ)** — The multiplier applied to a constraint penalty term in a QUBO. Must be large enough to force constraint satisfaction but not so large that it dominates the objective. Calibrated empirically.

**QAOA (Quantum Approximate Optimization Algorithm)** — A hybrid quantum-classical gate-model algorithm for optimization. Currently research-stage; not yet competitive with D-Wave Stride for production-scale problems.

**Quantum-Inspired Solver** — A classical optimization algorithm whose mathematical structure derives from quantum physics (annealing, bifurcation dynamics). Captures 60–80% of quantum optimization advantage without quantum hardware. Examples: Fujitsu Digital Annealer, Toshiba SBM.

**Time Limit** — The Stride hybrid solver parameter controlling maximum solve time. Longer limits produce higher solution quality. Typical production range: 60–300 seconds.

**Combinatorial Optimization** — A class of problems seeking the best selection or arrangement from a finite but exponentially large set of possibilities. The primary application domain for quantum annealing.

**Local Minimum** — A solution better than all immediate neighbors but not the global optimum. Classical optimizers get trapped in local minima; quantum annealing uses tunneling to escape.

**Energy** — In Ocean results, the value of the QUBO cost function for a given solution. Lower energy = better solution. The annealer minimizes energy.

---

## Leader's Takeaway

```{epigraph}
BASF's scheduling team didn't wait for quantum to be ready. They learned QUBO. The hardware was ready for them.
```

The pattern that emerges from BASF, Volkswagen, Mastercard, and Verge Ag is consistent and instructive. None of these organizations adopted quantum optimization because the hardware was revolutionary. They adopted it because their optimization problems were real, the ROI was calculable, and the formulation skill — QUBO — was learnable.

The hardware was secondary. The math was primary.

Quantum computing's most commercially mature application requires no faith in future hardware milestones, no tolerance for physics speculation, and no budget for experimental technology. It requires the ability to look at a business problem — a scheduling problem, a routing problem, a selection problem — and ask: *Can I express this as a set of binary decisions and a cost function?*

If the answer is yes, D-Wave's Stride hybrid solver is ready today. The Advantage2 on this campus is ready today. The Ocean SDK is a `pip install` away.

The executives and engineers who develop QUBO formulation fluency in 2026 will be the ones running production quantum optimization in 2028 while their competitors are still waiting for the technology to "mature." It has already matured, for this problem class. The bottleneck is formulation skill — and that bottleneck is exactly what this chapter, and this course, is designed to close.

```{admonition} Chapter Summary
:class: note

- The most commercially ready quantum application is combinatorial optimization — and it is in production now at BASF, Volkswagen, Mastercard, and Verge Ag.
- QUBO (Quadratic Unconstrained Binary Optimization) is the mathematical language of quantum annealing. Learning to formulate QUBO is the most practically valuable quantum skill available today.
- D-Wave's Ocean SDK provides a Python interface for formulating and submitting QUBO problems. The CQM interface handles constraint penalty construction automatically.
- The Stride hybrid solver handles enterprise-scale problems (millions of variables) by decomposing QUBOs into QPU-tractable subproblems. Direct QPU access is appropriate for small problems (<3,000 variables) and research.
- Three optimization pathways exist: quantum annealing (production-ready), QAOA on gate-model (research/near-term), quantum-inspired classical (high near-term ROI on existing infrastructure).
- ROI framework: cost envelope × quality gap × improvement factor vs. pilot cost. Most enterprises with >$50M optimization spend have a compelling pilot ROI.
- QUBO formulation skills transfer: problems formulated for quantum annealers today run on quantum-inspired classical solvers and will run on larger QPUs as hardware scales.
```
