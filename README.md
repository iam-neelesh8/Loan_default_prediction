# Loan Default Risk Prediction 

# Introduction

Individuals and organizations have both relied on loans daily. The activity of taking a loan has become inevitable due to increasing competition in the finance world and a significant number of financial constraints. Loan lending is an essential function for the management of banks and small to large businesses in times of financial difficulty to function smoothly. Loan defaulters’ prediction is one of the important aspects any bank or any financial institution should mainly focus on. It is as important as focusing on the client acquisition to a particular bank.
A person can approach a bank for several reasons , for example to take home loan , vehicle loan , education loan etc. There lie several factors for a bank to understand the demographics of a client and classify him/her if he qualifies for the loan or not. There are several factors that can help a bank to classify a person to the qualified list which includes client’s age , occupation , pay, age, gender, credit history, previous loan history etc. Credit scores are used to measure risk and creditworthiness by industry experts and researchers around the world.
To assess the borrower's credit risk and to make a lending decision, a credit analysis of potential borrowers is required. This allows any bank to determine if the client would be able to repay the debts within instalments over a given span of time. Whenever a customer defaults on their loan repayments, actions should be taken. Therefore, banks should be very keen and monitor its clients and avoid risky clients and monitor all the debts to avoid loss for the banks.

# Problem Description 

The problem description for our project can be best explained with the help of a real-time scenario. A bank named ‘Home Credit’ has a huge customer base and is willing to expand its services by providing home loan to its customers to its clients. This bank is facing a problem in identifying the right customers and classify them as who can repay the amount in a timely manner. For this , we have a huge chunk of data that has all its customer demographics, their previous bank transaction frequencies , credit history and a few other factors which can impact their status if they can qualify or not. Since this is a real problem to deal with for any bank, by identifying trends associated with default risk, the banks can act accordingly, by taking the necessary actions either by denying the loan, reducing the loan amount, lending (at a higher interest rate, etc.

# Description of Data

Source of the dataset: https://www.kaggle.com/competitions/home-credit-default-risk/data
We sourced our data ‘ Home Credit default risk’ from Kaggle. The dataset is a combination of 346 columns initially with huge number of rows and the memory of the dataset is 2.68 GB. It contains 10 main files that can directly or indirectly be useful for our prediction. The set of files in this dataset contains the columns that considered as the main factors to classify the clients into loan defaulters or not.

# Files description :

1. application_{train|test}.csv : Listed here are the main tables, separated into Train (with TARGET) and Test (without TARGET).Each application contains of static data. 

2. bureau.csv : This file consists of the previous credit history provided by other financial institutions reported to Credit Bureau.
3. bureau_balance.csv: This file consists of the history of previous credit balances in the Credit Bureau on monthly basis.
4. POS_CASH_balance.csv : This file contains the information of the applicant's monthly cash and point of sale loan balances with the bank. Every previous credit in the bank is represented by one row per month. 
5. credit_card_balance.csv : This file has the data of Summary of balances from previous credit cards the applicant has on file with the respective bank for the past 12 months. 
6. previous_application.csv: This file has the data of Clients with existing loans already with banks are prohibited from applying for Home Loans. Each application for a loan appears once in data. 
7. installments_payments.csv: This file has the data that shows an analysis of the repayment history associated with the previously disbursed loans from the bank.
8. HomeCredit_columns_description.csv: A description of each column in the data files can be found in this file.

# Methodology

We as a team followed some of the generic steps of how a dataset should be analyzed. Out of those the first step was:

# Data Collection and Exploration :

As mentioned in the previous section our data was collected from Kaggle which typically had about 9 files out of which we used 7 files considering the requirements for our model development. Our data was quite huge because it had all the data of the existing customers who are in association with the bank and some of their previous details. Since it was huge , there was a lot of data imbalance identified. But, before even building the models on the data , we implemented all the data preprocessing techniques on a single file ( application_train.csv) which had all the existing customers data. We identified almost 307511 current customers, out of which we have 291057, has previous data of other loans from the same company. They’re existed large number of null values and data redundancies which as making the data not supportive for model building. So, to prevent this we made sure we remove the columns which had more than 50% of the null values which are not going to be a great contribution for the model building. In addition to this we have performed string indexing where all the categorical values and numerical values were divided and replaced the categorical columns with the most repeated values using mode and used mean values for the numerical columns and performed the one hot encoding as well. Below are the EDAs for the imbalanced data before even developing the models.

# Exploratory Data analysis :

![image](https://user-images.githubusercontent.com/38136560/224322158-74d30edf-dced-4d3f-b284-f4af5a2849ee.png)

From the above plot we can see that the data is imbalanced we can see that there are more than 250000 customers who pay loan regularly and there are customers less than 25000 who do not pay loan installments regularly.

![image](https://user-images.githubusercontent.com/38136560/224322547-c979b2a0-6962-4e2d-a3f9-6868871811e2.png)

Because the data being imbalanced, from the above we can clearly see that Females most likely to pay loans regularly when compared to the males.

# Models Used and Results:

Through our project we implemented 3 different models in two different ways as explained below.
Initially we decided to build 1. Decision Trees , 2. Random Forest , 3. GBT classification models on our primary file (application_train.csv). Since the data was imbalanced already , we balanced the data by creating weights. Apart from that we also performed logistic regression to check if the models we chose were correct. The results below are the accuracy , precession and recall values for the first file application_train.csv.

![image](https://user-images.githubusercontent.com/38136560/224323269-8b34c92c-4d4d-4424-9a1c-d746d18f2c6e.png)

On the later part, we decided to extend the model building for rest of the files which are previous_application.csv , POS_CASH_balance.csv , credit_card_balance.csv. These 3 files have multiple records for one customer. To use these files as a feature for building the model we must make one record for one customer. We used group by for each customer and used aggregate functions to make one record for each customer. Here we combined all the columns from all the files and balanced the data using weights along with adding an extra feature column and implemented the machine learning models. Here we decided to build 1. Decision Trees , 2. Random Forest , 3. GBT classification models yet again by balancing the data including the weights. The results identified were not as expected and the accuracy of the models was 100% which is not suggestable. So, we tried implementing the models again by removing the weights and perform the models all over again. The results are attached below for the models performed on rest of the files without balancing the data.

![image](https://user-images.githubusercontent.com/38136560/224323418-74f361bb-b560-402d-b955-ca1898a207cd.png)

# References :
1. https://www.kaggle.com/competitions/home-credit-default-risk/data
2. https://towardsdatascience.com/machine-learning-predicting-bank-loan-defaults-d48bffb9aee2
3. https://towardsdatascience.com/loan-default-prediction-for-profit-maximization-45fcd461582b
4. https://medium.datadriveninvestor.com/can-you-predict-customers-loan-default-using-machine-learning-be774489b8f5
5. https://www.kaggle.com/code/emilyjiminroh/eda-home-credit-default-risk-collabo-ver
6. https://stackoverflow.com/questions/35804755/apply-onehotencoder-for-several-categorical-columns-in-sparkmlib
7. https://www.analyticsvidhya.com/blog/2020/10/improve-class-imbalance-class-weights/
8. https://medium.com/@haoyunlai/smote-implementation-in-pyspark-76ec4ffa2f1d
9. https://spark.apache.org/docs/latest/ml-classification-regression.html
10. https://towardsdatascience.com/machine-learning-with-pyspark-and-mllib-solving-a-binary-classification-problem-96396065d2aa
11. https://www.datatrigger.org/post/spark_3_weighted_random_forest/
12. https://www.projectpro.io/recipes/perform-missing-value-imputation-dataframe-pyspark





