# Exp-10-Data-Science-Process-on-Complex-Dataset

# Aim:
To Perform Data Science Process on a complex dataset and save the data to a file.

# Algorithm:
## STEP 1:
Read the given Data

## STEP 2:
Clean the Data Set using Data Cleaning Process

## STEP 3:
Apply Feature Generation/Feature Selection Techniques on the data set

## STEP 4:
Apply EDA /Data visualization techniques to all the features of the data set

# Program:
Developed by : Priyadharshini.P
Register number : 212222100039

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

### Assuming the dataset is in a CSV file
df = pd.read_csv('covid_19_data.csv')
print(df.head())
print(df.describe())
print(df.dtypes)
print(df.isnull().sum())
df = df.dropna(thresh=len(df) * 0.7, axis=1)

### Create a bar plot of total cases by country
country_total_cases = df.groupby('Country/Region')['Confirmed'].sum().sort_values(ascending=False)
plt.bar(country_total_cases.index[:10], country_total_cases[:10])
plt.xlabel('Country')
plt.ylabel('Total Cases')
plt.title('Top 10 Countries with Highest Total Cases')
plt.xticks(rotation=45)
plt.show()

### correlation matrix and heatmap
corr_matrix = df.corr()
sns.heatmap(corr_matrix, annot=True, cmap='coolwarm')
plt.title('Correlation Matrix')
plt.show()

column_name = 'Confirmed'
print(df[column_name].describe())

### Plot a histogram to visualize the distribution of the column
plt.hist(df[column_name], bins=10)
plt.xlabel(column_name)
plt.ylabel('Frequency')
plt.title('Distribution of ' + column_name)
plt.show()
### Calculate and display the skewness and kurtosis of the column
skewness = df[column_name].skew()
kurtosis = df[column_name].kurtosis()
print('Skewness:', skewness)
print('Kurtosis:', kurtosis)
### bivariate analysis
column1 = 'Confirmed'
column2 = 'Recovered'
### Scatter plot
plt.scatter(df[column1], df[column2])
plt.xlabel(column1)
plt.ylabel(column2)
plt.title(column1 + ' vs. ' + column2)
plt.show()
### Correlation coefficient
correlation_coeff = df[column1].corr(df[column2])
print('Correlation Coefficient:', correlation_coeff)
### Box plot by a categorical variable
categorical_var = 'Country/Region'
sns.boxplot(x=categorical_var, y=column1, data=df)
plt.xlabel(categorical_var)
plt.ylabel(column1)
plt.title('Box Plot of ' + column1 + ' by ' + categorical_var)
plt.xticks(rotation=90)
plt.show()





