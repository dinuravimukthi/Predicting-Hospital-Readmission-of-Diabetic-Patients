# Predicting-Hospital-Readmission-of-Diabetic-Patients

The <a href="https://archive.ics.uci.edu/dataset/296/diabetes+130-us+hospitals+for+years+1999-2008">Diabetes 130-US Hospitals for Years 1999-2008</a><sup>[1]</sup> dataset from UC Irvine Machine Learning Repository contains 101766 instances and 47 features, each instance recording the demographic details, prescribed drugs and dosage changes, conducted tests, and number of visits over a year, number of lab tests, and procedures for a given patient. There are 3 distinct labels: 
* Patient readmits within 30 days (<30)
* patient readmits after 30 days (>30)
* patient did not readmit (No)

This project focuses on predicting whether a patient will readmit to the hospital after he/she is discharged.
Therefore, patients who did not readmit will be considered as one target class, and the rest of the initial labels will be considered as patients who readmitted (Yes) target class.
<br><br>
<a href="https://diabetic-patients-hospital-readmission.onrender.com/">Deployed Link</a>

## Key Steps
### 1. Exploratory Data Analysis
Inspected data types, distributions of numerical features, and unique values of each categorical variable. Identified that many categorical variables contain missing values as a string, denoted by either "?" or "Unknown/Invalid".

### 2. Preprocessing
_<h4>Handling Missing Values</h4>_
* Removed the features that contained >80% of missing instances except the conducted tests.
* Dropped the instances with missing values for the diagnoses features as they cannot be imputed, and only a small number (<2%) of values were missing.
* Dropped the instances with missing values for gender.

_<h4>Handling Duplicated Values</h4>_
Identified that there are multiple records for the same patient for their separate admissions. Decided not to remove these duplicates to prevent the loss of valuable data.

_<h4>Biased Features</h4>_
Most of the features for prescribed drugs contained a single value. Removed the features that had more than 2% of the 'No' values.

### 3. Feature Engineering
* Removed irrelevant columns to the goal of the project.
* Mapped categorical features of many unique values to contain 3-4 distinct values based on the frequency of those unique values and their intentions.
* Removed irrelevant instances for the goal as identified by categorical feature mappings. Eg: deceased patients.
* Created several new features to better capture some identified patterns.

### 4. Encoding
Experimented with both one-hot encoding and a combination of one-hot and ordinal encoding.
Decided to use the combination approach based on results.

### 5. Scaling
Experimented with both min-max scaling and scaling by the standard deviation.
Decided to use the standard deviation scaling approach based on the results.

### 6. Model Selection
Experimented with a total of six models:
* SGD Classifier
* Logistic regression
* Random Forest
* K-Neighbors Classifier
* XGBoost
* Neural Network

### 7. Hyperparameter Tuning
Tuned hyperparameters for the best-performed models: XGBoost and the Neural Network using the grid search cross-validation and the keras-tuner methods respectively.

### 8. Testing
Tested the XGBoost model with the testing subset. 
Achieved a testing accuracy of 0.639 and a recall of 0.535 

<br>

### References
[1] J. Clore, K. Cios, J. DeShazo, and B. Strack. "Diabetes 130-US Hospitals for Years 1999-2008," UCI Machine Learning Repository, 2014. [Online]. Available: https://doi.org/10.24432/C5230J.
