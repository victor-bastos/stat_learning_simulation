# Simulation Plan — MATH 60603A
**Project:** Impact of Multicollinearity on OLS, Ridge, and LASSO Regression

This project studies how increasing correlation among predictors influences:
- **Predictive accuracy** (test RMSE)
- **Estimation variability** (distribution of estimated coefficients)
- **Stability** (for LASSO: overlap of selected variables)
- **Statistical diagnostics**
  - *OLS:* SEs, 95% CIs, p-values, VIF, condition number
  - *Ridge/LASSO:* effective degrees of freedom and coefficient norms (ℓ1/ℓ2)

We vary the predictor correlation (ρ) in a Monte Carlo framework and compare **OLS**, **Ridge**, and **LASSO**.

---

## Data Generation
- Predictors \\(X\\) from a multivariate normal with controllable pairwise correlation \\(\\rho\\).
- Response \\(y = X\\beta + \\varepsilon\\), with some nonzero \\(\\beta\\) (signal) and some zeros (noise).
- Gaussian noise with variance \\(\\sigma^2\\).

## Evaluation Protocol (per ρ)
1. Split into train/test.
2. Fit **OLS**, **Ridge**, **LASSO** (λ via CV for Ridge/LASSO).
3. Repeat **R** times (Monte Carlo).

## Metrics
- **Predictive:** test RMSE.
- **Variability:** sampling distribution of coefficients across replications.
- **Stability (LASSO):** Jaccard overlap of selected sets.
- **Diagnostics:** OLS SEs/CI/p-values, VIF, condition number; Ridge/LASSO effective df and coefficient norms.

---

## How to Run
1. Install R packages: `MASS`, `glmnet`, `ggplot2`, `dplyr`, `purrr`, `tidyr`, `broom`, `car`.
2. Open `simulation_plan.Rmd` in RStudio and click **Knit** (HTML recommended).
3. Adjust parameters in the **Setup** chunk (sample size, p, signal layout, ρ grid, repetitions).
4. Outputs (summaries/plots) are shown in the knitted report; CSVs are written to `results/` (git-ignored).

