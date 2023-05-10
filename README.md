# Lending Club
> The given dataset contains the loan deatils of the lending company from 2007 to 2011. The data given in dataset contains information about past loan applicants and whether they ‘defaulted’ or not. The aim is to identify patterns which indicate if a person is likely to default, which may be used for taking actions such as denying the loan, reducing the amount of loan, lending (to risky applicants) at a higher interest rate, etc.


## Table of Contents
* [Python Libraries](#python-libraries)
* [Data Understanding](#data-Understanding)
* [Data Cleaning](#Data-Cleaning)
* [Data Correction](#Data Correction)

* [General Info](#general-information)
* [Technologies Used](#technologies-used)
* [Conclusions](#conclusions)
* [Acknowledgements](#acknowledgements)
* [General Info](#general-information)
* [Technologies Used](#technologies-used)
* [Conclusions](#conclusions)
* [Acknowledgements](#acknowledgements)

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
Give credit here.
- Integer Values
  Term feature converted into data type integer by removing months keyword from data values.
- Float Values
  The interest rate feature converted into float data type by removing `%` sign from the data values.
- Data Deduplication
  There are no duplicate rows found in the dataset.


## Contact
Created by [@githubvaibhav-nk] - feel free to contact me!


<!-- Optional -->
<!-- ## License -->
<!-- This project is open source and available under the [... License](). -->

<!-- You don't have to include all sections - just the one's relevant to your project -->
