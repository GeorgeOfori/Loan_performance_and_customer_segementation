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
1. Which customer segments contribute most to loan disbursement and default?

2. What are the risk patterns across demographics and employment types?

3. How do regional branches compare in terms of loan portfolio performance?

4. What operational or policy strategies can optimize loan recovery and profitability?



## Exploratory Data Analysis(EDA) and Data Cleaning 
 The data cleaning include: check structure, removed duplicates, and handled missing values.
 
 The Exploratory Data Analysis(EDA) includes


    


   ![Loan Status Distribution](Images/Loan_status_distribution.png)

 #### Key insights
 1. Paid Loans Dominate: The most frequent status is "Paid", indicating a relatively strong repayment culture or successful underwriting processes. This is a good sign for overall loan portfolio health.
 2. Significant Approved Loans: A high number of loans are in the "Approved" category. This suggests an active pipeline and potential for future earnings, but also underlines the importance of close monitoring 
    to ensure conversion to repayment.
 3. Default Rate Noticeable: The "Defaulted" loans, although smaller in count, are significant enough to warrant attention. This group presents a clear risk and should be examined for shared traits (e.g., 
    demographics, income level, loan size).
 4. In Progress Loans: The mid-sized bar for "In Progress" shows an active set of loans currently in repayment or early stages. Timely engagement and support could reduce the chance of future defaults.



     ![Age vs Outstanding Balance](Images/Age_vs_outstanding_balance.png)


#### Key insights:
 1. There is no clear linear relationship between age and outstanding balance, indicating that loan balances are distributed fairly evenly across different age groups.
 2. Defaulted and In Progress loans are widespread across all ages, but slightly concentrated among the 25 to 50 age range, indicating higher financial activity or risk within this demographic.
 3. Approved loans also appear across the board, but many still show relatively high outstanding balances suggesting early-stage repayment or potential risk zones.



     ![Loan Status by Gender](Images/Loan_status_by_gender.png)


#### Key insights:
 1. Both genders show similar patterns in loan status distributions.
 2. Slightly more females than males have fully paid their loans.
 3. Default rates are comparable, though slightly higher in males, suggesting a potential area for gender-focused risk assessment.
 4. The number of approved and in-progress loans are relatively similar across genders, indicating fair approval practices and engagement.



    ![Distribution of Loan Amounts](Images/Distribution_of_loan_amounts.png)


 #### Key insights:

 1. Loan Size is Fairly Evenly Distributed: The histogram indicates a fairly uniform distribution of loan amounts, with most loans clustering between 10,000 and 45,000 units.
 2. Mild Peaks at Mid Ranges: There's a slight increase in loans around 30,000–35,000, indicating borrower preference or eligibility for mid-sized loans.
 3. Low Volume at Extremes: Fewer loans are issued below 10,000 or above 45,000, which could be due to policy constraints or fewer applicants needing amounts at those ranges.


   
For full data exploration and cleaning steps, see the [Data Exploration & Cleaning Notebook](notebooks/data_exploration_cleaning.ipynb).


## Data Transformation(ETL)
  Data extracted, transformed and loaded into Power BI for modeling and visualiaztion.
  ![Table view](Images/Data_view.png)


## Power BI 
 ### Data Modelling
 ![Modeling view](Images/Data_modeling_view.png)


### Dataset Overview
The analysis is based on a star schema consisting of the following tables:

1. fact_loan: Core transactional data for loans (Loan ID, Customer ID, Loan Amount, Term, Start/End Dates, Payment Status).

2. dim_customer: Contains customer demographic and financial attributes (Age, Gender, Income, Employment Status).

3. dim_branch: Provides metadata about loan branches (City, Region).

4. date_table: Supports time-based analysis.


### Report view 
   #### overview

 ![Overview](Images/Overview.png)
 

