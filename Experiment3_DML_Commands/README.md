# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
<img width="1200" height="611" alt="image" src="https://github.com/user-attachments/assets/17d24c16-afb6-4ddf-ba99-5d14a1617b39" />

```sql
SELECT EmployeeID, FirstName, BirthDate,
       CAST((julianday('2023-12-30') - julianday(BirthDate)) / 365.25 AS INTEGER) AS age
FROM employees
WHERE CAST((julianday('2023-12-30') - julianday(BirthDate)) / 365.25 AS INTEGER) > 50;
```

**Output:**

<img width="955" height="505" alt="image" src="https://github.com/user-attachments/assets/3a367414-0812-4c23-ab30-c6b016934bf1" />

**Question 2**
---
<img width="1193" height="654" alt="image" src="https://github.com/user-attachments/assets/d3c196b6-fc62-4fb9-a734-8f8c4a560255" />

```sql
SELECT product_id,
       discounted_price,
       discount_percentage,
       discounted_price / (1 - discount_percentage) AS original_price
FROM Products;
```

**Output:**

<img width="1151" height="283" alt="image" src="https://github.com/user-attachments/assets/e982bea5-9584-4cd1-a024-8e9f10a1b90c" />

**Question 3**
---

<img width="1169" height="614" alt="image" src="https://github.com/user-attachments/assets/d810f766-b04c-4c33-8e4b-9bea2675ded2" />


```sql
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM orders
WHERE purch_amt BETWEEN 500 AND 4000
  AND purch_amt NOT IN (948.50, 1983.43);
```

**Output:**

<img width="1193" height="485" alt="image" src="https://github.com/user-attachments/assets/71e955a5-b001-4a57-869b-6acdf08bb688" />

**Question 4**
---
<img width="1190" height="586" alt="image" src="https://github.com/user-attachments/assets/312b623c-9166-4fbf-a600-91f7e39dae94" />

```sql
SELECT product_id,
       original_price,
       discount_percentage,
       tax_rate,
       original_price * (1 - discount_percentage) * (1 + tax_rate) AS final_price
FROM Products;
```

**Output:**

<img width="1183" height="382" alt="image" src="https://github.com/user-attachments/assets/199d8bc8-bc06-4414-b982-1e4c92104629" />

**Question 5**
---
<img width="750" height="139" alt="image" src="https://github.com/user-attachments/assets/976c7e28-49a8-4d86-be13-8fe874ccc96f" />

```sql
UPDATE customer
SET grade = 5
WHERE city = 'Chennai';
```

**Output:**

<img width="1204" height="510" alt="image" src="https://github.com/user-attachments/assets/68b189b5-48bb-44d9-9533-69ffcb7b91fb" />

**Question 6**
---
<img width="1202" height="279" alt="image" src="https://github.com/user-attachments/assets/c930f0c2-5edb-49e9-abdc-746874696011" />

```sql
UPDATE products
SET product_name = 'Grapefruit'
WHERE product_id = 4;
```

**Output:**

<img width="1187" height="209" alt="image" src="https://github.com/user-attachments/assets/977dfb7e-3eab-4c95-a987-456a9b8eb289" />

**Question 7**
---
<img width="1190" height="607" alt="image" src="https://github.com/user-attachments/assets/71b801f0-d4c2-4c18-91ac-df311b8296a9" />

```sql
SELECT id,
       base,
       CASE
           WHEN base IS NOT NULL THEN 'Provided'
           ELSE 'Not Provided'
       END AS base_status
FROM Calculations;
```

**Output:**

<img width="1218" height="561" alt="image" src="https://github.com/user-attachments/assets/6d20589f-b436-40aa-b086-d798f8e4375b" />

**Question 8**
---

<img width="1212" height="746" alt="image" src="https://github.com/user-attachments/assets/70b9eafa-fddc-477e-9b9d-b35e0d2078bb" />

```sql
DELETE FROM customer
WHERE GRADE = 2;
```

**Output:**

<img width="848" height="598" alt="image" src="https://github.com/user-attachments/assets/69b9650e-63e9-487f-8306-fb48a4ffd327" />

**Question 9**
---
<img width="1195" height="707" alt="image" src="https://github.com/user-attachments/assets/4f4b408e-730a-4381-aea5-57da35dd0e09" />

```sql
SELECT *
FROM EmployeePosition
WHERE strftime('%Y', DateOfJoining) = '2020';
```

**Output:**

<img width="1204" height="364" alt="image" src="https://github.com/user-attachments/assets/78662594-3289-4883-8900-d0e4bc7192be" />

**Question 10**
---
<img width="1208" height="634" alt="image" src="https://github.com/user-attachments/assets/7a7af19c-fcf6-4c5c-8793-b7df75645c3c" />

```sql
UPDATE employees
SET salary = 8000
WHERE employee_id = 105
  AND salary < 5000;
```

**Output:**

<img width="1182" height="311" alt="image" src="https://github.com/user-attachments/assets/4d26a975-0bfb-4c3e-bcab-1b00ccc105a1" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
