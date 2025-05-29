# Project Overview
 ### Project Title:
Loan Performance & Customer Segmentation Dashboard

### Objective:
To analyze loan performance metrics across branches and customer demographics, and to identify actionable customer segments for improved risk profiling and targeted product strategies.

### Goals:
1. Assess the health of the loan portfolio

2. Evaluate repayment behavior and outstanding balances

3. Analyze loan performance by region, branch, and customer attributes

4. Identify patterns in defaulted or underperforming loans

5. Segment customers based on income, age, and employment status for marketing and risk analysis

### Business Value:
This project enables decision-makers in financial institutions to:

1. Enhance loan product offerings based on performance trends

2. Target high-value and low-risk customer segments

3. Detect risky borrowers early for preventive actions

4. Monitor branch- and region-level performance efficiently

5. Optimize strategies for marketing, risk management, and loan recovery

### Business Questions
 Loan Performance
1. What is the total loan amount disbursed, repaid, and outstanding?
   
2. What percentage of loans are active, defaulted, or fully paid?

3. How does loan performance differ across regions and branches?

 Customer Demographics
1. What is the distribution of borrowers by age, gender, and employment status?

2. How does income level relate to loan performance and default rates?

3. Are certain age groups more likely to default?

 Branch-Level Insights
1. Which branches have the highest outstanding balances or default rates?

2. How do average interest rates vary across branches or regions?

 Loan Segmentation
1. What characteristics (age, income, employment status) are associated with:

   Fully repaid loans?


### Dataset Overview
The analysis is based on a star schema consisting of the following tables:

1. fact_loan: Core transactional data for loans (Loan ID, Customer ID, Loan Amount, Term, Start/End Dates, Payment Status).

2. dim_customer: Contains customer demographic and financial attributes (Age, Gender, Income, Employment Status).

3. dim_branch: Provides metadata about loan branches (City, Region).

4. date_table: Supports time-based analysis.



   Defaulted loans?



