**Task 3: Customer Churn Prediction — Bank Customers**

**Objective:**
The goal of this project is to build a machine learning model that identifies bank customers who are likely to churn (i.e., close their account and leave the bank). Early identification of at-risk customers allows the bank to take proactive retention actions, reducing revenue loss.

**Approach**

1. Data Cleaning & Preparation:
Dropped non-predictive identifier columns: RowNumber, CustomerId, Surname
Verified no missing values were present in the dataset.

3. Categorical Encoding
Label Encoding applied to Gender (binary feature: Female = 0, Male = 1)
One-Hot Encoding applied to Geography (3 categories → 2 dummy columns: Geography_Germany, Geography_Spain; France used as baseline)


4. Feature Scaling
Applied StandardScaler to normalize numeric features
Scaler was fit only on training data and then applied to the test set

5. Model Training
Algorithm: Random Forest Classifier (100 estimators)
Train/Test Split: 80% training / 20% test (stratified)
 class_weight='balanced', to handles the ~80/20 class imbalance

6. Evaluation
Evaluated using Precision, Recall, F1-Score, and Confusion Matrix
Primary focus metric: Recall on Class 1 (Churners) — missing a churner is more costly than a false alarm.

**Results & Insights:**
The model performs strongly at identifying customers who will stay (recall = 0.97) but misses 56% of actual churners (recall = 0.44). This is the primary area for improvement.

Age is the dominant churn driver — customers aged 40–60 are at the highest risk, with churn rates of 45–55% in that range.
Germany requires targeted intervention — its churn rate is double that of France and Spain despite a smaller customer base; this warrants investigation into local pricing, service, or competition
Product holding is a non-linear risk signal — customers with 1 product churn more, but customers with 3–4 products churn at nearly 100%, suggesting a product mismatch rather than a loyalty effect
Churn is driven by life stage and financial profile, not engagement behavior alone — retention strategies should prioritize middle-aged, high-balance, single-product customers.
