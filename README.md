1. Project Title
Emergency Department Wait Time Prediction Using Machine Learning: A Systematic Literature Review

2. Brief Overview
This project is a Systematic Literature Review (SLR) that analyzes six peer-reviewed research articles (published between 2022 and 2025) focusing on supervised machine learning approaches for predicting patient wait times and length of stay in Emergency Departments. The study identifies a shift toward gradient boosting models (XGBoost, LightGBM) and highlights current research gaps such as the need for continuous regression, triage-level segmentation, and SHAP-based interpretability using public datasets like MIMIC-IV-ED.

3. Template Used
IEEE Template (IEEEtran conference class).

4. Steps to Compile Locally
Since you have a single main.tex file, follow these steps to generate the PDF:

Install a LaTeX Distribution:

Windows: MiKTeX or TeX Live.

Mac: MacTeX.

Linux: sudo apt-get install texlive-full.

Open the File: Use a LaTeX editor like TeXstudio, VS Code (with LaTeX Workshop extension), or Texmaker.

Compile Sequence: Because the document contains citations (\cite) and a bibliography section, you must run the compiler in this specific order to link the references correctly:

Step 1: Run pdflatex main.tex (Generates the initial PDF layout).

Step 2: Run bibtex main (Processes the citations).

Step 3: Run pdflatex main.tex (Incorporates the bibliography).

Step 4: Run pdflatex main.tex (Fixes the cross-references and numbering).

View Output: The final document will be saved as main.pdf in your project folder.
