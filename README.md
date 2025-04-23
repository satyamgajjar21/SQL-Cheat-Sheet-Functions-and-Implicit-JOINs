# 📘 SQL Cheat Sheet: Functions and Implicit JOINs

A quick reference guide covering essential SQL functions, subqueries, and implicit joins — helpful for beginners, interview prep, or day-to-day database querying. 🧠💡

---

## 📌 Table of Contents
- [🔢 Aggregate Functions](#-aggregate-functions)
- [🔣 String Functions](#-string-functions)
- [📅 Date Functions](#-date-functions)
- [🔍 Subqueries](#-subqueries)
- [🔗 Joins](#-joins)
- [👥 Authors](#-authors)

---

## 🔢 Aggregate Functions

| Function | Syntax | Description | Example |
|---------|--------|-------------|---------|
| **COUNT** | `SELECT COUNT(column_name) FROM table_name WHERE condition;` | Returns number of rows that match the condition | `SELECT COUNT(dep_id) FROM employees;` |
| **AVG** | `SELECT AVG(column_name) FROM table_name WHERE condition;` | Returns the average of a numeric column | `SELECT AVG(salary) FROM employees;` |
| **SUM** | `SELECT SUM(column_name) FROM table_name WHERE condition;` | Returns the total sum of a column | `SELECT SUM(salary) FROM employees;` |
| **MIN** | `SELECT MIN(column_name) FROM table_name WHERE condition;` | Returns the smallest value in a column | `SELECT MIN(salary) FROM employees;` |
| **MAX** | `SELECT MAX(column_name) FROM table_name WHERE condition;` | Returns the largest value in a column | `SELECT MAX(salary) FROM employees;` |
| **ROUND** | `SELECT ROUND(number, decimals);` | Rounds a number to a given decimal place | `SELECT ROUND(salary, 2) FROM employees;` |

---

## 🔣 String Functions

| Function | Syntax | Description | Example |
|---------|--------|-------------|---------|
| **LENGTH** | `SELECT LENGTH(column_name) FROM table;` | Returns length of a string (in bytes) | `SELECT LENGTH(f_name) FROM employees;` |
| **UCASE** | `SELECT UCASE(column_name) FROM table;` | Converts text to uppercase | `SELECT UCASE(f_name) FROM employees;` |
| **LCASE** | `SELECT LCASE(column_name) FROM table;` | Converts text to lowercase | `SELECT LCASE(f_name) FROM employees;` |
| **DISTINCT** | `SELECT DISTINCT column_name FROM table;` | Eliminates duplicates | `SELECT DISTINCT UCASE(f_name) FROM employees;` |

---

## 📅 Date Functions

| Function | Syntax | Description | Example |
|---------|--------|-------------|---------|
| **DAY** | `SELECT DAY(column_name) FROM table;` | Returns day of the month | `SELECT DAY(b_date) FROM employees WHERE emp_id = 'E1002';` |
| **CURRENT_DATE** | `SELECT CURRENT_DATE;` | Returns the current date | `SELECT CURRENT_DATE;` |
| **DATEDIFF** | `SELECT DATEDIFF(date1, date2);` | Calculates the difference (in days) between two dates | `SELECT DATEDIFF(CURRENT_DATE, date_column) FROM table;` |
| **FROM_DAYS** | `SELECT FROM_DAYS(number_of_days);` | Converts number of days to a date | `SELECT FROM_DAYS(DATEDIFF(CURRENT_DATE, date_column)) FROM table;` |
| **DATE_ADD** | `SELECT DATE_ADD(date, INTERVAL n TYPE);` | Adds a date interval (e.g., DAY, MONTH) | `SELECT DATE_ADD(date, INTERVAL 3 DAY);` |
| **DATE_SUB** | `SELECT DATE_SUB(date, INTERVAL n TYPE);` | Subtracts a date interval | `SELECT DATE_SUB(date, INTERVAL 3 DAY);` |

---

## 🔍 Subqueries

Subqueries are queries nested inside another query, typically in the `WHERE` clause.

```sql
SELECT emp_id, f_name, l_name, salary
FROM employees
WHERE salary < (SELECT AVG(salary) FROM employees);
