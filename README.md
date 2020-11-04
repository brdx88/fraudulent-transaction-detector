# Fraudulent Transaction Detector

Fraud has become a scandal in financial reporting. Evidently, many large companies
were dragged into fraud cases such as SK Global, Vivendi, Enron, Parmalat, Adelphia, Cendant,
WorldCom, and Royal Ahold (Albrecht, et al., 2008). Companies are caught up in the situation of
business globalization which has triggered intense business competition. As a result, companies
are looking for any way to keep their business operating properly and even become winners in
global business competition. One of the ways is to commit financial reporting fraud.

There is a lack of public available datasets on financial services and specially in the emerging mobile money transactions domain. Financial datasets are important to many researchers and in particular to us performing research in the domain of fraud detection. Part of the problem is the intrinsically private nature of financial transactions, that leads to no publicly available datasets.

We present a synthetic dataset generated using the simulator called PaySim as an approach to such a problem. PaySim uses aggregated data from the private dataset to generate a synthetic dataset that resembles the normal operation of transactions and injects malicious behaviour to later evaluate the performance of fraud detection methods.

PaySim simulates mobile money transactions based on a sample of real transactions extracted from one month of financial logs from a mobile money service implemented in an African country. The original logs were provided by a multinational company, who is the provider of the mobile financial service which is currently running in more than 14 countries all around the world.

This synthetic dataset is scaled down 1/4 of the original dataset and it is created just for [Kaggle](https://www.kaggle.com/ntnu-testimon/paysim1).

Transaction Fraud occurs when a stolen payment card or data is used to generate an unauthorized transaction. The move to real-time transactions is causing significant security challenges for banks, merchants and issuers alike. Quicker transaction times increase the chances of fraudulent transactions going undetected. -*paygilant.com*

# Problems
A business can lose a significant amount of assets due to fraud. At an extreme level, the effects of fraud can even shut down a company. Based on this dataset, we could find:
1. Does type of transaction affect the fraud transaction? 
2. Are transactions flagged as fraud is the real fraud transaction? 
3. Can we predict the transaction which has a fraud pattern?

# Goals
1. Find out the correlation between fraud transaction and type of transaction, flagged as fraud, amount of transaction, transaction's timestamp, and anything.
2. Make a Machine Learning model to predict whether the transaction is fraud or not.





# Conclusions
1. The Fraudulent in this dataset is obviously not balance 99% : 1%, but at least we know that most transactions are safe. However maybe it's only 1% transactions which fraud, but when it comes to 'amount', there are \$1,467,967 are fraud (89.2%) and \$178,197.0 are not fraud (10.8%).

2. 16 transactions flagged as fraudulent, but actually there are 8213 transactions are fraud. We definitely can't use `isFlaggedFraud` feature because there are 8197 fraud transaction which are not flagged as fraudulent transaction. 

3. We see all transactions which has been flagged (\$4,861,598) is a lot bigger than the actual (\$1,467,967), eventhough the transaction is way smaller (16 transactions) than the actual fraud (8213 transactions).
This `isFlaggedFraud` feature is so irrelevant for us to see which transaction is fraud.

4. We now know that 100% fraud transaction came from customer recipient, while the transaction which not fraud is from 66.1% Customer and 33.9% Merchant.

5. Most of the number of general transaction is used for cash out and payment:
  - 35.2% of transactions is used for cash out
  - 33.8% of transactions is used for payment
  - 22.0% of transactions is used for cash in
  -  8.4% of transaction is used for transfer
  -  6.5% of transaction is used for debit

6. All fraud transactions is coming from 'transfer' and 'cash out' transaction type.

7. Fraudulent transaction is using different origin name and different destination name.

8. The patterns of fraudulent transactions are either:
  - 1 origin name for 1 destination name, or
  - 1 origin name for 2 destination name.

  But fraudulent transaction tends to using 1 origin name with 1 different destination name. 99.5% fraudulent transaction came from 1 different destination name and 0.5% using 2 same destination name with using 1 origin name.

9. Fraudulent transaction tends to emptying the origin's balance, especially origin's balance which lower than equal \$10,000,000. 

10. The fraudulent behavior of the agents aims to profit by taking control customers accounts and try to empty the funds by transferring to another account and then cashing out of the system. The difference pattern of fraud and not fraud transaction is very contrast.

11. No matter what, if there's a deviation between origin and destination's balance, that transaction will be called as fraud.

12. Our Machine Learning model using Xtreme Gradient Boosting algorithm can predict fraud transaction with Recall metrics: 0.99 of 1.0 because in this case we are going to reduce the False Negative (the actual is fraud, but model predicts not fraud).

# Recommendations
1. Don't use `isFlaggedFraud` again.
2. Otherwise, use our Machine Learning model with the best Recall metrics is 0.99 of 1.00. Our model can predict whether the transaction is fraud or not with minimum error.
