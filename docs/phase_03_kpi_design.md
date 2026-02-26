## PHASE 3 — KPI DESIGN

---

### Core KPIs

#### 1. Total Customers
Distinct count of `Customer_ID`  
> Measures the total unique customers in the dataset.

---

#### 2. New Customers (per month)
Count of `Customer_ID` where `Customer_Type` = "New" grouped by `YearMonth`  
> Tracks how many first-time customers transacted each month.

---

#### 3. Returning Customers (per month)
Count of `Customer_ID` where `Customer_Type` = "Returning" grouped by `YearMonth`  
> Tracks how many repeat customers transacted each month.

---

#### 4. Retention Rate
```
Returning Customers (Month n) / Total Customers (Month n-1)
```
> Measures the percentage of previous month's customers who came back.

---

#### 5. Churn Rate
```
1 − Retention Rate
```
> Measures the percentage of customers who did not return the following month.

#### 6. Monthly Revenue
SUM of `Revenue` grouped by `YearMonth`  
> Tracks total revenue generated each month across all transactions.

---

#### 7. Revenue per Customer
```
Monthly Revenue / Active Customers per Month
```
> Measures average revenue contribution per active customer each month.

---

#### 8. Average Order Value (AOV)
```
Monthly Revenue / Number of Orders per Month
```
> Measures average transaction value per order each month.  
> Added because this dataset has individual transaction lines (Quantity × Unit_Price) rather than a single final price per order.

---

#### 9. Revenue Concentration
Top 10% of customers by total Revenue contribution  
> Measures how dependent overall revenue is on a small group of high-value customers.  
> Ties directly to concentration risk analysis in Phase 6.

---

#### 10. Top Countries by Revenue
SUM of `Revenue` grouped by `Country`  
> Identifies which markets drive the most revenue.  
> Unique to this dataset given the international transaction data available.

---

### KPI Pillars
These KPIs directly support the three core analysis pillars:

| Pillar | KPIs |
|---|---|
| Customer | Total Customers, New Customers, Returning Customers, Retention Rate, Churn Rate |
| Revenue | Monthly Revenue, Revenue per Customer, Average Order Value, Revenue Concentration |
| Risk | Churn Rate, Revenue Concentration, Top Countries by Revenue |

---

### Note

Distinct Count was not available on Mac Excel. A helper column Customer_Count was created using `=1/COUNTIF(tbl_Cleaned[Customer_ID],[@[Customer_ID]])` to calculate distinct customer counts via SUM in PivotTables. Total unique customers confirmed as 2,997.

