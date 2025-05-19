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
Write a SQL query to find the total amount of fruits with a unit type of 'LB'. Note: Inventory attribute contains amount of fruits Table: fruits
```
SELECT
SUM(inventory) AS total
FROM fruits
WHERE unit LIKE '%LB%';
```
**Output:**

![image](https://github.com/user-attachments/assets/dfb80ef8-1ccf-47d5-ad49-c821a34b8bc6)


**Question 2**
Write a SQL query to find how many employees have an income greater than 50K? Table: employee
```
SELECT
COUNT(*) AS employees_count
FROM employee
WHERE income>50000;
```
**Output:**

![image](https://github.com/user-attachments/assets/9de846e4-3b1f-4877-8e0b-3f202012b92c)


**Question 3**
Write a SQL query to find how many employees work in California? Table: employee
```
SELECT
COUNT(*) AS employees_in_california
FROM employee
WHERE city='California';
```

**Output:**

![image](https://github.com/user-attachments/assets/5b55f557-e492-44ca-9b74-e5d6e957896e)

**Question 4**
How many medical records does each doctor have? Sample table:MedicalRecords Table
```
SELECT
DoctorID,
COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY DoctorID
ORDER BY DoctorID ASC;
```

**Output:**

![image](https://github.com/user-attachments/assets/95746bcd-0d89-49ca-acab-70950da32a92)


**Question 5**
What is the average duration of insurance coverage for patients covered by each insurance company? Sample table:Insurance Table
```
SELECT
InsuranceCompany,
ABS(AVG(StartDate-EndDate)) AS AvgCoverageDurationDays
FROM Insurance
GROUP BY InsuranceCompany;
```

**Output:**

![image](https://github.com/user-attachments/assets/d0af0c15-9814-48e8-8508-5603586075a6)


**Question 6**
How many medical records are there for each patient? Sample table:MedicalRecords Table
```
SELECT
PatientID,
COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY PatientID
ORDER BY PatientID;
```

**Output:**

![image](https://github.com/user-attachments/assets/a876dee9-ed84-4932-963a-7f75d54577b6)


**Question 7**
Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 1,000,000. Sample table: employee
```
SELECT
age,
MIN(income) AS Income
FROM employee
GROUP BY age
HAVING MIN(income)<1000000;
```
**Output:**

![image](https://github.com/user-attachments/assets/7bf61521-b6b8-42e8-a2ff-ceef8fa3b109)

**Question 8**
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the average work hours for each date, and excludes dates where the average work hour is not less than 10. Sample table: employee1
```
SELECT
jdate,
AVG(workhour) AS "AVG(workhour)"
FROM employee1
GROUP BY jdate
HAVING AVG(workhour)<10;
```

**Output:**

![image](https://github.com/user-attachments/assets/89c0cbf2-aa34-4781-8fe4-57665a504d23)


**Question 9**
Write the SQL query that achieves the selection of product names and the maximum price for each category from the "products" table, and includes only those products where the maximum price is greater than 15. Sample table: products
```
SELECT
category_id,
product_name,
MAX(price) AS Price
FROM products
GROUP BY category_id 
HAVING MAX(price)>15;
```

**Output:**

![image](https://github.com/user-attachments/assets/f7d0e71b-5cdb-4d3b-b7d8-83f366a684bc)


**Question 10**
Write the SQL query that accomplishes the selection of average price for each category from the "products" table and includes only those products where the average price falls between 10 and 15. Sample table: products
```
SELECT
category_id,
AVG(price) AS 'AVG(Price)'
FROM products
GROUP BY category_id
HAVING AVG(price) BETWEEN 10 AND 15;
```

**Output:**

![image](https://github.com/user-attachments/assets/fe9e470d-5b6e-4711-ae3f-38d85282b4c9)

## Grade

![image](https://github.com/user-attachments/assets/f9b8ebba-8193-4f47-8fb1-3ca892d9539b)



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
