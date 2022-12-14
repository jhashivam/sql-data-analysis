1. Select the information from the "dept_no" column of the "departments" table. Select all data from the "departments" table.

```sql
SELECT 
    dept_no
FROM
    departments;

SELECT 
    *
FROM
    departments;

```

2. Select all people from the "employees" table whose first name is "Elvis".
```sql
SELECT 
    *
FROM
    employees
WHERE
    first_name = 'Elvis';

```
3. Retrieve a list with all female employees whose first name is Kellie.
```sql
SELECT 
    *
FROM
    employees
WHERE
    first_name = 'Kellie'
        AND gender = 'F';

```
4. Retrieve a list with all employees whose first name is either Kellie or Aruna.
```sql
SELECT 
    *
FROM
    employees
WHERE
    first_name = 'Kellie'
        OR first_name = 'Aruna';

```
5. Retrieve a list with all female employees whose first name is either Kellie or Aruna.
```sql
SELECT 
    *
FROM
    employees
WHERE
    (first_name = 'Kellie'
        OR first_name = 'Aruna') AND gender = 'F';
```
6. Use the IN operator to select all individuals from the “employees” table, whose first name is either “Denis”, or “Elvis”.
```sql
SELECT 
    *
FROM
    employees
WHERE
    first_name IN ("Denis","Elvis");
```
7. Extract all records from the ‘employees’ table, aside from those with employees named John, Mark, or Jacob.
```sql
SELECT 
    *
FROM
    employees
WHERE
    first_name NOT IN ('John' , 'Mark', 'Jacob');
    
```
8. Select the data about all individuals, whose first name starts with "Mark", specify that the name can be succeeded by any sequence of characters.
```sql
SELECT 
    *
FROM
    employees
WHERE
    first_name LIKE ('MarK%');
```
9. Retrieve a list with all employees who have been hired in the year 2000.
```sql
SELECT 
    *
FROM
    employees
WHERE
    hire_date LIKE ('2000%');
```
10. Retrieve a list with all employees whose employee number is written with 5 characters, and starts with "1000".
```sql
SELECT 
    *
FROM
    employees
WHERE
    emp_no LIKE ('1000_');
```
11. Extract all individuals from the "employees" table whose first name contains "Jack".
```sql
SELECT 
    *
FROM
    employees
WHERE
    first_name LIKE ('jack%');
```
12. Extract list containing the names of employees that do not contain "Jack".
```sql
SELECT 
    *
FROM
    employees
WHERE
    first_name NOT LIKE ('jack%');
```
13. Select all the information from the "salaries" table regarding contracts from 66,000 to 70,000 dollars per year.
```sql
SELECT 
    *
FROM
    salaries
WHERE
    salary BETWEEN 66000 AND 70000;
```
14. Retrieve a list with all individuals whose employee number is not between "10004" and "10012".
```sql
SELECT 
    *
FROM
    employees
WHERE
    emp_no NOT BETWEEN 10004 AND 10012;
```
15. Select the names of all departments with numbers between "d003" and "d006".
```sql
SELECT 
    *
FROM
    departments
WHERE
    dept_no BETWEEN 'd003' AND 'd006';
```
16. Select the names of all departments whose department number value is not null.
```sql
SELECT 
    *
FROM
    departments
WHERE
    dept_no IS NOT NULL;
```
17. Retrieve a list with data about all female employees who were hired in the year 2000 or after.
```sql
SELECT 
    *
FROM
    employees
WHERE
    gender = 'F'
        AND hire_date > '2000-01-01';
```
18. Extract a list with all employees' salaries higher than $150,000 per annum.
```sql
SELECT 
    *
FROM
    salaries
WHERE
    salary > 150000;
```
19. Obtain a list with all different "hire dates" from the "employees" table.
```sql
SELECT DISTINCT
    (hire_date)
FROM
    employees;
```
20. How many annual contracts with a value higher than or equal to $100,000 have been registered in the salaries table?
```sql
SELECT 
    COUNT(*)
FROM
    salaries
WHERE
    salary >= 100000;
```
21. How many managers do we have in the “employees” database?
```sql
SELECT 
    COUNT(*)
FROM
    dept_manager; 
```
22. Select all data from the "employees" table, ordering it by "hire date" in descending order.
```sql
SELECT 
    *
FROM
    employees
ORDER BY hire_date DESC;
```
23. Write a query that obtains two columns. The first column must contain annual salaries higher than `80,000` dollars.The second column, renamed to `emps_with_same_salary`, must show the number of employees contracted to that salary. Lastly, sort the output by the first column.
```sql
SELECT 
    salary, COUNT(salary) AS emps_with_same_salary
FROM
    salaries
WHERE
    salary > 80000
GROUP BY salary
ORDER BY salary;
``` 
24. Select all employees whose average salary is higher than $120,000 per annum.
```sql
SELECT 
    emp_no, AVG(salary) AS salary_count
FROM
    salaries
GROUP BY emp_no
HAVING AVG(salary) > 120000
ORDER BY emp_no;
```
25. Select the first 100 rows from the 'dept_emp' table.
```sql
select * from dempt_emp limit 100;
```
26. Task 1:
    a. Select ten records from the “titles” table to get a better idea about its content.
    b. Then, in the same table, insert information about employee number 999903. State that he/she is a “Senior Engineer”, who has started working in this position on October 1st, 1997.
    c. At the end, sort the records from the “titles” table in descending order to check if you have successfully inserted the new record.
