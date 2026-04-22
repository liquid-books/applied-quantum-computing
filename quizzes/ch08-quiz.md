# Chapter 8 Quiz: Quantum + AI — The Hybrid Frontier

*Not in the book TOC. For assessment use only.*

---

## Exercise 1: Concept Application — The Dequantization Test

A quantum AI vendor presents the following claim at a procurement meeting:

> *"Our quantum principal component analysis (qPCA) algorithm reduces dimensionality reduction time for our genomics pipeline by 10,000x versus classical PCA. The result is proven in our 2021 technical paper, which has 47 citations."*

**Question:** Apply the dequantization framework from Chapter 8 to evaluate this claim. Your response should:

a) Explain what dequantization is and why it is relevant to this specific claim (3–4 sentences)

b) Identify the specific dequantization result that directly applies to quantum PCA

c) State the single most important question you would ask this vendor before making any procurement decision

d) Explain whether the citation count (47 citations) provides evidence of quantum advantage, and why or why not

**Expected length:** 200–300 words

---

## Exercise 2: Methodology Critique

The following abstract describes a QML experiment:

> *"We implement a quantum kernel support vector machine using a 4-qubit ZZFeatureMap circuit on a statevector simulator. Our method achieves 96.2% accuracy on a synthetic 2D binary classification dataset (150 samples), outperforming a classical linear SVM baseline (88.4%). We conclude that quantum kernels demonstrate advantage over classical methods for this task."*

**Question:** Identify **four** specific methodological problems with this experiment that prevent it from supporting the conclusion. For each problem, state:
- What the problem is
- Why it matters
- What the researchers should have done instead

**Format:** A numbered list with three-to-four sentences per item.

---

## Exercise 3: Scenario Analysis — The Talent Decision

A large financial services firm with 200 ML engineers is deciding how to respond to the quantum AI landscape. Their Chief Data Officer presents three options at a board meeting:

**Option A:** Do nothing now. Wait until quantum ML is clearly production-ready, then hire a team.

**Option B:** Hire 10 quantum ML specialists immediately, build a dedicated quantum AI lab, and begin piloting quantum approaches on five production ML workloads.

**Option C:** Train 20 existing ML engineers in quantum literacy over the next 12 months, hire 2 quantum ML specialists to guide the program, and establish a governance process for evaluating quantum AI vendor claims.

**Question:** Evaluate each option using the talent framework from Chapter 8.

a) What are the principal risks of Option A? What specific competitive disadvantage could it create in the 2027–2030 window?

b) What are the principal risks of Option B? What does the credit-scoring case study suggest about beginning quantum pilots without adequate classical baseline discipline?

c) Why is Option C best aligned with the chapter's recommendations? What is its primary limitation?

d) What single addition to Option C would most improve it?

**Expected length:** 300–400 words

---

## Exercise 4: Governance Design

You are the Director of AI Procurement at a healthcare organization. A vendor has approached you with the following pitch:

> *"Our Quantum-Enhanced Diagnostic AI uses quantum kernel classification to identify early-stage pancreatic cancer from CT scan features with 91.7% sensitivity versus 88.3% for our classical baseline — a 3.4-percentage-point improvement that could save thousands of lives annually. Our system runs on IBM Quantum hardware and has been validated in a 400-patient retrospective study."*

**Question:** Design the governance process your organization should follow before considering this technology for any clinical application. Your process should include:

a) The five-question procurement filter from Chapter 8 applied specifically to this claim — for each question, identify what evidence would constitute a satisfactory answer

b) Two additional domain-specific questions appropriate to a healthcare context that the generic five-question filter does not address

c) The "Classical Baseline Optimization Plan" document required before any pilot could begin — specify what classical algorithms must be tested, what tuning methodology is required, and what minimum performance gap is required to proceed

d) A recommendation on whether the 400-patient retrospective study is adequate evidence to support a clinical pilot, with specific reference to statistical power and confidence intervals

**Expected length:** 400–500 words

---

## Answer Key

### Exercise 1

**a) Dequantization explained:** Dequantization is the development of classical algorithms that match the asymptotic performance of quantum algorithms, eliminating the claimed quantum speedup. It is directly relevant here because quantum PCA (qPCA) is one of the specific quantum ML algorithms that has been dequantized — a classical algorithm using randomized sampling methods has been shown to achieve the same asymptotic performance as the quantum algorithm.

