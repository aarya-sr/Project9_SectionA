Project 9: House Price Prediction

From Data Cleaning to Deployment-Ready ML System


1. Project Overview -->

This project focuses on building a complete machine learning pipeline to predict residential property prices in King County, Washington (2014).


The objective is to:

• Build regression models using classical ML techniques

• Identify key drivers influencing house prices

•  model performance using evaluation metrics

• Deploy the best-performing model via a Streamlit application



2. Dataset Overview -->

Source: King County House Sales Dataset

Records: 4,600

Features: 18

Target Variable: Sale Price (USD)

Time Period: May–July 2014

Coverage: 44 cities, 77 ZIP codes



3. System Architecture -->

Raw Data
   ↓
Data Cleaning
   ↓
Feature Engineering
   ↓
Outlier Removal
   ↓
Train-Test Split
   ↓
Encoding + Scaling
   ↓
Model Training
   ↓
Model Evaluation
   ↓
Best Model Selection
   ↓
Model Serialization
   ↓
Streamlit Deployment



4. Technology Stack -->

• Component	Technology

• Data Processing	Pandas, NumPy

• ML Models	Linear Regression, Random Forest, Decision Tree

• Evaluation	MAE, RMSE, R²

• Visualization	Matplotlib

• Model Saving Joblib

• Deployment	Streamlit



5. Methodology -->

1. Data Cleaning ->

• Removed 49 zero-price records

• Removed 2 invalid bedroom/bathroom entries

2. Feature Engineering ->

• Extracted year_sold, month_sold

• Dropped non-informative features (street, country)

3. Outlier Removal ->

Applied 1st–99th percentile quantile trimming

4. Encoding ->

One-Hot Encoding on city and statezip

5. Scaling ->

StandardScaler applied to area-related features

6. Train-Test Split ->

• 80/20 split with random_state=42

• Data leakage prevention ensured



6. Models Implemented -->

• Model	MAE	RMSE	R² Score

• Linear Regression	-> $87,505	$137,383	0.742

• Random Forest	-> $94,924	$155,674	0.669

• Decision Tree	-> $146,122	$215,091	0.367



7. Key Findings -->

• sqft_living contributes ~51% of predictive importance

• Location features significantly influence pricing

• Linear Regression outperformed more complex models

• Model explains 74.2% of variance in house prices



8. Deployment -->

The best-performing model (Linear Regression) was serialized:

joblib.dump(lr, "house_price_model.pkl")
joblib.dump(scaler, "scaler.pkl")

A Streamlit web application allows users to:

• Input property details

• Generate price predictions

• Interact with the trained model


9. Repository Structure -->

├── data.csv
├── House_price.ipynb
├── House_Price_Prediction_Report.pdf
├── requirements.txt
└── README.md


10. Future Improvements -->

• Apply log transformation on target variable

• Use Ridge / Lasso Regression

• Implement K-Fold Cross Validation

• Evaluate XGBoost / LightGBM

• Deploy as REST API


11. Contributors -->

Team contributions and individual roles are detailed in the project report.


12. Conclusion -->

This project demonstrates:

• End-to-end ML pipeline

• Rigorous model comparison

• Feature importance analysis

• Deployment-ready architecture

• Real-world regression problem solving


The final model achieves R² = 0.742, making it a strong predictive system for residential property pricing.
