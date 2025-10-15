# 📘 Python Session-5 Summary (Up to Advanced Array Calculation)

## 🔹 1. Introduction to NumPy
- NumPy stands for **Numerical Python**
- Used for efficient numerical computation with arrays and matrices

---

## 🔹 2. NumPy Basics

### ✅ Check Version
```python
import numpy as np
print(np.__version__)
````

---

## 🔹 3. Array Creation and Manipulation

### 📦 Create Arrays

```python
np.array([1, 2, 3])
np.array([[1, 2], [3, 4]])
np.zeros((2, 3))
np.ones((3, 2))
np.arange(0, 12, 2)
```

### 🔄 Reshape Arrays

```python
arr.reshape((2, 3))
```

---

## 🔹 4. Array Data Types

### 🧪 Specify and Convert Data Types

```python
arr = np.array([1, 2, 3], dtype=np.float64)
arr.astype(np.int64)
arr.dtype
```

---

## 🔹 5. Array Operations

### ➕ Element-wise Arithmetic

```python
a + b
a - b
a * b
a / b
```

---

## 🔹 6. Looping Concepts

### 🔁 For Loop and While Loop

```python
for i in arr: print(i)
while i < len(arr): print(arr[i])
```

---

## 🔹 7. Looping to Generate Lists

### 📈 Loop 1 to 10 and Store in List

```python
x = []
for i in range(1, 11):
    x.append(i)
```

---

## 🔹 8. Looping for Calculations

### 🔽 Backward Loop (1000 to 100)

```python
for i in range(1000, 0, -100):
    ...
```

### 🔼 Forward Loop (100 to 1000)

```python
for i in range(100, 1100, 100):
    ...
```

---

## 🔹 9. Compound Interest Calculation

### 💰 Logic:

```python
capital += capital * interest_rate
```

Loop over years and append yearly result to list → DataFrame

---

## 🔹 10. Investment Calculations

### 💵 Fixed Deposits

Loop for fixed return on same capital

### 💸 Recurring Deposits

Loop for monthly contributions and interest accumulation

---

## 🔹 11. Loop Breaks / Control Flow

* `break`, `continue`, custom "do while" style using `while True`

---

## 🔹 12. Currency Format

### 💲 Format Numbers

```python
f"${value:,.2f}"
```

---

## 🔹 13. Nested Loops

### ⏹️ Loop inside loop for multi-step calculations

---

## 🔹 14. Advanced Array Calculation

### ➕ Add constant to entire array

```python
sales = np.array([...])
sales + 100
```

---



## 🔹 15. 🧮 Linear Algebra

### 🔢 Matrix Operations
```python
matrix_a = np.array([[1, 2], [3, 4]])
matrix_b = np.array([[5, 6], [7, 8]])

# Dot product
np.dot(matrix_a, matrix_b)

# Transpose
matrix_a.T
````

---

## 🔹 16. 🧠 NumPy in Practice

### 🛠 Handling Missing Data

```python
array_with_nan = np.array([1, 2, np.nan, 4])
array_without_nan = np.nan_to_num(array_with_nan, nan=0)
```

---

## 🔹 17. 💾 Input and Output

### 📥 Save/Load Arrays

```python
np.savetxt('array.txt', array_to_save)
np.loadtxt('array.txt')
```

---

## 🔹 18. 📊 Charts and Visualization

### 📘 Dataset: `MED_STORE_2022.xlsx`, Sheet: `MED_AUS_DATA`

Group by `STATE_CODE` and count `CUSTOMER_ID` to get `SUBS`.

---

### 📈 Vertical Bar Chart

```python
plt.bar(df['STATE_CODE'], df['SUBS'])
plt.xlabel('STATES')
plt.ylabel('SUBS')
plt.title('STATE WISE SUBSCRIBER')
plt.show()
```

---

### 📉 Horizontal Bar Chart

```python
plt.barh(df['STATE_CODE'], df['SUBS'])
plt.xlabel('SUBS')
plt.ylabel('STATES')
plt.title('STATE WISE SUBSCRIBER')
plt.show()
```

---

### 🥧 Pie Chart

```python
plt.pie(SUBS, labels=STATES, autopct='%1.1f%%', startangle=140)
plt.title('STATE WISE SUBS RATE')
plt.show()
```

---

### 🧿 3D Pie Chart (Exploded Slice)

```python
explode = (0.1, 0, 0, 0)
plt.pie(Runs, explode=explode, labels=Players, autopct='%1.1f%%',
        shadow=True, startangle=90)
plt.axis('equal')
plt.show()
```

---

### 📉 Line Chart

```python
plt.plot(df['Date'], df['Value_A'], marker='o', label='Value A')
plt.plot(df['Date'], df['Value_B'], marker='o', label='Value B')
plt.legend()
plt.grid(True)
plt.show()
```

---

### 🌡️ Heatmap

```python
sns.heatmap(df, annot=True, cmap='YlGnBu', linewidths=0.5, linecolor='gray')
plt.title('Heatmap using Seaborn')
```




