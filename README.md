# SQL Interview Questions

### 11. What is a subquery?
Subquery is a query embedded inside another query.

### 12. Difference between GROUP BY and HAVING clause?
The WHERE clause is applied before any grouping takes place and filters individual rows.
On the other hand, the HAVING clause is applied on GROUP BY clause.

### 13. Difference between DELETE and TRUNCATE?
1. The basic difference in both is DELETE command is the DML command and the TRUNCATE command is DDL.
2. DELETE command is used to delete a specific row from the table whereas the TRUNCATE command is used to remove all rows from the table.

### 14. Difference between CHAR and VARCHAR in SQL?
CHAR is a fixed-length data type in SQL, meaning it will always occupy the exact number of characters specified, even if the actual value is shorter.
Padding with spaces is done to meet the required length. On the other hand, VARCHAR is a variable-length data type. It stores only the number of characters that are used, without extra padding, making it more efficient for storing variable-length strings.

### 15. Group By clause in SQL?
GROUP BY is used to group the records by one or more column.Basically group the rows that share value in specified column.

### 16. Distinct keyword in SQL?
The DISTINCT keyword is used in to remove duplicate values from the result set of a SELECT query.

### 17. Aggregate Functions in SQL?
1. AVG(): Returns the average value from specified columns.
2. COUNT(): Returns the number of table rows.
3. MAX(): Returns the largest value among the records.
4. MIN(): Returns the smallest value among the records.
5. SUM(): Returns the sum of specified column values.
6. FIRST(): Returns the first value.
7. LAST(): Returns last value.

### 18. Constraints in SQL?
There are 5 major constraints used in SQL, such as

1. NOT NULL: That indicates that the column must have some value and cannot be left NULL.
2. UNIQUE: This constraint is used to ensure that each row and column has a unique value and no value is being repeated in any other row or column.
3. PRIMARY KEY: This constraint is used in association with NOT NULL and UNIQUE constraints such as on one or the combination of more than one column to identify the particular record with a unique identity.
4. FOREIGN KEY: It is used to ensure the referential integrity of data in the table. It matches the value in one table with another using the PRIMARY KEY.

### 18. Difference between DROP and TRUNCATE?
TRUNCATE removes all rows from the table which cannot be retrieved back, DROP removes the entire table from the database and it also cannot be retrieved back.


### Employee Table
| EMPID | EMPNAME    | SALARY  | AGE  | JOBNAME     | DOJ       | DEPTID |
|-------|------------|---------|------|-------------|-----------|--------|
| `1`   | `Aditya`   | `50000` | `36` | `developer` | 20011987  | 101    |
| `2`   | `Minakshi` | `60000` | `32` | `analyst`   | 20011986  | 102    |     
| `3`   | `Divisha`  | `70000` | `2`  | `tester`    | 20012001  | 103    |
| `4`   | `Madhu`    | `80000` | `1`  | `manager`   | 20012005  | 105    |

### DEPARTMENT Table
| DEPTID | DEPTNAME   | DEPTLOCATION | 
|--------|------------|--------------|
| `101`  | `Devops`   | `Bhopal`     | 
| `102`  | `Business` | `Bhopal`     | 
| `103`  | `Testing`  | `Pune`       |  
| `104`  | `Admin`    | `Pune`       |  


#### 1. INNER JOIN - will return matching records from both the tables-
```java
select * from Employee INNER JOIN DEPARTMENT ON Employee.DEPTID =Department.DEPTID
```

#### 2. LEFT JOIN - will return all the records from left table and matching ones from right table
```java
select * from Employee LEFT JOIN DEPARTMENT ON Employee.DEPTID =Department.DEPTID
```
### Employee Table
| EMPID | EMPNAME    | SALARY  | AGE  | JOBNAME     | DOJ      | DEPTID | DEPTNAME   | DEPTLOCATION |
|-------|------------|---------|------|-------------|----------|--------|------------|--------------|
| `1`   | `Aditya`   | `50000` | `36` | `developer` | 20011987 | 101    | `Devops`   | `Bhopal`     |
| `2`   | `Minakshi` | `60000` | `32` | `analyst`   | 20011986 | 102    | `Business` | `Bhopal`     |
| `3`   | `Divisha`  | `70000` | `2`  | `tester`    | 20012001 | 103    | `Testing`  | `Bhopal`     |
| `4`   | `Madhu`    | `80000` | `1`  | `manager`   | 20012005 | 104    | `NULL`     | `NULL`       |

