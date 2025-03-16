# SQL Commands and Queries

## 1. Creating a Database
```sql
CREATE DATABASE database_name;
USE database_name;
```

## 2. Creating a Table
```sql
CREATE TABLE Employee (
    ID INT,
    EmpName VARCHAR(255),
    City VARCHAR(255),
    Salary INT
);
```

## 3. Inserting Data
```sql
INSERT INTO Employee (ID, EmpName, City, Salary)
VALUES (1, 'Tom', 'ABC', 7000);
```

## 4. Fetching Data from Table
- **Select all records:**
```sql
SELECT * FROM Employee;
```

- **Select specific columns:**
```sql
SELECT ID, EmpName FROM Employee;
```

- **Select distinct records:**
```sql
SELECT DISTINCT City FROM Employee;
```

## 5. Filtering Data
- **Using WHERE clause:**
```sql
SELECT EmpName FROM Employee WHERE Salary = 8000;
SELECT * FROM Employee WHERE Salary >= 7000;
```

## 6. Sorting Data
- **Ascending order:**
```sql
SELECT * FROM Employee ORDER BY Salary;
```
- **Descending order:**
```sql
SELECT * FROM Employee ORDER BY Salary DESC;
```
- **Order by multiple columns:**
```sql
SELECT * FROM Employee ORDER BY City, Salary;
```

## 7. Using Logical Operators
- **AND operator:** Both conditions must be true
```sql
SELECT * FROM Employee WHERE City = 'ABC' AND Salary < 700;
```
- **OR operator:** At least one condition must be true
```sql
SELECT * FROM Employee WHERE City = 'ABC' OR EmpName = 'Henry';
```
- **NOT operator:** Negates a condition
```sql
SELECT * FROM Employee WHERE NOT Salary = 800;
```

## 8. Using IN and BETWEEN Operators
- **IN operator:**
```sql
SELECT * FROM Employee WHERE City IN ('xyz', 'yxz');
```
- **NOT IN operator:**
```sql
SELECT * FROM Employee WHERE City NOT IN ('xyz', 'yxz');
```
- **BETWEEN operator:**
```sql
SELECT * FROM Employee WHERE Salary BETWEEN 7000 AND 9000;
```
- **NOT BETWEEN operator:**
```sql
SELECT * FROM Employee WHERE Salary NOT BETWEEN 7000 AND 9000;
```

## 9. Using LIKE Operator
- **Starts with 'A':**
```sql
SELECT * FROM Employee WHERE City LIKE 'A%';
```
- **Ends with 'A':**
```sql
SELECT * FROM Employee WHERE City LIKE '%A';
```

## 10. Aggregate Functions
- **Maximum salary:**
```sql
SELECT MAX(Salary) AS Result FROM Employee;
```
- **Minimum salary:**
```sql
SELECT MIN(Salary) AS Result FROM Employee;
```
- **Sum of all salaries:**
```sql
SELECT SUM(Salary) FROM Employee;
```
- **Sum with condition:**
```sql
SELECT SUM(Salary) FROM Employee WHERE Salary >= 7000;
```

## 11. Constraints (Primary Key, Foreign Key, and Checks)
```sql
CREATE TABLE Employee (
    ID INT NOT NULL UNIQUE PRIMARY KEY,
    EmpName VARCHAR(255) NOT NULL,
    Salary INT CHECK (Salary < 1000)
);
```

## 12. Altering Table
- **Add a new column:**
```sql
ALTER TABLE Employee ADD Age INT;
```
- **Remove a column:**
```sql
ALTER TABLE Employee DROP COLUMN Age;
```

## 13. Updating Data
```sql
UPDATE Employee
SET Salary = 9500, City = 'JKL'
WHERE ID = 4;
```

## 14. Stored Procedures
- **Retrieve all records:**
```sql
CREATE PROCEDURE AllRecords
AS
SELECT * FROM Employee;
GO
```
- **Retrieve records based on City:**
```sql
CREATE PROCEDURE AllRecordsByCity @City VARCHAR(255)
AS
SELECT * FROM Employee WHERE City = @City;
```
- **Execute Procedure:**
```sql
EXEC AllRecordsByCity @City = 'ABC';
```
- **Retrieve records based on multiple conditions:**
```sql
CREATE PROCEDURE AllRecordsByCityAndName @City VARCHAR(255), @EmpName VARCHAR(255)
AS
SELECT * FROM Employee WHERE City = @City AND EmpName = @EmpName;
```
```sql
EXEC AllRecordsByCityAndName @City = 'ABC', @EmpName = 'xyz';
```

## 15. Indexing
- **Creating a backup table:**
```sql
SELECT * INTO EmpBackup FROM Employee;
SELECT * FROM EmpBackup;
```

## 16. Limiting Results
- **Select top 50% records:**
```sql
SELECT TOP 50 PERCENT * FROM Employee;
```
- **Select top 50% records with a condition:**
```sql
SELECT TOP 50 PERCENT * FROM Employee WHERE Salary > 7000;
```

## 17. Database Backup
```sql
BACKUP DATABASE mydb TO DISK = 'E:\path';
```

## 18. Views
- **Creating a view:**
```sql
CREATE VIEW [Salary Above 7000] AS
SELECT EmpName, City FROM Employee WHERE Salary > 7000;
```
- **Dropping a view:**
```sql
DROP VIEW [Salary Above 7000];
```

## 19. Dropping a Table
```sql
DROP TABLE Employee;
```

---

This document serves as a quick reference guide to essential SQL operations, covering database creation, table manipulation, data retrieval, filtering, ordering, aggregation, constraints, stored procedures, indexing, and database management tasks.

