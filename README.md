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
6. Analyzing this dataset and focusing on 6120 (California State Library)

## Prerequisites
* Python 3.13.5

## Structure of this repo
```text
C:.
│  README.md
│
+---data
|   |  
|   +---01_Original_Bill
|   |       SB101_2023_cleaned.csv    # Original budget bill
|   |
|   +---02_Trailer_Bills    # Three separate files compliant with specific laws, and a single integrated file combining them
|   |       AB102_2023_trailer_bill.csv
|   |       combined_trailer_bills.csv
|   |       SB104_2023_trailer_bill.csv
|   |       SB105_2023_trailer_bill.csv
|   |
|   +---03_Budget_Bill_Final
|   |       2023_budget_bill_final.csv    # Combining the original budget bill with trailer bills
|   |
|   +---04_Budget_Bill_Organized
|   |       2023_Budget_Final_Amounts.csv    # Organizing the combined budget data, including aggregating the amount of the same budget
|   |
|   +---05_Connection_bill_to_fiscal
|   |   +---05_01_Prototype_FY23P11
|   |   |       Crosswalk_FY23P11.csv    # Crosswalk table for the 11th period for FY23 (May 2024)
|   |   |       Detail_FY23P01.csv    # Detail data for the 11th period for FY23 (May 2024)
|   |   |
|   |   \---05_02_30month_to_FY25P09
|   |           Budget_Spending_Summary_FY23-25.csv     # Summary of datail data
|   |           Final_Crosswalk_Table_FY23-25.csv    # Crosswalk table after first period for FY23 
|   |           Monthly_Budget_Spending_FY23-25.csv     # Monthly summary for visualization
|   |      
|   +---06_Focusing_on_6120
|   |       Budget_ID_Top5_Vendors_6120.csv 
|   |       Progress_Rate_6120_Total.csv
|   |
|   +---98_Fiscal_with_adresses
|   |       Fiscal_final_with_addresses.csv
|   |
|   \---99_FisCal_Data_Raw
|
+---doc
|   |   Data_Integration_Design.md     # Explain how to integrate
|   |   Final_Presentation.pdf     # Final presentation slides in MaCSS capstone project
|   |   (Memo)Analysis of budget on CSL.pdf     # Result of Analysis regarding CSL (6120)
|   |   QA_For_Future_Work.pdf     # 7 QAs for future work
|   |
|   \---image     # For using in Final presentation slides
|           budget_utilization_pie_chart.png
|           matching_status_top_start.png
|           Progress_Rate_6120_Total.png
|
\---src
        01_2023BudgetAct_Parser.ipynb    # For parsering the original budget bill
        02_2023trailerbill_parser.ipynb    # For parsering the trailer bills
        03_2023trailerbill_connection.ipynb    # For connecting above two datasets
        04_Budget_data_organized.ipynb    # For organizing above dataset
        05_Connection_bill_to_fiscal.ipynb    # For connecting budget bill and actual spending data
        99_Fiscal_combine_sort.ipynb    # For combining fiscal data
```