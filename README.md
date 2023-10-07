# Data Mining Project
This repository showcases the final project completed as part of the Data Mining course instructed by Prof. Butler at the University of Bishop's.

## Project Objective
The primary goal of this project is to construct a predictive model capable of determining the probability that a given customer will default on a loan. To achieve this, a customer's profile is composed of a list of bank transactions leading up to the loan request. Each transaction is categorized as either a debit (negative values indicating money leaving the account) or a credit (positive values indicating money entering the account). The customer's profile includes the following attributes for 15,000 customers:

Id: Customer identification number
dates: Transaction dates
transaction_amount: Numpy array of credits and debits (varied length across customers)
days_before_request: Days before loan request for each transaction
loan_amount: Amount loaned to the customer by the bank
loan_date: Date of the loan
outcome: isDefault: Customer's repayment status (0 for paid back, 1 for not paid back)

## Algorithm Selection
For this dataset, we employed various classifiers, including "SVM," "KNearestNeighbor," "DecisionTree," "RandomForest," and "GradientBoosting." Notably, RandomForest and GradientBoosting classifiers are ensemble learning algorithms known for their capacity to enhance model performance by combining predictions from multiple models. We expect these two algorithms to outperform the others. The GradientBoosting classifier, in particular, demonstrates superior performance compared to RandomForest (AUC = 0.713%). However, a t-test conducted on these two classifiers yields a p-value of 0.028, indicating no significant difference in their performance.

## Confidence Interval
The highest accuracy achieved by our model is 0.73%. Using the confidence interval formula, we can assert with 95% confidence that the true success rate falls within the range of [0.64, 0.81].

Identifying Safe and Risky Customers
We can categorize customers into subsets based on their risk level. We define a threshold to identify safe and risky customers:

isPay_thresh = 0.15: Customers with isDefault = 0 (indicating payback)
notPay_thresh = 0.95: Customers with isDefault = 1 (indicating non-payment)
By applying these thresholds to the predictions for 5,000 customers in the test set, we identify customers with y_pred values below isPay_thresh as safe customers and those with y_pred values above notPay_thresh as risky customers.

## Predictive Features
Our feature construction is based on nine attributes for each customer:

Minimum, maximum, mean, and standard deviation of transaction history
The count of negative and positive transactions
The mean of all negative transactions
The total number of transactions
The amount of loan each customer has paid or not paid
Feature importance analysis reveals that min, std, and max have the lowest importance, while loan_amount is the most significant predictor for our model.

## Intuitive Feature Selection
The chosen features are primarily derived from the transaction history of each customer, making them highly relevant for the predictive task at hand. Incorporating transaction dates could further enhance the model's accuracy by considering transaction activity aggregated by category over time steps, such as weekly aggregation of transactions.

The feature selection aligns with the intuition that transaction history, transaction counts, and loan repayment behavior are key factors in predicting loan default.
