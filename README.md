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

# Result
The data clearning has beeen done successfully.
