# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
<img width="1159" height="378" alt="image" src="https://github.com/user-attachments/assets/c28cb243-e790-4f50-b0a5-e44a60a2585f" />

```sql
ALTER TABLE Student_details ADD COLUMN ParentsNumber number;
ALTER TABLE Student_details ADD COLUMN Adhar_Number number;
```

**Output:**

<img width="1214" height="449" alt="Screenshot 2025-09-29 133608" src="https://github.com/user-attachments/assets/a6c12364-7193-4678-9ec7-bbd383983257" />

**Question 2**
---
<img width="1173" height="251" alt="image" src="https://github.com/user-attachments/assets/0a5ee193-ce82-4c43-8698-81327e32ea4c" />

```sql
INSERT INTO Books (ISBN, Title, Author, Publisher, Year)
VALUES ('978-1234567890', 'Data Science Essentials', 'Jane Doe', 'TechBooks', 2024);
```

**Output:**

<img width="1197" height="313" alt="image" src="https://github.com/user-attachments/assets/a4b75bb3-7975-4fa4-8444-c7c597ddca88" />

**Question 3**
---
<img width="1223" height="435" alt="image" src="https://github.com/user-attachments/assets/2637b3d6-2e35-4a93-9963-5632122e87b1" />

```sql
CREATE TABLE Invoices (
    InvoiceID INTEGER PRIMARY KEY,
    InvoiceDate DATE NOT NULL,
    Amount REAL CHECK (Amount > 0),
    DueDate DATE CHECK (DueDate > InvoiceDate),
    OrderID INTEGER,
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
);
```

**Output:**

<img width="1207" height="369" alt="image" src="https://github.com/user-attachments/assets/0477d084-a4f6-4ccd-845b-d6f36ba1060e" />

**Question 4**
---
<img width="1209" height="419" alt="image" src="https://github.com/user-attachments/assets/0056fdd1-e0fd-478f-b6ba-db7d7c8abf19" />

```sql
CREATE TABLE item (
    item_id TEXT PRIMARY KEY,
    item_desc TEXT NOT NULL,
    rate INTEGER NOT NULL,
    icom_id TEXT CHECK (length(icom_id) = 4),
    FOREIGN KEY (icom_id) REFERENCES company(com_id)
        ON UPDATE SET NULL
        ON DELETE SET NULL
);
```

**Output:**

<img width="1057" height="461" alt="image" src="https://github.com/user-attachments/assets/b59ede12-bc83-464b-8c9c-28cbe107d27c" />

**Question 5**
---
<img width="711" height="341" alt="image" src="https://github.com/user-attachments/assets/316bc88f-eac6-41c3-af79-55d0b007dd45" />

```sql
INSERT INTO Employee (EmployeeID, Name, Department, Salary)
SELECT EmployeeID, Name, Department, Salary
FROM Former_employees;
```

**Output:**

<img width="1223" height="361" alt="image" src="https://github.com/user-attachments/assets/ac294f47-eb9d-4b43-a882-428ca446c223" />

**Question 6**
---
<img width="930" height="446" alt="image" src="https://github.com/user-attachments/assets/b3e9784b-00a6-4bd0-b91a-7a9d82bf6bba" />

```sql
CREATE TABLE Products (
    ProductID INTEGER,
    ProductName TEXT,
    Price REAL,
    Stock INTEGER
);
```

**Output:**

<img width="1214" height="377" alt="image" src="https://github.com/user-attachments/assets/15ccd23f-5b83-4370-9ef4-4b78b44363a0" />

**Question 7**
---
<img width="1226" height="413" alt="image" src="https://github.com/user-attachments/assets/75d22694-3504-4701-b49b-cb1128c75ef6" />

```sql
CREATE TABLE Attendance (
    AttendanceID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    AttendanceDate DATE,
    Status TEXT CHECK (Status IN ('Present', 'Absent', 'Leave')),
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
);
```

**Output:**

<img width="1203" height="367" alt="image" src="https://github.com/user-attachments/assets/24dfdef5-baa4-443f-9fe6-79163fcd9577" />

**Question 8**
---
<img width="1206" height="509" alt="image" src="https://github.com/user-attachments/assets/58f332c2-d88b-404e-9dcb-6565778816f8" />

```sql
INSERT INTO Customers (CustomerID, Name, Address, City, ZipCode)
VALUES (306, 'Diana Prince', 'Themyscira', NULL, NULL);

INSERT INTO Customers (CustomerID, Name, Address, City, ZipCode)
VALUES (307, 'Bruce Wayne', 'Wayne Manor', 'Gotham', '10007');

INSERT INTO Customers (CustomerID, Name, Address, City, ZipCode)
VALUES (308, 'Peter Parker', 'Queens', NULL, '11375');
```

**Output:**

<img width="1215" height="358" alt="image" src="https://github.com/user-attachments/assets/3ce85555-9fdf-4c36-a182-4474460e9a6d" />

**Question 9**
---
<img width="821" height="359" alt="image" src="https://github.com/user-attachments/assets/f596d3b3-6fc6-4af0-b123-69828a06d395" />

```sql
CREATE TABLE Products (
    ProductID INTEGER PRIMARY KEY,
    ProductName TEXT NOT NULL,
    Price REAL CHECK (Price > 0),
    Stock INTEGER CHECK (Stock >= 0)
);
```

**Output:**

<img width="1209" height="353" alt="image" src="https://github.com/user-attachments/assets/ec18232b-c9ea-4b16-9af2-c4a7393f01f6" />

**Question 10**
---
<img width="1001" height="334" alt="image" src="https://github.com/user-attachments/assets/e939cc3a-fc03-46d6-8436-713524a95dd9" />

```sql
ALTER TABLE Customers ADD COLUMN email TEXT;
```

**Output:**

<img width="1216" height="363" alt="image" src="https://github.com/user-attachments/assets/3150ccd3-adcc-4802-95b1-48319cd19d48" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
