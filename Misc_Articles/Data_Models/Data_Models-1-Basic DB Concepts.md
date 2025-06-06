---

# 🧱 1. Basic Database Concepts

These are essential even if you’re working mainly in Python (e.g., with Pandas or SQL-based workflows).

---

## 📦 What is a Database?

A **database** is an organized collection of structured data, typically stored electronically in a computer system.

* A **Database Management System (DBMS)** allows users to create, read, update, and delete data in a database.
* Examples: MySQL, PostgreSQL, SQLite, Microsoft SQL Server.

---

## 📊 Tables, Rows, and Columns

A **table** is a collection of related data entries, organized in **rows** and **columns**.

### Example:

| ID | Name    | Age |
| -- | ------- | --- |
| 1  | Alice   | 25  |
| 2  | Bob     | 30  |
| 3  | Charlie | 28  |

* **Columns** define data types (e.g., ID: Integer, Name: String).
* **Rows** are individual records (e.g., a person’s data).

---

## 🔑 Primary Key

A **primary key** uniquely identifies each row in a table.

* Must be **unique** and **not null**.
* Each table should have one primary key.

### Example:

| **StudentID** (PK) | Name  | Age |
| ------------------ | ----- | --- |
| 101                | Ravi  | 22  |
| 102                | Seema | 23  |

---

## 🔗 Foreign Key

A **foreign key** is a column in one table that links to the **primary key** of another table. It creates relationships between tables.

### Example:

**Students Table**

| StudentID | Name  |
| --------- | ----- |
| 101       | Ravi  |
| 102       | Seema |

**Enrollments Table**

| EnrollmentID | StudentID (FK) | Course  |
| ------------ | -------------- | ------- |
| 1            | 101            | Math    |
| 2            | 102            | Physics |

Here, `StudentID` in **Enrollments** is a **foreign key** referring to `StudentID` in **Students**.

---

## 🔄 Relationships Between Tables

### 1️⃣ One-to-One

Each record in Table A is linked to **only one** record in Table B, and vice versa.

#### Example:

**Person Table**

| PersonID | Name   |
| -------- | ------ |
| 1        | Ramesh |

**Passport Table**

| PassportID | PersonID (FK) | PassportNumber |
| ---------- | ------------- | -------------- |
| 201        | 1             | IN123456       |

---

### 2️⃣ One-to-Many

One record in Table A is linked to **many** records in Table B.

#### Example:

**Department Table**

| DeptID | DeptName |
| ------ | -------- |
| 1      | HR       |

**Employee Table**

| EmpID | Name  | DeptID (FK) |
| ----- | ----- | ----------- |
| 1     | Anil  | 1           |
| 2     | Sunil | 1           |

Here, one department has many employees.

---

### 3️⃣ Many-to-One

Many records in Table A relate to **one** record in Table B.

> This is just the reverse view of one-to-many.

**Example above still applies**: Many employees → One department.

---

### 4️⃣ Many-to-Many

Records in Table A can be linked to **many** records in Table B, and vice versa.

#### Example:

**Students Table**

| StudentID | Name  |
| --------- | ----- |
| 1         | Ravi  |
| 2         | Seema |

**Courses Table**

| CourseID | CourseName |
| -------- | ---------- |
| 101      | Math       |
| 102      | Science    |

**Enrollments Table (Join Table)**

| StudentID (FK) | CourseID (FK) |
| -------------- | ------------- |
| 1              | 101           |
| 1              | 102           |
| 2              | 101           |

---

## 🧹 Normalization

**Normalization** is the process of organizing data to:

* Remove redundancy
* Ensure data integrity

### Normal Form Examples:

* **1NF**: Atomic values (no multiple values in one cell)
* **2NF**: Remove partial dependency
* **3NF**: Remove transitive dependency

---

## 🔄 Denormalization

**Denormalization** is the process of combining tables to reduce **joins** and improve **read performance**, often at the cost of redundancy.

### Example:

Instead of separate **Employee** and **Department** tables, we merge them:

| EmpID | Name  | DeptName |
| ----- | ----- | -------- |
| 1     | Anil  | HR       |
| 2     | Sunil | HR       |

Now, `DeptName` is repeated—but it's faster to read.


