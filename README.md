# 📈 Time Series Forecasting for FinTech Data

Applying the **Box–Jenkins methodology** to two contrasting financial time series: daily Bitcoin prices (nonseasonal) and monthly U.S. credit-card debt (seasonal), using ARIMA and SARIMA models for short-term forecasting.

---

## 📌 Overview

This project was completed as part of **MA 641 – Time Series Analysis I** at Stevens Institute of Technology (Fall 2025).

Two FinTech datasets are analyzed:
- **Bitcoin (BTC/USD)** — daily closing prices from CoinGecko (April 2013 – November 2025), exhibiting high volatility and no seasonal pattern
- **U.S. Revolving Consumer Credit (REVOLSL)** — monthly credit-card balances from the Federal Reserve (FRED), featuring a strong upward trend and a repeating 12-month seasonal cycle

---

## 🗂️ Project Structure

```
time-series-fintech/
│
├── data/
│   ├── bitcoin.csv            # Daily Bitcoin prices from CoinGecko
│   └── REVOLSL.csv            # Monthly U.S. credit-card debt from FRED
│
├── MA641_Project_NehaNagaraj.Rmd   # Full R Markdown analysis
├── MA641_Project_NehaNagaraj.pdf   # Rendered project report
└── README.md
```

---

## 🔍 Methodology

The Box–Jenkins procedure was followed for both datasets:

1. **Identification** — Visual inspection and Augmented Dickey–Fuller (ADF) tests to determine the degree of differencing required for stationarity
2. **Estimation** — Multiple candidate models fitted: AR(1), MA(1), ARMA(1,1), ARIMA, and SARIMA variants
3. **Model Selection** — Best model chosen using AIC and BIC
4. **Diagnostic Checking** — Residual ACF/PACF plots and Ljung–Box test to verify white noise residuals
5. **Forecasting** — Short-term forecasts generated with 95% confidence intervals

---

## 📊 Results

### Bitcoin — ARIMA(0, 1, 1) with Drift

| Step | Finding |
|------|---------|
| Stationarity | ADF on raw series: p = 0.85 (non-stationary). After first differencing: p < 0.05 ✅ |
| Best Model | ARIMA(0, 1, 1) with drift |
| AIC | ≈ 76,432 (lowest among all candidates) |
| Diagnostics | Ljung–Box p = 0.044 — residuals approximate white noise |
| Forecast | 30-day projection shows modest upward trend with widening confidence intervals |

### U.S. Credit-Card Debt — SARIMA(1, 1, 1)(1, 1, 1)[12]

| Step | Finding |
|------|---------|
| Stationarity | Required both regular and seasonal differencing to achieve stationarity |
| Best Model | SARIMA(1, 1, 1)(1, 1, 1)[12] |
| AIC / BIC | 13,523.7 / 13,546.3 (lowest among all candidates) |
| Diagnostics | Ljung–Box p > 0.05 — no remaining autocorrelation |
| Forecast | 12-month projection shows continued gradual growth with recurring year-end seasonal peaks |

---

## 🛠️ Tech Stack

- **Language:** R
- **Libraries:** `forecast`, `tseries`, `ggplot2`, `readr`, `dplyr`

---

## 📁 Data Sources

- [Bitcoin Historical Data — CoinGecko](https://www.coingecko.com/en/coins/bitcoin/historical_data)
- [Revolving Consumer Credit (REVOLSL) — FRED](https://fred.stlouisfed.org/series/REVOLSL)

---

## 👩‍💻 Author

**Neha Nagaraj**  
M.S. Data Science, Stevens Institute of Technology  
[LinkedIn](https://www.linkedin.com/in/neha-nagaraj-23j2002/) · neha23nagaraj@gmail.com
