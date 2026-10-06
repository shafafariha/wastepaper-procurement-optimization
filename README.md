# 📦 Behavioral Discrete Choice Modeling & Game-Theoretic Optimization for Wastepaper Recycling Procurement

[![Paper Status](https://img.shields.io/badge/Research%20Paper-Accepted%20(Forthcoming)-0052CC?style=for-the-badge&logo=googlescholar&logoColor=white)](#-academic-publication--status)
[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Econometrics](https://img.shields.io/badge/Statsmodels-Discrete%20Choice-4B8BBE?style=for-the-badge)](https://www.statsmodels.org/)
[![Game Theory](https://img.shields.io/badge/Game%20Theory-Nash%20Equilibrium-darkgreen?style=for-the-badge)](#stage-3-game-theoretic-competitive-formulation)
[![Risk Analysis](https://img.shields.io/badge/Monte%20Carlo-Risk%20Simulation-orange?style=for-the-badge)](#stage-4-monte-carlo-risk--uncertainty-quantification)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)

> **Author**: Shafa Fariha Tsuraya ([@shafafariha](https://github.com/shafafariha))  
> **Industrial Context**: Developed from field market research and procurement operations during an internship as **Market Research Analyst** at **Baling Center (BC)**, Pulp & Paper Manufacturing Industry.

---

## 📌 Table of Contents
- [Executive Summary](#-executive-summary)
- [Academic Publication & Status](#-academic-publication--status)
- [Data Governance & Confidentiality Notice](#-data-governance--confidentiality-notice)
- [Industry Background & Problem Statement](#-industry-background--problem-statement)
- [Integrated Decision Framework Architecture](#-integrated-decision-framework-architecture)
- [Methodology & Mathematical Formulations](#-methodology--mathematical-formulations)
  - [Stage 1: Discrete Choice Modeling (Random Utility Theory)](#stage-1-discrete-choice-modeling-random-utility-theory)
  - [Stage 2: Purchase Price Optimization](#stage-2-purchase-price-optimization)
  - [Stage 3: Game-Theoretic Competitive Formulation](#stage-3-game-theoretic-competitive-formulation)
  - [Stage 4: Monte Carlo Risk & Uncertainty Quantification](#stage-4-monte-carlo-risk--uncertainty-quantification)
- [Empirical Findings & Strategic Insights](#-empirical-findings--strategic-insights)
- [Repository Structure](#-repository-structure)
- [Installation & Reproducibility Guide](#-installation--reproducibility-guide)
- [Automated Pipeline & CI/CD Workflow](#-automated-pipeline--cicd-workflow)
- [Tech Stack](#-tech-stack)
- [Citation](#-citation)
- [Author & Contact](#-author--contact)

---

## 📖 Executive Summary

In circular economy supply chains, **Baling Centers (BC)** operate as pivotal consolidation hubs responsible for aggregating, inspecting, compacting, and delivering recovered wastepaper (OCC, ONP, and mixed grades) to downstream paper mills. However, raw material acquisition in wastepaper markets is notoriously decentralized, price-volatile, and driven by informal supplier networks. Traditional procurement models rely predominantly on deterministic single-attribute pricing, often overlooking that suppliers evaluate buyers based on a complex bundle of operational attributes, including payment immediacy, collection/transportation assistance, quality deduction thresholds, and business relationship tenure.

This project delivers an **end-to-end behavioral procurement optimization framework** that bridges empirical econometrics with operational decision science:
1. **Behavioral Choice Estimation**: Quantifies supplier utility and decision determinants using **Binary Logistic Discrete Choice Modeling (DCM)** rooted in **Random Utility Theory (McFadden, 1974)**.
2. **Price & Volume Optimization**: Simulates procurement volume expansion against gross processing margin trade-offs across candidate pricing intervals.
3. **Strategic Game Formulation**: Analyzes simultaneous competitive dynamics between the Baling Center and regional competitors under varying supplier price sensitivities using **Non-Cooperative Game Theory and Best-Response Analysis**.
4. **Stochastic Risk Quantification**: Validates financial robustness via **Monte Carlo simulations** subjected to coupled volume and participation probability shocks.

---

## 📑 Academic Publication & Status

This project corresponds to the empirical methodology and analytical framework developed in the following academic research:

> **Title**: *Integrating Discrete Choice Modeling and Game Theoretic Optimization for Supplier Selection and Procurement Strategy in Wastepaper Recycling Supply Chains*  
> **Author**: Shafa Fariha Tsuraya\*  
> **Status**: **Accepted for Publication in a Peer-Reviewed Academic Journal (Forthcoming)**  
> **Publication Notice**: Full publication details, official digital object identifier (DOI), and volume/issue citations will be updated in this repository upon official release.

---

## 🔒 Data Governance & Confidentiality Notice

> [!IMPORTANT]
> **Commercial Non-Disclosure & Data Sanitization Policy**  
> The empirical models in this study were originally calibrated using internal field market research data gathered during the author's tenure as **Market Research Analyst Intern** at **Baling Center (BC)**.
> 
> To safeguard commercial confidentiality, trade secrets, proprietary cost structures, and supplier identities:
> - **Zero Exposure of Raw Commercial Records**: The primary confidential dataset (`Field Research.csv`), individual supplier names, GPS coordinates, and exact transactional cost accounting are strictly omitted from public repositories.
> - **Public Overview & Normalized Insights**: All econometric discussions, game-theoretic conclusions, and simulation insights presented in this documentation are reported in **generalized, qualitative, and high-level conceptual terms without citing proprietary commercial numbers**.
> - **Synthetic / Dummy Data Generator Provided**: A synthetic dataset generator script is provided in this repository (`generate_synthetic_data.py`), allowing researchers and engineers to reproduce the complete statistical and game-theoretic pipeline without violating corporate data governance protocols.

---

## 🏭 Industry Background & Problem Statement

```plaintext
[ Informal Collectors / Waste Banks / Aggregators ]
                     │
                     ▼ (Multi-attribute decision: Price, Distance, Payment, Pickup)
           ┌───────────────────┐
           │   Baling Center   │ ◄── Competitor Consolidation Hubs
           └─────────┬─────────┘
                     │ (Sorting, Quality Grading, Baling)
                     ▼
          [ Downstream Paper Mills ]
```

Recovered paper is an indispensable circular feedstock for paper packaging manufacturing, reducing virgin pulp extraction and operational carbon footprints. Baling Centers face unique structural procurement challenges:
- **Supplier Heterogeneity**: Suppliers range from micro-collectors and waste banks to large industrial scrap dealers with drastically varying supply capacities, vehicle accessibility, and cash-flow sensitivities.
- **Competitor Cannibalization**: Sourcing zones overlap with competitor baling hubs and local middlemen, leading to predatory bidding wars when supply tightens.
- **The Pricing Paradox**: Increasing purchase prices expands acquired volume but drastically erodes operational milling margins; conversely, conservative pricing causes suppliers to divert loads to competing hubs.
- **Non-Price Differentiators**: Field research demonstrates that factors such as on-site pickup logistics, transparent Destination Quality Control (DQC) grading, and cash settlement speed frequently outweigh marginal price differentials.

---

## 🔄 Integrated Decision Framework Architecture

The framework synthesizes behavioral econometrics, mathematical optimization, game-theoretic strategy, and stochastic risk analysis into a sequential four-stage decision workflow:

1. **Stage 1: Econometric Behavioral Modeling**
   - Conduct empirical field market research surveying active wastepaper suppliers across economic, logistical, quality, and operational attributes.
   - Execute feature engineering and multicollinearity diagnostics (Variance Inflation Factor analysis).
   - Calibrate binary logistic regression using Maximum Likelihood Estimation with backward stepwise model selection guided by the Akaike Information Criterion (AIC).
   - Evaluate model fit, odds ratios, and average marginal effects to identify primary drivers of supplier choice.

2. **Stage 2: Price & Volume Optimization**
   - Model the trade-off between purchase price adjustments, supplier conversion probabilities, and operational margins.
   - Compute expected acquired procurement volume as a probability-weighted function of supplier capacity.
   - Evaluate single-agent procurement profit curves across simulated pricing scenarios.

3. **Stage 3: Game-Theoretic Strategic Formulation**
   - Formulate a simultaneous non-cooperative game between the Baling Center and regional competing buyers.
   - Construct multi-attribute strategy profiles spanning purchase pricing, payment conditions (cash on delivery vs. credit terms), and pickup logistics.
   - Derive the strategic payoff matrix across varying levels of supplier price sensitivity.
   - Calculate composite strategic scores balancing profitability and volume market capture to identify dominant best-response strategies.

4. **Stage 4: Stochastic Risk & Uncertainty Quantification**
   - Stress-test the preferred procurement strategy using Monte Carlo simulation under simultaneous stochastic shocks.
   - Inject behavioral participation shocks and operational volume volatility.
   - Evaluate downside risk, Value-at-Risk profiles, and capital resilience across worst-case, base-case, and upside scenarios.

---

## 🔬 Methodology & Mathematical Formulations

### Stage 1: Discrete Choice Modeling (Random Utility Theory)

The supplier's decision to sell to the Baling Center is grounded in **Random Utility Theory (RUT)**. A supplier $n$ chooses alternative $i \in \{0, 1\}$ (where $1$ denotes choosing the Baling Center and $0$ denotes selecting an alternative buyer or retaining current channels) if and only if the perceived utility $U_{ni}$ exceeds all alternative utilities:

$$U_{ni} = V_{ni} + \varepsilon_{ni}$$

Where:
- $V_{ni} = \mathbf{x}_{ni}^\top \boldsymbol{\beta}$ is the deterministic systematic component explained by observable economic, operational, and material attributes.
- $\varepsilon_{ni}$ is the unobserved stochastic error term, assumed to follow an Independent and Identically Distributed (i.i.d.) Type I Extreme Value (Gumbel) distribution.

Under these standard assumptions, the probability $P_n$ that supplier $n$ selects the Baling Center takes the closed-form **Binary Logistic formulation**:

$$P_n(Y = 1 \mid \mathbf{x}_n) = \frac{\exp(\mathbf{x}_n^\top \boldsymbol{\beta})}{1 + \exp(\mathbf{x}_n^\top \boldsymbol{\beta})} = \frac{1}{1 + \exp(-\mathbf{x}_n^\top \boldsymbol{\beta})}$$

#### Candidate Feature Definitions
1. **`Quality_Index`**: Composite index evaluating wastepaper material cleanliness and moisture retention:
   $$\text{Quality Index} = \frac{(4 - \text{Moisture Score}) + (4 - \text{Impurities Score})}{2}$$
2. **`Source_Radius`**: Geographical road distance between supplier warehouse and the Baling Center.
3. **`Business_Age`**: Number of years the supplier has been in commercial operation:
   $$\text{Business Age} = \text{Current Year} - \text{Founding Year}$$
4. **`Supplier_Margin`**: Current trading margin captured by the supplier:
   $$\text{Supplier Margin} = P_{\text{current buyer}} - P_{\text{purchase}}$$
5. **`Payment_Match`**: Binary indicator ($1$ if BC payment terms match the supplier's preferred settlement timeline, $0$ otherwise).
6. **`Pickup_Match`**: Binary indicator ($1$ if the supplier requires on-site vehicle collection logistics, $0$ otherwise).
7. **`Weekly_Volume`**: Historical average collection capacity.
8. **`Skema_Potongan_DQC`**: Deduction scheme applied during factory gate quality inspection.

#### Parameter Estimation & Selection
Parameters were estimated via **Maximum Likelihood Estimation (MLE)**. Parsimonious specification was achieved using **Backward Stepwise Selection based on Akaike Information Criterion (AIC)**:

$$\text{AIC} = 2k - 2\ln(\hat{L})$$

where $k$ is the number of parameters and $\hat{L}$ is the maximized likelihood.

---

### Stage 2: Purchase Price Optimization

To evaluate purchase price decisions in isolation, multiple pricing adjustment scenarios $\Delta P$ were simulated relative to baseline market expectations.

For each supplier $n$, the adjusted purchase price is modeled as:

$$P_{n}^{\text{buy}} = P_{n}^{\text{expected}} + \Delta P$$

The total expected volume acquired is given by:

$$\mathbb{E}[\text{Volume}] = \sum_{n=1}^{N} P_n(\Delta P) \cdot \text{Volume}_n$$

The expected procurement profit function balances increased supply capture against reduced operating margin:

$$\mathbb{E}[\Pi(\Delta P)] = \sum_{n=1}^{N} \Big[ P_n(\Delta P) \cdot \text{Volume}_n \cdot C \cdot \big(\bar{P}_{\text{mill}} - P_n^{\text{buy}}\big) \Big]$$

Where $\bar{P}_{\text{mill}}$ is the downstream sales price realized upon selling baled material to the paper mill and $C$ is the mass conversion constant.

---

### Stage 3: Game-Theoretic Competitive Formulation

Because competitors inevitably react to unilateral pricing moves, procurement was modeled as a **Non-Cooperative Simultaneous Game in Normal Form**:

$$\Gamma = \langle \mathcal{N}, \{\mathcal{S}_i\}_{i \in \mathcal{N}}, \{\Pi_i\}_{i \in \mathcal{N}} \rangle$$

- **Players $\mathcal{N}$**: $\{\text{Baling Center (BC)}, \text{Regional Competitor Buyers}\}$.
- **BC Action Space $\mathcal{S}_{\text{BC}}$**:
  - `BC_Basic`: Baseline price, standard terms, no vehicle pickup.
  - `BC_Premium`: Aggressive price incentive, standard terms, vehicle pickup included.
  - `BC_Service_Plus`: Moderate price incentive, cash/instant payment matching, vehicle pickup included.
  - `BC_Aggressive`: Maximum price hike, standard terms, vehicle pickup included.
- **Competitor Action Space $\mathcal{S}_{\text{Comp}}$**:
  - `Competitor_Cash_Pickup`: Matching logistics and cash terms at baseline price.
  - `Competitor_Low_Price`: Aggressive cost suppression with standard services.
  - `Competitor_Price_Match`: Retaliatory price matching with full services.

#### Multi-Attribute Utility & Payoff Function
The relative choice probability for each strategy pair is governed by relative utility across price margins and service amenities:

$$U_{\text{BC}} = \beta_{\text{price}} \cdot \text{Margin}_{\text{BC}} + \beta_{\text{payment}} \cdot \text{Pay}_{\text{BC}} + \beta_{\text{pickup}} \cdot \text{Pick}_{\text{BC}} + \beta_{\text{qual}} \cdot \text{Quality}$$

$$P_{\text{BC}} = \frac{\exp(U_{\text{BC}})}{\exp(U_{\text{BC}}) + \exp(U_{\text{Comp}})}$$

#### Multi-Objective Strategic Evaluation
To prevent margin destruction while defending supplier volume share, strategies were ranked using a composite **Strategic Score**:

$$\text{Strategic Score} = w_1 \cdot \left(\frac{\mathbb{E}[\Pi]}{\max \mathbb{E}[\Pi]}\right) + w_2 \cdot \left(\frac{P_{\text{BC}}}{\max P_{\text{BC}}}\right)$$

where $w_1$ and $w_2$ represent management weights assigned to profit realization and market capture share, respectively.

---

### Stage 4: Monte Carlo Risk & Uncertainty Quantification

To stress-test the selected optimal strategy against market turbulence, a **Monte Carlo simulation** was executed across repeated iterations. In each iteration $k$:

1. **Participation Probability Shock**:  
   The baseline supplier choice probability is subjected to a stochastic perturbation:

   $$\tilde{P}_{n, k} = \max\left(0, \min\left(1, P_n + \varepsilon_{n, k}^{P}\right)\right)$$

   where $\varepsilon_{n, k}^{P} \sim \mathcal{N}(0, \sigma_P^2)$ represents random behavioral fluctuation.

2. **Supply Volume Volatility**:  
   Individual supply volume fluctuates according to operational shocks:

   $$\tilde{V}_{n, k} = V_n \cdot (1 + \varepsilon_{n, k}^{V})$$

   where $\varepsilon_{n, k}^{V} \sim \mathcal{N}(0, \sigma_V^2)$ reflects weekly delivery variance.

3. **Simulated Realized Profit**:  
   Total realized procurement profit for iteration $k$ is calculated as:

   $$\Pi_k = \sum_{n=1}^N \Big[ \tilde{P}_{n, k} \cdot \tilde{V}_{n, k} \cdot C \cdot (\bar{P}_{\text{mill}} - P_n^{\text{buy}}) \Big]$$

Empirical quantiles were evaluated across the distribution: Worst-Case Value-at-Risk ($5^{\text{th}}$ percentile), Base-Case Median ($50^{\text{th}}$ percentile), and Best-Case Upside ($95^{\text{th}}$ percentile).

---

## 📊 Empirical Findings & Strategic Insights

> [!NOTE]
> In compliance with commercial non-disclosure guidelines, the insights below summarize qualitative and strategic conclusions from the research without citing proprietary transactional figures.

### 1. Econometric Model Performance
- **Goodness-of-Fit**: The logit model demonstrated substantial convergence improvement over the null baseline, with the Likelihood Ratio test confirming high collective statistical significance across selected variables.
- **Classification & Discriminative Power**: The estimated model achieved strong discriminative ability (evaluated via ROC curve and classification accuracy), reliably differentiating between suppliers with high conversion potential and those committed to incumbent channels.

### 2. Behavioral Elasticities & Determinants of Choice
- **Material Quality Index (Strongest Positive Driver)**: Material cleanliness and low moisture/impurity levels represent the single most powerful determinant of partnership viability. High-quality wastepaper streams substantially reduce downstream sorting costs, enabling sustainable bilateral collaboration.
- **Business Longevity & Vendor Inertia**: Long-established suppliers exhibit significant inertia and strong loyalty toward existing buyers. Acquiring mature suppliers requires relational trust and tailored service packages rather than generic pricing adjustments.
- **Sourcing Radius & Transportation Logistics**: Sourcing distance serves as a natural friction point. However, providing dedicated vehicle pickup and transportation assistance effectively overcomes geographic distance, expanding the feasible procurement radius.

### 3. Price-Only vs. Multi-Attribute Strategy Comparison
- **Limitations of Price-Only Policies**: While unconstrained price increases improve supplier conversion in the short run, they rapidly compress gross operational margins. In competitive markets, unilateral price increases trigger retaliatory bidding by competitors, leaving buyers with thinner margins and volatile supply.
- **Game-Theoretic Dominance of Service Bundling**: The strategy combining **moderate pricing incentives, on-site vehicle pickup, and flexible payment settlement (`BC_Service_Plus`)** proved strategically dominant. It consistently outperformed aggressive price-war strategies across all evaluated competitor counter-moves and across varying levels of supplier price sensitivity.

### 4. Risk Resilience Under Market Uncertainty
- **Downside Protection**: Monte Carlo simulations confirmed that the service-oriented procurement strategy maintains robust profitability across stochastic market shocks.
- **Zero Loss Probability**: Even under combined downside volume drops and behavioral conversion fluctuations, simulated outcomes remained safely positive, validating that service-differentiated procurement acts as an effective operational buffer against market volatility.

---

## 📁 Repository Structure

```plaintext
wastepaper-procurement-optimization/
├── .github/
│   └── workflows/
│       └── ci.yml                 # Automated validation and CI workflow
├── data/
│   ├── sample_suppliers.csv       # Anonymized synthetic dataset (schema-compatible)
│   └── data_dictionary.md         # Detailed variable definitions and units
├── notebooks/
│   └── procurement_analysis.ipynb # End-to-end interactive research notebook
├── src/
│   ├── __init__.py
│   ├── data_loader.py             # Data ingestion and validation utilities
│   ├── discrete_choice.py         # Logit estimation, AIC selection, and odds ratios
│   ├── price_optimization.py      # Scenario simulation and margin curve analysis
│   ├── game_theory.py             # Payoff matrix construction and Nash equilibrium
│   ├── monte_carlo.py             # Stochastic risk simulation and VaR analysis
│   └── generate_synthetic_data.py # Safe dummy data generator for reproduction
├── tests/
│   ├── test_models.py             # Unit tests for econometric estimators
│   └── test_simulation.py        # Validation for Monte Carlo stability
├── .gitignore
├── LICENSE
├── requirements.txt               # Pinned Python package dependencies
└── README.md                      # Project documentation
```

---

## 🚀 Installation & Reproducibility Guide

### 1. Clone the Repository
```bash
git clone https://github.com/shafafariha/wastepaper-procurement-optimization.git
cd wastepaper-procurement-optimization
```

### 2. Set Up Virtual Environment
- **Windows (PowerShell)**:
  ```powershell
  python -m venv venv
  .\venv\Scripts\Activate.ps1
  ```
- **Linux / macOS**:
  ```bash
  python3 -m venv venv
  source venv/bin/activate
  ```

### 3. Install Required Dependencies
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Generate Synthetic Data
To execute the pipeline safely without accessing proprietary corporate records, run the synthetic dataset generator:
```bash
python src/generate_synthetic_data.py --samples 100 --output data/sample_suppliers.csv
```

### 5. Run the End-to-End Pipeline
Execute the complete analysis or launch the Jupyter notebook:
```bash
# Run modular pipeline
python -m src.discrete_choice
python -m src.game_theory
python -m src.monte_carlo

# Or explore interactively
jupyter notebook notebooks/procurement_analysis.ipynb
```

---

## 🤖 Automated Pipeline & CI/CD Workflow

This repository includes an automated GitHub Actions workflow (`.github/workflows/ci.yml`) to ensure full reproducibility and publication-ready health checks upon every push:

```yaml
name: Model Pipeline & Validation CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  validate-pipeline:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Codebase
        uses: actions/checkout@v4

      - name: Set up Python Environment
        uses: actions/setup-python@v5
        with:
          python-version: '3.10'
          cache: 'pip'

      - name: Install Dependencies
        run: |
          pip install --upgrade pip
          pip install -r requirements.txt

      - name: Generate Synthetic Benchmark Data
        run: |
          python src/generate_synthetic_data.py --samples 100 --output data/sample_suppliers.csv

      - name: Run Econometric & Game Theory Tests
        run: |
          pytest tests/ -v
```

---

## 🛠️ Tech Stack

| Domain | Tools & Libraries |
| :--- | :--- |
| **Core Language** | [Python 3.10+](https://www.python.org/) |
| **Econometrics & Statistics** | [Statsmodels](https://www.statsmodels.org/), [SciPy](https://scipy.org/) |
| **Data Manipulation** | [Pandas](https://pandas.pydata.org/), [NumPy](https://numpy.org/) |
| **Machine Learning & Metrics**| [Scikit-Learn](https://scikit-learn.org/) |
| **Scientific Visualization** | [Matplotlib](https://matplotlib.org/), [Seaborn](https://seaborn.pydata.org/) |
| **Testing & CI/CD** | [Pytest](https://pytest.org/), [GitHub Actions](https://github.com/features/actions) |

---

## 📑 Citation

If you find this methodology, econometric formulation, or game-theoretic framework useful in your research or industrial operations, please cite the forthcoming paper:

```bibtex
@article{tsuraya2026procurement,
  author    = {Shafa Fariha Tsuraya},
  title     = {Integrating Discrete Choice Modeling and Game Theoretic Optimization for Supplier Selection and Procurement Strategy in Wastepaper Recycling Supply Chains},
  journal   = {Peer-Reviewed Academic Journal},
  year      = {2026},
  note      = {Accepted for Publication (Forthcoming)}
}
```

---

## 👤 Author & Contact

**Shafa Fariha Tsuraya**  
- **Role**: Market Research Analyst / Data & AI Engineer  
- **Email**: [shafafaraya@gmail.com](mailto:shafafaraya@gmail.com)  
- **LinkedIn**: [Shafa Fariha Tsuraya](https://www.linkedin.com/in/shafa-fariha-tsuraya/)  
- **GitHub**: [@shafafariha](https://github.com/shafafariha)  
- **Medium**: [@shafafaraya](https://medium.com/@shafafaraya)  

---
*Developed with rigorous data privacy compliance and open-source reproducibility standards.*
