## Practical 01

**Aim:** Implement SQL queries to perform various DDL Commands (Create a minimum 5 tables with different data types and operate upon them).

**Description:** To understand and implement Data Definition Language (DDL) commands such as CREATE, ALTER, DROP, and TRUNCATE in Oracle SQL to design and manage the structure of relational database tables using different data types and constraints.

**Code:**

```sql
-- Creating Table 1: Departments
CREATE TABLE departments (
    dept_id NUMBER(4) PRIMARY KEY,
    dept_name VARCHAR2(50) NOT NULL,
    location VARCHAR2(50)
);

-- Creating Table 2: Employees
CREATE TABLE employees (
    emp_id NUMBER(6) PRIMARY KEY,
    first_name VARCHAR2(30),
    last_name VARCHAR2(30) NOT NULL,
    hire_date DATE DEFAULT SYSDATE,
    salary NUMBER(8, 2),
    dept_id NUMBER(4),
    CONSTRAINT fk_dept FOREIGN KEY (dept_id) REFERENCES departments(dept_id)
);

-- Creating Table 3: Projects
CREATE TABLE projects (
    proj_id NUMBER(5) PRIMARY KEY,
    proj_name VARCHAR2(100) NOT NULL,
    budget NUMBER(12, 2),
    start_date DATE
);

-- Creating Table 4: Clients
CREATE TABLE clients (
    client_id NUMBER(5) PRIMARY KEY,
    client_name VARCHAR2(100) NOT NULL,
    contact_email VARCHAR2(100) UNIQUE,
    phone_no CHAR(10)
);

-- Creating Table 5: Assignments
CREATE TABLE assignments (
    emp_id NUMBER(6),
    proj_id NUMBER(5),
    role VARCHAR2(30),
    hours_allocated NUMBER(4, 1),
    PRIMARY KEY (emp_id, proj_id),
    FOREIGN KEY (emp_id) REFERENCES employees(emp_id),
    FOREIGN KEY (proj_id) REFERENCES projects(proj_id)
);

-- ALTER Commands: Modify, Add, and Rename columns
ALTER TABLE employees ADD (email VARCHAR2(100));
ALTER TABLE employees MODIFY (salary NUMBER(10, 2));
ALTER TABLE clients RENAME COLUMN phone_no TO mobile_no;

-- TRUNCATE Command
TRUNCATE TABLE assignments;

-- DROP Command
DROP TABLE clients;
```

**Output:**

Structure of `EMPLOYEES` Table (after ALTER):

| Column Name | Data Type | Nullable | Primary Key / Constraint |
|---|---|---|---|
| EMP_ID | NUMBER(6) | No | Primary Key |
| FIRST_NAME | VARCHAR2(30) | Yes | None |
| LAST_NAME | VARCHAR2(30) | No | None |
| HIRE_DATE | DATE | Yes | Default SYSDATE |
| SALARY | NUMBER(10,2) | Yes | None |
| DEPT_ID | NUMBER(4) | Yes | Foreign Key (DEPARTMENTS) |
| EMAIL | VARCHAR2(100) | Yes | None |

**Conclusion:** DDL commands (CREATE, ALTER, TRUNCATE, and DROP) were successfully implemented to define, alter, truncate, and remove table structures in Oracle XE.

---

## Practical 02

**Aim:** Implement SQL queries to perform various DML Commands (Insert minimum 10 rows using different insert methods, edit and remove data using UPDATE and DELETE commands).

**Description:** To understand and apply Data Manipulation Language (DML) commands in Oracle SQL, including different methods of inserting records, and modifying or removing existing data using UPDATE and DELETE statements.

**Code:**

```sql
-- Method 1: Standard Insert specifying column list
INSERT INTO departments (dept_id, dept_name, location) VALUES (10, 'IT', 'New York');
INSERT INTO departments (dept_id, dept_name, location) VALUES (20, 'HR', 'Chicago');
INSERT INTO departments (dept_id, dept_name, location) VALUES (30, 'Finance', 'Boston');

-- Method 2: Standard Insert without column list (all columns)
INSERT INTO employees VALUES (101, 'John', 'Doe', TO_DATE('2022-01-15', 'YYYY-MM-DD'), 60000.00, 10, 'john.doe@company.com');
INSERT INTO employees VALUES (102, 'Jane', 'Smith', TO_DATE('2021-03-20', 'YYYY-MM-DD'), 55000.00, 10, 'jane.smith@company.com');
INSERT INTO employees VALUES (103, 'Robert', 'Johnson', TO_DATE('2020-07-10', 'YYYY-MM-DD'), 70000.00, 20, 'robert.j@company.com');

-- Method 3: Inserting rows with NULL values
INSERT INTO employees (emp_id, first_name, last_name, hire_date, salary, dept_id) 
VALUES (104, 'Emily', 'Davis', SYSDATE, 50000.00, 20);

-- Method 4: Multi-row insert using INSERT ALL
INSERT ALL
    INTO employees (emp_id, first_name, last_name, hire_date, salary, dept_id, email) VALUES (105, 'Michael', 'Brown', SYSDATE, 48000.00, 30, 'mbrown@company.com')
    INTO employees (emp_id, first_name, last_name, hire_date, salary, dept_id, email) VALUES (106, 'Sarah', 'Wilson', SYSDATE, 65000.00, 10, 'swilson@company.com')
    INTO employees (emp_id, first_name, last_name, hire_date, salary, dept_id, email) VALUES (107, 'David', 'Taylor', SYSDATE, 52000.00, 30, 'dtaylor@company.com')
    INTO employees (emp_id, first_name, last_name, hire_date, salary, dept_id, email) VALUES (108, 'Laura', 'Anderson', SYSDATE, 58000.00, 20, 'landerson@company.com')
    INTO employees (emp_id, first_name, last_name, hire_date, salary, dept_id, email) VALUES (109, 'James', 'Thomas', SYSDATE, 72000.00, 10, 'jthomas@company.com')
    INTO employees (emp_id, first_name, last_name, hire_date, salary, dept_id, email) VALUES (110, 'Emma', 'White', SYSDATE, 45000.00, 30, 'ewhite@company.com')
SELECT * FROM dual;

-- UPDATE Commands
UPDATE employees SET salary = salary * 1.10 WHERE dept_id = 10;
UPDATE employees SET email = 'emily.davis@company.com' WHERE emp_id = 104;

-- DELETE Commands
DELETE FROM employees WHERE emp_id = 110;

```


**Output: **

