# Customer Churn Analysis — Telco Customer Base

**26.5% churn rate, driven primarily by contract type and early-tenure risk.**

A full churn analysis on a 7,043-customer telecom dataset — from EDA through a custom risk-scoring model, customer-value segmentation, and an ROI-backed retention strategy.

**Tools:** Python (Pandas, NumPy, Seaborn) · Power BI
**Dataset:** [`WA_Fn-UseC_-Telco-Customer-Churn.csv`](https://www.kaggle.com/datasets/blastchar/telco-customer-churn) — 7,043 customers, 21 fields

📄 [Full PDF Report](./report/Customer_Churn_Analysis_Report.pdf) · 📓 [Notebook](./notebooks/customer_churn_analysis.ipynb) · 📊 [Power BI Dashboard](./dashboard/customer_churn_analysis.pbix)

---

## Executive Summary

Four factors stand out as the clearest churn drivers:

- **Contract type** — month-to-month customers churn at **42.7%**, vs. 11.3% (one-year) and 2.8% (two-year)
- **Tenure** — customers in their first 6 months churn at **53.3%**, falling to 9.5% past 48 months
- **Missing add-ons** — customers without Tech Support or Online Security churn at ~3x the rate of those with it
- **Payment method & internet type** — Electronic check payers (45.3%) and Fiber optic users (41.9%) churn well above other segments

These drivers feed into a composite **Risk Score** and a **Customer Value** metric, combined into a 2x2 segmentation. The top-priority group — **High Risk / High Value** (868 customers, ₹28.6L in value, 44.9% churn) — is projected to lose ~390 customers without intervention. A targeted 10% retention discount to this segment returns an estimated **1.35x** on cost even under conservative assumptions.

## Risk Scoring Model

| Factor | Weight |
|---|---|
| Month-to-month contract | +3 |
| Tenure under 6 months | +3 |
| Electronic check payment | +2 |
| No Tech Support | +2 |
| No Online Security | +2 |
| Fiber optic internet | +1 |

| Risk Tier | Score Range | Churn Rate |
|---|---|---|
| Low | 0–3 | 5.0% |
| Medium | 4–7 | 21.2% |
| High | 8–13 | 55.3% |

## Customer Value Segmentation (Risk × Value)

| Risk Tier | Value Tier | Customers | Avg. Value (₹) | Churn Rate |
|---|---|---|---|---|
| Low | High Value | 1,696 | 4,476 | 6.0% |
| Low | Low Value | 1,145 | 672 | 3.5% |
| Medium | High Value | 957 | 4,000 | 17.8% |
| Medium | Low Value | 793 | 507 | 25.3% |
| **High** | **High Value** | **868** | **3,292** | **44.9%** |
| High | Low Value | 1,584 | 384 | 61.0% |

## Retention Strategy by Segment

- **High Risk / High Value (top priority):** proactive personal outreach + targeted discount or free Tech Support add-on
- **High Risk / Low Value:** low-cost automated tactics only (email nudge, push to auto-pay)
- **Medium Risk / High Value:** annual-contract upgrade incentive
- **Medium Risk / Low Value:** automated check-in emails
- **Low Risk / High Value:** loyalty perks, not discounts
- **Low Risk / Low Value:** deprioritize

## Repo Structure

```
customer-churn-analysis/
├── notebooks/customer_churn_analysis.ipynb   # full EDA + risk model in Python
├── dashboard/
│   ├── customer_churn_analysis.pbix          # Power BI interactive dashboard
│   └── customer_churn_analysis.png           # dashboard preview image
├── report/Customer_Churn_Analysis_Report.pdf # formatted write-up
└── data/                                     # source dataset
```

## How to Reproduce

```bash
git clone https://github.com/divyainsights99/customer-churn-analysis.git
cd customer-churn-analysis
pip install -r requirements.txt
jupyter notebook notebooks/customer_churn_analysis.ipynb
```

To explore the dashboard interactively, open `dashboard/customer_churn_analysis.pbix` in [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free).

---
*Prepared by Divya Gupta — July 2026*
