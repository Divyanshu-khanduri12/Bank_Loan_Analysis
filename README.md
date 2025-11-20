Bank Loan Analysis Dashboard (Power BI)
Project Overview

A Power BI dashboard that analyzes a bank's loan portfolio to provide insights into application volumes, funded amounts, repayment status, portfolio quality, and borrower profiles. The dashboard supports interactive filtering and drill-downs to help credit teams, risk analysts, and stakeholders make data-driven decisions.

Key Metrics (from dataset)

Total Loan Applications: 38.6K

Good Loans: 33.2K (86.18%)

Bad Loans: 5K (13.82%)

Total Funded Amount: $435.8M

Total Received Amount: $473.1M

Average Interest Rate: 12.0%

Average DTI: 13.3%

These numbers are taken from the dashboard KPI cards (Summary page).

Pages / Visualizations

Summary – High-level KPI cards, good vs bad loan donut visuals, portfolio totals, and a performance table broken down by status (Fully Paid / Charged Off / Current).

Overview – Trend analysis (monthly applications), geographic map, loan term distribution, loan applications by purpose/grade/employment length, and ownership breakdown.

Detailed – Transaction-level table with loan-level fields such as id, purpose, home_ownership, grade, sub_grade, issue_date, total_fund_amount, average_int_rate, sum_of_installment, total_received_amount.

Data Sources & Model

Source file: Bank_loan_powerbi.pbix (Power BI Desktop report) – the data model includes a main Bank_loan table and date dimension (Dim_Date).

Key fields used: id, purpose, home_ownership, grade, sub_grade, issue_date, total_fund_amount, total_received_amount, average_int_rate, dti, emp_length, term, loan_status, installment.

Modeling notes: Date table (Dim_Date) used for time intelligence; measures are created using DAX and the model is star-like with Bank_loan as the fact table.

Important DAX Measures (examples)

Total_Loan_Application = COUNTROWS(Bank_loan)

Total_Fund_Amount = SUM(Bank_loan[total_fund_amount])

Total_Received_Amount = SUM(Bank_loan[total_received_amount])

Average_Interest_Rate = AVERAGE(Bank_loan[average_int_rate])

Good_Loans = CALCULATE([Total_Loan_Application], Bank_loan[loan_status] = "Good")

Bad_Loans = CALCULATE([Total_Loan_Application], Bank_loan[loan_status] = "Bad")

(Exact measure names and logic may vary in the PBIX; adjust according to your model.)

Key Features

Interactive slicers for Purpose, Grade, State, Home Ownership, and Good vs Bad loan classification.

Trend and month-over-month (MoM) / month-to-date (MTD) calculations for quick performance checks.

Drill-through and drill-down capabilities to inspect loan details from KPI cards and charts.

Clean color-coded design and KPI cards for stakeholder-ready presentation.

How to Open & Use

Open the Bank_loan_powerbi.pbix file in Power BI Desktop.

Refresh the dataset if needed (ensure source CSV/Excel/DB is available or embedded).

Use the left-hand page navigator to switch between Summary, Overview, and Detailed pages.

Apply slicers (Purpose, Grade, State, Home Ownership) and click visuals to drill into the data.

Suggested Improvements / Next Steps

Add additional credit-risk metrics (PD/LGD estimates) and cohort analyses.

Include cohort retention charts for borrower repayment behavior over time.

Implement automated data refresh using Power BI Service and scheduled gateways if sources are live.

Add commentary cards highlighting monthly anomalies or alerts for high delinquency by segment.
