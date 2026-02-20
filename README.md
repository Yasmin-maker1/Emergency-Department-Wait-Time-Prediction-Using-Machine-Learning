# Emergency-Department-Wait-Time-Prediction-Using-Machine-Learning

### Systematic Literature Review — Data Science & Machine Learning Course


![Status](https://img.shields.io/badge/Status-In%20Progress-yellow)
![Dataset](https://img.shields.io/badge/Dataset-MIMIC--IV--ED-blue)
![Tools](https://img.shields.io/badge/Tools-Python%20%7C%20scikit--learn%20%7C%20XGBoost%20%7C%20SHAP-green)

---

## Project Overview

This repository contains the Systematic Literature Review (SLR) for our machine learning course project. The project investigates how supervised machine learning can predict patient wait times in Emergency Departments (EDs) using the publicly available MIMIC-IV-ED dataset.

ED overcrowding is a recognized global healthcare problem. Prolonged wait times are associated with increased patient mortality, reduced care quality, and higher rates of patients leaving without being seen. By training ML models on routinely collected triage data, we aim to produce accurate, interpretable wait time predictions that can support real-time clinical decision-making.

---

## Research Question

How can supervised machine learning algorithms trained on ED triage data accurately predict patient wait times, and what approaches produce the most clinically interpretable and generalizable models?

---

## Dataset

**MIMIC-IV-ED — Medical Information Mart for Intensive Care IV, Emergency Department Module**

| Property | Details |
|----------|---------|
| Source | Beth Israel Deaconess Medical Center, Boston, MA |
| Time Period | 2011 – 2019 |
| Size | ~425,000 ED visits |
| Access | Free (requires PhysioNet account + data use agreement) |
| Link | https://physionet.org/content/mimic-iv-ed/2.2/ |

> **Note:** Do NOT upload the raw dataset files to this repository. Each team member must create a free PhysioNet account and sign the data use agreement independently to download the data.

---

## Tools & Technologies

| Tool | Purpose |
|------|---------|
| Python 3.x | Main programming language |
| pandas & NumPy | Data loading, cleaning, and manipulation |
| scikit-learn | Baseline ML models (Random Forest, Logistic Regression) |
| XGBoost / LightGBM | Primary gradient boosting predictors |
| SHAP | Model interpretability and feature importance |
| matplotlib & seaborn | Data visualization |
| LaTeX (IEEE template) | Academic document formatting |
| Overleaf | Collaborative LaTeX editing (linked to this repository) |

---

## Repository Structure
```
ED-WaitTime-Prediction-SLR/
│
├── README.md
│
├── latex/
│   ├── main.tex               # Main LaTeX source file (IEEE template)
│   ├── references.bib         # Bibliography file
│   └── sections/
│       ├── abstract.tex
│       ├── introduction.tex
│       ├── methodology.tex
│       ├── literature_review.tex
│       └── synthesis_conclusion.tex
│
├── docs/
│   ├── Literature_Review_ED_WaitTime.docx
│   └── Literature_Review_ED_WaitTime.xlsx
│
└── Literature_Review_ED_WaitTime.pdf
```

---

## How to Compile the LaTeX Document Locally

**Requirements:** TeX Live, MiKTeX, or MacTeX installed on your machine.
```bash
# 1. Clone the repository
git clone https://github.com/YOUR-USERNAME/YOUR-REPO-NAME.git
cd YOUR-REPO-NAME

# 2. Navigate to the latex folder
cd latex

# 3. Compile (run the sequence below for references to resolve correctly)
pdflatex main.tex
bibtex main
pdflatex main.tex
pdflatex main.tex

# 4. Output: main.pdf
```

You can also upload the contents of the `latex/` folder to Overleaf and compile directly there without any local installation.

---

## Team Members

| Name | Role |
|------|------|
| Yasmin Rocio Orduz Landazabal | Team Lead / Introduction & Synthesis |
| Annagrace Howell | Literature Review — Articles 1, 2 & 3 |
| Vandan Patel | Literature Review — Articles 4, 5 & 6 / Developer |

---

## Project Status

| Milestone | Due Date | Status |
|-----------|----------|--------|
| Topic Selection | Week 1 | Done |
| Literature Collection | Week 2 | Done |
| SLR Document (LaTeX) | Feb 21, 2026 | In Progress |
| PowerPoint Presentation | Milestone 2 | Pending |
| Project Implementation | TBD | Pending |
