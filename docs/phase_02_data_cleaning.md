## PHASE 2 — DATA CLEANING

---

### Sheet: Cleaned_Data (copied from Raw_Data, table named tbl_Cleaned)

---

#### Task 1 — Check for Duplicates
Checked for duplicate rows using **Table Design → Remove Duplicates** with all columns selected.  
**5,269 duplicate rows** were found and removed.  
**536,640 unique rows** remained after removal.

---

#### Task 2 — Confirm Date Format
Clicked on a data cell in the `Invoice_Date` column and checked the Number Format box.  
Result showed **Custom** — this is expected as the Date/Time format was manually set in Power Query.  
Data cells were confirmed as true date values (right-aligned). No conversion needed.

> **Note:** The header row cell shows General — this is normal behavior in Excel and does not affect the data.

---

#### Task 3 — Validate Revenue
Created a `Revenue_Check` helper column using:
```
=ROUND([@[Quantity]]*[@[Unit_Price]],2)=[@[Revenue]]
```
FALSE results were found from two sources:

1. **Return/cancellation transactions** — rows with negative Quantity values, missing Customer_IDs and zero Unit_Price. These are system and return entries, not genuine sales. Flagged for removal in Task 5.
2. **Floating point rounding difference of 0.001** — a minor precision issue in the original dataset, not a real error. Values accepted as-is.

`Revenue_Check` column deleted after investigation.

---

#### Task 4 — Check Missing Values
Checked for missing values across all columns using `COUNTBLANK(tbl_Cleaned[ColumnName])`.

> **Important:** Initial checks using unqualified column references (e.g. `COUNTBLANK([Customer_ID])`) returned incorrect results. All columns were rechecked using full table references (e.g. `COUNTBLANK(tbl_Cleaned[Customer_ID])`) for accuracy.

**Results:**

| Column | Blank Count |
|---|---|
| Invoice_No | 0 |
| Stock_Code | 0 |
| Description | 0 (resolved during deletion) |
| Quantity | 0 |
| Invoice_Date | 305,984 |
| Unit_Price | 0 |
| Customer_ID | 135,037 |
| Country | 0 |
| Revenue | 0 |
| Year/Month/YearMonth | 305,984 (derived from Invoice_Date) |

**Actions taken:**
- Rows with blank Customer_ID (135,037) deleted first
- Remaining rows with blank Invoice_Date deleted after
- Description blanks resolved as part of the same deletion process
- Final clean row count: **170,492**
- All columns confirmed at 0 blanks after cleaning

---

#### Task 5 — Handle Negative Values
Identified negative Quantity rows representing customer returns and cancellations.  
Added helper column `Transaction_Type` using:
```
=IF([@[Quantity]]<0,"Return","Sale")
```

**Results:**
- Return rows: **4,111** (2.4% of dataset)
- Sale rows: **166,381**

All 4,111 return rows were filtered and deleted.  
`Transaction_Type` helper column removed after confirmation.  
**Final clean dataset: 166,381 rows of completed sales transactions only.**

---

#### Task 6 — Add Customer_First_Purchase
Added `First_Purchase` column using TEXT(MINIFS()) to find each customer's earliest purchase date:
```
=TEXT(MINIFS($F:$F,$G:$G,$G2),"DD/MM/YYYY")
```

`Invoice_Date` contained a Date/Time component which caused initial errors — resolved by first creating a `Date_Only` helper column using `INT([@[Invoice_Date]])` to strip the time component. MINIFS took several minutes to calculate across 166,381 rows.

Converted text result to true date value using DATEVALUE in a separate `First_Purchase_Date` column:
```
=DATEVALUE([@[First_Purchase]])
```
Formatted as Short Date → copied → **Paste Special → Values Only** to remove formula dependency.  
`First_Purchase` and `Date_Only` helper columns deleted after confirmation.

---

#### Task 7 — Add Customer_Type
Added `Customer_Type` column using:
```
=IF(INT([@[Invoice_Date]])=[@[First_Purchase_Date]],"New","Returning")
```
`INT()` was used inline to strip the time component from `Invoice_Date` for accurate date comparison.  
Transactions matching a customer's first purchase date are labelled **New**, all others **Returning**.

---

### Goal
`Cleaned_Data` is free of duplicates, missing critical values, and negative transactions.  
Customer-level columns added. Final clean dataset: **166,381 rows.**  
Dataset is fully retention-ready for Phase 3 — KPI Design.

