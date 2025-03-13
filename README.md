# DAI-101-Assignment-1
This project involves performing data cleaning and exploratory data analysis (EDA) on a real estate dataset containing information about various properties. The dataset includes details such as location, size, area type, number of bathrooms, balconies, and price.

Data Cleaning
Data cleaning is the process of preparing raw data by identifying and handling issues such as missing values, duplicate records, outliers, and inconsistencies. This ensures that the data is accurate and ready for analysis.


Handle Missing Values

Missing values can occur due to data collection errors, incomplete surveys, or system issues.

Methods to handle missing values:

Removal: Drop rows/columns using dropna(). This is useful if missing values are minimal.

Imputation: Fill missing values using:

Mean/median (for numerical data)
Mode (for categorical data)
Forward or backward fill (for time-series data)
Predictive imputation (using models like KNN imputer)

Identify and Remove Duplicate Records
Duplicate records can distort analysis, leading to incorrect conclusions.
Detect duplicates using df.duplicated() and remove them using df.drop_duplicates().

Detect and Treat Outliers

Outliers are extreme values that deviate significantly from the rest of the data.

Methods to detect outliers:
Statistical methods:
Z-score (values above 3 or below -3 are considered outliers)
IQR (Interquartile Range: values beyond Q1 - 1.5*IQR or Q3 + 1.5*IQR)
Visualization methods:
Box plots
Histograms
Scatter plots
Methods to handle outliers:
Removal (if they are errors)
Transformation (e.g., log transformation)
Capping (replacing extreme values with upper/lower limits)

Standardize Categorical Values
Inconsistent categorical values can occur due to typos or different formats (e.g., "male" vs. "Male" vs. "M").
Standardization techniques:
Convert text to lowercase using .str.lower()
Use .replace() to fix typos
Apply encoding techniques like one-hot encoding or label encoding for machine learning models

Exploratory Data Analysis (EDA)
EDA is the process of analyzing datasets to summarize their key characteristics and discover patterns or insights. It involves univariate, bivariate, and multivariate analyses.

Univariate Analysis (Single-Variable Exploration)
This involves analyzing a single variable at a time.

Summary Statistics
Provides key metrics such as:
Mean (average): df['column'].mean()
Median (middle value): df['column'].median()
Mode (most frequent value): df['column'].mode()
Variance (spread of data): df['column'].var()
Skewness (asymmetry of data distribution): df['column'].skew()
Kurtosis (peakedness of data distribution): df['column'].kurt()
Frequency Distributions for Categorical Variables
Shows the count of occurrences for each category.
Use .value_counts() in pandas.
Bar charts or pie charts can visualize categorical distributions.
Histograms and Box Plots
Histograms: Show the frequency distribution of numerical variables.
Use plt.hist() in Matplotlib or sns.histplot() in Seaborn.
Box Plots: Help detect outliers and understand data spread.
Use sns.boxplot() to visualize quartiles and outliers.

Bivariate Analysis (Two-Variable Exploration)
Examines relationships between two variables.

Correlation Matrix

Measures the strength of relationships between numerical variables.
Use .corr() in pandas and visualize using sns.heatmap().
Scatter Plots
Used for continuous numerical variables to identify trends and correlations.
Example: sns.scatterplot(x='Variable1', y='Variable2', data=df)
Bar Plots, Violin Plots, and Box Plots
Bar Plots: Compare categorical and numerical data (sns.barplot(x='category', y='value', data=df)).
Violin Plots: Show distribution, density, and probability (sns.violinplot(x='category', y='value', data=df)).
Box Plots: Compare numerical data across categories (sns.boxplot(x='category', y='value', data=df)).
2.3 Multivariate Analysis (Multiple Variables Exploration)
Examines interactions between multiple variables.

Pair Plots

A grid of scatter plots between different numerical variables.
Helps visualize relationships between multiple variables.
Use sns.pairplot(df).
Heatmaps
Used to show correlations between multiple numerical variables.
A darker color represents a stronger correlation.
sns.heatmap(df.corr(), annot=True, cmap='coolwarm')
Grouped Comparisons
Compares multiple features together.
Example: Comparing average salaries by job role and location.
Can be visualized using:
Facet Grids: sns.FacetGrid()
Grouped Bar Plots: sns.barplot()
3D Scatter Plots: ax.scatter3D() in Matplotlib for multidimensional analysis.

Steps Performed

1. Data Cleaning

Checked for missing values:

society column had significant missing values (~41%).

balcony, bath, size, and location had minor missing values.

Handling missing data :
By removing and replacing with most frequent data

Checked for duplicate records:

Found and removed duplicate entries.

Handled inconsistent data formats:

size contained values like "2 BHK" and "4 Bedroom", which were standardized.

total_sqft had range values (e.g., "1200 - 1500"), requiring conversion to numeric.

total_sqft had values in sq.meters, sq.yards which are to be converted into sq.ft.

Identified and handled outliers:

bathroom count showed extreme values (max = 40), requiring further validation.

price column had a wide range, needing further investigation.

2. Exploratory Data Analysis (EDA)

Summary Statistics:

Displayed key statistics such as mean, median, min, and max for numerical columns.

Identified key trends in the dataset.

Categorical Analysis:

location had 1,305 unique values, indicating a diverse dataset.

area_type had 4 unique values.

Price Distribution:

The price ranged from 8 lakh INR to 3600 lakh INR, suggesting potential outliers.

Bathroom Analysis:

Most properties had 2 to 3 bathrooms, but extreme values (40) were detected.

Next Steps

Handle outliers in price and bathroom columns.

Convert non-numeric fields into standardized formats.

Perform deeper analysis on price per square foot trends.

Visualize key trends using histograms, boxplots, and scatter plots.