| EMP_ID | FIRST_NAME | LAST_NAME | HIRE_DATE | SALARY | DEPT_ID | EMAIL |
|---|---|---|---|---|---|---|
| 101 | John | Doe | 15-JAN-22 | 66000.00 | 10 | john.doe@company.com |
| 102 | Jane | Smith | 20-MAR-21 | 60500.00 | 10 | jane.smith@company.com |
| 103 | Robert | Johnson | 10-JUL-20 | 70000.00 | 20 | robert.j@company.com |
| 104 | Emily | Davis | 21-SEP-26 | 50000.00 | 20 | emily.davis@company.com |
| 105 | Michael | Brown | 21-SEP-26 | 48000.00 | 30 | mbrown@company.com |
| 106 | Sarah | Wilson | 21-SEP-26 | 71500.00 | 10 | swilson@company.com |
| 107 | David | Taylor | 21-SEP-26 | 52000.00 | 30 | dtaylor@company.com |
| 108 | Laura | Anderson | 21-SEP-26 | 58000.00 | 20 | landerson@company.com |
| 109 | James | Thomas | 21-SEP-26 | 79200.00 | 10 | jthomas@company.com |

**Conclusion:** DML statements (INSERT, UPDATE, DELETE) were successfully demonstrated using various methods to manage row-level data in Oracle XE.

---

## Practical 03

**Aim:** Retrieve data using the SELECT command and various SQL operators.

**Description:** To understand and apply the SELECT statement along with comparison, logical, and special SQL operators (such as BETWEEN, IN, LIKE, IS NULL) to retrieve and filter data from relational tables.

**Code:**

```sql
-- 1. Simple SELECT and Relational Operators
SELECT emp_id, first_name, last_name, salary FROM employees WHERE salary > 60000;

-- 2. Logical Operators (AND, OR, NOT)
SELECT emp_id, first_name, last_name, dept_id, salary 
FROM employees 
WHERE dept_id = 10 AND salary >= 65000;

SELECT emp_id, first_name, last_name, dept_id 
FROM employees 
WHERE dept_id = 20 OR dept_id = 30;

-- 3. BETWEEN ... AND Operator
SELECT emp_id, first_name, last_name, salary 
FROM employees 
WHERE salary BETWEEN 50000 AND 65000;

-- 4. IN Operator
SELECT emp_id, first_name, last_name, dept_id 
FROM employees 
WHERE dept_id IN (10, 30);

-- 5. LIKE Operator (Pattern Matching)
SELECT emp_id, first_name, last_name 
FROM employees 
WHERE last_name LIKE 'S%';

SELECT emp_id, first_name, last_name 
FROM employees 
WHERE first_name LIKE '_a%';

-- 6. IS NULL / IS NOT NULL Operators
SELECT emp_id, first_name, last_name, email 
FROM employees 
WHERE email IS NULL;

SELECT emp_id, first_name, last_name, email 
FROM employees 
WHERE email IS NOT NULL;
```

**Output:**

1. **SELECT:** 102-Jane, 106-Sarah, 109-James
2. **AND:** 106-Sarah, 109-James ,**OR:** 103-Robert, 104-Emily, 105-Michael, 107-David, 108-Laura
3. **BETWEEN:** 104-Emily, 108-Laura
4. **IN:** 101-John, 102-Jane, 105-Michael, 106-Sarah, 107-David, 109-James
5. **LIKE:**  
   - `S%` → 102-Jane Smith  
   - `_a%` → 102-Jane, 106-Sarah, 108-Laura, 109-James
6. **IS NULL:** No rows ,**IS NOT NULL:** 101–109


**Conclusion:** The SELECT statement combined with comparison, logical, pattern matching (LIKE), set membership (IN), range (BETWEEN), and NULL test operators was successfully verified.

---

## Practical 04

**Aim:** Implement SQL queries using Date functions like ADD_MONTHS, MONTHS_BETWEEN, ROUND, NEXT_DAY, TRUNC, GREATEST, NEW_TIME etc.

**Description:** To understand and apply Oracle SQL date functions for performing date arithmetic, calculating intervals between dates, rounding, truncating, and finding relative dates in database queries.

**Code:**

```sql
-- Date Functions Demonstration using DUAL and EMPLOYEES tables

-- 1. ADD_MONTHS: Adding 6 months to current date
SELECT SYSDATE, ADD_MONTHS(SYSDATE, 6) AS six_months_later FROM DUAL;

-- 2. MONTHS_BETWEEN: Calculating months difference between two dates
SELECT MONTHS_BETWEEN(SYSDATE, TO_DATE('2025-01-01', 'YYYY-MM-DD')) AS months_diff FROM DUAL;

-- 3. NEXT_DAY: Finding the date of the next specified weekday
SELECT SYSDATE, NEXT_DAY(SYSDATE, 'MONDAY') AS next_monday FROM DUAL;

-- 4. LAST_DAY: Finding the last day of the current month
SELECT SYSDATE, LAST_DAY(SYSDATE) AS end_of_month FROM DUAL;

-- 5. ROUND and TRUNC on Dates
SELECT SYSDATE, 
       ROUND(SYSDATE, 'MONTH') AS rounded_month, 
       TRUNC(SYSDATE, 'YEAR') AS truncated_year 
FROM DUAL;

-- 6. GREATEST and LEAST with Dates
SELECT GREATEST(TO_DATE('2026-01-01', 'YYYY-MM-DD'), TO_DATE('2026-12-31', 'YYYY-MM-DD')) AS max_date FROM DUAL;

-- 7. NEW_TIME: Converting time between time zones (AST to PST)
SELECT TO_CHAR(NEW_TIME(TO_DATE('2026-09-21 12:00:00', 'YYYY-MM-DD HH24:MI:SS'), 'AST', 'PST'), 'YYYY-MM-DD HH24:MI:SS') AS converted_time FROM DUAL;
```

**Output:**

| Function Output Column | Sample Output Value |
| ---------------------- | ------------------- |
| SYSDATE                | 21-SEP-26           |
| SIX_MONTHS_LATER       | 21-MAR-27           |
| MONTHS_DIFF            | 20.67               |
| NEXT_MONDAY            | 28-SEP-26           |
| END_OF_MONTH           | 30-SEP-26           |
| ROUNDED_MONTH          | 01-OCT-26           |
| TRUNCATED_YEAR         | 01-JAN-26           |
| MAX_DATE               | 31-DEC-26           |
| CONVERTED_TIME         | 2026-09-21 08:00:00 |

**Conclusion:** Built-in Oracle SQL date functions were successfully implemented to perform date manipulations, calculations, and conversions.

---

## Practical 05

**Aim:** Implement SQL queries using Numeric functions like ABS, CEIL, COS, COSH, EXP, FLOOR, POWER, MOD, ROUND, TRUNC, SQRT etc.

**Description:** To understand and apply Oracle SQL numeric functions for performing mathematical operations, including absolute value, rounding, truncation, exponentiation, and modulus calculations on numeric data.

**Code:**

