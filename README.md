# City of Manila Seasonal Weather Forecasting
### Evaluating 14-Day Ahead Weather Predictions in the City of Manila: A Comparative Multivariate Study Using ARIMAX and Lagged Multiple Linear Regression

---

## Academic Context
**Institution:** Southern Luzon State University
**College:** College of Arts and Sciences  
**Degree:** Bachelor of Science in Mathematics  
**Date:** April 2026  

### **Course Compliance**
This research serves as a partial requirement for the following courses:
* **MAT25 (Statistical Modelling):** ARIMAX Modelling, Multiple Linear Regression, Partial Autocorrelation Function
* **MAT26 (Applied Multivariate Analysis):** Principal Component Analysis, Hotellings $T^2$ Test

---

## The Research Team
This study is a collaborative effort by a six-member research group.

* **[Sieg Gabriel Sola] (Technical Lead):** Responsible for the mathematical framework, Python implementation, ARIMAX architecture, and statistical diagnostics (PCA, PACF, Hotelling’s $T^2$).
* **Co-Authors:** [Christian Mark Regencia], [Dan Lloyd Otico], [Jerica Sabido], [Jorgia Sabido], [Keziah Nicole Lingahan] (Literature Review, Theoretical Framework, and Documentation).

---

## Methodology Highlight
This project employs a **Two-Tier Architecture** to forecast 14 days of Manila’s weather:

1. **Dimensionality Reduction (PCA):** 12 meteorological variables were transformed into **7 Principal Components**, capturing >90% of atmospheric variance.
2. **Feature Engineering:** Optimal lag windows ($W$) were determined via **Partial Autocorrelation Function (PACF)** diagnostics for each seasonal fold.
3. **Forecasting Models:** * **ARIMAX:** A stochastic approach modeling.
    * **Lagged MLR:** A deterministic baseline using "Direct Training" to eliminate the error snowball effect.

---

## Key Results
* **ARIMAX** demonstrated statistically significant superiority ($p < 0.05$) in high-volatility variables like **Wind Speed** and **Humidity** during the Habagat season.
* While the **MLR** passed the multivariate **Hotelling’s $T^2$ test**, it failed to capture the dynamic atmospheric spikes that the ARIMAX successfully tracked.

---

## Acknowledgements
Special thanks to the faculty of the **SLSU Department of Mathematics** for the mentorship and theoretical foundations provided in MAT25 and MAT26.
