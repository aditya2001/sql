# sql


### Employee Table
| EMPID | EMPNAME    | SALARY  | AGE  | JOBNAME     | DOJ       | DEPTID |
|-------|------------|---------|------|-------------|-----------|--------|
| `1`   | `Aditya`   | `50000` | `36` | `developer` | 20011987  | 101    |
| `2`   | `Minakshi` | `60000` | `32` | `analyst`   | 20011986  | 102    |     
| `3`   | `Divisha`  | `70000` | `2`  | `tester`    | 20012001  | 103    |
| `4`   | `Madhu`    | `80000` | `1`  | `manager`   | 20012005  | 105    |

### Employee Table
| DEPTID | DEPTNAME   | DEPTLOCATION | 
|--------|------------|--------------|
| `101`  | `Devops`   | `Bhopal`     | 
| `102`  | `Business` | `Bhopal`     | 
| `103`  | `Testing`  | `Pune`       |  
| `104`  | `Admin`    | `Pune`       |  


#### INNER JOIN - will return matching records from both the tables-
```java
select * from Employee INNER JOIN DEPARTMENT ON Employee.DEPTID =Department.DEPTID
```

#### LEFT JOIN - will return all the records from left table and matching ones from right table
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

#### RIGHT JOIN - will return all the records from right table and matching records from left tables
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


#### OUTER JOIN - will return the matching records and also unmatched records from left and right table
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


#### Find count of employees by department id ->
```java
select DEPTID, COUNT(*) from Employees GROUP BY DEPTID;
```

#### Find max salary of employee ->
```java
select MAX(SALARY) from Employee;
```

#### Find employee with 2nd highest salary
```java

```

#### Find average salary of employees in each department
```java

```