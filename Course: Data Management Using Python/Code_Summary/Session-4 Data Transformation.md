# 📘 Python Session-4 Full Notebook Summary

## 🔹 Topic: Python Functions

### 1. 🅰️ Character/String Functions

#### 🔠 Convert Case
```python
df['col'].str.upper()
df['col'].str.lower()
df['col'].str.title()
````

#### 🔗 Concatenate Fields

```python
df['Full_Address'] = df['State'] + '-' + df['District'] + '-' + df['Area_Name']
```

#### 🔍 Find Character Position

```python
df['index'] = df['Customer_Name'].str.index(' ')
df['find'] = df['Customer_Name'].str.find(' ')
```

#### ✂️ Extract First and Last Names

```python
# Using index
df['Delimiter_position'] = df['Customer_Name'].apply(lambda x: x.index(' '))
df['First_Name'] = df.apply(lambda x: x['Customer_Name'][:x['Delimiter_position']], axis=1)
df['Last_Name'] = df.apply(lambda x: x['Customer_Name'][x['Delimiter_position']+1:], axis=1)

# Using split
df['First_Name'] = df['Customer_Name'].apply(lambda x: x.split(' ')[0])
df['Last_Name'] = df['Customer_Name'].apply(lambda x: x.split(' ')[1])
```

#### 🔁 Replace Characters

```python
string.replace('old', 'new')
df['Gender'] = df['Gender'].replace('M', 'Male').replace('F', 'Female')
```

#### 🔢 Length and Name Splits

```python
len('Full Name')

first, middle, last = full_name.split(' ')
first, middle, last = full_name.split('-')
first, middle, last = full_name.split('_')
```

---

### 2. 🔢 Numeric Functions

#### 🧮 Calculations and Formatting

```python
df['Discounted_amount'] = df['Sales'] * df['Discount']
df['Sales_After_Discount'] = df['Sales'] - df['Discounted_amount']
df['Profit_Margin'] = df['Profit'] / df['Sales_After_Discount']
```

#### 💲 Format Currency and Percentages

```python
df['Sales'] = df['Sales'].apply(lambda x: f"${x:,.2f}")
df['Discount'] = df['Discount'].apply(lambda x: f"{x:.2%}")
df['Profit'] = df['Profit'].apply(lambda x: f"${x:,.2f}")
df['Profit_Margin'] = df['Profit_Margin'].apply(lambda x: f"{x:.2%}")
```

---

### 3. 📆 Datetime Functions

#### 📊 Extract Components

```python
df['Year'] = df['Order_Date'].dt.year
df['Month'] = df['Order_Date'].dt.month
df['Day'] = df['Order_Date'].dt.day
df['Quarter'] = df['Order_Date'].dt.quarter
df['Weekday'] = df['Order_Date'].dt.strftime("%A")
df['Month_Name'] = df['Order_Date'].dt.strftime("%B")
```

#### 📉 Date Differences

```python
df['Days_gap'] = (df['Ship_Date'] - df['Order_Date']).dt.days
df['Age'] = datetime.now().year - pd.to_datetime(df['DOB']).dt.year
```

#### ➕ Add Offsets to Dates

```python
df['Add_5_Years'] = pd.to_datetime(df['Order_Date']) + pd.DateOffset(years=5)
df['Add_5_Months'] = pd.to_datetime(df['Order_Date']) + pd.DateOffset(months=5)
df['Add_5_Days'] = pd.to_datetime(df['Order_Date']) + pd.to_timedelta(5, unit='D')
df['Add_5_Qtrs'] = pd.to_datetime(df['Order_Date']) + pd.DateOffset(months=15)
```

#### 🧮 Relativedelta Example

```python
from datetime import date
from dateutil.relativedelta import relativedelta

initial_date = date(2024, 12, 12)
new_date = initial_date + relativedelta(days=10)
print(new_date)
```
