# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
![image](https://github.com/user-attachments/assets/0b7d4bc5-4267-4e32-84e1-5ba05efc74da)
```
SELECT 
medication_id AS medic,
medication_name,
dosage
FROM Medications
WHERE CAST(REPLACE(dosage,'mg','') AS INTEGER)=(SELECT MAX(CAST(REPLACE(dosage,'mg','') AS INTEGER))
FROM Medications);
```

**Output:**

![image](https://github.com/user-attachments/assets/276af843-503c-41ec-9ecd-1b596e8ffb14)


**Question 2**
![image](https://github.com/user-attachments/assets/33e5abd1-f8c9-4f35-a3a4-7f793025ea64)
```
SELECT
o.ord_no,
o.purch_amt,
o.ord_date,
o.customer_id,
o.salesman_id
FROM Orders o
JOIN Salesman s ON o.salesman_id=s.salesman_id
WHERE s.city='New York';
```

**Output:**

![image](https://github.com/user-attachments/assets/1ec856e4-5540-4739-98ff-2f548b19b02d)


**Question 3**
![image](https://github.com/user-attachments/assets/7535af8d-0978-4e66-91b8-4b75986c4bfe)
```
SELECT student_name,grade
FROM GRADES
WHERE grade IN(SELECT MIN(grade) FROM GRADES AS g WHERE g.subject=GRADES.subject);
```
**Output:**
![image](https://github.com/user-attachments/assets/7dbcc7b1-0b33-47a6-8563-089de4e5b00b)


**Question 4**
![image](https://github.com/user-attachments/assets/05c2069d-515c-46d9-8c78-18970780d735)
```
SELECT *
FROM customer
WHERE city <>(
SELECT
city
FROM customer
WHERE id=(SELECT MAX(id) FROM customer));
```

**Output:**

![image](https://github.com/user-attachments/assets/c0588e3a-1286-4799-8ab7-3d1066686984)


**Question 5**
![image](https://github.com/user-attachments/assets/813cfee7-6d81-402c-bc8c-21e3e968fe82)
```
SELECT 
name
FROM customer
WHERE phone IN(
SELECT phone
FROM customer
GROUP BY phone
HAVING COUNT(*)=1)
```

**Output:**

![image](https://github.com/user-attachments/assets/b41e7794-0380-4a6f-891a-ff3cd92eb0d4)


**Question 6**
![image](https://github.com/user-attachments/assets/e44e1374-3703-4cac-8e9e-617aa202c87e)
```
SELECT *
FROM GRADES
WHERE grade IN(SELECT MAX(grade) FROM GRADES AS g WHERE g.subject=GRADES.subject);
```

**Output:**

![image](https://github.com/user-attachments/assets/772c32cb-595a-4ae5-aa3c-a9245beb8508)


**Question 7**
![image](https://github.com/user-attachments/assets/856cd8df-d03c-4585-8f74-8a4feec68580)
```
SELECT
o.ord_no,
o.purch_amt,
o.ord_date,
o.customer_id,
o.salesman_id
FROM Orders o
JOIN Salesman s ON o.salesman_id=s.salesman_id
WHERE s.city='New York';
```
**Output:**

![image](https://github.com/user-attachments/assets/9b9dcf74-5829-4f6e-b456-efa304b02b11)


**Question 8**
![image](https://github.com/user-attachments/assets/7037ac3a-452e-4196-9a04-a9a29a3338f2)
```
SELECT *
FROM GRADES
WHERE grade IN(SELECT MIN(grade) FROM GRADES AS g WHERE g.subject=GRADES.subject);
```

**Output:**

![image](https://github.com/user-attachments/assets/ce1519b7-e332-47fd-a1ec-7700fb7de7de)

**Question 9**
![image](https://github.com/user-attachments/assets/f4b3586c-34bf-4011-95b1-3c96e1639419)
```
SELECT * 
FROM Orders
WHERE salesman_id IN(
SELECT
salesman_id
FROM Orders
WHERE customer_id='3007');
```
**Output:**

![image](https://github.com/user-attachments/assets/9073df1f-6da0-4ef6-ab99-445fcef6560e)


**Question 10**
![image](https://github.com/user-attachments/assets/62e74690-f05a-4e68-9b91-36029ca4a54b)
```
SELECT *
FROM Employee
WHERE age<(SELECT AVG(age) FROM Employee WHERE income>250000);
```

**Output:**

![image](https://github.com/user-attachments/assets/64a2d4f3-bd73-49a8-95d3-726796e976bf)

## Grade
![image](https://github.com/user-attachments/assets/445907dd-8136-480a-a257-eca7842ae7ca)




## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
