# Ex-01_DS_Data_Cleansing


## AIM
To read the given data and perform data cleaning and save the cleaned data to a file. 

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. 
Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information. 

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Get the information about the data
### STEP 3
Remove the null values from the data
### STEP 4
Save the Clean data to the file

# CODE and OUTPUT

Data Cleaning
```
import pandas as pd
df = pd.read_csv("SAMPLEIDS.csv")
df
```
![Screenshot 2025-03-13 105845](https://github.com/user-attachments/assets/c33c2825-1a60-47ea-95b2-3f08fbb91ad5)
```
df.isnull().sum()

```
![Screenshot 2025-03-13 105857](https://github.com/user-attachments/assets/7cc4675f-ed41-47a8-a177-0dfcf8325b08)

```
df.isnull().any()
```
![Screenshot 2025-03-13 105905](https://github.com/user-attachments/assets/f4a92d1e-3f64-4b0a-829c-44bd54a28624)

```
 df.dropna()
```
![Screenshot 2025-03-13 105911](https://github.com/user-attachments/assets/9ebd71ad-9b78-4ff1-8f91-4de506af3b15)

```
 df.fillna(0)
```
![Screenshot 2025-03-13 105918](https://github.com/user-attachments/assets/4a336d0f-9473-43e9-8256-55fbe99e5010)

```
df.fillna(method = 'ffill')
```

![Screenshot 2025-03-13 105926](https://github.com/user-attachments/assets/53383dce-42dd-4f1b-baea-0791441f9f86)

```
 df.fillna(method = 'bfill')
```
![Screenshot 2025-03-13 105933](https://github.com/user-attachments/assets/e2dae73f-d5a1-4226-b7cb-c660a14a2926)

```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![Screenshot 2025-03-13 105940](https://github.com/user-attachments/assets/0c3cd08b-3e00-4c45-b7ff-78d9df00593b)



 IQR(Inter Quartile Range)
 

```
 ir=pd.read_csv('iris.csv')
 ir
```
![Screenshot 2025-03-13 105947](https://github.com/user-attachments/assets/8639af01-0f3a-4ee4-b2ca-bf1c5df6e14c)

```
ir.info()
```
![Screenshot 2025-03-13 105955](https://github.com/user-attachments/assets/63727d51-40b4-4364-8f61-a71dc981ed00)

```
ir.describe()
```
![Screenshot 2025-03-13 110002](https://github.com/user-attachments/assets/6e562f5a-5ec3-4954-a5ef-5b512a40311d)

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![Screenshot 2025-03-13 110008](https://github.com/user-attachments/assets/9e80435a-f72b-4738-952b-2e590f271d9e)

```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```
![Screenshot 2025-03-13 110013](https://github.com/user-attachments/assets/d06304c8-6c9e-4171-8ea1-7811f1d5b344)

```
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```
![Screenshot 2025-03-13 110020](https://github.com/user-attachments/assets/dc52b4a7-a2df-4ddb-a6c7-41d1550d20fb)

```
delid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
delid
```
![Screenshot 2025-03-13 110027](https://github.com/user-attachments/assets/c7a17e54-3a8a-4634-8a3c-8a330f9cc9cf)

```
 sns.boxplot(x='sepal_width',data=delid)
```
![Screenshot 2025-03-13 110035](https://github.com/user-attachments/assets/2f3597a2-bda8-49d2-8738-83127eb85f10)


 Z-Score

```
import matplotlib.pyplot as plt
 import pandas as pd
 import numpy as np
 import scipy.stats as stats
 dataset=pd.read_csv("heights.csv")
 dataset
```

![Screenshot 2025-03-13 110042](https://github.com/user-attachments/assets/4fe032a9-ac48-4088-8860-188fac77160b)

```
 df = pd.read_csv("heights.csv")
 q1 = df['height'].quantile(0.25)
 q2 = df['height'].quantile(0.5)
 q3 = df['height'].quantile(0.75)
 iqr = q3-q1
 iqr
```
![Screenshot 2025-03-13 110048](https://github.com/user-attachments/assets/5a3e66a7-6bb3-4b4d-b227-426ed891869d)


```
low = q1- 1.5*iqr
low
```
![Screenshot 2025-03-13 110055](https://github.com/user-attachments/assets/dad21533-622a-4425-84e1-db8ea625d78d)

```
 high = q3 + 1.5*iqr
 high
```
![Screenshot 2025-03-13 110100](https://github.com/user-attachments/assets/800f23c9-468a-4922-af09-360757248d65)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
````
![Screenshot 2025-03-13 110106](https://github.com/user-attachments/assets/02d0ebc2-9e9c-4133-8460-2150f58001d7)

```
z = np.abs(stats.zscore(df['height'])) 
z
```
![Screenshot 2025-03-13 110137](https://github.com/user-attachments/assets/2d180ccd-a03e-4ca5-a226-5e62ccb82694)

```
df1 = df[z<3]
df1
```
![Screenshot 2025-03-13 110153](https://github.com/user-attachments/assets/0ec9c343-04db-4e77-a253-ac208d10337f)


### Result

Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
