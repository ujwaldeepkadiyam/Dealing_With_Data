# 📘 Python Session-4 Summary: Character Functions

## 🔹 1. CHARACTER FUNCTIONS

### 🔡 Convert Character Case
```python
df['Name_Capital'] = df['Name'].str.upper()
df['Name_Small'] = df['Name'].str.lower()
df['Name_Proper'] = df['Name'].str.title()
````

---

### 🔗 Concatenate Character Fields

```python
df['Full_Address'] = df['State'] + '-' + df['District'] + '-' + df['Area']
```

---

### 📍 Find Character Position

```python
df['Index_Pos'] = df['Customer_Name'].str.index(' ')
df['Find_Pos'] = df['Customer_Name'].str.find(' ')
```

---

### 🧩 Split First and Last Name (Using Index)

```python
df['Delimiter'] = df['Customer_Name'].apply(lambda x: x.index(' '))
df['First_Name'] = df.apply(lambda x: x['Customer_Name'][:x['Delimiter']], axis=1)
df['Last_Name'] = df.apply(lambda x: x['Customer_Name'][x['Delimiter']+1:], axis=1)
```

---

### 🪓 Split Names Using `split()`

```python
df['First_Name'] = df['Customer_Name'].apply(lambda x: x.split(' ')[0])
df['Last_Name'] = df['Customer_Name'].apply(lambda x: x.split(' ')[1])
```

---

### 🔁 Replace Values in Text

```python
df['Gender'] = df['Gender'].replace('M', 'Male').replace('F', 'Female')
string = string.replace('Endulkar', 'Tendulkar')
```

---

### 📏 Get String Length

```python
len('Full Name String')
```

---

### 🧵 Split by Delimiters (`space`, `-`, `_`)

```python
first, middle, last = full_name.split(' ')
first, middle, last = full_name.split('-')
first, middle, last = full_name.split('_')
```

---

These functions are essential for:

* Cleaning and standardizing text data
* Parsing names
* Creating composite identifiers
* Preparing text columns for reporting and analysis



# 📘 Python Session-4 Summary: Numeric Functions

## 📊 Dataset Used:
- Excel file: `Python_Function_Data.xlsx`
- Sheet: `NUMERIC FUNCTION TEST`

---

## 🔹 Aggregation by Quarter

### 🧾 Define Monthly Columns
```python
qtr_1_vars = ['Jan', 'Feb', 'Mar']
qtr_2_vars = ['Apr', 'May', 'Jun']
qtr_3_vars = ['Jul', 'Aug', 'Sep']
qtr_4_vars = ['Oct', 'Nov', 'Dec']
````

### ➕ Compute Quarterly Totals

```python
prod_sales['Qtr_1_total_sales'] = prod_sales[qtr_1_vars].sum(axis=1)
prod_sales['Qtr_2_total_sales'] = prod_sales[qtr_2_vars].sum(axis=1)
prod_sales['Qtr_3_total_sales'] = prod_sales[qtr_3_vars].sum(axis=1)
prod_sales['Qtr_4_total_sales'] = prod_sales[qtr_4_vars].sum(axis=1)
```

---

## 🔹 Yearly Aggregation

### 📆 Define Full Year Columns

```python
yearly_vars = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun',
               'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']
```

### 🧮 Yearly Calculations

```python
prod_sales['yearly_total_sales'] = prod_sales[yearly_vars].sum(axis=1)
prod_sales['yearly_avg_sales'] = prod_sales[yearly_vars].mean(axis=1)
prod_sales['yearly_min_sales'] = prod_sales[yearly_vars].min(axis=1)
prod_sales['yearly_max_sales'] = prod_sales[yearly_vars].max(axis=1)
```

---

These numeric functions are essential for summarizing data and performing **statistical analysis** over **monthly sales figures**, allowing creation of quarterly and annual performance insights.

📂 Data is displayed using:

```python
pd.set_option('display.max_rows', None)
pd.set_option('display.max_columns', None)
```


Here is the **Markdown summary** for the **Datetime Functions** section from your **Session 4 notebook**, as referenced in the Table of Contents and confirmed in the code:

---

````markdown
# 📘 Python Session-4 Summary: Datetime Functions

## 🔹 3. DATETIME FUNCTIONS

### 📅 Convert and Extract from Dates
```python
df['Order_Date_Year'] = df['Order_Date'].dt.year
df['Order_Date_Month'] = df['Order_Date'].dt.month
df['Order_Date_Day'] = df['Order_Date'].dt.day
df['Order_Date_Qtr'] = df['Order_Date'].dt.quarter
df['Order_Date_Day_Name'] = df['Order_Date'].dt.strftime('%A')
df['Order_Date_Month_Name'] = df['Order_Date'].dt.strftime('%B')
````

---

### 🕒 Get Today's Date & Time

```python
import datetime as dt
today = dt.datetime.now()
today_date = dt.date.today()
```

---

### 📆 Calculate Date Differences

```python
df['Days_gap'] = (df['Ship_Date'] - df['Order_Date']).dt.days
df['Age'] = dt.datetime.now().year - pd.to_datetime(df['DOB']).dt.year
```

---

### ➕ Add Time Offsets to Dates

```python
from dateutil.relativedelta import relativedelta

df['Add_5_Years'] = pd.to_datetime(df['Order_Date']) + pd.DateOffset(years=5)
df['Add_5_Months'] = pd.to_datetime(df['Order_Date']) + pd.DateOffset(months=5)
df['Add_5_Days'] = pd.to_datetime(df['Order_Date']) + pd.to_timedelta(5, unit='D')
df['Add_5_Qtrs'] = pd.to_datetime(df['Order_Date']) + pd.DateOffset(months=15)
```

---

### 📦 Use of `relativedelta` for Custom Gaps

```python
from datetime import date
from dateutil.relativedelta import relativedelta

initial_date = date(2024, 12, 12)
new_date = initial_date + relativedelta(years=1, months=6, days=10)
```

---

These functions are vital for:

* Extracting features from dates
* Performing age and tenure calculations
* Creating time-based features for time series modeling
* Handling scheduled and delayed operations in datasets

📂 Source Sheet: `'DATETIME FUNCTION TEST'` from Excel file




