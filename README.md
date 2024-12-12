Project Overview: AnomaData - Automated Anomaly Detection for Predictive Maintenance
This project focuses on leveraging machine learning techniques to automate anomaly detection for predictive maintenance in industrial systems. By analyzing sensor data over time, the goal is to identify unusual patterns or anomalies that could indicate impending failures or maintenance needs. This proactive approach helps optimize maintenance schedules, reduce downtime, and prevent costly breakdowns.

Key Steps and Methodology
Data Collection and Preprocessing:

Dataset: The project uses a time-series dataset that is provided in an Excel file, which contains various sensor readings along with a target variable (y) indicating the presence of anomalies (1 for anomaly, 0 for normal).
Data Cleaning: Redundant columns are removed, and missing values are handled using backward filling. The time column is converted into a datetime format and set as the index to enable time-series analysis.
Exploratory Data Analysis (EDA):

The distribution of the target variable (y) is visualized using count plots.
Anomalies over time are analyzed by resampling the data on an hourly basis to understand their patterns and distribution.
Feature Engineering:

Temporal features are extracted from the time index, such as hour, day, and weekday, to capture the time-dependent patterns in the data.
Rolling statistics (mean) and differences of key columns are added as additional features to capture trends and volatility in sensor readings.
Model Preparation:

The data is split into predictors (X) and the target variable (y).
Standard scaling is applied to the numerical features for better model performance.
The dataset is split into training and test sets using an 80/20 ratio, with stratification to preserve the distribution of anomalies.
Handling Imbalanced Data:

To address the class imbalance (i.e., anomalies are rare), the Synthetic Minority Over-sampling Technique (SMOTE) is used to oversample the minority class (anomalies) in the training set, ensuring that the model learns from a balanced dataset.
Model Training and Evaluation: Several classification models are trained and evaluated, including:

Random Forest Classifier: A robust model for handling imbalanced data with a balanced class weight.
Logistic Regression, Decision Trees, Gradient Boosting, SVM, KNN, and XGBoost: Additional models are evaluated for comparison.
For each model, performance is evaluated using classification metrics such as accuracy, precision, ROC-AUC score, and confusion matrix. Hyperparameter tuning is performed using Grid Search to optimize the Random Forest model, achieving a higher ROC-AUC score.

Model Selection:

Random Forest (RF) is selected as the final model due to its high precision and robust performance across metrics. XGBoost is also considered for its superior AUC score, but Random Forest is preferred for its reliability in making accurate positive predictions.
Model Deployment:

The best-performing model is saved using the joblib library, allowing for easy deployment and future inference.
Summary of Results
Best Model: Random Forest Classifier (RF)
Precision: RF outperforms others slightly in terms of precision, making it more reliable for detecting true positives (anomalies).
ROC-AUC: XGBoost achieved a slightly higher AUC, but RF still provides excellent discriminatory power.
Conclusion: RF is chosen for its precision and overall performance in predicting anomalies.
Deployment
The trained Random Forest model is saved into a file (anomaly_detection_model.pkl) using joblib for deployment. This allows the model to be easily loaded and used for making predictions on new, unseen data.
