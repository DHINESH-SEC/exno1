<h1 align="center">Ex. 1   Data Cleaning and Outlier Detection & Removal</h1>


## AIM
### To read the given data and perform data cleaning and save the cleaned data to a file.

## Explanation
### Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

## Algorithm
### STEP 1
#### Read the given Data

### STEP 2
#### Get the information about the data

### STEP 3 
#### Remove the null values from the data

### STEP 4
#### Save the Clean data to the file

### STEP 5
#### Remove outliers using IQR

### STEP 6
#### Use zscore of to remove outliers

## Coding and Outputs

<h3 align="center">Data Cleaning</h3>

```py
import pandas as pd
import numpy as np
import seaborn as sns
import os 
df=pd.read_csv("SAMPLEIDS.csv")
df
```
![image](https://github.com/PSriVarshan/exno1/assets/114944059/ed03bbd1-7c97-4cd8-8cf0-3f5f9e14dcc8)

```py
df.isnull().sum()

```

![image](https://github.com/PSriVarshan/exno1/assets/114944059/57d42b69-bd5e-4c22-b8e8-6f2ae3f0404a)



```py
df.isnull().any()
```
![image](https://github.com/PSriVarshan/exno1/assets/114944059/918f392c-8185-4d11-94f3-63785887574c)

```py
df.dropna()
```

![image](https://github.com/PSriVarshan/exno1/assets/114944059/38354c0d-60a4-4c93-a25d-4302bad7ac62)

```py
df.fillna(0)
```

![image](https://github.com/PSriVarshan/exno1/assets/114944059/2b8ac0df-d0c1-46e1-87a4-ff8f930ff3d7)

```py
df.fillna(method = 'ffill')
```

![image](https://github.com/PSriVarshan/exno1/assets/114944059/87b27264-923b-4b0d-904f-106894f0fbcd)

```py

df.fillna(method = 'bfill')
```

![image](https://github.com/PSriVarshan/exno1/assets/114944059/9a0df734-21b5-4b1e-baf0-2c87c82fafd7)

```py
df_dropped = df.dropna()
df_dropped
```

![image](https://github.com/PSriVarshan/exno1/assets/114944059/e7881fae-d374-4f76-bac8-481821e6461e)

```py
df.fillna({'GENDER':'MALE','NAME':'KANISHKAR','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![WhatsApp Image 2024-02-26 at 10 16 32_b866136c](https://github.com/KANISHKAR2607/exno1/assets/118886772/6a2c7ddf-f022-477f-8420-6cca78668e0d)


<hr><hr>

<h3 align="center">IQR(Inter Quartile Range)</h3>

```py
import pandas as pd
```

```py
ir=pd.read_csv('iris.csv')
ir
```
![image](https://github.com/PSriVarshan/exno1/assets/114944059/32840cf3-736d-4c4b-bc8e-2d55ee7e1417)

```py
ir.describe()
```
![image](https://github.com/PSriVarshan/exno1/assets/114944059/e0ce99a8-f7b9-4ccd-9ac8-df82b53f4bc6)

```py
import seaborn as sns
```

```py

sns.boxplot(x='sepal_width',data=ir)
```


![image](https://github.com/PSriVarshan/exno1/assets/114944059/1c9bfcae-a2b3-4573-b204-c2590c8bc9a6)


```py
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```

![image](https://github.com/PSriVarshan/exno1/assets/114944059/05ef4457-91f5-4a19-b413-1d4eea93b0a7)

```py

rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```

![image](https://github.com/PSriVarshan/exno1/assets/114944059/c554ef7e-012c-40f6-8b82-dbe4ae9a20b3)

```py
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/PSriVarshan/exno1/assets/114944059/0a32cc24-1970-41a2-acf7-cb58a6955c01)

```py
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/PSriVarshan/exno1/assets/114944059/19664bc6-f558-48f3-b449-fa6652c4e7ed)

<hr><hr>

<h3 align="center">Z-Score</h3>

```py
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
```
```py
dataset=pd.read_csv("heights.csv")
dataset
```

![image](https://github.com/PSriVarshan/exno1/assets/114944059/080b6095-73da-4bee-a763-08c7a0b81a07)

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

![image](https://github.com/PSriVarshan/exno1/assets/114944059/ffb0b515-5964-4405-9e0b-6d2c986c3308)


```py
low = q1 - 1.5*iqr
low
```

![image](https://github.com/PSriVarshan/exno1/assets/114944059/b68f4b97-1246-4747-9aff-06e058c94f44)

```py
high = q3 + 1.5*iqr
high
```

![image](https://github.com/PSriVarshan/exno1/assets/114944059/da8aa517-c1de-4e43-91d6-ec677f8beaa5)


```py
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/PSriVarshan/exno1/assets/114944059/5444510b-6eb1-4fdd-a65f-02c85bd685d4)


```py
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/PSriVarshan/exno1/assets/114944059/02efcb16-a37a-4313-8111-7396dbd21f2e)

```py
df1 = df[z<3]
df1
```

![image](https://github.com/PSriVarshan/exno1/assets/114944059/fbfd480f-960d-4d51-8695-71718cc8a342)

<hr>

## Result
<br>

### Hence the data was cleaned , outliers were detected and removed.
