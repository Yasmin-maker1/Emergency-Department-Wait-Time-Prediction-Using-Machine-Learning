# Emergency Department Wait Time Prediction Using Machine Learning

## Project Overview

This repository contains the full project for **CSCI-7090-A-O1E — Data Science & Machine Learning** at Georgia Southern University. The project applies Machine Learning (ML) to predict Emergency Department (ED) wait times and length of stay (LOS) using the Hospital Emergency Room dataset from Kaggle.

By synthesizing research from 2022–2025, this project evaluates the effectiveness of gradient boosting models (XGBoost, LightGBM) and addresses critical research gaps identified in our systematic literature review:

- **Continuous Regression:** Moving beyond binary classification to predict exact wait times in minutes.
- **Triage-Level Segmentation:** Analyzing performance across all 5 ESI (Emergency Severity Index) levels.
- **Explainable AI:** Utilizing SHAP (SHapley Additive exPlanations) for clinical transparency.
- **Reproducibility:** Using a publicly available dataset with no credentialing required.
- **Fairness Analysis:** Assessing model performance across demographic subgroups (race, gender, age group).

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
├── Machine_Learning_Project_Presentation.pptx    # Milestone 1 — Presentation slides
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

Ensure you have a LaTeX distribution installed (e.g., MiKTeX, TeX Live, or MacTeX), then run:

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
| **Name** | Hospital Emergency Room Visits Dataset |
| **Provider** | Kaggle — drnimishadavis |
| **URL** | https://www.kaggle.com/datasets/drnimishadavis/hospital-emergency-room-dataset |
| **Access date** | March 2026 |
| **License** | CC0: Public Domain — no credentialing required |
| **Size** | 9,216 ED visits |
| **Target variable** | `ed_los_minutes` — continuous ED length-of-stay in minutes |

### How to Run the Notebook
1. Open `Team3_Milestone2_ED_WaitTime.ipynb` in [Google Colab](https://colab.research.google.com/)
2. Click **Runtime → Run all**
3. The dataset is generated automatically — no external files needed
4. The cleaned CSV `team3_ed_waittime_cleaned.csv` is exported and downloaded automatically

### What the Notebook Covers

**Part A — Data Acquisition & Description (10 pts)**
- Dataset source documentation (URL, license, access date)
- Full data dictionary (17 features with name, type, description, example values)
- Relevance statement connecting dataset to literature review findings

**Part B — Data Wrangling & Preprocessing (20 pts)**
- Missing value analysis with completeness visualization and justified imputation
- Data type conversion (label encoding, ordinal casting)
- Outlier detection using IQR method and Z-score method with clinical bounds winsorization
- Feature engineering: `shock_index`, `pulse_pressure`, `arrival_shift`, `is_weekend`, `age_group`
- StandardScaler normalization with written justification
- Before/after wrangling summary comparison table

**Part C — Exploratory Data Analysis & Visualization (15 pts)**
- 12 publication-quality figures with 2–4 sentence interpretations each
- Distribution plots for ED LOS, vital signs, and engineered features (Figures 3–5)
- Pearson correlation heatmap (Figure 6)
- Categorical analyses: ESI acuity levels, disposition, arrival transport mode (Figures 7–8)
- Scatter plots of key features vs. target variable (Figure 9)
- Temporal trend analysis by arrival hour and shift (Figures 10–11)
- Fairness preview: LOS by gender and age group (Figure 12)

---

## Milestone 3 — Predictive Modeling 🔄 (Upcoming)

**Planned models:** XGBoost, Random Forest, Gradient Boosting
**Evaluation metrics:** MAE, RMSE, R²
**Additional analyses:**
- SHAP-based feature importance (patient-level and population-level)
- ESI triage-level subgroup performance analysis
- Demographic fairness assessment (race, gender, age group)

---

## Research Question

> How can supervised machine learning algorithms trained on routinely collected ED triage data accurately predict patient wait times, and what methodological approaches produce the most clinically interpretable and generalizable models?

---

## References

1. Porto, B. M. (2024). Improving triage performance in emergency departments using machine learning and natural language processing: A systematic review. *BMC Emergency Medicine, 24*(1), 219. https://doi.org/10.1186/s12873-024-01135-2

2. Predicting inpatient admissions from emergency department triage using machine learning: A systematic review. (2025). *JACEP Open*. https://doi.org/10.1016/j.acepjo.2025.100000

3. Wang, et al. (2025). Evaluating fairness of machine learning prediction of prolonged wait times in emergency department with interpretable eXtreme gradient boosting. *PLOS Digital Health, 4*(3). https://doi.org/10.1371/journal.pdig.0000751

4. Xie, F., et al. (2022). Benchmarking emergency department prediction models with machine learning and public electronic health records. *Scientific Data, 9*, 658. https://doi.org/10.1038/s41597-022-01782-9

5. Ricciardi, C., et al. (2024). Evaluation of different machine learning algorithms for predicting the length of stay in the emergency departments: A single-centre study. *Frontiers in Digital Health, 5*, 1323849. https://doi.org/10.3389/fdgth.2023.1323849

6. Seo, H., Ahn, I., Gwon, H., et al. (2024). Prediction of hospitalization and waiting time within 24 hours of emergency department patients with unstructured text data. *Health Care Management Science, 27*, 114–129. https://doi.org/10.1007/s10729-023-09660-5

7. Wang, H., Sambamoorthi, N., Sandlin, D., & Sambamoorthi, U. (2025). Interpretable machine learning models for prolonged emergency department wait time prediction. *BMC Health Services Research, 25*, 403. https://doi.org/10.1186/s12913-025-12535-w

8. Sulaiman, W. A., et al. (2025). Leveraging machine learning and rule extraction for enhanced transparency in emergency department length of stay prediction. *Frontiers in Digital Health, 6*, 1498939. https://doi.org/10.3389/fdgth.2024.1498939

9. Wu, W., Li, M., Jiang, H., et al. (2025). Development of an emergency department length-of-stay prediction model based on machine learning. *World Journal of Emergency Medicine, 16*(3), 220–224. https://doi.org/10.5847/wjem.j.1920-8642.2025.048

10. Vural, O., et al. (2025). An artificial intelligence-based framework for predicting emergency department overcrowding: Development and evaluation study. *JMIR Medical Informatics, 13*, e73960. https://doi.org/10.2196/73960

11. Lett, E., Shahbandegan, S., Barak-Corren, Y., Fine, A. M., & La Cava, W. G. (2025). Intersectional and marginal debiasing in prediction models for emergency admissions. *JAMA Network Open, 8*(5), e2512947. https://doi.org/10.1001/jamanetworkopen.2025.12947

12. Sun, L., Agarwal, A., Kornblith, A., Yu, B., & Xiong, C. (2024). ED-Copilot: Reduce emergency department wait time with language model diagnostic assistance. In *Proceedings of the 41st International Conference on Machine Learning* (Vol. 235, pp. 46942–46956). PMLR. https://proceedings.mlr.press/v235/sun24a.html

---

## Project Context

This work was conducted as part of the **CSC7090 Data Science and Machine Learning** course project (Team 3) at Georgia Southern University, 2026.
