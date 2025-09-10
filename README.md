![](images/sql.png)

Here’s your content neatly formatted in **Markdown (MD)** with proper sectioning and fenced SQL code blocks:


# DDL & DML Sample

```sql
CREATE DATABASE learning;
USE learning;

CREATE TABLE departments (
    department_id integer(4),
    department_name varchar(30) NOT NULL,
    manager_id integer(6),
    location_id integer(4)
);

CREATE TABLE employees (
    employee_id integer(6),
    first_name varchar(20),
    last_name varchar(25) NOT NULL,
    email varchar(25) NOT NULL,
    phone_integer varchar(20),
    hire_date DATE NOT NULL,
    job_id varchar(10) NOT NULL,
    salary integer(8),
    commission_pct integer(2),
    manager_id integer(6),
    department_id integer(4)
);

-- Insert into departments
INSERT INTO departments VALUES (10, 'Administration', 200, 1700);
INSERT INTO departments VALUES (20, 'Marketing', 201, 1800);
INSERT INTO departments VALUES (30, 'Purchasing', 114, 1700);
INSERT INTO departments VALUES (40, 'Human Resources', 203, 2400);
INSERT INTO departments VALUES (50, 'Shipping', 121, 1500);
INSERT INTO departments VALUES (60, 'IT', 103, 1400);
INSERT INTO departments VALUES (70, 'Public Relations', 204, 2700);
INSERT INTO departments VALUES (80, 'Sales', 145, 2500);
INSERT INTO departments VALUES (90, 'Executive', 100, 1700);
INSERT INTO departments VALUES (100, 'Finance', 108, 1700);
INSERT INTO departments VALUES (110, 'Accounting', 205, 1700);
INSERT INTO departments VALUES (120, 'Treasury', NULL, 1700);
INSERT INTO departments VALUES (130, 'Corporate Tax', NULL, 1700);
INSERT INTO departments VALUES (140, 'Control And Credit', NULL, 1700);
INSERT INTO departments VALUES (150, 'Shareholder Services', NULL, 1700);
INSERT INTO departments VALUES (160, 'Benefits', NULL, 1700);
INSERT INTO departments VALUES (170, 'Manufacturing', NULL, 1700);
INSERT INTO departments VALUES (180, 'Construction', NULL, 1700);
INSERT INTO departments VALUES (190, 'Contracting', NULL, 1700);
INSERT INTO departments VALUES (200, 'Operations', NULL, 1700);
INSERT INTO departments VALUES (210, 'IT Support', NULL, 1700);
INSERT INTO departments VALUES (220, 'NOC', NULL, 1700);
INSERT INTO departments VALUES (230, 'IT Helpdesk', NULL, 1700);
INSERT INTO departments VALUES (240, 'Government Sales', NULL, 1700);
INSERT INTO departments VALUES (250, 'Retail Sales', NULL, 1700);
INSERT INTO departments VALUES (260, 'Recruiting', NULL, 1700);
INSERT INTO departments VALUES (270, 'Payroll', NULL, 1700);

-- Insert into employees (sample)
INSERT INTO employees VALUES (100, 'Steven', 'King', 'SKING', '515.123.4567', '1987-05-01', 'AD_PRES', 24000, NULL, NULL, 90);
INSERT INTO employees VALUES (101, 'Neena', 'Kochhar', 'NKOCHHAR', '515.123.4568', '1989-06-05', 'AD_VP', 17000, NULL, 100, 90);
INSERT INTO employees VALUES (102, 'Lex', 'De Haan', 'LDEHAAN', '515.123.4569', '1989-06-05', 'AD_VP', 17000, NULL, 100, 90);
...
````

---

# DQL Queries

### 1. Self Join

```sql
SELECT e1.last_name || ' works for ' || e2.last_name "employees and Their Managers",
       e1.*, e2.last_name
FROM employees e1
JOIN employees e2
    ON e1.manager_id = e2.employee_id
   AND e1.last_name LIKE 'R%'
ORDER BY e1.last_name;
```

### 2. Left Outer Join

```sql
SELECT d.department_id, e.last_name
FROM departments d
LEFT OUTER JOIN employees e
    ON d.department_id = e.department_id
