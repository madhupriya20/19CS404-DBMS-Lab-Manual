# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

*Syntax:*

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

*Question 1*
--
<img width="1113" height="612" alt="Q1" src="https://github.com/user-attachments/assets/41e57d74-2b83-48f0-8440-d838ac65e0b2" />


```sql
ALTER TABLE Student_details ADD COLUMN State TEXT;
```

*Output:*


<img width="1356" height="321" alt="QA1" src="https://github.com/user-attachments/assets/024ff4bf-f664-42aa-929b-7d8f23dc703f" />


*Question 2*
---

<img width="537" height="173" alt="Q2" src="https://github.com/user-attachments/assets/111ec911-a757-4175-be0f-8b773e3aa6f2" />

```sql
CREATE TABLE Departments(
DepartmentID INTEGER,
DepartmentName TEXT);
```

*Output:*

<img width="1412" height="318" alt="QA2" src="https://github.com/user-attachments/assets/97aa5094-458d-480f-8a5a-4abf4614b1e2" />


*Question 3*
---
<img width="881" height="386" alt="Q3" src="https://github.com/user-attachments/assets/cfe97115-372f-465e-8ca4-9e0b30debf9f" />


```sql
CREATE TABLE item(
item_id TEXT PRIMARY KEY,
item_desc TEXT NOT NULL,
rate INTEGER NOT NULL,
icom_id TEXT(4),
FOREIGN KEY (icom_id) REFERENCES company(com_id)
ON UPDATE CASCADE
ON DELETE CASCADE);
```

*Output:*

<img width="1245" height="327" alt="QA3" src="https://github.com/user-attachments/assets/0879d283-d312-4245-a1e6-c5d1aad224f4" />


*Question 4*
---
<img width="1330" height="483" alt="Q4" src="https://github.com/user-attachments/assets/99f455ff-a3f7-4b52-b54d-0ba96c12c890" />


```sql
CREATE TABLE products(
product_id INTEGER PRIMARY KEY,
product_name TEXT NOT NULL,
list_price DECIMAL(10,2) NOT NULL,
discount DECIMAL(10,2)NOT NULL
DEFAULT 0,
CHECK (list_price >= discount),
CHECK (list_price >= 0),
CHECK (discount >=0 )
);
```

*Output:*

<img width="1185" height="201" alt="QA4" src="https://github.com/user-attachments/assets/2e696cf0-8224-45d2-9186-fb4ba0bbdc1e" />

*Question 5*
---
<img width="1156" height="247" alt="Q5" src="https://github.com/user-attachments/assets/291fd5db-14cf-48cb-9ba4-084e099f7b2e" />


```sql
INSERT INTO Employee (EmployeeID,Name,Position,Department,Salary) VALUES(001,'Sarah Parker','Manager','HR',60000);
```

*Output:*

<img width="1001" height="187" alt="QA5" src="https://github.com/user-attachments/assets/a3e5d7c0-0124-4050-85cf-9c1de6c0e320" />


*Question 6*
---
<img width="837" height="391" alt="Q6" src="https://github.com/user-attachments/assets/b3aa16b5-05ad-43f7-a939-135880128642" />


```sql
INSERT INTO Customers (CustomerID,Name,Address,City,ZipCode) VALUES(302,'Laura Croft','456 Elm St','Seattle','98101');
INSERT INTO Customers (CustomerID,Name,Address,City,ZipCode) VALUES(303,'Bruce Wayne','789 Oak St','Gotham','10001');
```

*Output:*

<img width="1498" height="427" alt="QA6" src="https://github.com/user-attachments/assets/48f3c4f6-e335-43ef-a9a3-5dce95292412" />


*Question 7*
---

<img width="981" height="455" alt="Q7" src="https://github.com/user-attachments/assets/dcc822a0-44e4-425a-b99b-5f386b1eb654" />

```sql
CREATE TABLE item(
item_id TEXT PRIMARY KEY,
item_desc TEXT NOT NULL,
rate INTEGER NOT NULL,
icom_id TEXT(4),
FOREIGN KEY (icom_id) REFERENCES company(com_id)
ON UPDATE SET NULL
ON DELETE SET NULL);
```

*Output:*

<img width="1528" height="386" alt="QA7" src="https://github.com/user-attachments/assets/da5115b7-0e5e-42c9-828f-f2bc88ba1e61" />


*Question 8*
---
<img width="1701" height="368" alt="Q8" src="https://github.com/user-attachments/assets/666b2f1e-c689-483a-bd8d-2da0235d392b" />


```sql
CREATE TABLE contacts(
contact_id INTEGER PRIMARY KEY,
first_name TEXT NOT NULL,
last_name TEXT NOT NULL,
email TEXT,
phone TEXT NOT NULL,
CHECK(LENGTH(phone)>=10)
);
```

*Output:*

<img width="1612" height="238" alt="QA8" src="https://github.com/user-attachments/assets/867efbd2-b639-4fe9-94a4-53dd3c872b67" />


*Question 9*
---
<img width="717" height="227" alt="Q9" src="https://github.com/user-attachments/assets/871c3c91-78ec-4729-9a84-0c916ade81fa" />


```sql
ALTER TABLE student_details
ADD COLUMN Date_of_birth Date;
```

*Output:*

<img width="1102" height="266" alt="QA9" src="https://github.com/user-attachments/assets/2de91c7e-03b9-4e32-85a4-3ada25bcea35" />


*Question 10*
---
<img width="758" height="306" alt="Q10" src="https://github.com/user-attachments/assets/af0f51cb-8821-429c-8bc6-df079e2009fb" />


```sql
INSERT INTO Student_details (RollNo,Name,Gender,Subject,Marks)
SELECT RollNo,Name,Gender,Subject,Marks
FROM Archived_students;
```

*Output:*

<img width="995" height="227" alt="QA10" src="https://github.com/user-attachments/assets/97a4a076-df71-4d5b-91e3-a3f08126bbf3" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
<img width="1111" height="76" alt="image" src="https://github.com/user-attachments/assets/a3ba9268-0c0f-4abf-bb43-84f1d14e3c70" />

