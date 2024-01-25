## sql-challenge
Research for Pewlett Hackard (fictional company) for employees employed during the 1980s and 1990s.

# Data 
departments.csv, dept_emp.csv, dept_manager.csv, employees.csv, salaries.csv, titles.csv

# Table Schemata (See ERD diagram in repo)
-- Create employees, salaries, titles, departments, dept_emp, dept_manager tables
DROP TABLE IF EXISTS employees;
DROP TABLE IF EXISTS salaries;
DROP TABLE IF EXISTS titles;
DROP TABLE IF EXISTS departments;
DROP TABLE IF EXISTS dept_emp;
DROP TABLE IF EXISTS dept_manager;

CREATE TABLE employees (
	emp_no INT PRIMARY KEY,
	emp_title_id VARCHAR,
	birth_date DATE,
	first_name VARCHAR,
	last_name VARCHAR,
	sex VARCHAR,
	hire_date DATE
);

CREATE TABLE salaries(
	emp_no INT,
	salary INT,
	PRIMARY KEY (emp_no),
	FOREIGN KEY (emp_no) REFERENCES employees (emp_no)
);

CREATE TABLE titles(
	title_id VARCHAR PRIMARY KEY,
	title VARCHAR
);

CREATE TABLE departments(
	dept_no INT PRIMARY KEY,
	dept_name VARCHAR
);

CREATE TABLE dept_emp(
	emp_no INT,
	dept_no INT,
	PRIMARY KEY (emp_no, dept_no),
	FOREIGN KEY (emp_no) REFERENCES employees (emp_no),
	FOREIGN KEY (dept_no) REFERENCES departments (dept_no)
);

CREATE TABLE dept_manager(
	dept_no INT,
	emp_no INT,
	PRIMARY KEY (dept_no, emp_no),
	FOREIGN KEY (dept_no) REFERENCES departments (dept_no),
	FOREIGN KEY (emp_no) REFERENCES employees (emp_no)
);