```sql
SELECT 
    *
FROM
    titles
LIMIT 10;

INSERT INTO employees 
(
    emp_no,
    birth_date, 
    first_name, 
    last_name, 
    gender, 
    hire_date
)
VALUES
(
    999903,
    "1977-09-14",
    "Johnathan",
    "Creek",
    "M",
    "1999-01-01"
 ); 

INSERT INTO titles
(
    emp_no,
    title,
    from_date,
    to_date
)
VALUES
(
    999903,
    'Senior Engineer',
    '1999-01-01',
    '2000-12-01'
);

```
27. Task 2:
    a. Insert information about the individual with employee number 999903 into the “dept_emp” table. 
    b. He/She is working for department number 5, and has started work on October 1st, 1997; her/his contract is for an indefinite period of time.
```sql
INSERT INTO dept_emp
values 
(
	999903, 
	"d005", 
	"1991-10-01", 
	"9999-01-01"
);  
```
28. Create a new department called "Business Analysis". Register it under number "d010".
```sql
INSERT INTO departments
(
    dept_no,
    dept_name
)
VALUES
(
    'd010',
    'Business Analysis'
);
```
29. Change the "Business Analysis" department name to "Data Analysis".
```sql
UPDATE departments 
SET 
    dept_name = 'Data Analysis'
WHERE
    dept_no = 'd010';
```
30. Remove the department number 10 record from the "departments" table.
```sql
DELETE FROM departments 
WHERE
    dept_no = 'd010';
```
31. How many departments are there in the "employees" database? Use the "dept_emp" table
```sql
SELECT 
  COUNT(DISTINCT dept_no)
FROM
    dept_emp;
```
32. What is the total amount of money spent on salaries for all contracts starting after the 1st of January 1997?
```sql
SELECT 
    SUM(salary)
FROM
    salaries
WHERE
    from_date > '1997-01-01';
```
33. Which is the lowest employee number in the database?
```sql
SELECT 
    MIN(emp_no)
FROM
    employees;
```
34. Which is the highest employee number in the database?
```sql
SELECT 
    MAX(emp_no)
FROM
    employees;
```
35. What is the average annual salary paid to employees who started after the 1st of January 1997?
```sql
SELECT 
    AVG(salary)
FROM
    salaries
WHERE
    from_date > '1997-01-01';
```
36. Round the average amount of money spent on salaries for all contracts that started after the 1st of January 1997 to a precision of cents.
```sql
SELECT 
    ROUND(AVG(salary), 2)
FROM
    salaries
WHERE
    from_date > '1997-01-01';
```
37. Select the department number and name from the ‘departments_dup’ table and add a third column where you name the department number (‘dept_no’) as ‘dept_info’. If ‘dept_no’ does not have a value, use ‘dept_name’.
```sql

```
38. Modify the code obtained from the previous question in the following way. Apply the IFNULL() function to the values from the first and second column, so that ‘N/A’ is displayed whenever a department number has no value, and ‘Department name not provided’ is shown if there is no value for ‘dept_name’.
```sql

```
39. Extract a list containing information about all managers' employee number, first and last name, department number, and hire date.
```sql

```
40. Join the 'employees' and the 'dept_manager' tables to return a subset of all the employees whose last name is Markovitch.
```sql

```
41. Select the first and last name, the hire date, and the job title of all employees whose first name is "Margareta" and have the last name "Markovitch".
42. Use a CROSS JOIN to return a list with all possible combinations between managers from the dept_manager table and department number 9.
43. How many male and how many female managers do we have in the "employees" database?
44. Extract the information about all department managers who were hired between the 1st of January 1990 and the 1st of January 1995.
45. Select the entire information for all employees whose job title is "Assistant Engineer".
46. Create a view that will extract the average salary of all managers registered in the database. Round this value to the nearest cent.
47. Create a procedure called "emp_info" that uses as parameters the first and the last name of an individual, and returns their employee number.
48. Create a function called "emp_info" that takes for parameters the first and last name of an employee, and returns the salary from the newest contract of that employee.
49. Obtain a result set containing the employee number, first name, and last name of all employees with a number higher than 109990. Create a fourth column in the query, indicating whether this employee is also a manager, according to the data provided in the dept_manager table, or a regular employee.
50. Extract a dataset containing the following information about the managers: employee number, first name, and last name. Add two columns at the end – one showing the difference between the maximum and minimum salary of that employee, and another one saying whether this salary raise was higher than $30,000 or NOT.

