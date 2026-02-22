# ecommerce-sales-analysis-sql-bi-Olist-Store
This project showcases an end-to-end data analysis workflow using PostgreSQL for data cleaning and transformation, and Power BI for visualization. Using the Brazilian E-Commerce Public Dataset by Olist, it delivers clean, analysis-ready data and interactive dashboards that generate actionable business insights

📌 Project Overview

This project presents an end-to-end analytical pipeline built using the Brazilian E-Commerce Public Dataset by Olist.

The objective was to:

Design a structured SQL data pipeline

Ensure data integrity and consistency

Build an analytical sales view

Develop business dashboards in Power BI

The architecture follows a professional layered approach:
Raw Data → Staging → Production (Clean) → Analytical View → BI Dashboard

🏗️ Data Architecture



1️⃣ Staging Layer

Raw CSV data is ingested into the staging schema using TEXT data types to guarantee import stability.

Purpose:

Avoid truncation errors

Allow flexible profiling

Prepare for structured transformation

Key staging tables:

stg_orders

stg_order_items

stg_customers

stg_products




2️⃣ Production (Clean) Layer

Data is transformed into structured tables with:

Proper data types (NUMERIC, TIMESTAMP, INT)

Standardized text formatting

Business logic applied

Clean relational structure

Core Tables:

Fact Table

order_items (revenue generation point)

Dimension Tables

orders

customers

products

sellers

Design decision:
Data was normalized to prevent redundancy and preserve referential integrity.



3️⃣ Analytical View

A denormalized reporting view was created:

public.view_sales_report

This view integrates:

Time dimensions (year, month, date)

Customer & seller location

Product category

Revenue metrics:

item_revenue

shipping_cost

total_item_amount

This is the layer connected to Power BI.



📊 Key Business Metrics

Total Revenue

Number of Orders

Average Ticket

Sales by State

Top Categories

Top Products

Top Sellers

Monthly Revenue Evolution



🔍 Data Validation & Integrity Checks

Validation was performed in SQL before dashboard development.



✅ Primary Key Checks

No duplicates found in:

orders

customers

products

sellers



✅ Revenue Reconciliation

Revenue totals between:

order_items

view_sales_report

Matched successfully.

⚠ Order Discrepancy Identified

Total Orders in orders: 99,441
Orders in view_sales_report: 98,666
Difference: 775 orders

Explanation:
The analytical view uses INNER JOIN logic, excluding orders without valid relational matches.

✅ Null & Negative Checks

No negative revenue values

No null revenue values

⚠ Late 2018 Dataset Limitation

A sharp revenue decline after June 2018 was investigated.

Validation revealed:
Only 1 delivered order recorded in September 2018.

Conclusion:
The drop reflects dataset incompleteness rather than confirmed market contraction.


📈 Business Insights

Revenue grew steadily between Sep 2016 and May 2018 (+1.15M).

Structural trend reversal observed from June 2018.

Health & Beauty is the leading category (16% of total revenue).

Revenue concentration exists across top sellers and regions.

São Paulo dominates revenue contribution.

Revenue is influenced not only by volume but also by pricing strategy.



🛠️ Tools Used

PostgreSQL

Power BI

GitHub



🎯 Key Learning Outcomes

Designing layered SQL architecture

Fact vs Dimension modeling

Data profiling and validation

Revenue reconciliation

Business-oriented insight generation

Translating SQL analysis into BI storytelling

stg_product_category_translation
