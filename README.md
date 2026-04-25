# Emergency Department Wait Time Prediction Using Machine Learning

## Project Overview

This repository contains the full project for **CSCI-7090-A-O1E — Data Science & Machine Learning** at Georgia Southern University. The project applies Machine Learning (ML) to predict Emergency Department (ED) length of stay (LOS) as a continuous variable using the publicly available Hospital Emergency Room Visits dataset (Kaggle, CC0 license).

We extend prior work along four axes typically treated in isolation in the recent ED-ML literature:

- **Continuous Regression:** predicting ED LOS in minutes rather than the binary "prolonged vs. not prolonged" classification used in most published studies.
- **Triage-Level Segmentation:** evaluating model performance across all five Emergency Severity Index (ESI) levels rather than collapsing to a single pooled metric.
- **Explainable AI:** applying SHAP TreeExplainer to the best gradient-boosted model and reporting global feature importance for clinical interpretability.
- **Demographic Fairness Audit:** disaggregating MAE and RMSE across race/ethnicity, gender, and age group to surface subgroup-level disparities that pooled metrics hide.

To our knowledge this is the first study to combine all four on a single publicly accessible dataset.

---

## Authors

| Name | Role | Email |
|------|------|-------|
| Vandan Patel | Team Lead | vp04406@georgiasouthern.edu |
| Annagrace Howell | Developer | ag29516@georgiasouthern.edu |
| Yasmin Rocio Orduz Landazabal | Data Analyst | yo00553@georgiasouthern.edu |

**Instructor:** Prof. Vijayalakshmi Ramasamy, Ph.D.
**Course:** CSCI-7090-A-O1E — Data Science & Machine Learning
**Institution:** Georgia Southern University
**Semester:** Spring 2026

---

## Repository Structure

**Milestone 1 — Literature Review**
- `Team_3_Literature_Review.pdf` — Compiled SLR PDF
- `Literature_Review_ED_WaitTime.xlsx` — Synthesis of all 17 reviewed articles
- `Machine Learning Project Presentation.pptx` — Slides
- `Machine Learning Project Presentation-2.pdf` — Slides (PDF)

**Milestone 2 — Data Wrangling & EDA**
- `Team3_Milestone2_ED_WaitTime.ipynb` — Notebook
- `Team3_Milestone2.pdf` — Notebook PDF
- `Team3_Milestone2.pptx` — Slides
- `team3_ed_waittime_cleaned.csv` — Cleaned dataset (9,216 visits, 26 features)

**Milestone 3 — Final ML Pipeline**
- `Team3_Milestone3_ED_WaitTime.ipynb` — Final ML notebook (Linear, Ridge, Random Forest, XGBoost, LightGBM + SHAP + ESI + fairness)
- `Team3_Milestone3_ED_WaitTime.pdf` — PDF of executed notebook

**Final Paper**
- `main.tex` — IEEE LaTeX source
- `Team3_Final_Paper.pdf` — Compiled paper (10 pages)
- `Team3_Draft_Paper.pdf` — Earlier draft (kept for record)

---

## Research Questions

The project is structured around two research questions, each chosen to surface a different facet of model trustworthiness:

- **RQ1 (Predictive accuracy and generalizability across triage levels).** Can supervised regression models trained on routinely collected ED triage data predict patient LOS in minutes with materially lower error than naive baselines, and does that accuracy generalize across all five ESI triage levels, or is it driven by a single dominant sub-population?

- **RQ2 (Explainability, interpretability, and demographic fairness).** Which features actually drive the model's LOS predictions according to SHAP attribution, do those drivers align with clinical intuition and prior interpretable-ML studies, and does the resulting model produce equitable error across subgroups defined by race/ethnicity, gender, and age?

---

## Key Results

