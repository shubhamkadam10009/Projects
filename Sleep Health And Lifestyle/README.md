
## Sleep Health and Lifestyle
![pexels-marcus-aurelius-4064174](https://github.com/shubhamkadam10009/Projects/assets/135099215/e90ab103-9a7b-4ccd-863a-49e24aa76eef)

## Table of Content :
* [Data Set Overview]()
* [Final Dashboard]()
* [Data Source]()
* [Tools]()
* [Data Cleaning/Preparation]()
* [Exploratory Data Analysis (EDA)]()
* [Questions Asked For Data Analysis]()
* [Results/Findings]()
* [Conclusion]()

### Data Set Overview :
The Sleep Health and Lifestyle Dataset comprises 400 rows and 13 columns, covering a wide range of variables related to sleep and daily habits. It includes details such as gender, age, occupation, sleep duration, quality of sleep, physical activity level, stress levels, BMI category, blood pressure, heart rate, daily steps, and the presence or absence of sleep disorders.
#
### Final Dashboard : [File PowerBI](https://github.com/shubhamkadam10009/Other/blob/main/End%20to%20End%20Projects/Sleep_health_and_lifestyle/Sleep_Health_and_lifestyle/Sleep_Health_and_Lifestyle.pbix)
![Screenshot (29)](https://github.com/shubhamkadam10009/Projects/assets/135099215/ad7a05ac-d2e3-4aa9-9bdf-e63bd8a70726)
#
### Data Source : [Original Data Set](https://github.com/shubhamkadam10009/Other/blob/main/End%20to%20End%20Projects/Sleep_health_and_lifestyle/Sleep_Health_and_lifestyle/Original_Data_Sets/Sleep_health_and_lifestyle_dataset.csv)
The Data Set is downloaded from the **Kaggle**.
#
### Tools used for the Data Analysis :
* **Excel**
* **Python (Pandas)** : For Data Preparation and cleaning purpose.
* **PowerBi** : For the Visualisation purpose.
#
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
![Screenshot (44)](https://github.com/shubhamkadam10009/Projects/assets/135099215/b63bddf5-74b4-4c0e-8fa0-dae9d09c6c19)
```
# Exploring the Data Set
df.info()
```
![Screenshot (45)](https://github.com/shubhamkadam10009/Projects/assets/135099215/f607fbf3-fac8-457e-8717-bc1d2f21c9e1)
```
# Exploring the Data Set
df.describe()
```
![Screenshot (46)](https://github.com/shubhamkadam10009/Projects/assets/135099215/6a6d4aa4-beca-4023-bb21-5b4e4fb57e98)
```
# Dropping the unnecessary columns
df=df.drop(["Person ID"],axis=1)
df
```
![Screenshot (47)](https://github.com/shubhamkadam10009/Projects/assets/135099215/02321cf8-56dd-47a6-8916-f9ef797a24de)
```
#Checking the Null Values
df.isna().sum()
```
![Screenshot (48)](https://github.com/shubhamkadam10009/Projects/assets/135099215/796774e1-0504-4a18-8f22-d0e7d1b228f2)
**The Data set has not any null values, and we remove the unnecessary columns. Hence our Data Set is ready for the further analysis:**

```
# Saving our Data set for further Analysis
df.to_csv("/content/drive/MyDrive/Data Analysis End to End Projects/Sleep_Health_and_lifestyle/Sleep_Health_and_Lifestyle.csv")
```
### Questions Asked For the Data Analysis :
* Sleep Disorder Percentage.
* Gender Percentage in the Data using a pie chart.
* Distribution of Age using Histogram.
* Determine the Highest occupation in the Data Set.
* Analyze the distriibution of the Sleep duration based on Gender.
* Visualize the average sleep duration across different occupations using a bar chart.
* Explore the relationship betn average sleep duration and BMI category.
* Identify the Dominent occupation within the Male Category.
* Find the Average Heart with the BMI category
### Results / Findings :
[Final Data Analysis Report (PPT)](https://github.com/shubhamkadam10009/Other/blob/main/End%20to%20End%20Projects/Sleep_health_and_lifestyle/Sleep_Health_and_lifestyle/Final%20Analysis%20Report.pptx)
#
![Screenshot (49)](https://github.com/shubhamkadam10009/Projects/assets/135099215/99c13719-25c1-4135-b15f-c602de80ce28)
![Screenshot (50)](https://github.com/shubhamkadam10009/Projects/assets/135099215/54752974-3eb4-477b-932a-94735b414c5a)
![Screenshot (51)](https://github.com/shubhamkadam10009/Projects/assets/135099215/62f76ed3-6bad-4516-88a9-203865541741)
![Screenshot (52)](https://github.com/shubhamkadam10009/Projects/assets/135099215/cd2a2f68-540c-4e0e-a25a-118b26323b02)
![Screenshot (53)](https://github.com/shubhamkadam10009/Projects/assets/135099215/ac45f01d-fe5a-4bdb-aed7-2862b0ef8c1f)
#
### Conclusion :
`This is my another project as a Data Analyst where the data is obtained from the Kaggle. The usual data processing steps are performed, including data cleaning. EDA (Exploratory Data Analysis ) techniques are applied to gain insight from the data, and the questions are formulated based on the analysis. Visualisation such as bar chart, pie chart and other types of chart are created to present the findings.
`
