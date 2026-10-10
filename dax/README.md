# DAX Measures

## Overview

DAX measures were created in Power BI to calculate business metrics and support interactive analysis across the dashboard.

The measures are organized into three main areas:

- Sales & Revenue
- Customer Analysis
- Marketing Funnel

## Sales & Revenue Measures

### 1. Total Revenue

Calculates the total revenue from order items after discounts.

```dax
Total Revenue =
SUM(fact_order[after_discount])
```

### 2. Net Revenue

Calculates revenue from valid transactions that meet the net transaction criteria.

```dax
Net Revenue =
CALCULATE(
    [Total Revenue],
    fact_order[is_valid] = 1,
    fact_order[is_net] = 1
)
```

### 3. Total Sales

Calculates the total amount paid across transactions.

```dax
Total Sales =
SUM(transaction_detail[total_paid])
```

### 4. Total Shipping

Calculates the total shipping cost across transactions.

```dax
Total Shipping =
SUM(transaction_detail[shipping_cost])
```

### 5. Total Tax

Calculates the total tax across transactions.

```dax
Total_Tax =
SUM(transaction_detail[tax])
```

### 6. Total Quantity

Calculates the total quantity of products ordered.

```dax
Total Quantity =
SUM(fact_order[quantity])
```

### 7. Total Orders

Counts the distinct orders recorded in the order table.

```dax
Total Orders =
DISTINCTCOUNT(fact_order[order_id])
```

### 8. Net Orders

Counts distinct orders that meet the valid and net transaction criteria.

```dax
Net Orders =
CALCULATE(
    DISTINCTCOUNT(fact_order[order_id]),
    fact_order[is_valid] = 1,
    fact_order[is_net] = 1
)
```

### 9. Average Revenue per Order

Calculates average revenue per order by dividing total revenue by the number of distinct orders.

```dax
Average Revenue per Order =
DIVIDE(
    [Total Revenue],
    [Total Orders]
)
```

### 10. Net Average Revenue per Order

Calculates average net revenue per net order.

```dax
Net Average Revenue per Order =
DIVIDE(
    [Net Revenue],
    [Net Orders]
)
```

## Customer Measures

### 1. Total Customers

Counts the distinct customers recorded in the order table.

```dax
Total Customers =
DISTINCTCOUNT(fact_order[customer_id])
```

### 2. Customers with Purchase

Counts distinct customers with valid and net transactions.

```dax
Customers with Purchase =
CALCULATE(
    DISTINCTCOUNT(fact_order[customer_id]),
    fact_order[is_valid] = 1,
    fact_order[is_net] = 1
)
```

### 3. Customers with Purchase 2024

Counts distinct customers with valid and net transactions in 2024.

```dax
Customers with Purchase 2024 =
CALCULATE(
    DISTINCTCOUNT(fact_order[customer_id]),
    fact_order[is_valid] = 1,
    fact_order[is_net] = 1,
    dim_date[year] = 2024
)
```

### 4. New Customers 2024

Counts distinct customers who registered in 2024.

```dax
New Customers 2024 =
CALCULATE(
    DISTINCTCOUNT(dim_customer[customer_id]),
    YEAR(dim_customer[registration_date]) = 2024
)
```

## Marketing Funnel Measures

### 1. Total Events

Counts the total number of marketing funnel events.

```dax
Total Events =
COUNTROWS(fact_funnel)
```

### 2. Total Converted Orders

Counts the distinct orders recorded in the marketing funnel table.

```dax
Total Converted Orders =
DISTINCTCOUNT(fact_funnel[order_id])
```

### 3. Conversion Rate

Calculates the ratio of distinct orders in the marketing funnel table to the total number of funnel events.

```dax
Conversion Rate =
DIVIDE(
    [Total Converted Orders],
    [Total Events],
    0
)
```
