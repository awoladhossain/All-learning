# SQL Exercises : SQL Practice with Solution for Beginners and Experienced

## Sales Table

```sql
-- Create Sales table

CREATE TABLE Sales (
    sale_id INT PRIMARY KEY,
    product_id INT,
    quantity_sold INT,
    sale_date DATE,
    total_price DECIMAL(10, 2),
    FOREIGN KEY (product_id) REFERENCES Products(product_id)
);
```

```sql
-- Insert sample data into Sales table

INSERT INTO Sales (sale_id, product_id, quantity_sold, sale_date, total_price) VALUES
(1, 101, 5, '2024-01-01', 2500.00),
(2, 102, 3, '2024-01-02', 900.00),
(3, 103, 2, '2024-01-02', 60.00),
(4, 104, 4, '2024-01-03', 80.00),
(5, 105, 6, '2024-01-03', 90.00);
```

## Products Table

```sql
-- Create Products table

CREATE TABLE Products (
    product_id INT PRIMARY KEY,
    product_name VARCHAR(100),
    category VARCHAR(50),
    unit_price DECIMAL(10, 2)
);
```

```sql
-- Insert sample data into Products table

INSERT INTO Products (product_id, product_name, category, unit_price) VALUES
(101, 'Laptop', 'Electronics', 500.00),
(102, 'Smartphone', 'Electronics', 300.00),
(103, 'Headphones', 'Electronics', 30.00),
(104, 'Keyboard', 'Electronics', 20.00),
(105, 'Mouse', 'Electronics', 15.00);
```

1. Retrieve all columns from the Sales table.

```sql
SELECT * FROM Sales;
```

2. Retrieve the product_name and unit_price from the Products table.
```sql
SELECT product_name, unit_price FROM Products;
```

3. Retrieve the sale_id and sale_date from the Sales table.

```sql
SELECT sale_id, sale_date FROM Sales;
```

4. Filter the Sales table to show only sales with a total_price greater than $100.

```sql
SELECT * FROM Sales WHERE total_price > 100;
```

5. Highest product price

```sql
select *
from products
where
    unit_price = (
        select max(unit_price)
        from products
    );
```

6. Lowest product price

```sql
select *
from products
where
    unit_price = (
        select min(unit_price)
        from products
    );
```

7. 2nd highest product price

```sql
select *
from products
where
    unit_price = (
        select max(unit_price)
        from products
        where
            unit_price < (
                select max(unit_price)
                from products
            )
    );
```

8. Total Max price of Product

```sql
SELECT MAX(unit_price) FROM Products;
```

9.Filter the Products table to show only products in the 'Electronics' category.

```sql
SELECT * FROM Products WHERE category = 'Electronics';
```

10. Retrieve the sale_id and total_price from the Sales table for sales made on January 3, 2024.

```sql
SELECT sale_id, total_price
FROM Sales
WHERE sale_date = '2024-01-03';
```

11. Retrieve the product_id and product_name from the Products table for products with a unit_price greater than $100.

```sql
SELECT product_id, product_name
FROM Products
WHERE unit_price > 100;
```

12. Calculate the total revenue generated from all sales in the Sales table.

```sql
SELECT SUM(total_price) AS total_revenue
FROM Sales;
```

13. Calculate the average unit_price of products in the Products table.

```sql
SELECT AVG(unit_price) AS average_unit_price
FROM Products;
```

14. Calculate the total quantity_sold from the Sales table.

```sql
SELECT SUM(quantity_sold) AS total_quantity_sold
FROM Sales;
```

15. Count Sales Per Day from the Sales table

```sql
SELECT sale_date, COUNT(*) AS sales_count
FROM Sales
GROUP BY sale_date
ORDER BY sale_date;
```

16. Retrieve product_name and unit_price from the Products table with the Highest Unit Price

```sql
SELECT product_name, unit_price
FROM Products
ORDER BY unit_price DESC
LIMIT 1;
```

17. Retrieve the sale_id, product_id, and total_price from the Sales table for sales with a quantity_sold greater than 4.

```sql
SELECT sale_id, product_id, total_price
FROM Sales
WHERE quantity_sold > 4;
```

18.  Retrieve the product_name and unit_price from the Products table, ordering the results by unit_price in descending order.

```sql
SELECT product_name, unit_price
FROM Products
ORDER BY unit_price DESC;
```

19. Retrieve the total_price of all sales, rounding the values to two decimal places.

```sql
SELECT ROUND(SUM(total_price), 2) AS total_sales
FROM Sales;
```

20. Calculate the average total_price of sales in the Sales table.

```sql
SELECT AVG(total_price) AS average_total_price
FROM Sales
```

21. Retrieve the sale_id and sale_date from the Sales table, formatting the sale_date as 'YYYY-MM-DD'.

```sql
SELECT sale_id, DATE_FORMAT(sale_date, '%Y-%m-%d') AS formatted_date
FROM Sales;
```

22. Calculate the total revenue generated from sales of products in the 'Electronics' category.
```sql
SELECT SUM(Sales.total_price) AS total_revenue
FROM Sales
JOIN Products ON Sales.product_id = Products.product_id
WHERE Products.category = 'Electronics';
```

23. Retrieve the product_name and unit_price from the Products table, filtering the unit_price to show only values between $20 and $600.

```sql
SELECT product_name, unit_price
FROM Products
WHERE unit_price BETWEEN 20 AND 600;
```
24. Retrieve the product_name and category from the Products table, ordering the results by category in ascending order.
```sql
SELECT product_name, category
FROM Products
ORDER BY category ASC;
```

25. Calculate the total quantity_sold of products in the 'Electronics' category.
```sql
SELECT SUM(quantity_sold) AS total_quantity_sold
FROM Sales
JOIN Products ON Sales.product_id = Products.product_id
WHERE Products.category = 'Electronics';
```

26.  Retrieve the product_name and total_price from the Sales table, calculating the total_price as quantity_sold multiplied by unit_price.
```sql
SELECT product_name, quantity_sold * unit_price AS total_price
FROM Sales
JOIN Products ON Sales.product_id = Products.product_id;
```

27. Identify the Most Frequently Sold Product from Sales table
```sql
SELECT product_id, COUNT(*) AS sales_count
FROM Sales
GROUP BY product_id
ORDER BY sales_count DESC
LIMIT 1;
```

28. Find the Products Not Sold from Products table
```sql
SELECT product_id, product_name
FROM Products
WHERE product_id NOT IN (SELECT DISTINCT product_id FROM Sales);
```

29. Calculate the total revenue generated from sales for each product category.
```sql
SELECT p.category, SUM(s.total_price) AS total_revenue
FROM Sales s
JOIN Products p ON s.product_id = p.product_id
GROUP BY p.category;
```

30. Find the product category with the highest average unit price.
```sql
SELECT category
FROM Products
GROUP BY category
ORDER BY AVG(unit_price) DESC
LIMIT 1;
```
