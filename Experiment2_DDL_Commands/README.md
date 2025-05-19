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
Create a table named Orders with the following constraints: OrderID as INTEGER should be the primary key. OrderDate as DATE should be not NULL. CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).
```
CREATE TABLE Orders(
OrderID INTEGER PRIMARY KEY,
OrderDate DATE NOT NULL,
CustomerID INTEGER,
FOREIGN KEY(CustomerID) REFERENCES Customers(CustomerID));
```

**Output:**
![image](https://github.com/user-attachments/assets/384596c6-38da-4694-a8c8-147f29481d39)


**Question 2**
Create a table named Department with the following constraints: DepartmentID as INTEGER should be the primary key. DepartmentName as TEXT should be unique and not NULL. Location as TEXT.
```
CREATE TABLE Department(
DepartmentID INTEGER PRIMARY KEY,
DepartmentName TEXT NOT NULL UNIQUE,
Location TEXT);
```
**Output:**
![image](https://github.com/user-attachments/assets/4e1bceb2-a51d-467b-8724-6119248122d1)


**Question 3**
Create a table named Locations with the following columns: LocationID as INTEGER LocationName as TEXT Address as TEXT
```
CREATE TABLE Locations(
LocationID INTEGER,
LocationName TEXT,
Address TEXT);
```
**Output:**

![image](https://github.com/user-attachments/assets/eb6fde33-5a2e-4bc1-9112-add0cf6da41a)

**Question 4**
In the Products table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.
```
INSERT INTO Products('ProductID','Name','Category')
VALUES(106,'Fitness Tracker','Wearables');

INSERT INTO Products('ProductID','Name','Category','Price','Stock')
VALUES(107,'Laptop','Electronic',999.99,50);

INSERT INTO Products('ProductID','Name','Category','Stock')
VALUES(108,'Wireless Earbud','Accessorie',100);
```
**Output:**

![image](https://github.com/user-attachments/assets/41f89c2c-d06e-469b-8618-b2730a2f5117)


**Question 5**
Write an SQL command can to add a column named email of type TEXT to the customers table
```
ALTER TABLE customers ADD COLUMN
email TEXT;
```
**Output:**

![image](https://github.com/user-attachments/assets/a43ae292-89fd-41e7-b952-c778c3a70d03)


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
![image](https://github.com/user-attachments/assets/2ebfe66d-d665-423c-adcb-f14068e010ce)


**Question 7**
Insert all books from Out_of_print_books into Books Table attributes are ISBN, Title, Author, Publisher, YearPublished
```
INSERT INTO Books(ISBN,Title,Author,Publisher,YearPublished)
SELECT ISBN, Title, Author, Publisher, YearPublished
FROM Out_of_print_books;
```
**Output:**
![image](https://github.com/user-attachments/assets/7326fda1-70b9-4a26-9258-a05652f6fa80)


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

![image](https://github.com/user-attachments/assets/bf867727-6a7e-4601-8ce3-702c424b01ec)

**Question 9**
 Insert a record with EmployeeID 001, Name Sarah Parker, Position Manager, Department HR, and Salary 60000 into the Employee table.
```
INSERT INTO Employee(EmployeeID,Name,Position,Department,Salary)
VALUES(001,'Sarah Parker','Manager','HR','60000');
```
**Output:**

![image](https://github.com/user-attachments/assets/df8ec515-c9f6-4791-b1a2-f3625e4ac38a)


**Question 10**
Write a SQL query to Rename the "city" column to "location" in the "customer" table.
Sample table: customer

customer_id | cust_name | city | grade | salesman_id -------------+----------------+------------+-------+------------- 3002 | Nick Rimando | New York | 100 | 5001 3007 | Brad Davis | New York | 200 | 5001 3005 | Graham Zusi | California | 200 | 5002
```
ALTER TABLE customer RENAME COLUMN city TO location;
```
**Output:**
![image](https://github.com/user-attachments/assets/59efb98a-1927-48c0-8258-d0afff360ddb)

## Grade
![image](https://github.com/user-attachments/assets/7f5672d1-5bdb-47ce-80c3-a4ebe130e3ab)

## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
