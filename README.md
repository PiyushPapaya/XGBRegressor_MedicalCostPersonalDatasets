# XGBRegressor: Predicting Medical Costs

Based on demographic, lifestyle, and geographic factors, this project forecasts individual health insurance costs using a **XGBRegressor** model. The [Medical Cost Personal Dataset](https://www.kaggle.com/datasets/mirichoi0218/insurance) is used to train the model.

---

## About the Dataset

With **1338 records** and **7 features**, the dataset captures lifestyle and personal data that affects insurance premiums.

### Features

| Feature | Description |
|---------|-------------|
| **age** | Age of the primary beneficiary |
| **sex** | Gender of the insurance holder (`male` or `female`) |
| **bmi** | Body Mass Index — a measure of body fat based on height and weight (ideal: 18.5–24.9) |
| **children** | Number of dependents covered by the insurance |
| **smoker** | Smoking status (`yes` or `no`) |
| **region** | Residential area in the U.S. (`northeast`, `northwest`, `southeast`, `southwest`) |
| **charges** | Individual medical costs billed by insurance |

### Sample Records

| age | sex    | bmi    | children | smoker | region     | charges      |
|-----|--------|--------|-----------|---------|-------------|--------------|
| 19  | female | 27.9   | 0         | yes     | southwest   | 16884.924    |
| 18  | male   | 33.77  | 1         | no      | southeast   | 1725.5523    |
| 28  | male   | 33.0   | 3         | no      | southeast   | 4449.462     |
| 33  | male   | 22.705 | 0         | no      | northwest   | 21984.47061  |
| 32  | male   | 28.88  | 0         | no      | northwest   | 3866.8552    |

### Encoded Version (One-Hot Encoding)

| age | sex | bmi    | children | smoker | charges      | region_northeast | region_northwest | region_southeast | region_southwest |
|-----|-----|--------|-----------|---------|--------------|------------------|------------------|------------------|------------------|
| 19  | 0   | 27.900 | 0         | 1       | 16884.92400  | 0                | 0                | 0                | 1                |
| 18  | 1   | 33.770 | 1         | 0       | 1725.55230   | 0                | 0                | 1                | 0                |
| 28  | 1   | 33.000 | 3         | 0       | 4449.46200   | 0                | 0                | 1                | 0                |
| 33  | 1   | 22.705 | 0         | 0       | 21984.47061  | 0                | 1                | 0                | 0                |
| 32  | 1   | 28.880 | 0         | 0       | 3866.85520   | 0                | 1                | 0                | 0                |

### Statistical Summary

| Metric | age | bmi | children | charges |
|--------|-----|-----|-----------|----------|
| **count** | 1338 | 1338 | 1338 | 1338 |
| **mean** | 39.21 | 30.66 | 1.09 | 13270.42 |
| **std** | 14.05 | 6.10 | 1.21 | 12110.01 |
| **min** | 18.00 | 15.96 | 0.00 | 1121.87 |
| **25%** | 27.00 | 26.30 | 0.00 | 4740.29 |
| **50%** | 39.00 | 30.40 | 1.00 | 9382.03 |
| **75%** | 51.00 | 34.69 | 2.00 | 16639.91 |
| **max** | 64.00 | 53.13 | 5.00 | 63770.43 |

---

## About the Notebook

The notebook walks through the full process of building and evaluating an **XGBRegressor** model for predicting insurance costs. The steps include:

1. Importing necessary libraries  
2. Loading and preprocessing the dataset  
3. Splitting the data into training and testing sets  
4. Optimizing hyperparameters using **Grid Search** and **Random Search**  
5. Training the XGBRegressor model  
6. Extracting model weights and feature importance  
7. Evaluating predictions using **Mean Absolute Error (MAE)** and **R² score**  
8. Visualizing performance: learning curves, actual vs predicted values, and residuals  

The learning curve shows that the model generalizes well. Training and validation scores converge as the training size increases, indicating stable learning without overfitting.

---

## Results

### Model Parameters and Coefficients

| # | Parameter | Value |
|---|------------|-------|
| 1 | Bias | -7284.280 |
| 2 | Age | 244.876 |
| 3 | Sex | -393.978 |
| 4 | BMI | 102.972 |
| 5 | Children | 367.047 |
| 6 | Smoker | 23389.500 |
| 7 | Northeast | -9958.670 |
| 8 | Northwest | -10502.200 |
| 9 | Southeast | -10121.800 |
| 10 | Southwest | -10909.600 |

### Performance Metrics

| Metric | Value |
|---------|--------|
| **Mean Absolute Error (MAE)** | 4178.99 |
| **R² Score** | 0.7449 |

The model predicts costs reliably up to around **30,000**, but tends to underestimate very high costs (above 40,000).  
Smoking status and region have the greatest influence on predictions, followed by BMI and age. This aligns with expectations, as lifestyle and geographic factors strongly impact insurance pricing.

---

Notebook created and trained on [Kaggle](https://www.kaggle.com) by **Piyush Nagpal**.
