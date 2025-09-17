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
import numpy as np
import pandas as pd
data=pd.read_csv("SAMPLEIDS.csv")
data
```
<img width="1102" height="844" alt="image" src="https://github.com/user-attachments/assets/c0e08601-05ce-4248-8817-78d4c016dbbf" />

```
data.head(4)
```
<img width="1101" height="213" alt="image" src="https://github.com/user-attachments/assets/e0ddad16-67ff-461f-8b6c-59dc5fa60a90" />

```
data.tail(7)
```
<img width="1055" height="318" alt="image" src="https://github.com/user-attachments/assets/407d193d-e936-45ce-b316-21ed6e6d1a9c" />

```
data.isnull()
```
<img width="999" height="838" alt="image" src="https://github.com/user-attachments/assets/327d8a46-20ea-4f08-932f-e0b72a79d255" />

```
data.notnull()
```
<img width="907" height="854" alt="image" src="https://github.com/user-attachments/assets/12e9638e-1c16-4dd7-8cbf-dc7fe89cdff2" />


```
data.isnull().sum()
```
<img width="343" height="281" alt="image" src="https://github.com/user-attachments/assets/0489dbae-046b-414f-a06e-ebe01443a473" />

```
data.isnull().any()
```
<img width="366" height="280" alt="image" src="https://github.com/user-attachments/assets/6d42d65f-e1ce-45ee-8956-2f14bc216176" />

```
data.dropna(axis=1)
```
<img width="537" height="835" alt="image" src="https://github.com/user-attachments/assets/2f7120e4-6cfc-4401-857c-78ad6f4e7bc9" />

```
data.dropna(axis=0)
```
<img width="1038" height="547" alt="image" src="https://github.com/user-attachments/assets/aa812feb-afb9-46ac-9fe1-06a680773737" />

```
data.fillna(0)
```
<img width="1183" height="840" alt="image" src="https://github.com/user-attachments/assets/30113b40-2d42-421d-8355-b7c9c3ba445b" />

```
data.fillna(method="ffill")
```
<img width="1057" height="842" alt="image" src="https://github.com/user-attachments/assets/5014f2be-3ea5-4e51-bd2f-f8d4ed0002c3" />

```
data.bfill()
```
<img width="1016" height="849" alt="image" src="https://github.com/user-attachments/assets/eca1c234-7932-40f0-ac50-9408f7a218cd" />

```
data.fillna({'REGNO':0, 'NAME':'PRAVEEN'})
```
<img width="1019" height="830" alt="image" src="https://github.com/user-attachments/assets/62ffe84c-2cbf-4e05-a97d-22493bf821cf" />

```
ir=pd.read_csv("iris.csv")
ir
```
<img width="737" height="476" alt="image" src="https://github.com/user-attachments/assets/110eee6b-1745-43b3-ac17-e48cad28a492" />

```
ir.describe()
```
<img width="648" height="357" alt="image" src="https://github.com/user-attachments/assets/712226e2-55c4-47c0-8084-ddaf0348844c" />

```
import seaborn as sns
sns.boxplot(x="sepal_width",data=ir)
```
<img width="888" height="579" alt="image" src="https://github.com/user-attachments/assets/b76ec9cd-c08d-478c-b92f-fb950d5c5d57" />

```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```
<img width="122" height="30" alt="image" src="https://github.com/user-attachments/assets/2a48ca2b-482a-4094-9da3-19730c2cb852" />

```
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```
<img width="438" height="115" alt="image" src="https://github.com/user-attachments/assets/6bf91a60-a0a9-498b-a36c-f9054043a391" />

```
rid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid
```
<img width="901" height="493" alt="image" src="https://github.com/user-attachments/assets/72a2f0ee-2dd3-4ddc-896e-c3db71f4cae8" />

```
rid=ir[((ir.sepal_width>(q1-1.5*iqr))&(ir.sepal_width<(q3+1.5*iqr)))]
rid['sepal_width']
```
<img width="517" height="256" alt="image" src="https://github.com/user-attachments/assets/b01ddccb-4769-4641-99c7-41442af6af27" />

```
import scipy.stats as stats
z=np.abs(stats.zscore(ir.sepal_width))
z
```
<img width="539" height="274" alt="image" src="https://github.com/user-attachments/assets/f2e1b066-61a7-4892-ae00-74803e3b65fc" />

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
