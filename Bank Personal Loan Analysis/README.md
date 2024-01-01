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
![Screenshot 2024-01-02 010645](https://github.com/himanshucgithub/Project/assets/112814361/fcb47ba9-bccf-4e25-9046-dc8095f6a182)

```
# Explore the data
df.isnull().sum()
```
![Screenshot 2024-01-02 010914](https://github.com/himanshucgithub/Project/assets/112814361/12a7d9d4-3d1f-4c74-a7c9-a7d96b9c7580)
### There is no null value in the data sets, so no need of null value treatment.

```
# Explore the data Set
df.describe()
```
![image](https://github.com/himanshucgithub/Project/assets/112814361/d508e1a7-1418-4666-8fe3-f2c3bb7d310b)

```
# Dropping the unnecessary columns :
df.drop(["ID","ZIP Code"],axis=1,inplace=True)
```

```
df.head(1)
```
![image](https://github.com/himanshucgithub/Project/assets/112814361/637f8af9-827f-4d24-b8d7-ecb2bde1e9b5)

```
# 5 Number Summary
import plotly.express as ps
```

```
fig= ps.box(df,y = ["Age",'Experience','Income','Family','Education'])
fig.show()
```
![image](https://github.com/himanshucgithub/Project/assets/112814361/c55f2378-2e00-495e-b89e-6917132f0ded)

From the above data we can see that some values in the Experience column are having negative values an some outliers in the income columns we need to handle them.

```
#checking the types of data
df.dtypes
```
![image](https://github.com/himanshucgithub/Project/assets/112814361/bbc55abb-1cf5-46b0-9922-a63a7b5a22f4)

```
df.skew()
```
![image](https://github.com/himanshucgithub/Project/assets/112814361/267379ed-3c5c-4fb9-8921-f25dab0ab159)

```
# Performing the EDA
df.hist(figsize=(20,20))
```
![image](https://github.com/himanshucgithub/Project/assets/112814361/93fc2935-2cc7-410f-b2db-5a766afa47dd)

![image](https://github.com/himanshucgithub/Project/assets/112814361/89e39f30-48d6-440e-87d8-c0f8387907a1)

```
#Performing EDA
sns.displot(df['Experience'])
```
![image](https://github.com/himanshucgithub/Project/assets/112814361/720808fc-49ee-4113-96f6-72c44c39a559)

```
 # Treating the Experience Columns :
 df["Experience"].mean()
```
20.145