#### Key insights:
1. Roughly 45% of the total loan amount has been repaid, while 43% remains outstanding.
2. The Approved segment holds a significant share, representing potential future income. Defaulted amount is lower but non-negligible.
3. Loan volume grew steadily, peaked, and then significantly dropped in 2025, suggesting reduced demand, stricter lending policies, or operational issues.
4. Loan amounts are fairly distributed, but regional focus is clear.
5. Wisconsin has the highest outstanding, implying higher risk exposure if defaults increase.
  


 #### Customer Segmentation and Risk

    

   ![Customer segmentation & Risk](Images/Customer_segementation_&_risk.png)


#### Key insights:
1. Male customers account for $1.61M (55.23%) in loans.Female customers account for $1.31M (44.77%). This suggests a slightly higher loan uptake by males.
2. Highest outstanding balance by employment status: Retired: $386.55K (31.58%) Followed by Employed, Unemployed, and Self-Employed. Default rate is highest among: Unemployed (0.17) and Employed (0.15). Lower 
   for Self-Employed (0.05) and Retired (0.03).
3. Defaults and approved loans are spread across all age groups, but younger and middle-aged clients (20–50) show more activity.


#### Regional Performance Analysis


    

 ![Regional Performance Analysis](Images/Regional_performance_analysis.png)

#### Key insights:

1. Top 3 regions by total loan amount: Delaware ($3.34M), Montana ($3.12M),Idaho ($2.92M). Regions with highest default rates: Maine (0.16) and Texas (0.15). Lowest performing region in payment ratio: Maine 
   (32.57)  Delaware and Montana are performing well with high disbursements and moderate default rates.
2. Highest average interest rate: Wisconsin (9.6%), followed by Mississippi (9.1%) and Lowest is Florida (8.8%)



## Final Recommendations

1. Implement Data-Driven Risk Scoring. Develop a robust credit risk model. Assign risk-weighted interest rates and loan limits, for instance higher rates for unemployed borrowers or regions with historical 
   defaults.
   
2. Optimize Regional Branch Strategy by scalling up lending operations in Delaware, Montana, and Idaho, where loan performance is stable. Also, reassess underwriting policies in Maine and Texas, potentially 
   reduce disbursements or tighten approval thresholds. Invest in staff training and automated underwriting tools in underperforming branches.
  
3. Targeted Product Design by introducing a senior-focused loan products (e.g., pension-backed loans), given retirees’ high balances and low default risk. Also offer microloans or emergency credit lines with 
   stricter monitoring for high-risk groups (unemployed, early-career professionals).
  
4. Proactive Loan Monitoring should be establised to determine early warning systems to flag borrowers with poor repayment behavior. Branches exceeding default risk thresholds. Also launch automated reminders, 
   credit counseling, and loan restructuring programs before defaults spike.

5. Periodic Portfolio Review by conducting quarterly portfolio health checks by region, age group, and risk tier.




### CALCULATED COLUMNS & MEASURES
   #### Calculated Columns (Power BI DAX)
   
1. Loan Tenure (Months)
  LoanTenureMonths = DATEDIFF(fact_loan[StartDate], fact_loan[EndDate], MONTH)

2. Payment Ratio
   PaymentRatio = DIVIDE(fact_loan[AmountPaid], fact_loan[LoanAmount])

3. IsDefault = IF(fact_loan[Status] = "Defaulted", 1, 0)

  ####  DAX Measures
1. Total Loans
   TotalLoans = COUNT(fact_loan[LoanID])

2. Total Loan Amount
   TotalLoanAmount = SUM(fact_loan[LoanAmount])

3. Outstanding Balance
   TotalOutstanding = SUM(fact_loan[OutstandingBalance])

4. Average Interest Rate 
   AverageInterestRate = AVERAGE(fact_loan[InterestRate])

5. Default Rate
   DefaultRate = DIVIDE(SUM(fact_loan[IsDefault]), COUNT(fact_loan[LoanID]))
