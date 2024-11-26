Sales Insights Data Analysis Project
Table of Contents
1.	Overview
2.	Project Objectives
3.	Dataset Information
4.	SQL Queries
5.	Power BI Analysis
6.	Insights and Results
7.	Future Enhancements
Overview
The Sales Insights Data Analysis Project showcases how raw sales data can be 
transformed into meaningful insights through structured query language (SQL) and visualization tools 
like Power BI. This project provides answers to various business queries such as customer records, 
market-specific sales, and total revenue in specific time periods.
Project Objectives
To perform data extraction, transformation, and analysis using SQL.
To normalize sales data for consistent comparison using Power BI.
To generate business-critical insights, such as total revenue, market-specific transactions, and product sales trends.
Dataset Information
The project uses the following tables:

Customers: Contains customer details.
Transactions: Includes sales transaction data, such as product codes, market codes, sales amount, and currency.
Date: Contains date-related details such as year, month, and day for joining with transactions.

Key columns:

- Customers Table: customer_id, customer_name, location
- Transactions Table: transaction_id, product_code, sales_amount, currency, market_code
- Date Table: date, year, month, month_name
SQL Queries
A detailed set of SQL queries is included to analyze the sales data. 
These queries address key business requirements:

- Retrieve all customer records.
- Count the total number of customers.
- Filter transactions for the Chennai market (Mark001).
- Identify distinct product codes sold in Chennai.
- Fetch transactions in 2020 and calculate total revenue.
- Analyze revenue at a monthly level (e.g., January 2020).

Example SQL Query:

SELECT SUM(transactions.sales_amount) 
FROM transactions 
INNER JOIN date ON transactions.order_date = date.date 
WHERE date.year = 2020 AND date.month_name = 'January' 
AND (transactions.currency = 'INR' OR transactions.currency = 'USD');
Power BI Analysis
Data Transformation
To normalize sales amounts across currencies, a calculated column norm_amount was created:

= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]75 else [sales_amount], type any)

Key Visualizations
- Revenue trends by year and month.
- Product-wise sales distribution.
- Market-specific sales comparison (e.g., Chennai vs. other markets).
- Currency normalization impact on total revenue.
Insights and Results
- Chennai market contributed significantly to total sales in 2020, with X% of the total revenue.
- January 2020 was the highest revenue-generating month, accounting for Y% of yearly sales.
- USD transactions normalized to INR contributed to Z% of the total sales.
- The top-performing product codes in Chennai were P001, P002, and P003.
Future Enhancements
Advanced Analysis
- Implement predictive models to forecast sales trends using Python or R.
- Explore customer segmentation using clustering techniques.

Integration
- Link the dataset with external data sources like regional demographics for enhanced insights.

Visualization
- Use advanced Power BI features like drill-throughs and KPI indicators.
- Publish Power BI dashboards for real-time monitoring.

Optimization
- Optimize SQL queries for faster execution using indexing and query tuning techniques.
How to Run This Project
1. Set up a database and import the datasets (customers, transactions, date).
2. Execute the SQL scripts provided in the repository for data analysis.
3. Load the data into Power BI and apply the provided formulas for normalization and visualization.
Conclusion
This project demonstrates how SQL and Power BI can be used effectively to analyze sales data and deliver actionable insights. It provides a strong foundation for exploring more advanced analytics and visualization techniques.
