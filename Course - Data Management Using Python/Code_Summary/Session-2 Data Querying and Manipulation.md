# 📘 Python Session-2 Cheat Sheet

## 📂 File Handling with Pandas

* `import pandas as pd`
* `pd.read_excel(path, sheet_name='Sheet')` – Read Excel file
* `pd.set_option('display.max_rows', None)` – Show all rows
* `pd.set_option('display.max_columns', None)` – Show all columns

---

## 🔎 Data Exploration

* `df.head(100)` – First 100 rows
* `df.tail(10)` – Last 10 rows
* `df[10:20]` – Slice specific rows
* `df.shape` – Rows and columns
* `df.info()` – Structure and data types
* `df.columns.values` – List of column names
* `df.dtypes` – Data types of all columns
* `df.describe()` – Summary stats

---

## 🧹 Missing Values Handling

* `df.isnull().sum()` – Missing count per column
* `df.isnull().count()` – Total count per column
* `df.isnull().sum().sum()` – Total missing values

---

## 🎯 Random Sampling

* `df.sample(n=10, random_state=42)` – Random 10 rows

---

## 📊 Column-wise Exploration

* `df['column'].value_counts()` – Count unique values
* `df['column'].nunique()` – Number of unique values

---

## 🗃️ Sorting and Indexing

* `df.sort_values(by='column', ascending=False)` – Sort
* `df.reset_index(drop=True, inplace=True)` – Reset index

---

## 🧾 Grouping and Aggregation

* `df.groupby('column').agg({'col1':'sum', 'col2':'count'})` – Aggregation
* `df.groupby(['col1','col2']).size().reset_index(name='count')` – Group and count

---

## 🧠 Conditional Subset

* `df[df['column'] > value]` – Filter rows by condition

---

