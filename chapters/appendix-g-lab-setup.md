---
title: "Appendix G: Lab Setup Guide"
subtitle: "Get fully set up before Chapter 1 — zero technical background required"
short_title: "Appendix G: Lab Setup"
description: "Step-by-step setup instructions for IBM Quantum Platform, Quirk, Google Colab, and all Python packages used in the book's labs. Includes direct links to all nine advanced lab notebooks."
label: appendix-g-lab-setup
tags: [lab setup, IBM Quantum, Colab, Qiskit, setup guide, getting started]
---

# Appendix G: Lab Setup Guide

This guide walks you through setting up every tool used in the book's hands-on labs. Follow these steps **before starting Chapter 1** and you'll never be blocked by a missing account or installation mid-chapter.

All tools in this book are free. You do not need to pay for anything to complete any lab.

---

## G.1 Tools at a Glance

| Tool | Used In | Account Required | Cost |
|------|---------|-----------------|------|
| **D-Wave Leap** | Ch 5, 6, 7, 8, 9 | Yes (free developer) | Free |
| IBM Quantum Platform | Ch 1, 2, 3, 4, 7, 8, 9 | Yes (free IBMid) | Free |
| Quirk (algassert.com/quirk) | Ch 2, 5 | No | Free |
| Google Colab | All advanced labs | Yes (Google account) | Free |
| IBM Quantum Composer | Ch 3, 5 | Yes (free IBMid) | Free |
| Qiskit (via Colab) | Ch 2, 4, 7, 8 | No (auto-installed) | Free |
| Qiskit Nature (via Colab) | Ch 7 | No (auto-installed) | Free |
| Qiskit Machine Learning (via Colab) | Ch 8 | No (auto-installed) | Free |
| liboqs-python (via Colab) | Ch 5 | No (auto-installed) | Free |
| D-Wave Ocean SDK (via Colab) | Ch 5, 6, 7, 8, 9 | No (auto-installed) | Free |

**Minimum setup required before Chapter 1:**
- Create an IBMid at quantum.ibm.com (5 minutes)
- Confirm you have a Google account for Colab

Everything else installs automatically when you open a lab notebook.

---

## G.2 D-Wave Leap Setup (Required for Chapters 5, 6, 7, 8, 9)

D-Wave Leap is the cloud access platform for D-Wave's quantum annealing hardware — including the same Advantage2 class of system hosted on FAU's campus. All D-Wave labs in this book (Labs 5B, 6A, 7B, 8B, 9B) run through Leap. Setup takes approximately 5 minutes and requires no credit card.

### Step 1: Create a Free Developer Account

