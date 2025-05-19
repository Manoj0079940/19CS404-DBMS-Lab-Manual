# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
![image](https://github.com/user-attachments/assets/1b38173c-1cd7-4a97-bed8-85f061d01a31)
```
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.city AS "city",
    s.commission
FROM 
    customer c
JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    c.city <> s.city
    AND s.commission > 0.12;
```

**Output:**

![image](https://github.com/user-attachments/assets/0b60968f-a341-42e4-a3a3-60098f2165ff)


**Question 2**
![image](https://github.com/user-attachments/assets/e0822b51-ec48-45b9-a806-a6cb287bf8f8)
```
SELECT DISTINCT c.cust_name
FROM customer c
LEFT JOIN orders o ON c.customer_id = o.customer_id AND o.purch_amt < 100
WHERE o.purch_amt IS NOT NULL;
```
**Output:**

![image](https://github.com/user-attachments/assets/7b3292e0-64da-456d-baed-376b8ddc2c00)

**Question 3**
![image](https://github.com/user-attachments/assets/7041c45f-86f8-4499-b9b4-edc60f303cd0)
```
SELECT 
    s.name AS Salesman,
    c.cust_name,
    s.city
FROM 
    salesman AS s
INNER JOIN 
    customer AS c
ON 
    s.city = c.city;
```


**Output:**

![image](https://github.com/user-attachments/assets/60909471-9819-4e9d-9e5e-5ba4c175d309)

**Question 4**
![image](https://github.com/user-attachments/assets/dce86330-d1c5-4632-9d6d-926724c92a05)
```
SELECT 
    s.name
FROM 
    salesman AS s
LEFT JOIN 
    customer AS c
ON 
    s.salesman_id = c.salesman_id
WHERE 
    c.city = 'London';
```

**Output:**

![image](https://github.com/user-attachments/assets/9a3a30a8-dc3d-4893-966b-d0c5c6b8c35b)


**Question 5**
![image](https://github.com/user-attachments/assets/ac79d6f9-f2c8-4b5c-8309-f6e161bd7daf)

```
SELECT 
    p.first_name AS patient_name, 
    d.first_name AS doctor_name
FROM 
    patients AS p
INNER JOIN 
    doctors AS d
ON 
    p.doctor_id = d.doctor_id
WHERE 
    p.date_of_birth > '1990-01-01';
```
**Output:**
![image](https://github.com/user-attachments/assets/cf389ca4-98f0-4e17-89f0-4afcd37a9646)


**Question 6**
![image](https://github.com/user-attachments/assets/c0fdba46-103d-4fb4-9eb5-14b35f8e4f09)
```
SELECT 
    c.cust_name, 
    o.ord_no, 
    o.ord_date, 
    o.purch_amt
FROM 
    customer AS c
LEFT JOIN 
    orders AS o
ON 
    c.customer_id = o.customer_id
WHERE 
    o.purch_amt > 1000;
```

**Output:**

![image](https://github.com/user-attachments/assets/37d79d0b-3a74-43d2-a1ec-1902d5bfe9d7)


**Question 7**
![image](https://github.com/user-attachments/assets/f68447ed-4631-4eb5-ba30-c8ede0be0bbe)
```
SELECT 
    c.*
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
WHERE 
    o.ord_date > '2012-08-17';
```

**Output:**

![image](https://github.com/user-attachments/assets/d24f7bf2-3be7-4dd9-86f3-6ec81b755bca)

**Question 8**
![image](https://github.com/user-attachments/assets/91ec6896-eb65-4c79-a016-94e94965c753)
```
SELECT 
    p.date_of_birth, 
    a.*
FROM 
    patients AS p
INNER JOIN 
    appointments AS a
ON 
    p.patient_id = a.patient_id
WHERE 
    p.first_name = 'Alice';
```
**Output:**

![image](https://github.com/user-attachments/assets/781daa8f-7079-49b5-a60e-483ae9e03b05)


**Question 9**
![image](https://github.com/user-attachments/assets/891737e2-2de2-4b40-8dab-4e75a5ee875d)
```
SELECT p.*
FROM patients p
INNER JOIN test_results t ON p.patient_id = t.patient_id
WHERE t.test_name = 'X-Ray' AND t.result = 'Normal';
```
**Output:**

![image](https://github.com/user-attachments/assets/dd1fb149-18a3-4de9-87de-a72f8ba2d6da)

**Question 10**
![image](https://github.com/user-attachments/assets/3d529c44-d907-4db2-be8d-85c7a98cd202)
```
SELECT 
    patients.first_name AS patient_name,
    doctors.first_name AS doctor_name
FROM 
    patients
INNER JOIN 
    doctors ON patients.doctor_id = doctors.doctor_id
WHERE 
    patients.discharge_date IS NULL;
```

**Output:**

![image](https://github.com/user-attachments/assets/491330a7-d9a5-46ea-ba92-a786a1b48ddd)

## Grade
![image](https://github.com/user-attachments/assets/92018c83-6c5b-4dfb-a2b1-84aac10650b1)


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