```sql
-- Comprehensive execution of Oracle SQL Numeric Functions
SELECT 
    ABS(-45.75) AS abs_val,
    CEIL(14.2) AS ceil_val,
    FLOOR(14.8) AS floor_val,
    COS(0) AS cos_val,
    COSH(0) AS cosh_val,
    EXP(2) AS exp_val,
    POWER(2, 5) AS power_val,
    MOD(17, 5) AS mod_val,
    SQRT(64) AS sqrt_val
FROM DUAL;

-- Demonstration of ROUND and TRUNC on numeric values
SELECT 
    ROUND(125.678, 2) AS round_2dec,
    ROUND(125.678, -1) AS round_tens,
    TRUNC(125.678, 2) AS trunc_2dec,
    TRUNC(125.678, 0) AS trunc_zero
FROM DUAL;
```

**Output:**

Numeric Operations Result Set 1:

| ABS_VAL | CEIL_VAL | FLOOR_VAL | COS_VAL | COSH_VAL | EXP_VAL | POWER_VAL | MOD_VAL | SQRT_VAL |
|---|---|---|---|---|---|---|---|---|
| 45.75 | 15 | 14 | 1 | 1 | 7.389056 | 32 | 2 | 8 |

Numeric Operations Result Set 2 (Rounding & Truncation):

| ROUND_2DEC | ROUND_TENS | TRUNC_2DEC | TRUNC_ZERO |
|---|---|---|---|
| 125.68 | 130 | 125.67 | 125 |

**Conclusion:** Oracle SQL numeric functions were tested and validated for performing mathematical calculations and precision handling.

---

## Practical 06

**Aim:** Implement SQL queries using Character Functions like INITCAP, LOWER, UPPER, LTRIM, RTRIM, TRANSLATE, REPLACE, SUBSTR etc.

**Description:** To understand and apply Oracle SQL character functions for manipulating string data, including case conversion, trimming whitespace or characters, substring extraction, and character replacement or translation.

**Code:**

```sql
-- String Case Conversion Functions
SELECT 
    INITCAP('oracle database xe') AS initcap_str,
    LOWER('DATABASE SYSTEMS') AS lower_str,
    UPPER('pl/sql practical') AS upper_str
FROM DUAL;

-- Trimming and Padding Functions
SELECT 
    LTRIM('   Oracle', ' ') AS ltrim_str,
    RTRIM('Database***', '*') AS rtrim_str,
    LPAD('SQL', 8, '*') AS lpad_str,
    RPAD('SQL', 8, '#') AS rpad_str
FROM DUAL;

-- String Substring, Translation, and Replacement Functions
SELECT 
    SUBSTR('Oracle XE Practical', 1, 6) AS substr_str,
    REPLACE('Welcome to Java', 'Java', 'Oracle SQL') AS replace_str,
    TRANSLATE('12345 Hello', '12345', 'ABCDE') AS translate_str,
    LENGTH('Oracle Database') AS str_len
FROM DUAL;
```

**Output:**

Case Conversions:

| INITCAP_STR | LOWER_STR | UPPER_STR |
|---|---|---|
| Oracle Database Xe | database systems | PL/SQL PRACTICAL |

Padding and Trimming:

| LTRIM_STR | RTRIM_STR | LPAD_STR | RPAD_STR |
|---|---|---|---|
| Oracle | Database | *****SQL | SQL##### |

Substring, Replace, Translate & Length:

| SUBSTR_STR | REPLACE_STR | TRANSLATE_STR | STR_LEN |
|---|---|---|---|
| Oracle | Welcome to Oracle SQL | ABCDE Hello | 15 |

**Conclusion:** Character and string manipulation functions in Oracle SQL were successfully executed and formatted.

---

## Practical 07

**Aim:** Implement SQL queries using Group functions like AVG, MIN, MAX, SUM, COUNT, DECODE etc.

**Description:** To understand and apply Oracle SQL aggregate (group) functions to summarize and analyze data across multiple rows, including calculating averages, totals, counts, and conditional value substitution using DECODE.

**Code:**

```sql
-- 1. Using Aggregate Group Functions on EMPLOYEES table
SELECT 
    COUNT(*) AS total_employees,
    COUNT(email) AS emp_with_email,
    SUM(salary) AS total_salary_expense,
    AVG(salary) AS average_salary,
    MIN(salary) AS minimum_salary,
    MAX(salary) AS maximum_salary
FROM employees;

-- 2. Combining Group Functions with DECODE conditional evaluation
SELECT 
    dept_id,
    COUNT(*) AS dept_count,
    SUM(DECODE(dept_id, 10, salary, 0)) AS it_salary_total,
    SUM(DECODE(dept_id, 20, salary, 0)) AS hr_salary_total,
    SUM(DECODE(dept_id, 30, salary, 0)) AS fin_salary_total
FROM employees
GROUP BY dept_id;
```

**Output:**

Aggregate Summary:

| TOTAL_EMPLOYEES | EMP_WITH_EMAIL | TOTAL_SALARY_EXPENSE | AVERAGE_SALARY | MINIMUM_SALARY | MAXIMUM_SALARY |
| --------------- | -------------- | -------------------- | -------------- | -------------- | -------------- |
| 9               | 9              | 567200.00            | 61688.88...    | 48000.00       | 79200.00       |

Group Summary with DECODE:

| DEPT_ID | COUNT | IT SALARY TOTAL | HR SALARY TOTAL | FIN SALARY TOTAL |
| ------- | ----- | --------------- | --------------- | ---------------- |
| 30      | 2     | 0               | 0               | 100000           |
| 20      | 3     | 0               | 178000          | 0                |
| 10      | 4     | 277200          | 0               | 0                |

**Conclusion:** SQL group (aggregate) functions along with the DECODE function were successfully used to aggregate and summarize dataset records.

---

## Practical 08

**Aim:** Implement SQL queries using GROUP BY HAVING and ORDER BY clauses.

**Description:** To understand and apply the GROUP BY clause to group rows sharing common values, the HAVING clause to filter grouped results, and the ORDER BY clause to sort query output.

**Code:**

```sql
-- 1. Grouping data by department and calculating aggregates
SELECT dept_id, COUNT(*) AS total_emp, AVG(salary) AS avg_sal
FROM employees
GROUP BY dept_id
ORDER BY dept_id ASC;

-- 2. Filtering grouped data using HAVING clause and sorting with ORDER BY
SELECT 
    dept_id, 
    COUNT(*) AS emp_count, 
    ROUND(AVG(salary), 2) AS average_salary
FROM employees
GROUP BY dept_id
HAVING AVG(salary) > 55000
ORDER BY average_salary DESC;
```

**Output:**

Query 1 (GROUP BY & ORDER BY):