**b) Specific result:** Tang (2021) extended the dequantization program (which began with the recommendation systems result in Tang 2019) to quantum PCA, demonstrating that a classical low-rank approximation algorithm using efficient sampling achieves the same asymptotic speedup claimed by qPCA.

**c) Single most important question:** "Are you familiar with the Tang (2021) dequantization result for qPCA, and if so, how does your algorithm's performance compare against the classical sampling-based alternative, not against naive classical PCA?" A vendor who cannot answer this question has not read the relevant literature. A vendor who can answer it and claims their approach still provides advantage must demonstrate why their specific data conditions defeat the classical sampling method.

**d) Citation count:** 47 citations provides no evidence of quantum advantage. Citations measure influence and interest, not correctness. A paper can be widely cited because it is interesting, controversial, or methodologically useful — not because its central claim is validated. Several of the most-cited retracted QML papers accumulated citations before their problems were identified. The only relevant evidence is: peer-reviewed experimental results that include an optimized classical baseline and have been independently replicated.

---

### Exercise 2

**Four methodological problems:**

1. **No comparison against an optimized classical kernel baseline.** The paper compares the quantum kernel against a linear SVM — the most basic and least powerful classical baseline. An RBF kernel SVM with properly tuned C and γ parameters would almost certainly match or exceed the 96.2% accuracy on this dataset. The conclusion that "quantum kernels demonstrate advantage over classical methods" cannot be supported without comparison against the best available classical kernel.

2. **Statevector simulator, not hardware.** The experiment was run on a noise-free classical simulation of the quantum circuit, not actual quantum hardware. Simulators do not capture gate errors, decoherence, or measurement errors. Results on simulators do not constitute evidence of quantum hardware performance. Any claim of quantum advantage must be demonstrated on hardware under realistic noise conditions.

3. **Toy synthetic 2D dataset with 150 samples.** A 150-sample 2D dataset is specifically the regime where quantum kernels are most likely to show synthetic advantages, because the 4-qubit circuit maps data into a feature space specifically designed for this dimensionality. This does not generalize to real-world datasets with hundreds of features and thousands of samples, which is where production ML systems operate. The advantage claim cannot be generalized from this dataset.

4. **Missing statistical rigor: single run, no confidence intervals.** A single accuracy result (96.2%) with no confidence interval does not constitute statistical evidence. With 150 test samples, a 96.2% vs. 88.4% difference could have wide confidence intervals depending on the test set size. The experiment should report: 5-fold cross-validation results, mean ± standard deviation across multiple random seeds, and a statistical significance test (e.g., McNemar's test for paired classifiers) before claiming any advantage.

---

### Exercise 3

**a) Option A risks:** Option A loses the talent pipeline window. Quantum ML talent takes 3–5 years to develop from classical ML foundations. If quantum ML hardware becomes production-ready between 2027 and 2030 and the organization has not started building competency, it will face a talent market where experienced quantum ML practitioners are scarce and expensive — exactly as happened with deep learning talent in 2015–2018. The firm cannot simply "hire a team" when the technology is ready if no such teams have been developing for years. The competitive disadvantage is not that it will be behind — it is that it will be behind for at least another 3–5 years while building the capability it should have started building now.

**b) Option B risks:** Option B risks significant capital misallocation. Deploying 10 specialists to five production ML workloads assumes those workloads are appropriate quantum pilot candidates — an assumption requiring the governance rigor this chapter teaches, which Option B does not mention. The credit-scoring case study illustrates the specific risk: an eager quantum team begins a pilot, reports a promising accuracy improvement against an under-tuned classical baseline, the result propagates through the organization as a "validated quantum advantage," and the subsequent classical catch-up damages both the credibility of the quantum program and the careers of those who championed it.

**c) Why Option C is best / its limitation:** Option C is best aligned because it builds quantum literacy at scale (20 engineers with quantum competency is a meaningful organizational capability), establishes the governance process before pilots begin (the lesson of the credit-scoring case), and allocates specialists to guidance rather than independent work — ensuring quantum ML competency is distributed, not siloed. Its primary limitation: the 12-month timeline for training 20 engineers is optimistic without dedicated time allocation. If these engineers continue full-time production responsibilities, quantum literacy training competes with immediate deliverables.

