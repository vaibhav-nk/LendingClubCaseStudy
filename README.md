# Lending Club
> The given dataset contains the loan deatils of the lending company from 2007 to 2011. The data given in dataset contains information about past loan applicants and whether they ‘defaulted’ or not. The aim is to identify patterns which indicate if a person is likely to default, which may be used for taking actions such as denying the loan, reducing the amount of loan, lending (to risky applicants) at a higher interest rate, etc.


## Table of Contents
* [Python Libraries](#python-libraries)
* [Data Understanding](#data-Understanding)
* [Data Cleaning](#Data-Cleaning)
* [Data Correction](#Data-Correction)
* [Derived Metrics](#Derived-Metrics)
* [Data Filtering](#Data-Filtering)
* [Graph Plotting](#Graph-Plotting)
* 
<!-- You can include any other section that is pertinent to your problem -->

## python-libraries
- To perform the EDA on the given dataset we are using python libraries like
  numpy, pandas, datetime
- For plotting the extracted data on different graphs we will using below libraries
  seaborn, matplotlib, plotly

<!-- You don't have to answer all the questions - just the ones relevant to your project. -->

## Data Understanding
- Shape
  Data set has 39717 rows and 111 features.
- Details
  Dataset has important features which will be considered in this analysis.
  Loan amount, Approved amount, Investor Amount (actual given loan amount), Loan term, Interest rate, Monthly installment amount, Loan Grade and Subgrades,         Borrowers employment title, Employment experience, Home ownership (Own, Rent, Mortgage), Annual Income, Income source verification status, Loan issue date, Loan   status, Purpose of loan, Title of loan, Address state code, Debt to income ratio.
  Apart from above features this dataset also contains the behavioral features like delinquency,  Charged Off with in 12 months etc. These features are not         available at the time of loan approval, so these behavioral features are not considered in this analysis.

<!-- You don't have to answer all the questions - just the ones relevant to your project. -->


## Data Cleaning
- Missing Values
  All the features which has only null values has no significance in this analysis, so need to be dropped from the dataset.
  Also features which has missing values above 60% can create biased results. So these features also need to be dropped from the dataset.
- Unique Values
  The features which has unique values do not have any correlation with other features. So those features need to be dropped from the dataset.
  Zip code has encrypted values so need to be dropped from dataset.
  Desc feature requires NLP to derive useful metrics, it is dropped from dataset for time being.
  Url feature has loan_id as meaning full information, but it is also unique value, so dropped.
- Missing Value Imputation
  The missing values in emp_title are filled with Untitled.
  The missing values in emp_length & title are filled with Unknown.
<!-- As the libraries versions keep on changing, it is recommended to mention the version of library used in this project -->

## Data Correction
- Integer Values
  Term feature converted into data type integer by removing months keyword from data values.
- Float Values
  The interest rate feature converted into float data type by removing `%` sign from the data values.
- Data Deduplication
  There are no duplicate rows found in the dataset.

## Derived Metrics
- Monthly Installment Amount Percentage
  This derived metric will be used to analyze whether this higher percentage is increasing the count of default applications.
  Code :
  loan_df['monthly_inst_percentage'] = (loan_df['installment']/(loan_df['annual_inc']/12))*100
- Binning
  Continuous variable like dti, int_rate & annual_inc are binned to analyze trend with other features.
  Code:
  loan_df['dti_bin'], cut_bin = pd.qcut(loan_df['dti'], q = 15, retbins = True)
  loan_df['ann_inc_bin'], cut_bin = pd.qcut(loan_df['annual_inc'], q = 20, retbins = True)
  loan_df['int_rate_bin'], cut_bin = pd.qcut(loan_df['int_rate'], q = 20, retbins = True)
- Create Continuous Variable
  The feature issue_d converted into continuous feature like month and year.
  loan_df['issue_month'] = loan_df.issue_d.apply(lambda x: int(datetime.strptime(x.split('-')[0], '%b').month))
  loan_df['issue_year'] = loan_df.issue_d.apply(lambda x: int(x.split('-')[1]))
  
## Data Filtering
- Loan status:
  Loan status has 3 values as 'Fully Paid', 'Current', 'Charged Off'.
  Application with loan status as 'current' can turn into any category between 'Fully Paid' or 'Charged Off'.
  So we are filtering out only those two loan status which has certain understanding. And not considering account having loan status as 'Current' in this           analysis. 

## Graph Plotting
- Loan distributed in different types
- Home ownership wise loans
- Monthwise Loans
- Monthwise Verified Loans
- Termwise Verified Loans
- Experience wise Invested Amt
- State wise Investment Loans
- Installment Percentage Vs Dti
- Loan Subgrade And Investment
- Loan purpose & Investment Amount
- Annual Income & Interest Rate

## Contact
Created by [@vaibhav-nk] - feel free to contact me!


<!-- Optional -->
<!-- ## License -->
<!-- This project is open source and available under the [... License](). -->

<!-- You don't have to include all sections - just the one's relevant to your project -->
