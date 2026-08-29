# AI-nak

> **AI-nak — Regime-Aware Multimodal Market Intelligence & Portfolio Research System**

AI-nak is a research-oriented AI system designed to analyze financial markets using multiple sources of information instead of relying on a single price chart.

The system combines:

* Market prices and technical indicators
* Financial news and events
* Macroeconomic indicators
* Relationships between stocks
* Market regime detection
* Multimodal analysis
* Ensemble decision making
* Downside-aware portfolio allocation
* Explainable AI and natural-language trade memos

> **Project Status:** Phase 0 — Foundation & Team Setup
> **Project Type:** Research / Educational Prototype
> **Live Trading:** Not supported

---

# 1. Project Vision

Traditional trading systems often depend on a small set of signals.

AI-nak attempts to model the market more like a collaborative investment organization:

```text
                    AI-nak
                       │
        ┌──────────────┼──────────────┐
        │              │              │
        ▼              ▼              ▼
   Market Data      News Data      Macro Data
        │              │              │
        └──────────────┼──────────────┘
                       ▼
              Feature Engineering
                       │
        ┌──────────────┼──────────────┐
        ▼              ▼              ▼
      DMGN          Hawkes           VMSE
   Relationships   Event Decay     Market Regime
        │              │              │
        └──────────────┼──────────────┘
                       ▼
                     TMFT
              Multimodal Fusion
                       │
                       ▼
               Meta-Ensemble
                       │
                       ▼
                 Portfolio/RL
                       │
                       ▼
                 Risk Control
                       │
                       ▼
               SHAP + GenAI
                       │
                       ▼
                Trade Memo
```

---

# 2. The Seven AI-nak Layers

| Layer | Module                   | Purpose                                                     |
| ----- | ------------------------ | ----------------------------------------------------------- |
| 1     | **DMGN**                 | Understand relationships between stocks                     |
| 2     | **Hawkes Event Filter**  | Model how news/event impact decays                          |
| 3     | **VMSE**                 | Detect the current market regime                            |
| 4     | **TMFT**                 | Combine numerical, textual and chart information            |
| 5     | **Meta-Ensemble**        | Select/weight models based on market regime                 |
| 6     | **RL Portfolio Agent**   | Decide portfolio allocation while controlling downside risk |
| 7     | **GenAI Explainability** | Explain decisions in plain English                          |

---

# 3. One-Month Development Goal

The first milestone is **not** a production trading system.

Our goal is to build a complete research prototype:

```text
Historical Market Data
        +
Historical News
        +
Macro Data
        ↓
Feature Engineering
        ↓
AI-nak Models
        ↓
Trading Signal
        ↓
Portfolio Allocation
        ↓
Backtesting
        ↓
Risk Analysis
        ↓
Explainable Trade Memo
```

At the end of the first month, we should be able to run the complete pipeline on historical data.

---

# 4. Repository Structure

