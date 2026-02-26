# Customer Retention & Revenue Stability Analysis

![Dashboard](dashboard/dashboard_full_view.png)

---

## Executive Summary

This project analyses customer retention patterns and revenue stability for a UK-based e-commerce retailer using transactional data from 2010 to 2011. The cleaned dataset comprises 166,381 transactions across 2,997 unique customers spanning 33 countries. While revenue increased approximately 8x year-over-year, growth was primarily acquisition-driven and accompanied by substantial volatility. Key structural risks identified include a 78.60% coefficient of variation in monthly revenue and an 84.42% revenue concentration in the United Kingdom, indicating limited geographic diversification.

---

## Performance Snapshot

| Metric | Value |
|---|---|
| Total Revenue | £3,865,463.08 |
| Total Customers | 2,997 |
| Total Transactions | 166,381 |
| Avg Monthly Revenue | £175,702.87 |
| Avg Retention Rate | 21.27% |
| Revenue Volatility (Coefficient of Variation) | 78.60% |
| UK Revenue Share | 84.42% |
| Analysis Period | Jan 2010 — Dec 2011 (22 active months) |

> The business experienced rapid growth but exhibited high volatility, low retention, and significant geographic concentration risk.

---

## Objective

To analyse customer retention dynamics, revenue stability, and geographic concentration exposure for a UK-based e-commerce retailer over a 22-month period. The objective is to assess whether observed growth was structurally sustainable or primarily acquisition-driven, identify key operational and market risks, and translate findings into data-backed strategic recommendations using a structured Excel-based analytical workflow.

---

## Business Context

E-commerce businesses heavily concentrated in a single dominant market face elevated structural risk, particularly when revenue growth is driven primarily by new customer acquisition rather than repeat purchasing. For a retailer generating £3.86M across 166,381 transactions, assessing revenue stability and customer concentration is essential for sustainable scaling. This analysis equips business owners, commercial leaders, and investors with quantitative insight to inform retention strategy, geographic diversification, and revenue forecasting decisions.

---

## Business Questions

This analysis was structured around five core business questions:

1. Is observed revenue growth structurally sustainable, or primarily driven by continuous new customer acquisition?
2. How stable is monthly revenue performance, and what does observed volatility imply for forecasting reliability?
3. Is the customer base demonstrating strengthening loyalty, or does churn remain the dominant behavioural pattern?
4. How concentrated is revenue across geographic markets, and what systemic exposure does this create?
5. Are there data anomalies or outliers that materially distort retention or revenue metrics?

---

## Analysis Approach

The analysis was conducted entirely in Microsoft Excel using a structured 10-phase workflow. Raw transactional data was imported and transformed via Power Query, followed by systematic cleaning to remove duplicates, null values, returns, and date inconsistencies.

Ten core KPIs were defined across three analytical pillars: Customer, Revenue, and Risk. Metrics were computed using PivotTables, structured table formulas, and helper columns to ensure traceability and reproducibility.

Retention was calculated using a month-over-month methodology based on active customer counts. Revenue stability was evaluated through growth rate tracking, standard deviation, and coefficient of variation analysis. Geographic concentration exposure was quantified by segmenting revenue and customer distribution by country and applying a structured risk classification.

All results were consolidated into an executive dashboard and synthesised into five structured business insights addressing growth sustainability, retention dynamics, customer composition, market concentration, and anomaly detection.

---

## Key Findings

1. Revenue grew approximately 8x year-over-year — from an average of £36K per month in 2010 to £292K in 2011 — but a coefficient of variation of 78.60% confirms the growth was highly unstable, with monthly revenue fluctuating between £17K and £421K.

2. Average retention rate of 21.27% (excluding the January 2011 anomaly) indicates growth was largely acquisition-driven. The implied churn rate of approximately 78.73% suggests most customers did not return after their initial purchase.

3. Returning customers grew 40–50x — from 1–3 per month in early 2010 to 88–108 per month by late 2011 — representing approximately 45% of active customers by November 2011, indicating early signs of loyalty development.

