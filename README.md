## PROJECT OVERVIEW

### Project Title:
Loan Performance & Customer Segmentation Dashboard

### Objective:
To analyze loan performance metrics across branches and customer demographics, and to identify actionable customer segments for better risk profiling and product targeting.

### Goals:
Understand the health of the loan portfolio

Evaluate repayment behavior and outstanding balances

Analyze loan performance by region, branch, and customer demographics

Identify patterns in defaulted or underperforming loans

Segment customers based on income, age, and employment status for marketing and risk profiling

### Business Value:
This project empowers decision-makers in a financial institution to:

Improve loan product offerings

Target profitable customer segments

Detect risky borrowers early

Monitor performance by branch, region, and customer type

Optimize marketing, risk, and recovery strategies


## BUSINESS QUESTIONS
1. Loan Performance

What is the total loan disbursed, repaid, and outstanding?

What percentage of loans are in default, active, or fully paid?

How does loan performance vary by region and branch?

2. Customer Demographics

What is the distribution of borrowers by age, gender, and employment status?

How does income relate to loan performance (e.g., default rates)?

Are younger or older customers more likely to default?

3. Branch-Level Insights

Which branches have the highest outstanding balances or default rates?

How does the average interest rate differ across branches or regions?

4. Loan Segmentation

What are the common characteristics (age, income, employment) of customers with:

Fully repaid loans?

Defaulted loans?

Can we identify clusters of high-risk vs low-risk customers?

Predictive Metrics

Can we engineer features like payment behavior or risk level?

What customer profiles are likely to require intervention?



### DATA DICTIONARY
#### Fact Table: fact_loan
This table holds transactional and performance data about each loan.

Column Name	Description
LoanID	         Unique identifier for each loan record.
CustomerID	Foreign key linking to dim_customer, identifies the borrower.
BranchID	Foreign key linking to dim_branch, shows where the loan was processed.
LoanAmount	Original principal amount of the loan.
InterestRate	Interest rate applied to the loan (could be monthly or annual).
Term	Duration of the loan (e.g., in months).
StartDate	Date when the loan started.
EndDate	Expected maturity or payoff date.
Status	Current status of the loan – likely values include: Active, Fully Paid, Defaulted.
AmountPaid	Total amount paid by the customer till date (interest + principal).
OutstandingBalance	Remaining unpaid loan balance (principal + interest).


### Dimension Table: dim_branch
This provides branch-level metadata for grouping loans regionally.

Column Name	Description
BranchID	Unique identifier for each branch (joins with fact_loan).
BranchName	Name of the bank branch.
City	City where the branch is located.
Region	Region (e.g., North, South, Central) — useful for regional insights.

### Dimension Table: dim_customer
This gives demographic and economic context about the borrowers.

Column Name	Description
CustomerID	Unique identifier for each customer (joins with fact_loan).
Name	Customer's full name (not always needed in analysis).
Age	Age of the customer.
Gender	Gender (e.g., Male, Female).
Income	Annual income of the customer.
EmploymentStatus	e.g., Employed, Self-Employed, Unemployed, Retired, Student, etc.

### Date Table
To support time-based analysis and trends

Sample Columns	Description
Date	The actual date.
Year	Year part.
Month	Month name or number.
Quarter	Quarter (Q1 to Q4).
Weekday	Day of week, for behavioral analysis.