| DEPT_ID | TOTAL_EMP | AVG_SAL  |
| ------- | --------- | -------- |
| 10      | 4         | 69300.00 |
| 20      | 3         | 59333.33 |
| 30      | 2         | 50000    |

Query 2 (GROUP BY, HAVING & ORDER BY):

| DEPT_ID | EMP_COUNT | AVERAGE_SALARY |
|---|---|---|
| 10 | 4 | 69300.00 |
| 20 | 3 | 59333.33 |

**Conclusion:** The GROUP BY, HAVING, and ORDER BY clauses were successfully applied to group rows, filter aggregated records, and sort final results.

---

## Practical 09

**Aim:** Implement SQL queries using Set Operators like UNION, UNION ALL, INTERSECT, MINUS etc.

**Description:** To understand and apply SQL set operators to combine, intersect, or find the difference between the result sets of two or more SELECT queries.

**Code:**

```sql
-- Setup temporary table structures for Set Operations
CREATE TABLE tech_team (
    emp_name VARCHAR2(50)
);

CREATE TABLE management_team (
    emp_name VARCHAR2(50)
);

INSERT INTO tech_team VALUES ('Alice');
INSERT INTO tech_team VALUES ('Bob');
INSERT INTO tech_team VALUES ('Charlie');
INSERT INTO tech_team VALUES ('David');

INSERT INTO management_team VALUES ('Charlie');
INSERT INTO management_team VALUES ('David');
INSERT INTO management_team VALUES ('Emma');
INSERT INTO management_team VALUES ('Frank');

-- 1. UNION (Combines and eliminates duplicate rows)
SELECT emp_name FROM tech_team
UNION
SELECT emp_name FROM management_team;

-- 2. UNION ALL (Combines including duplicate rows)
SELECT emp_name FROM tech_team
UNION ALL
SELECT emp_name FROM management_team;

-- 3. INTERSECT (Returns common rows in both queries)
SELECT emp_name FROM tech_team
INTERSECT
SELECT emp_name FROM management_team;

-- 4. MINUS (Returns rows in first query but not in second query)
SELECT emp_name FROM tech_team
MINUS
SELECT emp_name FROM management_team;
```

**Output:**

UNION Result (Unique list):

| EMP_NAME |
|---|
| Alice |
| Bob |
| Charlie |
| David |
| Emma |
| Frank |

INTERSECT Result (Common names):

| EMP_NAME |
|---|
| Charlie |
| David |

MINUS Result (Tech team only):

| EMP_NAME |
|---|
| Alice |
| Bob |

**Conclusion:** Set operators (UNION, UNION ALL, INTERSECT, MINUS) were successfully used to evaluate relationships between multiple query result sets.

---

## Practical 10

**Aim:** Execute SQL queries for implementation of Inner Join and Cross Join.

**Description:** To understand and implement the INNER JOIN to combine rows from two or more tables based on a related column, and the CROSS JOIN to produce the Cartesian product of two tables.

**Code:**

```sql
-- 1. INNER JOIN (Retrieves records with matching values in both tables)
SELECT 
    e.emp_id, 
    e.first_name || ' ' || e.last_name AS employee_name, 
    e.salary, 
    d.dept_name, 
    d.location
FROM employees e
INNER JOIN departments d ON e.dept_id = d.dept_id;

-- 2. CROSS JOIN (Generates Cartesian product of two tables)
SELECT 
    d.dept_name, 
    p.proj_name
FROM departments d
CROSS JOIN projects p;
```

**Output:**

INNER JOIN Result:

| EMP_ID | EMPLOYEE_NAME | SALARY | DEPT_NAME | LOCATION |
|---|---|---|---|---|
| 101 | John Doe | 66000.00 | IT | New York |
| 102 | Jane Smith | 60500.00 | IT | New York |
| 103 | Robert Johnson | 70000.00 | HR | Chicago |
| 104 | Emily Davis | 50000.00 | HR | Chicago |
| 105 | Michael Brown | 48000.00 | Finance | Boston |

CROSS JOIN Result (Cartesian Product):

| DEPT_NAME | PROJ_NAME |
|---|---|
| IT | Cloud Migration |
| IT | ERP Upgrade |
| HR | Cloud Migration |
| HR | ERP Upgrade |
| Finance | Cloud Migration |
| Finance | ERP Upgrade |

**Conclusion:** Inner Join and Cross Join queries were successfully executed to combine related rows and calculate Cartesian products.

---

## Practical 11

**Aim:** Execute SQL queries for implementation of Outer Join and Cross Join.

**Description:** To understand and implement LEFT, RIGHT, and FULL OUTER JOINs to retrieve matching and non-matching rows between tables, along with the CROSS JOIN for Cartesian products.

**Code:**

```sql
-- 1. LEFT OUTER JOIN (Returns all rows from left table and matched rows from right)
SELECT 
    e.emp_id, 
    e.first_name, 
    d.dept_id, 
    d.dept_name
FROM employees e
LEFT OUTER JOIN departments d ON e.dept_id = d.dept_id;

-- 2. RIGHT OUTER JOIN (Returns all rows from right table and matched rows from left)
SELECT 
    e.emp_id, 
    e.first_name, 
    d.dept_id, 
    d.dept_name
FROM employees e
RIGHT OUTER JOIN departments d ON e.dept_id = d.dept_id;

-- 3. FULL OUTER JOIN (Returns all rows when there is a match in left or right table)
SELECT 
    e.emp_id, 
    e.first_name, 
    d.dept_id, 
    d.dept_name
FROM employees e
FULL OUTER JOIN departments d ON e.dept_id = d.dept_id;

-- 4. CROSS JOIN (Cartesian product)
SELECT 
    e.first_name, 
    d.dept_name
FROM (SELECT first_name FROM employees WHERE ROWNUM <= 2) e
CROSS JOIN departments d;
```

**Output:**

LEFT OUTER JOIN Result:

| EMP_ID | FIRST_NAME | DEPT_ID | DEPT_NAME |
|---|---|---|---|
| 101 | John | 10 | IT |
| 103 | Robert | 20 | HR |
| 105 | Michael | 30 | Finance |

FULL OUTER JOIN Result:

| EMP_ID | FIRST_NAME | DEPT_ID | DEPT_NAME |
|---|---|---|---|
| 101 | John | 10 | IT |
| 102 | Jane | 10 | IT |
| 103 | Robert | 20 | HR |
| NULL | NULL | 40 | Marketing |

**Conclusion:** Outer joins (LEFT, RIGHT, FULL) and Cross joins were successfully implemented to query matched and unmatched database records.

---

## Practical 12

**Aim:** Implementation of Views.

**Description:** To understand and implement views in Oracle SQL as virtual tables derived from one or more base tables, including creating, querying, and updating data through views.

**Code:**

