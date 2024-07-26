INTRODUCTION.
Project Overview.
- Exploratory data analysis to help generate insights for the business.
Business Problem.
The company has decided to create a new movie studio, but they don’t know anything about creating movies. I am charged with exploring the types of films that are currently doing the best at the box office.
I will translate those findings into actionable insights that the head of the company ‘s new movie studio can use to decide what type of films to create.

DATA UNDERSTANDING
I chose the movies gross data set, to help me analysis the income of movie studios through the years, the data set offers analysis for 8yrs; 2010-2018, where it offers data ranging from both domestic and foreign gross through the year.
DATA ANALYSIS
For my analysis, I chose to clean just the domestic gross income and foreign gross income; these two sets show the income of domestic or local gross income of the studios production performance at the local box office premiere. And the Foreign gross shows how their productions faired on globally. 
And after cleaning I plotted graphs to show the differences in the foreign and domestic gross between two top performing studios across the years.
RECOMMENDATIONS
First, from the analysis I would recommend to spend more on domestic advertising to boost the domestic gross income since better advertising results in more popularity and that might help increase profit for the studio.
Also, I would also recommend that we try and emulate some of the other studios techniques to try and learn what they do in their production process; that is pre and post production that helps them keep their costs of production reasonable, thus results in them bigger profits back home and also globally.


## Final Project Submission

Please fill out:
* Student name: Dennis Victor Muriungi
* Student pace: Full Time
* Scheduled project review date/time: 26/7//2024
* Instructor name: Antonny Muiko
* Blog post URL:N/A
 

 
 
### 1.Importing Libraries
import pandas as pd
import numpy as np

import seaborn as sns
import matplotlib.pyplot as plt
%matplotlib inline
### 2. Loading The Data
movie_gross = pd.read_csv( r'C:\Users\Administrator\Documents\Flatiron\phase-two-project\unzipped\bom.movie_gross.csv')
### 3. Data Analysis
# checking for the first ten movies in the dataframe 
movie_gross.head(10)
#Checking for the last ten in the dataset 

movie_gross.tail(10)
# Checking for the total number null values in each column 
movie_gross.isna().sum()
#Confirming number of rows and columns in the dataframe 

movie_gross.shape
### 4. Cleaning the data
# dropping null values 
movie_gross = movie_gross.dropna(0)
movie_gross
movie_gross.isna().sum()
domestic_gross_mean = movie_gross['domestic_gross'].mean

print(domestic_gross_mean)


# Clean and convert the 'foreign_gross' column to numeric values
movie_gross['foreign_gross'] = movie_gross['foreign_gross'].replace('[\$,]', '', regex=True)  
movie_gross['foreign_gross'] = pd.to_numeric(movie_gross['foreign_gross'], errors='coerce')  # Convert to numeric, coerce errors to Null value

# Calculate the mean of the 'foreign_gross' column, skipping NaNs
foreign_gross_mean = movie_gross['foreign_gross'].mean()

print(foreign_gross_mean)

movie_gross['year']
### Plotting graph of WB studios annual domestic gross through the years
# Group studio and year against domestic gross
annual_domestic_gross = movie_gross.groupby(['studio','year'])['domestic_gross'].sum().reset_index()

# Select studio i want to plot 
studio = 'WB'
# Data for selected studio
studio_data = annual_domestic_gross[annual_domestic_gross['studio']== studio]

# plotting graph

plt.figure(figsize=(10,6))
plt.plot(studio_data['year'], studio_data['domestic_gross'], marker='o', linestyle = '-', color = 'b')
plt.title(f'Domestic gross through the years for {studio}')
plt.xlabel('Year')
plt.ylabel('Domestic Gross')
plt.grid(True)
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
### Plotting graph of WB studios annual foreign gross through the years
# Group studio and year against foreign gross
annual_foreign_gross = movie_gross.groupby(['studio','year'])['foreign_gross'].sum().reset_index()

# Select studio i want to plot 
studio = 'WB'
# Data for selected studio
studio_data = annual_foreign_gross[annual_domestic_gross['studio']== studio]

# plotting graph

plt.figure(figsize=(10,6))
plt.plot(studio_data['year'], studio_data['foreign_gross'], marker='o', linestyle = '-', color = 'y')
plt.title(f'Foreign gross through the years for {studio}')
plt.xlabel('Year')
plt.ylabel('Foreign Gross')
plt.grid(True)
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
### Plotting graph of BV studios annual domestic gross through the years
# Group studio and year against domestic gross
annual_domestic_gross = movie_gross.groupby(['studio','year'])['domestic_gross'].sum().reset_index()

# Select studio i want to plot 
studio = 'BV'
# Data for selected studio
studio_data = annual_domestic_gross[annual_domestic_gross['studio']== studio]

# plotting graph

plt.figure(figsize=(10,6))
plt.plot(studio_data['year'], studio_data['domestic_gross'], marker='o', linestyle = '-', color = 'b')
plt.title(f'Domestic gross through the years for {studio}')
plt.xlabel('Year')
plt.ylabel('Domestic Gross')
plt.grid(True)
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
### Plotting graph of BV studios annual foreign gross through the years
# Group studio and year against foreign gross
annual_foreign_gross = movie_gross.groupby(['studio','year'])['foreign_gross'].sum().reset_index()

# Select studio i want to plot 
studio = 'BV'
# Data for selected studio
studio_data = annual_foreign_gross[annual_foreign_gross['studio']== studio]

# plotting graph

plt.figure(figsize=(10,6))
plt.plot(studio_data['year'], studio_data['foreign_gross'], marker='o', linestyle = '-', color = 'b')
plt.title(f'Foreign gross through the years for {studio}')
plt.xlabel('Year')
plt.ylabel('Foreign Gross')
plt.grid(True)
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

