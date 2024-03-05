# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
import pandas as pd
df=pd.read_csv('/content/SAMPLEIDS.csv')
df
df.head()
df.tail()
```
![Screenshot 2024-02-23 155627](https://github.com/LINGARAJA-L/exno1/assets/129825857/50f59bc4-854d-44ed-a5a7-58e2db4ed670)

```
df.info()
```
![Screenshot 2024-02-23 155627](https://github.com/LINGARAJA-L/exno1/assets/129825857/c1652bc4-1221-43d7-9b43-caa041e9e504)

```
df.describe()
```
![Screenshot 2024-02-23 155639](https://github.com/LINGARAJA-L/exno1/assets/129825857/06daaaa1-c30f-4862-b074-d382efa80330)

```
df.shape
```
![Screenshot 2024-02-23 155639](https://github.com/LINGARAJA-L/exno1/assets/129825857/3e10b016-b53b-42cc-8760-8dc37ce380a0)

```
df.isnull().sum()
```
![Screenshot 2024-02-23 155639](https://github.com/LINGARAJA-L/exno1/assets/129825857/fdd16109-48a7-43ca-9f24-0d33c7f1dd7f)

```
x=df.dropna(how='any')
x
```
![Screenshot 2024-02-23 155648](https://github.com/LINGARAJA-L/exno1/assets/129825857/d08986ef-512d-41db-96ea-3b361d394462)

```
tot=df.dropna(subset=['TOTAL'],how='any')
tot
```
![Screenshot 2024-02-23 155655](https://github.com/LINGARAJA-L/exno1/assets/129825857/0bab79c0-b06d-4fee-be85-62ecf39d9e30)

```
df.fillna(0)
```
![Screenshot 2024-02-23 155709](https://github.com/LINGARAJA-L/exno1/assets/129825857/5dd90d31-5c22-4859-ba11-265eaa09bbb8)

```
mn=df.TOTAL.mean()
mn
```
![Screenshot 2024-02-23 155715](https://github.com/LINGARAJA-L/exno1/assets/129825857/f54a9796-7190-4ffa-9fba-ea52b144277d)

```
df.TOTAL.fillna(mn,inplace=True)
for x in df.index:
  if df.loc[x,"AVG"]>100:
    df.drop(x,inplace=True)
df
```
![Screenshot 2024-02-23 155715](https://github.com/LINGARAJA-L/exno1/assets/129825857/ebeda40e-32f2-450d-a2fb-e4c2d1103d04)

# Outlier Detection and Removal 
## Coding and Output
```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
data = pd.read_csv("/content/SAMPLEIDS.csv")
data.head()
```
![image](https://github.com/Yamunaasri/exno1/assets/115707860/2e6f57eb-a0eb-46c0-80b6-78ef2ff9c3b4)

```py
data = pd.get_dummies(data)
data.isnull().sum()
```
![image](https://github.com/Yamunaasri/exno1/assets/115707860/b11b71a8-0335-4acf-8e69-555a75bacf24)
```py
columns_with_null = data.columns[data.isnull().any()]
import seaborn as sns
plt.figure(figsize=(10,10))
sns.barplot(columns_with_null)
plt.title("NULL VALUES")
plt.show()
```
![image](https://github.com/Yamunaasri/exno1/assets/115707860/deddaf55-87f4-42dc-b4ce-280775cc04b5)
```py
for column in columns_with_null:
    median = data[column].median()  
    data[column].fillna(median, inplace=True)
data.isnull().sum().sum()
```
![image](https://github.com/Yamunaasri/exno1/assets/115707860/5636ffde-4bb3-4f4b-979f-f81fe1ee00bd)

## IQR
```py
import pandas as pd
import seaborn as sns
ir = pd.read_csv("/content/iris (1).csv")
ir.head()
```
![image](https://github.com/Yamunaasri/exno1/assets/115707860/93d4d44c-8a8e-42ba-b50e-0d427a929e41)
```py
ir.describe()
```
![image](https://github.com/Yamunaasri/exno1/assets/115707860/82718575-7497-43ea-b6b0-0c048b061dd6)
```py
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/Yamunaasri/exno1/assets/115707860/2a264b0b-1be7-4cb5-993a-edfb54c7369d)
```py
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/Yamunaasri/exno1/assets/115707860/ec87fae6-5baa-4b0a-9c09-1c4e1c893ad8)
```py
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/Yamunaasri/exno1/assets/115707860/a6e1a0ff-84f2-47ae-a39a-f8037875611e)
```py
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/Yamunaasri/exno1/assets/115707860/8becd206-ddc7-4a58-85fc-b9cb1b63a53f)
```py
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/Yamunaasri/exno1/assets/115707860/53b3e4cc-9961-4b92-af15-afa9dca57f97)

## Z SCORE
```py
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset
```
![image](https://github.com/Yamunaasri/exno1/assets/115707860/65296f84-d620-42a2-91e9-825f3313e72c)
```py
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```
```py
iqr = q3-q1
iqr
```
![image](https://github.com/Yamunaasri/exno1/assets/115707860/b9d6b692-7f29-4303-8e22-335186cf6ae3)
```py
low = q1 - 1.5*iqr
low
```
![image](https://github.com/Yamunaasri/exno1/assets/115707860/3f341bea-42c2-4cbd-928a-9e1fa576cfaf)
```py
high = q3 + 1.5*iqr
high
```
![image](https://github.com/Yamunaasri/exno1/assets/115707860/ae80602f-3344-443c-a723-d5cef7928731)
```py
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/Yamunaasri/exno1/assets/115707860/3e5ce1e1-567e-4253-82bb-192c04024d35)
```py
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/Yamunaasri/exno1/assets/115707860/ef207f0d-fcc0-452e-bbd3-5f3c48a03515)

# Result
The data clearning has beeen done successfully.
