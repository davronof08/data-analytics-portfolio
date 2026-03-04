# Demand Forecasting Model Evaluation
**Academic Case Study Analysis | Baruch College | Fall 2023**

Team project analyzing seasonal demand to identify the most
accurate forecasting method for inventory planning.

---

## 📊 Interactive Dashboard
**Download:** [Power BI Dashboard (.pbix)](Demand_Forecasting_Model_Evaluation.pbix)  
**View:** [PDF Export](Demand_Forecasting_Model_Evaluation.pdf)

---

## Project Overview
Compared **10 forecasting methods** using **108 monthly observations (2003–2012)**
to find the best approach for reducing forecast error in a seasonal supply chain.

**Best method:** Holt-Winters' Additive  
**Key metrics:** MAPE = 10.68% | MAD = 1,263.4 | MSE = 2,912,807.8 | RMSE = 1,715.7

---

## Business Context
- **Problem:** ABC Industrial, an equipment manufacturer with 4 plants and 6 regional stockyards serving hundreds of dealers nationwide, struggled to plan inventory under ±40% seasonal demand swings.  
- **Impact:** Seasonal demand peaks disrupted supply and caused frequent stockouts in some regions and excess inventory in others, triggering emergency stockyard-to-stockyard transfers at **$145/unit** for **6.7% of annual volume** (~14,800 units/year), or **~$2.1M/year** in logistics cost.  
- **Root Cause:** Legacy forecasting methods did not capture both seasonality and the underlying demand trend, limiting the ability to plan regional inventory effectively.  
- **Goal:** Identify the most suitable forecasting method for ABC to reduce emergency transfer costs and improve inventory planning.  
- **Solution:** ABC Industrial should implement a Holt-Winters Additive model to improve its forecast accuracy and better support regional inventory allocation, helping to reduce emergency transfer costs.

---

## My Contribution
As part of a 4-person analytics team, I focused on the quantitative forecasting work:
- **Data preparation:** Structured 108 months of historical demand data for analysis
- **Model building:** Built and optimized advanced forecasting methods in Excel using Solver
- **Error evaluation:** Calculated MAD, MSE, and MAPE
- **Dashboard:** Built an interactive Power BI dashboard with DAX-driven method switching
- **Business translation:** Summarized results and implications for inventory planning

---

## Methods Evaluated (10)

**Simple Methods (5)**
1. Naïve Forecast
2. Moving Average (3-month)
3. Moving Average (4-month)
4. Weighted Moving Average (3-month) — optimized weights
5. Weighted Moving Average (4-month) — optimized weights

**Advanced Methods (5) — Solver-optimized**

6. Linear Regression (R² = 0.65)
7. Exponential Smoothing (α = 0.207)
8. Time Series Decomposition (trend × seasonal)
9. Holt-Winters' Multiplicative (α ≈ 0.336, β ≈ 0.002, γ = 1.0)
10. **Holt-Winters' Additive ⭐** (α = 0.389, β = 0.006, γ = 1.0)

---

## Key Results

### Top 5 Performance Ranking
| Rank | Method                      | MAD     | MSE           | MAPE   |
|------|-----------------------------|--------:|--------------:|-------:|
| 🥇   | **Holt-Winters' Additive**  | 1,263.4 | 2,912,807.8   | 10.68% |
| 🥈   | Holt-Winters' Multiplicative| 1,300.9 | 3,028,049.9   | 11.15% |
| 🥉   | Time Series                 | 1,336.1 | 3,057,668.0   | 11.86% |
| 4    | Exponential Smoothing       | 1,971.9 | 7,786,874.4   | 16.59% |
| 5    | Weighted MA (4-month)       | 2,026.4 | 7,345,878.1   | 17.40% |

### Why Holt-Winters' Additive Won
- Captures both **trend** and **seasonality** simultaneously
- An additive model fits well when seasonal variation is consistent in size
- Achieved the lowest MAPE across all 10 methods tested

---

## Skills Demonstrated
- **Forecasting:** Holt-Winters (additive/multiplicative), Exponential smoothing,
  Time-Series decomposition and Linear regression
- **Excel (Advanced):** Solver optimization, Data Analysis ToolPak
- **Power BI:** DAX measures, data modeling, interactive dashboard design

---

## Repository Structure

```
01-forecasting-analysis/
├── README.md                                      # This file
├── methodology.md                                 # Detailed formulas
├── Case_Study_Demand_Forecasting.xlsx             # Excel calculations and charts
├── Demand_Forecasting_Model_Evaluation.pbix       # Power BI interactive dashboard
└── Demand_Forecasting_Model_Evaluation.pdf        # Dashboard export
```
---

## Contact
Questions about this analysis? Connect with me on 💼[LinkedIn](https://linkedin.com/in/davronoff) or 📧 [Email](mailto:davronof08@gmail.com)

---

*Skills: Statistical Forecasting • Time Series Analysis • Power BI • DAX • Excel Solver • Holt-Winter's Method • Supply Chain Analytics*
