Balena Quant Invitational: Hack996

Hybrid Alpha Trading Strategy Framework

A modular and intelligent trading strategy framework combining LSTM, XGBoost, and Hidden Markov Models (HMM) for regime-aware signal generation, with support for PCA-based feature selection and future sentiment integration.

---

Presentation Slide Link:
https://docs.google.com/presentation/d/1wxjvfb1Svup0Y6Iu2SWQbWtlgFqIu0sOeK2lxt5uOzY/edit?usp=sharing

---

Objectives

- Predict price movement with high Sharpe Ratio (≥ 1.8)
- Maintain Max Drawdown above -40%
- Ensure active trading with ≥ 3% signal frequency per step
- Adapt dynamically to market regimes and feature importance
- Package into a reusable, production-ready pipeline

---

Model Components

LSTM (Long Short-Term Memory)
- Captures temporal price dynamics
- Used to forecast future returns
- Evaluated with multiple rolling windows

XGBoost
- Trained using LSTM's predicted returns and regime data
- Outputs final trade signal: Buy (1), Hold (0), Sell (-1)

Hidden Markov Model (HMM)
- Detects market regimes based on historical behavior
- Regime used as input feature for model decision-making

PCA (Principal Component Analysis)
- Reduces dimensionality and noise
- Highlights top contributing features

---

Workflow Summary

1. Raw financial data input (price, volume, indicators, etc.)
2. Feature ranking using PCA
3. Market regime detection using HMM → hmm_state
4. Rolling window strategy to find optimal time frame
5. Feature selection using XGBoost
6. Train LSTM model with selected features and optimal window
7. XGBoost train on LSTM output and regime to produce trading signal.


---

Results (Dataset Tested)

| Dataset | Sharpe Ratio | Max Drawdown  | Trade Frequency  |
|---------|--------------|---------------|------------------|
| A       | 3.86         | -5.16%        | 32.79%           |
| B       | 1.73         | -6.09%        | 8.42%            |
| C       | 2.08         | -2.92%        | 9.30%            |

=> Framework met or nearly met all success criteria across test scenarios.


