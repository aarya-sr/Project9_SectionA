Here is a **clean, professional README.md** you can directly use for your GitHub repository.

(I’ve structured it properly with title, description, setup, Streamlit section, results, etc., based on your report .)

---

# House Price Prediction

**Traditional Machine Learning | King County, Washington**

## Project Overview

This project builds an end-to-end Machine Learning pipeline to predict residential property sale prices using historical housing data from **King County, Washington (2014)**.

We implemented data preprocessing, feature engineering, model training, evaluation, and deployment using a Streamlit web application.

**Dataset Size:** 4,600 records, 18 features
**Target Variable:** Sale Price (USD)
**Best Model:** Linear Regression (R² = 0.742)

---

## Problem Statement

Accurately predicting house prices is a critical regression problem in real estate. Pricing depends on:

* Structural attributes (sqft, bedrooms, bathrooms)
* Location (city, ZIP code)
* Property features (view, waterfront, condition)
* Temporal factors (year built)

The goal is to build a model that estimates property prices reliably and explain the key drivers influencing valuations.

---

## Dataset Description

The dataset contains residential transactions from **May–July 2014** across:

* 44 Cities
* 77 ZIP Codes
* 4,600 properties

### Important Features

* `sqft_living`
* `sqft_lot`
* `bedrooms`
* `bathrooms`
* `view`
* `waterfront`
* `yr_built`
* `city`
* `statezip`

---

## Machine Learning Pipeline

### Data Cleaning

* Removed 49 zero-price records
* Removed 2 invalid bedroom/bathroom entries

### Feature Engineering

* Extracted year_sold & month_sold
* Dropped non-informative columns (street, country)

### Outlier Removal

* Applied 1st–99th percentile quantile trimming

### Encoding

* One-Hot Encoding for city & statezip

### Scaling

* StandardScaler applied to continuous area features

### Train-Test Split

* 80/20 split (random_state=42)
* Prevented data leakage by fitting transformers only on training data

---

## Models Implemented

| Model                 | R² Score  | MAE      | RMSE     |
| --------------------- | --------- | -------- | -------- |
| **Linear Regression** | **0.742** | $87,505  | $137,383 |
| Random Forest         | 0.669     | $94,924  | $155,674 |
| Decision Tree         | 0.367     | $146,122 | $215,091 |

Linear Regression performed best and was selected for deployment.

---

## Key Insights

*  `sqft_living` contributes over **50% of predictive power**
*  Location (city & ZIP) is the second strongest driver
* Waterfront & view significantly increase property value
* Most relationships were largely linear → explaining Linear Regression’s strong performance

---

## Model Deployment

The best model and scaler were serialized using `joblib`:

```python
joblib.dump(lr, "house_price_model.pkl")
joblib.dump(scaler, "scaler.pkl")
```

These are used inside the Streamlit app for live predictions.

---

# Streamlit Web App

We developed an interactive Streamlit application that:

* Accepts user inputs (bedrooms, sqft, location, etc.)
* Applies preprocessing (encoding + scaling)
* Loads trained model
* Displays predicted house price instantly

### Run the App Locally

```bash
git clone <your-repo-link>
cd house-price-prediction
pip install -r requirements.txt
streamlit run app.py
```

---

## Tech Stack

* Python
* Pandas
* NumPy
* Scikit-learn
* Matplotlib
* Joblib
* Streamlit

---

## Project Structure

```
├── data.csv
├── House_price.ipynb
├── app.py
├── house_price_model.pkl
├── scaler.pkl
├── requirements.txt
└── README.md
```

---

## Future Improvements

* Apply log transformation to price
* Implement Ridge & Lasso Regression
* Add k-fold cross-validation
* Try XGBoost / LightGBM
* Deploy as REST API (FastAPI/Flask)
* Cloud deployment (AWS / Render / Streamlit Cloud)

---

## Contributors

1. Prachee Dhar, Streamlit & Report
2. Aarya Srivastava,  Model Evaluation
3. Suhaani Garg,  Preprocessing
4. Manjeet,  Data Sourcing & Model Training

---

## Conclusion

This project demonstrates:

✔ Full ML pipeline implementation
✔ Model comparison & evaluation
✔ Feature importance analysis
✔ Deployment-ready model
✔ Streamlit integration

The final model explains **74.2% of variance** in housing prices and provides reliable real-world predictions.
