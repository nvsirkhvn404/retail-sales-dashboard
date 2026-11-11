# MegaMart Retail Sales Dashboard

An interactive Power BI dashboard analyzing retail sales performance across 5 stores, 200 customers, and 50 products over a 2-year period (Sep 2023 - Sep 2025). Built as a hands-on project to practice data modelling, DAX, and dashboard design.

# Dashboard Demo
![Dashboard Demo](screenshots/dashboard-demo.gif) 

## Overview

This project takes a raw, multi-table retail dataset through the full BI workflow: data cleaning, star schema modelling, DAX measure development, and interactive report design. six report pages, 20+ DAX measures, and cross-filtered slicers throughout.

**Source data:** [Retail Sales Dataset](dataset\retail_sales_dataset.xlsx) *(adapted into a multi-table structure for this project)*

## Data Model

Star schema with one fact table and three dimension tables, plus a dedicated date dimension for time intelligence.

```
dim_customers ─┐
dim_products ──┼──► fact_transactions ◄── Date
dim_stores ────┘
```

| Table | Grain | Rows |
|---|---|---|
| `fact_transactions` | One row per line item | 5,000 |
| `dim_customers` | One row per customer | 200 |
| `dim_products` | One row per product | 50 |
| `dim_stores` | One row per store | 5 |
| `Date` | One row per calendar day | ~730 |

## Key DAX Measures

Organized into display folders inside a dedicated `_measures` table:

- **Core** - `Total Sales`, `Total Profit`, `Profit Margin %`, `Avg Order Value`, `Total Transactions`
- **Time Intelligence** - `Sales YoY %`, `Sales MTD`, `Sales YTD`, `Rolling 3M Sales`
- **Customer** - `Customer Lifetime Value`, `Repeat Purchase Rate`, `Avg Orders per Customer`
- **Rank** - `Product Sales Rank`, `Store Sales Rank`, `Top 10 Flag`

Example:
```dax
Total Sales =
SUMX(
    fact_transactions,
    fact_transactions[quantity]
    * RELATED(dim_products[unit_price])
    * (1 - fact_transactions[discount])
)
```

## Report Pages

| Page | What it shows |
|---|---|
| **Executive Overview** | Company-wide KPIs, monthly sales trend, category and region breakdown |
| **Products** | Top/bottom performers, cost vs. revenue, category-subcategory treemap, discount trends |
| **Stores & Region** | Store and city-level performance, region × month sales heatmap |
| **Customers** | Demographics, lifetime value, repeat purchase rate, top spenders |
| **Time Intelligence** | YoY comparison, rolling averages, quarter × year matrix |
| **Payment Method** | Sales and discount behavior split by payment type |

All pages share a `synced filter` panel (region, category, payment method, age group, date range), selections made on any page apply across the whole report.

## Screenshots

<details open>
<summary>View all pages</summary>

![Overview](screenshots/01-executive-overview.png)
![Products](screenshots/02-products.png)
![Stores & Region](screenshots/03-stores-region.png)
![Customers](screenshots/04-customers.png)
![Time Intelligence](screenshots/05-time-intelligence.png)
![Payment Method](screenshots/06-payment-method.png)

</details>

## Running This Yourself

1. Clone the repo.
2. Open `retail_sales_dashboard.pbip` in Power BI Desktop.
3. If prompted, point the data source to the `dataset/` folder.
4. Refresh.

---

*Built as a learning project, feedbacks are welcome.*