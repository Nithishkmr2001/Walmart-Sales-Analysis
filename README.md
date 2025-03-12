# Walmart Sales Analysis: SQL + Python Project

## Overview

This project provides an end-to-end data analysis solution for extracting business insights from Walmart sales data. We leverage Python for data processing, SQL for advanced querying, and structured problem-solving techniques to answer key business questions. This project is ideal for data analysts looking to enhance their skills in data manipulation, SQL querying, and data pipeline creation.

## Project Workflow

### 1. Environment Setup

**Tools Used:** Visual Studio Code (VS Code), Python, SQL (MySQL)
**Objective:** Create a well-structured workspace for efficient development and data handling.

### 2. Kaggle API Configuration

- Download the Kaggle API key (`kaggle.json`) from your Kaggle profile.
- Save it in the `.kaggle` folder.
- Use `kaggle datasets download -d <dataset-path>` to fetch datasets.

### 3. Data Acquisition

- **Dataset:** Walmart Sales Dataset
- **Storage:** Save downloaded data in the `data/` directory.

### 4. Library Installation & Data Loading

#### Install Dependencies:

```sh
pip install pandas  sqlalchemy pymysql
```

#### Load Data:

```python
import pandas as pd
df = pd.read_csv('Walmart.csv')
df.head()
```

### 5. Exploratory Data Analysis (EDA)

**Objective:** Understand data distribution, column types, and potential issues.

#### Key Methods:

```python
df.shape
df.info()
df.describe()
df.head()
```

### 6. Data Cleaning

#### Tasks:

- Remove duplicate records:
  ```python
  df.drop_duplicates(inplace=True)
  ```
- Handle missing values:
  ```python
  df.dropna(inplace=True)
  ```
- Standardize data types:
  ```python
  df['unit_price'] = df['unit_price'].str.replace('$', '').astype(float)
  ```

### 7. Feature Engineering

#### Enhancements:

- Create a new column: **Total Amount**
  ```python
  df['Total'] = df['unit_price'] * df['quantity']
  df['Total'] = df['Total'].round(2)
  ```
- Save cleaned data:
  ```python
  df.to_csv()
  ```

### 8. Data Ingestion into MySQL & PostgreSQL

#### Connections:

```python
from sqlalchemy import create_engine
import pymysql

engine = create_engine("mysql+pymysql://root:password@localhost:3306/Walmart_sales")
con = engine.connect()
```

#### Insert Data into MySQL:

```python
df.to_sql()
```

### 9. SQL Analysis & Business Insights

#### Key Queries:

1. **Revenue Trends by Top 10 Branches & Categories**

2. **Best-Selling Product Categories**
   
3. **Top 5 Average Order Value (AOV) by Branch**
   
4. **Top 5 Performing Cities by Sales**
  
5. **Total Revenue by Payment Method**
  
### 10. Project Documentation & Publishing

#### Documentation:

- Maintain detailed project notes in Markdown or Jupyter Notebook.

#### Publishing:

Upload project files to GitHub, including:

- `README.md`
- Jupyter Notebooks
- SQL scripts
- Data access steps

---

## Requirements

- **Python:** 3.8+
- **Databases:** MySQL
- **Libraries:** pandas, numpy, sqlalchemy, pymysql
- **Kaggle API Key** (for data downloading)

