# DM_Project


This is my final project in the course of data mining taught by Prof. Butler at university of Bishop's. 



The goal is to build a model that predicts a probability that a given customer will default on a loan
A customer profile consists of a list of bank transactions preceding the loan request. Each transaction is either a debit
(money going out of account, negative values) or credit (money coming into account, positive values).
Customer profile (attributes) (15000 customers total):
Id – id of each customer
dates – dates of each transaction
transaction_amount – numpy array of credits and debits, length varies across different customers
(your predictions will be primarily based on information in this array)
days_before_request – days before loan request for each transaction
loan_amount – amount loaned to customer by bank
loan_date – date of loan
outcome:
isDefault – did the customer pay back (isDefault=0) or not pay back (isDefault=1)?


Which algorithm did you use and why?

In this dataset, we use some classifiers such as “SVM”, “KNearestNeighbor”, “DecisionTree”,
“RandomForest”, GradientBoosting”. RandomForest and GradientBoosting classifiers are ensemble
learning algorithms.
Ensembles are used to achieve top performance and it combines predictions from multiple models, so it’s
a way to improve performance. So we expect that these two algorithms have better performance among
the others. The gradientBoosting classifier has better performance compaired to RandomForest (AUC =
0.713 %). However, By applying t-test on these two classifiers, we got p-vlaue = 0.028, so there is no
difference between these two algorithms!


How certain are you of the results? Confidence interval

The best accuracy that we got from our model, is 0.73% , so by using the confidence interval formula, we
can say that, we are 95 percent sure that the true success rate lies between [0.64 , 0.81].
Is there a subset of potential customers that are very safe to lend to? A subset that is very dangerous?
We can define a threshold and find them as a safe subset or dangerous subset.
isPay_thresh = 0.15 # isDef = 0 payback
notPay_thresh = 0.95 # isDef = 1 notPayBack
after getting the prediction of test set for 5000 customers, we find the customers who y_pred is less than
isPay_thresh as a safe customers. And customers who y_pred is more than notPay_thresh as a dangerous
customers.



What features of the dataset best predict isDefault?

We construct our data based 9 feature. Per each customer calculated the min, max, mean, std transaction
of the history of the customer, the number of negative and positive transactions for each customer and
also mean of all negative transactions. And also a feature that represent the total number of transaction
for each customer. And the amount of loan each customer has paid or not paid.
Based on the above figure, we can see that min, std and max has the three lowest importance.
Also, loan_amount has the highest importance for our model.


Do these features make sense intuitively? Justify your use of the features?

These features are extracted from the data set mostly based on the transaction history of each customer,
so it make sense to use them. Plus, if we could use the date of each transaction it could make better and
more real results, transaction activity aggregated by category over time steps, for example weekly
aggregation of transactions.
