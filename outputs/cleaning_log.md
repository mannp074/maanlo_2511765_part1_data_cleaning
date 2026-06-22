# Cleaning Log

## Issues Found

- Irregular spacing in text columns
- Missing values in region and ship_mode
- Mixed date formats
- Exact duplicate rows
- Duplicate order IDs with conflicting information
- Negative discounts
- Discounts above allowed range
- Cancelled orders
- Failed payments
- Refunded orders
- Invalid shipping records (ship date earlier than order date)

## Cleaning Actions Performed

- Removed leading, trailing, and extra spaces
- Standardized text capitalization
- Filled missing region values with 'Unknown'
- Filled missing ship_mode values with 'Unknown'
- Converted mixed date formats into standard format
- Created shipping_delay_days column
- Removed exact duplicate rows
- Flagged duplicate order IDs for review
- Converted discount values to numeric
- Flagged invalid discount records
- Flagged cancelled orders
- Flagged failed payments
- Flagged refunded orders
- Flagged invalid shipping records

## Business Rules Applied

- Missing region → Unknown
- Missing ship_mode → Unknown
- Missing discount → 0
- Negative discount → Invalid
- Discount above allowed range → Invalid
- Cancelled orders excluded from sales summaries
- Failed payments excluded from sales summaries
- Refunded orders summarized separately
- Ship date before order date flagged as invalid

## Records Removed

- Exact duplicate rows removed: 20

## Records Flagged

- Duplicate Order ID Rows: 63
- Invalid Discounts: 22
- Cancelled Orders: 145
- Failed Payments: 69
- Refunded Orders: 71
- Invalid Shipping Records: 93

## Assumptions

- Missing discounts treated as 0
- Unknown region and ship mode retained instead of deleting rows
- Duplicate order IDs retained for manual review

## Limitations

- Conflicting duplicate order IDs require manual investigation.
- Shipping anomalies were flagged but not corrected.
