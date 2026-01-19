# Comparative Data Mining Study: Social Media Engagement
**Author:** Inviona Hoxha  
**Course:** Introduction to Data Mining  
**Academic Framework:** KDD Process (Fayyad et al., 1996)

## 📋 Project Overview
This project implements a high-fidelity data mining pipeline designed to analyze and predict social media engagement metrics. Utilizing the **Knowledge Discovery in Databases (KDD)** methodology, the study transitions from raw data acquisition to actionable predictive modeling, comparing frequentist baselines with non-linear ensemble methods.



## 🛠 Technical Architecture
The implementation is strictly modularized according to the five phases of the KDD framework:

### 1. Data Selection
* **Target Isolation:** The pipeline is configured to isolate `engagement_rate` as the primary dependent variable.
* **Automated Detection:** Integrated logic to identify target variables based on priority lists and numerical characteristics.

### 2. Data Preprocessing
* **Missing Value Imputation:** Implementation of a dual-strategy approach using median imputation for numerical features and mode imputation for categorical data.
* **Outlier Analysis:** Robust detection utilizing the Interquartile Range (IQR) method ($Q1 - 1.5 \times IQR$ to $Q3 + 1.5 \times IQR$).

### 3. Data Transformation
* **Leakage Mitigation:** A proactive detection engine that identifies features with a correlation coefficient $|\rho| > 0.95$ relative to the target, preventing data leakage.
* **Feature Engineering:** * Automated skewness analysis ($|S| > 1.0$).
    * Application of $log(1+x)$ transformations to normalize feature distributions.
    * $Z$-score standardization to ensure feature scale parity.

### 4. Data Mining (Comparative Modeling)
The study evaluates two distinct algorithmic paradigms:
* **Baseline:** Ordinary Least Squares (OLS) Linear Regression to establish a frequentist performance floor.
* **Advanced:** Random Forest Regressor utilizing an ensemble of 100 decision trees with optimized depth and sample split parameters.



### 5. Evaluation and Interpretation
Models are evaluated through a multi-dimensional lens:
* **Predictive Accuracy:** $R^2$, $RMSE$, and $MAE$.
* **Computational Efficiency:** Real-time profiling of training latency and peak memory consumption (MB).
* **Residual Analysis:** Diagnostic plotting to verify the assumptions of homoscedasticity.

## 📊 Analytical Visualizations
The pipeline generates a specialized visualization suite within the `/visualizations` directory:
* **Radar Charts:** Normalized comparison of Accuracy vs. Efficiency vs. Robustness.
* **Residual Distributions:** Error frequency analysis to detect prediction bias.
* **Prediction Heatmaps:** 2D density plots showing the convergence of predicted vs. actual values.

## 🚀 Execution Instructions
1. **Environment:** Ensure Python 3.8+ is installed.
2. **Dependencies:** `pip install pandas numpy scikit-learn matplotlib seaborn psutil`
3. **Data:** Place `social-media-dataset.csv` in the root directory.
4. **Run:** `python kdd_pipeline.py`

## 📂 Repository Structure
```text
├── kdd_pipeline.py              # Main KDD implementation
├── social-media-dataset.csv     # Input dataset
├── Report_Inviona_Hoxha.pdf     # Technical project report
├── visualizations/              # Exported analytical graphs
└── model_comparison_results.csv # Empirical results log