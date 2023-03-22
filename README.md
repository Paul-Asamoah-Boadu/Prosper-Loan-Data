<h1>Prosper Loan Data Exploration</h1>
<h2>By Paul Boadu Asamoah</h2>


<h2>Dataset</h2>
<a id="intro"></a>
<h2>Introduction</h2>
Prosper is a peer-to-peer lending platform that connects borrowers with lenders. It allows borrowers to request loans up to $40,000 and investors to invest as little as $25 per loan. Prosper uses a proprietary algorithm to determine a credit rating for borrowers and assign interest rates to loans.

The dataset provided includes information on loan listings on the Prosper platform between `2005` and `2014`. The dataset has `113,937 listings` and `81 columns`. Some of the important columns in the dataset include the loan amount, interest rate, borrower's credit score, employment status, income, and loan status.

Other variables in the dataset, such as Prosper rating, estimated loss, estimated return, group affiliation, credit utilization, and credit inquiries, can be analyzed to learn more about the borrower's creditworthiness and borrowing habits. 

<a id="wrangling"></a>
<h2>Data Wrangling</h2>

<a id="gathering"></a>
<h3>Data Gathering</h3>

The prosper loan dataset was manually downloaded and loaded as `prosperLoanData.csv` using pd.read_csv with the extension ".csv," and was assigned to a variable df.

__Assessing Data__

Programmatic assessment were used to assess the data. Which was carried out using the following Pandas and Numpy methods:


`.shape`

`.info()`

`.value_counts()`

`.loc`, `.iloc`

`.isna(), .isnull()`

`.sum()`

`.sample()`

`.nunique()`

`.head()`

`.tail()`


Some __quality issues__ in the datasets were found during the data review. Here are several problems with the quality.

- Rename `ProsperRating (Alpha)` and `ListingCategory (numeric)` column by move (Alpha) and (numeric) respectively.
- Change datatype of `LoanOriginationDate` from object to Pandas datetime.
- Change datatype of `Term`, `LoanStatus`, `ProsperRating (Alpha)`, `BorrowerState`, `IncomeRange`, `EmploymentStatus` categorical.
- Replace the values of `ListingCategory (numeric)` to its actual names and change the datatype to categorical.
- Drop all missing values.

__Data Cleaning__

The important columns were extracted from the original dataset, resulting in a new dataset with 113,937 rows and 20 columns. 

To eliminate missing values, entries before June 2009 were dropped, leaving the dataset with 76,216 rows and 20 columns.

Additionally, column names like `ProsperRating (Alpha)` and `ListingCategory (numeric)` were changed to `ProsperRating` and `ListingCategory`, respectively. 

Data types for Term, LoanStatus, ProsperRating, BorrowerState, IncomeRange, and EmploymentStatus were changed to categorical, while LoanOriginationDate was converted to a Pandas datetime. 

`ListingCategory (numeric)` values were replaced with their actual names and then changed to categorical data type.


## Summary of Findings

It was discovered there has been a continueous increase from June 2019 to late 2012 in monthly loan payment over loan origination date till a decrease set in from late 2012 to early 2013. Following this drop, payments increased sharply from 25,000 to 180,000 between 2013 and 2014, followed by another drop.

The analysis revealed that the evolution of a company's loan terms, highlighting the addition of 12-month and 60-month terms in 2010, in addition to the initial 36-month term. Interestingly, there has been a significant and steady increase in monthly loan payments since the introduction of the 12-month term, which has continued until 2013. From 2009 to the present, the 36-month term has also seen consistent increases in loan payments. The 60-month term, on the other hand, initially saw a 100-dollar decrease in monthly loan payments shortly after its introduction in 2012, but has since seen a slow and steady rise, with current monthly loan payments hovering around 350 dollars.

Additionally, the ProsperRating and IsBorrowerHomeowner distribute a sizable proportion of borrowers rated C, with a relatively even split between those who own a home and those who do not. Borrowers with an A credit score are more common, with a higher percentage owning a home. Borrowers with an AA credit rating are relatively uncommon, and the majority own a home.

The analysis summarizes the Borrower APR and maximum loan amount across different Prosper ratings. Borrowers with an A rating generally have low Borrower APR and higher loan amounts while borrowers with AA ratings have the lowest APR and a maximum loan limit of 25,000 dollars. The Borrower APR for B and C rating borrowers ranges from 0.07 to 0.3, with a maximum loan limit of 25,000 dollars. However, D rating borrowers have higher Borrower APR compared to other ratings. E and HR ratings have the highest Borrower APR and lowest maximum monthly income, with HR borrowers having a high debt-to-income ratio.


## Key Insights for Presentation

The investigation concentrated on the borrower's loan status. By investigating the ProsperRating in relation to homeowners, I learned a lot about the nature of the borrowers. 

Following that, I plotted the trend of monthly loan payment vs term of payment over the years. FacetGrid was used to further analyse the relationship between loan original amount and monthly loan payment versus employment status. 
These analyses helped me understand the loan trend and the borrowers' creditworthiness.
