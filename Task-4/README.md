**Task - 4: Predicting Insurance Claim Amounts**

**Objective:**
<br>
Estimate medical insurance claim amounts based on personal data using a supervised machine learning approach. The goal is to build a Linear Regression model that can accurately predict insurance charges from features such as age, BMI, smoking status, number of children, sex, and region.

<br>
**Approach:**
<br>
1. Data Exploration
<br>
Loaded the dataset and ran df.describe() to understand distributions.
<br>
Confirmed no null values across all columns.
<br>
Identified that charges is right-skewed (mean $13,270 >> median $9,382), indicating a small group of high-cost patients pulls the average up.
<br>

3. Data Preprocessing
<br>
Encoded categorical columns using LabelEncoder:
<br>
sex → 0/1
<br>
smoker → 0/1
<br>
region → 0–3
<br>

Separated features (X) and target variable (y = charges)
<br>
Applied an 80/20 train-test split with random_state=42
<br>
Scaled features using StandardScaler to normalize the input range
<br>

3. Model Training
4. <br>
Trained a Linear Regression model using sklearn.linear_model.LinearRegression.
<br>
Model learned a weighted combination of all features to predict charges.
<br>


5. Visualizations
6. <br>
Three key visualizations were created to understand feature impact:
<br>
a) BMI vs Charges: Shows smokers form a high-charge cluster; BMI has a steeper effect for smokers
<br>
b) Age vs Charges: Reveals three charge tiers: non-smokers (low), moderate smokers, high-BMI smokers
<br>
c) Charges by Smoking Status: Histogram showing non-smokers cluster under $15,000; smokers spread $15,000–$60,000+.


7. Model Evaluation
8. <br>
Evaluated on the test set using three metrics:
<br>
pythony_pred = model.predict(X_test_sc)
<br>
print("MAE: ",  mean_absolute_error(y_test, y_pred))
<br>
print("RMSE:", np.sqrt(mean_squared_error(y_test, y_pred)))
<br>
print("R²:  ",  r2_score(y_test, y_pred))

**Results/Insights:**

MAE = $4,186      Average prediction error of ~$4,186 per patient
<br>
RMSE = $5,799     Larger errors on high-charge outlier patients
<br>
R² = 0.783Model   explains 78.3% of variance in charges.

Smoking is the dominant predictor: smokers consistently pay $20,000–$25,000 more than non-smokers, regardless of age or BMI. It was the highest-weighted feature in the model.

Age has a steady linear effect, charges increase gradually with age for all patients, but the gap between smokers and non-smokers is maintained across every age group.

BMI matters most for smokers, for non-smokers, BMI alone does not dramatically raise charges. For smokers, higher BMI compounds the cost significantly.
