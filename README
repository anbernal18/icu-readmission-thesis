# ICU 30-Day Readmission Risk Stratification

**MSc Data Science Thesis — University of Europe for Applied Sciences**  
Ana Cecilia Bernal García · Student ID: 33527353  
Supervisor: Raja Hashim Ali

---

## Overview

This repository contains the full implementation of a comparative study evaluating machine learning and deep learning models for predicting 30-day hospital readmission risk at ICU discharge.

The study addresses a clinically relevant problem: identifying high-risk patients before discharge so that targeted interventions can be applied. Rather than proposing a single model, this work systematically compares 15 model configurations across five feature groups to understand *what kind of information* actually drives predictive performance in ICU settings.

**Central finding:** Static administrative features (prior admissions, capped length of stay) dominate over temporal vital sign sequences. XGBoost with static + temporal-summary features outperforms all other configurations, including deep learning models.

---

## Dataset

**MIMIC-IV v3.1** — a large publicly available ICU database from Beth Israel Deaconess Medical Center.  
Access is restricted and requires credentialing via [PhysioNet](https://physionet.org/content/mimiciv/). Data is **not included** in this repository.

Cohort: Adult ICU patients discharged alive, with a minimum stay of 12 hours.  
Outcome: Binary — readmission within 30 days of hospital discharge.

Temporal split (using MIMIC-IV anonymized years):
- **Training:** 2119–2155  
- **Validation:** 2156–2161  
- **Test:** 2162–2168

---

## Models Compared 

| Category | Model |
|---|---|
| Classical ML | Logistic Regression, XGBoost |
| Recurrent Neural Networks | LSTM, GRU |
| Missingness-Aware RNN | GRU-D |
| Attention-Based | Transformer |

Each model was evaluated across five feature groups (G1–G5), ranging from static-only to full temporal sequences.

---

## Evaluation Framework

The study evaluates seven research questions covering:

- **RQ1** — Discrimination (AUROC, AUPRC)
- **RQ2** — Calibration and reliability (ECE, Brier Score, DCA)
- **RQ3** — Temporal robustness (year-wise AUROC)
- **RQ4** — Handling of irregular and missing time-series data
- **RQ5** — Risk stratification efficiency (Precision@K, Recall@K)
- **RQ6** — Estimated clinical utility under intervention capacity constraints
- **RQ7** — Interpretability via SHAP

---

## Repository Structure

```
├── data/
│   └── cohort_extraction.sql       # BigQuery extraction queries
├── preprocessing/
│   ├── feature_engineering.py      # Static + temporal feature construction
│   └── temporal_split.py           # Train/val/test split logic
├── models/
│   ├── logistic_regression.py
│   ├── xgboost_model.py
│   ├── lstm.py
│   ├── gru.py
│   ├── gru_d.py
│   └── transformer.py
├── evaluation/
│   ├── discrimination.py           # AUROC, AUPRC, F1
│   ├── calibration.py              # ECE, Brier, reliability diagrams
│   ├── temporal_robustness.py      # Year-wise evaluation
│   ├── risk_stratification.py      # Precision@K, risk tiers
│   └── clinical_utility.py        # DCA, intervention simulations
├── notebooks/
│   └── results_analysis.ipynb      # Full results and figures
├── figures/                        # Output figures (PDF)
└── README.md
```

---

## Key Results

| Model | Feature Group | AUROC | AUPRC |
|---|---|---|---|
| XGBoost | G2 (Static + Temporal Summary) | **0.6617** | — |
| Logistic Regression | G1 (Static only) | — | — |
| GRU | G4 (Full temporal) | — | — |
| Transformer | G4 (Full temporal) | — | — |

> Full results are reported in the thesis and the accompanying journal manuscript (submitted to *Health Policy and Technology*).

---

## Requirements

```
Python 3.9+
pandas
numpy
scikit-learn
xgboost
torch
shap
matplotlib
google-cloud-bigquery
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## Usage

1. Set up MIMIC-IV access via Google BigQuery
2. Run cohort extraction: `data/cohort_extraction.sql`
3. Build features: `preprocessing/feature_engineering.py`
4. Train models: scripts in `models/`
5. Evaluate: scripts in `evaluation/`
6. View results: `notebooks/results_analysis.ipynb`

---

## Citation

If you use any part of this work, please cite:

```
Bernal García, A. C. (2026). Evaluating Machine-Learning-Based Risk Stratification
for 30-Day ICU Readmission. MSc Thesis, University of Europe for Applied Sciences.
```

---

## License

This repository is shared for academic transparency. The code is available under the MIT License. MIMIC-IV data is not included and requires independent credentialing via PhysioNet.

---

## Acknowledgements

Supervised by Raja Hashim Ali. Data accessed via Google BigQuery under the MIMIC-IV PhysioNet Data Use Agreement.
