![image](https://user-images.githubusercontent.com/91864024/180405365-f5850d6b-45f8-4815-89f0-55054dc29435.png)
# Credit Card Fraud Detection
## I. Outline
- There are several transactions made everyday. Therefore, it is needed to classify and evaluate the validity of each transaction.
- This project aims to detect if a transaction is a fraud or a normal transaction.
## II. Business Objective/ Problem
- Assume that you work in the Data Science department of a local bank. They have a need to expand development and check the transactions are valid or not.
- They want to build a model that predicts whether the transactions that happen every day are valid or not
- This project is built on that request
## III. Project implementation
### 1. Business Understanding
Based on the above description (or after asking specific questions to the business and related subjects) => identify the problem:
- A model that can predict the fraud transaction
- The data can be imbalance, figure out method to deal with such kind of data.
### 2. Data Understanding/ Acquire
- Re: this is a simulated credit card transaction dataset containing legitimate and fraud transactions from the duration 1st Jan 2019 - 31st Dec 2020. 
It covers credit cards of 1000 customers doing transactions with a pool of 800 merchants.
- This was generated using Sparkov Data Generation | Github tool created by Brandon Harris. This simulation was run for the duration - 1 Jan 2019 to 31 Dec 2020. The files were combined and converted into a standard format.
- I do not own the simulator. I used the one used by Brandon Harris and just to understand how it works.
- You can download data here: https://www.kaggle.com/code/janiobachmann/credit-fraud-dealing-with-imbalanced-datasets/data


![image](https://user-images.githubusercontent.com/91864024/180409661-65c569da-4303-4d7a-906d-add75d0e218b.png)

### 3. Build model
**- Understand the dataset:**

![image](https://user-images.githubusercontent.com/91864024/180410114-d94d75a0-8271-4c0d-b7e1-869835dbe80a.png)

- 75% of transactions during the analyzed period € 77.16.
- The maximum amount determined during this period is €25,691.16, much higher than the average amount of €88.35.

![image](https://user-images.githubusercontent.com/91864024/180410437-f5ceff5f-4b77-429e-8562-e1eb6248ea2a.png)

Comments: 99.83% of transactions are normal, while only 0.17% are fraud.

**- Pre-processing data:**

![image](https://user-images.githubusercontent.com/91864024/180410873-940d4477-e727-49fd-99c0-e3e1700c9acf.png)

- There is no missing data
- Apply Standard Scaler for dataset:

![image](https://user-images.githubusercontent.com/91864024/180411459-e66fd4e1-4539-4a2b-afa0-c67e8ea73bac.png)
![image](https://user-images.githubusercontent.com/91864024/180411513-85d04ac3-add4-493c-8b84-8746991ad927.png)

- Split train/ test data:

![image](https://user-images.githubusercontent.com/91864024/180411222-3dc16cf0-e50e-49a2-a73f-3ff6a09df8ac.png)

**- Build model:**
- Apply 2 models: Random Forest, Decision Tree:
![image](https://user-images.githubusercontent.com/91864024/180411714-9278d9d3-d485-4988-aea3-63cf9c6c474c.png)

==> apply Random Forest for better accuracy (you can also use Decision Tree. It can work well with this dataset, too)

**- Evaluate confusion matrix:**

![image](https://user-images.githubusercontent.com/91864024/180412096-e9b9174d-54a0-4940-bc73-3360ed5451ec.png)
![image](https://user-images.githubusercontent.com/91864024/180412155-3b1add93-71b4-4626-9f95-d4bfff94619b.png)

==> Based on the confusion matrix, the Random Forest model has high accuracy. However, only 0.17% of transactions are fraudulent in this dataset. 
To balance the data, we will use SMOTE to rebalance the classes of the data

![image](https://user-images.githubusercontent.com/91864024/180412716-aafb1cc2-ee40-44ee-a2eb-f7da1246ab85.png)

### 4. Oversampling with SMOTE
**- Oversampling:**

![image](https://user-images.githubusercontent.com/91864024/180413088-335cb5cd-4465-4f91-a3aa-8468d04b0044.png)

**- Evaluate confusion matrix:**

![image](https://user-images.githubusercontent.com/91864024/180413137-7a154893-8a9b-4472-953b-163083a94923.png)
![image](https://user-images.githubusercontent.com/91864024/180413196-2d0c701d-539d-43bb-8ec7-3680493a5467.png)

### 5. Conclusion
- After using SMOTE to oversampling, we have:
  - 85,132 True Positives.
  - 17 False Negatives.
  - 0 False Positives.
  - 85,440 True Negatives.

- Besides:
  - Accuracy: 99.99%;
  - Precision: 99.98%;
  - Recall: 100%;
  - F1 Score: 99.99%.

--> model fit to predict fraud.

Thank you for your experience with my project. Hope you enjoy it!