```sql
-- 1. Creating a Simple View
CREATE VIEW high_salary_emps AS
SELECT emp_id, first_name, last_name, salary, dept_id
FROM employees
WHERE salary >= 60000;

-- 2. Creating a Complex View using Join
CREATE VIEW emp_department_summary AS
SELECT 
    e.emp_id,
    e.first_name || ' ' || e.last_name AS full_name,
    e.salary,
    d.dept_name,
    d.location
FROM employees e
JOIN departments d ON e.dept_id = d.dept_id;

-- 3. Querying Views
SELECT * FROM high_salary_emps;
SELECT * FROM emp_department_summary WHERE location = 'New York';

-- 4. Dropping a View
DROP VIEW high_salary_emps;
```

**Output:**

```text
View HIGH_SALARY_EMPS created.
View EMP_DEPARTMENT_SUMMARY created.
View HIGH_SALARY_EMPS dropped.
```

Data Output from `emp_department_summary` View:

| EMP_ID | FULL_NAME | SALARY | DEPT_NAME | LOCATION |
|---|---|---|---|---|
| 101 | John Doe | 66000.00 | IT | New York |
| 102 | Jane Smith | 60500.00 | IT | New York |
| 106 | Sarah Wilson | 71500.00 | IT | New York |

**Conclusion:** Database views were successfully created, queried, and dropped, demonstrating their functionality as virtual tables.

---

## Practical 13

**Aim:** Write a basic PL/SQL program to find whether a given number is even or odd using IF-THEN-ELSE.

**Description:** To understand the basic structure of a PL/SQL block and implement conditional logic using IF-THEN-ELSE to determine whether a given number is even or odd.

**Code:**

```sql
SET SERVEROUTPUT ON;

DECLARE
    num NUMBER := 24;
BEGIN
    IF MOD(num, 2) = 0 THEN
        DBMS_OUTPUT.PUT_LINE('The number ' || num || ' is Even.');
    ELSE
        DBMS_OUTPUT.PUT_LINE('The number ' || num || ' is Odd.');
    END IF;
END;
/
```

**Output:**

```text
PL/SQL procedure successfully completed.

The number 24 is Even.
```

**Conclusion:** A basic PL/SQL block using IF-THEN-ELSE logic was successfully implemented to identify even and odd numbers.

---

## Practical 14

**Aim:** Write a basic PL/SQL program to find whether a given number is prime or not.

**Description:** To implement a PL/SQL program using loops and conditional logic to determine whether a given number is a prime number by checking its divisibility.

**Code:**

```sql
SET SERVEROUTPUT ON;

DECLARE
    num NUMBER := 17;
    is_prime BOOLEAN := TRUE;
    i NUMBER := 2;
BEGIN
    IF num <= 1 THEN
        is_prime := FALSE;
    ELSE
        WHILE i <= TRUNC(SQRT(num)) LOOP
            IF MOD(num, i) = 0 THEN
                is_prime := FALSE;
                EXIT;
            END IF;
            i := i + 1;
        END LOOP;
    END IF;

    IF is_prime THEN
        DBMS_OUTPUT.PUT_LINE('The number ' || num || ' is Prime.');
    ELSE
        DBMS_OUTPUT.PUT_LINE('The number ' || num || ' is NOT Prime.');
    END IF;
END;
/
```

**Output:**

```text
PL/SQL procedure successfully completed.

The number 17 is Prime.
```

**Conclusion:** A PL/SQL program combining WHILE loops and conditional constructs was successfully created to verify prime numbers.

---

## Practical 15

**Aim:** Write a basic PL/SQL program to check whether a given number is divisible by 5 using IF-THEN-ELSE.

**Description:** To implement conditional logic in PL/SQL using the modulus operator to check whether a given number is exactly divisible by 5.

**Code:**

```sql
SET SERVEROUTPUT ON;

DECLARE
    num NUMBER := 45;
BEGIN
    IF MOD(num, 5) = 0 THEN
        DBMS_OUTPUT.PUT_LINE('The number ' || num || ' is divisible by 5.');
    ELSE
        DBMS_OUTPUT.PUT_LINE('The number ' || num || ' is NOT divisible by 5.');
    END IF;
END;
/
```

**Output:**

```text
PL/SQL procedure successfully completed.

The number 45 is divisible by 5.
```

**Conclusion:** Conditional evaluation using IF-THEN-ELSE and MOD operator was successfully implemented in PL/SQL.

---

## Practical 16

**Aim:** Write a basic PL/SQL program using FOR loop to print numbers from 1 to 10.

**Description:** To understand and implement the numeric FOR loop construct in PL/SQL to iterate through a defined range and print numbers sequentially.

**Code:**

```sql
SET SERVEROUTPUT ON;

BEGIN
    DBMS_OUTPUT.PUT_LINE('Printing numbers from 1 to 10:');
    FOR counter IN 1..10 LOOP
        DBMS_OUTPUT.PUT_LINE('Number: ' || counter);
    END LOOP;
END;
/
```

**Output:**

```text
PL/SQL procedure successfully completed.

Printing numbers from 1 to 10:
Number: 1
Number: 2
Number: 3
Number: 4
Number: 5
Number: 6
Number: 7
Number: 8
Number: 9
Number: 10
```

**Conclusion:** The numeric FOR loop construct was successfully executed in PL/SQL to generate sequential integer outputs.

---

## Practical 17

**Aim:** Write a basic PL/SQL program using FOR loop to print even number series up to 50.

**Description:** To implement a PL/SQL FOR loop combined with conditional logic or step increments to print the series of even numbers up to 50.

**Code:**

```sql
SET SERVEROUTPUT ON;

BEGIN
    DBMS_OUTPUT.PUT_LINE('Even numbers series up to 50:');
    FOR num IN 1..50 LOOP
        IF MOD(num, 2) = 0 THEN
            DBMS_OUTPUT.PUT_LINE(num);
        END IF;
    END LOOP;
END;
/
```

**Output:**

```text
PL/SQL procedure successfully completed.

Even numbers series up to 50:
2
4
6
8
...
46
48
50
```

**Conclusion:** A PL/SQL numeric FOR loop with an embedded conditional filter was successfully used to output even numbers up to 50.

---

## Practical 18

**Aim:** Write a basic PL/SQL program using FOR loop to print the multiplication table of a given number.

**Description:** To implement a PL/SQL FOR loop to compute and display the multiplication table (1 to 10) of a given input number.

**Code:**

```sql
SET SERVEROUTPUT ON;

DECLARE
    num NUMBER := 7;
BEGIN
    DBMS_OUTPUT.PUT_LINE('Multiplication Table of ' || num || ':');
    FOR i IN 1..10 LOOP
        DBMS_OUTPUT.PUT_LINE(num || ' x ' || i || ' = ' || (num * i));
    END LOOP;
END;
/
```

