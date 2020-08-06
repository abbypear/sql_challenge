# sql_challenge
---list the following details of each employee: employee number, last name, first name, sex, and salary.
SELECT employees.first_name, employees.last_name, employees.sex, salaries.emp_no
FROM salaries
JOIN employees
	ON salaries.emp_no = employees.emp_no

---list first name, last name, and hire date for employees who were hired in 1986.
SELECT first_name, last_name, hire_date
FROM employees
WHERE hire_date BETWEEN '1986-01-01' AND '1986-12-31'

---list the manager of each department with the following information: department number, department name, the manager's employee number, last name, first name.
SELECT dept_manager.emp_no, employees.first_name, employees.last_name, departments.dept_name, departments.dept_no
FROM departments
JOIN dept_manager
ON departments.dept_no = dept_manager.dept_no
JOIN employees
ON dept_manager.emp_no = employees.emp_no

---list the department of each employee with the following information: employee number, last name, first name, and department name.
SELECT employees.emp_no, employees.first_name, employees.last_name
FROM employees
JOIN dept_emp
ON employees.emp_no = dept_emp.emp_no
JOIN departments
ON dept_emp.dept_no = departments.dept_no

---list first name, last name, and sex for employees whose first name is "Hercules" and last names begin with "B."
SELECT first_name, last_name, sex
FROM employees
WHERE first_name = 'Hercules' AND last_name LIKE '%B'

---list all employees in the Sales department, including their employee number, last name, first name, and department name.
SELECT employees.first_name, employees.last_name, employees.emp_no, departments.dept_name
FROM employees
JOIN dept_emp
ON dept_emp.emp_no = employees.emp_no
JOIN departments
ON departments.dept_no = dept_emp.dept_no
WHERE dept_name = 'Sales'

---list all employees in the Sales and Development departments, including their employee number, last name, first name, and department name.
SELECT employees.first_name, employees.last_name, employees.emp_no, departments.dept_name
FROM employees
JOIN dept_emp
ON dept_emp.emp_no = employees.emp_no
JOIN departments
ON departments.dept_no = dept_emp.dept_no
WHERE dept_name = 'Sales' OR dept_name = 'Development'

---in descending order, list the frequency count of employee last names, i.e., how many employees share each last name.
SELECT employees.last_name, COUNT(last_name) AS "last_name frequency count"
FROM employees
GROUP BY last_name
order by "last_name frequency count" DESC
