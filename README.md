# mysql-questions

![mysql1](https://github.com/user-attachments/assets/ea65c48d-cabf-46b2-814b-dec556c89753)

![mysql2](https://github.com/user-attachments/assets/2ed70fbc-813c-4b35-9f5b-754dded82661)

![mysql3](https://github.com/user-attachments/assets/43ddb4fa-ec2c-424e-a7f8-811721e402b0)

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



