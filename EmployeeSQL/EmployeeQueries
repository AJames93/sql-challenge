--Delete the following tables
DROP TABLE departments;
DROP TABLE dept_emp;
DROP TABLE dept_manager;
DROP TABLE employees;
DROP TABLE salaries;
DROP TABLE titles;

--Creating departments table
CREATE TABLE departments (
	dept_no VARCHAR(30) NOT NULL,
	dept_name VARCHAR (30) NOT NULL
);

--Creating dept_emp table
CREATE TABLE dept_emp (
	emp_no INT NOT NULL,
	dept_no VARCHAR (30) NOT NULL
);

--Creating dept_manager table
CREATE TABLE dept_manager (
	dept_no VARCHAR (30) NOT NULL,
	emp_no INT NOT NULL
);

--Creating employees table
CREATE TABLE employees (
	emp_no INT NOT NULL,
	emp_title VARCHAR (30) NOT NULL,
	birth_date VARCHAR (30) NOT NULL,
	first_name VARCHAR (30) NOT NULL,
	last_name VARCHAR (30) NOT NULL,
	sex VARCHAR (1) NOT NULL,
	hire_date  VARCHAR (30) NOT NULL
);

--Creating salaries table
CREATE TABLE salaries (
	emp_no INT NOT NULL,
	salary INT NOT NULL
);

--Creating titles table
CREATE TABLE titles (
	title_id VARCHAR (30) NOT NULL,
	title VARCHAR (30) NOT NULL
);

--Pulling data from tables
SELECT * FROM departments
SELECT * FROM dept_emp
SELECT * FROM dept_manager
SELECT * FROM employees
SELECT * FROM salaries
SELECT * FROM titles

--Question 1. List the following details of each employee: employee number, last name, first name, sex, and salary.
SELECT employees.emp_no AS "Employee Number", employees.last_name AS "Last Name", employees.first_name
	AS "First Name", employees.sex AS "Gender", salaries.salary AS "Salary"
FROM salaries
INNER JOIN employees ON
salaries.emp_no=employees.emp_no;

--Question 2. List first name, last name, and hire date for employees who were hired in 1986.
SELECT first_name AS "First Name", last_name AS "Last Name", hire_date AS "Hire Date"
FROM employees
WHERE hire_date BETWEEN '1/1/1986' AND '12/31/1986'
ORDER BY hire_date;

--Question 3. List the manager of each department with the following information: 
--department number, department name, the manager's employee number, last name, first name.

SELECT departments.dept_no AS "Department Number", departments.dept_name AS "Department Name", 
	dept_manager.emp_no AS "Manager Employee Number", employees.last_name AS "Last Name", 
	employees.first_name AS "First Name"
FROM departments
JOIN dept_manager
ON departments.dept_no = dept_manager.dept_no
JOIN employees
ON dept_manager.emp_no = employees.emp_no;

--Question 4. List the department of each employee with the following information: 
--employee number, last name, first name, and department name.

SELECT dept_emp.emp_no AS "Employee Number", employees.last_name AS "Last Name", 
	employees.first_name AS "First Name", departments.dept_name AS "Department Name"
FROM dept_emp
JOIN employees
ON dept_emp.emp_no=employees.emp_no
JOIN departments
ON dept_emp.dept_no=departments.dept_no;

--Question 5. List first name, last name, and sex for employees whose first name is "Hercules" and 
--last names begin with "B."

SELECT first_name AS "First Name", last_name AS "Last Name", sex AS "Gender"
FROM employees
WHERE first_name='Hercules' 
AND last_name LIKE 'B%';

--Question 6. List all employees in the Sales department, 
--including their employee number, last name, first name, and department name.

SELECT dept_emp.emp_no AS "Employee Number", employees.last_name AS "Last Name", 
	employees.first_name AS "First Name", departments.dept_name AS "Department Name"
FROM dept_emp
JOIN employees
ON dept_emp.emp_no=employees.emp_no
JOIN departments
ON dept_emp.dept_no=departments.dept_no
WHERE dept_name='Sales';

--Question 7. List all employees in the Sales and Development departments, 
--including their employee number, last name, first name, and department name.

SELECT dept_emp.emp_no AS "Employee Number", employees.last_name AS "Last Name", 
	employees.first_name AS "First Name", departments.dept_name AS "Department Name"
FROM dept_emp
JOIN employees
ON dept_emp.emp_no=employees.emp_no
JOIN departments
ON dept_emp.dept_no=departments.dept_no
WHERE dept_name='Sales' OR dept_name='Development';

--Question 8. In descending order, list the frequency count of employee last names, 
--i.e., how many employees share each last name.

SELECT last_name AS "Last Name", COUNT (last_name) AS "Frequency"
FROM employees
GROUP BY last_name
ORDER BY "Frequency" DESC;