#### 3. RIGHT JOIN - will return all the records from right table and matching records from left tables
```java
select * from Employee RIGHT JOIN DEPARTMENT ON Employee.DEPTID =Department.DEPTID
```

### Employee Table
| EMPID  | EMPNAME    | SALARY  | AGE    | JOBNAME     | DOJ      | DEPTID | DEPTNAME   | DEPTLOCATION |
|--------|------------|---------|--------|-------------|----------|--------|------------|--------------|
| `1`    | `Aditya`   | `50000` | `36`   | `developer` | 20011987 | 101    | `Devops`   | `Bhopal`     |
| `2`    | `Minakshi` | `60000` | `32`   | `analyst`   | 20011986 | 102    | `Business` | `Bhopal`     |
| `3`    | `Divisha`  | `70000` | `2`    | `tester`    | 20012001 | 103    | `Testing`  | `Bhopal`     |
| `NULL` | `NULL`     | `NULL`  | `NULL` | `NULL`      | 20012005 | 104    | `Admin`    | `Bhopal`     |


#### 4. OUTER JOIN - will return the matching records and also unmatched records from left and right table
```java
select * from Employee OUTER JOIN DEPARTMENT ON Employee.DEPTID =Department.DEPTID
```

### Employee Table
| EMPID | EMPNAME    | SALARY  | AGE  | JOBNAME     | DOJ      | DEPTID | DEPTNAME   | DEPTLOCATION |
|-------|------------|---------|------|-------------|----------|--------|------------|--------------|
| `1`   | `Aditya`   | `50000` | `36` | `developer` | 20011987 | 101    | `Devops`   | `Bhopal`     |
| `2`   | `Minakshi` | `60000` | `32` | `analyst`   | 20011986 | 102    | `Business` | `Bhopal`     |
| `3`   | `Divisha`  | `70000` | `2`  | `tester`    | 20012001 | 103    | `Testing`  | `Bhopal`     |
| `4`   | `Madhu`    | `80000` | `1`  | `manager`   | 20012005 | 104    | `NULL`     | `NULL`        |
|`NULL` | `NULL`     | `NULL`  |`NULL`| `NULL`      | `NULL`   | 105    | `Admin`    | `Bhopal`     |


### 5. Find count of employees by department id ->
```java
select DEPTID, COUNT(*) from Employees GROUP BY DEPTID HAVING COUNT(*) > 1;
```

### 5. Find count of employees by department id who have age >20 ->
```java
select DEPTID, COUNT(*) from Employees WHERE AGE > 30 GROUP BY DEPTID;
```

### 6. Find max salary of employee ->
```java
select MAX(SALARY) from Employee;
```

### 7. Find employee with 3rd highest salary
```java
SELECT MAX(SALARY)
FROM Employee
WHERE Salary NOT IN (
  SELECT TOP 2 SALARY
  FROM Employees
  ORDER BY SALARY DESC
);
```

### 8. Find average salary of employees in each department
```java
select DEPTID, AVG(SALARY) from Employees GROUP BY DEPTID
```

### 9. Find top 3 departments with highest average salary of employees
```java
select TOP 3 DEPTID, AVG(SALARY) from Employees GROUP BY DEPTID ORDER BY AVG(SALARY) DESC;
```

### 10. Find the department with max employees
```java
SELECT TOP 1 DEPTNAME, COUNT(*) AS MAX_EMPLOYEES
FROM EMPLOYEES
GROUP BY DEPTNAME
ORDER BY COUNT(*) DESC;
```

### 11. Query to fetch no of employees working in a specific department?
```java
select COUNT(*) from EMPLOYEES where DEPTID = 'Devops';
```

### 12. Between
```java
SELECT * FROM EMPLOYEES WHERE SALARY BETWEEN '50000' AND '100000';
```

### 13. Like 
```java
SELECT * FROM EMPLOYEES WHERE EMPNAME LIKE 'S%';
```

### 14. Write a query to retrieve Departments who have less than 2 employees working in it.
```java
SELECT DEPTID, COUNT(EMPID) as 'EmpNo' FROM EMPLOYEES GROUP BY DEPTID HAVING COUNT(EMPID) < 2;
```


