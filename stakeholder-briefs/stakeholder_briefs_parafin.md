# Stakeholder Briefs — Finance Data Lead Project (Parafin)

The JD names five groups this role serves directly: Finance, Product, GTM, Engineering/Data, and Investors/Lenders/Board. Below is a one-paragraph brief for each, framed around what that stakeholder specifically needs and how the dashboard project demonstrates it.

---

## 1. Finance (internal finance team / leadership)
Finance needs trustworthy, current numbers on origination volume, revenue run-rate, and portfolio health without having to chase down a spreadsheet every time. This project's Metrics Dashboard tracks exactly those three things — origination principal by partner and month, a 3-month trailing average annualized revenue run-rate (deliberately smoothed so leadership isn't reacting to single-month noise), and portfolio-wide delinquency — all built on live formulas so the numbers stay correct as new data lands, not a static snapshot someone has to remember to refresh.

## 2. Product
Product needs to know how lending performance breaks down by partner integration and merchant vertical, so they can prioritize roadmap decisions — e.g., is a partner's embedded flow originating well but converting poorly, or underwriting worse than others. The partner × month cross-tab and cohort-level views in this dashboard are built to answer exactly that kind of "is this partner integration working" question, without Product needing to write their own query.

## 3. GTM (sales / partnerships)
GTM needs quick, credible numbers to bring into partner conversations — origination growth, repayment health, how a specific partner's book is performing relative to others — often on short notice. This project's Reconciliation and Cohort tabs are built so that kind of ad hoc pull ("how's the DoorDash book doing this quarter") is a filter away rather than a custom analysis, with the underlying logic transparent enough that GTM can trust what they're repeating externally.

## 4. Engineering / Data
Engineering cares about whether financial data is structured cleanly, whether there's a real audit trail, and whether Finance is quietly maintaining a fragile pile of manual overrides. This project's four-table relational structure (PARTNERS, ORIGINATIONS, REPAYMENTS, REVENUE_RECOGNIZED) with clear join keys, plus a Reconciliation tab that does a live anti-join to catch orphaned records, is meant to show the habit of building financial data as something a data team could pick up and trust — not a one-off Excel artifact.

## 5. Investors / Lenders / Board
This audience needs a small number of defensible, well-labeled metrics — origination volume, revenue run-rate, delinquency by vintage — presented in a way that survives scrutiny in a board deck or lender diligence request. The cohort delinquency view in particular speaks their language directly: vintage-based loss tracking is the standard lens lenders and investors use to judge portfolio quality, and showing it by dollar volume (not just count) is the detail that signals real familiarity with how credit portfolios get evaluated.
