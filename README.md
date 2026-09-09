# Finova - Finance Analytics Dashboard

A Power BI dashboard that brings transactions, fees, tax, and customer data into one view - built so anyone can check "how are we doing?" without digging through raw CSVs.

## What it does

**Overview Analysis** — five KPI cards (Total Amount, Total Transactions, Avg Transaction Value, Total Fees, Total Tax), each with YoY change, plus six visuals:
- Total Amount by Month — trend line, spot seasonal spikes
- Total Amount by Transaction Status — Success / Failed / Pending
- Total Amount by Customer Segment — Retail, Premium, SME, Corporate, Wealth
- Total Amount by State — top vs. bottom regions
- Transaction Type Analysis — amount, fees, tax, count across 10 types
- Total Amount by Gender — Male vs. Female split
- - <img width="1121" height="592" alt="image" src="https://github.com/user-attachments/assets/4be81c8b-e2bf-496a-bd09-357acd4468fc" />

**Transactions** — full drill-down grid: transaction ID, date, customer, type, status, gender, segment, amount, fees, tax.
<img width="1121" height="586" alt="image" src="https://github.com/user-attachments/assets/3f8ad076-5fb2-4cdc-8b41-77398fcfb28e" />

Filters: **Year, Dynamic Measure, Occupation, Category.**

## Repo layout

```
Finova/
├── Finova.pbix               # Power BI report
├── finance_transactions.csv  # transaction-level data
├── customers.csv             # customer master data
└── Images Used/              # images referenced in the report
```

Two tables, joined on customer ID — transactions carry the facts (type, status, amount, fees, tax), customers carry the who (gender, segment, occupation, state).

## Run it

```bash
git clone https://github.com/Vipul-Ai-eng/Finova.git
```

Open `Finova.pbix` in Power BI Desktop, repoint the two CSVs to your local clone if it asks, refresh, done.

## Built with

Power BI Desktop + CSV source data.
