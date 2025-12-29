# MySQL CSV Data Ingestion – Date Normalization Case Study

## Overview
This project demonstrates a real-world data ingestion problem commonly encountered
when loading CSV files from Excel into MySQL using `LOAD DATA INFILE` way.

The focus is on **preventing NULL date values** caused by inconsistent source formats
and Excel’s date handling.

---

## Problem Statement
During CSV ingestion, date columns were being imported as `NULL` in MySQL despite
appearing valid in Excel.

### Root Causes Identified
- Excel stored dates as text rather than true date values
- Source files contained mixed date formats, some had **DD/MM/YYYY** While other **YYYY-MM-DD**
- MySQL requires strict `YYYY-MM-DD` formatting for `DATE` columns
- Silent failures occurred during ingestion

---

## Way to Solution 

### Step 1: Source Data Normalization (Excel)
Dates were normalized at the source using Excel before export:

```excel
=TEXT(A2,"yyyy-mm-dd")
```
---
Values ​​were then pasted as static values ​​and exported as UTF-8 CSV.

Outcome

100% successful ingestion

No NULL dates




