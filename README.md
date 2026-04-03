# 🛰️ City of Manila Seasonal Weather Forecasting: A Comparative Study
### Evaluating 14-Day Ahead Weather Predictions in the City of Manila: A Comparative Multivariate Study Using ARIMAX and Lagged Multiple Linear Regression

This documentation provides a functional summary of the full research study. The complete and expanded experimental contexts are documented in the associated manuscript.

---

## 📖 Research Overview
This research compares a recursive stochastic approach (ARIMAX) against a direct deterministic approach (Lagged Multiple Linear Regression) to determine which better maintains predictive stability over a 14-day horizon. The models are evaluated using statistical tools such as Hotellings $T^2$ Test and Diebold-Mariano Test and standard metrics such as MAE and RMSE.

---

## ⚙️ Methodology and Framework
1. **Preprocessing and Dimensionality Reduction:**
* **Data Source:** $15$ meteorological parameters were sourced from the Open-Meteo API ($3$ target labels and $12$ predictors).
* **Stationarity:** All features were subjected to Augmented Dickey-Fuller Test and non-stationary variables (Dew Point) were first-order differenced.
* **PCA:** The $12$ predictors were reduced to $7$ Principal Components, retaining $93$% of the explained variance.

2. **Forecasting Models:**
* **ARIMAX:** Utilizes auto_arima for optimal (p,d,q) selection.
* **Direct Multi-Step LMLR:** A high-dimensional framework using $168$ independent linear regressions. Each model is trained to map a 65-predictor feature ($7$ PC lags + $3$ label lags determined from PACF plots) directly to a specific lead time ($h=1,2,3,...,14$), to avoid recursive error propagation.

3. **Seasonal Partitioning:**
To account for the distinct weather patterns in the Philippines, the data is partitioned into four folds:

| **Fold** | **Season** | **Training Range** | **Testing Range** | **Training Rows** |
| :--- | :--- | :--- | :--- | :---: |
| 1 | Habagat | Jan 2023 – Aug 2025 | Sep 01 – Sep 14, 2025 | 973 |
| 2 | Transition | Jan 2023 – Oct 2025 | Nov 01 – Nov 14, 2025 | 1034 |
| 3 | Amihan | Jan 2023 – Jan 2026 | Feb 01 – Feb 14, 2026 | 1126 |
| 4 | Dry Season | Jan 2023 – Feb 2026 | Mar 01 – Mar 14, 2026 | 1154 |

4. **Evaluation and Validation:**
* **Multivariate Validation:** Hotelling's $T^2$ test to detect mean vector drift in $14$-day forecasts.
* **Statistical Superiority:** Diebold-Mariano Test to identify if the ARIMAX's stochastic advantage is statistically significant over LMLR.
* **Accuracy Metrics:** RMSE and MAE across all $14$-day predictions.

---

## 📊 Summary of Results

The study evaluated the $14$-day predictive accuracy across four distinct seasonal folds. The **ARIMAX** model was compared against the **Direct Multi-Step LMLR**.

| **Season** | **Target Variable** | **ARIMAX RMSE** | **LMLR RMSE** | **DM p-value** | **Verdict** |
| :--- | :--- | :---: | :---: | :---: | :---: |
| Habagat | Temperature | 0.5492 | 0.5935 | 0.63697 | Tie |
| Habagat | Humidity | 1.4973 | 4.0254 | 0.01704 | **ARIMAX** |
| Habagat | Wind Speed | 0.8045 | 5.7275 | 0.00002 | **ARIMAX** |
| Transition | Temperature | 0.2937 | 0.7325 | 0.00092 | **ARIMAX** |
| Transition | Humidity | 2.5179 | 3.0399 | 0.49152 | Tie |
| Transition | Wind Speed | 1.8051 | 7.5052 | 0.12280 | Tie |
| Amihan | Temperature | 0.4519 | 1.1461 | 0.00621 | **ARIMAX** |
| Amihan | Humidity | 5.4028 | 12.0550 | 0.02444 | **ARIMAX** |
| Amihan | Wind Speed | 0.8284 | 1.9375 | 0.00690 | **ARIMAX** |
| Dry Season | Temperature | 0.7519 | 1.3126 | 0.07309 | Tie |
| Dry Season | Humidity | 3.9352 | 5.6180 | 0.24121 | Tie |
| Dry Season | Wind Speed | 1.7485 | 2.3590 | 0.10653 | Tie |

![ARIMAX vs LMLR Predictions Lineplots](plots/ARIMAX%20vs%20LMLR%20Predictions%20Lineplots.png)

### Summary of Findings
The **LMLR** model failed to capture the volatility of the seasons (although Hotelling's $T^2$ validated the mean vector of **LMLR** predictions at $\alpha=0.01$). The DM-Test ($\alpha=0.05$) revealed that the **ARIMAX** framework significantly outperformed the **LMLR** in 6 out of the $12$ scenarios while maintaining statistical parity for the remaining scenarios.

---

## 🎓 Academic Context
**Institution:** Southern Luzon State University <br>
**College:** College of Arts and Sciences <br>
**Degree:** Bachelor of Science in Mathematics <br>
**Date:** April 2026 <br>

### **Course Compliance**
This research serves as a partial requirement for the following courses:
* **MAT25 (Statistical Modelling):** ARIMAX Modelling, Multiple Linear Regression, Partial Autocorrelation Function
* **MAT26 (Applied Multivariate Analysis):** Principal Component Analysis, Hotellings $T^2$ Test

---

## 👥 Research Team
This study is a collaborative effort by a six-member research group.

* **[Sieg Gabriel Sola](https://www.linkedin.com/in/sieg-gabriel-sola) (Technical Lead):** Responsible for the mathematical framework, Python implementation, models' architectures, and statistical tests and analyses.
* **Co-Authors:** C.M.R., D.L.O., Je.S., Jo.S., K.N.L. (Literature Review and Theoretical Framework).

Special thanks to A.A. for the academic guidance provided throughout the duration of the MAT25 and MAT26 courses.

---
