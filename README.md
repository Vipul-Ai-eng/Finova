# Finova - Finance Analytics Dashboard

I built Finova to solve a pretty common problem in finance teams: the data exists, but it's scattered across raw transaction logs and customer records, and nobody wants to open a spreadsheet every time they need to answer "how are we doing this month?" This is a Power BI dashboard that pulls transaction, fee, tax, and customer data into one place so that question has a one-click answer.

## Why this exists

The brief (from the business requirements this was built against) was straightforward on paper: give management real-time visibility into transactions, customer behavior, fees, taxes, and performance across segments and regions. In practice that meant figuring out which five numbers actually matter enough to be KPIs, which breakdowns tell a story versus which are just noise, and how to let someone filter by year, occupation, or category without the report falling over.

## What's inside

**Overview Analysis** — the main landing page. Five KPI cards up top (Total Amount, Total Transactions, Avg Transaction Value, Total Fees, Total Tax — each with a YoY delta so you're not staring at a number with no context), and six visuals underneath that answer the "why" behind those numbers:

- **Total Amount by Month** — line/area chart, mainly for spotting seasonal spikes or slow months
- **Total Amount by Transaction Status** — donut chart of Success / Failed / Pending, basically a quick read on operational health
- **Total Amount by Customer Segment** — horizontal bar across Retail, Premium, SME, Corporate, Wealth
- **Total Amount by State** — horizontal bar, top vs. bottom performing regions
- **Transaction Type Analysis** — a matrix table (amount, fees, tax, count) across all 10 transaction types — Bill Payment, Card Payment, Deposit, Fee Charge, Interest Credit, Investment, Loan EMI, Refund, Transfer, Withdrawal
- **Total Amount by Gender** — donut chart, Male vs. Female contribution
- <img width="1121" height="592" alt="image" src="https://github.com/user-attachments/assets/4be81c8b-e2bf-496a-bd09-357acd4468fc" />


**Transactions** — the second page, a full drill-down grid: transaction ID, date, customer, type, status, gender, segment, amount, fees, tax. This is where you go when a KPI card raises a question and you need the actual rows behind it.

Everything filters by **Year**, **Dynamic Measure**, **Occupation**, and **Category** from the left panel, so the same six visuals can answer very different questions depending on what you're slicing by.
<img width="1121" height="586" alt="image" src="https://github.com/user-attachments/assets/3f8ad076-5fb2-4cdc-8b41-77398fcfb28e" />


## Repo layout

```
Finova/
├── Finova.pbix               
├── finance_transactions.csv  
├── customers.csv             
└── Images Used/              
```

The data model is intentionally simple - two tables, joined on customer ID inside Power BI. `finance_transactions.csv` has the transaction-level facts (type, status, amount, fees, tax), and `customers.csv` has who the customer actually is (gender, segment, occupation, state). That join is what lets the segment/state/gender breakdowns work without duplicating customer info into every transaction row.

## Running it yourself

```bash
git clone https://github.com/Vipul-Ai-eng/Finova.git
```

Open `Finova.pbix` in Power BI Desktop. If it complains about the data source paths (it will, since it was pointing at my local folder), just repoint `finance_transactions.csv` and `customers.csv` to wherever you cloned the repo, hit refresh, and you're good. From there, play with the filters on the left — that's really the point of the report, not just staring at the default view.

## Built with

Power BI Desktop for everything — data modeling, DAX measures, and the visuals themselves — on top of two CSV files as the source data.

## License

Not licensed yet — I'll add one (probably MIT) if this ends up being useful to anyone beyond this project.
