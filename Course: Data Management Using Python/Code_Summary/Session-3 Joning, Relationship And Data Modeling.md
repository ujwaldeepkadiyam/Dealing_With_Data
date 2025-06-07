# 📘 Python Session-3 Cheat Sheet

## 🔗 Join Concepts

### 🔼 Vertical Join (Appending Tables)

* Rules:

  1. Both tables must have the same fields.
  2. Data types must match.
  3. Source table is the first one; target table is appended.

### 🔁 Horizontal Join (Merging Tables)

* Rules:

  1. Identify left and right tables.
  2. Identify common fields.
  3. Check common and uncommon records between both.

---

## 📂 File Import: Read Excel Sheets

```python
import pandas as pd

file_path = '...\\VERTICAL_JOIN_DATA.xlsx'

df1 = pd.read_excel(file_path, sheet_name='MED_APPOLO')
df2 = pd.read_excel(file_path, sheet_name='MED_CIPLA')
df3 = pd.read_excel(file_path, sheet_name='MED_GENO')
df4 = pd.read_excel(file_path, sheet_name='MED_RELEGARE')
df5 = pd.read_excel(file_path, sheet_name='MED_GSK')
```

---

## 🔼 Append (Vertical Join)

```python
df_combined = pd.concat([df1, df2, df3, df4, df5], ignore_index=True)
```

---

## 🔍 Explore Combined Data

* `df_combined.head()`
* `df_combined.tail()`
* `df_combined.info()`
* `df_combined.shape`
* `df_combined.duplicated().sum()`

---

## 🧹 Remove Duplicates

```python
df_cleaned = df_combined.drop_duplicates()
```

---

## 🔁 Horizontal Join (Merge)

```python
# Example format
pd.merge(left_df, right_df, how='inner', on='common_column')
```

Types of Join:

* `inner` – Only matching rows
* `left` – All from left, matching from right
* `right` – All from right, matching from left
* `outer` – All rows from both

---

## 🧠 Filtering Data

```python
df[df['column'] == 'value']
df[df['column'] > 100]
```


---


## 🔹 Join Concepts

* **Vertical Join** using `pd.concat([...])`

  * Rules:

    * All tables must have same columns and data types
    * First table is source, others are targets
* **Horizontal Join** using `pd.merge(...)`

  * Rules:

    * Identify left/right tables and join keys
    * Understand which records are common/uncommon

---

## 🔹 Data Loading

* Load Excel:

  ```python
  pd.read_excel(file_path, sheet_name='SheetName')
  ```
* Load CSV with encoding:

  ```python
  pd.read_csv(file_path, sep=',', encoding='Latin1')
  ```

---

## 🔹 Data Integrity Management

* Handle column mismatches:

  ```python
  df.rename(columns={'old': 'new'}, inplace=True)
  ```
* Handle different data types:

  ```python
  df['col'] = df['col'].astype(str)
  ```
* Unequal columns during concatenation → missing columns are filled with NaN automatically

---

## 🔹 Data Modeling & Consolidation

* Combine quarterly transactional files (e.g., Q1–Q4) into one:

  ```python
  pd.concat([q1, q2, q3, q4], ignore_index=True)
  ```
* Explore with:

  ```python
  df.info(), df.head(), df.shape
  ```

---

## 🔹 Data Models in Python

### 🗂️ Master Tables

* `TRANSACTION_TABLE`
* `CUSTOMER_TABLE`
* `PRODUCT_TABLE`
* `STORE_TABLE`
* `STAFF_MASTER`
* `SUPPLIER_MASTER` *(when available)*

### 🔗 Data Model Construction

```python
step1 = pd.merge(transaction_master, customer_master, on='CUST_ID', how='left')
step2 = pd.merge(step1, product_master, on='PROD_ID', how='left')
step3 = pd.merge(step2, store_master, on='STORE_ID', how='left')
step4 = pd.merge(step3, staff_master, on='STAFF_ID', how='left')
final_output = pd.merge(step4, supplier_master, on='SUPPLIER_ID', how='left')  # optional
```

### 📐 Reorder Columns

```python
final_output = final_output[new_order_vars]
```

Example structure:

```python
[
 'ORDER_ID', 'ORDER_DT', 'CUST_ID', 'CUST_NAME', 'DOB', 'MOBILE',
 'PROD_ID', 'PROD_NAME', 'CATEGORY', 'PRICE', 'INVENTORY',
 'SUPPLIER_ID', 'SUPPLIER_NAME', 'SUPP_LOCATION', 'CONTACT',
 'STORE_ID', 'STORE_NAME', 'LOCATION',
 'STAFF_ID', 'STAFF_NAME', 'DESIGNATION', 'YOE', 'QTY'
]
```

