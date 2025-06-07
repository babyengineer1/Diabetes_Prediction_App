# Diabetes_Prediction_App
## Introduction
Diabetes is a chronic condition that often goes undiagnosed until complications arise. Early detection is key to effective management and reducing long-term health risks. Stark Health Clinic, a forward-thinking healthcare provider, is seeking to integrate predictive analytics into its workflow to proactively identify individuals at risk of developing diabetes.
This project aims to develop a machine-learning model that can predict diabetes based on basic health and lifestyle attributes. The ultimate goal is to deploy this model within a user-friendly web interface using Streamlit, allowing clinicians or patients to input basic data and receive instant risk predictions.

## Objectives
* Build a predictive model to classify individuals as diabetic or non-diabetic.
* Perform exploratory data analysis (EDA) to understand key drivers of diabetes.
* Integrate the trained model into a real-time Streamlit application.
* Optimise for sensitivity (recall) to minimise missed diagnoses.

## Dataset Overview
* Source: Provided as diabetes_prediction_dataset.csv
* Records: 100,000 individuals

### * Features:
  * Demographic: gender, age
  * Medical history: hypertension, heart_disease
  * Lifestyle: smoking_history
  * Health indicators: bmi, HbA1c_level, blood_glucose_level
  * Target: diabetes (0 = No, 1 = Yes).

## Step Taken
### 1. Data Exploration & Cleaning
  * Verified dataset had no missing values.
  * Checked distributions and outliers using histograms and boxplots.
  * Found HbA1c_level, blood_glucose_level, and age to be highly informative.

### 2. Feature Engineering
* Encoded categorical variables:
  * gender: mapped to numerical values.
  * smoking_history: label-encoded.
* Ensured all input features were numeric to support use with XGBoost.
* No need for feature scaling due to tree-based models.

### 3. Model Training
* Tested three models:
  * Logistic Regression
  * Random Forest Classifier
  * XGBoost Classifier (best performing)

* Used 80/20 train-test split.
  
* Evaluation metrics:
  * Accuracy
  * Recall (priority): to capture more true diabetic cases.
  * F1-score
  * ROC-AUC

XGBoost achieved the best balance of recall and precision.

## 4. Model Deployment
* Saved trained model using joblib.
* Developed an interactive web app using Streamlit.
* App includes:
  * Input form for all relevant fields
  * Encodes values automatically
  * Displays a clear prediction message

Link to app: https://diabetespredictionapp-459u8xctifzcg32rde338e.streamlit.app/ 

## Challenges Encountered
### 1. Categorical Input Handling:
  XGBoost does not accept string inputs. In the app, categorical variables had to be mapped manually, replicating the training-time encoding.
### 2. Model Consistency:
  Ensuring the same feature order, encoding method, and data types were used in both training and prediction phases was critical.

### 3. Trade-offs in Evaluation Metrics:
While overall accuracy was high, the more important metric was recall, to avoid false negatives — i.e., not identifying someone who actually has diabetes.

## Technology Used
* Python: Data handling and modeling
* Pandas / NumPy: Data processing
* Matplotlib / Seaborn: Visualization
* Scikit-learn / XGBoost: Machine learning
* Streamlit: Web app interface
* Joblib: Model serialisation


## What's in This Repo
* app.py: the Streamlight app
* Diabetes.joblib: trained model
* notebook.ipynb: full code and analysis
* README.md: you're reading it
* requirements.txt: all the dependencies

## Conclusion
This project successfully demonstrates the use of machine learning to support early detection of diabetes. The final system combines a well-performing XGBoost model with an intuitive front-end application. It is designed to be accessible, efficient, and informative, helping Stark Health Clinic take a proactive approach in managing patient health.
The approach can be further expanded by incorporating electronic medical records, lab test history, or real-time wearable data for even greater predictive accuracy.
