# 2023 Budget Spending Analysis: Data Integration Design (Updated)

## 1. Data Sources
* **Source A (Master): 2023 Budget Acts (Scraped from Text)**
    * A master list extracted from legislative Budget Act texts. It includes budget amounts, Business Units (BU), Budget References, Fund Codes, and Object/Project Codes.
* **Source B (Transaction): Open Fi$Cal Monthly Reports (2023.07 - 2025.12)**
    * Monthly expenditure records. Contains `monetary_amount` (actual spending), `VENDOR_NAME` (payee), and `accounting_date` (payment date), along with attributes such as `agency_name` and `department_name`.

## 2. The Bridge: Budget_ID
To connect these two datasets, a unique common key called **`Budget_ID`** is generated.

### Budget_ID Structure
`[Year]-[Business_Unit]-[Budget_Reference]-[Fund_Code]-[Target_Code]`

### Generation Logic
* **Code Normalization (Padding):** Numerical codes for BU (4 digits), Ref (3 digits), and Fund (4 digits) are padded with leading zeros using the `pad_code` function to ensure consistent string lengths (e.g., `110` → `0110`).
* **Target_Code Selection:**
    * Priority 1: `object_code` (used if it is not "0", "EMPTY", or "NaN").
    * Priority 2: `program_code` (the project code from the Budget Act is used as a fallback).
* **Fiscal Side:** Two temporary IDs are generated from the fiscal `program_code` for prefix matching: `Budget_ID_7` (first 7 digits) and `Budget_ID_4` (first 4 digits).

## 3. Mapping Strategy (2-Step Merging)
To maximize the matching rate between legislative items and system transactions, a **2-step sequential merge** is employed:

1.  **Step 1 (7-digit Match):** Matches the budget `Budget_ID` against the fiscal `Budget_ID_7` (precise Object-level matching).
2.  **Step 3 (4-digit Match):** For items not matched in Step 1, a second attempt is made using the fiscal `Budget_ID_4` (Project-level rescue matching).
3.  **Result:** This ensures that even if detailed expenditure codes vary, transactions are correctly linked to the corresponding budget project.

## 4. Integration Pipeline
1.  **Year Filtering:** Fiscal data is strictly filtered to `year_of_enactment == 2023` to ensure alignment with the 2023 Budget Act.
2.  **Automated Looping:** All files matching `Vendor_FY2*P*.csv` (covering FY23-FY25) are processed in bulk to capture the full spending lifecycle across multiple years.
3.  **Master Preservation:** A final `Left Join` is performed using the Budget Master as the base table. This ensures all legislated items are retained in the report, even those with zero spending (0% execution rate).

## 5. Output Reports
* **Final_Budget_Expenditure_Details.csv:** A comprehensive transaction log (approx. 1.5M rows). Includes `department_name` and `VENDOR_NAME` for granular drill-down analysis.
* **Budget_Spending_Summary_FY23-25.csv:** A summary report aggregated by `Budget_ID`. Ideal for high-level execution rate visualization.
* **Final_Crosswalk_Table_FY23-25.csv:** A master dictionary linking `Budget_ID` to `agency_name`, `department_name`, and `program_description`.

---
