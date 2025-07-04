# mysql-questions


Problem Statement
You are given two tables: Sales and Employees.

The Sales table records the details of each sale made by employees, including the following columns:

sale_id

employee_id

sale_amount

The Employees table holds information about the employees, including the following columns:

employee_id

first_name

last_name

Task
Write a query to find the following:

The average sales amount for each employee, along with the number of sales they made.



Expected Output Columns
The query must return the following columns:

employee_id

first_name

last_name

average_sale

total_sales_count

Sorting Requirements
The result should be ordered in descending order of average_sale.

If two or more employees have the same average sale, then sort them in ascending order of employee_id.

Input Format
Employees Table
Column Name	Data Type
employee_id	INTEGER
first_name	VARCHAR(255)
last_name	VARCHAR(255)

Sales Table
Column Name	Data Type
sale_id	INTEGER
employee_id	INTEGER
sale_amount	DECIMAL(10,2)

Output Format
Column Name	Data Type
employee_id	INTEGER
first_name	VARCHAR(255)
last_name	VARCHAR(255)
average_sale	DECIMAL(10,6)
total_sales_count








//  code  ---------------------------------------------------------------------------------------------------------------------------------------------->






SELECT 
    e.employee_id,
    e.first_name,
    e.last_name,
    ROUND(AVG(s.sale_amount), 6) AS average_sale,
    COUNT(s.sale_id) AS total_sales_count
FROM Employees e
JOIN Sales s ON e.employee_id = s.employee_id
GROUP BY e.employee_id, e.first_name, e.last_name
HAVING average_sale >= (
    SELECT AVG(sale_amount) FROM Sales
)
ORDER BY average_sale DESC, e.employee_id ASC;



