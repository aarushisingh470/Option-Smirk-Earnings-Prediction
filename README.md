# Option-Smirk-Earnings-Prediction

This repository contains the capstone research project for the **NYU Courant Mathematics in Finance program**.

The project studies whether **option-implied volatility smirk signals can predict equity returns**, particularly across different market regimes and around earnings announcements.

The central idea is that the **shape of the implied volatility curve reflects investor demand for downside protection**, which may contain information about future stock movements that is not fully incorporated into equity prices.

---

# Authors

Aarushi Singh  
Pranam Hegde  
Sunny Dhindsa  

Advisor: Sahin Rahman  
New York University Courant Institute of Mathematical Sciences  
December 2025

---

# Research Questions

This project investigates three main questions:

1. Do **option-implied volatility smirk measures predict stock returns**?
2. Does the predictive power of smirk signals change across **market regimes (crisis vs modern markets)**?
3. Can option-implied signals help predict **earnings announcement reactions**?

The goal is to determine whether **information embedded in options markets leads equity price movements.**

---

# Key Variables

## Volatility Smirk

The **volatility smirk** measures the difference between implied volatility of out-of-the-money puts and calls.

```
smirk_iv = IV_put − IV_call
```

A larger smirk indicates stronger demand for **downside protection**.

## Price Smirk

An alternative smirk measure using option prices.

```
smirk_price = mid_put − mid_call
```

Both metrics capture the market's willingness to pay for downside insurance.

---

# Data

The analysis uses three primary datasets.

### Equity Options Dataset

A cross-sectional equity options dataset containing approximately **230,000 observations**.

Fields include:

- Date
- Expiration
- Strike
- Call/Put indicator
- Bid / Ask prices
- Volume
- Open Interest
- Implied Volatility
- Underlying Price

Derived features include:

- IV smirk
- price smirk
- log moneyness
- days to expiration
- liquidity measures

---

### Crisis Period Datasets

Two crisis periods are analyzed to study smirk behavior during market stress.

- **2008 Financial Crisis**
- **2020 COVID Market Shock**

Datasets:

```
spx2008.csv
spx2020.csv
```

These datasets allow comparison of volatility skew dynamics during extreme market conditions.

---

### Earnings Event Dataset

A set of **20 equities with identifiable earnings reactions** is used to test whether smirk signals anticipate earnings surprises.

For each stock:

- 3–5 day pre-earnings option window
- smirk feature construction
- next-day return classification

Example firms included:

- MSFT
- JPM
- XOM

---

# Methodology

The modeling pipeline follows several steps.

1. Clean option chain data
2. Construct mid prices
3. Compute implied volatility smirk metrics
4. Engineer predictive features
5. Evaluate predictive power across three regimes

The regimes analyzed include:

- **2008 crisis period**
- **2020 crisis period**
- **modern cross-sectional options data**
- **earnings announcement events**

Regression analysis, decile portfolio sorting, and classification models are used to evaluate predictive performance.

---

# Strategy Performance

To evaluate economic significance, we construct a simple signal-based trading framework using smirk measures.

Strategy structure:

- **Long:** stocks with high smirk values  
- **Short:** stocks with low smirk values  

Performance summary:

| Metric | Value |
|------|------|
| Average monthly return | ~0.9% |
| Annualized Sharpe Ratio | ~0.75 |

Sharpe ratio calculation:

```
Sharpe = √12 × (mean monthly return / standard deviation of monthly returns)
```

The results suggest that option-implied volatility asymmetry contains **economically meaningful information about future stock returns**, especially during crisis periods and around earnings announcements.

---

# Key Findings

### Crisis Regimes

During **2008 and 2020**, smirk measures spike sharply as investors demand downside protection. Predictive signals are strongest during these stress periods.

### Modern Cross-Section

Smirk signals still show **positive relationships with short-horizon returns**, but the signal is weaker due to increased market efficiency.

### Earnings Events

Pre-earnings smirk patterns align with **post-announcement return direction**, suggesting informed positioning in the options market before earnings releases.

Overall, smirk predictability appears to be **regime-dependent**.

---

# Repository Structure

```
option-smirk-equity-return-prediction
│
├── notebooks
│   Research.ipynb
│   RecentDataResearch.ipynb
│   RecentEarningsTest.ipynb
│
├── data
│   spx2008.csv
│   spx2020.csv
│
├── results
│   res_spx_2008.csv
│   res_spx_2008_pct.csv
│   res_spx_2020.csv
│   res_spx_2020_pct.csv
│
│   res_msft_2008.csv
│   res_msft_2008_pct.csv
│   res_msft_2020.csv
│   res_msft_2020_pct.csv
│
│   res_jpm_2008.csv
│   res_jpm_2008_pct.csv
│   res_jpm_2020.csv
│   res_jpm_2020_pct.csv
│
│   res_xom_2008.csv
│   res_xom_2008_pct.csv
│   res_xom_2020.csv
│   res_xom_2020_pct.csv
│
├── papers
│   What Does the Individual Option Volatility Smirk Tell Us About Future Equity Returns.pdf
│   Option Characteristics as Cross-Sectional Predictors.pdf
│   Why Do Option Prices Predict Stock Returns.pdf
│
├── presentation
│   Capstone_Presentation.pptx
│
└── README.md
```

---

# References

Xing, Y., Zhang, X., & Zhao, R. (2010)  
*What Does the Individual Option Volatility Smirk Tell Us About Future Equity Returns?*

Neuhierl, A., Tang, D., Varneskov, R., & Zhou, X. (2022)  
*Option Characteristics as Cross-Sectional Predictors.*

Lin, T., & Lu, X. (2014)  
*Why Do Option Prices Predict Stock Returns? Evidence from Analyst Tipping.*
