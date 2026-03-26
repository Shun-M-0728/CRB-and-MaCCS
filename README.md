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
5. Connecting the budget bill and actual spending data, while creating crosswalk table

## Structure of this repo
```text
C:.
│  README.md
│
├─Data
|  |  2023_budget_bill_final.csv    # Combining the original budget bill with trailer bills
|  |  2023_Budget_Final_Amounts.csv    # Organizing the combined budget data, including aggregating the amount of the same budget
|  |  Fiscal_Data_Final.csv    # Combining fiscal data
|  |  SB101_2023_cleaned.csv    # Original budget bill
│  │  Crosswalk_FY23P01.csv    # Crosswalk table for the first period for FY23
│  │  Detail_FY23P01.csv    # Detail data for the first period for FY23
│  │  Final_Budget_Expenditure_Details.csv    # Detail data after first period for FY23
│  │  Final_Crosswalk_Table_FY23-25.csv    # Crosswalk table after first period for FY23 
│  │  Budget_Spending_Summary_FY23-25.csv     # Summary of datail data : "Final_Budget_Expenditure_Details.csv"
│  │  Monthly_Budget_Spending_FY23-25.csv     # Monthly summary for visualization 
|  |
|  ├─FisCal_Data_Raw
|  └─Trailer_Bills
|
├─doc
|       Data_Integration_Design.md     # Explain how to integrate
|
└─src
        01_2023BudgetAct_Parser.ipynb    # For parsering the original budget bill
        02_2023trailerbill_parser.ipynb    # For parsering the trailer bills   
        03_2023trailerbill_connection.ipynb    # For connecting above two datasets
        04_Budget_data_organized.ipynb    # For organizing above dataset
        05_Connection_bill_to_fiscal.ipynb    # For connecting budget bill and actual spending data
        99_Fiscal_combine_sort.ipynb    # For combining fiscal data
```