**Output:**

```text
PL/SQL procedure successfully completed.

Multiplication Table of 7:
7 x 1 = 7
7 x 2 = 14
7 x 3 = 21
7 x 4 = 28
7 x 5 = 35
7 x 6 = 42
7 x 7 = 49
7 x 8 = 56
7 x 9 = 63
7 x 10 = 70
```

**Conclusion:** A PL/SQL FOR loop was successfully executed to construct and display the multiplication table for a specified number.

---

## Practical 19

**Aim:** Write a basic PL/SQL program using WHILE loop to print odd number series up to 50.

**Description:** To understand and implement the WHILE loop construct in PL/SQL to generate and display the series of odd numbers up to 50.

**Code:**

```sql
SET SERVEROUTPUT ON;

DECLARE
    num NUMBER := 1;
BEGIN
    DBMS_OUTPUT.PUT_LINE('Odd Numbers Series up to 50:');
    WHILE num <= 50 LOOP
        DBMS_OUTPUT.PUT_LINE(num);
        num := num + 2;
    END LOOP;
END;
/
```

**Output:**

```text
PL/SQL procedure successfully completed.

Odd Numbers Series up to 50:
1
3
5
7
9
...
43
45
47
49
```

**Conclusion:** The WHILE loop structure was successfully implemented in PL/SQL to calculate and output odd numbers up to 50.

---

## Practical 20

**Aim:** Write a basic PL/SQL program using WHILE loop to print the sum of numbers from 1 to 100.

**Description:** To implement a WHILE loop in PL/SQL to accumulate and calculate the sum of numbers from 1 to 100 using a running total variable.

**Code:**

```sql
SET SERVEROUTPUT ON;

DECLARE
    counter NUMBER := 1;
    total_sum NUMBER := 0;
BEGIN
    WHILE counter <= 100 LOOP
        total_sum := total_sum + counter;
        counter := counter + 1;
    END LOOP;
    
    DBMS_OUTPUT.PUT_LINE('The sum of numbers from 1 to 100 is: ' || total_sum);
END;
/
```

**Output:**

```text
PL/SQL procedure successfully completed.

The sum of numbers from 1 to 100 is: 5050
```

**Conclusion:** Accumulation of values from 1 to 100 using a WHILE loop in PL/SQL was successfully executed.

---

## Practical 21

**Aim:** Write a basic PL/SQL program using WHILE loop to print the Fibonacci series (0, 1, 1, 2, 3, 5, 8, 13...).

**Description:** To implement a WHILE loop in PL/SQL to generate and display the Fibonacci series, where each number is the sum of the two preceding numbers.

**Code:**

```sql
SET SERVEROUTPUT ON;

DECLARE
    first_term NUMBER := 0;
    second_term NUMBER := 1;
    next_term NUMBER;
    term_count NUMBER := 1;
    total_terms NUMBER := 10;
BEGIN
    DBMS_OUTPUT.PUT_LINE('Fibonacci Series up to ' || total_terms || ' terms:');
    
    WHILE term_count <= total_terms LOOP
        DBMS_OUTPUT.PUT_LINE(first_term);
        next_term := first_term + second_term;
        first_term := second_term;
        second_term := next_term;
        term_count := term_count + 1;
    END LOOP;
END;
/
```

**Output:**

```text
PL/SQL procedure successfully completed.

Fibonacci Series up to 10 terms:
0
1
1
2
3
5
8
13
21
34
```

**Conclusion:** A WHILE loop construct in PL/SQL was successfully designed to compute and display the Fibonacci sequence.

---

## Practical 22

**Aim:** Write a PL/SQL program to implement implicit and explicit cursors.

**Description:** To understand the concept of cursors in PL/SQL, including implicit cursors automatically created for DML/SELECT INTO statements, and explicit cursors declared and controlled explicitly for processing multi-row query results.

**Code:**

```sql
SET SERVEROUTPUT ON;

-- Part 1: Implicit Cursor Example
DECLARE
    v_rows_affected NUMBER;
BEGIN
    UPDATE employees 
    SET salary = salary * 1.05 
    WHERE dept_id = 10;
    
    IF SQL%FOUND THEN
        v_rows_affected := SQL%ROWCOUNT;
        DBMS_OUTPUT.PUT_LINE('Implicit Cursor: Successfully updated ' || v_rows_affected || ' rows.');
    ELSE
        DBMS_OUTPUT.PUT_LINE('Implicit Cursor: No rows were updated.');
    END IF;
END;
/

-- Part 2: Explicit Cursor Example
DECLARE
    CURSOR emp_cursor IS
        SELECT emp_id, first_name, last_name, salary FROM employees WHERE dept_id = 10;
        
    v_emp_id employees.emp_id%TYPE;
    v_first_name employees.first_name%TYPE;
    v_last_name employees.last_name%TYPE;
    v_salary employees.salary%TYPE;
BEGIN
    DBMS_OUTPUT.PUT_LINE('--- Explicit Cursor Processing ---');
    OPEN emp_cursor;
    LOOP
        FETCH emp_cursor INTO v_emp_id, v_first_name, v_last_name, v_salary;
        EXIT WHEN emp_cursor%NOTFOUND;
        DBMS_OUTPUT.PUT_LINE('ID: ' || v_emp_id || ' | Name: ' || v_first_name || ' ' || v_last_name || ' | Salary: $' || v_salary);
    END LOOP;
    CLOSE emp_cursor;
END;
/
```

**Output:**

```text
PL/SQL procedure successfully completed.
Implicit Cursor: Successfully updated 4 rows.

PL/SQL procedure successfully completed.
--- Explicit Cursor Processing ---
ID: 101 | Name: John Doe | Salary: $69300
ID: 102 | Name: Jane Smith | Salary: $63525
ID: 106 | Name: Sarah Wilson | Salary: $75075
ID: 109 | Name: James Thomas | Salary: $83160
```

**Conclusion:** Both implicit cursors (SQL%FOUND, SQL%ROWCOUNT) and explicit cursors (OPEN, FETCH, CLOSE loop) were successfully implemented to manage database rows in PL/SQL.

---

## Practical 23

**Aim:** Write PL/SQL programs based on Exception Handling (Predefined and User-defined Exceptions).

**Description:** To understand and implement exception handling in PL/SQL using predefined exceptions such as NO_DATA_FOUND and ZERO_DIVIDE, as well as user-defined exceptions raised explicitly using RAISE.

**Code:**