```text
AI-nak/
│
├── configs/
│   ├── base.yaml
│   ├── data.yaml
│   ├── model.yaml
│   ├── training.yaml
│   └── portfolio.yaml
│
├── data/
│   ├── raw/
│   │   ├── prices/
│   │   ├── news/
│   │   └── macro/
│   │
│   ├── interim/
│   │   ├── prices/
│   │   ├── news/
│   │   └── macro/
│   │
│   ├── processed/
│   │   ├── market/
│   │   ├── news/
│   │   ├── macro/
│   │   └── features/
│   │
│   └── external/
│
├── docs/
│   ├── architecture/
│   ├── modules/
│   └── experiments/
│
├── notebooks/
│   ├── 01_data_exploration/
│   ├── 02_baselines/
│   ├── 03_dmgn/
│   ├── 04_hawkes/
│   ├── 05_vmse/
│   ├── 06_tmft/
│   ├── 07_ensemble/
│   ├── 08_rl/
│   └── 09_evaluation/
│
├── src/
│   └── ainak/
│       │
│       ├── data/
│       │   ├── collectors/
│       │   ├── loaders/
│       │   ├── validators/
│       │   └── schemas/
│       │
│       ├── preprocessing/
│       │   ├── cleaning/
│       │   ├── alignment/
│       │   ├── normalization/
│       │   └── splits/
│       │
│       ├── features/
│       │   ├── technical/
│       │   ├── sentiment/
│       │   ├── macro/
│       │   ├── graph/
│       │   └── event/
│       │
│       ├── models/
│       │   ├── baselines/
│       │   ├── dmgn/
│       │   ├── hawkes/
│       │   ├── vmse/
│       │   ├── tmft/
│       │   └── ensemble/
│       │
│       ├── portfolio/
│       ├── explainability/
│       ├── backtesting/
│       ├── pipeline/
│       ├── utils/
│       └── constants/
│
├── scripts/
│   ├── download_data.py
│   ├── preprocess_data.py
│   ├── train.py
│   ├── evaluate.py
│   └── run_pipeline.py
│
├── tests/
│   ├── test_data/
│   ├── test_features/
│   ├── test_models/
│   ├── test_portfolio/
│   └── test_pipeline/
│
├── models/
│   ├── checkpoints/
│   ├── trained/
│   └── artifacts/
│
├── reports/
│   ├── experiments/
│   ├── figures/
│   ├── metrics/
│   └── final/
│
├── logs/
│
├── .env.example
├── .gitignore
├── main.py
├── pyproject.toml
├── requirements.txt
├── requirements-dev.txt
└── README.md
```

---

# 5. What Goes Where?

## `data/`

Contains datasets.

```text
raw        → Original downloaded data
interim    → Intermediate processing
processed  → ML-ready datasets
external   → External/reference datasets
```

### Important

Do **not** commit large datasets to GitHub.

The `.gitignore` already prevents this.

---

## `src/ainak/`

This contains the actual AI-nak source code.

This is the most important development directory.

---

## `notebooks/`

Use notebooks for:

* Data exploration
* Visualization
* Experiments
* Model analysis
* Research

Do not put the entire project logic inside notebooks.

If an experiment becomes reusable, move the implementation into:

```text
src/ainak/
```

---

## `models/`

Contains generated model artifacts.

```text
checkpoints/ → Temporary training checkpoints
trained/    → Final trained models
artifacts/  → Model-related files
```

Large model files should not normally be committed to GitHub.

---

## `reports/`

Contains:

* Experiment results
* Graphs
* Metrics
* Final reports

---

## `tests/`

Contains automated tests.

Every important module should eventually have tests.

---

# 6. Team Responsibilities

We have four members.

## Member 1 — Data Engineering

Primary ownership:

```text
data/
src/ainak/data/
src/ainak/preprocessing/
src/ainak/features/
```

Responsibilities:

* Price collection
* News collection
* Macro data
* Data cleaning
* Timestamp alignment
* Dataset generation
* Technical features

---

## Member 2 — ML/DL Engineering

Primary ownership:

```text
src/ainak/models/baselines/
src/ainak/models/hawkes/
src/ainak/models/vmse/
```

Responsibilities:

* XGBoost
* LSTM
* Hawkes Process
* VAE
* Market regime detection
* Model evaluation

---

## Member 3 — Graph & Multimodal Engineering

Primary ownership:

```text
src/ainak/models/dmgn/
src/ainak/models/tmft/
src/ainak/features/graph/
```

Responsibilities:

* Market graph construction
* GAT/GATv2
* DMGN embeddings
* Text encoder
* Image/chart encoder
* Multimodal fusion

---

## Member 4 — Portfolio & Intelligence Engineering

Primary ownership:

```text
src/ainak/models/ensemble/
src/ainak/portfolio/
src/ainak/backtesting/
src/ainak/explainability/
```

Responsibilities:

* Meta-Ensemble
* Regime gating
* Portfolio allocation
* RL environment
* SAC
* Risk management
* SHAP
* GenAI trade memo

---

# 7. Shared Directories

These directories are shared by the whole team:

```text
configs/
docs/
scripts/
tests/
src/ainak/pipeline/
src/ainak/utils/
```

Before modifying shared code, communicate with the team.

---

