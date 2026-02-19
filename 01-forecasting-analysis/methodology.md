# Forecasting Methodology - Technical Reference

Quick reference guide for the statistical methods and formulas used in this forecasting analysis.

---

## Dataset
- **Period:** 2003-2012 (108 monthly observations)
- **Seasonality:** Dual peaks (Apr-Jun, Sep-Nov)
- **Trend:** Linear growth ~120 units/month
- **Variation:** 40% seasonal swing

---

## Methods & Formulas

### 1. Naïve Method
```
F(t+1) = A(t)
```
Forecast = Last period's actual demand

---

### 2. Moving Average (n periods)
```
F(t+1) = [A(t) + A(t-1) + ... + A(t-n+1)] / n
```
**Tested:** n = 3, 4 months

---

### 3. Weighted Moving Average
```
F(t+1) = w₁·A(t) + w₂·A(t-1) + w₃·A(t-2) + ...
```
**Best 3-month weights:** 0.55, 0, 0.45  
**Best 4-month weights:** 0.42, 0, 0.2, 0.38

---

### 4. Linear Regression
```
F(t) = a + b·t
```
**Results:**
- Intercept (a): 4,772.65
- Slope (b): 119.79
- R²: 0.6475

---

### 5. Exponential Smoothing
```
F(t+1) = α·A(t) + (1-α)·F(t)
```
**Optimal α:** 0.2072

---

### 6. Time Series Decomposition
```
Demand = Trend × Seasonal × Irregular
F(t) = Trend(t) × Seasonal_Index(t)
```
**Trend:** Y = 4,668.43 + 119.44·X  
**R²:** 0.8298 (improved from 0.6475)

---

### 7. Holt-Winter's Multiplicative
```
Level:       L(t) = α·[A(t)/S(t-12)] + (1-α)·[L(t-1) + T(t-1)]
Trend:       T(t) = β·[L(t) - L(t-1)] + (1-β)·T(t-1)
Seasonality: S(t) = γ·[A(t)/L(t)] + (1-γ)·S(t-12)
Forecast:    F(t+h) = [L(t) + h·T(t)] × S(t+h-12)
```
**Parameters:** α=0.3357, β=0.0017, γ=1.0  
**RMSE:** 1,749.26

---

### 8. Holt-Winter's Additive ⭐ **WINNER**
```
Level:       L(t) = α·[A(t) - S(t-12)] + (1-α)·[L(t-1) + T(t-1)]
Trend:       T(t) = β·[L(t) - L(t-1)] + (1-β)·T(t-1)
Seasonality: S(t) = γ·[A(t) - L(t)] + (1-γ)·S(t-12)
Forecast:    F(t+h) = L(t) + h·T(t) + S(t+h-12)
```
**Parameters:** α=0.3889, β=0.0062, γ=1.0  
**RMSE:** 1,715.65

**Why Additive Won:** Seasonal variation is constant in absolute terms (~2,000-3,000 units), not proportional to demand level.

---

## Error Metrics

### Mean Absolute Deviation (MAD)
```
MAD = Σ|A(t) - F(t)| / n
```

### Mean Squared Error (MSE)
```
MSE = Σ[A(t) - F(t)]² / n
```

### Mean Absolute Percentage Error (MAPE)
```
MAPE = [Σ|A(t) - F(t)| / A(t)] / n × 100%
```

---

## Results Summary

| Method | MAD | MSE | MAPE |
|--------|-----|-----|------|
| **Holt-Winter's Additive** | **1,263** | **2,912,808** | **10.68%** |
| Holt-Winter's Multiplicative | 1,301 | 3,028,050 | 11.15% |
| Time Series Decomposition | 1,336 | 3,057,668 | 11.86% |
| Exponential Smoothing | 1,972 | 7,786,874 | 16.59% |
| Linear Regression | 1,993 | 7,590,642 | 17.94% |
| Weighted MA (4-month) | 2,026 | 7,345,878 | 17.40% |
| Moving Average (4-month) | 1,800 | 8,414,118 | 19.03% |
| Naïve | 2,419 | 10,663,081 | 21.44% |

---

## Parameter Optimization

**Tool:** Excel Solver (GRG Nonlinear)  
**Objective:** Minimize MAPE  
**Constraints:** 0 ≤ α, β, γ ≤ 1

**Validation:**
- Training: 2003-2011 (96 obs)
- Test: 2012 (12 obs)

---

## Implementation

**Excel Functions Used:**
- `AVERAGE()`, `STDEV()` - Descriptive stats
- `LINEST()` - Regression parameters
- Solver - Parameter optimization
- Custom formulas - Holt-Winter's calculations

**Computation:** <5 seconds for 108 observations

---

## Key Findings

1. **50% error reduction** vs simple methods (21.4% → 10.68% MAPE)
2. **Seasonal methods essential** for demand with dual peaks
3. **Additive > Multiplicative** when seasonal variation is constant
4. **Trend + Seasonality** both critical (R² jumped from 0.65 to 0.83)

---

*Tools: Excel 2019, Analysis ToolPak, Solver*  
*Contact: davronof08@gmail.com*