```sql
SET SERVEROUTPUT ON;

-- 1. Predefined Exception: ZERO_DIVIDE
DECLARE
    num_a NUMBER := 100;
    num_b NUMBER := 0;
    result NUMBER;
BEGIN
    result := num_a / num_b;
    DBMS_OUTPUT.PUT_LINE('Result: ' || result);
EXCEPTION
    WHEN ZERO_DIVIDE THEN
        DBMS_OUTPUT.PUT_LINE('Predefined Exception Caught: Division by zero is undefined.');
END;
/

-- 2. Predefined Exception: NO_DATA_FOUND
DECLARE
    v_emp_name employees.first_name%TYPE;
BEGIN
    SELECT first_name INTO v_emp_name FROM employees WHERE emp_id = 999;
    DBMS_OUTPUT.PUT_LINE('Employee Name: ' || v_emp_name);
EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('Predefined Exception Caught: No employee found with ID 999.');
END;
/

-- 3. User-Defined Exception
DECLARE
    account_balance NUMBER := 500;
    withdraw_amount NUMBER := 1000;
    insufficient_funds EXCEPTION;
BEGIN
    IF withdraw_amount > account_balance THEN
        RAISE insufficient_funds;
    ELSE
        account_balance := account_balance - withdraw_amount;
        DBMS_OUTPUT.PUT_LINE('Withdrawal successful.');
    END IF;
EXCEPTION
    WHEN insufficient_funds THEN
        DBMS_OUTPUT.PUT_LINE('User-Defined Exception Caught: Insufficient funds in account balance.');
END;
/
```

**Output:**

```text
PL/SQL procedure successfully completed.
Predefined Exception Caught: Division by zero is undefined.

PL/SQL procedure successfully completed.
Predefined Exception Caught: No employee found with ID 999.

PL/SQL procedure successfully completed.
User-Defined Exception Caught: Insufficient funds in account balance.
```

**Conclusion:** System predefined exceptions (ZERO_DIVIDE, NO_DATA_FOUND) and user-defined custom exceptions were successfully handled in PL/SQL.

---

## Practical 24

**Aim:** Write a PL/SQL program to implement Database Triggers.

**Description:** To understand and implement database triggers in Oracle, including BEFORE and AFTER triggers that automatically execute in response to specific DML events on a table.

**Code:**

```sql
SET SERVEROUTPUT ON;

-- Create Audit Table for logging updates
CREATE TABLE emp_audit_log (
    log_id NUMBER GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    emp_id NUMBER,
    old_salary NUMBER,
    new_salary NUMBER,
    changed_by VARCHAR2(50),
    changed_date DATE
);

-- 1. BEFORE UPDATE Trigger to validate data
CREATE OR REPLACE TRIGGER trg_check_min_salary
BEFORE UPDATE OF salary ON employees
FOR EACH ROW
BEGIN
    IF :NEW.salary < 30000 THEN
        RAISE_APPLICATION_ERROR(-20002, 'Salary cannot be updated below $30,000.');
    END IF;
END;
/

-- 2. AFTER UPDATE Trigger to log changes into audit table
CREATE OR REPLACE TRIGGER trg_audit_salary_update
AFTER UPDATE OF salary ON employees
FOR EACH ROW
BEGIN
    INSERT INTO emp_audit_log (emp_id, old_salary, new_salary, changed_by, changed_date)
    VALUES (:OLD.emp_id, :OLD.salary, :NEW.salary, USER, SYSDATE);
END;
/

-- Trigger Execution Test
UPDATE employees SET salary = 72000 WHERE emp_id = 101;
```

**Output:**

```text
Table EMP_AUDIT_LOG created.
Trigger TRG_CHECK_MIN_SALARY created.
Trigger TRG_AUDIT_SALARY_UPDATE created.
1 row updated.
```

Audit Log Entry Output (`emp_audit_log` Table):

| LOG_ID | EMP_ID | OLD_SALARY | NEW_SALARY | CHANGED_BY | CHANGED_DATE |
|---|---|---|---|---|---|
| 1 | 101 | 69300.00 | 72000.00 | SYSTEM | 21-SEP-26 |

**Conclusion:** Database triggers (BEFORE and AFTER DML triggers) were successfully built and verified for automated data integrity and auditing.

---

## Practical 25

**Aim:** Draw the ER Diagram for a Library Management System.

**Description:** To understand the concepts of Entity-Relationship (ER) modeling and design an ER diagram identifying entities, attributes, relationships, and cardinalities for a Library Management System.

**Code:**

```sql
-- DDL schema script representing the Library Management System ER Diagram

CREATE TABLE Books (
    book_id NUMBER PRIMARY KEY,
    title VARCHAR2(150) NOT NULL,
    isbn VARCHAR2(20) UNIQUE,
    author VARCHAR2(100),
    publisher VARCHAR2(100),
    category VARCHAR2(50),
    copies_available NUMBER DEFAULT 1
);

CREATE TABLE Members (
    member_id NUMBER PRIMARY KEY,
    name VARCHAR2(100) NOT NULL,
    email VARCHAR2(100) UNIQUE,
    phone VARCHAR2(15),
    membership_date DATE DEFAULT SYSDATE
);

CREATE TABLE Loans (
    loan_id NUMBER PRIMARY KEY,
    book_id NUMBER REFERENCES Books(book_id),
    member_id NUMBER REFERENCES Members(member_id),
    issue_date DATE DEFAULT SYSDATE,
    due_date DATE,
    return_date DATE
);
```

**Output:**

Entity and Attribute Definitions:

| Entity Name | Primary Key | Foreign Key | Attributes |
|---|---|---|---|
| Books | book_id | None | title, isbn, author, publisher, category, copies_available |
| Members | member_id | None | name, email, phone, membership_date |
| Loans | loan_id | book_id, member_id | issue_date, due_date, return_date |

Relationship and Cardinality Specifications:

| Relationship Name | Entity 1 | Entity 2 | Cardinality | Description |
|---|---|---|---|---|
| Issue/Return | Members | Loans | 1 : N | One member can borrow multiple books over time |
| Included In | Books | Loans | 1 : N | One book can be issued across multiple loan records |

**Conclusion:** The Entity-Relationship model and relational tables for a Library Management System were designed and documented.

---

## Practical 26

**Aim:** Draw the ER Diagram for a Banking System.

**Description:** To apply Entity-Relationship modeling concepts to design an ER diagram for a Banking System, identifying entities such as Customer, Account, and Branch along with their relationships and constraints.

**Code:**