# 8. Initial Setup — Every Team Member

## Prerequisites

Install:

* Git
* Python 3.11
* VS Code recommended
* GitHub account

Check:

```powershell
git --version
```

```powershell
python --version
```

Recommended Python:

```text
Python 3.11.x
```

---

# 9. Clone the Repository

Every team member should clone the repository.

```powershell
git clone https://github.com/The-Techies-VIT-Pune/AI-nak.git
```

Example:

```powershell
git clone https://github.com/The-Techies-VIT-Pune/AI-nak.git
```

Enter the project:

```powershell
cd AI-nak
```

---

# 10. Create Python Virtual Environment

Each team member must create their **own** virtual environment.

```powershell
python -m venv .venv
```

Activate:

```powershell
.\.venv\Scripts\Activate.ps1
```

You should see:

```text
(.venv) PS C:\...\AI-nak>
```

---

# 11. If PowerShell Blocks Activation

Run:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

Then:

```powershell
.\.venv\Scripts\Activate.ps1
```

---

# 12. Install Project Dependencies

With `.venv` activated:

```powershell
python -m pip install --upgrade pip
```

Install project dependencies:

```powershell
pip install -r requirements.txt
```

Install development dependencies:

```powershell
pip install -r requirements-dev.txt
```

---

# 13. Verify Installation

Run:

```powershell
python -c "import numpy, pandas, sklearn, xgboost, torch, transformers, gymnasium, shap; print('AI-nak dependencies OK')"
```

Check PyTorch:

```powershell
python -c "import torch; print('PyTorch:', torch.__version__); print('CUDA available:', torch.cuda.is_available())"
```

---

# 14. Run the Project

Run:

```powershell
python main.py
```

Expected:

```text
==================================================
              AI-nak
==================================================
System initialization successful.

Phase 0: Project Foundation
Status: READY
==================================================
```

---

# 15. Run Tests

Run:

```powershell
pytest
```

Expected:

```text
1 passed
```

If tests fail, do not ignore the error.

Fix the environment/problem before beginning development.

---

# 16. Environment Variables

Copy:

```text
.env.example
```

to:

```text
.env
```

PowerShell:

```powershell
Copy-Item .env.example .env
```

Then add your own API keys to `.env`.

Example:

```env
AINAK_ENV=development

NEWS_API_KEY=
ALPHA_VANTAGE_API_KEY=

OPENAI_API_KEY=

LOG_LEVEL=INFO
```

### NEVER commit `.env`.

The `.gitignore` already prevents it.

---

# 17. Git Branch Architecture

We use three levels:

```text
main
  │
  └── develop
        │
        ├── feature/member1-...
        ├── feature/member2-...
        ├── feature/member3-...
        └── feature/member4-...
```

### `main`

Stable code only.

Rules:

```text
❌ No direct development
❌ No experimental code
❌ No unfinished features
```

---

### `develop`

Integration branch.

All completed features are merged here first.

```text
feature branch
      ↓
   Pull Request
      ↓
   develop
```

After the complete milestone is stable:

```text
develop
   ↓
 main
```

---

# 18. Team Branches

## Member 1

```text
feature/data-foundation
```

Create:

```powershell
git checkout develop
git pull origin develop
git checkout -b feature/data-foundation
git push -u origin feature/data-foundation
```

---

## Member 2

```text
feature/ml-baselines
```

Create:

```powershell
git checkout develop
git pull origin develop
git checkout -b feature/ml-baselines
git push -u origin feature/ml-baselines
```

---

## Member 3

```text
feature/dmgn-tmft
```

Create:

```powershell
git checkout develop
git pull origin develop
git checkout -b feature/dmgn-tmft
git push -u origin feature/dmgn-tmft
```

---

## Member 4

```text
feature/portfolio-intelligence
```

Create:

```powershell
git checkout develop
git pull origin develop
git checkout -b feature/portfolio-intelligence
git push -u origin feature/portfolio-intelligence
```

---

# 19. Daily Git Workflow

Before starting work:

```powershell
git checkout develop
git pull origin develop
```

Then switch to your feature branch:

```powershell
git checkout feature/YOUR-BRANCH
```

If your branch already exists:

```powershell
git pull origin feature/YOUR-BRANCH
```

---

# 20. During Development

Check changes:

```powershell
git status
```

View differences:

```powershell
git diff
```

Run tests:

```powershell
pytest
```

Then stage:

```powershell
git add .
```

Commit:

```powershell
git commit -m "feat: add price data collector"
```

Push:

```powershell
git push
```

---

# 21. Pull Request Workflow

Never directly merge your feature into `main`.

Use:

```text
Your Feature Branch
        │
        ▼
   Pull Request
        │
        ▼
     develop
        │
        ▼
Testing / Integration
        │
        ▼
       main
```

On GitHub:

```text
Compare:
feature/your-branch

Against:
develop
```

Create a Pull Request.

At least one other team member should review important changes.

---

# 22. Git Commit Convention

Use meaningful commit messages.

### Feature

```text
feat: add price data collector
feat: implement xgboost baseline
feat: add graph construction
```

### Bug Fix

```text
fix: correct timestamp alignment
fix: prevent future data leakage
```

### Refactoring

```text
refactor: reorganize feature pipeline
```

### Testing

```text
test: add price validator tests
```

### Documentation

```text
docs: update DMGN architecture
```

### Configuration

```text
chore: update dependencies
```

Avoid commits like:

```text
update
changes
final
final2
done
testing
new
```

---

# 23. Important Git Rules

### Rule 1

Never work directly on:

```text
main
```

### Rule 2

Don't commit:

```text
.venv/
.env
large datasets
model checkpoints
temporary files
```

### Rule 3

Pull before starting work:

```powershell
git checkout develop
git pull origin develop
```

### Rule 4

Run tests before pushing:

```powershell
pytest
```

### Rule 5

Keep commits small and meaningful.

### Rule 6

Don't modify another member's module without communicating first.

---

# 24. Data Rules

AI-nak is a time-series project.

The biggest danger is **data leakage**.

Never allow future information to enter training features.

Incorrect:

```text
2026-08-29 prediction
       ↑
using information from
2026-08-30
```

Correct:

```text
Past Data
   ↓
Features
   ↓
Prediction
   ↓
Future Outcome
```

Always respect timestamps.

---

# 25. Model Development Rules

Every model should have:

```text
1. Input definition
2. Output definition
3. Training procedure
4. Validation procedure
5. Evaluation metrics
6. Saved configuration
7. Experiment record
```

For example:

```text
XGBoost

Input:
Technical + macro features

Output:
P(next day UP)

Metrics:
Accuracy
F1
ROC-AUC
Sharpe
Maximum Drawdown
```

---

# 26. Experiment Tracking

For every experiment record:

```text
Experiment ID
Date
Model
Features
Hyperparameters
Training period
Validation period
Test period
Accuracy
F1
Sharpe
Maximum Drawdown
Observations
```

Store experiment documentation under:

```text
reports/experiments/
```

and:

```text
docs/experiments/
```

---

# 27. Development Philosophy

We are learning DL while building the project.

Therefore:

```text
Simple Model
     ↓
Understand
     ↓
Test
     ↓
Evaluate
     ↓
Improve
     ↓
Advanced Model
```

Do not immediately jump to:

```text
GATv2 + VAE + Transformer + RL
```

Build incrementally.

---

# 28. AI-nak Development Order

The project should follow:

```text
Phase 0
Foundation
    ↓
Phase 1
Data
    ↓
Phase 2
Baselines
    ↓
Phase 3
DMGN + Hawkes + VMSE
    ↓
Phase 4
TMFT + Ensemble
    ↓
Phase 5
Portfolio + RL + Explainability
    ↓
Final Backtesting
```

---

# 29. Phase 0 Definition of Done

Before starting Phase 1:

```text
[ ] Repository created
[ ] Git initialized
[ ] main branch created
[ ] develop branch created
[ ] Team feature branches created
[ ] Python 3.11 installed
[ ] Virtual environment created
[ ] requirements installed
[ ] .env configured locally
[ ] main.py runs
[ ] pytest passes
[ ] README understood by all members
[ ] Team responsibilities assigned
[ ] Git workflow understood
```

