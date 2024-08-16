# Corporate ESG Data Analysis Project

## Table of Contents
1. [Project Overview](#project-overview)
2. [Data Sources](#data-sources)
3. [Tools](#tools)
4. [Data Cleaning/Preparation](#data-cleaningpreparation)
5. [Exploratory Data Analysis](#exploratory-data-analysis)
6. [Data Analysis](#data-analysis)
7. [Results](#results)
8. [Recommendations](#recommendations)
9. [Limitations](#limitations)
    
## Project Overview
This project aims to analyze a comprehensive dataset of over 50,000 companies, with details such as website domain, company name, stock ticker, and involvement in specific controversial activities. The primary objective is to conduct an ESG (Environmental, Social, and Governance) assessment, exploring corporate practices and generating insights into the global corporate landscape.

## Data Sources
The dataset includes information on over 50,000 companies.- Variables include:
1. **Company Name**
2. **Website Domain**
3. **Stock Ticker**
4. **Involvement in Controversial Activities** (e.g., arms manufacturing, environmental violations, etc.)
   
## Tools
1. **Python**: For data cleaning, preparation, and analysis.
2. **Pandas**: Data manipulation and analysis.
3. **NumPy**: Numerical operations.
4. **Matplotlib/Seaborn**: Data visualization.
5. **Scikit-Learn**: Machine learning models (if applicable).
6. **Jupyter Notebook**: Interactive computing environment.
   
## Data Cleaning/Preparation
### Steps:
1. **Loading the Dataset**:
   ```python
   import pandas as pd
   df = pd.read_csv('companies_dataset.csv');
   ```
2. **Handling Missing Values**
   1. Identify missing values
   2. Impute or drop missing data depending on the context
      ```df.isnull().sum()
      df.dropna(subset=['Company Name', 'Website Domain', 'Stock Ticker'], inplace=True)
3. **Standardizing data**
   1. Convert all text to lowercase
   2. Remove duplicates
      ```df['Company Name'] = df['Company Name'].str.lower()
      df.drop_duplicates(subset=['Company Name', 'Stock Ticker'], inplace=True)
4. **Feature Engineering**
   1. Create new variables if necessary, such as a binary indicator for companies involved in controversial activities.
      
      ```df['Controversial Activities'] = df['Controversial Activities'].apply(lambda x: 1 if x else 0)```

## Exploratory Data Analysis
### Steps:

1. **Descriptive Statistics**:
   1. Summary statistics of key variables.
    ```df.describe()```

2. **Distribution Analysis**:
   1. Plot distributions of key features.
    ```
    import seaborn as sns
    import matplotlib.pyplot as plt
    
    sns.histplot(df['Controversial Activities'])
    plt.show()

3. **Correlation Analysis**
   1. Analyze the relationships between variables.
    ```
    corr_matrix = df.corr()
    sns.heatmap(corr_matrix, annot=True)
    plt.show()```

## Data Analysis
### Steps:
1. **ESG Score Calculation**:
   1. Develop an ESG scoring model based on company involvement in controversial activities.
    ```df['ESG Score'] = 100 - (df['Controversial Activities'] * 20)  # Example scoring model```

2. **Trend Analysis**:
   1. Identify trends in controversial activities across industries or regions
    ```
    industry_trend = df.groupby('Industry')['Controversial Activities'].mean()
    industry_trend.plot(kind='bar')
    plt.show()

3. **Clustering Analysis**
   1. Group companies based on ESG scores and other features.
    ```from sklearn.cluster import KMeans

    kmeans = KMeans(n_clusters=3)
    df['Cluster'] = kmeans.fit_predict(df[['ESG Score']])
    sns.scatterplot(x='ESG Score', y='Cluster', data=df)
    plt.show()

## Results
1. The analysis reveals that a significant number of companies are involved in controversial activities.
2. Companies in certain industries or regions have lower ESG scores, indicating higher involvement in undesirable activities.
3. Clustering analysis highlights distinct groups of companies based on ESG scores.

## Recommendations
1. **Investors**: Consider companies with higher ESG scores for sustainable investments.
2. **Companies**: Focus on improving practices in areas flagged by the ESG assessment.
3. **Regulators**: Use these insights to develop or refine policies addressing controversial corporate activities.
   
## Limitations
1. **Data Accuracy**: The dataset relies on reported information, which may not capture all activities.
2. **Scoring Model**: The ESG scoring model is simplistic and may need to be refined for more accurate assessments.
3. **Generalization**: The results are based on the dataset provided and may not be applicable to all industries or regions.

