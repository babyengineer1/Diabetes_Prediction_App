# Diabetes_Prediction_App

🩺 Diabetes Prediction Project
Using data to detect diabetes risk early, and make healthcare more proactive, not reactive.

## Why I Built This
Let's face it: diabetes is a massive health problem. It develops quietly and often goes undetected until it's serious. The frustrating part? We have the data to spot it early, we're just not using it well enough.
So, I set out to build a machine learning model that could predict a person's risk of diabetes based on their basic health information, such as age, blood glucose, BMI, and lifestyle factors like smoking. But I didn't stop at just building a model. I turned it into a real-time prediction web app using Streamlit, so anyone, a doctor, a clinic assistant, or even a curious patient, can use it instantly.
This wasn't just a coding exercise. It was a chance to solve a real-world problem in a way that's accessible, intuitive, and actually usable.

## What This Project Does
The final product is an intelligent web app that:
* Accepts patient data through a simple form.
* It runs it through a trained machine learning model.
* Returns a prediction: "High Risk" or "Likely Non-Diabetic", in under a second.
It's designed to be both accurate and interpretable, focusing on real-world impact.

## How I Built It
### 1. Understanding the Data
I worked with a dataset of 100,000 records, each containing health metrics like:
* Age, Gender
* Hypertension & Heart Disease status
* Smoking history
* BMI, HbA1c level, Blood Glucose
* Diabetes outcome (target)
I started with a full EDA (Exploratory Data Analysis) to spot trends, distributions, and correlations. Unsurprisingly, HbA1c and blood glucose were highly predictive, but age and smoking mattered too.

### 2. Preprocessing & Feature Engineering
* Encoded categorical values like gender and smoking history.
* Checked for missing or strange values (luckily, it was clean).
* Considered feature scaling and transformations but kept it simple since tree-based models handle that well.

### 3. Model Selection & Training
I trained and compared three models:
* Logistic Regression — good for interpretability
* Random Forest — a strong baseline
* XGBoost — my final choice, thanks to superior performance

Metrics used:
* Accuracy: overall correctness
* Recall: caught the true positives (super important here!)
* F1-score: balanced view of precision vs recall
* ROC-AUC: overall model quality
I chose XGBoost because it consistently offered the best trade-off between accuracy and recall, which is vital in a medical use case, missing a real diabetes case is worse than flagging a false one.

### 4. Building the Streamlight App
Once I had the model, I wanted to make it easy to use. That's where Streamlit came in. I built a clean, intuitive app that:
* Takes user input via sliders and dropdowns
* Encodes the data behind the scenes
* Runs the prediction using the saved model
* Gives a clear result
This app can be deployed anywhere, local machine, cloud, or integrated into a clinic's system.

## Challenges I Faced
* Handling categorical data in Streamlit: XGBoost needs numeric input, so I had to map categories exactly like I did during training manually.
* Consistency between training and inference: I made sure the model and the app "speak the same language" in terms of features.
* Balancing model performance and usability: I didn't just chase high accuracy, I optimized for business value, focusing on minimizing false negatives.

## Tech Stack
* Python: Core language
* Pandas & NumPy: Data wrangling
* Matplotlib & Seaborn: Data visualisation
* Scikit-learn & XGBoost: Model building
* Streamlit: App interface
* Joblib: Model saving/loading

## Try It Yourself
Clone the repo, install dependencies, and run the app:

pip install -r requirements.txt
streamlit run app.py
You'll be able to enter health details and see a live prediction in seconds.

## What's in This Repo
* app.py: the Streamlight app
* Diabetes.joblib: trained model
* notebook.ipynb: full code and analysis
* README.md: you're reading it!
* requirements.txt: all the dependencies

## Final Thoughts
This project isn't just about predicting diabetes, it's about what happens after the prediction. When you give doctors a tool that helps them act early, you're not just saving time, you're potentially saving lives.
Thanks for checking it out. I hope it sparks ideas, or, better yet, action.
