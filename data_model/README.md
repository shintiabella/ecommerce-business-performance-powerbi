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

## Relationships

The model uses many-to-one relationships with single-direction filtering between transactional tables and their related dimensions.

| From | To | Status |
|---|---|---|
| `fact_funnel[customer_id]` | `dim_customer[customer_id]` | Inactive |
| `fact_funnel[order_id]` | `fact_order[order_id]` | Inactive |
| `fact_funnel[sku_id]` | `dim_product[sku_id]` | Active |
| `fact_funnel[status]` | `dim_status[status]` | Active |
| `fact_order[customer_id]` | `dim_customer[customer_id]` | Active |
| `fact_order[order_date]` | `dim_date[date]` | Active |
| `fact_order[sku_id]` | `dim_product[sku_id]` | Active |
| `fact_order[transaction_id]` | `transaction_detail[transaction_id]` | Active |
| `transaction_detail[customer_id]` | `dim_customer[customer_id]` | Inactive |
| `transaction_detail[payment_method]` | `dim_payment[payment_id]` | Active |
