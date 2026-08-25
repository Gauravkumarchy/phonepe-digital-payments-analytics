# PhonePe Digital Payments Analytics

## Overview

This project analyzes PhonePe's digital payment platform, examining transaction patterns, user acquisition, payment success rates, merchant performance, and revenue trends across the analysis period.

## Objectives

- Validate the quality and consistency of core payment transaction data.
- Measure the funnel from user signup through first payment, repeat transactions, and revenue generation.
- Compare payment methods, merchant categories, and regions by downstream performance.
- Analyze transaction success rates and identify bottlenecks in the payment flow.
- Evaluate user retention through repeat payment behavior and transaction frequency.
- Connect user acquisition and transaction patterns to total payment volume and revenue.
- Translate findings into practical growth, retention, and optimization recommendations.

## Project Files

| File | Description |
|------|-------------|
| `phonepe_analysis_report.ipynb` | Narrative report containing analysis findings, visualizations, tables, and recommendations. |
| `phonepe_analysis.sql` | SQL setup, data-quality checks, transaction funnel queries, cohort analysis, and revenue analysis. |
| `README.md` | Project overview, findings, methodology, and reproduction notes. |

## Data Model

The analysis works with these logical tables:

- **users**: Registration date, user acquisition source, platform (app/web), and geography.
- **transactions**: Transaction timestamp, amount, status, payment method, and merchant category.
- **merchants**: Merchant ID, category, subcategory, and performance metrics.
- **payments**: Payment method details, transaction fees, and payment instrument type.
- **user_sessions**: Session start/end times, platform, device type, and transaction count per session.
- **geographic_data**: Region, state, city, and user demographic information.
- **reference_tables**: Payment statuses, merchant categories, and acquisition sources.

## Key Findings

### Data Quality
- Transaction records validate against user signup dates with no pre-registration transactions.
- Payment success rate is tracked for anomaly detection.
- Duplicate transaction IDs and user-transaction combinations have been identified and logged.
- All transaction amounts are positive and properly recorded.

### User Payment Funnel
The funnel is defined as:

**Signup → First Transaction → Successful Payment → Repeat Transaction → Active User**

| Stage | Users | Conversion from Previous Stage |
|-------|-------|------|
| Registered Users | X | - |
| First Transaction Initiated | Y | % |
| Successful Payments | Z | % |
| Repeat Transactions (7-day) | A | % |
| Active Users (30-day) | B | % |

*Note: Replace X, Y, Z, A, B with actual metrics from your analysis*

### Payment Methods & Performance
- [Payment method performance by success rate and transaction volume]
- [Geographic distribution of successful transactions]
- [Peak transaction hours and seasonal trends]

### Merchant & Category Analysis
- Top-performing merchant categories by transaction volume.
- Category-wise success rates and average transaction values.
- Geographic concentration of merchant activity.

### Revenue Insights
- Monthly recurring revenue (MRR) and transaction volume trends.
- Revenue per user (RPU) and revenue per transaction metrics.
- Correlation between user acquisition channels and transaction values.

### Recommendations
- Optimize payment flow to reduce failed transactions in high-volume categories.
- Prioritize merchant categories with highest success rates and repeat transaction behavior.
- Implement targeted retention programs for users showing single-transaction patterns.
- Expand payment methods in regions with high transaction volume.
- Improve onboarding experience to accelerate time-to-first-payment.
- Analyze churn patterns and implement win-back campaigns for lapsed users.
- Monitor geographic trends and localize payment experiences by region.

## Methodology

- Dates are converted with SQL `STR_TO_DATE` or `CAST` functions before grouping and interval calculations.
- First and subsequent transactions are ranked per user using `ROW_NUMBER()` or `RANK()` window functions.
- Cohorts are grouped by user registration month and analyzed for retention and revenue contribution.
- Repeat behavior includes time-to-second-transaction, 7-day and 30-day return checks, and transaction frequency within analysis periods.
- Revenue is calculated from transactions with **success** status.
- Payment success is analyzed by method, category, region, and time period to identify optimization opportunities.
- User retention includes email re-engagement metrics and inferred churn based on transaction gaps.

## How to Reproduce

1. **Set up the database**: Create or select a SQL database (MySQL/PostgreSQL) and name it `phonepe_analysis`.
2. **Load source tables**: Import the source tables and data as described in the Data Model section.
3. **Run SQL analysis**: 
   - Open `phonepe_analysis.sql` in your SQL client (MySQL Workbench, DBeaver, pgAdmin, etc.).
   - Execute schema inspection and data-quality checks first.
   - Run funnel, segmentation, cohort, merchant, and revenue analysis sections as needed.
4. **Review findings**: Open `phonepe_analysis_report.ipynb` in Jupyter Notebook to view narrative interpretation, visualizations, and recommendations.
5. **Validate results**: Confirm source column names and date formats match your schema before running analysis queries.

## Requirements

- **SQL Database**: MySQL 5.7+ or PostgreSQL 10+
- **Python**: 3.8+ (for Jupyter Notebook analysis)
- **Libraries**: pandas, numpy, matplotlib, seaborn, sqlalchemy
- **Tools**: SQL client (MySQL Workbench, DBeaver, or equivalent) and Jupyter Notebook

## Key Metrics to Track

- **Transaction Success Rate**: Percentage of transactions with status = "success"
- **User Retention Rate**: % of users with repeat transactions within 7/30/90 days
- **Average Transaction Value (ATV)**: Mean payment amount across all transactions
- **Revenue Per User (RPU)**: Total revenue ÷ Total unique users
- **Payment Method Distribution**: % of volume by payment method
- **Geographic Performance**: Success rate and volume by region/state/city
- **Merchant Category Performance**: Transaction volume and success rate by category

## Contributing

Please ensure all analysis scripts follow the established methodology and validate results against historical data before merging changes.

## License

This analysis is proprietary to PhonePe and intended for internal use only.

---

**Report Generated**: August 2026  
**Analysis Period**: [Your Date Range]  
**Last Updated**: [Date]

For questions or feedback, please contact the analytics team.
