## Bank Personal Loan Analysis 
#
![pexels-nappy-935979](https://github.com/shubhamkadam10009/Projects/assets/135099215/e86e0ed8-0421-493c-b36d-a8720b2aff2e)

### Table of Content :
* [Buisness Case]()
* [Final Dashboard]()
* [Data Source and Data Description]()
* [Tools]()
* [Data Cleaning]()
* [Exploratory Data Analysis ( EDA )]()
* [Questions Asked For Data Analysis]()
* [Results / Findings]()
#
## Buisness Case :
` This case is about the bank ( Thera Bank ) whose management wants to explore the ways of converting its liability customers to personal loan customer(while retaining them as depositor). A campaign that the bank ran last year for the liability customers showed the healthy conversion rate of over 9% success. This has encouraged the retail marketing department to device campaigns with better target marketing to increase the success ratio with minimum budget.`
#
## Final Dashboard : [PowerBi File](https://github.com/shubhamkadam10009/Other/blob/main/End%20to%20End%20Projects/Bank%20Personal%20Loan%20Modelling/Data%20Set/Bank%20Personal%20Loan%20Analysis.pbix)
![Screenshot (93)](https://github.com/shubhamkadam10009/Projects/assets/135099215/e6445e7c-0bbf-423a-8ed4-f953c7a239ed)

#
## Data Source and Data Description : [Original Data Set File](https://github.com/shubhamkadam10009/Other/blob/main/End%20to%20End%20Projects/Bank%20Personal%20Loan%20Modelling/Data%20Set/Bank_Personal_Loan_Modelling.csv)
The Data Set is Downloaded from the **Kaggle**.
The file Contain data on the 5000 customers. The data includes demographical information (age, income, etc), the customers relationship with bank (mortage, security, account, etc), and the customer response to the last personal loan campaign ( Personal Loan ). Among this 5000 customers, only 480 (=9.6%) accept the personal loan that was offered to them in the earlier campiagn
#
## Tools :
* **Python(Pandas,matplotlib,seaborn)** : For Data cleaning and EDA 
* **PowerBi** : For Visualisation purpose
#
## Data Cleaning / Preparation :
```
# Import the Standar Libarries
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
`( 5000,14)`
```
# Explore the Data Sets
df.info()
```
![Screenshot (54)](https://github.com/shubhamkadam10009/Projects/assets/135099215/04a03797-58f8-42d9-bbe0-901e3d4b111f)
```
# Explore the data
df.isnull().sum()
```
![Screenshot (55)](https://github.com/shubhamkadam10009/Projects/assets/135099215/a2041981-7a1e-4f92-9473-cf36abec5f3b)
```
# Explore the data Set
df.describe()
```
![Screenshot (56)](https://github.com/shubhamkadam10009/Projects/assets/135099215/7a021104-8730-4093-8a42-7146f57a9de2)
```
# Dropping the unnecessary columns :
df.drop(["ID","ZIP Code"],axis=1,inplace=True)
```
```
df.head(1)
```
![Screenshot (57)](https://github.com/shubhamkadam10009/Projects/assets/135099215/894b6a34-c657-4b8b-8cc2-9bee490fe779)
```
# 5 Number Summary
import plotly.express as ps
```
```
fig= ps.box(df,y = ["Age",'Experience','Income','Family','Education'])
fig.show()
```
![Screenshot (58)](https://github.com/shubhamkadam10009/Projects/assets/135099215/4dbb9f33-9f5e-4790-b575-095b5151f9e6)
`From the above data we cans see that some values in the Experience columns are having negative Values an some outliers in the income columns we need to handle them`
```
#checking the types of data
df.dtypes
```
![Screenshot (59)](https://github.com/shubhamkadam10009/Projects/assets/135099215/1f83719c-af8d-4917-9649-c3a393c640a1)
```
df.skew()
```
![Screenshot (60)](https://github.com/shubhamkadam10009/Projects/assets/135099215/e056f1f7-121b-48e5-8978-6a23db882d6c)
```
# Performing the EDA
df.hist(figsize=(20,20))
```
![Screenshot (61)](https://github.com/shubhamkadam10009/Projects/assets/135099215/b28b5ad1-cbf7-4bba-8865-4fc0d8a073ee)
![Screenshot (62)](https://github.com/shubhamkadam10009/Projects/assets/135099215/4ba78401-ea79-46ae-ab85-233386d82774)
```
#Performing EDA
sns.displot(df['Experience'])
```
![Screenshot (63)](https://github.com/shubhamkadam10009/Projects/assets/135099215/8f496c71-9356-4ae9-b24d-8267a20e962c)
```
 # Treating the Experience Columns :
 df["Experience"].mean()
```
`20.1045`
```
# Treating the Experience Columns
cond = df["Experience"] < 0
negative_experience = df[cond]
negative_experience.head()
```
![Screenshot (64)](https://github.com/shubhamkadam10009/Projects/assets/135099215/268e1027-dcc2-49a7-bc6f-8c2ec01912a2)
```
negative_experience.count()
```
![Screenshot (65)](https://github.com/shubhamkadam10009/Projects/assets/135099215/07760f15-97ff-47bc-8b3d-cf17a3a29968)
```
sns.displot(negative_experience["Age"])
```
![Screenshot (66)](https://github.com/shubhamkadam10009/Projects/assets/135099215/ce4ced85-568a-4b57-9970-7573084a5882)
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
There are 624 records wich has negative values for experience, approx 1.04 %
```
data =df.copy()
```
```
data.head()
```
![Screenshot (67)](https://github.com/shubhamkadam10009/Projects/assets/135099215/529cb4c3-fe4e-4ea3-a392-9d01aeca075c)

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
![Screenshot (68)](https://github.com/shubhamkadam10009/Projects/assets/135099215/061765b9-1dc8-447b-92b3-2dca4a6a6a80)
```
# Now checking the correlation in the data
data.corr()
```
![Screenshot (69)](https://github.com/shubhamkadam10009/Projects/assets/135099215/3db9847d-a7c2-4ee5-bf74-22568b252abe)
```
plt.figure(figsize=(10,10))
sns.heatmap(data.corr(),annot = True)
```
![Screenshot (70)](https://github.com/shubhamkadam10009/Projects/assets/135099215/e0b5f536-f1e9-402f-b114-0fe5b12cf1b9)
`From the above we can see that the correlation betn the age column and the experience column is more, so we have to delete one of the column depending upon the interest`
```
data.drop(["Experience"],axis=1,inplace=True)
```
```
data.head()
```
![Screenshot (71)](https://github.com/shubhamkadam10009/Projects/assets/135099215/c83fa6f2-3f38-45b7-b454-a41264e8c255)
```
# Now Moving Towards the Education Column :
data["Education"].unique()
```
`array([1,2,3])`
`
#### 1 means - under graduate
#### 2 means - Graduate
#### 3 means - Working professional or higher
#### so now converting the above data into the readable format`
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
![Screenshot (72)](https://github.com/shubhamkadam10009/Projects/assets/135099215/1bef8609-c768-4873-b6f9-6914f1018bb8)
```
data["EDU"].unique()
```
`array(['Under Graduate', 'Graduate', 'Professional'], dtype=object)`
`# So here we converted the data in the education column which is in the form of 1,2,3 into direct readable column, Now we dont need the Education column in the data table, so we will drop that column`
```
data.drop(["Education"],axis=1, inplace=True)
data.head()
```
![Screenshot (73)](https://github.com/shubhamkadam10009/Projects/assets/135099215/3a48a536-a83c-4cdf-b30d-8d0664fdf9ce)
```
education_dist = data.groupby(by="EDU")["Age"].count()
education_dist
```
![Screenshot (74)](https://github.com/shubhamkadam10009/Projects/assets/135099215/dd0d9b59-26a3-44fd-8653-48122ded99b5)
![Screenshot (75)](https://github.com/shubhamkadam10009/Projects/assets/135099215/c8b2cd00-c502-4980-9290-69f60fd89a5d)
`# Now let us handle the columns security account and CD account columns`
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
![Screenshot (76)](https://github.com/shubhamkadam10009/Projects/assets/135099215/567d7cab-0e7d-4267-b1f2-7bdfe43ea11a)
```
values=data["Account_Holder_Category"].value_counts()
```
```
values.index
```
![Screenshot (77)](https://github.com/shubhamkadam10009/Projects/assets/135099215/589f9166-50ba-490b-b4fb-319540322035)
```
# plotting pie chart of the above data
ps.pie (data, values = values,names= values.index, title = "Pie Chart")
```
![Screenshot (78)](https://github.com/shubhamkadam10009/Projects/assets/135099215/fbc1e2ac-3afa-4c00-b043-d28154bdbdca)
```
#Saving Data For Further Analysis
data.to_csv("/content/drive/MyDrive/Data Analysis End to End Projects/Bank Personal Loan Modelling/Bank Personal Loan Modelling EDA.csv")
```
[EDA Performed, Cleaned CSV File](https://github.com/shubhamkadam10009/Other/blob/main/End%20to%20End%20Projects/Bank%20Personal%20Loan%20Modelling/Data%20Set/Bank%20Personal%20Loan%20Modelling%20EDA.csv) 
#
## Questions Asked For Data Analysis :
* How many persons accepted the loans ?
* Whats is the relation between Family Size & number of loan taken ?
* Whats is the relation between Education, income and loan ?
* Whats is the relation between Education, mortage and loan ?
* Whats is the relation between the person who has securities and loan ?
* Whats is the relation between CD account and Loan ?
* Whats is the relation between CCavg and loan ?
* Whats is the relation between average income and loan ?
#
## Results / Findings :
#
![Screenshot (85)](https://github.com/shubhamkadam10009/Projects/assets/135099215/6d94eac9-04c1-4af0-b6f1-dd5b959dd341)
`From the above we can see that the data is having a huge bias(alomot 1:10) towards the category of people not accepting the personal loan. Hence we can build an opinion that our model will tends to perform better towards predicting which customers will not accept the personal loan. However, our goal is to identityfy the customer who can accept the personal loan based on the given features.`
![Screenshot (86)](https://github.com/shubhamkadam10009/Projects/assets/135099215/59ee7ecb-60b1-4b68-8d92-479769cc820c)
` Family size does not have any impact in personal loan. But it seems families with size of 3 and 4 are more likely to take loan.`
![Screenshot (87)](https://github.com/shubhamkadam10009/Projects/assets/135099215/b4cf5381-f674-42ab-93cd-db0356190b6a)
`Customers who has securies account are more likly to take loan. Majority of customers who does not have loan do not have securities account.`
![Screenshot (88)](https://github.com/shubhamkadam10009/Projects/assets/135099215/d3b0cfd9-ba39-4457-b486-22ffd44e1ef5)
`From the above we can see that customers whose education level is 1 and did not take loan has higher mortgage than customers who take loan of same education level. Customers whose education level is 2and 3 and did not take loan has lesser mortgage than customers who take loan of same education level`
![Screenshot (89)](https://github.com/shubhamkadam10009/Projects/assets/135099215/513a544c-d9d7-4d85-a5e2-47a7364fc0e9)
`From above we can say that customers with undergraduate level of education and family greater than 3 are good customers who took loan. Customer who took loan have same income range irrespective of education level. Education of Graduate and above have more chance to take loan.`
![Screenshot (90)](https://github.com/shubhamkadam10009/Projects/assets/135099215/43c8c905-fbf1-424b-b1d5-7e5c20ef6710)
`Customers who does not have CD account , does not have loan as well. This seems to be majority. But almost all customers who has CD account has loan as well`
![Screenshot (91)](https://github.com/shubhamkadam10009/Projects/assets/135099215/cb608217-10b0-4c61-a38b-2a3f6bd95621)
` The CCavg is greater of the person who has the loan as compared to the person who has not any loan`
![Screenshot (92)](https://github.com/shubhamkadam10009/Projects/assets/135099215/dde8d5b5-d781-44d0-8a87-9c51a06bb6dd)
`Person who has income more is tend to apply for the loan, compared to the less income. The avg of the income of the person who has loan is greater compared to the person who has not taken loan.`




