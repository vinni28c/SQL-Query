# SQL Queries Reference Guide

This repository contains a collection of essential SQL queries categorized by language components such as **DDL**, **DML**, **DQL**, **DCL**, and **TCL**, along with examples of **joins** and **advanced SQL** statements.

---

## 🧱 Data Definition Language (DDL)
Used to define and modify database structures.

```sql
CREATE TABLE employees (
  id INT PRIMARY KEY,
  name VARCHAR(100),
  salary DECIMAL(10,2)
);

ALTER TABLE employees ADD COLUMN department_id INT;

DROP TABLE employees;

TRUNCATE TABLE employees;
```

---

## ✏️ Data Manipulation Language (DML)
Used to insert, update, and delete data.

```sql
INSERT INTO employees (id, name, salary) VALUES (1, 'John Doe', 55000.00);

UPDATE employees SET salary = 60000.00 WHERE id = 1;

DELETE FROM employees WHERE id = 1;
```

---

## 🔍 Data Query Language (DQL)
Used to query data from the database.

```sql
SELECT name, salary FROM employees WHERE department_id = 10;

SELECT DISTINCT department_id FROM employees;

SELECT department_id, AVG(salary)
FROM employees
GROUP BY department_id
HAVING AVG(salary) > 50000;
```

---

## 🔒 Data Control Language (DCL)
Used to control access to data.

```sql
GRANT SELECT, INSERT ON employees TO user1;

REVOKE INSERT ON employees FROM user1;
```

---

## 🔁 Transaction Control Language (TCL)
Used to manage database transactions.

```sql
COMMIT;

ROLLBACK;

SAVEPOINT before_update;
```

---

## 🤝 Joins
Used to combine data from multiple tables.

```sql
-- Inner Join
SELECT e.name, d.name
FROM employees e
INNER JOIN departments d ON e.department_id = d.id;

-- Left Join
SELECT e.name, d.name
FROM employees e
LEFT JOIN departments d ON e.department_id = d.id;
```

---

## 🚀 Advanced SQL Statements

```sql
-- Subquery
SELECT name, salary
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);

-- Conditional Logic
SELECT name,
  CASE
    WHEN salary > 60000 THEN 'High'
    ELSE 'Low'
  END AS salary_level
FROM employees;

-- Counting and Filtering
SELECT COUNT(*) FROM employees WHERE department_id = 10;

-- Common Table Expression (CTE)
WITH HighEarners AS (
  SELECT name, salary FROM employees WHERE salary > 70000
)
SELECT * FROM HighEarners;

-- Ranking Function
SELECT name, salary,
  RANK() OVER (ORDER BY salary DESC) AS salary_rank
FROM employees;
```

---

## 📘 Summary
These SQL statements provide practical examples to help you learn and understand different aspects of SQL — from defining tables to querying and managing data effectively.

---

### 🧩 Author
Created as a beginner-friendly reference to learn and experiment with SQL commands.

---

### 📄 License
This project is open-source and available under the [MIT License](LICENSE).
