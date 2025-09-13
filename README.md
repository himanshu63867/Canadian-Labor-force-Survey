# Canadian-Labor-force-Survey
_**1. Labor Force Status Prediction**_
**Problem Statement:** The primary objective is to develop a predictive model that can accurately determine an individual's labor force status based on their demographic and socioeconomic characteristics. The model aims to classify individuals into categories such as "Employed," "Unemployed," or "Not in the labor force" using a dataset from a labor force survey.

**Solution:** The problem is framed as a multi-class classification task. A Random Forest Classifier is used to build the model. The key steps of the solution are:

**Data Preprocessing:**

Irrelevant columns like REC_NUM, SURVYEAR, and SURVMNTH are removed.

Columns with more than 40% missing values and rows with missing target values (LFSSTAT) are dropped.

Categorical features are encoded using LabelEncoder.

Missing numerical values are imputed using the median strategy via SimpleImputer.

Numerical features are scaled using StandardScaler to ensure consistent data representation.

**Model Training and Evaluation:**

The data is split into training and testing sets with a test_size of 20%.

A RandomForestClassifier with 100 estimators is trained on the processed data.

The model's performance is evaluated using accuracy score and a classification report. The model achieved an accuracy of approximately 88.03%, with high precision and recall for the "Employed" and "Not in the labor force" categories, which are likely the most prevalent in the dataset.

_**2. Unemployment Rate Prediction**___
Problem Statement: The goal is to build a regression model to predict unemployment rates. The analysis focuses on identifying key factors that influence these rates, with a particular emphasis on sectors with a high percentage of immigrants. The model's insights can be used to inform government policies aimed at improving labor market inclusivity.

**Solution:** The problem is approached as a regression task using the XGBoost algorithm, a powerful gradient-boosting framework known for its performance. The solution pipeline is as follows:

**Data Preparation & Feature Engineering:**

A Date column is created from the SURVYEAR and SURVMNTH features to extract Year, Month, and Quarter.

Irrelevant columns are dropped.

A key feature, Immigrant_Percentage, is engineered by calculating the mean percentage of immigrants in each sector (NAICS_21).

The target variable, UnemploymentRate, is calculated by grouping data by NAICS_21 and IMMIG and taking the mean of the Unemployed variable.

Rows with missing values are filled using the ffill method (forward-fill).

**Model Training and Evaluation:**

A XGBRegressor model is trained on the processed data.

The model's performance is evaluated using Root Mean Squared Error (RMSE) and R-squared (R 
2
 ) score. The model demonstrated a very high R 
2
  score of approximately 0.99 and a low RMSE, indicating that it can accurately predict unemployment rates.

Insights:

Feature importance analysis from the XGBoost model highlights the key factors influencing unemployment predictions.

The analysis identifies the top sectors with the highest unemployment rates among immigrants.

_**3. Hourly Earnings Prediction**_
**Problem Statement:** The objective is to predict the hourly earnings of employed individuals to identify influential factors and detect potential income disparities. The model leverages demographic and employment-related variables such as age, gender, education, and industry.

**Solution:** This is a regression problem solved using a Random Forest Regressor. The methodology involves:

**Data Preparation:**

An interaction feature, AGE_EDUC, is created by multiplying age and education levels.

The target variable, HRLYEARN, is log-transformed to address its likely skewed distribution.

Missing values in the target variable are imputed with the median.

**Preprocessing and Model Training:**

Missing values in the feature set are imputed using a median strategy.

Categorical features (GENDER, NAICS_21) are one-hot encoded.

All features are scaled using StandardScaler.

A RandomForestRegressor model is trained on the prepared data.

**Evaluation:**

The model's performance is assessed using Mean Squared Error (MSE), R-squared (R 
2
 ), and Root Mean Squared Error (RMSE). The model achieved a very high R 
2
  of 0.9995, indicating a strong fit to the training data.

_**4. Predicting Reasons for Leaving a Job**_
Problem Statement: This project aims to predict the reason why an individual left their last job (WHYLEFTN) based on various factors. By developing a classification model, the project seeks to uncover the primary drivers of job separation, which can inform policies aimed at improving job satisfaction and retention.

**Solution:** This is a multi-class classification problem addressed with a Random Forest Classifier. The steps taken were:

**Data Preprocessing:**

Irrelevant columns are dropped.

A key step is the imputation of missing values in both the features and the target variable (WHYLEFTN) using the most_frequent strategy.

Categorical features are encoded using LabelEncoder.

The dataset is then split into training and testing sets.

Model Training and Evaluation:

A RandomForestClassifier is trained on the preprocessed data.

The model's performance is evaluated with accuracy score and a classification report. The model achieved an accuracy of 98.32%. However, the classification report shows that while some classes have high precision and recall, others have very low scores, which may indicate an imbalanced dataset where certain reasons for leaving a job are much more common than others.

Policy Implications: The insights gained from this model could be valuable for the government. By identifying the key drivers of job loss, the government can:

**Target Resources**:Direct resources toward job seekers and skills development in specific areas.

**Evaluate Policies**: Adjust labor market policies to address the root causes of job separation.

**Improve the Labor Market**: Ultimately create a more dynamic and responsive labor market that benefits both individuals and the Canadian economy as a whole.







