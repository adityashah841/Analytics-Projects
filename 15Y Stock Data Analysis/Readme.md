# Big Tech 15-Year Stock Analysis (2010–2025)

This repository contains all code and outputs for a comprehensive analysis of five leading technology stocks—Apple (AAPL), Amazon (AMZN), Google (GOOGL), Microsoft (MSFT) and NVIDIA (NVDA)—over a 15-year period.  We cover:

1. **Data Preparation & EDA**  
2. **Trend & Volatility Analysis**  
3. **Principal Component Analysis**  
4. **Event Study (COVID-19 Crash)**  
5. **Forecasting** (ARIMA, Prophet, ETS, Ensembles)  
6. **Risk Assessment** (GARCH, VaR & ES)  
7. **Portfolio Simulations & Strategy Comparison**

---

## 📥 Data

Download the dataset from Kaggle and place the CSV in `data/`:

> **Kaggle link:**  
> [https://www.kaggle.com/​your-username/​big-tech-15yr-historical-data](https://www.kaggle.com/datasets/marianadeem755/stock-market-data)

---

## 🛠️ Requirements

- R version ≥ 4.0
- R packages:

```r
install.packages(c(
  "tidyverse", "tidyquant", "lubridate", "zoo", "tseries",
  "forecast", "prophet", "rugarch", "quadprog", "MASS"
))
```
- Shell tools: `git`, kaggle CLI (optional)

---

## 🚀 Quick Start

1. Clone this repo
  ```bash
  git clone https://github.com/your-username/big-tech-stock-analysis.git
  cd 15Y Stock Data Analysis
  ```
2. Install R dependencies (Code cell provided above)
3. Run the full pipeline (Recommended in RStudio)

This will
- Ingest and clean the data file
- Produce EDA plots
- Conduct PCA, event study, forecasting, risk modeling
- Generate simulation results & comparison charts

## 📑 Scripts Overview
The provided R-markdown script follows the following outline
- Data Ingestion & Preparation
  - Load raw CSV of daily OHLCV data (2010–2025)
  - Compute daily log-returns for each ticker
  - Reshape into “long” and “wide” formats for downstream tasks
- Exploratory Data Analysis (EDA)
  - Plot closing‐price time series on linear and indexed (100 = Jan 2010) scales
  - Compute and plot 30-day rolling volatility of log-returns
  - Overlay all five stocks’ daily log-returns on one chart
  - Show per-ticker return histograms to inspect tail behavior
- Correlation & Principal Component Analysis
  - Compute pairwise return correlations and display as heatmap
  - Run PCA on the daily return covariance matrix
  - Interpret PC1–PC3 loadings and variance explained
  - Biplots (PC1 vs PC2, PC1 vs PC3) to visualize factor structure
- Event Study: COVID-19 Crash (Feb–Mar 2020)
  - Estimate market-model alphas and betas over 1-year pre-event window
  - Compute abnormal returns and cumulative abnormal returns (CAR)
  - Plot CARs for all tickers through the event window
  - Conduct t-tests and confidence-band inference on CAR
- Univariate Forecasting & Model Comparison
  - ARIMA on daily log-returns (20-day forecast)
  - ETS and Prophet on price levels (60-day hold-out)
  - Compute accuracy metrics (MAPE, RMSE) for each model & ticker
  - Build inverse-MAPE weighted ensembles and evaluate improvement
- Risk Modeling with GARCH
  - Fit GARCH(1,1) models with Student-t residuals per ticker
  - Forecast one-day‐ahead volatility σₜ₊₁
  - Compute 95% VaR and Expected Shortfall (ES)
  - Summarize comparative risk measures across tickers
- Portfolio Construction & Monte-Carlo Simulation
  - Define four static allocation strategies:
    - Equal‐weight control
    - Inverse‐risk (1/σ₁)
    - Return‐based (15-yr cum-ret)
    - Markowitz MV (μ′w–½γ w′Σw), with/without box-constraints
  - Simulate 5 000 multivariate‐normal return paths for horizons: 1 m, 6 m, 1 y, 5 y, 10 y
  - For each strategy & horizon, compute:
    - Mean cumulative return
    - Return volatility (SD)
    - 5th & 95th percentiles
  - Identify top‐performing strategy per horizon
- Refinements & Sensitivity
  - Introduce weight caps (e.g. ≤ 30%) in MV optimizer to avoid NVDA concentration
  - Compare return-based weights from full 15 yr vs rolling 6-month momentum
  - Re-evaluate simulation outcomes under each refinement
- Conclusions & Recommendations
  - Key findings on growth, volatility, and diversification benefits
  - Model performance trade-offs (forecast accuracy vs ensemble gains)
  - Strategy guidance by investor horizon and risk appetite
  - Future extensions (conditional strategies, regime-switching, deeper GARCH)














