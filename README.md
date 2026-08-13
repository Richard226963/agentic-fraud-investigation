# Agentic Fraud Investigation

[![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![pandas](https://img.shields.io/badge/pandas-2.x-150458?style=flat-square&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![NumPy](https://img.shields.io/badge/NumPy-1.x-013243?style=flat-square&logo=numpy&logoColor=white)](https://numpy.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.x-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![XGBoost](https://img.shields.io/badge/XGBoost-2.x-0091BD?style=flat-square)](https://xgboost.ai/)
[![FAISS](https://img.shields.io/badge/FAISS-RAG-5B3B8C?style=flat-square)](https://faiss.ai/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=flat-square&logo=jupyter&logoColor=white)](https://jupyter.org/)

A four-layer fraud investigation pipeline — **detection → investigation → decision → reporting** —
that turns messy telecom operations data into defensible case files: every flagged customer
backed by SOP-cited evidence and a recommended action.

## Pipeline

1. **Detection** — leak-safe feature engineering and a time-based train/test split;
   supervised (XGBoost) vs unsupervised (Isolation Forest) anomaly detection, plus an
   ensemble combining both
2. **Investigation** — rule-based detectors for known fraud patterns (SIM-swap takeover,
   reseller rings, promo-bundle abuse)
3. **Decision** — customer-level rollup fusing transaction signals and rule hits into
   prioritized cases
4. **Reporting** — RAG-based case files citing the relevant SOP documents, with citation
   accuracy tracked

## Results

The dataset is real (1,200 customers · 7,634 transactions · 200 SIM swaps · 280 complaint
notes · 4 SOPs) and every number below comes from actually running the pipeline.

| Component | Key result |
|---|---|
| XGBoost (leak-safe time split) | fraud precision / recall / F1 **1.00 / 1.00 / 1.00** |
| Isolation Forest (unsupervised) | fraud recall 0.38 — the supervised model's lift is genuine |
| Ensemble (XGBoost ∪ Isolation Forest) | fraud recall **1.00**, precision 0.78, F1 0.87 |
| SOP rule detectors | **59 / 59** ground-truth fraud customers captured |
| Combined system | all 59 ground-truth fraud customers flagged |

## Getting started

Open the notebook in [Google Colab](https://colab.research.google.com/) and run it top to
bottom — the dataset downloads automatically from Google Drive on first run.

```bash
# or locally
jupyter notebook Agentic_Fraud_Investigation.ipynb
```

**Requirements:** `pandas`, `numpy`, `scikit-learn`, `xgboost`, `faiss-cpu`, `gdown`

## Repository structure

```
agentic-fraud-investigation/
├── Agentic_Fraud_Investigation.ipynb   # end-to-end pipeline (59 cells)
└── README.md
```
