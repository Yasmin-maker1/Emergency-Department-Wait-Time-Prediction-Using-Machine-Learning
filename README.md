# Emergency Department Wait Time Prediction Using Machine Learning

## Project Overview

This repository contains the full project for **CSCI-7090-A-O1E — Data Science & Machine Learning** at Georgia Southern University. The project applies Machine Learning (ML) to predict Emergency Department (ED) wait times and length of stay (LOS) using the publicly available MIMIC-IV-ED dataset.

By synthesizing research from 2022–2025, this project evaluates the effectiveness of gradient boosting models (XGBoost, LightGBM) and addresses critical research gaps identified in our systematic literature review:

- **Continuous Regression:** Moving beyond binary classification to predict exact wait times in minutes.
- **Triage-Level Segmentation:** Analyzing performance across all 5 ESI (Emergency Severity Index) levels.
- **Explainable AI:** Utilizing SHAP (SHapley Additive exPlanations) for clinical transparency.
- **Reproducibility:** Benchmarking against the publicly available MIMIC-IV-ED dataset.
- **Fairness Analysis:** Assessing model performance across demographic subgroups (race, gender, insurance type).

---

## Authors

| Name | Role | Email |
|------|------|-------|
| Vandan Patel | Team Lead | vp04406@georgiasouthern.edu |
| Annagrace Howell | Developer | ag29516@georgiasouthern.edu |
| Yasmin Rocio Orduz Landazabal | Data Analyst | yo00553@georgiasouthern.edu |

**Instructor:** Ph.D. Vijayalakshmi Ramasamy  
**Course:** CSCI-7090-A-O1E — Data Science & Machine Learning  
**Institution:** Georgia Southern University

---

## Repository Structure

```
/
├── README.md
├── main.tex                                      # Milestone 1 — LaTeX source (IEEE format)
├── Team_3_Literature_Review.pdf                  # Milestone 1 — Compiled literature review PDF
├── Machine_Learning_Project_Presentation.pdf     # Milestone 1 — Presentation slides
├── Team3_Milestone2_ED_WaitTime.ipynb            # Milestone 2 — Data wrangling & EDA notebook
└── team3_ed_waittime_cleaned.csv                 # Milestone 2 — Cleaned ML-ready dataset
```

---

## Milestone 1 — Systematic Literature Review ✅

**Files:** `main.tex`, `Team_3_Literature_Review.pdf`, `Machine_Learning_Project_Presentation.pdf`

### Overview
A PRISMA-style systematic literature review analyzing 12 peer-reviewed articles (2022–2025) on ML-based ED wait time and length-of-stay prediction, sourced from IEEE Xplore, PubMed, ACM Digital Library, Springer, Nature, and JAMA Network Open.

### Key Findings
- Gradient boosting ensemble methods (XGBoost, LightGBM, Random Forest) consistently outperform traditional clinical scoring systems across all reviewed studies
- The MIMIC-IV-ED public dataset has emerged as the community reproducibility benchmark, appearing in 3 of 12 reviewed studies
- **Critical gaps identified:** No single study combines continuous regression + SHAP interpretability + ESI-level segmentation + demographic fairness on a public dataset

### Technical Specifications
- **Template:** IEEE Conference Format (`IEEEtran`)
- **Source File:** `main.tex`
- **Language:** LaTeX

### Steps to Compile Locally

Ensure you have a LaTeX distribution installed (e.g., MiKTeX, TeX Live, or MacTeX), then run the following sequence in your terminal:

```bash
pdflatex main.tex
bibtex main
pdflatex main.tex
pdflatex main.tex
```

The resulting file will be `main.pdf`.

---

## Milestone 2 — Data Collection, Wrangling & Visualization ✅

**Notebook:** `Team3_Milestone2_ED_WaitTime.ipynb`  
**Cleaned Dataset:** `team3_ed_waittime_cleaned.csv`