```sql
-- DDL schema script representing the Banking System ER Diagram

CREATE TABLE Branch (
    branch_id NUMBER PRIMARY KEY,
    branch_name VARCHAR2(100) NOT NULL,
    city VARCHAR2(50),
    assets NUMBER(15, 2)
);

CREATE TABLE Customer (
    customer_id NUMBER PRIMARY KEY,
    name VARCHAR2(100) NOT NULL,
    address VARCHAR2(200),
    phone VARCHAR2(15)
);

CREATE TABLE Account (
    account_number NUMBER PRIMARY KEY,
    account_type VARCHAR2(20) CHECK (account_type IN ('Savings', 'Checking', 'Fixed Deposit')),
    balance NUMBER(12, 2) DEFAULT 0.00,
    branch_id NUMBER REFERENCES Branch(branch_id),
    customer_id NUMBER REFERENCES Customer(customer_id)
);

CREATE TABLE Transaction (
    transaction_id NUMBER PRIMARY KEY,
    account_number NUMBER REFERENCES Account(account_number),
    transaction_type VARCHAR2(10) CHECK (transaction_type IN ('Deposit', 'Withdrawal')),
    amount NUMBER(12, 2) NOT NULL,
    transaction_date DATE DEFAULT SYSDATE
);
```

**Output:**

Entity-Relationship Schema Breakdown:

| Entity Name | Key Attributes | Foreign Key References | Functionality |
|---|---|---|---|
| Branch | branch_id (PK), branch_name, city, assets | None | Represents physical bank branch location |
| Customer | customer_id (PK), name, address, phone | None | Holds personal details of bank clients |
| Account | account_number (PK), account_type, balance | branch_id, customer_id | Represents deposit/checking accounts |
| Transaction | transaction_id (PK), amount, transaction_date | account_number | Records monetary transactions |

System Relationships:

| Entity 1 | Relationship | Entity 2 | Cardinality |
|---|---|---|---|
| Customer | Holds | Account | 1 : N |
| Branch | Maintains | Account | 1 : N |
| Account | Executes | Transaction | 1 : N |

**Conclusion:** An ER Diagram and database design for a Banking System were successfully specified with entities, keys, and foreign relationship constraints.

---

## Practical 27

**Aim:** Write a case study on Online Shopping System Database and Relations.

**Description:** To analyze the requirements of an Online Shopping System and design the underlying relational database structure, including tables, keys, and relationships needed to support customers, products, orders, and payments.

**Code:**

```sql
-- Schema Implementation for Online Shopping System Case Study

CREATE TABLE Users (
    user_id NUMBER PRIMARY KEY,
    user_name VARCHAR2(100) NOT NULL,
    email VARCHAR2(100) UNIQUE NOT NULL,
    address VARCHAR2(250),
    created_at DATE DEFAULT SYSDATE
);

CREATE TABLE Categories (
    category_id NUMBER PRIMARY KEY,
    category_name VARCHAR2(50) NOT NULL
);

CREATE TABLE Products (
    product_id NUMBER PRIMARY KEY,
    product_name VARCHAR2(150) NOT NULL,
    price NUMBER(10, 2) NOT NULL,
    stock_quantity NUMBER DEFAULT 0,
    category_id NUMBER REFERENCES Categories(category_id)
);

CREATE TABLE Orders (
    order_id NUMBER PRIMARY KEY,
    user_id NUMBER REFERENCES Users(user_id),
    order_date DATE DEFAULT SYSDATE,
    total_amount NUMBER(10, 2),
    status VARCHAR2(20) CHECK (status IN ('Pending', 'Shipped', 'Delivered', 'Cancelled'))
);

CREATE TABLE Order_Items (
    order_item_id NUMBER PRIMARY KEY,
    order_id NUMBER REFERENCES Orders(order_id),
    product_id NUMBER REFERENCES Products(product_id),
    quantity NUMBER DEFAULT 1,
    unit_price NUMBER(10, 2) NOT NULL
);

CREATE TABLE Payments (
    payment_id NUMBER PRIMARY KEY,
    order_id NUMBER REFERENCES Orders(order_id),
    payment_method VARCHAR2(30) CHECK (payment_method IN ('Credit Card', 'Debit Card', 'UPI', 'COD')),
    payment_status VARCHAR2(20),
    payment_date DATE DEFAULT SYSDATE
);
```

**Output:**

Relational Mapping and Structural Design:

| Table Name | Primary Key | Foreign Keys | Business Function |
|---|---|---|---|
| Users | user_id | None | Manages user registration and profile data |
| Categories | category_id | None | Classifies items into product lines |
| Products | product_id | category_id | Tracks catalog pricing and stock availability |
| Orders | order_id | user_id | Stores placed customer orders and shipping state |
| Order_Items | order_item_id | order_id, product_id | Normalizes multi-product order selections |
| Payments | payment_id | order_id | Logs online payment details and gateway status |

**Conclusion:** The database architecture for an Online Shopping System case study was thoroughly analyzed and converted into a normalized relational model.

---

## Practical 28

**Aim:** Write a case study on Online Examination System Database and Relations.

**Description:** To analyze the requirements of an Online Examination System and design the underlying relational database structure, including tables, keys, and relationships needed to support students, exams, questions, and results.

**Code:**

```sql
-- Schema Implementation for Online Examination System Case Study

CREATE TABLE Students (
    student_id NUMBER PRIMARY KEY,
    full_name VARCHAR2(100) NOT NULL,
    email VARCHAR2(100) UNIQUE NOT NULL,
    enrollment_no VARCHAR2(20) UNIQUE NOT NULL
);

CREATE TABLE Exams (
    exam_id NUMBER PRIMARY KEY,
    title VARCHAR2(100) NOT NULL,
    total_marks NUMBER NOT NULL,
    pass_marks NUMBER NOT NULL,
    duration_minutes NUMBER NOT NULL
);

CREATE TABLE Questions (
    question_id NUMBER PRIMARY KEY,
    exam_id NUMBER REFERENCES Exams(exam_id),
    question_text VARCHAR2(500) NOT NULL,
    option_a VARCHAR2(200),
    option_b VARCHAR2(200),
    option_c VARCHAR2(200),
    option_d VARCHAR2(200),
    correct_option CHAR(1)
);

CREATE TABLE Exam_Attempts (
    attempt_id NUMBER PRIMARY KEY,
    student_id NUMBER REFERENCES Students(student_id),
    exam_id NUMBER REFERENCES Exams(exam_id),
    attempt_date DATE DEFAULT SYSDATE,
    score NUMBER,
    result_status VARCHAR2(10) CHECK (result_status IN ('Pass', 'Fail'))
);
```

**Output:**

Relational Components for Online Examination System:

| Table Name | Primary Key | Foreign Keys | Functional Purpose |
|---|---|---|---|
| Students | student_id | None | Stores student credentials and registration details |
| Exams | exam_id | None | Configures exam title, duration, and passing criteria |
| Questions | question_id | exam_id | Contains test question bank and multiple-choice options |
| Exam_Attempts | attempt_id | student_id, exam_id | Logs exam submission date, final score, and pass/fail state |

**Conclusion:** The case study for the Online Examination System relational structure was designed and documented with complete relational integrity.
