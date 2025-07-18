# forest-fire-area-predictor

## Introduction
Predicting the area affected by forest fires is a challenging regression problem that involves forecasting a continuous output based on multiple environmental and weather-related variables. Here, we address this task through linear regression, alongside comparisons to KNN and SVM models using an actual fire dataset.

---

## Dataset Overview
The dataset contains information about forest fires with the following features:
- Spatial: `X`, `Y` (spatial coordinates)
- Temporal: `month`, `day`
- Meteorological: `FFMC`, `DMC`, `DC`, `ISI`, `temp`, `RH`, `wind`, `rain`
- **Target Variable**: `area` (burned area in hectares)

---
## Data Preprocessing

1. **Categorical Encoding**  
   - Converted `month` and `day` to numerical values using label encoding.

2. **Missing Values**  
   - No missing values found.

3. **Train-Test Split**  
   - 80% training set (413 samples), 20% test set (104 samples)

4. **Feature Scaling**  
   - Standardized all features using Z-score normalization (StandardScaler).

---

## Models Trained

### Linear Regression (Primary)

- A simple linear model to establish a baseline.
- Implements scikit-learn’s `LinearRegression`.

### Evaluation Metrics

- **MSE**: Mean Squared Error  
- **MAE**: Mean Absolute Error  
- **R² Score**: Coefficient of Determination

---

## Results

### Linear Regression Performance

| Dataset | MSE       | MAE   | R² Score |
|---------|-----------|-------|----------|
| Train   | 2006.48   | 16.34 | 0.0352   |
| Test    | 11748.94  | 24.58 | 0.0033   |


### Comparison with Other Models

| Model            | Train MSE | Test MSE | Train MAE | Test MAE | Train R² | Test R² |
|------------------|-----------|----------|-----------|----------|----------|---------|
| Linear Regression| 2006.48   | 11748.94 | 16.34     | 24.58    | 0.0352   | 0.0033  |
| KNN Regression   | 1673.28   | 11784.99 | 14.08     | 26.36    | 0.1954   | 0.0002  |
| SVM Regression   | 2173.02   | 12126.72 | 10.77     | 19.65    | -0.0449  | -0.0288 |


## Insights & Discussion

- **Low Predictive Power**: All models, including Linear Regression, achieved poor R² scores, indicating that the independent variables poorly explain the burned area.
- **Data Limitations**: The output variable (`area`) is highly skewed with many zeros, making accurate regression difficult.
- **Model Generalization is Low**: Models overfit training data and perform worse on unseen test data.

---

## Conclusion

Linear Regression is **not effective** for accurately predicting forest fire size with the given dataset. Even non-linear models like KNN and SVM did not perform well, suggesting:

- Additional/improved features are needed.
- More advanced models like Random Forests or Neural Networks might help.
- Log transformation of the `area` variable could reduce skew and improve regression accuracy.

---

## Requirements

- Python 3.7+
- numpy
- pandas
- scikit-learn
- matplotlib / seaborn (for visualization)
