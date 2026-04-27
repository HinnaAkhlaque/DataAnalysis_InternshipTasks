**Task - 4: Predicting Insurance Claim Amounts**

**Objective:**
Estimate medical insurance claim amounts based on personal data using a supervised machine learning approach. The goal is to build a Linear Regression model that can accurately predict insurance charges from features such as age, BMI, smoking status, number of children, sex, and region.


**Approach:**

1. Data Exploration
Loaded the dataset and ran df.describe() to understand distributions.
Confirmed no null values across all columns.
Identified that charges is right-skewed (mean $13,270 >> median $9,382), indicating a small group of high-cost patients pulls the average up.

3. Data Preprocessing
Encoded categorical columns using LabelEncoder:
sex → 0/1
smoker → 0/1
region → 0–3

Separated features (X) and target variable (y = charges)
Applied an 80/20 train-test split with random_state=42
Scaled features using StandardScaler to normalize the input range

3. Model Training
Trained a Linear Regression model using sklearn.linear_model.LinearRegression.
Model learned a weighted combination of all features to predict charges.


4. Visualizations
Three key visualizations were created to understand feature impact:
a) BMI vs Charges: Shows smokers form a high-charge cluster; BMI has a steeper effect for smokers
b) Age vs Charges: Reveals three charge tiers: non-smokers (low), moderate smokers, high-BMI smokers
c) Charges by Smoking Status: Histogram showing non-smokers cluster under $15,000; smokers spread $15,000–$60,000+.


5. Model Evaluation
Evaluated on the test set using three metrics:

pythony_pred = model.predict(X_test_sc)
print("MAE: ",  mean_absolute_error(y_test, y_pred))
print("RMSE:", np.sqrt(mean_squared_error(y_test, y_pred)))
print("R²:  ",  r2_score(y_test, y_pred))

**Results/Insights:**

MAE = $4,186      Average prediction error of ~$4,186 per patient
RMSE = $5,799     Larger errors on high-charge outlier patients
R² = 0.783Model   explains 78.3% of variance in charges.

Smoking is the dominant predictor: smokers consistently pay $20,000–$25,000 more than non-smokers, regardless of age or BMI. It was the highest-weighted feature in the model.

Age has a steady linear effect, charges increase gradually with age for all patients, but the gap between smokers and non-smokers is maintained across every age group.

BMI matters most for smokers, for non-smokers, BMI alone does not dramatically raise charges. For smokers, higher BMI compounds the cost significantly.
