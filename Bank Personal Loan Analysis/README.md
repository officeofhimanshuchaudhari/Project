# Bank Personal Loan Analysis
![Personal-Loan-1](https://github.com/himanshucgithub/Project/assets/112814361/a0f32c4d-1c91-4ca1-9080-361b367425e5)

## Table of Content :
* Buisness Case
* Final Dashboard
* Data Source and Data Description
* Tools
* Data Cleaning
* Exploratory Data Analysis ( EDA )
* Questions Asked For Data Analysis
* Results / Findings

## Buisness Case :
This case is about the bank (Thera Bank) whose management wants to explore the ways of converting its liability customers to personal loan customer (while retaining them as depositor). A campaign that the bank ran last year for the liability customers showed the healthy conversion rate of over 9% success. This has encouraged the retail marketing department to device campaigns with better target marketing to increase the success ratio with minimum budget.

## Final Dashboard : [Power Bi File](https://github.com/himanshucgithub/Files/blob/main/End%20to%20End%20Projects/Bank%20Personal%20Loan%20Analysis/Bank%20Personal%20Loan%20Analysis.pbix)
![Screenshot 2024-01-02 005551](https://github.com/himanshucgithub/Project/assets/112814361/d1bc87c3-fe64-4f81-a2ba-4a6b62ac5137)

## Data Source and Data Description : [Original Data Set File](https://github.com/himanshucgithub/Files/blob/main/End%20to%20End%20Projects/Bank%20Personal%20Loan%20Analysis/Bank_Personal_Loan_Modelling.csv)
The Data Set is Downloaded from the Kaggle. The file Contain data on the 5000 customers. The data includes demographical information (age, income, etc), the customers relationship with bank (mortage, security, account, etc), and the customer response to the last personal loan campaign ( Personal Loan ). Among this 5000 customers, only 480 (=9.6%) accept the personal loan that was offered to them in the earlier campiagn.

## Tools :
* **Python(Pandas,matplotlib,seaborn)** : For Data cleaning and EDA
* **PowerBi** : For Visualisation purpose

## Data Cleaning / Preparation :
```
# Import the Standard Libarries
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
```

```
# Load the data :
df=pd.read_csv("/content/drive/MyDrive/Data Analysis End to End Projects/Bank Personal Loan Modelling/Original Data Sets/Bank_Personal_Loan_Modelling.csv")
```

```
# Expolore the Data set
df.shape
```
(5000,14)

```
# Explore the Data Sets
df.info()
```

