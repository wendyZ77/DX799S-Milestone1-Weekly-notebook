# DX799S Milestone One — Weekly Notebooks

**Student:** Wendy Zhang  
**Course:** Module C: Data Science Capstone (DX799S)  
**Project:** Marketing Conversion Propensity and Campaign Performance

---

## Overview

This repository contains the six weekly Jupyter notebooks for Milestone One. Each notebook applies a different set of machine learning techniques to two marketing datasets:

- **Google Ads Sales** (`data/GoogleAds_DataAnalytics_Sales_Uncleaned.csv`) — 2,600 records, regression target `Conversions`
- **Digital Marketing Campaign** (`data/digital_marketing_campaign_dataset.csv`) — 8,000 records, binary classification target `Conversion`
- **Marketing & Product Performance** (`data/marketing_and_product_performance.csv`) — supplemental EDA only

---

## Repository Structure

```
├── data/
│   ├── GoogleAds_DataAnalytics_Sales_Uncleaned.csv
│   ├── digital_marketing_campaign_dataset.csv
│   └── marketing_and_product_performance.csv
├── figures/
│   ├── figure1.png   ← Week 1 model comparison (Test R²)
│   ├── figure2.png   ← Week 2 lasso regularization path (coefficients vs alpha)
│   ├── figure3.png   ← Week 3 method comparison (Test R²)
│   ├── figure4.png   ← Week 4 top odds ratios
│   ├── figure5.png   ← Week 5 ROC-AUC comparison
│   └── figure6.png   ← Week 6 decision tree depth vs ROC-AUC (overfitting curve)
├── ModC-week1-Zhang-Wendy.ipynb   ← Polynomial & interaction terms
├── ModC-week2-Zhang-Wendy.ipynb   ← Lasso, ridge, elastic net
├── ModC-week3-Zhang-Wendy.ipynb   ← Forward/backward selection, PCR, PLSR
├── ModC-week4-Zhang-Wendy.ipynb   ← Logistic regression & feature scaling
├── ModC-week5-Zhang-Wendy.ipynb   ← Support vector machines
├── ModC-week6-Zhang-Wendy.ipynb   ← Decision trees & random forests
├── requirements.txt
└── ENVIRONMENT.md
```

---

## Setup and Running

### 1. Clone the repository

```bash
git clone https://github.com/wendyZ77/DX799S-Milestone1-Weekly-notebook.git
cd DX799S-Milestone1-Weekly-notebook
```

### 2. Create a virtual environment and install dependencies

```bash
python -m venv .venv
source .venv/bin/activate        # macOS / Linux
# .venv\Scripts\activate         # Windows

pip install -r requirements.txt
```

### 3. Run a weekly notebook

Open any notebook in Jupyter:

```bash
jupyter notebook ModC-week1-Zhang-Wendy.ipynb
```

Each notebook is self-contained and generates its figure into the `figures/` directory when run.

---

## Weekly Notebooks Summary

| Week | Topic | Dataset | Key result |
|------|-------|---------|-----------|
| 1 | Polynomial & interaction terms | Google Ads (regression) | Test R² ≈ −0.006 after removing leakage fields |
| 2 | Lasso, ridge, elastic net | Google Ads (regression) | All methods R² < 0; lasso zeros all coefficients |
| 3 | Forward/backward selection, PCR, PLSR | Google Ads (regression) | All methods RMSE ≈ 2.29, identical to baseline |
| 4 | Logistic regression & feature scaling | Digital Marketing (classification) | ROC-AUC = 0.770 after StandardScaler + tuning |
| 5 | Support vector machines | Digital Marketing (classification) | Tuned RBF SVM ROC-AUC = 0.785 |
| 6 | Decision trees & random forests | Digital Marketing (classification) | Tuned RF ROC-AUC = 0.798 |

---

## Data Integrity Note

Two fields were excluded from the Google Ads regression task before any modeling:
- `Conversion Rate` — mathematically derived from the target (Conversions ÷ Clicks)
- `Sale_Amount` — a post-conversion outcome

`CustomerID` was excluded from all classification models. These exclusions are applied in `build_feature_matrix()` inside each notebook.
