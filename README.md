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
2. **Handling Missing Values**:
   1. Identify missing values.
   2. Impute or drop missing data depending on the context.
```df.isnull().sum()
df.dropna(subset=['Company Name', 'Website Domain', 'Stock Ticker'], inplace=True)

3. **Standardizing Data**
