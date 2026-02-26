## PHASE 5 — REVENUE STABILITY ANALYSIS

### Sheet: Revenue_Stability (table: tbl_Revenue_Stability)

---

### What Was Built

#### 1. Monthly Revenue Trend Line
Referenced from PT_Monthly_Revenue. Built as a line chart in Phase 7 — Dashboard.

---

#### 2. Revenue Growth %
```
(Current Month Revenue − Previous Month Revenue) / Previous Month Revenue
```
Column: `Revenue_Growth_Pct` — formatted as Percentage (2 decimal places).  
First month left blank — no previous month for comparison.

---

#### 3. Revenue Volatility
```
Standard Deviation of Monthly Revenue
```
Calculated using:
```
=STDEV(tbl_Revenue_Stability[Monthly_Revenue])
```

Summary section added below the table:

| Metric | Value |
|---|---|
| Mean Monthly Revenue (Overall) | 175,702.87 |
| Mean Monthly Revenue (2010) | 36,124.71 |
| Mean Monthly Revenue (2011) | 292,017.99 |
| Revenue Volatility (Std Dev) | 138,095.97 |
| Coefficient of Variation (CV) | 78.60% |

2010 and 2011 averages calculated using:
```
=AVERAGEIF(tbl_Revenue_Stability[Month],"2010*",tbl_Revenue_Stability[Monthly_Revenue])
=AVERAGEIF(tbl_Revenue_Stability[Month],"2011*",tbl_Revenue_Stability[Monthly_Revenue])
```

> CV of 78.60% indicates extremely high revenue volatility — monthly revenue swings wildly around the mean.  
> 2011 average monthly revenue (£292,017.99) was approximately 8x higher than 2010 (£36,124.71) — significant growth but highly unstable.

---

#### 4. Revenue per Returning vs New Customers
Two columns added:
- `Rev_Per_New_Customer` = Monthly_Revenue / New_Customers
- `Rev_Per_Returning_Customer` = Monthly_Revenue / Returning_Customers

New_Customers and Returning_Customers referenced from tbl_Retention using:
```
=ROUND(IFERROR(XLOOKUP([@Month],tbl_Retention[Month],tbl_Retention[New_Customers]),"N/A"),0)
```
Months with zero Returning_Customers return N/A to avoid division errors.

---

### This Answers:
**Is growth sustainable or acquisition-driven?**  
Revenue per New Customer consistently higher in early months — growth was largely acquisition-driven in 2010.  
Returning Customer revenue per head grew steadily through 2011 — suggesting improving retention value over time.

### Note
`Rev_Per_New_Customer` and `Rev_Per_Returning_Customer` divide total monthly revenue by customer count.  
This does not isolate revenue by customer type at transaction level and should be interpreted with caution.

