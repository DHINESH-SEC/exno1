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
   
1) Read and display DataFrame
```
  import pandas as pd
  df=pd.read_csv('/content/SAMPLEDS.csv')            
  df
````
2) Display head
```
df.head()
```
3) Display tail
````
df.tail()
````
4) Info of datafram
````
df.info()
````
5) Describe about the dataframe
```
df.describe()
```
6) Describe about the dataframe
```
df.describe()
````
7) Shape of the datafram
```
df.shape
````
8) Checking tha NUll values
```
df.isnull().sum()
```
9) Drop the Null values
```
x=df.dropna(how='any')
x
``
10) Drop the Null values in Total
```
tot=df.dropna(subset=['TOTAL'],how='any')
tot
```
11) FIll the Null values
````
df.fillna(0)
````
12) Finding the mean value
```
mn=df.TOTAL.mean() mn
````
13) Fill Null value with Mean value
   ``` 
df.head()
````
14) Final output

```
for x in df.index:
  if df.loc[x,"AVG"]>100:
    df.drop(x,inplace=True)
df
```
15)Cut and paste portion of image:
```
import cv2
image=cv2.imread('Deepika.jpg',1)
image=cv2.resize(image,(400,400))
tag =image[150:200,110:160]
image[110:160,150:200] = tag
cv2.imshow('partimage1',image)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
Output

1) ![Screenshot 2024-03-18 084949](https://github.com/DHINESH-SEC/exno1/assets/161271714/6dded0b2-6379-4a30-82e4-d40c6f94d737))
2) ![Screenshot 2024-03-18 085212](https://github.com/DHINESH-SEC/exno1/assets/161271714/dfff50fa-35cd-4bb3-b624-966549ae7470)
3) ![Screenshot 2024-03-18 085220](https://github.com/DHINESH-SEC/exno1/assets/161271714/5cb587b1-d185-42cc-bba2-ccbb0cb7668a)
4) ![Screenshot 2024-03-18 085349](https://github.com/DHINESH-SEC/exno1/assets/161271714/d4b26bd5-5d7e-460c-a081-fc9ca34ec84c)
5) ![Screenshot 2024-03-18 085401](https://github.com/DHINESH-SEC/exno1/assets/161271714/0459c7b4-9038-4149-b98d-99e9a8129a5b)
6) ![Screenshot 2024-03-18 085409](https://github.com/DHINESH-SEC/exno1/assets/161271714/aaa4b9de-0c3e-47f4-89dc-a38d1a874d07)
7) ![Screenshot 2024-03-18 085604](https://github.com/DHINESH-SEC/exno1/assets/161271714/a8a93f8a-5e88-4024-a05f-ac6351e3f1e7)
8) ![Screenshot 2024-03-18 085621](https://github.com/DHINESH-SEC/exno1/assets/161271714/f8a61f6e-2f2a-49e6-a62f-e81844ded5a1)
9) ![Screenshot 2024-03-18 085633](https://github.com/DHINESH-SEC/exno1/assets/161271714/fd68ffc0-48de-4f68-81a9-78c1fb268690)
10) ![Screenshot 2024-03-18 085640](https://github.com/DHINESH-SEC/exno1/assets/161271714/a4bd7d7d-d3f9-4e3b-b828-7b4ca2719b2c)
11) ![Screenshot 2024-03-18 085941](https://github.com/DHINESH-SEC/exno1/assets/161271714/6ba5c3ac-5d96-4947-9af8-418d5a0acafc)
12) ![Screenshot 2024-03-18 085950](https://github.com/DHINESH-SEC/exno1/assets/161271714/43505ae7-2cd4-4539-b62d-a2ae179e7984)
13) ![Screenshot 2024-03-18 090004](https://github.com/DHINESH-SEC/exno1/assets/161271714/033c6e95-b5ae-4eb3-af1a-b6e0351d57d4)
14) ![Screenshot 2024-03-18 090017](https://github.com/DHINESH-SEC/exno1/assets/161271714/665707c7-b6e7-4715-a718-7e4942f3361a)
15) ![Screenshot 2024-03-18 090137](https://github.com/DHINESH-SEC/exno1/assets/161271714/c0ca0c9b-01a8-4348-af4e-f802b02f80fc)

# Result
The data clearning has beeen done successfully.


       
