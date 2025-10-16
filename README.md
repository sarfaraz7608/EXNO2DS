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
<img width="1038" height="490" alt="Screenshot 2025-10-16 134059" src="https://github.com/user-attachments/assets/d40de263-d524-4848-badc-299c0e5b0cf5" />
```
dt.info()
dt.shape
```
<img width="449" height="357" alt="Screenshot 2025-10-16 134106" src="https://github.com/user-attachments/assets/7bd8f502-0c1a-49a5-b4c4-6b6ce1293789" />
<img width="255" height="92" alt="Screenshot 2025-10-16 134116" src="https://github.com/user-attachments/assets/4320b635-00c1-4d59-9277-a804420c0286" />
```
dt.set_index("PassengerId", inplace=True)
dt.describe()
```
<img width="788" height="311" alt="Screenshot 2025-10-16 134123" src="https://github.com/user-attachments/assets/c4036b13-eba6-432d-8cbd-5f2a8bb0d924" />
```
dt.nunique()
```
<img width="231" height="238" alt="Screenshot 2025-10-16 134132" src="https://github.com/user-attachments/assets/24d0e9ec-881f-415b-8f7e-f4885d79102d" />
```
dt["Survived"].value_counts()
```
<img width="376" height="103" alt="Screenshot 2025-10-16 134140" src="https://github.com/user-attachments/assets/2d69e7b7-7b76-48cf-81b0-66fcd7d4f6e3" />
```
per=(dt["Survived"].value_counts()/dt.shape[0]*100).round(2)
per
```
<img width="354" height="83" alt="Screenshot 2025-10-16 134147" src="https://github.com/user-attachments/assets/6f721e40-a117-4475-94f4-827f8345a3cd" />
```
sns.countplot(data=dt,x="Survived")
```
<img width="698" height="476" alt="Screenshot 2025-10-16 134155" src="https://github.com/user-attachments/assets/7bcd6469-d240-4710-8b9e-ec07f0219347" />
```
dt.Pclass.unique()
```
<img width="186" height="56" alt="Screenshot 2025-10-16 134204" src="https://github.com/user-attachments/assets/d4265b4f-0c23-40de-bab0-331bc1b3dab1" />
```
dt.rename(columns = {'Sex':'Gender'}, inplace = True)
sns.catplot(x="Gender",col="Survived",kind="count",data=dt,height=5,aspect=.7)
```
<img width="818" height="540" alt="Screenshot 2025-10-16 134211" src="https://github.com/user-attachments/assets/0fd8f42c-201f-4e69-bde2-73346a804aa7" />
```
sns.catplot(x="Survived",hue="Gender",data=dt,kind="count")
```
<img width="702" height="553" alt="Screenshot 2025-10-16 134217" src="https://github.com/user-attachments/assets/0da7f4f2-a560-4c99-bbfc-be05a2e9aca8" />
```
dt.boxplot(column="Age",by="Survived")
```
<img width="667" height="513" alt="Screenshot 2025-10-16 134224" src="https://github.com/user-attachments/assets/bc8132aa-3649-4559-905a-3b942a7823e7" />
```
sns.scatterplot(x = dt["Age"], y = dt["Fare"])
```
<img width="675" height="482" alt="Screenshot 2025-10-16 134230" src="https://github.com/user-attachments/assets/cf0c8dc3-4749-4ccc-9431-dd5b46d3b7b5" />
```
sns.jointplot(x="Age",y="Fare",data=dt)
```
<img width="710" height="639" alt="Screenshot 2025-10-16 134245" src="https://github.com/user-attachments/assets/f549693d-b90e-406c-bfe3-3a8d14f36063" />
```
fig, ax1 = plt.subplots(figsize=(8,5))
pt=sns.boxplot(ax=ax1,x="Pclass", y="Age", hue="Gender", data=dt)
```

<img width="774" height="472" alt="Screenshot 2025-10-16 134251" src="https://github.com/user-attachments/assets/64f233c9-ccb7-46a4-8728-46c95c041b3c" />
```
sns.catplot(data=dt,col="Survived",x="Gender", hue="Pclass", kind="count")
```

<img width="1045" height="501" alt="Screenshot 2025-10-16 134300" src="https://github.com/user-attachments/assets/854f48c1-b82f-40b7-b850-06a06d418adc" />
```
corr = dt.corr()
sns.heatmap(corr, annot=True)
```

<img width="581" height="462" alt="Screenshot 2025-10-16 134314" src="https://github.com/user-attachments/assets/f17d8122-f4a6-49e8-9234-b38dbc11e3cb" />
```
sns.pairplot(dt)
```
<img width="1038" height="663" alt="Screenshot 2025-10-16 134332" src="https://github.com/user-attachments/assets/f0dee807-748c-45b1-be6e-5bad9f3e658d" />

# RESULT
Thus the program to perform Exploratory Data Analysis on the given data set is successfully implemented.


       

