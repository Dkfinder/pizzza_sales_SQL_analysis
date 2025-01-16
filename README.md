# pizzza_sales_SQL_analysis
Project Overview
This repository contains the MySQL-based analysis of pizza sales data. The project focuses on analyzing sales trends, customer preferences, and product performance. By querying and organizing the data in MySQL, we aim to uncover insights that can guide decision-making, marketing strategies, and operational improvements for pizza businesses.

Features
Sales Overview: Analyzing total sales over time (daily, weekly, monthly).
Product Performance: Identifying top-selling pizzas and understanding customer preferences.
Customer Segmentation: Analyzing sales data based on customer demographics and regions.
Order Insights: Understanding average order value, order frequency, and repeat customer rates.
Time-based Trends: Analyzing how sales change by day, week, month, or season.
Promotions & Discounts: Evaluating the impact of special offers on sales.
Tools Used
MySQL: Used for querying, analyzing, and managing the database.
SQL Queries: Custom queries designed to pull insights from the sales data.
Data: The dataset consists of transactional data, including orders, products, customers, and discounts.
Dataset
The dataset used in this project includes sales records, customer information, product details (pizza types), and promotional offers. The data is assumed to be anonymized and is used solely for analysis purposes.

Example Data Schema:
orders: Contains order details (order_id, customer_id, product_id, quantity, order_date, total_amount).
products: Contains pizza product details (product_id, name, category, price).
customers: Contains customer details (customer_id, name, region, contact).
discounts: Contains promotional discount details (discount_id, order_id, discount_value).
Installation & Setup
Prerequisites
Install MySQL: Download and install MySQL from the official website: MySQL Downloads.
Install MySQL Workbench or phpMyAdmin for easy database management.
Steps
Clone the repository to your local machine:

bash
Copy
git clone https://github.com/dkfinder/pizza-sales-analysis.git
Import the Database:

If the repository includes a SQL dump file (pizza_sales_data.sql), import it into MySQL using the following command in your MySQL Workbench or via the command line:
bash
Copy
mysql -u username -p database_name < pizza_sales_data.sql
Set up your Database: If your project contains separate scripts for setting up the database schema and tables, run them in the correct order:

sql
Copy
source create_tables.sql;
source insert_data.sql;
Run SQL Queries: Open MySQL Workbench and execute the provided queries or create new ones to analyze the data.

How to Use
Open the database: Connect to the MySQL database using your MySQL client (e.g., MySQL Workbench or phpMyAdmin).
Run Queries: Use the SQL queries provided in the repository to get insights about pizza sales, customer behavior, and trends.
Example query to calculate total sales for the past month:
sql
Copy
SELECT SUM(total_amount) FROM orders WHERE order_date BETWEEN '2024-12-01' AND '2024-12-31';
Modify and Extend: You can extend the analysis by adding new tables, queries, or integrating this project with a front-end dashboard or reporting tool.
Example Queries
Here are a few example SQL queries to get started:

Total Sales by Month:

sql
Copy
SELECT MONTH(order_date) AS month, SUM(total_amount) AS total_sales
FROM orders
GROUP BY MONTH(order_date)
ORDER BY month;
Top Selling Pizzas:

sql
Copy
SELECT p.name, SUM(o.quantity) AS total_quantity_sold
FROM orders o
JOIN products p ON o.product_id = p.product_id
GROUP BY p.name
ORDER BY total_quantity_sold DESC
LIMIT 10;
Sales by Customer Region:

sql
Copy
SELECT c.region, SUM(o.total_amount) AS total_sales
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id
GROUP BY c.region;
Contributing
If you'd like to contribute to this project, feel free to fork the repository, make changes, and submit a pull request. Ensure that you follow the repository’s structure and naming conventions.

License
This project is licensed under the MIT License - see the LICENSE file for details.

