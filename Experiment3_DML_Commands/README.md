# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
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
Create a table named Orders with the following constraints: OrderID as INTEGER should be the primary key. OrderDate as DATE should be not NULL. CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).
```
CREATE TABLE Orders(
OrderID INTEGER PRIMARY KEY,
OrderDate DATE NOT NULL,
CustomerID INTEGER,
FOREIGN KEY(CustomerID) REFERENCES Customers(CustomerID));
```
**Output:**

![image](https://github.com/user-attachments/assets/ba8ad843-8818-4381-9a5f-0a626229b5eb)

**Question 2**
Create a table named Department with the following constraints: DepartmentID as INTEGER should be the primary key. DepartmentName as TEXT should be unique and not NULL. Location as TEXT.
```
CREATE TABLE Department(
DepartmentID INTEGER PRIMARY KEY,
DepartmentName TEXT NOT NULL UNIQUE,
Location TEXT);
```
**Output:**
![image](https://github.com/user-attachments/assets/0209ced3-ab3c-4fac-9870-f0cfcad1a007)


**Question 3**
Create a table named Locations with the following columns: LocationID as INTEGER LocationName as TEXT Address as TEXT
```
CREATE TABLE Locations(
LocationID INTEGER,
LocationName TEXT,
Address TEXT);
```
**Output:**

![image](https://github.com/user-attachments/assets/c15099b3-19bf-4080-b939-1f9268da1beb)


**Question 4**
 In the Products table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.
ProductID Name Category Price Stock

106 Fitness Tracker Wearables 107 Laptop Electronics 999.99 50 108 Wireless Earbuds Accessories 100
```
INSERT INTO Products('ProductID','Name','Category')
VALUES(106,'Fitness Tracker','Wearables');

INSERT INTO Products('ProductID','Name','Category','Price','Stock')
VALUES(107,'Laptop','Electronic',999.99,50);

INSERT INTO Products('ProductID','Name','Category','Stock')
VALUES(108,'Wireless Earbud','Accessorie',100);
```

**Output:**
![image](https://github.com/user-attachments/assets/db79719a-0933-4dfb-92bd-31119cf51083)


**Question 5**
Write an SQL command can to add a column named email of type TEXT to the customers table
```
ALTER TABLE customers ADD COLUMN
email TEXT;
```

**Output:**

![image](https://github.com/user-attachments/assets/85a7e3e9-2e45-4a3c-9596-fedb0ced8247)


**Question 6**
Create a table named ProjectAssignments with the following constraints: AssignmentID as INTEGER should be the primary key. EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID). ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID). AssignmentDate as DATE should be NOT NULL.
```
CREATE TABLE ProjectAssignments(
AssignmentID INTEGER PRIMARY KEY,
EmployeeID INTEGER,
ProjectID INTEGER,
AssignmentDate DATE NOT NULL,
FOREIGN KEY(EmployeeID) REFERENCES Employees(EmployeeID),
FOREIGN KEY(ProjectID) REFERENCES Projects(ProjectID));
```

**Output:**
![image](https://github.com/user-attachments/assets/75118e8b-8c87-4907-8152-3aafe782b79b)


**Question 7**
Insert all books from Out_of_print_books into Books Table attributes are ISBN, Title, Author, Publisher, YearPublished
```
INSERT INTO Books(ISBN,Title,Author,Publisher,YearPublished)
SELECT ISBN, Title, Author, Publisher, YearPublished
FROM Out_of_print_books;
```

**Output:**

![image](https://github.com/user-attachments/assets/514973af-f426-41bc-b34d-3507674ac6b8)


**Question 8**
Create a new table named contacts with the following specifications: contact_id as INTEGER and primary key. first_name as TEXT and not NULL. last_name as TEXT and not NULL. email as TEXT. phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.
```
CREATE TABLE contacts(
contact_id INTEGER PRIMARY KEY,
first_name TEXT NOT NULL,
last_name TEXT NOT NULL,
email TEXT,
phone TEXT NOT NULL CHECK(LENGTH(phone)>9));
```

**Output:**

![image](https://github.com/user-attachments/assets/9a8ece62-359b-45b0-a344-a3179ff750e1)


**Question 9**
Insert a record with EmployeeID 001, Name Sarah Parker, Position Manager, Department HR, and Salary 60000 into the Employee table.
```
INSERT INTO Employee(EmployeeID,Name,Position,Department,Salary)
VALUES(001,'Sarah Parker','Manager','HR','60000');
```
**Output:**

![image](https://github.com/user-attachments/assets/3e4ee061-1b97-4446-9291-e649cecb9ee6)


**Question 10**
Write a SQL query to Rename the "city" column to "location" in the "customer" table.

Sample table: customer

customer_id | cust_name | city | grade | salesman_id -------------+----------------+------------+-------+------------- 3002 | Nick Rimando | New York | 100 | 5001 3007 | Brad Davis | New York | 200 | 5001 3005 | Graham Zusi | California | 200 | 5002
```
ALTER TABLE customer RENAME COLUMN city TO location;

```

**Output:**
![image](https://github.com/user-attachments/assets/5609f23d-96c3-41d8-a073-57877ea95260)

## Grade
![image](https://github.com/user-attachments/assets/4e039867-9495-4858-b010-e72279177f9d)


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
