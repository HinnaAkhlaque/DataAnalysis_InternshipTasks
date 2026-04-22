**Task 2 : Credit Risk Prediction**

**Objective:**
The goal of this project is to build a machine learning model that assesses credit risk,
determining whether a loan applicant will default or successfully repay their loan, based on their income,education etc.

Our target variable Loan_Status indicates:
1 (Y) — Loan Approved / No Default   |
0 (N) — Loan Rejected / Default Risk

**Approach:**
Missing values were found across multiple columns such as:
| Column | Missing | Strategy |
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

Logistic Regression outperformed the Decision Tree across every metric.

Class Imbalance: ~69% approved (Y) vs ~31% rejected (N), the dataset is imbalanced, which directly impacted model recall for defaulters
Loan Amount: Right-skewed with outliers up to 700K. Both approved and rejected applicants had similar distributions, making it a weak standalone predictor
Education: Graduate applicants had a ~71% approval rate vs ~61% for non-graduates
Income: Heavily right-skewed with many outliers. Income alone did not strongly separate approved from rejected applicants
Credit History: The most influential feature — 84% of applicants had positive credit history, strongly correlated with loan approval

**Limitations:**

Low defaulter recall (0.58 for LR, 0.55 for DT)
Nearly half of actual defaulters were wrongly approved due to class imbalance. This is a critical risk in real-world banking
            