**d) Single best addition:** Mandate that any quantum ML pilot proposal must include a Classical Baseline Optimization Plan (with tuning budget and minimum performance gap) as a required approval document. This single structural addition would have prevented the credit-scoring mistake and would focus the quantum team's energy on genuine advantage opportunities rather than easy wins against weak baselines.

---

### Exercise 4

**a) Five-question filter applied:**

1. *Peer-reviewed evidence?* Required: a paper in a peer-reviewed clinical AI or quantum computing journal (not a vendor white paper) with the 400-patient retrospective study fully described, including the CT feature set, the preprocessing pipeline, and the train/test methodology. Evidence the vendor must provide: paper citation with DOI.

2. *Classical baseline optimized?* Required: documentation that the classical baseline was implemented using state-of-the-art methods (not default scikit-learn parameters) with full hyperparameter tuning and cross-validation. Evidence required: the exact classical algorithm, tuning methodology, and whether gradient-boosted trees or neural network classifiers were included in the comparison — not just a classical kernel SVM.

3. *Dequantization considered?* Required: the vendor must explain why efficient classical kernel methods (tuned RBF, polynomial kernel) cannot match the quantum kernel result on this feature set. Evidence required: documented comparison against optimized classical SVM with multiple kernel choices.

4. *Statistical evidence sufficient?* With 400 patients, the precision of sensitivity estimates is limited. A 91.7% sensitivity estimate on 400 samples has an approximate 95% confidence interval of approximately ±2.4 percentage points (binomial proportion CI). This means the confidence interval for the quantum result (approximately 89.3%–94.1%) overlaps substantially with the confidence interval for the classical baseline (approximately 85.9%–90.7%). The difference is not clearly statistically significant. Required: full confidence intervals, not point estimates; ideally, results from an independent validation cohort.

5. *Independently replicated?* Required: at least one independent academic medical center or clinical AI research group has reproduced the core sensitivity/specificity result on a separate patient cohort. A single retrospective study from the vendor is insufficient for a clinical application.

**b) Two additional healthcare-specific questions:**

- *Regulatory status:* Has this system received FDA 510(k) clearance or De Novo classification for the claimed clinical indication, or is there a pre-submission interaction on file? Quantum-enhanced diagnostic AI is a class II medical device and requires regulatory clearance before clinical deployment, regardless of performance characteristics.

- *Explainability:* Can the quantum kernel classification decision be explained in terms that a radiologist can audit and challenge? Quantum kernels operating in high-dimensional Hilbert space are fundamentally non-interpretable — a radiologist cannot examine why the model classified a case as high-risk. For a pancreatic cancer screening application, this is not a minor concern. It affects liability, informed consent, and the ability of clinicians to exercise appropriate professional judgment.

**c) Classical Baseline Optimization Plan:** Must include comparison against: gradient-boosted classifier (XGBoost or LightGBM) with full hyperparameter search, a tuned RBF kernel SVM, and a logistic regression model as interpretable reference. Tuning methodology: nested cross-validation (5 outer folds, 5 inner folds) with Bayesian hyperparameter optimization. Compute budget: at minimum equivalent to the quantum implementation effort. Minimum performance gap to proceed: the quantum system must exceed the best classical baseline by at least 2 full percentage points of sensitivity at equal specificity, with a 95% confidence interval that does not overlap zero — not a point estimate.

**d) Adequacy of 400-patient study:** A 400-patient retrospective study is inadequate to support a clinical pilot for pancreatic cancer screening for several reasons. Pancreatic cancer prevalence in a general population is approximately 0.03% — a 400-patient cohort is almost certainly not drawn from a population with meaningful prevalence unless it is a high-risk cohort, in which case generalizability is limited. At the reported 91.7% sensitivity, the 95% confidence interval spans approximately ±2.4 percentage points, meaning the true sensitivity could be as low as 89.3% — a clinically meaningful uncertainty for a cancer detection application. A minimum adequate study for a clinical pilot would require prospective data, at least 1,000 patients, and an independent validation cohort that was not used in any part of the model development.
