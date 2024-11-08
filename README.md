## Project Structure:<br>
1.Data Preprocessing and Feature Extraction: This section is responsible for reading and processing raw physiological data, applying smoothing techniques, and extracting relevant features such as heart rate variability (HRV), respiratory rate, blood oxygen (SpO2), sleep stages, etc.<br>
2.Feature Selection: Uses RFECV (Recursive Feature Elimination with Cross-Validation) to select the optimal subset of features.<br>
3.Model Training: Trains models, such as XGBoost, on the selected features to predict the target variable (Disease Classification).<br>
4.Model Tuning: Fine-tunes model hyperparameters based on the optimal subset of features.<br>
5.PPC Prediction: Uses the tuned model to perform the disease classification task.<br>
## Requirements:<br>
Ensure the following Python libraries are installed:<br>
`pip install pandas xgboost scikit-learn neurokit2 hrvanalysis scipy`<br>
## Workflow:<br>
### 1. Data Preprocessing and Feature Extraction<br>
Load data from an Excel file containing physiological and clinical characteristics, extracting multiple raw physiological data types, including ECG, respiratory rate, SpO2, and accelerometer data. Apply smoothing using a moving average filter. Use the NeuroKit2 library to extract ECG features, including R-peak detection, and the hrvanalysis library to compute HRV features. Additionally, extract features related to respiration, blood oxygen saturation, and sleep.<br>
### 2. Feature Selection<br>
Use Recursive Feature Elimination with Cross-Validation (RFECV) to select the optimal subset of features for each model and dataset. AUC (Area Under Curve) is used as the evaluation metric during feature selection.<br>
### 3. Model Training<br>
Train models, such as XGBoost classifiers, using StratifiedKFold (5-fold) cross-validation to split the data into training and testing sets. Calculate multiple performance metrics, including F1 score, accuracy, precision, and ROC AUC, to evaluate the model’s performance.<br>
### 4. Model Tuning<br>
Optimize hyperparameters using GridSearchCV. The grid search explores different values for parameters such as n_estimators, max_depth, and learning_rate to find the best model configuration.<br>
### 5. PPC Prediction<br>
After completing feature extraction, selection, and model tuning, use the optimized model for disease classification. Print performance metrics, including AUC, accuracy, F1 score, and precision, to assess the model’s effectiveness and predictive capability.<br>
## Notes:<br>
1.The dataset includes physiological data such as ECG, respiration, SpO2, accelerometer readings, and clinical data from electronic medical records, which are crucial for analyzing sleep and other health conditions.<br>
2.Before running the code, ensure the file paths Physiological and Clinical Characteristics of Sleep 100.xlsx and clinical_data.csv are correct.。