### Dataset
| Field | Detail |
|-------|--------|
| **Name** | MIMIC-IV-ED (v2.2) |
| **Provider** | PhysioNet / Beth Israel Deaconess Medical Center, Boston MA |
| **URL** | https://physionet.org/content/mimic-iv-ed/2.2/ |
| **Size** | ~400,000 ED visits (2011–2019) |
| **Access** | Requires free PhysioNet credentialing (CITI training) |
| **Target variable** | `ed_los_minutes` — continuous ED length-of-stay in minutes |

### How to Run the Notebook
1. Open `Team3_Milestone2_ED_WaitTime.ipynb` in [Google Colab](https://colab.research.google.com/)
2. Complete PhysioNet credentialing and download MIMIC-IV-ED v2.2
3. Upload `triage.csv.gz` and `edstays.csv.gz` to your Colab session
4. Update the file paths in cell A2 if needed
5. Run all cells top-to-bottom: **Runtime → Run all**
6. The cleaned CSV `team3_ed_waittime_cleaned.csv` is exported automatically

### What the Notebook Covers

**Part A — Data Acquisition & Description (10 pts)**
- Dataset source documentation (URL, license, citation, access date)
- Full data dictionary (19 features with name, type, description, example values)
- Relevance statement connecting dataset to literature review findings

**Part B — Data Wrangling & Preprocessing (20 pts)**
- Missing value analysis with completeness visualization and justified imputation
- Data type conversion (timestamps parsed, label encoding, ordinal casting)
- Outlier detection using IQR method and Z-score method with clinical bounds winsorization
- Feature engineering: `shock_index`, `pulse_pressure`, `arrival_hour`, `arrival_shift`, `is_weekend`
- StandardScaler normalization with written justification
- Before/after wrangling summary comparison table

**Part C — Exploratory Data Analysis & Visualization (15 pts)**
- 12 publication-quality figures with 2–4 sentence interpretations each
- Distribution plots for ED LOS, vital signs, and engineered features
- Pearson correlation heatmap with interpretation of strongest correlations
- Categorical analyses: ESI acuity levels, disposition, arrival transport mode
- Scatter plots of key features vs. target variable with trend lines
- Time-series trend analysis across 2011–2019
- Fairness preview: LOS distribution by gender and arrival transport mode

---

## Milestone 3 — Predictive Modeling 🔄 (Upcoming)

**Planned models:** XGBoost, Random Forest, Gradient Boosting  
**Evaluation metrics:** MAE, RMSE, R²  
**Additional analyses:**
- SHAP-based feature importance (patient-level and population-level)
- ESI triage-level subgroup performance analysis
- Demographic fairness assessment (race, gender, insurance type)

---

## Research Question

> How can supervised machine learning algorithms trained on routinely collected ED triage data accurately predict patient wait times, and what methodological approaches produce the most clinically interpretable and generalizable models?

---

## Key References

1. Johnson, A., et al. (2023). MIMIC-IV-ED (v2.2). PhysioNet. https://doi.org/10.13026/5ntk-km72
2. Xie, F., et al. (2022). Benchmarking emergency department prediction models. Scientific Data, 9, 658.
3. Wang, et al. (2025). Evaluating fairness of ML prediction of prolonged ED wait times. PLOS Digital Health, 4(3).
4. Wang, H., Sambamoorthi, N., et al. (2025). Interpretable ML models for prolonged ED wait time prediction. BMC Health Services Research, 25, 403.
5. Wu, W., et al. (2025). Development of an ED LOS prediction model based on ML. World Journal of Emergency Medicine, 16(3).
6. Lett, E., et al. (2025). Intersectional and marginal debiasing in ED admission predictions. JAMA Network Open, 8(5).
7. Sun, L., et al. (2024). ED-Copilot: Reduce ED wait time with language model diagnostic assistance. ICML 2024.

---

## Project Context

This work was conducted as part of the **CSC7090 Data Science and Machine Learning** course project (Team 3) at Georgia Southern University, 2026.