```sql

  38. select 
        dept_no, dept_name, coalesce(dept_no, dept_name) as dept_info 
        from departments_dup 
        order by dept_no asc;
  39. select 
        IFNULL(dept_no, 'NA') as dept_no, 
        IFNULL(dept_name, "Department name not provided") as dept_name, 
        COALESCE(dept_no, dept_name) as dept_info 
      from departments_dup;
  40. select 
        e.first_name, e.last_name, e.hire_date, e.emp_no, d.dept_no 
        from employees as e 
        inner join 
        dept_manager as d 
        on e.emp_no = d.emp_no;
  41. select *
        from employees as e 
        left join 
        dept_manager as d 
        on e.emp_no = d. emp_no 
        where 
        e.last_name = "Markovitch" 
        order by d.dept_no DESC, e.emp_no;
  42. select 
        e.first_name, e.last_name, e.hire_date, t.title 
        from employees as e 
        left join 
        titles as t 
        on e.emp_no = t.emp_no 
        where e.first_name = "Margareta" and  e.last_name = "Markovitch";
  43. select 
        e.gender, count(d.emp_no) 
        from employees as e 
        inner join 
        dept_manager as d 
        on e.emp_no = d.emp_no 
        group by e.gender;
  44. select * 
        from employees 
        where (hire_date between "1990-01-01" and "1995-01-01") and emp_no in(select emp_no from dept_manager); 
  45. select * 
        from employees e 
        where 
        exists 
            ( 
                select * 
                from titles t 
                where t.emp_no = e.emp_no 
                and 
                title="Assistant Engineer"
             );
  46. create 
	    or 
    	replace 
	    view v_avg_manager_salary 
	    as
	    select 
		    round(avg(salary),2)
            from salaries s
            join dept_manager m 
            on s.emp_no = m.emp_no;
  47. Delimiter $$
	create 
	procedure emp_info(in p_first_name varchar(255), in p_last_name varchar(255), out p_emp_no integer)
	begin
	select e.emp_no into p_emp_no 
	from employees e
	where e.first_name = p_first_name
	and 
	e.last_name = p_last_name;
	end $$
	Delimiter ;  
  48. delimiter $$
   	create Function emp_info(p_first_name varchar(255), p_last_name varchar(255)) returns Decimal(10,2)
   	DETERMINISTIC NO SQL READS SQL DATA
   	begin
   	declare v_emp_salary Decimal(10,2);
		select s.salary INTO v_emp_salary from salaries as s 
		left join employees e on s.emp_no = e.emp_no 
    		where (e.first_name = p_first_name and e.last_name = p_last_name) 
		order by from_date DESC limit 1;
   	return v_emp_salary;
   	end $$  
   
	select emp_info('Aruna', 'Journel');
  49. select
	e.emp_no, e.first_name, e.last_name,
	case when dm.emp_no is not null then 'Manager'
	else 'Employee'
	end as is_manager
	from
	employees e
	left join
	dept_manager dm on dm.emp_no = e.emp_no
	where e.emp_no > 109990;
  50. select d.emp_no, e.first_name, e.last_name, max(s.salary) - min(s.salary) as salary_difference, 
	if (max(s.salary) - min(s.salary) > 30000, 
		'Salary was raised by more than $30,000', 
		'Salary was not raised by more than $30,000') 
	as salary_increase
	from dept_manager d 
	join 
	employees e on e.emp_no = d.emp_no 
	join 
	salaries s on s.emp_no = d.emp_no 
	group by s.emp_no;
```
