## PHASE 6 — SEGMENT RISK ANALYSIS

### Segment Used: Country
The original workflow used Category as the segment. This dataset does not have a Category column — Description was considered but has 4,070 unique values, too granular for segment analysis. Country was used instead as it has 33 unique values and directly supports concentration risk analysis.

---

### Analysis Structure
1. **Revenue by Country** — SUM of Revenue grouped by Country
2. **Customer Count by Country** — SUM of Customer_Count grouped by Country
3. **Revenue Contribution %** — Country Revenue / Total Revenue
4. **Customer Contribution %** — Country Customers / Total Customers
5. **Risk_Flag** — High (≥50%), Medium (10–49%), Low (<10%)

---

### PivotTables Built
- **PT_Revenue_By_Country** — Revenue by Country, sorted descending
- **PT_Customer_By_Country** — Customer Count by Country, sorted descending

---

### Risk Flag Formula
```
=IFS([@[Revenue_Contribution_Pct]]>=0.5,"High",[@[Revenue_Contribution_Pct]]>=0.1,"Medium",[@[Revenue_Contribution_Pct]]<0.1,"Low")
```

---

### Key Finding
- **United Kingdom = 84.42% of revenue and 90.52% of customers** — flagged as High risk
- No country falls in the Medium range — concentration jumps from 84.42% (UK) directly to 2.52% (EIRE)
- This indicates extreme single-market dependency with no meaningful secondary markets

---

### Check
Are we overly dependent on 1–2 markets?  
**Yes — overwhelmingly dependent on the United Kingdom.**  
This ties directly to concentration risk and will be expanded in Phase 8 — Insight Writing.

---

### Additional Table — tbl_Top5_Countries
Created during Phase 7 Dashboard build to improve chart readability. The original 33-country chart compressed non-UK bars to near-invisible sizes. A summary table was created in the Segment_Risk sheet grouping data into Top 5 countries by revenue plus an "All Others" row:

| Country | Revenue | Revenue_Contribution_Pct |
|---|---|---|
| United Kingdom | 3,263,199.25 | 84.42% |
| EIRE | 97,282.79 | 2.52% |
| Germany | 93,933.59 | 2.43% |
| Netherlands | 89,850.96 | 2.32% |
| France | 85,054.61 | 2.20% |
| All Others | 236,141.88 | 6.11% |

Table named tbl_Top5_Countries. Used as data source for the Revenue by Country chart in the Dashboard. All Others calculated as Total Revenue minus Top 5 sum.

