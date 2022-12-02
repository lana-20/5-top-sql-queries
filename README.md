# 5-top-sql-queries

/*1. select the highest salary in the company*/

SELECT MAX(salary) FROM employees

/*2. return employee's record with max salary*/

SELECT first_name, last_name, salary, department_id FROM employees
WHERE salary = (SELECT MAX(salary) FROM employees)

/*3. select range of employees based on the employee_id (100-150)*/

SELECT employee_id, first_name, last_name, salary, department_id FROM employees
WHERE employee_id BETWEEN 100 AND 150

/*4. return employee's name highest salary and name of department*/

SELECT e.employee_id, e.first_name, e.last_name, e.salary, d.department_name
FROM employees e, departments d
WHERE e.department_id = d.department_id AND e.salary = (SELECT MAX(salary) FROM employees)

SELECT e.employee_id, e.first_name, e.last_name, e.salary, d.department_name
FROM employees e INNER JOIN departments d
ON e.department_id = d.department_id WHERE e.salary = (SELECT MAX(salary) FROM employees)

/*5. select second highest salary in the company*/

SELECT MAX(salary) FROM employees WHERE salary NOT IN (SELECT MAX(salary) FROM employees)

SELECT MAX(salary) FROM employees WHERE NOT salary = (SELECT MAX(salary) FROM employees)

SELECT MAX(salary) FROM employees WHERE salary < (SELECT MAX(salary) FROM employees)

SELECT MAX(salary) FROM employees WHERE salary != (SELECT MAX(salary) FROM employees)

SELECT MAX(salary) FROM employees WHERE salary <> (SELECT MAX(salary) FROM employees)

<img src="https://github.com/lana-20/sql-little-bobby-tables/blob/main/little_bobby_tables.jpeg"/>
