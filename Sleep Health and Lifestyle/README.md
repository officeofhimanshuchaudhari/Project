# Sleep Health and Lifestyle
![Sleep health and lifestyle](https://github.com/himanshucgithub/Project/assets/112814361/cb0c780c-4563-4621-9187-0503370f8fa8)

## Table of content :
* Data Set Overview
* Final Dashboard
* Data Source
* Tools
* Data Cleaning/Preparation
* Exploratory Data Analysis (EDA)
* Questions Asked For Data Analysis
* Results/Findings
* Conclusion

## Data Set Overview :
The Sleep Health and Lifestyle Dataset comprises 400 rows and 13 columns, covering a wide range of variables related to sleep and daily habits. It includes details such as gender, age, occupation, sleep duration, quality of sleep, physical activity level, stress levels, BMI category, blood pressure, heart rate, daily steps, and the presence or absence of sleep disorders.

## Final Dashboard : [File PowerBI](https://github.com/himanshucgithub/Files/blob/main/End%20to%20End%20Projects/Sleep%20Health%20and%20Lifestyle/Sleep_Health_and_Lifestyle/Sleep_Health_and_Lifestyle.pbix)

![Screenshot 2023-12-29 164342](https://github.com/himanshucgithub/Project/assets/112814361/7d8254b1-886a-4c27-bac0-cf1631d7dbc0)

## Data Source : [Original Datase](https://github.com/himanshucgithub/Files/blob/main/End%20to%20End%20Projects/Sleep%20Health%20and%20Lifestyle/Sleep_Health_and_Lifestyle/Original%20Data%20set/Sleep_health_and_lifestyle_dataset.csv)
The Data Set is downloaded from the **Kaggle**


## Tools used for the Data Analysis :
* **Excel**
* **Python (Pandas)** : For Data Preparation and cleaning purpose.
* **PowerBi** : For the Visualisation purpose.
* **PowerPoint** : For presentation purpose.

## Data Cleaning / Preparation :
```
# Import The Standard Libraries
import pandas as pd
import numpy as np
```
```
# Load the Data using pandas read function
df=pd.read_csv("/content/drive/MyDrive/Data Analysis End to End Projects/Sleep_Health_and_lifestyle/Data Sets/Sleep_health_and_lifestyle_dataset.csv")
df.head()
```

![Screenshot 2023-12-29 180756](https://github.com/himanshucgithub/Project/assets/112814361/ca998876-ee30-494e-b4f1-08ed2dac636d)

```
# Exploring the Data Set
df.info()
```

![image](https://github.com/himanshucgithub/Project/assets/112814361/edadbaf8-6322-4469-b933-8693d164f585)

```
# Exploring the Data Set
df.describe()
```

![image](https://github.com/himanshucgithub/Project/assets/112814361/2e8021df-519d-47c2-ae44-7ca8b35aa2c8)

```
# Dropping the unnecessary columns
df=df.drop(["Person ID"],axis=1)
df
```

![image](https://github.com/himanshucgithub/Project/assets/112814361/2639bf7a-a1e6-4656-9cbe-adab47fab0b0)

```
#Checking the Null Values
df.isna().sum()
```

![image](https://github.com/himanshucgithub/Project/assets/112814361/6f4462ab-9795-4c5f-8e6e-ad657cbb53df)

#### The Data set do not have any null values, and we remove the unnecessary columns. Hence our Data Set is ready for the further analysis:

```
# Saving our Data set for further Analysis
df.to_csv("/content/drive/MyDrive/Data Analysis End to End Projects/Sleep_Health_and_lifestyle/Sleep_Health_and_Lifestyle.csv")
```

## Questions Asked For the Data Analysis :
* Sleep Disorder Percentage.
* Gender Percentage in the Data using a pie chart.
* Distribution of Age using Histogram.
* Determine the Highest occupation in the Data Set.
* Analyze the distriibution of the Sleep duration based on Gender.
* Visualize the average sleep duration across different occupations using a bar chart.
* Explore the relationship betn average sleep duration and BMI category.
* Identify the Dominent occupation within the Male Category.
* Find the Average Heart with the BMI category.

## Results / Findings :
### [Final Data Analysis Report (ppt)](https://github.com/himanshucgithub/Files/blob/main/End%20to%20End%20Projects/Sleep%20Health%20and%20Lifestyle/Sleep_Health_and_Lifestyle/Final%20Analysis%20Report.pptx)

![Screenshot 2023-12-30 134552](https://github.com/himanshucgithub/Project/assets/112814361/f52f9fd2-7b4e-4069-81d4-360dfa51ad42)

![Screenshot 2023-12-30 134852](https://github.com/himanshucgithub/Project/assets/112814361/bf107f50-aaae-4176-b279-3e0760363c08)

![Screenshot 2023-12-30 135048](https://github.com/himanshucgithub/Project/assets/112814361/06294fb2-d231-4719-9b08-e0095bc35bae)

![Screenshot 2023-12-30 135330](https://github.com/himanshucgithub/Project/assets/112814361/0fdeacce-6557-41f9-a8c0-3059236d50a7)

![Screenshot 2023-12-30 135643](https://github.com/himanshucgithub/Project/assets/112814361/2064883b-ce3b-4377-a75a-55e5aa033a2e)
