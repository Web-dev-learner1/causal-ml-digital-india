# Digital India Inclusion Impact Assessment Using Causal ML

## 📌 Project Overview
This repository contains the code and diagnostic methodology for assessing the causal impact of Digital India's telecom infrastructure expansion on three key socioeconomic outcomes across Indian states: Digital Literacy, Employment, and GDP per Capita. 

Unlike standard predictive modeling, this project utilizes a **Causal Machine Learning** framework to isolate treatment effects from heavily confounded observational macroeconomic data, moving beyond correlation to estimate true causal impact.



## 🔬 Methodology & Causal Ensemble
To ensure robust estimates, this project implements a multi-method causal ensemble using the `EconML` and `DoWhy` ecosystems. Key approaches include:
* **Causal Forests (EconML):** Production-grade heterogeneous treatment effect estimation utilizing 2,000 trees.
* **Propensity Score Matching (PSM):** Implemented nearest neighbor and caliper matching, validating post-matching covariate balance using Standardized Mean Differences (SMD < 0.1).
* **Doubly Robust Estimation:** Combining outcome regression with propensity weighting.
* **Cross-Fitted T-Learners:** Utilizing 5-fold stratified cross-validation with bootstrap confidence intervals to mitigate overfitting bias.
* **Rosenbaum Sensitivity Analysis:** Testing robustness to unobserved confounders at bounds $\Gamma = 1, 1.5, 2, 2.5, 3$.

## 📊 Key Findings & Scientific Limitations
Real-world macroeconomic datasets are notoriously noisy. A major focus of this project was triangulating results across methods and rigorously quantifying data limitations.

* **GDP Per Capita:** The Causal Forest estimated a massive Mean CATE of ~127.41. However, alternative estimates showed a wide range (0 to 200), and the CATE distribution lacked variation, indicating substantial model instability.
* **Digital Literacy:** Estimated a ~0.23 percentage point increase, though T-Learner alternative estimates suggested potential negative bounds, highlighting high model sensitivity.
* **Employment:** Exhibited a minimal positive effect (~0.04) concentrated near zero.

**Critical Conclusion:** While the diagnostic checks (Propensity AUC, overlap density) showed adequate common support, the substantive findings remain inconclusive. The extreme model sensitivity highlights the strict limitations of utilizing small sample sizes ($N=17$ states) for heterogeneous effect estimation. This demonstrates the absolute necessity of rigorous Causal ML validation over naive correlational Machine Learning when analyzing flawed observational data.

## 📂 Repository Contents
* `Synaptica_Code.ipynb`: The main Jupyter Notebook containing the end-to-end data processing, the 7-method causal ensemble, diagnostic plotting, and sensitivity bounds. All graphs (overlap density plots, CATE distributions, etc.) are rendered within the notebook.

## 🛠️ Tech Stack
* **Causal Inference:** `EconML`, `DoWhy`
* **Machine Learning:** `XGBoost`, `Scikit-Learn`
* **Data Processing & Visualization:** `Pandas`, `NumPy`, `Matplotlib`, `Seaborn`

## 🚀 How to View
To view the code, methodologies, and visual diagnostics, simply click on the `Synaptica_Code.ipynb` file above. GitHub will render the notebook natively in your browser.

---
*Author: Shreelakshmi Somayaji* | *Guide: Dr. Bhaskarjyoti Das*
