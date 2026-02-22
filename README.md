# Emergency Department Wait Time Prediction: Systematic Literature Review

## Project Overview
This repository contains a Systematic Literature Review (SLR) exploring the application of Machine Learning (ML) to predict Emergency Department (ED) wait times and length of stay (LOS). 

By synthesizing research from 2022–2025, this project evaluates the effectiveness of gradient boosting models (XGBoost, LightGBM) and identifies critical research gaps. Our project specifically addresses these gaps by implementing:
* **Continuous Regression:** Moving beyond binary classification to predict exact wait times in minutes.
* **Triage-Level Segmentation:** Analyzing performance across different ESI (Emergency Severity Index) levels.
* **Explainable AI:** Utilizing SHAP (SHapley Additive exPlanations) for clinical transparency.
* **Reproducibility:** Benchmarking against the publicly available MIMIC-IV-ED dataset.

---

## Authors
* **Vandan Patel** - [vp04406@georgiasouthern.edu](mailto:vp04406@georgiasouthern.edu)
* **Annagrace Howell** - [ag29516@georgiasouthern.edu](mailto:ag29516@georgiasouthern.edu)
* **Yasmin Rocio Orduz Landazabal** - [yo00553@georgiasouthern.edu](mailto:yo00553@georgiasouthern.edu)

---

## Technical Specifications
* **Template:** IEEE Conference Format (`IEEEtran`)
* **Source File:** `main.tex`
* **Language:** LaTeX

---

## Steps to Compile Locally

To generate the final PDF from the source files, follow these instructions:

### Prerequisites
Ensure you have a LaTeX distribution installed (e.g., **MiKTeX**, **TeX Live**, or **MacTeX**).

### Compilation Commands
Run the following sequence in your terminal or LaTeX editor (such as TeXstudio or VS Code) to ensure all citations and references are correctly linked:

1.  **Generate initial layout:**
    ```bash
    pdflatex main.tex
    ```
2.  **Process citations:**
    ```bash
    bibtex main
    ```
3.  **Update bibliography:**
    ```bash
    pdflatex main.tex
    ```
4.  **Finalize references and numbering:**
    ```bash
    pdflatex main.tex
    ```

The resulting file will be `main.pdf`.

---

## Project Context
This work was conducted as part of the **CSC7090 Data Science and Machine Learning** course project (Team 3) at **Georgia Southern University**, February 2026.
