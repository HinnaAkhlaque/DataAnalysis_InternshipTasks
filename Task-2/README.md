**Task 2 : Credit Risk Prediction**

**Objective:**
The goal of this project is to build a machine learning model that assesses credit risk,
determining whether a loan applicant will default or successfully repay their loan, based on their income,education etc.

Our target variable Loan_Status indicates:
1 (Y) — Loan Approved / No Default
0 (N) — Loan Rejected / Default Risk

**Approach:**
Missing values were found across multiple columns such as:
| Column | Missing | Strategy | Reason |
|---|---|---|---|
| LoanAmount | 22 | **Median** |
| Loan_Amount_Term | 14 | **Mode** | 
| Credit_History | 50 | **Mode** | 
| Gender, Married, etc. | Few | **Mode** | 

*Feature Selection*:
features = ['ApplicantIncome', 'CoapplicantIncome', 'LoanAmount','Loan_Amount_Term', 'Credit_History']

*Train-Test Split*:
80% training / 20% testing
stratify=y used to preserve the 69/31 class ratio in both splits.

*Models Trained*:
Logistic Regression — max_iter=1000
Decision Tree Classifier — max_depth=5

*Evaluation Metrics*:
Accuracy Score
Confusion Matrix
Classification Report (Precision, Recall, F1-Score)

**Results & Insights:**
| Metric | Logistic Regression | Decision Tree |
|---|---|---|
| **Accuracy** | **86%** | 80% |
| Precision (Default) | **0.96** | 0.75 |
| Recall (Default) | **0.58** | 0.55 |
| F1-Score (Default) | **0.72** | 0.64 |
| Recall (No Default) | **0.99** | 0.92 |
| F1-Score (No Default) | **0.91** | 0.87 |
| False Negatives | **1** | 7 |
| Macro Avg F1 | **0.81** | 0.75 |

Logistic Regression outperformed the Decision Tree across every metric
            
