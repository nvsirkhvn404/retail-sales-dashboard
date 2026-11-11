# Dataset

This folder contains the Excel workbook used for the MegaMart Retail Sales Dashboard.

The workbook is organized into four related tables covering sales transactions, customers, products, and stores. These tables are connected in Power BI to build the data model used throughout the report.

## Workbook Overview

**File:** `retail_sales_dataset.xlsx`

| Sheet | Records | Description |
|---|---:|---|
| Transactions | 5,000 | Sales transactions, including date, product, customer, quantity, discount, and payment method |
| Customers | 200 | Customer details such as name, gender, birth date, city, and join date |
| Products | 50 | Product names, categories, subcategories, selling prices, and cost prices |
| Stores | 5 | Store details, including store name, city, and region |

## Dataset Coverage

- **Time period:** September 10, 2023 - September 9, 2025
- **Stores:** 5 across 4 regions
- **Customers:** 200
- **Products:** 50
- **Product categories:** Electronics, Fashion, and Groceries
- **Payment methods:** Cash, Credit Card, Mobile Money, and Bank Transfer

## How the Data Is Used

The four tables serve different purposes in the Power BI data model:

- **Transactions** acts as the central fact table, containing the sales activity.
- **Customers** provides customer information for demographic and purchasing analysis.
- **Products** provides product and pricing information for category and product performance analysis.
- **Stores** provides geographical information for regional and store-level comparisons.

The tables are connected using their respective ID columns. A separate Date table is created in Power BI for time-based analysis.

## Data Source

Originally sourced from:

[Retail Sales Dataset - Kaggle](https://www.kaggle.com/datasets/buharishehu/retail-sales-dataset)

The Excel workbook included in this repository is the version used for this project.

**Note:** This is sample retail data.
