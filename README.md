# Dynamic Factor Alpha  
**Regime-aware factor modeling and walk-forward machine learning for equity index forecasting**

---

## Overview

This repository implements an end-to-end quantitative research framework for forecasting and trading equity index returns using the latent structure of sector ETFs.

The project is built around three core ideas:

1. **Market structure is low-dimensional but regime-dependent**  
   Sector ETF correlations reveal a dominant market mode, secondary cluster factors, and macro regime switches.

2. **Predictive signals are weak, unstable, and geometry-driven**  
   Regularized linear models (Ridge, Lasso, ElasticNet) collapse to the same factor direction under strong common structure. Predictability emerges only in specific regimes.

3. **Evaluation must be strictly out-of-sample**  
   All models are trained using expanding-window walk-forward validation and evaluated on true out-of-sample forecasts.

The framework couples factor diagnostics, machine learning models, and portfolio simulation into a single reproducible research pipeline.

---

## Key Components

### 1. Data
- Target: **SPY daily log returns**
- Features: **Sector ETF returns** (XLK, XLF, XLE, XLI, XLY, XLP, XLU, XLV, etc.)
- All features are lagged and standardized inside each expanding window.

---

### 2. Feature Geometry & Regimes

- Static and rolling **correlation matrices**
- Rolling **sector–SPY correlations**
- Rolling **sector–sector correlations**
- Average pairwise correlation as a **market coupling index**
- Regime detection from correlation structure (e.g., XLE–XLU sign flips)

These diagnostics reveal:
- A dominant market mode
- Time-varying factor structure
- Macro regime transitions

---

### 3. Models

All models are trained using an **expanding-window walk-forward** procedure.

| Model | Purpose |
|------|--------|
| Ridge | Stable factor shrinkage |
| Lasso | Sparse factor selection |
| ElasticNet | Hybrid shrinkage & sparsity |

Alphas are searched on a logarithmic scale to capture the phase transition from intercept-only to full-factor solutions.

---

### 4. Signal → Portfolio Mapping

Predicted returns are mapped to portfolio positions using multiple sizing rules:

- **Binary**: sign-based long/short
- **Proportional**: scaled exposure
- **Quartile**: rank-based step exposure

Portfolio returns are constructed using correct self-financing return arithmetic.

---

### 5. Performance Metrics

#### Model-level (forecasting)
- RMSE
- MAE
- Out-of-sample \(R^2\)

#### Strategy-level (economic)
- Total & annualized return
- Volatility
- Sharpe ratio (log-return consistent)
- Max drawdown
- Calmar ratio
- Skewness & kurtosis

---

## Philosophy

This project is not about finding a single “best” model.  
It is about:

- understanding **why** signals appear and disappear  
- diagnosing **when** models break  
- and designing **regime-aware** systems that adapt to market structure.

---

## Folder Structure (example)

