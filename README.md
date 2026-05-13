# project-sql-analytics | SQL Data Warehouse Analytics Project

## Overview

This project demonstrates the creation of a SQL-based Data Warehouse for sales analytics and business intelligence reporting.

The project includes:

- Database and schema creation
- Dimension and fact table setup
- Bulk data loading from CSV files
- Analytical SQL queries
- Customer and product reporting views
- Segmentation and ranking analysis

The solution is designed using a simple star-schema architecture with fact and dimension tables.

---

# Database Architecture

## Database
- `DataWarehouse`

## Schema
- `gold`

---

# Tables

## Dimension Tables

### `gold.dim_customers`
Stores customer-related information.

| Column | Description |
|---|---|
| customer_key | Unique customer key |
| customer_id | Customer ID |
| customer_number | Customer reference number |
| first_name | Customer first name |
| last_name | Customer last name |
| country | Customer country |
| marital_status | Marital status |
| gender | Gender |
| birthdate | Date of birth |
| create_date | Record creation date |

---

### `gold.dim_products`
Stores product-related information.

| Column | Description |
|---|---|
| product_key | Unique product key |
| product_id | Product ID |
| product_number | Product reference number |
| product_name | Product name |
| category | Product category |
| subcategory | Product subcategory |
| cost | Product cost |
| product_line | Product line |

---

## Fact Table

### `gold.fact_sales`
Stores transactional sales data.

| Column | Description |
|---|---|
| order_number | Order identifier |
| product_key | Product foreign key |
| customer_key | Customer foreign key |
| order_date | Order date |
| shipping_date | Shipping date |
| due_date | Due date |
| sales_amount | Sales amount |
| quantity | Quantity sold |
| price | Unit price |

---

# Features

## 1. Database Setup
- Drops and recreates the database
- Creates schema and tables
- Supports fresh project initialization

---

## 2. Bulk Data Loading
Data is imported using SQL Server `BULK INSERT`.

### Imported CSV Files
- `gold_sub_customers.csv`
- `gold_sub_products.csv`
- `gold_fact_sales.csv`

---

# Analytical SQL Queries

## Magnitude Analysis
Used for measuring and aggregating business metrics.

### Includes:
- Total customers by country
- Customers by gender
- Products by category
- Average cost by category
- Revenue by category
- Revenue by customer
- Sold items by country

### SQL Concepts Used
- `SUM()`
- `COUNT()`
- `AVG()`
- `GROUP BY`
- `ORDER BY`

---

## Ranking Analysis
Ranks products and customers based on performance.

### Includes:
- Top 5 revenue-generating products
- Worst-performing products
- Top customers by revenue
- Customers with the fewest orders

### SQL Concepts Used
- `TOP`
- `RANK()`
- `ROW_NUMBER()`
- Window functions

---

# Customer Report View

## View Name
`gold.report_customers`

### Purpose
Provides consolidated customer-level analytics and KPIs.

### Metrics Included
- Total orders
- Total sales
- Total quantity purchased
- Total products purchased
- Customer lifespan
- Recency
- Average order value
- Average monthly spend

### Customer Segments
- VIP
- Regular
- New

### Age Groups
- Under 20
- 20–29
- 30–39
- 40–49
- 50 and above

---

# Product Report View

## View Name
`gold.report_products`

### Purpose
Provides consolidated product-level analytics and KPIs.

### Metrics Included
- Total orders
- Total sales
- Total quantity sold
- Total customers
- Product lifespan
- Average selling price
- Average order revenue
- Average monthly revenue

### Product Segments
- High-Performer
- Mid-Range
- Low-Performer

---

# Segmentation Analysis

## Product Segmentation
Products grouped by cost ranges:
- Below 100
- 100–500
- 500–1000
- Above 1000

---

## Customer Segmentation
Customers grouped by:
- VIP
- Regular
- New

Based on:
- Spending behavior
- Customer lifespan

---

# Technologies Used

- SQL Server
- T-SQL
- SQL Server Management Studio (SSMS)

---

# How to Run

## Step 1
Open SQL Server Management Studio (SSMS)

## Step 2
Run the SQL script in the following order:
1. Database creation
2. Table creation
3. Data loading
4. Analytical queries
5. Report views

## Step 3
Verify tables and views inside:
```sql
DataWarehouse > gold
