# ecommerce-sales-analysis-sql-bi-Olist-Store
This project showcases an end-to-end data analysis workflow using PostgreSQL for data cleaning and transformation, and Power BI for visualization. Using the Brazilian E-Commerce Public Dataset by Olist, it delivers clean, analysis-ready data and interactive dashboards that generate actionable business insights


Brazilian E-Commerce (Olist) – End-to-End SQL Data Pipeline & BI Analysis
📌 Project Overview

This project presents a complete analytical pipeline built using the Brazilian E-Commerce Public Dataset by Olist.

The objective was to:

Design a structured SQL data pipeline

Clean and transform raw transactional data

Validate data integrity before reporting

Create an analytical sales view

Develop business dashboards in Power BI

The architecture follows a professional layered approach:

Raw Data → Staging → Production (Clean) → Analytical View → BI Dashboard

🏗️ Data Architecture

The pipeline is divided into structured layers to ensure clarity, scalability, and data integrity.

1️⃣ Staging Layer (Raw Ingestion)

Raw CSV data is loaded into a staging schema using TEXT data types.

Purpose:

Guarantee smooth data ingestion

Avoid truncation errors

Allow flexible data profiling

Prepare data for structured transformation

Key staging tables:

stg_orders

stg_order_items

stg_customers

stg_products

stg_product_category_translation

2️⃣ Production Layer (Clean Tables)

Data is transformed into structured tables with:

Proper data types (NUMERIC, TIMESTAMP, INT)

Standardized formatting

Business logic applied

Referential integrity preserved

Fact Table (Revenue Generation Point)

order_items

Dimension Tables

orders

customers

products

sellers

Design principle:
Data normalization was applied to avoid redundancy and ensure maintainability.

3️⃣ Analytical View

A denormalized reporting view was created:

public.view_sales_report

This view integrates:

Time Dimensions

sale_date

sale_year

sale_month

Identifiers

order_id

customer_id

seller_id

Business Dimensions

product category

customer location

seller location

Revenue Metrics

item_revenue

shipping_cost

total_item_amount

This view serves as the data source for Power BI dashboards.

📊 Key Business Metrics

The following KPIs were developed:

Total Revenue

Number of Orders

Average Ticket

Sales by State

Top Products

Top Categories

Top Sellers

Monthly Revenue Evolution

🔍 Data Validation & Integrity Checks

All validation was performed in SQL before dashboard development.

✅ Primary Key Validation

No duplicate records were found in:

orders

customers

products

sellers

✅ Revenue Reconciliation

Revenue totals between:

order_items

view_sales_report

were successfully reconciled with consistent results.

⚠ Order Count Discrepancy

Total Orders in orders: 99,441
Orders in analytical view: 98,666
Difference: 775 orders

Explanation:
The analytical view uses INNER JOIN logic, excluding orders without valid relational matches.

⚠ Late 2018 Dataset Limitation

A sharp revenue decline was observed after June 2018.

Further validation showed:

Only 1 delivered order recorded in September 2018

Conclusion:
The drop reflects dataset incompleteness rather than confirmed market contraction.

✅ Null & Negative Checks

No negative revenue values detected

No null revenue values detected

The final dataset ensures analytical consistency for reporting purposes.

📈 Business Insights

Revenue grew steadily between Sep 2016 and May 2018 (+1.15M).

A structural trend reversal occurred from June 2018.

Health & Beauty is the leading category (16% of total revenue).

Revenue concentration exists across top sellers and key regions.

São Paulo dominates revenue contribution.

Revenue performance is influenced by pricing strategy, not only volume.

🛠 Tools Used

PostgreSQL

Power BI

GitHub

🎯 Key Learning Outcomes

Layered SQL architecture design

Fact vs Dimension modeling

Data profiling and integrity validation

Revenue reconciliation techniques

Business-oriented insight generation

Translating SQL analysis into BI storytelling

