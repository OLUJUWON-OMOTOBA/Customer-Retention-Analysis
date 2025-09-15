# Customer Retention Analysis

## Overview


A customer lifecycle and retention analysis that explores signup cohorts, churn rates, and average customer value. This repo demonstrates cohort analysis, churn calculation, and how to turn retention findings into actionable recommendations.

## Customer Churn Analysis
<img width="1244" height="706" alt="image" src="https://github.com/user-attachments/assets/2bbf4efa-5639-4509-8425-fbcac1c4c4b3" />

## Churn rate analysis (time based)
<img width="1240" height="705" alt="image" src="https://github.com/user-attachments/assets/9ea1146c-1dab-454d-b54d-936b3e3f4324" />

## What’s included


- `customers.csv` — sample customer-level dataset (600 rows)
- `retention_queries.sql` — SQL examples for cohort and churn queries
- `retention_dax_measures.txt` — suggested DAX measures for retention metrics
- `README.md` — this file


## Key features & highlights


- Churn analysis (Chart by categories and gender)
- Churn rate calculation and trends
- Churn rate by reason and cities


## Suggested Power BI build steps


1. Imported `customers.csv` into Power BI Desktop.
2. Parsed `signup_date` and `last_active_date` as Date types.
3. Created a Date dimension and relate to relevant date columns if you split events across tables.
4. Created calculated columns: tenure (months active), cohort month (signup month).
5. Build visuals:
- Cohort retention matrix or area chart showing % retained over months since signup
- Line chart: churn rate over time
- Bar chart: Average monthly spend by cohort
6. Add filters for cohort month and customer segments.


## DAX snippets


```dax
Churned Customers = CALCULATE(COUNT(customers[customer_id]), FILTER(customers, customers[churned] = 1))
Total Customers = COUNT(customers[customer_id])
Churn Rate = DIVIDE([Churned Customers], [Total Customers])
Months Active = DATEDIFF(customers[signup_date], customers[last_active_date], MONTH)
