
### Project Title
**Japan Stock Market Prediction using Bayesian Optimised Random Forests**

### Overview
This capstone project explores the viability of forecasting Japan's aggregate stock market close using machine learning techniques. Using a time-series approach and historical close price data from a comprehensive set of Japanese stocks, we construct and evaluate multiple regression models. The pipeline includes extensive feature engineering (lags, rolling stats, and returns), model comparison, hyperparameter optimisation via Bayesian methods, and diagnostic analysis of predictions and residuals. The overall objective is to understand the trade-offs between model complexity and generalisation, particularly in volatile financial settings.

### Goals
- Predict aggregate stock market close values using historical stock price data.
- Build a reusable machine learning pipeline with automated preprocessing.
- Use Random Forest as a baseline and apply Bayesian Optimisation to improve it.
- Compare model performance across metrics and analyse residual error patterns.
- Interpret the model to assess whether key features align with economic logic.

### Dataset
- **Source:** Kaggle - Huge Japanese Stock Market Dataset (All-in-One)
- **Size:** ~1GB of daily stock OHLCV data across multiple decades
- **Target Variable:** Total Market Close (sum of daily close prices across stocks)
- **Features:** Lagged closes, rolling mean/std deviation, and percent changes

### Models Used
1. **Random Forest Regressor** – Baseline tree model
2. **Bayesian-optimised Random Forest** – Final tuned model

### Key Results
| Model              | RMSE          | MAE             | R²      |
|-------------------|---------------|------------------|----------|
| Random Forest      | 2128878418.02 | 420191803.27     | 0.0510   |
| Bayesian RF (best) | 2128878418.02 | 2002203305.98    | -7.6597  |

### Interpretation of Results
While the Random Forest model achieved a very modest R² (0.0510), the Bayesian-optimised version dramatically underperformed with a negative R² of -7.6597, indicating substantial overfitting. Both models reached similar RMSE values (~2.1B JPY), but the optimised model suffered from much larger average errors (MAE).

This outcome highlights several key lessons:
- **Bayesian optimisation is not always better**: With noisy or unstable targets, extensive tuning can lock onto spurious correlations.
- **The market's short-term behaviour is complex**: Despite strong autocorrelation in price levels, one-day-ahead predictions remain difficult, especially during volatile periods.
- **Rolling features contributed meaningfully**: Feature importance plots identified 7-day rolling means and short lags (1–5 days) as dominant predictors.
- **Residual analysis showed time-dependent error spikes**: These typically occurred around price gaps, market holidays, or large shocks, suggesting areas for potential volatility modeling in future work.

### Files Included
- `CAW 25.3 Capstone Japan Stock Market Predictor Model.ipynb`: Full code and commentary
- `model_output/best_model_rf.pkl`: Final trained Random Forest model
- `model_output/scaler.pkl`: StandardScaler instance used for input transformation
- `model_output/sample_predictions.csv`: Actual vs predicted values for test set
- `model_output/feature_names.csv`: Final model's input features

### How to Run
1. Clone repository or download this project folder
2. Install dependencies: `pip install -r requirements.txt`
3. Open the Jupyter notebook and run all cells in order
4. Review saved outputs in the `model_output/` directory
5. The full model output has not been saved due to file size restrictions in github, but the other model outpus have.

---

