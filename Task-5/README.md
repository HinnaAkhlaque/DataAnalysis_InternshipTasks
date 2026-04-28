**Task- 5: Personal Loan Acceptance Prediction**

**Objective::**
Predict which customers are likely to accept a personal loan offer using the UCI Bank Marketing Dataset. The goal is to build a classification model that can help identify high-potential customers and improve campaign targeting efficiency.
<br>
<br>
<br>
**Approach:**
<br>
1. Data Exploration
<br>
Explored key features including age, job, marital status, and education <br>
Visualized loan acceptance rates across different customer segments <br>
Identified class imbalance — the majority of customers reject the offer <br>
<br>
2. Preprocessing
<br>
Label-encoded all categorical variables<br>
Applied StandardScaler for Logistic Regression <br>
Used stratified train/test split (80/20) to preserve class distribution <br>
<br>
3. Modeling
<br>
Trained and compared two classifiers:
<br>
Logistic Regression — with class balancing and feature scaling<br>
Decision Tree — with max depth of 5 and class balancing <br>
<br>
<br>

**Results and Insights:**

Logistic Regression = 88.49% accuracy <br>
Decision Tree = 89.35% accuracy <br>

The Decision Tree outperformed Logistic Regression, particularly in detecting customers who actually accept the loan (class 1 recall doubled from 20% to 40%) <br>
Call duration, previous campaign outcome, and contact timing were the strongest predictors — how and when a customer is contacted matters as much as who they are. <br>
60+ age group had the highest acceptance rate at ~42%, far above all other age groups, <br>
Technicians and Management customers showed the highest relative acceptance rates by job category <br>
Class imbalance remains the key limitation, overall accuracy looks high, but the model still misses a significant portion of actual acceptors
