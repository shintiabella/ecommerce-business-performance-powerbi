# E-commerce Business Performance Analysis — Power BI

## Project Overview

This project analyzes e-commerce business performance using Power BI, with a focus on data modeling, DAX measures, and interactive dashboard development.

The project uses an e-commerce dataset previously analyzed using PostgreSQL and Looker Studio. In this project, the same dataset is approached from a different perspective by building a star schema data model, developing DAX measures, and creating an interactive Power BI dashboard.

The analysis covers sales performance, product performance, customer behavior, and marketing funnel performance.

## Business Questions

This project aims to answer the following business questions:

- How does revenue change over time?
- Which sales channels and payment methods contribute the most revenue?
- Which product categories and brands generate the highest revenue?
- Which products contribute the most to overall revenue?
- How many customers are purchasing and how many are newly registered?
- How does the marketing funnel perform across different channels?
- What is the conversion rate from funnel events to purchases?

## Dataset & Data Preparation

The project uses an e-commerce transaction dataset containing sales, customer, product, payment, and marketing funnel data.

Data preparation was performed using PostgreSQL before importing the data into Power BI. The preparation process included data cleaning, validation, transformation, and creating tables required for the analytical data model.

The prepared data was then imported into Power BI and structured into a star schema to support analysis and DAX calculations.

## Data Model

The data model follows a star schema structure, with fact tables at the center and dimension tables providing descriptive attributes for analysis.

### Fact Tables

- `fact_order` — order-level sales and transaction data
- `fact_funnel` — marketing funnel events
- `transaction_detail` — detailed transaction and payment information

### Dimension Tables

- `dim_product` — product, category, brand, and SKU information
- `dim_customer` — customer attributes
- `dim_payment` — payment method information
- `dim_date` — date attributes for time-based analysis
- `dim_status` — funnel status and sorting order

The model uses relationships between fact and dimension tables to support filtering, aggregation, and DAX calculations in Power BI.

![Power BI Data Model](images/data_model.png)

## DAX Measures

DAX measures were created to calculate key business metrics used throughout the dashboard.

The main measures include:

- Total Revenue
- Net Revenue
- Total Sales
- Total Quantity
- Total Orders
- Total Customers
- Purchasing Customers
- Average Revenue per Order
- Total Events
- Total Converted Orders
- Conversion Rate
- New Customers

These measures are used across the dashboard to support KPI cards, trend analysis, product analysis, customer analysis, and marketing funnel analysis.

## Dashboard

The Power BI dashboard consists of three pages:

### 1. Executive Summary

Provides an overview of overall business performance through key performance indicators, revenue trends, sales channels, and payment methods.

### 2. Sales & Product Performance

Focuses on sales and product performance, including revenue and quantity by category, top products by revenue, and revenue by brand.

### 3. Customer & Marketing Analysis

Focuses on customer metrics and marketing funnel performance, including customer acquisition, purchasing customers, funnel events, and conversion rates by channel.

![Executive Summary](images/dashboard_page1.png)

![Sales & Product Performance](images/dashboard_page2.png)

![Customer & Marketing Analysis](images/dashboard_page3.png)
