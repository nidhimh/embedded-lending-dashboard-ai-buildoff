# Stakeholder Briefs 

Below is a one-paragraph brief for each, framed around what that stakeholder specifically needs and how the dashboard project demonstrates it.

---

## 1. Finance (internal finance team / leadership)

The dashboard tracks $39.68M in total origination principal disbursed across all partners from January 2022 through August 2026, broken out by partner and month with an accompanying trend chart. Current annualized revenue run-rate, based on a 3-month trailing average of recognized fee revenue (to smooth out single-month noise), sits in the low-to-mid $900K–$1.6M range depending on the period and is refreshed automatically as new revenue rows are added. Portfolio credit performance is visible in the Cohort Delinquency tab: 7.0% of total dollar volume across all origination cohorts is currently delinquent or in default, with a color-coded view showing which vintage months are underperforming so we can watch for deteriorating cohorts early.

## 2. Engineering / Data
The workbook has four raw data tabs (PARTNERS, ORIGINATIONS, REPAYMENTS, REVENUE_RECOGNIZED) feeding three analysis tabs, all built on live SUMIFS/INDEX-MATCH formulas rather than static values, so the dashboard recalculates correctly if the underlying CSVs are refreshed. The Reconciliation tab does an anti-join to surface any origination_id in ORIGINATIONS with zero matching rows in REPAYMENTS — it currently flags 10 records (7 funded within the last two weeks, which is expected lag; 3 funded 9–12 months ago with no repayments at all, which is a genuine data-integrity gap worth investigating in the source system). Worth noting: those 10 gap records were synthetically added to demonstrate the tab, since the original dataset had a clean 1-to-1 match with no gaps.

## 3. Partners
This dashboard gives visibility into how your merchants' advances are performing on the platform — total capital originated by month, how quickly it's being repaid, and how each funding cohort is trending on delinquency. Across the full portfolio, 93% of dollar volume is repaying on schedule or has already been paid off, with the remaining 7% currently delinquent or in default, broken out by the month each cohort was funded so we can spot and discuss any concerning trends together early rather than after they compound.
