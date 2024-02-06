# Credit-Risk-Classification
Evaluating a loan risk model based on peer-to-peer lending data.

# Report

## Overview of the Analysis

 This analysis was intended to analyze a peer-to-peer set of banking loans as will set up an anti-risk algorithm. In other words, this software will examine loan requests to determine if they will be "high-risk" loans, or loans where the recipient is likely to default on them. The algorithm reviews the following factors:
-the size of the requested loans (loan_size),
-the interest rate on each loan (interest_rate),
-the debtors' incomes (borrower_income),
-individual debtors' total accumulated debt (total_debt),
-their debt-to-income ratio (debt_to_income),
-individual debtors' number of bank accounts (num_of_accounts),
-various credit report risk indicators (derogatory_marks), and
-whether this specific debtor had prior been identified as high-risk (loan_status).

Upon reading the data, we isolated loan status from the broader CSV and used train_test_split to prepare a logistic regression model. This model took each of the features, or remaining columns in the CSV, and predicted the loan status for all debtors based on those parameters. We subsequently used sklearn's balanced_accuracy_score, confusion_matrix, and classification_report modules to review the precision of our model.

We then ran the training data through imbalanced-learn's RandomOverSampler module to resample and then predict it via a second logistic regression model. That model was also analyzed with balanced_accuracy_score, confusion_matrix, and classification_report.

## Results
MODEL 1
• Balanced accuracy: 95.205% (model was slightly over 95% accurate at identifying true positives and true negatives)

• Precision: 100% for healthy loans, 85% for high-risk loans (the model has 100% confidence at detecting healthy loans and 85% confidence at detecting high-risk loans)

• Recall: 99% for healthy, 91% for high-risk (model got false negatives 1% of the time and false positives 9% of the time)

MODEL 2
• Balanced accuracy: 99.368%
  
• Precision: 100% for healthy, 84% for high-risk

• Recall: 99% for both healthy and high-risk

## Summary

The RandomOverSampled model performs better due to its higher accuracy, jumping from >95% to >99%, and exhibiting a 3% improvement in f1-score.

It is more important to predict '1's, because this model was designed with high-risk detection in mind. Additional resources, such as manual oversight of each loan application, will assist in managing "initial" false positives or false negatives. While both models are generally solid, I currently recommend the ROS model over the original model.



