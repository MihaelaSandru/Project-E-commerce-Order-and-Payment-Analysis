E-commerce-Order-and-Payment-Analysis

Overview
This project aims to analyze e-commerce order and payment data to generate monthly dashboards and exception reports. The analysis involves loading data, performing data validation, and understanding delivery times. Future work includes generating comprehensive monthly key performance indicators (KPIs) and identifying critical exceptions.

Data Sources
Two primary datasets are used:

Orders.csv: Contains detailed information about customer orders.
Order_payements.csv: Contains payment-related information.
Current Status & Key Findings
Data Loading & Configuration
pandas, numpy, and matplotlib are imported for data manipulation and visualization.
Configuration variables for file names (ORDERS_FILE, PAYMENTS_FILE) and Service Level Agreement (SLA) days are set.
DataFrames orders and payments are loaded using dedicated functions.
Data Validation
Orders Validation:

No duplicate order_ids found.
Significant number of missing purchase dates (59,810) and delivery dates (63,087).
Critical Issue: 60,126 delivered orders are missing order_delivered_customer_date, severely impacting delivery time analysis.
Payments Validation:

No duplicate payments, missing order IDs, or missing payment values.
9 zero-value payments identified.
Cross-Table Validation - Critical Mismatch:

There is no common order_id between the orders and payments DataFrames.
Order_payements.csv contains order_purchase_timestamp and order_delivered_customer_date columns, suggesting it might be an orders dataset rather than just payment details for Orders.csv. This mismatch is a major blocker for any combined analysis.
Date Conversion & Delivery Analysis
Date columns in the orders DataFrame (order_purchase_timestamp, order_delivered_customer_date, order_estimated_delivery_date) have been converted to datetime objects.
delivery_time and delivery_days are calculated for delivered orders.
Delivery time is categorized into groups, but due to the high number of missing order_delivered_customer_date values, the current analysis shows an abnormally high percentage (98.2%) of orders falling into the >20 days category, indicating data quality issues impacting these metrics.

Generate Monthly Dashboard: Implementation is pending the resolution of the data mismatch, as payment data is crucial for monthly KPIs.
Generate Exception Reports: Implementation is pending the resolution of data quality issues.
How to Run
Ensure Orders.csv and Order_payements.csv are available in the working directory.
Run all cells in the notebook sequentially.
Dependencies
pandas
numpy
matplotlib