| Metric | Value |
|---|---|
| Best model (Test MAE) | **Ridge Regression — 89.09 min** |
| Random Forest Test MAE | 91.03 min |
| XGBoost Test MAE | 93.80 min |
| LightGBM Test MAE | 93.42 min |
| Naive baseline (predict mean) | 98.71 min |
| Best model R² | 0.141 |
| Top SHAP feature | `acuity` (mean &#124;SHAP&#124; = 46.07, ~6.4× the next feature) |
| ESI-stratified MAE range | 36.96 (ESI 5) — 130.28 (ESI 2) |
| Race/ethnicity MAE gap | 15.26 minutes |
| Gender MAE gap | 1.03 minutes |
| Age group MAE gap | 11.50 minutes |

A notable counter-finding from our experiments: on this moderately sized dataset (~9,000 visits), regularized linear regression matched or slightly outperformed the gradient-boosted models that dominate the recent ED-ML literature. We discuss this honestly in the paper as a dataset-size and signal-density effect rather than tuning around it.

---

## Milestone 1 — Systematic Literature Review

**Files:** `main.tex`, `Team_3_Literature_Review.pdf`, `Literature_Review_ED_WaitTime.xlsx`, `Machine Learning Project Presentation.pptx`

A PRISMA-style review analyzing 17 peer-reviewed articles (12 directly on ED ML + 5 methodological foundations: Morley 2018 on overcrowding, Gilboy 2012 ESI Implementation Handbook, Breiman 2001 Random Forests, Chen & Guestrin 2016 XGBoost, Ke et al. 2017 LightGBM). The synthesis spreadsheet groups every article by 13 fields (paper title, authors, year, source, research question, methodology, results, strengths, limitations, relevance to our project, IEEE citation, etc.) and is structured as the input to the literature review section of the final paper.

### Identified Research Gaps

Five gaps are recurrent across the twelve directly comparable studies:

1. Continuous-regression formulation is rare (10/12 studies use binary classification)
2. Triage-level segmentation across all five ESI levels is absent
3. SHAP-based interpretability is uneven (only 4/12 apply it)
4. Reproducibility is limited (9/12 use proprietary single-center data)
5. Fairness audits are scarce (only 2/12, both restricted to classification)

Our work targets all five gaps simultaneously on a single publicly-released dataset.

---

## Milestone 2 — Data Collection, Wrangling & Visualization

**Files:** `Team3_Milestone2_ED_WaitTime.ipynb`, `Team3_Milestone2.pdf`, `team3_ed_waittime_cleaned.csv`

### Dataset

| Field | Value |
|-------|-------|
| Name | Hospital Emergency Room Visits Dataset |
| Provider | Kaggle — drnimishadavis |
| URL | https://www.kaggle.com/datasets/drnimishadavis/hospital-emergency-room-dataset |
| Access date | March 2026 |
| License | CC0 — Public Domain |
| Records | 9,216 ED visits |
| Raw features | 17 |
| Final features (after engineering) | 26 |
| Target variable | `ed_los_minutes` (continuous, in minutes) |

### Preprocessing Highlights

- Median imputation for vital signs (≤12% missingness); mode imputation for sparse categoricals
- Clinical reference bounds enforced (HR 30–250 bpm, SBP 60–280 mmHg, LOS 5–4,320 min)
- Five engineered features: `shock_index` (HR/SBP), `pulse_pressure` (SBP−DBP), `arrival_shift`, `is_weekend`, `age_group`
- Label encoding for categoricals; StandardScaler normalization on all 19 numeric model features

---

## Milestone 3 — Final ML Pipeline

**Files:** `Team3_Milestone3_ED_WaitTime.ipynb`, `Team3_Milestone3_ED_WaitTime.pdf`

The Milestone 3 notebook is the final ML pipeline that produces every numerical result in `Team3_Final_Paper.pdf`. The notebook is organized into clearly headed sections, uses modular functions in every code cell, and includes a `main()` function that runs the full pipeline end-to-end.

### Notebook Structure

1. **Setup** — imports, constants, reproducibility seed
2. **Data Loading** — pulls the cleaned CSV directly from this GitHub repo (no upload needed)
3. **Feature Set** — 19 standardized regression features grouped by clinical role
4. **Modeling** — trains and benchmarks five regressors (Linear, Ridge, Random Forest, XGBoost, LightGBM) with 80/20 holdout + 5-fold CV
5. **Interpretability** — SHAP TreeExplainer on LightGBM with global feature ranking
6. **Stratified Evaluation** — Ridge refit within each of the five ESI levels
7. **Fairness Audit** — MAE and RMSE disaggregated across race/ethnicity, gender, and age group
8. **`main()`** — single function that runs everything end-to-end and prints all four result tables
9. **Summary and Key Takeaways** — interpretation and counter-findings vs. literature

### How to Run

**Option A — Open directly in Google Colab (recommended):**

[Click here to open in Colab](https://colab.research.google.com/github/Yasmin-maker1/Emergency-Department-Wait-Time-Prediction-Using-Machine-Learning/blob/main/Team3_Milestone3_ED_WaitTime.ipynb)

Then click `Runtime → Run all`. The notebook pulls the cleaned CSV directly from this repository — no manual upload required.

**Option B — Local Jupyter:**

    git clone https://github.com/Yasmin-maker1/Emergency-Department-Wait-Time-Prediction-Using-Machine-Learning.git
    cd Emergency-Department-Wait-Time-Prediction-Using-Machine-Learning
    pip install xgboost lightgbm shap scikit-learn pandas matplotlib seaborn
    jupyter notebook Team3_Milestone3_ED_WaitTime.ipynb

Total runtime: approximately 2–3 minutes (the 5-model benchmark with cross-validation is the slowest step).

---

## Final Paper

**File:** `Team3_Final_Paper.pdf` (10 pages, IEEE conference format)

The paper consolidates the literature review, methodology, results, discussion, and conclusion. All numerical tables are collected in the Appendix and structured as synthesis tables grouped by theme/method/clinical role. The LaTeX source (`main.tex`) is included for reproducibility.

### Compile Locally

Requires a LaTeX distribution (TeX Live, MiKTeX, or MacTeX) with `IEEEtran.cls` available:

    pdflatex main.tex
    pdflatex main.tex

---

## References

The final paper cites 24 references (12 directly comparable ED-ML studies + 12 supporting methodology and fairness foundations). The full reference list is in the paper's bibliography section. Highlights:

- Wu et al. (2025) — most directly comparable continuous-regression study (LightGBM, 187k records)
- Wang et al. (2025) — fairness-focused interpretable XGBoost on prolonged ED wait time
- Ricciardi et al. (2024) — large-scale (~500k records) prolonged-LOS classification
- Lett et al. (2025) — intersectional debiasing for ED admission prediction
- Lundberg & Lee (2017) — SHAP foundation
- Chen & Guestrin (2016) — XGBoost; Ke et al. (2017) — LightGBM; Breiman (2001) — Random Forests

Full bibliographic detail is provided in `Team3_Final_Paper.pdf` and in the consolidated `Literature_Review_ED_WaitTime.xlsx`.

---

## Project Context

This work was conducted as part of the **CSCI-7090 Data Science and Machine Learning** course project (Team 3) at Georgia Southern University, Spring 2026.
