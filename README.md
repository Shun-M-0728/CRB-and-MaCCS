# CRB-and-MaCCS

## Team member
Sanjana Karthick, Shun Moriguchi

## Purpose of this repo
To collaborate CRB and MaCCS as the Capstone project.

## Goal of this project
Building a prototype pipeline will serve as proof of concept for CRB to request funding  
With funding, CRB could outsource development of a comprehensive, queryable database of budget and spending data across time.  
- Eliminates repetitive, one-off research
- Enables faster, more efficient budget and spending analysis
- Improves responsiveness to legislators: The most common requests CRB receives are budget-related

## What we did
1. Parsering the original budget bill(SB101)  
2. Parsering the trailer bills(AB102, SB104 and SB105)
3. Connecting above these two datasets
4. Organizing the combined budget data, including aggregating the amount of the same budget

# Structure of this repo
+---Data
|   |   .DS_Store
|   |   2023_budget_bill_final.csv    # Combining the original budget bill with trailer bills
|   |   2023_Budget_Final_Amounts.csv    # Organizing the combined budget data, including aggregating the amount of the same budget
|   |   Fiscal_Data_Final.csv    # Combining fiscal data
|   |   SB101_2023_cleaned.csv    # Original budget bill
|   |
|   +---FisCal_Data_Raw
|   \---Trailer_Bills
|
\---src
        01_2023BudgetAct_Parser.ipynb    # For parsering the original budget bill
        02_2023trailerbill_parser.ipynb    # For parsering the trailer bills   
        03_2023trailerbill_connection.ipynb    # For connecting above two datasets
        04_Budget_data_organized.ipynb    # For organizing above dataset
        99_Fiscal_combine_sort.ipynb    # For combining fiscal data