# Credit Risk Scoring Model

**Author:** Ngoc Lam  
**University of Virginia**  
**Computer Science | Data Science**

## Overview
## Overview

This project develops a credit risk scoring model using the German Credit dataset to predict whether an applicant is likely to represent a good or bad credit risk.

The project combines exploratory data analysis, data preprocessing, and Logistic Regression to identify patterns associated with credit risk and evaluate the model's ability to distinguish between lower-risk and higher-risk applicants.

## Dataset

The project uses the German Credit dataset from the UCI Machine Learning Repository.

* 1,000 loan applicants
* 20 applicant and loan features
* Binary credit-risk outcome
* 700 good-credit applicants
* 300 bad-credit applicants

Features include:

* Credit amount
* Loan duration
* Age
* Checking account status
* Savings status
* Credit history
* Employment
* Housing
* Loan purpose
* Property information

For modeling, the target variable was transformed to:

* `0` = Good credit
* `1` = Bad credit

## Exploratory Data Analysis

EDA was conducted to understand differences between good- and bad-credit applicants.

### Key Findings

**Credit Amount**

Bad-credit applicants borrowed approximately **3,938** on average compared with **2,985** for good-credit applicants.

**Loan Duration**

Bad-credit applicants had an average loan duration of **24.86 months**, compared with **19.21 months** for good-credit applicants.

**Age**

Good-credit applicants were approximately **36.22 years old** on average, while bad-credit applicants averaged **33.96 years**.

**Checking Account Status**

Checking-account status showed substantial differences in observed default rates. Applicants with negative checking-account balances (`A11`) had an observed bad-credit rate of approximately **49.3%**, compared with **11.7%** for the `A14` category.

**Credit History**

Observed bad-credit rates also varied considerably across credit-history categories, suggesting that credit history may provide useful information for predicting applicant risk.

## Data Preprocessing

The dataset contains both numerical and categorical variables.

Numerical features were standardized using `StandardScaler`, while categorical features were transformed using `OneHotEncoder`.

A Scikit-learn `ColumnTransformer` and `Pipeline` were used to combine preprocessing and Logistic Regression into a reproducible modeling workflow.

The data was divided into:

* 80% training data
* 20% testing data

Stratified sampling maintained the original 70/30 distribution of good- and bad-credit applicants in both sets.

## Model

A **Logistic Regression** classifier was trained to estimate the probability that an applicant belongs to the bad-credit class.

Logistic Regression was selected because it provides both classification probabilities and interpretable coefficients that can help explain which applicant characteristics are associated with higher or lower predicted credit risk.

## Model Performance

At the default classification threshold of `0.50`, the model achieved:

| Metric    | Score |
| --------- | ----: |
| Accuracy  | 78.0% |
| Precision | 66.7% |
| Recall    | 53.3% |
| F1 Score  | 59.3% |
| ROC-AUC   | 80.4% |

The ROC-AUC of approximately **0.80** indicates that the model provides useful separation between good- and bad-credit applicants.

## Threshold Analysis

Because failing to identify higher-risk applicants can be costly, alternative classification thresholds were evaluated.

| Threshold |  Accuracy | Precision |    Recall |        F1 |
| --------- | --------: | --------: | --------: | --------: |
| 0.50      |     78.0% |     66.7% |     53.3% |     59.3% |
| 0.40      | **79.0%** |     63.2% | **71.7%** | **67.2%** |
| 0.30      |     75.5% |     56.3% |     81.7% |     66.7% |

A threshold of **0.40** was selected as an illustrative operating point because it substantially increased recall while maintaining strong overall accuracy and improving the F1 score on the test data.

At this threshold, the model correctly identified **43 of 60** bad-credit applicants, compared with 32 at the default 0.50 threshold.

## Feature Interpretation

Logistic Regression coefficients were analyzed to understand which characteristics were associated with predicted credit risk.

Examples of features associated with **higher predicted risk** included:

* Loan purpose category `A46`
* Property category `A124`
* Negative checking-account balance (`A11`)
* Low savings (`A61`)

Examples of features associated with **lower predicted risk** included:

* Checking-account category `A14`
* Credit-history category `A34`
* Loan purpose category `A41`
* Higher savings category (`A64`)

These relationships represent associations within the fitted model and should not be interpreted as causal effects.

## Technologies

* Python
* Pandas
* NumPy
* Matplotlib
* Scikit-learn
* Jupyter Notebook

## Project Structure

```text
Credit-Risk-Scoring-Model/
│
├── data/
│   ├── german.data
│   └── german.doc
│
├── credit_risk.ipynb
└── README.md
```

## Limitations

The dataset contains only 1,000 observations and represents historical German credit data, so results should not be interpreted as a production-ready lending system.

The 0.40 classification threshold was explored using the test data for this educational project. In a production modeling workflow, threshold selection and model tuning should be performed using a validation set or cross-validation before conducting final evaluation on an untouched test set.

Additionally, this model should not be used to make real lending decisions without further validation, fairness analysis, regulatory review, and consideration of the costs associated with different classification errors.

## Conclusion

The project demonstrates an end-to-end credit risk modeling workflow, including data exploration, preprocessing, classification, model evaluation, threshold analysis, and interpretation.

The Logistic Regression model achieved a **ROC-AUC of 0.804**, while threshold analysis demonstrated how classification decisions can be adjusted depending on the tradeoff between identifying higher-risk applicants and incorrectly flagging lower-risk applicants.
