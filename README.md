# McDonald's Menu Nutritional Analysis
  McDonald's is a global fast-food chain known for its diverse menu offerings. As a data analyst, 
your task is to analyze the nutritional content of the menu items available at McDonald's outlets. This analysis will provide valuable insights into the calorie count and nutrition 
facts of various menu items.

# Dependencies
   Used jupyter notebook For Analysisng Nutritional Dataset
   Libraries Used
```
import numpy as np
import seaborn as sns
import pandas as pd
import matplotlib.pyplot as plt
import plotly.express as px
```
# Data Preparation
```
MCD=pd.read_csv(r"C:\Users\bishn\Downloads\Nutrical Dataset (1).csv")
MCD.sample()
```
# Understanding of Data
```
MCD.info()
```
# Missing value Handing
```
MCD.isnull().sum()
```
# Data Describe
```
MCD.describe()
```
# Exploratory Data Analysis
```
# Distribution of Sugar level in the menu items
plt.figure(figsize=(12,5))
sns.histplot(x='Sugars',data=MCD,bins=12,kde=True)
plt.show()
```
# Distribution of different nutritions

``` 
sns.set(style="whitegrid")

# Create subplots
fig, axes = plt.subplots(4, 1, figsize=(10, 18))

# Total Fat
sns.histplot(MCD3['Total Fat'], bins=30, kde=True, ax=axes[0])
axes[0].set_title('Distribution of Total Fat')
axes[0].set_xlabel('Total Fat (g)')
axes[0].set_ylabel('Frequency')

# Protein
sns.histplot(MCD3['Protein'], bins=30, kde=True, ax=axes[1])
axes[1].set_title('Distribution of Protein')
axes[1].set_xlabel('Protein (g)')
axes[1].set_ylabel('Frequency')

# Carbohydrates
sns.histplot(MCD3['Carbohydrates'], bins=30, kde=True, ax=axes[2])
axes[2].set_title('Distribution of Carbohydrates')
axes[2].set_xlabel('Carbohydrates (g)')
axes[2].set_ylabel('Frequency')

#  Calories
sns.histplot(MCD3['Calories'], bins=30, kde=True, ax=axes[3])
axes[3].set_title('Distribution of calories')
axes[3].set_xlabel('Calories (g)')
axes[3].set_ylabel('Frequency')

plt.tight_layout()
plt.show()
```
# Explore the nutritional contentof different items.
```
# items contains vitamin A
High_vitaminA=MCD.sort_values('Vitamin A (% Daily Value)').tail(10)
plt.figure(figsize=(8,6))
sns.barplot(y='Item',x='Vitamin A (% Daily Value)',data=High_vitaminA,label='Vitamin A (% Daily Value)')
plt.show()

# Identifying which item under whhich category has more fat
max_fat=MCD.sort_values('Total Fat').tail(10)
plt.figure(figsize=(10,4))
sns.barplot(y='Item',x='Total Fat',data=max_fat,hue='Category')
plt.show()

# Identify which item has more protein 
max_protein=MCD.sort_values('Protein').tail(10)
plt.figure(figsize=(10,4))
sns.barplot(y='Item',x='Total Fat',data=max_protein)
plt.show()

# identifying which item has more carbohydrate
max_carb=MCD3.sort_values('Carbohydrates').tail(10)
plt.figure(figsize=(10,4))
sns.barplot(y='Item',x='Carbohydrates',data=max_carb)
plt.show()

# identifying which item has more calories
max_calories=MCD3.sort_values('Calories').tail(10)
plt.figure(figsize=(10,4))
sns.barplot(y='Item',x='Calories',data=max_calories)
plt.show()
```
#  identifying trends of vitamin A category wise
```
#  identifying trends of vitamin A category wise
plt.figure(figsize=(8,3))
sns.barplot(y='Category',x='Vitamin A (% Daily Value)',data=MCD)
plt.show()
'''

'''
#  Identifying trends of Iron categorywise
plt.figure(figsize=(8,3))
sns.barplot(y='Category',x='Iron (% Daily Value)',data=MCD3)
'''

plt.figure(figsize=(14,3))
sns.boxplot(y='Cholesterol',x='Category',data=MCD,hue='Category')
plt.legend(ncols=MCD['Category'].nunique()/3)
plt.show()
```
# Outlier treatment
```
col=MCD2.select_dtypes(exclude='object').columns
Q1 = MCD2[col].quantile(0.25)
Q3 = MCD2[col].quantile(0.75)
IQR = Q3 - Q1
MCD2= MCD2[~((MCD2[col] < (Q1 - 1.5*IQR))| (MCD2[col] > (Q3 + 1.5*IQR))).any(axis=1)]

```

# McDonald's could improve the nutritional profile of their menu.
 
•	Include information on allergens and ingredients to cater to customers with dietary restrictions.
•	Remove food items which are very high in calories or reduce its proportion 

•	Food with very low protein you can items with it to have protein consumption.

•	Implement a system for customers to provide feedback on the nutritional information provided. This can be through surveys, app reviews, or in-store feedback forms.

•	Can give discount or reduce price on healthy meals. 

•	Keep price of unhealthy meals a little higher.