---

# 30. Current Team Status

| Member   | Responsibility           | Branch                           | Status |
| -------- | ------------------------ | -------------------------------- | ------ |
| Member 1 | Data Engineering         | `feature/data-foundation`        | ⬜      |
| Member 2 | ML/DL                    | `feature/ml-baselines`           | ⬜      |
| Member 3 | DMGN + TMFT              | `feature/dmgn-tmft`              | ⬜      |
| Member 4 | Portfolio + Intelligence | `feature/portfolio-intelligence` | ⬜      |

Update this table as development progresses.

---

# 31. Useful Commands Cheat Sheet

## Check current branch

```powershell
git branch
```

## Check status

```powershell
git status
```

## Get latest changes

```powershell
git pull origin develop
```

## Switch branch

```powershell
git checkout branch-name
```

## Create branch

```powershell
git checkout -b feature/my-feature
```

## Stage changes

```powershell
git add .
```

## Commit

```powershell
git commit -m "feat: description"
```

## Push

```powershell
git push
```

## See commit history

```powershell
git log --oneline
```

## See differences

```powershell
git diff
```

## Run tests

```powershell
pytest
```

## Run application

```powershell
python main.py
```

---

# 32. Recommended Daily Workflow

Every development session:

```text
1. Pull latest develop
       ↓
2. Switch to feature branch
       ↓
3. Understand today's task
       ↓
4. Implement
       ↓
5. Test
       ↓
6. Commit
       ↓
7. Push
       ↓
8. Create/update Pull Request
```

---

# 33. Communication Between Members

Before changing shared interfaces, communicate with the team.

For example, Member 1 creates:

```python
load_market_data()
```

Member 2 depends on it.

The expected input/output should be documented before Member 2 builds on it.

Use:

```text
docs/
```

for important interface decisions.

---

# 34. Architecture Principle

The dependency direction should generally remain:

```text
DATA
 ↓
PREPROCESSING
 ↓
FEATURES
 ↓
MODELS
 ↓
ENSEMBLE
 ↓
PORTFOLIO
 ↓
EXPLAINABILITY
 ↓
PIPELINE
```

Avoid reverse dependencies.

For example:

```text
❌ Data → Portfolio
❌ Features → RL
❌ DMGN → GenAI
❌ XGBoost → UI
```

Instead:

```text
Data
 ↓
Features
 ↓
Models
 ↓
Decision
 ↓
Explanation
```

---

# 35. Research vs Production Code

### Notebook

Good for:

```text
Experiment
Visualization
Research
Debugging
```

### `src/ainak`

Good for:

```text
Reusable implementation
Production-like pipeline
Testing
Integration
```

### `scripts`

Good for:

```text
Running workflows
Data download
Training
Evaluation
```

---

# 36. Final Objective

AI-nak should eventually support:

```text
                  AI-nak
                    │
                    ▼
              Market Universe
                    │
                    ▼
              Data Collection
                    │
                    ▼
           Feature Engineering
                    │
       ┌────────────┼────────────┐
       ▼            ▼            ▼
     DMGN         Hawkes        VMSE
       │            │            │
       └────────────┼────────────┘
                    ▼
                  TMFT
                    │
                    ▼
             Meta-Ensemble
                    │
                    ▼
              Risk Manager
                    │
                    ▼
             Portfolio/RL
                    │
                    ▼
               Backtesting
                    │
                    ▼
              SHAP Analysis
                    │
                    ▼
             GenAI Trade Memo
```

---

# 37. Disclaimer

AI-nak is a research and educational project.

It is intended for:

* Machine learning research
* Financial data analysis
* Portfolio simulation
* Backtesting
* Explainable AI research

It is **not financial advice** and should not be used for live trading without extensive independent validation, risk controls, and regulatory/compliance review.

---

# AI-nak — Build. Experiment. Validate. Explain.

> **Don't optimize for complexity. Optimize for measurable improvement.**
