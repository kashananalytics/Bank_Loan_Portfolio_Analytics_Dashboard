# Bank_Loan_Portfolio_Analytics_Dashboard
473M received. 435M funded. 13.82% bad loan rate. A full bank loan portfolio analytics dashboard built in Power BI with risk breakdown, monthly trends and state-level mapping.

# 🏦 Bank Loan Portfolio Analytics Dashboard — Power BI

> Built to give a complete picture of a bank's loan portfolio — who is borrowing, how much is being funded, where the risk sits, and how applications are trending over time.

---

## 📸 Dashboard Preview

Dashboard Page
<br>
![Dashboard Preview](dashboard.png)

Overview Page
<br>
![Dashboard Preview](dashboard.png)

---

## 📌 Project Summary

This is a two-page Power BI project built on a real-world bank loan dataset covering **38,576 loan applications** worth **473.1M in total amount received** and **435.8M in total funded amount**.

The dashboard is split into two pages that work together:
- **Dashboard page** — focuses on good vs bad loan breakdown, loan status performance, and key risk metrics
- **Overview page** — focuses on trends, geography, loan purpose, home ownership, and term distribution

---

## 🔢 KPI Cards (Both Pages)

| KPI | Value |
|---|---|
| 📋 Total Applications | 38,576 |
| 💰 Total Amount Received | 473.1M |
| 🏦 Total Funded Amount | 435.8M |
| 📈 Avg Interest Rate | 12.05% |
| 📊 Avg DTI Ratio | 13.33% |

---

## 🎛️ Filters & Slicers

| Filter | Options |
|---|---|
| Loan Purpose | Car · Credit Card · Debt Consolidation · Educational · Home Improvement · House · Major Purchase · Medical · Moving · Other · Renewable Energy · Small Business |
| Grade Filter | A · B · C · D · E · F · G |

---

## 📊 Page 1 — Dashboard Visuals

**1. Good Application Panel**
Shows the healthy side of the portfolio at a glance.

| Metric | Value |
|---|---|
| Good Loan % | 86.18% |
| Total Applications | 33,243 |
| Total Funded Amount | 370.2M |
| Total Amount Received | 435.8M |

---

**2. Bad Application Panel**
Shows the risk exposure clearly in red.

| Metric | Value |
|---|---|
| Bad Loan % | 13.82% |
| Total Applications | 38,576 |
| Total Funded Amount | 435.8M |
| Total Amount Received | 473.1M |

---

**3. Grouped Bar Chart — Funded Amount and Total Application by Loan Status**

| Loan Status | Funded Amount | Total Amount |
|---|---|---|
| Fully Paid | 351.4M | 411.6M |
| Charged Off | 65.5M | 37.3M |
| Current | 18.9M | 24.2M |

---

**4. Loan Application Count by Status**

| Loan Status | Applications |
|---|---|
| Fully Paid | 0.71M |
| Charged Off | 0.12M |
| Current | 0.03M |

---

**5. Average Interest Rate by Loan Status**

| Loan Status | Avg Interest Rate |
|---|---|
| Current | 15.10% |
| Charged Off | 13.88% |
| Fully Paid | 11.64% |

---

**6. Average DTI Ratio by Loan Status**

| Loan Status | Avg DTI |
|---|---|
| Fully Paid | 4.2K |
| Charged Off | 0.7K |
| Current | 0.2K |

---

## 📊 Page 2 — Overview Visuals

**7. Monthly Funding Trend — Line Chart**
Tracks loan application volume month by month across the full year.

| Month | Applications |
|---|---|
| January | 2.3K |
| February | 2.3K |
| March | 2.6K |
| April | 2.8K |
| May | 2.9K |
| June | 3.2K |
| July | 3.4K |
| August | 3.4K |
| September | 3.5K |
| October | 3.8K |
| November | 4.0K |
| December | 4.3K |

Applications nearly doubled from January to December — a clear upward growth trend.

---

**8. Loan Applications by State — Bing Map**
Geographic view of loan distribution across US states. Clusters visible across Illinois, Indiana, Ohio, Pennsylvania, Virginia and North Carolina.

---

**9. Loan Application by Term — Donut Chart**

| Term | Applications | Share |
|---|---|---|
| 60 Months | 28,237 | 73.2% |
| 36 Months | 10,339 | 26.8% |

Most borrowers prefer longer repayment terms.

---

**10. Loan Applications by Home Ownership — Bar Chart**

| Ownership Type | Applications |
|---|---|
| Mortgage | 17,198 |
| Rent | (2nd highest) |
| Own | 2,838 |
| Other | 98 |
| None | 3 |

---

**11. Loan Applications by Purpose — Treemap**

| Purpose | Applications |
|---|---|
| Debt Consolidation | 18K (largest) |
| Credit Card | 5K |
| Other | 4K |
| Home Improvement | 3K |
| Small Business | 2K |
| Major Purchase | 2K |
| Car | 1K |

Debt Consolidation dominates — nearly 3x the next biggest category.

---

## 🧮 DAX Measures

```dax
-- Total Applications
Total Applications = COUNTROWS('Loan Data')

-- Total Funded Amount
Total Funded Amount = SUM('Loan Data'[funded_amnt])

-- Total Amount Received
Total Amount Received = SUM('Loan Data'[total_pymnt])

-- Good Loan Percentage
Good Loan % =
  DIVIDE(
    CALCULATE(COUNTROWS('Loan Data'), 'Loan Data'[loan_status] IN {"Fully Paid", "Current"}),
    [Total Applications]
  )

-- Bad Loan Percentage
Bad Loan % =
  DIVIDE(
    CALCULATE(COUNTROWS('Loan Data'), 'Loan Data'[loan_status] = "Charged Off"),
    [Total Applications]
  )

-- Average Interest Rate
Avg Interest Rate = AVERAGE('Loan Data'[int_rate])

-- Average DTI Ratio
Avg DTI Ratio = AVERAGE('Loan Data'[dti])
```

---

## 💡 Key Insights

- 🟢 **86.18% good loan rate** — the portfolio is mostly healthy but the 13.82% bad loan chunk is worth watching
- 📈 **Applications grew from 2.3K to 4.3K** between January and December — nearly doubled in one year
- 💳 **Debt Consolidation is the #1 loan purpose** at 18K — people are using loans to manage existing debt
- 🏠 **Mortgage holders borrow the most** — 17,198 applications, far ahead of renters and owners
- ⏱️ **73.2% choose 60-month terms** — borrowers prefer lower monthly payments over faster payoff
- ⚠️ **Current loans have the highest interest rate at 15.10%** — higher than both Fully Paid and Charged Off
- 🗺️ **Loan concentration is heavy in the Northeast and Midwest US states**

---

## 🛠️ Tools Used

- **Microsoft Excel** — raw data source
- **Power Query** — data cleaning and transformation
- **Power BI Desktop** — dashboard design across two pages
- **DAX** — all KPI and ratio calculations
- **Bing Maps** — geographic state-level loan distribution

---

## 🚀 How to Use

1. Download the `.pbix` file
2. Open in Power BI Desktop
3. Use the **loan purpose slicer** on the left to filter by category
4. Use the **A to G grade tabs** at the top to filter by loan grade
5. Switch between **Dashboard** and **Overview** pages using the top right buttons
6. Click any chart segment to cross-filter all other visuals

---

*Feel free to fork this or use the DAX measures for your own banking, finance or risk analytics projects.*
