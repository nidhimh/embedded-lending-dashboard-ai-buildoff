# Data Dictionary — Embedded SMB Lending Dataset

Four related tables modeling an embedded merchant cash advance (MCA) fintech.
Join keys: `partner_id` links PARTNERS → ORIGINATIONS → REPAYMENTS/REVENUE_RECOGNIZED;
`origination_id` links ORIGINATIONS → REPAYMENTS/REVENUE_RECOGNIZED.

---

## PARTNERS.csv

Platform partners that embed lending into their software (one row per partner).

| Column | Type | Description |
|---|---|---|
| `partner_id` | string | Unique partner identifier (e.g. `PTR-001`). Primary key. |
| `partner_name` | string | Partner brand name (DoorDash, Amazon, Worldpay, Mindbody, Toast, Squarespace). |
| `partner_category` | string | Business category of the partner platform (e.g. Food & Delivery, E-commerce Marketplace, Payments/Acquiring). |
| `integration_type` | string | How lending is embedded into the partner's product (API - Embedded Checkout, White-label Embedded, API - Embedded Dashboard). |
| `partner_since_date` | date (YYYY-MM-DD) | Date the partnership was established. |
| `platform_revenue_share_pct` | float (decimal) | Share of fee revenue paid to the partner per originated advance, as a decimal (e.g. `0.015` = 1.5%). |
| `primary_verticals_served` | string (comma-separated) | Merchant business verticals typically originated through this partner. |

---

## ORIGINATIONS.csv

One row per funded merchant cash advance.

| Column | Type | Description |
|---|---|---|
| `origination_id` | string | Unique advance identifier (e.g. `ORG-200001`). Primary key. |
| `merchant_id` | string | Unique identifier for the borrowing merchant. |
| `partner_id` | string | Foreign key to `PARTNERS.csv`. |
| `business_vertical` | string | Merchant's industry vertical (e.g. Restaurant, Fitness Studio, E-commerce Retail). |
| `state` | string | US state abbreviation of the merchant's business. |
| `funding_date` | date (YYYY-MM-DD) | Date the advance was disbursed to the merchant. |
| `estimated_maturity_date` | date (YYYY-MM-DD) | Projected payoff date based on estimated term. |
| `avg_monthly_gmv_usd` | float (USD) | Merchant's average monthly gross merchandise value / revenue processed through the partner platform. |
| `prior_advances_count` | integer | Number of previous advances this merchant has taken (0 = first-time borrower). |
| `risk_score` | integer | Internal underwriting risk score (higher = lower risk), range ~500–820. |
| `industry_risk_tier` | string | Categorical risk bucket derived from vertical/industry: `low`, `medium`, `high`. |
| `advance_amount_usd` | float (USD) | Principal amount advanced to the merchant. |
| `factor_rate` | float | Fixed multiplier applied to principal to determine total repayment obligation (e.g. `1.20` = repay 120% of principal). |
| `total_repayment_usd` | float (USD) | Total amount owed by the merchant = `advance_amount_usd × factor_rate`. |
| `total_fee_usd` | float (USD) | Total fee revenue on the advance = `total_repayment_usd − advance_amount_usd`. |
| `remittance_rate` | float (decimal) | Percentage of daily sales automatically withheld as repayment (e.g. `0.12` = 12% of daily sales). |
| `term_estimate_days` | integer | Estimated number of days to full repayment, derived from remittance rate and sales volume. |
| `status` | string | Current state of the advance: `active`, `completed`, `paid_off_early`, `delinquent`, `default`. |
| `pct_repaid` | float (decimal) | Fraction of `total_repayment_usd` collected to date (0.0–1.0). |
| `amount_repaid_usd` | float (USD) | Dollar amount collected to date = `total_repayment_usd × pct_repaid`. |

---

## REPAYMENTS.csv

Transaction-level remittance/payment events against each origination (roughly weekly).

| Column | Type | Description |
|---|---|---|
| `repayment_id` | string | Unique repayment transaction identifier (e.g. `RPY-0000001`). Primary key. |
| `origination_id` | string | Foreign key to `ORIGINATIONS.csv`. |
| `partner_id` | string | Foreign key to `PARTNERS.csv` (denormalized for convenience). |
| `payment_date` | date (YYYY-MM-DD) | Date the remittance/payment was collected. |
| `remittance_amount_usd` | float (USD) | Amount collected in this individual transaction. |
| `cumulative_repaid_usd` | float (USD) | Running total repaid on this origination as of this transaction (monotonically increasing). |
| `payment_method` | string | Collection method: `ach_remittance` (automatic daily/weekly sales withholding) or `manual_payment` (one-off merchant-initiated payment). |

---

## REVENUE_RECOGNIZED.csv

Monthly recognized fee revenue per origination (straight-line recognition of `total_fee_usd` over the advance term, with early write-off on default).

| Column | Type | Description |
|---|---|---|
| `revenue_id` | string | Unique revenue recognition record identifier (e.g. `REV-0000001`). Primary key. |
| `origination_id` | string | Foreign key to `ORIGINATIONS.csv`. |
| `partner_id` | string | Foreign key to `PARTNERS.csv` (denormalized for convenience). |
| `recognition_period` | string (YYYY-MM) | Calendar month in which the revenue is recognized. |
| `revenue_recognized_usd` | float (USD) | Fee revenue recognized in this period. |
| `cumulative_revenue_recognized_usd` | float (USD) | Running total fee revenue recognized on this origination as of this period. |
| `recognition_method` | string | Revenue recognition methodology applied — currently always `straight_line_fee_recognition`. |

---

## Entity Relationship Summary

```
PARTNERS (1) ──< ORIGINATIONS (many)
ORIGINATIONS (1) ──< REPAYMENTS (many)
ORIGINATIONS (1) ──< REVENUE_RECOGNIZED (many)
```
