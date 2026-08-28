# Forecasting BMW Global Monthly Sales

**A Comparative Analysis of ETS and ARIMA Models**

- **Authors**: Chuanlin Qin, Yanjun Pan
- **Date**: April 2026

---

## Project Overview

This project analyzes BMW global monthly sales data (January 2018 – December 2025) to generate reliable 12-month forecasts using time series methods.

### Key Findings

- **Dataset**: 96 monthly observations of BMW global total units sold
- **Preferred Model**: `ETS(M,A,M)` — multiplicative errors, additive trend, multiplicative seasonality
- **12-Month Forecast**: Predicts ~3-5% year-over-year growth with peaks in March and December

---

## Project Structure

```
├── code/               # R analysis scripts
│   ├── ARIMA model.Rmd
│   ├── ETS model.Rmd
│   ├── data distription.Rmd
│   └── Project Report Final code.Rmd
├── data/               # Dataset
│   └── bmw_global_sales_2018_2025.csv
├── figures/            # Visualization outputs
├── report/             # Final report
└── README.md
```

---

## Methodology

### 1. Data Description

- **Source**: Kaggle – BMW Global Automotive Sales Data
- **Granularity**: Monthly aggregated total units sold
- **Period**: 2018 Jan – 2025 Dec (96 observations)
- **Characteristics**: Upward trend + strong multiplicative seasonality

### 2. ETS Model Selection

Compared 9 ETS specifications. Selected **ETS(M,A,M)** based on lowest AIC/AICc/BIC and in-sample error metrics.

| Model | AIC | AICc | BIC |
|---|---|---|---|
| **ETS(M,A,M)** | **2336.48** | **2344.33** | **2380.07** |
| Auto ETS | 2336.48 | 2344.33 | 2380.07 |
| ETS(M,A,A) | 2338.96 | 2346.81 | 2382.56 |

**Residual diagnostics**: Ljung-Box p-value = 0.3316 → residuals ≈ white noise ✅

### 3. ARIMA Model Selection

Explored differencing strategies (seasonal, first, and combined). Selected **ARIMA(1,1,1)(0,1,1)[12]** via AIC comparison.

| Model | AIC | AICc | BIC |
|---|---|---|---|
| **ARIMA(1,1,1)(0,1,1)[12]** | **1894.63** | **1895.15** | **1904.31** |
| ARIMA(0,1,1)(0,1,1)[12] | 1895.55 | 1895.86 | 1902.81 |

**Residual diagnostics**: Ljung-Box p-value = 0.7481 → residuals ≈ white noise ✅

### 4. Model Comparison (Time Series Cross-Validation)

| Model | RMSE | MAE | MAPE (%) |
|---|---|---|---|
| **ETS(M,A,M)** | **20,558** | **16,629** | **6.09** |
| ARIMA(1,1,1)(0,1,1)[12] | 20,817 | 16,609 | 6.12 |

**→ Recommended Model: ETS(M,A,M)**

---

## Forecast Results (2026)

The ETS(M,A,M) model forecasts continued growth with strong seasonal patterns:

- **Year-over-year growth**: ~3-5%
- **Peak months**: March & December (holiday / dealer incentives)
- **95% Prediction Interval**: ±45,000 units by late 2026

---

## Business Recommendations

1. **Inventory & Supply Chain**: Front-load production in Jan & Oct to handle March/December peaks
2. **Risk Management**: Use 80% lower bound for conservative budgeting; upper bound for capacity planning
3. **Promotion Scheduling**: Target low-sales months (Feb, Apr) with loyalty programs to smooth demand

---

## References

- **Data**: Kaggle – BMW Global Automotive Sales Data (2018-2025)
- **Textbook**: Hyndman, R. J., & Athanasopoulos, G. (2021). *Forecasting: Principles and Practice* (3rd ed.). OTexts.

---

## AI Usage Statement

AI was used for debugging assistance only. All statistical outputs, R code, and final report were conducted independently.
