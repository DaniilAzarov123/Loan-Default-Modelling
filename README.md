# Loan-Default-Modelling

This repository contains an analysis of bank loan data from Kaggle: [Bank Loan Data](https://www.kaggle.com/datasets/udaymalviya/bank-loan-data/data).
A version of this analysis (excluding the Naive Bayes model) is also available as a Kaggle notebook here: [Loan Default Models – Kaggle Notebook](https://www.kaggle.com/code/daniilazarov/loan-default-models).

This project was originally completed as a final assignment for STAT-S 632: Applied Linear Models II at Indiana University. The version presented here is a refined and more concise version of that work.

## The main files

- `loan_data.csv`: The dataset used in the analysis
- `LoanDataKaggle.Rmd`: The RMarkdown file containing the full analysis
- `LoanDataKaggle.pdf`: A rendered PDF version of the RMarkdown file, including code output

## Data Description

This dataset contains 45,000 loan applications and includes 14 features across the following categories:

- **Personal demographics**:
    - Age of the applicant
    - Gender of the applicant
    - Educational background (High School, Bachelor, Master, etc.)
    - Annual income of the applicant
    - Years of employment experience
    - Type of home ownership (rent, own a house, mortgage)
- **Financial status**:
    - Length of the applicant's credit history
    - Credit score of the applicant
    - Whether the applicant has previous loan defaults (yes or no)
- **Loan details**:
    - Loan amount requested
    - Purpose of the loan (personal, education, medical, etc.)
    - Interest rate on the loan
    - Ratio of loan amount to income
- **Target variable**
    - Loan status:
        - 1 = Loan repaid successfully
        - 0 = Loan defaulted

## Analysis Overview

The **primary objective** of this project is to build a model that can reliably predict whether an applicant is likely to repay a loan or default, using the available personal, financial, and loan-related features.

### Models Applied

- **Logistic Regression**
    - Model Selection (AIC based)
    - Regularization (Lasso, Ridge)
- **Linear Discriminant Analysis (LDA)**
    - Model Selection
- **Quadratic Discriminant Analysis (QDA)**
    - Model Selection
- **Naive Bayes classifier**
    - Model Selection
- **Random Forest**
- **Boosting** (generalized boosted regression models)

In addition, **permutation-based resampling** was used to evaluate model performance on smaller datasets (subsets of 250 observations), highlighting robustness and generalization ability.

|              Model              |  Accuracy |    Smaller Dataset Permuation   |
|---------------------------------|-----------|---------------------------------|
| Logistic Regression (AIC based) | 37.2%     | 37.2% ± 3.1%                    |
| Logistic Regression (Ridge)     | 86.8%     | 86.8% ± 2.2%                    |
| Logistic Regression (Lasso)     | 47.9%     | 47.9% ± 3.2%                    |
| LDA                             | 80.8%     | 76.5% ± 2.7%                    |
| QDA                             | 71.5%     | 78.4% ± 2.7%                    |
| Naive Bayes Classifier          | 75.9%     | 77.9% ± 2.6%                    |
| Random Forest                   | 90.3%     | 90.4% ± 1.8%                    |
| Boosting                        | 88.4%     | 88.5% ± 1.9%                    |
| Random Chance                   | 65.2%     | 65.0% ± 3.2%                    |


## Summary

- The most accurate models were **Random Forest (90.3%)**, **Boosting (88.4%)**, and **Ridge Regression (86.8%)**.
- The **worst performance** came from the **logistic regression model selected via AIC**, which achieved only **37.2%** accuracy - well below **random chance performance (65.2%)**. This poor result is likely due to **heteroscedasticity** in the data.
- All models demonstrated **robust performance on smaller datasets**. For example, the Random Forest model achieved a mean accuracy of 90.4% with a standard deviation of 1.8% across smaller subsets.
