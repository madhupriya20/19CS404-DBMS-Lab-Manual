# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
<img width="959" height="454" alt="image" src="https://github.com/user-attachments/assets/f8bc0fc8-f75c-4563-b037-cc09d911ea35" />


```sql
SELECT 
    strftime('%Y-%m', date) AS Month,
    COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY strftime('%Y-%m', date)
ORDER BY Month;
```

**Output:**

<img width="555" height="474" alt="image" src="https://github.com/user-attachments/assets/aa565819-1544-4fb9-b314-3ea96912398b" />


**Question 2**
---
<img width="1018" height="434" alt="image" src="https://github.com/user-attachments/assets/14672bb7-7101-4eb4-8506-73c685da2f5c" />


```sql
select Diagnosis ,count(*) as DiagnosisCount
from MedicalRecords
group by Diagnosis
order by DiagnosisCount desc
limit 1;
```

**Output:**

<img width="861" height="405" alt="image" src="https://github.com/user-attachments/assets/5909b48f-e0e3-4ee7-8016-178c7a3cea6a" />


**Question 3**
---
<img width="528" height="513" alt="image" src="https://github.com/user-attachments/assets/f236d50b-9189-47d1-8438-0b8f5c259592" />


```sql
SELECT 
    strftime('%Y', ValidityPeriod) AS ValidityYear,
    COUNT(DISTINCT PatientID) AS TotalPatients
FROM Insurance
GROUP BY strftime('%Y', ValidityPeriod)
ORDER BY ValidityYear;
```

**Output:**

<img width="628" height="435" alt="image" src="https://github.com/user-attachments/assets/07d9f83a-11e0-40ff-b38c-53aac698c5f5" />


**Question 4**
---
<img width="866" height="472" alt="image" src="https://github.com/user-attachments/assets/a779a299-9062-43e2-9b33-5efc32a01685" />


```sql
SELECT COUNT(*) AS COUNT
FROM customer
WHERE city <> 'Noida';
```

**Output:**

<img width="409" height="364" alt="image" src="https://github.com/user-attachments/assets/1ee15f88-0250-4b27-82ef-570283552aab" />


**Question 5**
---
<img width="1085" height="449" alt="image" src="https://github.com/user-attachments/assets/c95c7b31-dfe5-496b-989f-a296922d20b8" />


```sql
SELECT SUM(CAST(workhour AS INTEGER)) AS "Total working hours"
FROM employee1;
```

**Output:**

<img width="491" height="358" alt="image" src="https://github.com/user-attachments/assets/1ea1347d-b80e-4887-bbda-7aaffb644160" />


**Question 6**
---
<img width="574" height="465" alt="image" src="https://github.com/user-attachments/assets/9862c774-d698-47b3-9621-f0992c01cfdb" />


```sql
SELECT COUNT(*) AS employees_in_california
FROM employee
WHERE city = 'California';
```

**Output:**

<img width="579" height="354" alt="image" src="https://github.com/user-attachments/assets/77e44125-ed94-452f-aa36-8537b5013301" />


**Question 7**
---
<img width="672" height="423" alt="image" src="https://github.com/user-attachments/assets/bb0d5714-a6bc-4a1d-8f3b-eaf578330e3e" />


```sql
SELECT AVG(LENGTH(email)) AS avg_email_length
FROM customer;
```

**Output:**

<img width="410" height="337" alt="image" src="https://github.com/user-attachments/assets/02074e0c-130d-4a25-8e26-f074c893d884" />


**Question 8**
---
<img width="1218" height="452" alt="image" src="https://github.com/user-attachments/assets/b151faf2-25dd-4a6b-af7c-f085998236d0" />


```sql
SELECT 
    category_id, 
    COUNT(product_name) AS "count(product_name)"
FROM products
GROUP BY category_id
HAVING MIN(category_id) < 3;
```

**Output:**

<img width="696" height="392" alt="image" src="https://github.com/user-attachments/assets/d1938a24-0eae-4a46-adf8-e74b9ceaf5f4" />


**Question 9**
---
<img width="1215" height="435" alt="image" src="https://github.com/user-attachments/assets/884c8668-9d92-40f0-b84c-da630a8a93d6" />


```sql
SELECT 
    category_id, 
    COUNT(product_name) AS COUNT
FROM products
WHERE category_id > 2
GROUP BY category_id;
```

**Output:**

<img width="587" height="381" alt="image" src="https://github.com/user-attachments/assets/b41cb5f1-54e4-4265-9991-c0bafdffb7e9" />


**Question 10**
---
<img width="1225" height="507" alt="image" src="https://github.com/user-attachments/assets/c6ac1678-cb0b-4c6b-a117-5c84e66da2ca" />


```sql
SELECT 
    occupation, 
    SUM(workhour) AS "SUM(workhour)"
FROM employee1
GROUP BY occupation
HAVING SUM(workhour) > 20;
```

**Output:**

<img width="595" height="488" alt="image" src="https://github.com/user-attachments/assets/8d9fc8a3-961a-459a-965a-8fc92200d3ee" />




## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.

<img width="1265" height="110" alt="Screenshot 2025-10-27 150429" src="https://github.com/user-attachments/assets/16bfef77-31ff-4028-a0fa-d20e79278cb1" />






