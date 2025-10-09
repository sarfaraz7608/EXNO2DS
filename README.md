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
import pandas as pd
import numpy as np
from scipy import stats

# STEP 1: Show basic dataset information
def initial_data_info(df):
    print("=== Dataset Info ===")
    print(df.info())
    print("\n=== Dataset Description ===")
    print(df.describe())
    print("\n=== Null Values Per Column ===")
    print(df.isnull().sum())
    print("=" * 60)

# STEP 2: Remove null values
def remove_nulls(df):
    return df.dropna()

# STEP 3: Remove outliers using IQR
def remove_outliers_iqr(df, columns):
    for col in columns:
        Q1 = df[col].quantile(0.25)
        Q3 = df[col].quantile(0.75)
        IQR = Q3 - Q1
        lower = Q1 - 1.5 * IQR
        upper = Q3 + 1.5 * IQR
        df = df[(df[col] >= lower) & (df[col] <= upper)]
    return df

# STEP 4: Remove outliers using Z-score
def remove_outliers_zscore(df, columns, thresh=3):
    for col in columns:
        z = np.abs(stats.zscore(df[col], nan_policy='omit'))
        df = df[(z < thresh) | (pd.isna(z))]
    return df

# STEP 5: Load your Titanic dataset
file_path = "titanic_dataset (1).csv"
df = pd.read_csv(file_path)

# Display initial info
print("Initial Information:")
initial_data_info(df)

# STEP 6: Remove null values
df_no_nulls = remove_nulls(df)
print("After Removing Null Values:", df_no_nulls.shape)
df_no_nulls.to_csv("titanic_no_nulls.csv", index=False)
print(" Saved: titanic_no_nulls.csv")

# STEP 7: Identify numeric columns
numeric_cols = df_no_nulls.select_dtypes(include=[np.number]).columns.tolist()

# STEP 8: Remove outliers using IQR
df_iqr = remove_outliers_iqr(df_no_nulls.copy(), numeric_cols)
print("After Removing Outliers (IQR):", df_iqr.shape)
df_iqr.to_csv("titanic_iqr_cleaned.csv", index=False)
print(" Saved: titanic_iqr_cleaned.csv")

# STEP 9: Remove outliers using Z-score
df_z = remove_outliers_zscore(df_no_nulls.copy(), numeric_cols)
print("After Removing Outliers (Z-score):", df_z.shape)
df_z.to_csv("titanic_zscore_cleaned.csv", index=False)
print("Saved: titanic_zscore_cleaned.csv")

print("=" * 80)
print(" Data cleaning complete! All cleaned files saved successfully.")
```

# RESULT
<img width="1197" height="746" alt="Screenshot 2025-10-09 110310" src="https://github.com/user-attachments/assets/e799e0f2-32cb-4dc7-8fab-6ec272cd78d7" />
<img width="1169" height="415" alt="Screenshot 2025-10-09 110319" src="https://github.com/user-attachments/assets/5209c9cd-0183-4571-9afe-0a7d20136850" />

       

