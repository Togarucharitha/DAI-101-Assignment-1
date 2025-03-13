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

Load the dataset and inspect its structure:

The dataset was loaded using Pandas, and its structure was examined using .info() and .head().

Handle missing values:

The society column had ~41% missing values, which were dropped due to high sparsity.

Minor missing values in balcony, bath, size, and location were imputed using mode or median.

Identify and remove duplicate records:

Duplicate rows were detected and removed to ensure data integrity.

Detect and treat outliers:

The price and bath columns had extreme values (e.g., properties with 40 bathrooms), which were handled using interquartile range (IQR) and capping methods.

Standardize categorical values:

size values (e.g., "2 BHK" and "4 Bedroom") were standardized.

total_sqft values that contained ranges (e.g., "1200 - 1500") were converted to numeric averages.

2. Exploratory Data Analysis (EDA)

Univariate Analysis (Single-Variable Exploration)

Summary statistics:

The average price is 112.57 lakh INR, with a wide standard deviation of 148.97 lakh INR.

The average number of bathrooms is 2.69, but extreme values were observed.

Frequency distributions for categorical variables:

The dataset contains 1,305 unique locations and 4 area types.

Histograms and box plots:

Price and bathroom distributions revealed skewed data, requiring transformations.

Bivariate Analysis (Two-Variable Exploration)

Correlation matrix:

price and total_sqft showed a strong positive correlation.

Scatter plots for numerical relationships:

price vs. total_sqft displayed a non-linear trend with outliers.

Box plots and violin plots:

Properties with more bedrooms had higher median prices but greater variability.

Multivariate Analysis (Multiple Variables Exploration)

Pair plots:

Relationships among price, total_sqft, and bathrooms were analyzed for patterns.

Heatmaps:

A correlation heatmap visualized strong associations among numerical features.

Grouped comparisons:

Properties in premium locations exhibited significantly higher prices.

Key Observations

Price distribution is highly skewed, with a few extreme high-value properties influencing the mean.

Number of bathrooms and price are correlated, but extreme values (e.g., 40 bathrooms) distort trends.

Location has a major impact on price, with certain high-demand areas showing much higher median prices.

Total square footage is not always directly proportional to price, indicating other influential factors like amenities and location.