1. Navigate to **[cloud.dwavesys.com](https://cloud.dwavesys.com)**
2. Click **Sign Up** → select **Developer** account type
3. Enter your name, email, and create a password
4. Verify your email address
5. Sign in — you will land on the Leap dashboard

**Free tier includes:** ~1 minute of QPU time per month + unlimited LeapHybridSampler time (the hybrid solver used in all book labs). This is more than sufficient for every lab in the book.

### Step 2: Get Your API Token

1. In the Leap dashboard, click your profile icon (top right) → **API Token**
2. Copy the token — it looks like `DEV-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`
3. Store it securely — you will use it in the lab notebooks

### Step 3: Install the Ocean SDK (via Colab — no local install needed)

All book lab notebooks install the Ocean SDK automatically. If you want to verify it works:

```python
# Run this in a Colab cell after opening any D-Wave lab notebook
!pip install dwave-ocean-sdk --quiet

import dwave.cloud
client = dwave.cloud.Client.from_config(token="YOUR-API-TOKEN-HERE")
solvers = client.get_solvers()
print([s.id for s in solvers])
# You should see a list including "hybrid_binary_quadratic_model_version2"
```

### Step 4: Configure the Token in Notebooks

Each D-Wave lab notebook has a configuration cell at the top. Replace `"YOUR-LEAP-API-TOKEN"` with your actual token:

```python
import os
os.environ["DWAVE_API_TOKEN"] = "DEV-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
```

Alternatively, create a `~/.config/dwave/dwave.conf` file for persistent configuration (see [D-Wave Ocean SDK docs](https://docs.ocean.dwavesys.com/en/stable/overview/install.html) for details).

### D-Wave Lab Notebooks in This Book

| Lab | Chapter | Description |
|-----|---------|-------------|
| Lab 5B | Ch 5 | PQC Migration Optimizer — QUBO feature selection for migration prioritization |
| Lab 6A | Ch 6 | D-Wave Stride Hands-On — business optimization on live hardware |
| Lab 7B | Ch 7 | Supply Chain Inventory Allocation as QUBO |
| Lab 8B | Ch 8 | ML Feature Selection for Demand Forecasting via D-Wave |
| Lab 9B | Ch 9 | Your Organization's QUBO — capstone optimization on D-Wave Leap |

### FAU Students: On-Campus Advantage2 Access

Once FAU's D-Wave Advantage2 is deployed on the Boca Raton campus (expected later 2026), on-campus access instructions will replace the Leap cloud configuration above. Until then, D-Wave Leap cloud provides access to the same Advantage2 class of hardware. See **Appendix H** for details on FAU's computing infrastructure.

### Troubleshooting D-Wave Leap

| Problem | Likely Cause | Fix |
|---------|-------------|-----|
| `AuthenticationError` | Token invalid or expired | Re-copy token from cloud.dwavesys.com dashboard |
| `SolverNotFoundError` | Wrong solver name | Use `LeapHybridSampler` for all book labs — not `DWaveSampler` |
| Submission timeout | Network issue | Re-run the submission cell; Leap submissions are idempotent |
| QPU minutes exhausted | Free tier limit | All book labs use `LeapHybridSampler` which has unlimited free time — switch from `DWaveSampler` if you see this error |

---

## G.3 IBM Quantum Platform Setup

IBM Quantum Platform gives you access to real quantum hardware and simulators through a browser. This takes about 10 minutes to set up.

### Step 1: Create an IBMid

1. Open your browser and go to **quantum.ibm.com**
2. Click the **"Sign in"** button in the top-right corner
3. On the sign-in page, click **"Create an IBMid"**
4. Fill in the registration form:
   - First name, last name
   - Email address (use one you check regularly — you'll need to verify it)
   - Password (at least 8 characters, one uppercase, one number)
   - Country
5. Click **"Next"**
6. IBM will send a verification email. Open your inbox and click the confirmation link.
7. Return to **quantum.ibm.com** and sign in with your new credentials.

:::{admonition} What you'll see after signing in
:class: tip
After your first login, IBM Quantum will show you a dashboard with your recent jobs, available systems, and usage statistics. If this is a new account, most sections will be empty — that's normal.
:::

### Step 2: Explore Compute Resources

1. In the left sidebar, click **"Compute Resources"** (or **"Infrastructure"** depending on the current UI version)
2. You will see a list of **quantum backends** — real quantum computers and simulators
3. Each backend shows:
   - **Name** (e.g., `ibm_brisbane`, `ibm_kyoto`)
   - **Number of qubits**
   - **Status** (Online / Offline / Maintenance)
   - **Queue depth** — how many jobs are waiting ahead of yours
4. Simulators (names starting with `ibmq_qasm_simulator` or `simulator_statevector`) run instantly with no queue

:::{admonition} Free tier backends
:class: note
On the free tier, you have access to a selection of smaller real backends (typically 5–127 qubits) and all simulators. You are limited to a certain number of circuits per month. Simulators do not count against your quota.
:::

### Step 3: Explore the Quantum Composer

1. In the left sidebar, click **"Quantum Composer"**
2. The Composer opens a visual drag-and-drop circuit editor. You will see:
   - A **circuit canvas** with horizontal "wires" representing qubits
   - A **gate palette** on the left — drag gates onto the circuit
   - A **state visualization** panel on the right — updates in real time as you build
3. Click any gate in the palette (e.g., the **H** gate for Hadamard) and drag it onto a qubit wire
4. The right panel updates instantly to show the quantum state after each gate
5. To run the circuit on a backend, click **"Run"** and select a backend from the dropdown

### Step 4: Check the Jobs Queue

1. Click **"Jobs"** in the left sidebar
2. This shows all circuits you have submitted to run on real hardware
3. Each job shows:
   - **Status**: Queued / Running / Completed / Failed
   - **Backend**: which machine ran it
   - **Shots**: how many times the circuit was sampled
   - **Results**: click a completed job to see measurement outcomes

### Step 5: Find Backend Calibration Data

Calibration data tells you how well a specific quantum computer is performing on a given day. This matters when comparing results across backends.

1. From **"Compute Resources"**, click on any backend name
2. The backend detail page shows:
   - **T1** — energy relaxation time (how long a qubit holds its state before decaying to |0⟩)
   - **T2** — dephasing time (how long coherence lasts)
   - **Gate error rates** — probability of error per gate operation
   - **Readout error rates** — probability of misreading a qubit during measurement
3. Higher T1/T2 values and lower error rates = better performance
4. Calibration updates daily — a backend that was noisy yesterday may be better today

### Step 6: Save Your API Token

For programmatic access from Colab notebooks, you'll need your IBM Quantum API token.

1. Click your **profile icon** (top right) → **"Account settings"**
2. Scroll to **"API token"** — click **"Copy"** to copy it to your clipboard
3. Store this token somewhere safe (a text file on your computer is fine — treat it like a password)
4. In the lab notebooks, there is a cell near the top that looks like this:

```python
from qiskit_ibm_runtime import QiskitRuntimeService

QiskitRuntimeService.save_account(
    channel="ibm_quantum",
    token="YOUR_API_TOKEN_HERE",
    overwrite=True
)
```

Replace `YOUR_API_TOKEN_HERE` with your actual token and run the cell once. Colab will remember it for the session.

:::{admonition} Free tier limits
:class: warning
The IBM Quantum free tier includes:
- Access to selected real quantum backends (5–127 qubits)
- 10 minutes of quantum compute time per month on real hardware
- Unlimited simulator runs (simulators are free and instant)
- No credit card required

For all labs in this book, the simulator is sufficient. Real hardware is optional and used only for comparison experiments.
:::

---

## G.3 Quirk Setup

Quirk is a zero-install, browser-based quantum circuit simulator made by Craig Gidney. No account, no download — just open the URL and start building.

### Step 1: Open Quirk

1. Go to **algassert.com/quirk** in any modern browser
2. Quirk loads immediately. You'll see a blank circuit canvas with a toolbar of quantum gates across the top

### Step 2: Understand the Interface

The Quirk interface has three main areas:

- **Gate toolbar** (top): All available quantum gates, organized by type. Hover over any gate to see its name and description.
- **Circuit canvas** (center): Horizontal wires represent qubits. Drag gates from the toolbar onto the wires.
- **Display panels** (right and bottom): Real-time visualizations of the quantum state — probability amplitudes, Bloch sphere, density matrix, and more.

### Step 3: Add Gates and Read Results

1. To add a gate: **drag it** from the toolbar and **drop it** on a qubit wire
2. To add a multi-qubit gate (like CNOT): drag the gate, then drag the control dot to the control qubit
3. The **probability display** (bottom panel) updates instantly. Each bar represents the probability of measuring a specific bitstring.
4. To remove a gate: drag it off the circuit canvas, or right-click and delete

**Example — build a Bell state:**
1. Drag the **H gate** onto qubit 0
2. Drag the **⊕ (CNOT target)** onto qubit 1 and connect its control to qubit 0
3. The probability display should show 50% for |00⟩ and 50% for |11⟩ — a maximally entangled Bell state

### Step 4: Save and Share Circuits

Quirk encodes your entire circuit in the URL. To save or share:

1. Build your circuit
2. Copy the URL from your browser's address bar — it updates automatically as you edit
3. Paste the URL anywhere (notes, email, browser bookmark) to restore the exact circuit
4. To share with a classmate: just send them the URL

:::{admonition} Quirk gotchas for first-time users
:class: warning
- **Quirk is a simulator only** — it does not connect to real quantum hardware
- **Qubit ordering** in Quirk is reversed compared to Qiskit. In Quirk, qubit 0 is the top wire; in Qiskit, qubit 0 is the bottom wire. When comparing circuits between tools, double-check bit ordering.
- **No save button** — your circuit lives in the URL. If you close the tab without copying the URL, the circuit is gone.
- **Page refresh resets the circuit** — copy your URL first.
:::

---

## G.4 Google Colab Setup

Google Colab is a free, cloud-hosted Jupyter notebook environment. All advanced labs in this book run in Colab — no local installation required.

### Step 1: Access Colab

1. Go to **colab.research.google.com**
2. Sign in with your Google account (the same account you use for Gmail or Google Drive)
3. Colab opens a "Welcome" notebook. You can ignore this.

### Step 2: Open a Notebook from GitHub

To open any of the book's lab notebooks:

1. Click **File → Open notebook**
2. A dialog box appears with tabs: Recent, Google Drive, GitHub, Upload, URL
3. Click the **GitHub** tab
4. In the search field, type: `liquid-books/applied-quantum-computing`
5. Press Enter — Colab will list all notebooks in the repository
6. Click the notebook you want to open

### Step 3: Run Cells

- To run a single cell: click inside it, then press **Shift + Enter**
- To run all cells from top to bottom: **Runtime → Run all**
- To restart the runtime and clear all variables: **Runtime → Restart runtime**

:::{admonition} Always run cells in order
:class: tip
Cells in a notebook depend on each other. Always run from top to bottom on your first pass. If you skip a cell or run them out of order, later cells may fail with `NameError` or `ImportError`.
:::

### Step 4: Use "Open in Colab" Badges

Each lab section in this book includes an **"Open in Colab"** badge — a blue button that links directly to the notebook. Clicking the badge opens the notebook in Colab immediately. No navigation required.

### Step 5: Runtime Settings

1. Click **Runtime → Change runtime type**
2. For all quantum labs in this book, select **CPU** — quantum simulation does not benefit from GPU
3. Click **Save**

GPU runtimes consume Colab's compute quota faster. CPU is faster to connect and sufficient for all labs here.

### Step 6: Save Your Work

Colab notebooks are temporary. Changes you make are not automatically saved to your Drive.

To save a personal copy:
1. Click **File → Save a copy in Drive**
2. A copy is saved to "My Drive / Colab Notebooks" in your Google Drive
3. Future edits to your copy are auto-saved

:::{admonition} Do not edit the original notebook
:class: warning
If you open a notebook directly from GitHub, you are editing a temporary copy. Save to Drive before making changes, or your work will be lost when the session ends.
:::

### Step 7: Common Colab Issues

**Runtime disconnected:**
Colab disconnects after ~90 minutes of idle time.
1. Click **Reconnect** (top right of the notebook)
2. Re-run the installation cell (the one with `pip install ...`)
3. Re-run the import cell
4. Continue from where you left off

**Package not found after reconnect:**
Installed packages do not persist across sessions. Every time you reconnect to a new runtime, re-run the `pip install` cell at the top of the notebook.

**Out of memory:**
If a cell crashes with a memory error, click **Runtime → Restart runtime** and re-run the notebook with fewer shots or a smaller circuit.

---

## G.5 Opening Book Notebooks in Colab

Click any link below to open the lab notebook directly in Google Colab. You will be prompted to sign in with your Google account if you are not already signed in.

| Chapter | Lab Name | Open in Colab |
|---------|----------|---------------|
| Chapter 1 | Quantum Momentum Index | [Open Notebook](https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch01-quantum-momentum-index.ipynb) |
| Chapter 2 | Bell Inequality CHSH | [Open Notebook](https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch02-bell-inequality-chsh.ipynb) |
| Chapter 3 | TCO Calculator | [Open Notebook](https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch03-tco-calculator.ipynb) |
| Chapter 4 | Backend Benchmarking | [Open Notebook](https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch04-backend-benchmarking.ipynb) |
| Chapter 5 | PQC Migration Scanner | [Open Notebook](https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch05-pqc-migration-scanner.ipynb) |
| Chapter 6 | Portfolio QAOA | [Open Notebook](https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch06-portfolio-qaoa.ipynb) |
| Chapter 7 | VQE Molecular Simulation | [Open Notebook](https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch07-vqe-molecular-simulation.ipynb) |
| Chapter 8 | QML Benchmark | [Open Notebook](https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch08-qml-benchmark.ipynb) |
| Chapter 9 | Quantum Eval Toolkit | [Open Notebook](https://colab.research.google.com/github/liquid-books/applied-quantum-computing/blob/main/notebooks/ch09-quantum-eval-toolkit.ipynb) |

:::{admonition} Bookmark this page
:class: tip
Bookmark this appendix or save the table above so you can return to these links throughout the course without hunting for them.
:::

---

## G.6 Local Python Setup (Optional)

If you prefer to run notebooks on your own machine instead of Colab, follow these steps. This is **optional** — all labs work in Colab without any local installation.

### Step 1: Install Python 3.10 or Higher

**Recommended: Anaconda**

1. Go to **anaconda.com/download**
2. Download the installer for your operating system (Windows, macOS, or Linux)
3. Run the installer — accept all defaults
4. Anaconda installs Python, Jupyter, and hundreds of scientific packages in one step

**Verify the installation:**
```bash
python --version
# Should output: Python 3.10.x or higher
```

### Step 2: Create a Virtual Environment

Using a dedicated environment prevents package conflicts between projects.

```bash
# Create environment named "quantum"
conda create -n quantum python=3.11

# Activate the environment
conda activate quantum
```

Or with plain Python `venv`:
```bash
python -m venv quantum-env
source quantum-env/bin/activate      # macOS / Linux
quantum-env\Scripts\activate         # Windows
```

### Step 3: Install Required Packages

With your environment activated, run:

```bash
pip install qiskit qiskit-aer qiskit-nature qiskit-machine-learning \
    pandas matplotlib numpy requests tabulate cryptography
```

This installs everything needed for all nine lab notebooks. Installation takes 2–5 minutes depending on your internet connection.

**Verify Qiskit installed correctly:**
```python
python -c "import qiskit; print(qiskit.__version__)"
```

### Step 4: Launch Jupyter

```bash
jupyter notebook
```

Jupyter opens in your browser at `http://localhost:8888`. Navigate to the folder where you saved the lab notebooks and click to open them.

### Step 5: IBM Quantum API Token (Required for Hardware Access)

Running notebooks locally does not require an IBM Quantum account for simulator jobs. However, to submit jobs to real quantum hardware, you need to authenticate:

1. Get your API token from **quantum.ibm.com** → Profile → Account Settings → API token
2. In your notebook, run the save-account cell once (see Section G.2, Step 6)
3. The token is saved locally at `~/.qiskit/qiskit-ibm.json` and reused automatically

:::{admonition} API token security
:class: warning
Your IBM Quantum API token is like a password. Do not paste it directly into a notebook you plan to share publicly on GitHub. Use environment variables instead:

```python
import os
token = os.environ.get("IBM_QUANTUM_TOKEN")
QiskitRuntimeService.save_account(channel="ibm_quantum", token=token)
```

Set the environment variable in your shell before launching Jupyter:
```bash
export IBM_QUANTUM_TOKEN="your_token_here"
```
:::

---

## G.7 Troubleshooting

### IBM Quantum Queue Times Are Too Long

**Symptom:** You submitted a job to real hardware and the estimated wait is hours.

**Fix:** Switch to a simulator — results are identical for most learning exercises.

```python
from qiskit_ibm_runtime import QiskitRuntimeService
from qiskit_aer import AerSimulator

# Use a local simulator instead of waiting in the hardware queue
simulator = AerSimulator()
```

All lab notebooks include a "simulator mode" toggle near the top. Set `USE_SIMULATOR = True` to skip the hardware queue entirely.

---

### Colab Runtime Disconnected

**Symptom:** You see "Runtime disconnected" or cells start failing with `NameError`.

**Fix:**
1. Click **Reconnect** in the top-right toolbar
2. Re-run the first cell in the notebook (the `pip install` cell)
3. Re-run the imports cell
4. Continue from your last completed cell

:::{admonition} Pro tip: keep Colab awake
:class: tip
Colab disconnects after ~90 minutes of idle time. To prevent this during a long lab session, keep the browser tab active and avoid switching away for extended periods. Some users run a simple loop in a cell to keep the runtime alive — though this is against Colab's terms for compute-intensive work.
:::

---

### Qiskit Version Conflicts

**Symptom:** You see errors like `ImportError: cannot import name 'QuantumCircuit'` or `AttributeError` on a Qiskit method.

**Cause:** Qiskit releases breaking changes between major versions. The notebooks were written for specific versions.

**Fix:** Use the pinned requirements in each notebook. The first cell of every lab notebook contains:

```python
pip install qiskit==1.x.x qiskit-aer==0.x.x  # pinned versions
```

Run this cell first, before any other cell. If you already ran the notebook and hit a version error, click **Runtime → Restart runtime** and re-run from the top.

---

### IBM Quantum API Token Expired or Invalid

**Symptom:** You see `IBMNotAuthorizedError` or `401 Unauthorized` when connecting to IBM Quantum.

**Fix:**
1. Go to **quantum.ibm.com** and sign in
2. Click your profile icon → **Account settings**
3. Under **API token**, click **"Regenerate"** to create a new token
4. Copy the new token
5. In your notebook (or terminal), run:

```python
from qiskit_ibm_runtime import QiskitRuntimeService

QiskitRuntimeService.save_account(
    channel="ibm_quantum",
    token="YOUR_NEW_TOKEN_HERE",
    overwrite=True
)
```

The `overwrite=True` flag replaces any previously saved token.

---

### "Backend Not Found" Error

**Symptom:** `QiskitBackendNotFoundError: No backend matches the criteria` or similar.

**Cause:** The backend you specified is offline, under maintenance, or has been retired by IBM.

**Fix:**
1. Go to **quantum.ibm.com → Compute Resources** and check backend status
2. Choose a backend that shows **"Online"**
3. Update your notebook:

```python
# List available backends
service = QiskitRuntimeService()
backends = service.backends(operational=True, simulator=False)
print([b.name for b in backends])

# Pick one from the list
backend = service.backend("ibm_brisbane")  # use an available backend name
```

Alternatively, switch to the simulator to avoid backend availability issues entirely.

---

### Packages Missing After Colab Reconnect

**Symptom:** `ModuleNotFoundError: No module named 'qiskit'` after your runtime reconnected.

**Cause:** Colab does not persist installed packages between sessions. Every new runtime starts clean.

**Fix:** Every time you open a lab notebook in a new session, run the `pip install` cell at the very top before doing anything else. This takes about 60–90 seconds and is unavoidable in Colab's free tier.

---

## G.8 Quick-Start Checklist

Use this checklist before starting Chapter 1:

**D-Wave Leap (required for Ch 5, 6, 7, 8, 9):**
- [ ] Created free developer account at cloud.dwavesys.com
- [ ] Verified email and signed in to Leap dashboard
- [ ] Copied API token from the dashboard
- [ ] Ran the verification cell in a Colab notebook to confirm solver access

**IBM Quantum (required for Ch 1, 2, 3, 4, 7, 8, 9):**
- [ ] Created IBMid at quantum.ibm.com
- [ ] Verified email and signed in to IBM Quantum Platform
- [ ] Located your API token in Account Settings

**Google Colab (required for all advanced labs):**
- [ ] Signed in to Google Colab at colab.research.google.com
- [ ] Opened the Chapter 1 notebook using the link in Section G.5
- [ ] Successfully ran the first cell (pip install)

**Quirk (required for Ch 2, 5):**
- [ ] Opened algassert.com/quirk and confirmed it loads in your browser

**Optional:**
- [ ] Completed local Python setup (Section G.7)
- [ ] Requested FAU OwlCloud/Athene HPC access (see Appendix H)

If every required box is checked, you're ready to start Chapter 1. Welcome to quantum computing.
