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

```
# Treating the Experience Columns
cond = df["Experience"] < 0
negative_experience = df[cond]
negative_experience.head()
```
![image](https://github.com/himanshucgithub/Project/assets/112814361/62879db9-ac36-41fa-bd2f-83b335447ec3)

```
negative_experience.count()
```
![image](https://github.com/himanshucgithub/Project/assets/112814361/15c39386-7298-40d2-9df6-c530b70e665c)

```
sns.displot(negative_experience["Age"])
```
![image](https://github.com/himanshucgithub/Project/assets/112814361/89b8af48-d26a-4223-8f5b-c868d10fb448)

```
negative_experience["Experience"].mean()
`-1.4423076923076923`
```

```
negative_experience.size
```
625

```
'There are {} records wich has negative values for experience, approx {} %'.format(negative_experience.size,((negative_experience.size/df.size)*100))
```
There are 64 records which has negative values for experience, approx 1.04 %

```
data = df.copy()
```

```
data.head()
```
![image](https://github.com/himanshucgithub/Project/assets/112814361/36e2d1d5-cb71-4e82-814f-0c57614a6df8)

```
# Handling the Negative data with the help of Numpy**
import numpy as np
```

```
data["Experience"] = np.where(data["Experience"]<0,
                              data["Experience"].mean(),
                              data["Experience"])
```

```
#checking whether the data is assign or not in the data table
cond = data["Experience"] < 0
data[cond]
```
![image](https://github.com/himanshucgithub/Project/assets/112814361/20f25e86-a3b6-4666-85ee-5532a1284dce)
From the above we can see that our negarive data in the column experience has been replace with the mean value, as the above result shows us that there is no negative values present in the column.

```
# Now checking the correlation in the data
data.corr()
```
![image](https://github.com/himanshucgithub/Project/assets/112814361/e4b002cb-ea61-44b1-8e51-f42d8bc6eebc)

```
plt.figure(figsize=(10,10))
sns.heatmap(data.corr(),annot = True)
```
![image](https://github.com/himanshucgithub/Project/assets/112814361/735b71a4-da47-4abe-9b90-7e2d970a07aa)
From the above we can see that the correlation betn the age column and the experience column is more, so we have to delete one of the column depending upon the interest.

```
data.drop(["Experience"],axis=1,inplace=True)
```

```
data.head()
```
![image](https://github.com/himanshucgithub/Project/assets/112814361/2b13091e-4791-4ad8-8dd0-533d52761111)

```
# Now Moving Towards the Education Column :
data["Education"].unique()
```
array([1,2,3])
#### 1 means - under graduate
#### 2 means - Graduate
#### 3 means - Working professional or higher
#### so now converting the above data into the readable format.

```
def experience(x):
  if x==1:
    return "Under Graduate"
  if x == 2:
    return "Graduate"
  if x == 3:
    return "Professional"
```

```
data["EDU"] = data["Education"].apply(experience)
```

```
data.head()
```
![image](https://github.com/himanshucgithub/Project/assets/112814361/f55ff86b-150b-4bb5-ae5d-ac1c1d7125da)

```
data["EDU"].unique()
```
array(['Under Graduate', 'Graduate', 'Professional'], dtype=object)

#### So here we converted the data in the education column which is in the form of 1,2,3 into direct readable column, Now we dont need the Education column in the data table, so we will drop that column.

```
data.drop(["Education"],axis=1, inplace=True)
data.head()
```
![image](https://github.com/himanshucgithub/Project/assets/112814361/0173e611-e1af-4ebe-8434-74f64f869325)

```
education_dist = data.groupby(by="EDU")["Age"].count()
education_dist
```
![image](https://github.com/himanshucgithub/Project/assets/112814361/03e53dc3-e21d-4d56-9157-bf0727fabd60)

```
# plotting pie chart of the above data
ps.pie(data, values = education_dist, names = education_dist.index, title = "Pie Chart")
```
![image](https://github.com/himanshucgithub/Project/assets/112814361/df14d1b0-f628-4203-a61a-5b6b9a699412)

Now lets handle the columns security account and CD account columns.

```
def sec (y) :
  if(y["Securities Account"]==1) &(y["CD Account"]==1):
    return "Hold Securities and Deposit Account"
  if(y["Securities Account"]==0) &(y["CD Account"]==0):
    return "Does Not hold Securities and Deposit Account"
  if(y["Securities Account"]==1) &(y["CD Account"]==0):
    return "Hold Securities account"
  if(y["Securities Account"]==0) &(y["CD Account"]==1):
    return "Hold CD Account"
```

```
data["Account_Holder_Category"] = data.apply(sec,axis=1)
```

```
data.head()
```
![image](https://github.com/himanshucgithub/Project/assets/112814361/33e4592e-9898-4b61-b080-47fa9050c775)

```
values=data["Account_Holder_Category"].value_counts()
```

```
values.index
```
![image](https://github.com/himanshucgithub/Project/assets/112814361/8048b84a-952c-4208-9e5f-f861004f4ecc)

```
# plotting pie chart of the above data
ps.pie (data, values = values,names= values.index, title = "Pie Chart")
```
![image](https://github.com/himanshucgithub/Project/assets/112814361/5f1435a6-138e-42d4-bd46-68f0f8232937)

```
#Saving Data For Further Analysis
data.to_csv("/content/drive/MyDrive/Data Analysis End to End Projects/Bank Personal Loan Modelling/Bank Personal Loan Modelling EDA.csv")
```

## [EDA Performed, Cleaned CSV File](https://github.com/himanshucgithub/Files/blob/main/End%20to%20End%20Projects/Bank%20Personal%20Loan%20Analysis/Bank%20Personal%20Loan%20Modelling%20EDA.csv)

## Questions Asked For Data Analysis :
* How many persons accepted the loans ?
* Whats is the relation between Family Size & number of loan taken ?
* Whats is the relation between Education, income and loan ?
* Whats is the relation between Education, mortage and loan ?
* Whats is the relation between the person who has securities and loan ?
* Whats is the relation between CD account and Loan ?
* Whats is the relation between CCavg and loan ?
* Whats is the relation between average income and loan ?

## Results / Findings :
![image](https://github.com/himanshucgithub/Project/assets/112814361/bfbb5682-f9d9-4cd6-9d4b-c15a9b2188d1)
From the above we can see that the data is having a huge bias(alomot 1:10) towards the category of people not accepting the personal loan. Hence we can build an opinion that our model will tends to perform better towards predicting which customers will not accept the personal loan. However, our goal is to identityfy the customer who can accept the personal loan based on the given features.

![image](https://github.com/himanshucgithub/Project/assets/112814361/ff1cbbd5-addc-4118-bc0b-40d0cb4095f5)
Family size does not have any impact in personal loan. But it seems families with size of 3 and 4 are more likely to take loan.

![image](https://github.com/himanshucgithub/Project/assets/112814361/80a917d1-25dc-4294-994e-8e468f955c8d)
Customers who has securies account are more likly to take loan. Majority of customers who does not have loan do not have securities account.

![image](https://github.com/himanshucgithub/Project/assets/112814361/2c8044da-f9cb-4e6d-afde-235dd9a0f7b7)
From the above we can see that customers whose education level is 1 and did not take loan has higher mortgage than customers who take loan of same education level. Customers whose education level is 2and 3 and did not take loan has lesser mortgage than customers who take loan of same education level.

![image](https://github.com/himanshucgithub/Project/assets/112814361/07ae171f-e3ba-4858-bd62-86589d00036c)
From above we can say that customers with undergraduate level of education and family greater than 3 are good customers who took loan. Customer who took loan have same income range irrespective of education level. Education of Graduate and above have more chance to take loan.

![image](https://github.com/himanshucgithub/Project/assets/112814361/61a0d01a-6a09-4e6f-80fe-1dfbf9603f4d)
Customers who does not have CD account , does not have loan as well. This seems to be majority. But almost all customers who has CD account has loan as well.

![image](https://github.com/himanshucgithub/Project/assets/112814361/deb4325f-bddf-411d-813f-28a201fe234f)
The CCavg is greater of the person who has the loan as compared to the person who has not any loan.

![image](https://github.com/himanshucgithub/Project/assets/112814361/888d9d98-50bd-4afe-b285-9f0d1d1ba83d)
Person who has income more is tend to apply for the loan, compared to the less income. The avg of the income of the person who has loan is greater compared to the person who has not taken loan.



