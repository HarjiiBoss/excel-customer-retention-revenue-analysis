## PHASE 4 — RETENTION CALCULATION LOGIC

---

### Overview
Phase 4 builds on the PivotTables created in Phase 3. A dedicated `Retention_Calc` sheet was created to house all retention calculations.

---

### Sheet Structure
Created a table in `Retention_Calc` with the following columns:

| Column | Description |
|---|---|
| Month | YearMonth |
| Active_Customers | Referenced from PT_Active_Customers |
| New_Customers | Referenced from PT_New_vs_Returning |
| Returning_Customers | Referenced from PT_New_vs_Returning |
| Retention_Rate | Returning Customers (Month n) / Active Customers (Month n-1) |
| Churn_Rate | 1 − Retention_Rate |

---

### Retention Rate Formula
```
Retention Rate (Month n) = Returning Customers (Month n) / Active Customers (Month n-1)
```
> First month row is left blank — no previous month exists for comparison.  
> This introduces time-based dependency logic into the analysis.

---

### Churn Rate Formula
```
Churn Rate = 1 − Retention Rate
```

---

### Average Retention Rate (Excluding Anomaly)
```
=AVERAGEIF(tbl_Retention[Retention_Rate],"<1")
```
Returns **21.27%** — excludes the 2011-01 anomaly (186.29%) by filtering out any value ≥ 1 (≥ 100%), which is mathematically impossible for a true retention rate.

---

### Notable Anomaly
2011-01 shows a Retention Rate of **186.29%** due to a massive customer jump from 19 (2010-12) to 221 (2011-01). This is not a real retention rate — it reflects a sudden surge in new customers rather than returning customer behaviour. Flagged for investigation in Phase 8 — Insight Writing.

---

### Goal
Retention and Churn Rate calculated for every month in the dataset.  
Average Retention Rate confirmed at **21.27%** (anomaly excluded).  
Results feed directly into the Dashboard and Insight Writing phases.

