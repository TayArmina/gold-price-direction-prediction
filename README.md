# Gold Price Direction Prediction

A time-series machine learning project for predicting the direction of the next Gold trading session using technical indicators, price-action features, and cross-market information.

## Overview

This project investigates whether next-session Gold direction can be predicted from historical Gold-market data together with information from related financial markets.

The analysis combines:

- Gold market features
- Technical indicators
- Price-action features
- Crude Oil WTI
- S&P 500
- Bitcoin
- USD/JPY
- US Dollar Index

Several classical machine-learning and deep-learning approaches were evaluated, including Logistic Regression, Random Forest, LSTM, CNN-LSTM, and an attention-based architecture. Model selection was based on chronological validation rather than model complexity.

## Methodology

The workflow includes:

- chronological train/validation/holdout separation
- leakage-aware time-series validation
- technical and price-action feature engineering
- cross-market feature construction
- feature ablation
- walk-forward validation
- L1 regularization
- feature-stability analysis
- threshold optimization
- historical holdout evaluation

The prediction target is the direction of the next available Gold trading session:

- `1` — Gold closes higher
- `0` — Gold closes at the same level or lower

## Final Model

The selected model is an **L1-regularized Logistic Regression** using 41 features.

| Metric | Historical Holdout |
|---|---:|
| Accuracy | 53.73% |
| Balanced Accuracy | 55.73% |
| Precision | 66.38% |
| Recall | 27.50% |
| F1 Score | 38.89% |
| ROC-AUC | 56.57% |
| Average Precision | 58.41% |

The model shows modest directional information rather than reliable standalone trading performance.

The final model configuration was selected using development data before evaluation on the 2022–2024 historical holdout. Because this period had been inspected during an earlier version of the project, it is reported transparently as a historical holdout rather than as a completely untouched test set.

## Data

Historical market data was downloaded from **Investing.com**.

The project uses data for:

- Gold Futures
- Crude Oil WTI
- S&P 500
- Bitcoin
- USD/JPY
- US Dollar Index

The raw datasets are not included in this repository. To reproduce the project, download the corresponding historical CSV files and place them inside a local `data/` directory using the filenames expected by the notebook.

## Repository Structure

```text
gold-price-direction-prediction/
├── Gold_Price_Direction_Prediction_GitHub.ipynb
└── README.md