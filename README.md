# Loan Default Risk Dashboard - Excel

Excel dashboard analysing 148,670 mortgage loans to find what drives default.
Built for a fictional lender, Nilora Finance.

Tools: Power Query, Power Pivot (DAX), Pivot Tables, Pivot Charts, Slicers.

![Overview](images/1-Overview.png)

## About the project

I wanted to answer a simple question a credit team would ask: which loans are most likely to default, and why?

I cleaned the data in Power Query, loaded it into the Data Model, wrote the measures in DAX and built the report from pivot tables. The 4 slicers (Region, Loan type, Loan purpose, Age group) are connected to all the pivots, so every page filters together.

The Objectives sheet has the 25 questions I worked on and the answer to each one. The Cleaning_Log sheet lists every cleaning step.

## Main findings

- 24.6% of loans are in default, worth 11.7B out of 49.2B
- LTV above 100% -> 65% default rate. LTV under 80% -> around 13-14%
- DTI above 50% -> 42.7%, about 3 times the 36-43% group
- Lump-sum payment loans -> 77.7%. Negative amortization -> 44.6% vs 22.4%
- Business loans (Type 2) -> 34.5% vs 22.8% for Type 1
- North-East is the riskiest region (30.4%)
- Credit score bands are all around 24-25%, so in this data credit score alone doesn't tell good loans from bad ones

## Data issues

While cleaning I noticed some missing values were almost always defaults:

- Interest rate missing in 36.4K loans, almost all of them defaults
- LTV / property value missing in 15.1K loans, all of them defaults
- Equifax bureau shows 100% default
- Zero income loans default at 99.4%

These come from how the data was recorded, not from real borrower risk. So I didn't use them as risk drivers. They're shown on a separate Data Quality page instead.

## Pages

1. Overview
2. Collateral & Affordability (LTV, DTI, income, loan size)
3. Borrower Profile (age, applicant type, credit score)
4. Product & Terms (amortization, lump sum, term, occupancy)
5. Data Quality

![Collateral](images/2-Collateral.png)
![Borrowers](images/3-Borrowers.png)
![Products](images/4-Products.png)
![Data Quality](images/5-Data%20Quality.png)

## Files

- `Loan_Default_Dashboard.xlsx` - the workbook (pivot and check sheets are hidden, right-click a tab > Unhide to see them)
- `data/Loan_Default_Clean.zip` - cleaned data from Power Query (the original data is on Kaggle, link below)
- `images/` - screenshots

## Data source

[Loan Default Dataset](https://www.kaggle.com/datasets/yasserh/loan-default-dataset) on Kaggle (CC0). The categories are anonymised and no currency is given.
