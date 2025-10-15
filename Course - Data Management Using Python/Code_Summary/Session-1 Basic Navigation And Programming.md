# 📘 Python Session-1 Cheat Sheet

## ✅ Python Version Check
- `from platform import python_version`
- `print(python_version())`

---

## 🧠 Variables and Data Types
- `instutute_name = 'DV Analytics'` – String
- `type(instutute_name)`
- `customer_age = 18` – Integer
- `type(customer_age)`
- `total_sales = 100.890` – Float
- `type(total_sales)`
- `value = 100 + 3j` – Complex
- `type(value)`
- `value_range = range(0, 10)` – Range
- `type(value_range)`
- `print(list(value_range))`

---

## 🔁 Comparison Operators
- `x > y` – Greater than
- `x < y` – Less than
- `x != y` – Not equal to
- `x == y` – Equal to

---

## 🔘 Boolean Type
- `type(True)`
- `type(False)`

---

## 📚 Collection Data Types

### List
- `stu_name = ['ravi','kiran','sohail','arbaz']`
- `type(stu_name)`

### Tuple
- `stu_name = ('ravi','kiran','sohail','arbaz')`
- Tuples are immutable

### Set
- `stu_name = {'ravi','kiran','sohail','arbaz'}`
- Cannot index or update individual items
- `set.update([items])`

### Dictionary
- `stu_name = {'ravi':23,'kiran':34}`
- `stu_name['ravi']` – Access/Update
- `del stu_name['ravi']` – Delete
- `stu_name.update({'new': 45})` – Merge

---

## ➕ Basic Arithmetic Operators
- `x + y` – Addition
- `x - y` – Subtraction
- `x * y` – Multiplication
- `x / y` – Division
- `x // y` – Floor Division
- `x % y` – Modulus
- `x ** y` – Exponent

---

## 🔠 String Indexing and Slicing
- `x[0]` – First character
- `x[-1]` – Last character
- `x[0:3]` – Substring from 0 to 2

---

## 🔁 List Operations
- `list[1] = 'new'` – Update
- `del list[1]` – Delete
- `list1 + list2` – Concatenate

---

## ⚠️ Tuple Limitations
- Tuples are immutable
- Cannot update or delete elements

---

## 🔁 Set Operations
- `set.update([elements])` – Add multiple items
- Sets do not support indexing or item updates

---

## 📒 Dictionary Operations
- `dict['key']` – Access or update
- `del dict['key']` – Delete key
- `dict.update({'key': value})` – Add/merge key

---

## 🧮 Basic Math Computation
- `a = 100`
- `b = 200`
- `c = a + b`

---

## 📊 Creating a Pandas DataFrame
- `import pandas as pd`
- `df = pd.DataFrame({...})`

---

## 🔎 Exploring a DataFrame
- `df.shape` – Shape of data
- `df.head()` – First 5 rows
- `df.tail()` – Last 5 rows
- `df.info()` – Structure info
- `df.describe()` – Statistical summary

---

## 🧭 Selecting Data in DataFrame
- `df.loc[1:3]` – Rows by label
- `df.iloc[0:3]` – Rows by position
- `df[['col1', 'col2']]` – Select columns

---

## 🛠️ Modify DataFrame Structure
- `df['new_col'] = value` – Add column
- `df.drop(['col'], axis=1)` – Drop column
- `df.rename(columns={'old':'new'}, inplace=True)` – Rename

---

## 🧹 Truncate a DataFrame
- `df_empty = df.iloc[0:0]` – Empty DataFrame

---

## 📂 File Import and Export
- `pd.read_excel(path)`
- `pd.read_csv(path)`
- `df.to_excel(path, index=False)`
- `df.to_csv(path, index=False)`

---

## 🗃️ SQL Server Integration
- `from sqlalchemy import create_engine`
- `engine = create_engine(...)`
- `pd.read_sql(query, conn)`
- `df.to_sql('table', engine, index=False)`

---

## 🧾 Subset or Filter Data
- `df_new = df[100:200]` – Slice rows
- `df_new = df[['col1', 'col2']]` – Select columns
- `df_new = df.drop(columns)` – Drop columns

---
