## PHASE 1 — DATA IMPORT VIA POWER QUERY

---

### Step 1 — Open Power Query
Go to **Data → Get Data → From Text/CSV** → select your CSV file → click **Transform Data** (not Load).  
This opens the Power Query Editor.

---

### Step 2 — Delete Auto-Generated Step (Important)
Power Query automatically adds a `Changed Type` step using its own guesses.  
Check the **Applied Steps** panel on the right.  
If you see an auto-generated `Changed Type` step → **delete it first**, then manually set your types in Step 3.  
This protects your IDs from being read as numbers.

---

### Step 3 — Set Column Data Types
In Power Query, select each column and assign the correct type manually:

| Column | Data Type |
|---|---|
| InvoiceNo | Text |
| StockCode | Text |
| Description | Text |
| Quantity | Whole Number |
| InvoiceDate | Date/Time |
| UnitPrice | Decimal Number |
| CustomerID | Text |
| Country | Text |

To change type: click the **icon at the top left of each column header** → select the correct type.  
Do this **before** any other transformation to avoid Power Query auto-inferring wrong types.

> **Note:** CustomerID must be set to Text to prevent ID corruption. Quantity will display as Int64 in Power Query — this is the same as Whole Number and requires no further action.

---

### Step 4 — Rename Columns
Rename columns to remove inconsistencies and improve readability:

| Original Name | New Name |
|---|---|
| InvoiceNo | Invoice_No |
| StockCode | Stock_Code |
| InvoiceDate | Invoice_Date |
| UnitPrice | Unit_Price |
| CustomerID | Customer_ID |

To rename: **double-click** each column header → type the new name → press **Enter**.

---

### Step 5 — Add Calculated Columns

#### Year
1. Select the `Invoice_Date` column
2. Go to **Add Column → Date → Year → Year**
3. A new column called `Year` is created automatically

#### Month
1. Select the `Invoice_Date` column
2. Go to **Add Column → Date → Month → Month**
3. Rename the column to `Month`

> This gives you the month as a number (1–12). Useful for sorting and calculations.

#### YearMonth
1. Go to **Add Column → Custom Column**
2. Name it `YearMonth`
3. Enter this formula (no `=` sign at the start):

```
Text.From(Date.Year([Invoice_Date])) & "-" & Text.PadStart(Text.From(Date.Month([Invoice_Date])), 2, "0")
```

This produces a clean format like `2010-01`, `2010-02` — sortable and pivot-friendly.

#### Revenue
1. Go to **Add Column → Custom Column**
2. Name it `Revenue`
3. Enter this formula (no `=` sign at the start):

```
[Quantity] * [Unit_Price]
```

> This dataset does not have a pre-calculated final price column. Revenue is derived from Quantity × Unit_Price and serves as the transaction value for all revenue analysis.

---

### Step 6 — Close & Load
Once all columns are confirmed in the **Applied Steps** panel:  
**Close & Load → Close & Load To** → select **Table** → load into a sheet named `Raw_Data`.  

---

### Goal
Data lands in Excel with correct types and calculated columns from the start.  
No ID corruption.  
No date misreads.  
No decimal errors.

`Raw_Data` is clean and retention-ready before Phase 2 begins.