4. 84.42% of total revenue and 90.52% of customers are concentrated in the United Kingdom. The second-largest market, EIRE, contributes only 2.52%, confirming extreme single-market dependency with no meaningful secondary market presence.

5. January 2011 recorded an anomalous retention rate of 186.29% — a mathematical impossibility driven by a sudden customer surge from 19 to 221 active customers. This outlier was excluded from all retention calculations to preserve analytical accuracy.

---

## Business Implications

1. High revenue volatility limits forecasting reliability and complicates cash flow planning, inventory management, and staffing allocation. Historical monthly performance alone cannot support predictable operational decision-making.

2. An acquisition-driven growth model is financially demanding. Replacing churned customers through continuous acquisition increases marketing expenditure without compounding lifetime value from a loyal customer base.

3. The rapid increase in returning customers during 2011 indicates emerging product-market resonance. However, without deliberate retention investment, this momentum may not translate into sustainable long-term revenue stability.

4. Heavy dependence on the UK market introduces systemic exposure. Adverse regulatory, economic, or competitive shifts within the UK could materially impact overall performance, given the absence of meaningful geographic diversification.

5. The January 2011 anomaly underscores the importance of robust data validation processes. Undetected metric distortions could result in flawed strategic decisions, particularly in areas such as retention budgeting and loyalty programme investment.

---

## Recommendations

1. **Prioritise retention infrastructure investment.**  
Implement structured post-purchase follow-ups, loyalty programmes, and personalised re-engagement campaigns to convert first-time buyers into repeat customers. Strengthening retention reduces reliance on continuous acquisition and improves revenue predictability.

2. **Validate seasonality patterns.**  
Investigate the September 2011 £421K revenue peak to determine whether it reflects recurring seasonality, promotional activity, or one-off external factors. If repeatable patterns are confirmed, align inventory planning and marketing allocation accordingly.

3. **Consolidate retention momentum.**  
Returning customers accounted for approximately 45% of active customers by November 2011. This upward trajectory should be reinforced through deliberate loyalty investment before growth normalises or reverses.

4. **Gradually diversify geographic exposure.**  
Increase strategic focus on existing secondary markets such as Germany, the Netherlands, and France, which collectively contribute approximately 7% of revenue. Controlled expansion within known markets offers a lower-risk pathway toward diversification.

5. **Strengthen reporting governance.**  
Implement automated anomaly detection and validation checks within reporting workflows to prevent metric distortion, ensuring that strategic decisions are based on reliable data.

---

## Strategic Outlook

The business enters 2012 with strong headline growth but notable structural vulnerabilities. Revenue volatility, acquisition dependency, and geographic concentration create compounded exposure that may constrain long-term scalability if left unaddressed.

The improving retention trajectory observed throughout 2011 is a positive signal, but early loyalty momentum remains fragile. The opportunity to transition from acquisition-led expansion to a retention-driven revenue model is present, yet requires deliberate and sustained investment in customer experience, post-purchase engagement, and retention analytics.

Geographic diversification represents a medium-term strategic priority. Heavy reliance on the UK market exposes the business to single-market shocks without a meaningful revenue buffer. Incremental expansion within established secondary markets provides a structured path toward greater resilience.

From a data governance perspective, the January 2011 anomaly underscores the importance of scalable reporting infrastructure. As retention and revenue metrics become central to strategic planning, decision-making must be supported by validated and systematically monitored data processes.

---

## Process