ORDER BY d.department_id, e.last_name;
```

### 3. Right Outer Join

```sql
SELECT d.department_id, e.last_name
FROM departments d
RIGHT OUTER JOIN employees e
    ON d.department_id = e.department_id
ORDER BY d.department_id, e.last_name;
```

```sql
DELETE FROM departments
WHERE department_id = 100;
```

### 4. Full Outer Join

```sql
SELECT d.department_id, e.last_name
FROM departments d
LEFT OUTER JOIN employees e
    ON d.department_id = e.department_id
UNION ALL
SELECT d.department_id, e.last_name
FROM departments d
RIGHT OUTER JOIN employees e
    ON d.department_id = e.department_id;
```

### 5. Sub Query Example

```sql
SELECT *
FROM employees
WHERE department_id NOT IN (
    SELECT department_id
    FROM departments
    WHERE location_id = 1700
)
ORDER BY last_name;
```

### 6. Top 10 Salary Employees

```sql
SELECT *
FROM (
    SELECT RANK() OVER (ORDER BY salary) AS rn
    FROM employees
) AS t1
WHERE rn < 11;
```

### 7. Ranking Functions

```sql
SELECT employee_id, first_name, job_id, hire_date, salary,
       RANK() OVER (ORDER BY hire_date) AS hire_seq_rank,
       ROW_NUMBER() OVER (ORDER BY hire_date) AS hire_seq_RN,
       DENSE_RANK() OVER (ORDER BY hire_date) AS hire_seq_dense_rank
FROM employees;
```

### 8. View Example

```sql
CREATE OR REPLACE VIEW emp_details_view AS
SELECT e.employee_id,
       e.job_id,
       e.manager_id,
       e.department_id,
       d.department_name
FROM employees e
INNER JOIN departments d
    ON e.department_id = d.department_id;
```

### 9. Sub Queries (Single Row)

```sql
SELECT *
FROM hr.departments
WHERE department_name = (
    SELECT department_name
    FROM hr.departments
    WHERE department_name = 'IT'
);
```

### 10. Sub Queries (Multiple Rows)

```sql
SELECT *
FROM hr.departments
WHERE department_name IN (
    SELECT department_name
    FROM hr.departments
    WHERE department_name = 'IT'
       OR department_name = 'Administration'
);
```

### 11. Sub Queries (Multiple Columns)

```sql
SELECT *
FROM hr.departments
WHERE (department_id, department_name) IN (
    SELECT department_id, department_name
    FROM hr.departments
    WHERE department_name = 'IT'
       OR department_name = 'Administration'
);
```

### 12. Inline View

```sql
SELECT e.employee_id, a.department_id, e.last_name, e.salary, a.min_sal
FROM hr.employees e,
     (SELECT MIN(salary) min_sal, department_id
      FROM hr.employees
      GROUP BY department_id) a
WHERE e.department_id = a.department_id
ORDER BY e.department_id, e.salary DESC;
```

### 13. Top-N Analysis

```sql
SELECT *
FROM (
    SELECT e.employee_id, e.last_name, e.salary
    FROM hr.employees e
    ORDER BY e.salary DESC
)
WHERE ROWNUM < 6;
```

### 14. Analytical Queries

```sql
SELECT NAME, company, power,
       RANK() OVER(ORDER BY power DESC) AS RANK,
       ROW_NUMBER() OVER(ORDER BY power DESC) AS Row_Number
FROM cars1;
```

```sql
WITH cte AS (
    SELECT NAME, company, power,
           ROW_NUMBER() OVER (PARTITION BY NAME, company ORDER BY power DESC) AS Row_Number
    FROM cars1
)
SELECT *
FROM cte
WHERE NAME = 'Prius' AND Row_Number = 1;
```

```sql
WITH cte AS (
    SELECT NAME, company, power,
           RANK() OVER(ORDER BY power DESC) AS RANK,
           ROW_NUMBER() OVER(ORDER BY power DESC) AS Row_Number
    FROM cars1
)
SELECT *
FROM cte;
```

```sql
SELECT *
FROM (
    SELECT NAME, company, power,
           DENSE_RANK() OVER (PARTITION BY company ORDER BY power) AS dn
    FROM cars1
    ORDER BY company
)
WHERE company = 'Toyota';
```




