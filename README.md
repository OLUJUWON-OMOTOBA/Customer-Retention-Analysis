# Customer Retention Analysis


![Power BI](https://img.shields.io/badge/Tool-Power%20BI-blue)
![Dataset](https://img.shields.io/badge/Dataset-Synthetic-green)


## Overview


A customer lifecycle and retention analysis that explores signup cohorts, churn rates, and average customer value. This repo demonstrates cohort analysis, churn calculation, and how to turn retention findings into actionable recommendations.


## What’s included


- `customers.csv` — sample customer-level dataset (600 rows)
- `retention_queries.sql` — SQL examples for cohort and churn queries
- `retention_dax_measures.txt` — suggested DAX measures for retention metrics
- `README.md` — this file


## Key features & highlights


- Cohort analysis (retention curves by signup month)
- Churn rate calculation and trends
- Average monthly spend and simple LTV approximation


## Suggested Power BI build steps


1. Import `customers.csv` into Power BI Desktop.
2. Parse `signup_date` and `last_active_date` as Date types.
3. Create a Date dimension and relate to relevant date columns if you split events across tables.
4. Create calculated columns: tenure (months active), cohort month (signup month).
5. Build visuals:
- Cohort retention matrix or area chart showing % retained over months since signup
- Line chart: churn rate over time
- Bar chart: Average monthly spend by cohort
6. Add filters for cohort month and customer segments.


## Example DAX snippets


```dax
Churned Customers = CALCULATE(COUNT(customers[customer_id]), FILTER(customers, customers[churned] = 1))
Total Customers = COUNT(customers[customer_id])
Churn Rate = DIVIDE([Churned Customers], [Total Customers])
Months Active = DATEDIFF(customers[signup_date], customers[last_active_date], MONTH)
