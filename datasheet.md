### Dataset Name
Huge Japanese Stock Market Dataset (All-in-One)

### Source
Kaggle: https://www.kaggle.com/datasets/stanleyfok/japanese-stocks-all-data

### Motivation
This dataset is used to investigate whether patterns in past stock closing prices can help forecast the aggregate market movement. This reflects a simplified version of market index prediction using bottom-up aggregation.

### Features Used
- Close price lags: 1, 2, 5, 10 days
- Rolling statistics: 3, 7, 14-day moving averages and volatilities
- Return calculations: 1-day and 5-day percentage changes

### Target Variable
- `Total_Market_Close`: The sum of daily close prices across all stocks in the dataset

### Data Quality
- Timestamps parsed and sorted chronologically
- Missing values forward-filled
- Duplicate timestamps aggregated with mean
- Stocks with missing data were excluded via inner join

### Train/Test Splits
- 80/20 time-based split (no shuffling)
- TimeSeriesSplit (5-fold) used within `BayesSearchCV` for validation

### Preprocessing Steps
- All input features scaled using `StandardScaler`
- Target variable left unscaled for interpretability
- Final features saved to CSV for reproducibility