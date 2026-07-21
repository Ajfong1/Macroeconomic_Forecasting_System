# FRED Economic Data Modeling: A VAR Analysis of Macroeconomic and Financial Indicators

This project uses a Vector Autoregression (VAR) model to explore the dynamic relationships between key U.S. macroeconomic and financial indicators, sourced from the Federal Reserve Economic Data (FRED) database. The goal is to understand how inflation, unemployment, interest rates, and equity markets influence one another over time, and to forecast their near-term trajectories.

Variables

UNRATE — U.S. Unemployment Rate (BLS)
CPIAUCSL — Consumer Price Index for All Urban Consumers (BLS)
T10YFFM — 10-Year Treasury Constant Maturity Minus Federal Funds Rate
S&P 500 — Daily closing value of the S&P 500 Index

Methodology

Data Preprocessing: Raw FRED series were cleaned and transformed using McCracken & Ng (FRED-MD) codes — including differencing and log transformations — to achieve stationarity. Post-COVID data (from October 2020 onward) was used to focus on the most relevant economic regime.
Exploratory Data Analysis: ACF/PACF diagnostics and residual analysis were used to validate stationarity assumptions and guide transformation choices for each series.
Model Selection: VAR(1) and VAR(2) specifications were compared using AIC, BIC, HQ, and FPE criteria, along with Granger causality and Breusch-Godfrey tests for serial correlation. VAR(2) was selected as the optimal model, showing meaningfully improved fit and a statistically significant Granger-causal link from financial variables to real economic indicators.
Impulse Response Functions (IRFs): Used to trace how a one-standard-deviation shock to a given variable propagates through the system over a 12-period horizon.
Forecasting: One-year-ahead forecasts with bootstrapped confidence intervals were generated for all four variables, reverse-transformed back to their original scales.

Key Findings

A second-order lag structure (VAR(2)) is necessary to capture delayed adjustment mechanisms; a VAR(1) model implies (incorrectly) that financial markets are fully decoupled from real economic outcomes.
S&P 500 shocks have a statistically significant effect on the 10-Year Treasury Spread at a two-period lag, consistent with capital rotation from fixed income into equities during periods of market optimism.
Forecasts point to a modest cooling in unemployment, continued linear growth in CPI, a stable Treasury spread, and continued upward momentum in equities — though wide confidence bands underscore the inherent uncertainty of macroeconomic forecasting.
Tools

R (VAR modeling via vars package), FRED API/data exports
