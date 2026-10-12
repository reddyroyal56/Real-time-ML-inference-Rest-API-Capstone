# Responsible Data Card — Customer Churn CSV

## Dataset purpose
For educational practice only: explore a baseline prediction of the `churned` label from customer tenure, support-ticket count, monthly spend, recent login recency, and plan type. Do not use this tiny sample to make real customer decisions.

## Provenance and permission
The CSV was supplied for the Task 03 workflow. The available files do not state the original creator, collection method, consent, license, or permitted uses. Confirm these with the provider before redistributing or using beyond the assessment.

## Population and representation
The file has 12 rows and 7 columns. The sampling frame, time period, geography, and inclusion criteria are not documented. Target labels: 7 records with `churned=0` and 5 with `churned=1`. This sample is too small to represent a customer population reliably.

## Features and target
- `customer_id`: identifier; excluded from model inputs.
- `tenure_months`: customer tenure in months.
- `support_tickets`: support-ticket count; time window unspecified.
- `monthly_spend_inr`: monthly spend in INR.
- `last_login_days`: days since last login.
- `plan_type`: customer plan category.
- `churned`: target label (1 or 0); exact business definition and observation window not documented.

Possible leakage cannot be ruled out without feature timestamps and the precise target definition. Some behavior variables may proxy for customer circumstances; assess this with domain review.

## Quality checks
The CSV has 12 rows and 7 columns. No missing values, exact duplicate rows, or duplicate IDs were observed in this copy. The tiny sample makes outlier analysis inconclusive. Train/test split is done before fitting transformations.

## Risks and safeguards
- Misleading performance due to tiny sample: obtain larger, representative, documented data.
- Privacy risk: confirm permission and avoid publishing identifiable records.
- False positives may cause unnecessary retention contact; false negatives may miss customers needing support.
- Evaluate error costs, fairness where lawful and appropriate, and human-review fallback before any real-world pilot.
- Do not use this toy model for automated customer decisions.

## Intended evaluation
Use a majority-class non-ML baseline and report accuracy, precision, recall, F1, and confusion matrix. If reliable probabilities are needed, assess calibration with sufficient validation data. Review false positives/negatives, subgroup error rates where appropriate, drift monitoring, and rollback conditions before deployment.
