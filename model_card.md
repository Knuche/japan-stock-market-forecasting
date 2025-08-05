### Model Name
Bayesian-Optimised Random Forest for Japanese Market Prediction

### Model Overview
This model is a regression ensemble trained to forecast Japan's total market close price using lagged values of historical stock prices. Features include daily lags, multi-day rolling statistics, and percent changes. Hyperparameters were tuned using Gaussian Process-based Bayesian Optimisation via `BayesSearchCV` from the `scikit-optimize` package.

### Intended Use
- Exploratory forecasting in financial markets
- Demonstration of time-aware model development
- Benchmarking for time-series feature engineering pipelines

### Performance Summary
- **Random Forest**: R² = 0.0510, RMSE ~2.13B
- **Bayesian RF**: R² = -7.6597, RMSE ~2.13B
- Feature importance: dominated by 1–5 day lags and 7-day rolling averages
- Weak model generalisation suggests non-stationarity in market behaviour

### Limitations
- Aggregating all stocks into a single target variable may introduce noise from unrelated sectors
- The model does not incorporate macroeconomic indicators or sector classifications
- Feature importance is directional but not causal
- R² values close to zero or negative indicate limited predictive power on test data

### Ethical Considerations
- This model is for educational and analytical use only
- It should not be used for financial advice or real-time trading
- Bias may arise from survivorship bias in stock datasets or unbalanced sector weighting

---