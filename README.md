# EXNO2DS
# AIM:
      To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
```
Developed by : SARFARAZ I
Reg No: 25015425
```
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
dt=pd.read_csv("titanic_dataset.csv")
dt
```
![image](https://github.com/Prasannalakshmiganesan/EXNO2DS/assets/118610231/01f08c40-c195-4fb2-bf92-3d46e023575b)

```
dt.info()
dt.shape
```
![image](https://github.com/Prasannalakshmiganesan/EXNO2DS/assets/118610231/1472e92f-77d9-4385-9066-3467b517e7d3)

![image](https://github.com/Prasannalakshmiganesan/EXNO2DS/assets/118610231/90bed7b7-7f76-4473-88e5-6ee1cc3e188a)

```
dt.set_index("PassengerId", inplace=True)
dt.describe()
```
![image](https://github.com/Prasannalakshmiganesan/EXNO2DS/assets/118610231/906a2c32-39db-444b-9a5e-d71e60b1af60)

```
dt.nunique()
```
![image](https://github.com/Prasannalakshmiganesan/EXNO2DS/assets/118610231/82b53011-e841-4dc9-95a1-193254524757)

```
dt["Survived"].value_counts()
```
![image](https://github.com/Prasannalakshmiganesan/EXNO2DS/assets/118610231/51ac7a10-f9cb-4844-979a-469bc349c27f)

```
per=(dt["Survived"].value_counts()/dt.shape[0]*100).round(2)
per
```
![image](https://github.com/Prasannalakshmiganesan/EXNO2DS/assets/118610231/e9b2dc7f-37b3-45d9-9585-a0c89312ba9c)

```
sns.countplot(data=dt,x="Survived")
```
![image](https://github.com/Prasannalakshmiganesan/EXNO2DS/assets/118610231/682f3f02-7064-4a0b-8336-57ecb653c491)

```
dt.Pclass.unique()
```
![image](https://github.com/Prasannalakshmiganesan/EXNO2DS/assets/118610231/e7f7be06-d6c4-4932-9e54-f3a361faade0)

```
dt.rename(columns = {'Sex':'Gender'}, inplace = True)
sns.catplot(x="Gender",col="Survived",kind="count",data=dt,height=5,aspect=.7)
```
![image](https://github.com/Prasannalakshmiganesan/EXNO2DS/assets/118610231/6ff622d4-7cbf-4400-9258-800f2efbcc36)

```
sns.catplot(x="Survived",hue="Gender",data=dt,kind="count")
```
![image](https://github.com/Prasannalakshmiganesan/EXNO2DS/assets/118610231/a7335070-4fc2-4445-82f6-6fddf96c7501)

```
dt.boxplot(column="Age",by="Survived")
```
![image](https://github.com/Prasannalakshmiganesan/EXNO2DS/assets/118610231/3010c0c5-6c68-4c32-a826-dbab55be7d8f)

```
sns.scatterplot(x = dt["Age"], y = dt["Fare"])
```
![image](https://github.com/Prasannalakshmiganesan/EXNO2DS/assets/118610231/6c85ab3b-474b-4bb5-8790-7923d626907e)

```
sns.jointplot(x="Age",y="Fare",data=dt)
```
![image](https://github.com/Prasannalakshmiganesan/EXNO2DS/assets/118610231/bdf9945c-f490-434e-bc44-7c0a815393f4)

```
fig, ax1 = plt.subplots(figsize=(8,5))
pt=sns.boxplot(ax=ax1,x="Pclass", y="Age", hue="Gender", data=dt)
```
![image](https://github.com/Prasannalakshmiganesan/EXNO2DS/assets/118610231/22e43b91-4d86-435d-9b61-0f67930907e6)

```
sns.catplot(data=dt,col="Survived",x="Gender", hue="Pclass", kind="count")
```
![image](https://github.com/Prasannalakshmiganesan/EXNO2DS/assets/118610231/fb2fa4da-4a98-4e3f-a534-ba7ed2d113d1)

```
corr = dt.corr()
sns.heatmap(corr, annot=True)
```
![image](https://github.com/Prasannalakshmiganesan/EXNO2DS/assets/118610231/ff2b5c11-ad3d-448f-aa2c-b1001ec84cf6)

```
sns.pairplot(dt)
```
![image](https://github.com/Prasannalakshmiganesan/EXNO2DS/assets/118610231/226265ac-0aff-490a-be49-4a73defe9f77)
# RESULT
Thus the program to perform Exploratory Data Analysis on the given data set is successfully implemented.


       

