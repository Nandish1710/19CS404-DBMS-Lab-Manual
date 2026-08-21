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

<img width="1221" height="275" alt="image" src="https://github.com/user-attachments/assets/394a3f6c-767d-4cdc-bfa0-4a3cfc177b02" />


```sql
INSERT INTO Products (ProductID, Name, Category)
VALUES (104, 'Tablet', 'Electronics');
```

**Output:**

<img width="1228" height="257" alt="image" src="https://github.com/user-attachments/assets/4293bcd7-4f87-4bb1-946e-302bff312910" />

**Question 2**
---

<img width="977" height="402" alt="image" src="https://github.com/user-attachments/assets/73b4b94c-b73a-4d70-bf12-c11f15580877" />

```sql
 CREATE TABLE Tasks (
    TaskID INTEGER,
    TaskName TEXT,
    DueDate DATE
);
```

**Output:**
<img width="1205" height="372" alt="image" src="https://github.com/user-attachments/assets/b3a88eee-a492-44dc-9f00-5188e04d7130" />

**Question 3**
---

<img width="1072" height="582" alt="image" src="https://github.com/user-attachments/assets/2851bbc0-c5c6-4113-a018-1509be957981" />

```sql
ALTER TABLE Student_details
ADD COLUMN Country TEXT;
```

**Output:**


<img width="1192" height="355" alt="image" src="https://github.com/user-attachments/assets/176c1a47-3034-4efd-b49f-50513849243a" />

**Question 4**
---

<img width="1202" height="492" alt="image" src="https://github.com/user-attachments/assets/8829a12e-ae2b-4fe0-b997-e56d3e5131ed" />

```sql
INSERT INTO Student_details (RollNo, Name, Gender, Subject, MARKS)
VALUES (205, 'Olivia Green', 'F', NULL, NULL);

INSERT INTO Student_details (RollNo, Name, Gender, Subject, MARKS)
VALUES (207, 'Liam Smith', 'M', 'Mathematics', 85);

INSERT INTO Student_details (RollNo, Name, Gender, Subject, MARKS)
VALUES (208, 'Sophia Johnson', 'F', 'Science', NULL);
```

**Output:**


<img width="1172" height="237" alt="image" src="https://github.com/user-attachments/assets/0cceb5bc-6ef2-4b78-850d-18c7d3c2be77" />

**Question 5**
---

<img width="1216" height="435" alt="image" src="https://github.com/user-attachments/assets/973b11b3-c680-4606-93b6-9265dfd095ae" />

```sql
CREATE TABLE Employees (
    EmployeeID INTEGER PRIMARY KEY,
    FirstName TEXT NOT NULL,
    LastName TEXT NOT NULL,
    Email TEXT UNIQUE,
    Salary REAL CHECK (Salary > 0),
    DepartmentID INTEGER,
    FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);
```

**Output:**


<img width="1061" height="390" alt="image" src="https://github.com/user-attachments/assets/9c7c8b98-2ba3-4130-83b4-bbf401eb6837" />

**Question 6**
---

<img width="1227" height="426" alt="image" src="https://github.com/user-attachments/assets/964466df-3e0e-4680-bd9d-0cb759ae25b0" />

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


<img width="1201" height="266" alt="image" src="https://github.com/user-attachments/assets/cea972b0-9f38-4703-b90d-583f42bbd8ab" />

**Question 7**
---

<img width="1190" height="591" alt="image" src="https://github.com/user-attachments/assets/74901775-1438-465b-9fc2-7a25815cd0d9" />

```sql
ALTER TABLE customer
ADD COLUMN birth_date timestamp;
```

**Output:**


<img width="1192" height="373" alt="image" src="https://github.com/user-attachments/assets/a3e537ea-42a6-424a-99cd-9bd8bb90f8c5" />

**Question 8**
---

<img width="937" height="358" alt="image" src="https://github.com/user-attachments/assets/1e373c1a-3684-42fd-b0fb-98e59c97e0dc" />

```sql
CREATE TABLE Invoices (
    InvoiceID INTEGER PRIMARY KEY,
    InvoiceDate DATE,
    DueDate DATE CHECK (DueDate > InvoiceDate),
    Amount REAL CHECK (Amount > 0)
);
```

**Output:**

 <img width="1192" height="302" alt="image" src="https://github.com/user-attachments/assets/9e7c94f6-fc45-44ed-86a9-7fc0f253259f" />

**Question 9**
---

<img width="922" height="427" alt="image" src="https://github.com/user-attachments/assets/400f5640-367f-4349-a24c-844918379292" />

```sql
CREATE TABLE Products (
    ProductID INTEGER,
    ProductName TEXT,
    Price REAL,
    Stock INTEGER
);
```

**Output:**

<img width="1213" height="318" alt="image" src="https://github.com/user-attachments/assets/2831b260-6524-47ca-848c-09c985d40be8" />

**Question 10**
---

<img width="995" height="467" alt="image" src="https://github.com/user-attachments/assets/ee847a38-a311-4f19-b98b-3c020dcce1c6" />

```sql
INSERT INTO Student_details
VALUES
(202, 'Ella King', 'F', 'Chemistry', 87),
(203, 'James Bond', 'M', 'Literature', 78);
```

**Output:**


<img width="1205" height="273" alt="image" src="https://github.com/user-attachments/assets/cfb6430f-5c00-462b-a3f8-fa9baa9d7c75" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
