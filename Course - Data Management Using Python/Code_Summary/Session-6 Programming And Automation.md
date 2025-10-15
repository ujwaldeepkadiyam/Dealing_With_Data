# 📘 Python Session-6 Summary

## 1️⃣ SYSTEM DEFINED FUNCTIONS vs USER DEFINED FUNCTIONS

### 📊 System Defined (Built-in) Functions
Use pandas to compute:
```python
df['total'] = df[months].sum(axis=1)
df['avg']   = df[months].mean(axis=1)
df['min']   = df[months].min(axis=1)
df['max']   = df[months].max(axis=1)
````

### 👨‍💻 User Defined Functions

```python
from statistics import mean, stdev

def sum_all(row): return sum(row[months])
def mean_all(row): return mean(row[months])
def min_all(row): return min(row[months])
def max_all(row): return max(row[months])
def std_all(row): return stdev(row[months])

df['total'] = df.apply(sum_all, axis=1)
df['avg']   = df.apply(mean_all, axis=1)
df['std']   = df.apply(std_all, axis=1)
```

---

## 2️⃣ LAMBDA FUNCTIONS

* One-line, anonymous function for quick logic

```python
df['QTR1'] = df[['Jan','Feb','Mar']].sum(axis=1)
df['RESULT'] = df['QTR1'].apply(lambda x: 'PASS' if x >= 300 else 'FAIL')
```

---

## 3️⃣ GLOBAL vs LOCAL VARIABLES

### 🔁 Example

```python
x = 10  # global
def func():
    x = 5  # local
    return x
```

---

## 4️⃣ RANKING METHODS

### 📊 Rank vs Dense Rank

```python
df['rank'] = df['sales'].rank(method='min', ascending=False)
df['dense_rank'] = df['sales'].rank(method='dense', ascending=False)
```

* Rank can skip numbers; Dense rank does not.

---

## 5️⃣ ROW LEVEL AGGREGATION (Partition-Like)

### SQL-style group-wise metrics

```python
df['city_total'] = df.groupby('CITY')['SALES'].transform('sum')
df['city_avg']   = df.groupby('CITY')['SALES'].transform('mean')
df['city_min']   = df.groupby('CITY')['SALES'].transform('min')
df['city_max']   = df.groupby('CITY')['SALES'].transform('max')
```

---

## 6️⃣ CUMULATIVE CALCULATIONS

### ➕ Cumulative Sum

```python
df['CUM_SALES'] = df.groupby('CITY')['SALES'].cumsum()
```

---

## 7️⃣ LEAD AND LAG CALCULATION

### ⏪ LAG Function
Retrieve **previous row's** value within a group:
```python
df['PREVIOUS_VISIT_DATE'] = df.groupby(['RESTAURANT', 'CUST_NAME'])['VISITS_DATE'].shift(1)
````

### ⏩ LEAD Function

Retrieve **next row's** value within a group:

```python
df['NEXT_VISIT_DATE'] = df.groupby(['RESTAURANT', 'CUST_NAME'])['VISITS_DATE'].shift(-1)
```

Used to compare customer behavior over time.

---

## 8️⃣ USE OF `FIRST.` AND `LAST.` (SAS-style logic in pandas)

### 📍 Flagging First and Last Record in Group

```python
df['start'] = df.groupby('STU_NAME').cumcount() == 0
df['end']   = df.groupby('STU_NAME').cumcount(ascending=False) == 0
```

* Convert to integer flags: `1` for True, `0` for False

---

## 9️⃣ SELECTING THE FIRST VALUE OF GROUPED VARIABLE

```python
df_first = df.groupby('STU_NAME').first().reset_index()
```

## 🔟 SELECTING THE LAST VALUE OF GROUPED VARIABLE

```python
df_last = df.groupby('STU_NAME').last().reset_index()
```

Used to simulate SQL/SAS-style first/last row behavior within groups.

---

Here is the **Markdown summary** for your **Session 6 notebook**, covering from **“12. How to Go for Month Back Calculations”** to the end:

---

````markdown
# 📘 Python Session-6 Summary (Final Sections)

---

## 12️⃣ HOW TO GO FOR MONTH BACK CALCULATIONS

### 🕓 Pull Records from Past 6 Months
```python
from datetime import datetime, timedelta

end_date = datetime.now()
start_date = end_date - timedelta(days=6*30)  # Approximate 6 months

df_last_6_months = df[(df['date'] >= start_date) & (df['date'] <= end_date)]
````

### 🕓 Pull Records from Past 12 Months

```python
start_date = end_date - timedelta(days=12*30)  # Approximate 12 months

df_last_12_months = df[(df['date'] >= start_date) & (df['date'] <= end_date)]
```

---

## 13️⃣ HOW TO SCHEDULE THE PYTHON PROGRAM

### 🛠 Install Scheduler

```bash
pip install schedule
```

### 🕒 Example: Schedule Every 5 Seconds

```python
import schedule
import time

def run_code():
    print("DV Analytics...")

schedule.every(5).seconds.do(run_code)

while True:
    schedule.run_pending()
    time.sleep(1)
```

### 🗓 Schedule Daily at Specific Time

```python
schedule.every().day.at("11:55").do(run_report)
```

---

## 14️⃣ HOW TO SCHEDULE A MACRO PROGRAM TO RUN AND EMAIL REPORTS

### 📝 Save DataFrame to Excel

```python
df.to_excel('report.xlsx', index=False)
```

### 📧 Send Report via Email

```python
import smtplib
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText
from email.mime.application import MIMEApplication

msg = MIMEMultipart()
msg['From'] = sender_email
msg['To'] = receiver_email
msg['Subject'] = 'Your Daily Report'
msg.attach(MIMEText(body))

with open('report.xlsx', 'rb') as f:
    part = MIMEApplication(f.read(), Name='report.xlsx')
    part['Content-Disposition'] = 'attachment; filename="report.xlsx"'
    msg.attach(part)

with smtplib.SMTP(smtp_server, smtp_port) as server:
    server.starttls()
    server.login(smtp_user, smtp_password)
    server.send_message(msg)
```

> Replace placeholders (`smtp.example.com`, credentials, emails) with your real values.

---



