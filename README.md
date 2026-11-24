# employee-attrition-prediction
# Employee Attrition Prediction

Predicting which employees are likely to leave a company, and identifying what drives attrition, using the IBM HR Analytics dataset (1,470 employees, 35 features).

**Notebook:** [employee-attrition-prediction.ipynb](employee-attrition-prediction.ipynb)

## Project Overview
Employee turnover is costly, and only about 16% of employees in this dataset left, so the data is imbalanced. This project compares three models, shows why accuracy alone is misleading, and tunes the decision threshold to catch more leavers.

## Models Compared
- Linear discriminant analysis
- Logistic regression
- Logistic regression with a spline on age

All models were trained on a stratified 75/25 train/test split.

## Key Results
| Model | Accuracy | Precision | Recall | AUC |
|---|---|---|---|---|
| Discriminant Analysis | 0.870 | 0.657 | 0.390 | 0.799 |
| Logistic Regression | 0.864 | 0.636 | 0.356 | 0.811 |
| Logistic Regression with Splines | 0.875 | 0.710 | 0.373 | 0.822 |

- The spline model performed best (AUC 0.82, accuracy 87.5%).
- Accuracy is misleading here: always predicting "No" already gives about 84% accuracy.
- Lowering the decision threshold raised test recall from 36% to 54%, trading precision (64% to 51%).
- Logistic odds ratios show the strongest drivers of attrition are overtime and frequent business travel (odds ratios around 7). Higher job involvement and satisfaction are protective.

## Tools
Python, pandas, scikit-learn, statsmodels, patsy, seaborn, matplotlib

## How to Run
1. Download the dataset (IBM HR Analytics Employee Attrition dataset, available on Kaggle) and save it as `data/Human_Resources.csv`.
2. Install the libraries:
   ```
   pip install -r requirements.txt
   ```
3. Open `employee-attrition-prediction.ipynb` in Jupyter and run all cells.

## Limitations
- Small dataset with only 59 leavers in