| Phase | What Was Done |
|---|---|
| Phase 1 — Data Import | Imported CSV via Power Query. Deleted auto-generated Changed Type step and manually set data types — InvoiceNo, StockCode, Description, CustomerID and Country as Text, Quantity as Whole Number, InvoiceDate as Date/Time, UnitPrice as Decimal Number. Renamed columns for consistency — InvoiceNo to Invoice_No, StockCode to Stock_Code, UnitPrice to Unit_Price, InvoiceDate to Invoice_Date, CustomerID to Customer_ID. Added Year, Month and YearMonth calculated columns from Invoice_Date. Added Revenue column as Quantity × Unit_Price. Closed and loaded into Excel as a table named Raw_Data. |
| Phase 2 — Data Cleaning | Copied Raw_Data to Cleaned_Data sheet (table: tbl_Cleaned). Removed 5,269 duplicate rows. Confirmed Invoice_Date as true Date/Time format (Custom). Validated Revenue using =ROUND([@[Quantity]]*[@[Unit_Price]],2)=[@[Revenue]] — FALSE rows identified as return/cancellation entries and floating point rounding differences (0.001), not real errors. Checked missing values using COUNTBLANK(tbl_Cleaned[ColumnName]) — found 135,037 blank Customer_IDs and 305,984 blank Invoice_Dates, all deleted. Removed 4,111 negative Quantity rows (returns/cancellations) using =IF([@[Quantity]]<0,"Return","Sale"). Added First_Purchase_Date using TEXT(MINIFS()) with INT() to strip Date/Time component, converted to true date via DATEVALUE, pasted as values only. Added Customer_Type using =IF(INT([@[Invoice_Date]])=[@[First_Purchase_Date]],"New","Returning"). Final clean dataset: 166,381 rows. |
| Phase 3 — KPI Design | Defined 10 core KPIs across three pillars — Customer, Revenue and Risk. Built three PivotTables in a dedicated Pivot_Tables sheet: (1) PT_Active_Customers — Active Customers per Month using Customer_Count SUM, formatted as whole numbers, Grand Total renamed to Unique Customers; (2) PT_New_vs_Returning — New vs Returning Customers per Month with Customer_Type as column, Grand Total row and column removed; (3) PT_Monthly_Revenue — Monthly Revenue SUM, Revenue column formatted as £ currency, Grand Total renamed to Total Revenue (£). All Row Labels renamed to Month. Distinct Count unavailable on Mac Excel — resolved using a Customer_Count helper column (1/COUNTIF) in tbl_Cleaned. Total unique customers: 2,997. Total Revenue: £3,865,463.08. |
| Phase 4 — Retention Calculation | Created Retention_Calc sheet and built a structured table referencing data directly from PT_Active_Customers and PT_New_vs_Returning PivotTables. Links kept live so sheet auto-updates on PivotTable refresh. Columns: Month, Active_Customers, New_Customers, Returning_Customers, Retention_Rate (Returning Month n / Active Month n-1), Churn_Rate (1 − Retention_Rate). First month left blank — no previous month for comparison. Converted to table named tbl_Retention. Retention_Rate and Churn_Rate formatted as Percentage (2 decimal places). Average Retention Rate calculated using AVERAGEIF(tbl_Retention[Retention_Rate],"<1") = 21.27% — excludes 2011-01 anomaly (186.29%) which resulted from customer jump from 19 (2010-12) to 221 (2011-01). Anomaly flagged for Phase 8. |
| Phase 5 — Revenue Stability | Created Revenue_Stability sheet with table tbl_Revenue_Stability. Columns: Month, Monthly_Revenue (referenced from PT_Monthly_Revenue), Prev_Monthly_Revenue, Revenue_Growth_Pct calculated as (Current − Previous) / Previous formatted as percentage, Cumulative_Revenue as running total using SUM($B$2:B2). Added New_Customers and Returning_Customers columns using ROUND(IFERROR(XLOOKUP())) from tbl_Retention. Added Rev_Per_New_Customer and Rev_Per_Returning_Customer using Monthly_Revenue divided by respective customer counts — N/A returned for months with zero returning customers. Added summary section below table: Mean Monthly Revenue = 175,702.87, Revenue Volatility (Std Dev) = 138,095.97, Coefficient of Variation (CV) = 78.60% — indicating extremely high revenue volatility. Summary cells styled using 20% Accent cell styles. Added AVERAGEIF calculations for 2010 and 2011 average monthly revenue — 2010: £36,124.71, 2011: £292,017.99. Confirmed 2011 average was approximately 8x higher than 2010. |
| Phase 6 — Segment Risk Analysis | Created Segment_Risk sheet with table tbl_Segment_Risk. Country used as segment instead of Category — Description column had 4,070 unique values, too granular for risk analysis. Built PT_Revenue_By_Country and PT_Customer_By_Country PivotTables in Pivot_Tables sheet. Columns: Country, Revenue (XLOOKUP from PT_Revenue_By_Country), Revenue_Contribution_Pct (Revenue/Total Revenue), Customer_Count (XLOOKUP from PT_Customer_By_Country), Customer_Contribution_Pct (Customer_Count/Total Customers), Risk_Flag using IFS formula — High (≥50%), Medium (10-49%), Low (<10%). Key finding: UK = 84.42% revenue and 90.52% customers — only High risk flag. No Medium range countries — concentration jumps from 84.42% (UK) to 2.52% (EIRE). Extreme single-market dependency confirmed. Additional table tbl_Top5_Countries created in Segment_Risk sheet during Phase 7 — Top 5 countries by revenue plus All Others row (£236,141.88 / 6.11%). Used as data source for Dashboard country chart to replace cluttered 33-country visual. |
| Phase 7 — Dashboard | Built Dashboard sheet with full executive layout. Header: title shape (Dark Navy, 20pt Bold White) — "£3.8M Revenue in 2010–2011 with High Volatility and 84% Market Concentration"; subtitle shape (Medium Navy, 9pt) — dataset context and updated date. Five KPI cards (Dark Navy, Gold numbers, Muted Blue-Grey context labels): Total Revenue £3.86M, Total Customers 2,997, Avg Retention Rate 21.27%, Revenue Volatility CV 78.60%, UK Concentration 84.42%. Four charts: (1) Monthly Revenue Line Chart — Gold, A to H; (2) Retention Rate Line Chart — Navy, I to P, with Jan 2011 anomaly annotation; (3) Revenue by Country Horizontal Bar — Top 5 + All Others, UK Gold, others Grey, A to H; (4) New vs Returning Stacked Column — Navy/Gold, I to P. Summary Insight Box — three section structured findings with Gold title, White headers, Muted Blue-Grey bullets, White italic conclusion. Footer connected directly below summary box. Gridlines removed. Color meaning system: Gold = Revenue, Navy = Customer/Retention metrics. |
| Phase 8 — Insight Writing | Wrote five structured insights covering: Revenue Growth & Volatility (8x growth, CV 78.60%), Customer Retention (21.27% avg, 78.73% churn), New vs Returning Behaviour (returning customers grew 40-50x), Market Concentration Risk (84.42% UK dependency), and January 2011 Anomaly (186.29% retention excluded from calculations). Each insight includes key data points, analytical observation, business implication and recommendation. Analytical note added flagging Rev_Per_Customer calculation limitation. |
| Phase 9 — README | Wrote full project README covering Executive Summary, Performance Snapshot, Objective, Business Context, Business Questions, Analysis Approach, Key Findings, Business Implications, Recommendations, Strategic Outlook, Process table, Methodology & Tools, and Data Source. |
| Phase 10 — Polish & Export | *(to be completed)* |

---

## Methodology & Tools

- **Tool:** Microsoft Excel (Power Query, Pivot Tables, Charts)
- **Techniques:** Retention rate calculation, cohort logic, revenue trend analysis, segment risk analysis
- **Currency Note:** Currency values in the dataset are in GBP (£) — British Pounds, as the majority of transactions are from the United Kingdom. No currency symbol is displayed in the raw data columns.

---

## Data Source

- **Dataset:** E-Commerce Analysis - UK
- **Source:** [https://www.kaggle.com/datasets/atharvaarya25/e-commerce-analysis-uk](https://www.kaggle.com/datasets/atharvaarya25/e-commerce-analysis-uk)
- **License:** Community Data License Agreement – Sharing, Version 1.0
- **Attribution:** Dataset sourced from Kaggle. All credit for the original data goes to the dataset publisher.
