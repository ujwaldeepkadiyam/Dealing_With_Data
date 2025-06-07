# 📘 Python Session-3 Summary (Up to Advanced Joining)

## 🔹 Topic: Joining, Relationship, and Data Model

---

## 1. 🧱 Types of Joining

### 🔼 Vertical Join – Appending Tables
- Combine datasets **row-wise** (same structure)
- Rules:
  - Same number of columns
  - Same data types
  - Order of columns matters

```python
pd.concat([df1, df2], ignore_index=True)
````

---

### 🔁 Horizontal Join – Merging Tables

* Combine datasets **column-wise** using a key
* Rules:

  * Must specify `on` (common key)
  * Use `how` for type of join

---

## 2. 📚 Practice with Vertical Join

### ✅ Scenario-Based Appending

* Scenario 1–5 cover:

  * Exact match appending
  * Column mismatch handling
  * Column renaming for compatibility
  * Adding missing columns

### ⚖️ Union vs Union All

* **Union** removes duplicates
* **Union All** retains all records

---

## 3. 🔗 Horizontal Join – Merging Datasets

### Types of Horizontal Joins in Python

#### 🔍 `INNER JOIN`

* Returns records with matching keys in both datasets

```python
pd.merge(df1, df2, how='inner', on='key')
```

#### 🌐 `FULL OUTER JOIN`

* Returns all records from both datasets, fills unmatched with NaN

```python
pd.merge(df1, df2, how='outer', on='key')
```

#### 🚫 `UNMATCHED JOIN`

* Identify records present in one dataset but not the other

#### ⬅️ `LEFT OUTER JOIN`

* All records from the left dataset, matched from right

```python
pd.merge(df1, df2, how='left', on='key')
```

#### ❌ `LEFT NULL JOIN`

* Only left records **without** a match in right

```python
pd.merge(df1, df2, how='left', on='key')[df2['key'].isnull()]
```

#### ➡️ `RIGHT OUTER JOIN`

* All records from the right dataset, matched from left

```python
pd.merge(df1, df2, how='right', on='key')
```

#### 🚫 `RIGHT NULL JOIN`

* Only right records **without** a match in left

---

## 4. 🧪 Merging Rules Summary

* **inner** = matched rows only
* **outer** = all rows from both sides
* **left** = all from left, matched from right
* **right** = all from right, matched from left

---

### 🧪 Merging Test Exercises

* Practice merges on various conditions
* Understand behavior of nulls and missing keys

---

# 📘 Python Session-3 Summary: Advanced Joining

## 🔹 ADVANCED JOINING

### 🔗 Multi-Column Join
Join based on multiple keys using `on=['PRODUCT', 'CITY']`.

#### 🧪 Example
```python
pd.merge(left=prod_units, right=prod_price, how='inner', on=['PRODUCT', 'CITY'])
````

### 💲 Add Sales Column

```python
df['SALES'] = df['UNITS'] * df['PRICE']
```

---

## 🧮 Types of Joins with Multi-Keys

### 🔍 Inner Join

* Returns only matching records from both datasets.

### 🌐 Full Outer Join

* Returns all records from both datasets; unmatched columns filled with NaN.

### 🚫 Unmatched Join

* Extract rows with mismatched values in either side.

```python
df[df['UNITS'].isnull() | df['PRICE'].isnull()]
```

### ⬅️ Left Join

* Returns all rows from the left table and matched from right.

### ❌ Left Null Join

* Only left table rows without a matching right table record.

```python
df[df['PRICE'].isnull()]
```

### ➡️ Right Join

* All rows from the right and matching from left.

### 🚫 Right Null Join

* Right table rows with no match in left table.

```python
df[df['UNITS'].isnull()]
```

---

## 🏷️ Use of `suffixes` in Merges

When merging datasets with overlapping column names, use:

```python
pd.merge(df1, df2, how='inner', on='ACC_NO', suffixes=('_Jan', '_Feb'))
```

---

# 📘 Python Session-3 Summary: Data Models

## 🔹 DATA MODEL DESIGN

---

## 🧊 Types of Data Models

### ⭐ 1. STAR SCHEMA
- A central **fact table** connects directly to all **dimension tables**.
- Simple and flat structure, ideal for query performance.

#### 🔄 Example: Merge Transaction Data with Master Tables
```python
transaction_master = pd.read_excel(file_path, sheet_name='TRANSACTION_TABLE')
customer_master    = pd.read_excel(file_path, sheet_name='CUSTOMER_TABLE')
product_master     = pd.read_excel(file_path, sheet_name='PRODUCT_TABLE')
store_master       = pd.read_excel(file_path, sheet_name='STORE_TABLE')
staff_master       = pd.read_excel(file_path, sheet_name='STAFF_MASTER')

# Step-by-step merging
dm1 = pd.merge(transaction_master, customer_master, how='left', on='CUST_ID')
dm2 = pd.merge(dm1, product_master, how='left', on='PROD_ID')
dm3 = pd.merge(dm2, store_master, how='left', on='STORE_ID')
final_output = pd.merge(dm3, staff_master, how='left', on='STAFF_ID')
````

#### 📑 Reordering Columns

```python
new_order_vars = ['ORDER_ID', 'ORDER_DT', 'CUST_ID', 'CUST_NAME', 'DOB', 'MOBILE',
                  'PROD_ID', 'PROD_NAME', 'CATEGORY', 'PRICE', 'INVENTORY', 'SUPPLIER_ID',
                  'STORE_ID', 'STORE_NAME', 'LOCATION', 'STAFF_ID', 'STAFF_NAME',
                  'DESIGNATION', 'YOE', 'QTY']

final_output_new = final_output[new_order_vars]
```

---

### ❄️ 2. SNOWFLAKE SCHEMA

* Dimension tables are further normalized into sub-dimensions.
* More complex structure; better for detailed analysis but slower queries.

#### ⛓️ Example: Including Supplier Table

```python
supplier_master = pd.read_excel(file_path, sheet_name='SUPPLIER_MASTER')

# Additional join to link supplier details
dm4 = pd.merge(final_output, supplier_master, how='left', on='SUPPLIER_ID')
```

---

These examples help establish a **robust data model** in Python using pandas merging logic.

* Star Schema: Ideal for performance and reporting
* Snowflake Schema: Preferred for normalized data and flexibility
