# Business Data Cleaning, Validation & Excel Reporting

## Problem Summary

This project focuses on cleaning and validating retail order data exported from multiple systems. The raw dataset contained inconsistent text values, mixed date formats, duplicate records, missing values, discount anomalies, and order status issues. The objective was to prepare an analysis-ready dataset and generate reports that can be used for business review and decision making.

---

## Dataset Description

The dataset contains order-level transaction data with information related to:

- Order details
- Customer information
- Product category and sub-category
- Shipping information
- Quantity, price, sales, cost and profit
- Payment status and order status

Total records in raw dataset: **932**

Final records after cleaning: **912**

---

## Tools Used

- Python
- Pandas
- Jupyter Notebook
- Microsoft Excel

---

## Data Cleaning Process

### Text Standardization

The following columns were cleaned and standardized:

- customer_name
- segment
- region
- state
- city
- category
- sub_category
- ship_mode
- payment_status
- order_status

Cleaning actions:

- Removed leading and trailing spaces
- Removed irregular spacing
- Standardized capitalization
- Filled missing region values with "Unknown"
- Filled missing ship mode values with "Unknown"

---

### Date Cleaning

The raw data contained multiple date formats including:

- DD MMM YYYY
- MM/DD/YYYY
- YYYY-MM-DD
- DD-MM-YYYY

Actions performed:

- Converted all dates into a consistent format
- Created shipping_delay_days column
- Identified invalid shipping records

---

### Duplicate Handling

Duplicate checks were performed on the dataset.

Results:

- Exact duplicate rows found: 20
- Duplicate order ID rows found: 63
- Exact duplicates removed: 20
- Duplicate order IDs retained and flagged for review

---

## Business Rules Applied

- Missing region values were replaced with "Unknown".
- Missing ship mode values were replaced with "Unknown".
- Missing discount values were treated as zero.
- Negative discounts were marked invalid.
- Discounts above the allowed range were marked invalid.
- Cancelled orders were excluded from completed sales summaries.
- Failed payment orders were excluded from completed sales summaries.
- Refunded orders were analyzed separately.
- Records with ship date earlier than order date were flagged.

---

## Data Quality Issues Identified

| Issue | Count |
|---------|------:|
| Invalid Discounts | 22 |
| Cancelled Orders | 145 |
| Failed Payments | 69 |
| Refunded Orders | 71 |
| Invalid Shipping Records | 93 |
| Exact Duplicate Rows Removed | 20 |
| Duplicate Order ID Rows Flagged | 63 |

---

## Calculated Columns Created

The following columns were added:

- cleaned_discount
- calculated_sales
- calculated_profit
- profit_margin
- shipping_delay_days
- order_month
- order_year
- data_quality_flag
- sales_difference
- profit_difference

---

## Data Quality Classification

| Category | Records |
|-----------|-------:|
| Clean | 612 |
| Warning | 187 |
| Invalid | 113 |

---

## Reports Generated

### Data Quality Report

The report contains:

- Missing value summary
- Duplicate summary
- Invalid discount summary
- Date issue summary
- Order status summary
- Sales and profit mismatch summary
- Final quality summary

---

### Pivot Reports

The following pivot summaries were created:

1. Sales and profit by region
2. Sales and profit by category and sub-category
3. Order count by ship mode
4. Profit margin by customer segment
5. Refunded, cancelled and failed orders by region
6. Monthly sales trend

---

## Key Business Insights

- West and East regions generated the highest sales.
- Technology products contributed significantly to profit.
- Copiers and Furnishings were among the most profitable sub-categories.
- A considerable number of orders were cancelled or had failed payments, affecting realized sales.
- Several shipping records showed date inconsistencies and require manual verification.
- Duplicate order IDs were retained for further review instead of being removed automatically.

---

## Assumptions

- Missing discount values were treated as zero.
- Missing region and ship mode values were replaced with "Unknown".
- Duplicate order IDs were preserved and flagged rather than deleted.
- Invalid shipping records were flagged but not corrected manually.

---

## Limitations

- Conflicting duplicate order IDs require manual investigation.
- Shipping date anomalies were only flagged.
- The analysis depends on the quality of the source data exported from multiple systems.
- Some business decisions regarding invalid records may require domain expertise.

---

## Screenshots Included

- raw_data_preview.png
- cleaned_data_preview.png
- pivot_summary_1.png
- pivot_summary_2.png

---

## Repository Structure

```
part1_data_cleaning/
│
├── data/
│   ├── raw_orders.xlsx
│   └── cleaned_orders.xlsx
│
├── outputs/
│   ├── data_quality_report.xlsx
│   ├── pivot_summary.xlsx
│   └── cleaning_log.md
│
├── screenshots/
│   ├── raw_data_preview.png
│   ├── cleaned_data_preview.png
│   ├── pivot_summary_1.png
│   └── pivot_summary_2.png
│
└── README.md
```

This project demonstrates a complete data cleaning, validation and reporting workflow for retail sales data using Python and Excel.
