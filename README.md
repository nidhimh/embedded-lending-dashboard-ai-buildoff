# Embedded Lending Portfolio Dashboard — Built 3x with AI (Claude, Microsoft Copilot, Gemini)

A mock, fully synthetic analytics build for a fintech that provides **embedded merchant cash advances (MCA)** to small businesses through platform partners like **DoorDash, Amazon, Worldpay, and Mindbody**.

I built the same project — same relational dataset, same auditable Excel dashboard, same stakeholder narratives — **three separate times, once per AI stack**: Claude, Microsoft Copilot, and Gemini. The goal wasn't to pick a "winner." It was to demonstrate that I can pick up any AI tool a team already uses and get to a production-quality, audit-ready deliverable fast — the core skill behind transitioning smoothly into AI-augmented analyst work.

## Why this project exists

I'm a Business Analyst showing recruiters and hiring managers two things at once:

1. **I can model and analyze a real fintech lending business** — origination volumes, revenue run-rate, portfolio delinquency, reconciliation logic — the way a Finance Data Lead would.
2. **I can do it with AI as a genuine accelerant**, not just a novelty — building the same rigorous, checkable output regardless of which AI tool is in front of me.

## The business scenario

A fintech extends embedded merchant cash advances to small businesses operating on partner platforms (DoorDash, Amazon, Worldpay, Mindbody). The dataset and dashboard model:

- **Origination volumes** — advance amounts issued, by partner and cohort
- **Revenue run-rate** — recognized revenue over time
- **Portfolio delinquency** — cohort-level delinquency tracking
- **Reconciliation & audit trails** — every metric on the dashboard ties back to source data through live formulas, not hardcoded numbers

## Highlights


- 🔗 **[Dashboard walkthrough](https://1drv.ms/x/c/a42c27f41a72e65b/IQQyijd58b9IT7JjyxVjdHnrAU13JeBfBvYbV84gukTbiUc?em=2&wdAllowInteractivity=False&wdHideGridlines=True&wdHideHeaders=True&wdDownloadButton=True&wdInConfigurator=True&wdInConfigurator=True)
** — the finished Excel dashboard in action
- 🔗 **[Catching a data gap](#)** — how I found and resolved a reconciliation issue mid-build
- 🔗 **[Generated stakeholder summary](#)** — one of the AI-generated briefs, translating the dataset into a narrative

*(Replace the `#` links above with your actual links.)*

## Repo structure

Each AI stack has an identical folder structure, so you can compare the same deliverable across tools directly.

```
├── claude/
│   ├── source-data/          # Synthetic CSVs (Partners, Originations, Repayments, Revenue Recognized)
│   ├── dashboard/             # Excel dashboard: Metrics, Reconciliation, Cohort Delinquency
│   ├── data-dictionary/       # Field-level definitions for every table and metric
│   └── stakeholder-briefs/    # Finance, Product, GTM, Engineering, and Investor/Board summaries
│
├── microsoft-copilot/
│   ├── source-data/
│   ├── dashboard/
│   ├── data-dictionary/
│   └── stakeholder-briefs/
│
└── gemini/
    ├── source-data/
    ├── dashboard/
    ├── data-dictionary/
    └── stakeholder-briefs/
```

**What's in each folder:**

| Folder | Contents |
|---|---|
| `source-data/` | Synthetic relational dataset (CSV) modeling partners, originations, repayments, and recognized revenue — generated with that stack's AI tool |
| `dashboard/` | An auditable Excel dashboard built on live formulas — origination volumes, revenue run-rate, and delinquency, with reconciliation logic and audit trails baked in |
| `data-dictionary/` | Definitions for every table, field, and metric, so the dashboard is legible to someone who didn't build it |
| `stakeholder-briefs/` | Plain-language summaries of the same dataset written for five different audiences: Finance, Product, GTM, Engineering, and Investor/Board |

## What this demonstrates

- **Data modeling** — designing a relational schema that reflects how an embedded lending business actually works (partners → originations → repayments → recognized revenue)
- **Financial/portfolio analysis** — origination volume, revenue run-rate, and delinquency metrics, the core KPIs a lending Finance team tracks
- **Auditability** — every number in the dashboard is traceable to source data through live formulas and reconciliation logic, not static outputs
- **Stakeholder communication** — translating the same underlying dataset into five distinct narratives, tuned to what Finance, Product, GTM, Engineering, and the Board each actually need to know
- **Tool-agnostic AI fluency** — reproducing the same rigorous deliverable across Claude, Microsoft Copilot, and Gemini, showing the workflow (not the tool) is the transferable skill

## Note on the data

All data in this project is **synthetic and fictional**, generated for demonstration purposes. It does not represent any real company, partner, or portfolio.

## About me

Business Analyst with an AI-augmented workflow, exploring how AI tools can accelerate the kind of financial/data analysis work that used to take days into something built in hours — without sacrificing rigor or auditability.

[LinkedIn](#) · [Portfolio](#) · [Email](#)
