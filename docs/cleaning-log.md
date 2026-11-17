# Cleaning log

Source: UCI Online Retail II dataset.
Original size: 1,067,371 invoice lines.
Date range: 2009-12-01 to 2011-12-09.

## Cleaning results

| rule | what | how_found | action | rows_removed | rows_remaining | customers_remaining | customers_lost | first_order_moved |
|---|---|---|---|---|---|---|---|---|
| Raw | file as received | - | - | 0 | 1,067,371 | 5,942 | 0 | 0 |
| R1 | No customer ID | Customer ID blank | removed | 243,007 | 824,364 | 5,942 | 0 | 0 |
| R2 | Returns and cancellations | Invoice starts with C | removed | 18,744 | 805,620 | 5,881 | 61 | 214 |
| R3 | Non-positive price or quantity | Price <= 0 or Quantity <= 0 | removed | 71 | 805,549 | 5,878 | 3 | 0 |
| R4 | Exact duplicate lines | all 8 columns identical to an earlier line | later copy removed | 26,124 | 779,425 | 5,878 | 0 | 0 |
| R5 | Fee, service, adjustment and test lines | StockCode in POST, C2, DOT, BANK CHARGES, ADJUST, ADJUST2, TEST001, TEST002, D | removed | 2,148 | 777,277 | 5,868 | 10 | 10 |

The cleaned dataset contains 777,277 invoice lines
and 5,868 customers.

## Records kept

- Manual (`M`) entries: 681 lines kept.
- `PADS` and `SP1002`: kept as product codes.
- High-spending customers: retained.

## Returns

Return lines were removed, but the original sales remain.
Gross spending is higher than net spending by
6.4%.

The Spearman correlation between gross and net spending
per customer is 0.986.

## Definitions

- Order: one customer making purchases on one day.
- Scoring snapshot: 2011-12-09.
- Test snapshot: 2011-09-10.
- Training snapshot: 2011-06-12.

952 customers (16.2%)
have their first recorded transaction in December 2009.
They may have purchased from the retailer before the dataset began.

## Limitations

- Transactions without a customer ID are excluded.
- Spending figures are gross rather than net of returns.
- The dataset covers one retailer from December 2009 to December 2011.
