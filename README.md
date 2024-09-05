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
           REG NO : 212223240146
           NAME : SANDHIYA R
```           
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```

![image](https://github.com/user-attachments/assets/289a572b-c955-4ba2-bbc8-1b06e4c24734)

```
df.shape
```

![image](https://github.com/user-attachments/assets/53cbb768-cdf2-403f-81e7-1305eac79d08)

```
df.describe()
```
![image](https://github.com/user-attachments/assets/2c6ff770-3205-4543-8784-ef9e6bd4a14a)
```
df.info()
```
![image](https://github.com/user-attachments/assets/d16e693c-c13a-4cc3-ab06-0d0d46974611)
```
df.head(10)
```
![image](https://github.com/user-attachments/assets/2f0e7c78-efa9-48bd-ab8d-6e93a3e2295f)
```
df.tail(10)
```
![image](https://github.com/user-attachments/assets/32df16d6-9d71-4b67-84b0-cda65e8df97e)
```
df.isna().sum()
```
![image](https://github.com/user-attachments/assets/87a58356-c997-4d25-9e80-edb55873895e)
```
df.dropna(how='any').shape
```
![image](https://github.com/user-attachments/assets/7edc5e59-e598-4141-ab8f-7d5b11f89a0f)
```
df.shape
```
![image](https://github.com/user-attachments/assets/0bcbbe78-13bd-4260-9b4b-09d917989c58)
```
x=df.dropna(how='any')
x
```
![image](https://github.com/user-attachments/assets/8822756c-68b4-4ed3-a6c7-cd220b3bcbed)
```
mn=df.TOTAL.mean()
mn
```
![image](https://github.com/user-attachments/assets/5531cd62-cf99-4b6a-8580-e58688975d64)
```
df.TOTAL.fillna(mn,inplace=True)
df
```

![image](https://github.com/user-attachments/assets/b6c7c673-5600-4f84-ad28-553009712403)
df.isnull().sum()

![image](https://github.com/user-attachments/assets/a654e0a0-e9dc-4c29-bb6c-ea45f4df6916)
```
df.M1.fillna(method='ffill',inplace=True)
df
```
![image](https://github.com/user-attachments/assets/796f9273-9e9e-4cc3-9b11-cb1fa7974319)
df.isnull().sum()
![image](https://github.com/user-attachments/assets/96263920-3e3d-4211-99dc-3ac4a63e1a3e)
```
df.M2.fillna(method='ffill',inplace=True)
df
```
![image](https://github.com/user-attachments/assets/dcc630a4-61b5-4605-8193-ffa4f84ccf6c)
df.isna().sum()
![image](https://github.com/user-attachments/assets/6eba7a6c-5aba-4340-8092-e7e854da3af2)
```
df.M3.fillna(method='ffill',inplace=True)
df
```
![image](https://github.com/user-attachments/assets/4f8208a1-202b-4072-bee8-a2be1ba031cb)
df.isnull().sum()
![image](https://github.com/user-attachments/assets/ceb87191-ab6d-486d-be70-7b9326885414)
df.duplicated()
![image](https://github.com/user-attachments/assets/f7dc155f-bb23-4c49-b7f4-56a70e753cfd)
```
df.drop_duplicates(inplace=True)
df
```
![image](https://github.com/user-attachments/assets/a013da03-4956-494b-a2f2-8f0e55a60d63)
df.duplicated()
![image](https://github.com/user-attachments/assets/c6374ac7-3ba3-4e1f-9cf5-580214a78f64)
df['DOB']
![image](https://github.com/user-attachments/assets/adf4cde9-9a0c-4b38-9308-f67507e612a5)
```
import seaborn as sns
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
![image](https://github.com/user-attachments/assets/20ece681-3efa-42ae-8ac5-c94e08f2e3a4)
```
df.dropna(inplace=True)
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
![image](https://github.com/user-attachments/assets/4b1d5693-270e-4fd0-be2f-7e72a2f8826f)

0UTLIERS DETECTION AND REMOVAL USING IQR
```
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
df=pd.DataFrame(age)
df
```
![image](https://github.com/user-attachments/assets/3ab7a7c3-3846-43b3-b56f-b09c7280b045)
sns.boxplot(data=df)
![image](https://github.com/user-attachments/assets/a99665d0-3237-4e15-8775-4e8f18f64c98)
sns.scatterplot(data=df)
![image](https://github.com/user-attachments/assets/a6a592b8-8e25-44c9-bdba-15886f12bfec)
```
q1=df.quantile(0.25)
q2=df.quantile(0.5)
q3=df.quantile(0.75)
iqr=q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/f93fb45e-196a-45ad-ba42-93948b08f57f)
```
Q1=np.percentile(df,25)
Q3=np.percentile(df,75)
IQR=Q3-Q1
IQR
```
![image](https://github.com/user-attachments/assets/9530e61b-3bbb-4ab4-a999-a5b4e34a5ff3)
```
lower_bound=Q1-1.5*IQR
upper_bound=Q3+1.5*IQR
lower_bound
```
![image](https://github.com/user-attachments/assets/acfbaa14-fcf9-4dbf-9e71-888f958220c5)
upper_bound
![image](https://github.com/user-attachments/assets/c3c27548-0c16-4c79-a6c4-6b4987ff8467)
```
outliers=[x for x in age if x<lower_bound or x>upper_bound]
print("Q1:",Q1)
print("Q3:",Q3)
print("IQR:",IQR)
print("Lower Bound:",lower_bound)
print("Upper Bound:",upper_bound)
print("Outliers:",outliers)
```
![image](https://github.com/user-attachments/assets/dbfb5164-d2bc-4ca2-a147-026bfb7a7b8c)
```
df=df[((df>=lower_bound)&(df<=upper_bound))]
df
```
![image](https://github.com/user-attachments/assets/99e5beeb-ac6e-455c-8015-8278dcb08e92)
```
df=df.dropna()
df
```
![image](https://github.com/user-attachments/assets/7f33fe52-70d6-4c76-97b7-66973b769702)
sns.boxplot(data=df)
![image](https://github.com/user-attachments/assets/15edf3db-1c8d-4a61-89e1-93d8929563f1)
sns.scatterplot(data=df)
![image](https://github.com/user-attachments/assets/c1c743c4-09db-4a1d-8f40-73e2c7f1b53d)
```
data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]
mean=np.mean(data)
std=np.std(data)
print('mean of the dataset is',mean)
print('std.deviation is',std)
```
![image](https://github.com/user-attachments/assets/ecef6b28-f8f8-4f0e-b6ee-c12d66b7003f)
```
threshold=3
outlier=[]
for i in data:
  z=(i-mean)/std
  if z>threshold:
    outlier.append(i)
print('outlier in dataset is',outlier)
```
![image](https://github.com/user-attachments/assets/fd4bb6e4-d479-48af-aa5d-9c70532e45c6)
```
import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats
data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,
                66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df
```
![image](https://github.com/user-attachments/assets/a9df1855-fd42-4824-97cc-7887428dcbdf)
```
z=np.abs(stats.zscore(df))
print(df[z['weight']>3])
```
![image](https://github.com/user-attachments/assets/406b2906-3d41-44f2-930a-290ca90fa045)

# Result
         Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.

