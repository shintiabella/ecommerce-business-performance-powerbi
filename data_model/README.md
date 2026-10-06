# Data Model

## Overview

The Power BI data model is designed around a star schema structure, separating transactional and event data from descriptive dimension tables.

The model is designed to support sales, product, customer, payment, and marketing funnel analysis through relationships between fact and dimension tables.

## Fact Tables

| Table | Description |
|---|---|
| `fact_order` | Contains SKU-level order data, including quantity, revenue, order date, sales channel, and transaction status indicators. The grain is one row per SKU in an order. |
| `fact_funnel` | Contains marketing funnel event data, including funnel status, channel source, customer, product, and funnel date. |
| `transaction_detail` | Contains detailed transaction and payment information, including total paid, tax, shipping cost, and payment method. |

## Dimension Tables

| Table | Description |
|---|---|
| `dim_product` | Contains product, category, brand, variant, and SKU information. |
| `dim_customer` | Contains customer attributes such as customer type, province, registration channel, and registration date. |
| `dim_payment` | Contains payment IDs and payment method information. |
| `dim_date` | Contains date attributes used for time-based analysis. |
| `dim_status` | Contains funnel status and sort order used to organize funnel stages. |

## Star Schema

The model uses `fact_order` as the primary sales fact table, with dimension tables providing descriptive attributes for analysis.

The `fact_funnel` table supports marketing funnel analysis, while `transaction_detail` provides detailed transaction and payment information.

The data model is designed to support filtering and aggregation across different business dimensions such as date, product, customer, payment method, and funnel status.

![Power BI Data Model](../images/data_model.png)
