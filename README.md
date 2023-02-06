# Customer Lifetime Value (CLV)

Please note that this analysis was originally inspired by an article on gormanalysis.com. The data set and outline for this project was provided by David Steier of Carnegie Mellon University.

Gormanalysis.com informs us that, "CLV is an estimation of the entire net profit attributed to a single customer. It's an important metric to understand because it helps businesses determine how much is too much to spend on advertising to acquire a single customer." 

The following analysis will demonstrate one method of calculating CLV. 

## Step 1: Understanding the data set

To begin, I looked for missingness, date ranges for the transactions, unique number of customers, produced descriptive statistics for the amount field, and checked if the amount spent increased or decreased over time. 

## Step 2: Exploring the data set

In this step, a box plot, scatter plot, and histogram were used in examining the amount field. There were several outliers in the data set that needed to be removed.

During this phase, two methods were considered:
1. Median imputation
2. Isolation forest

Ultimately the solution employed an isolation forest with hyper-parameter tuning.

<img src="./Static/Amount_Histograms.png" alt="drawing" width="550"/>

## Step 3: Determining the origin year of customers

To determine the origin year of customers, the solution utilized the pandas group by function. The records were group by customer ID and minimum of the transaction year. 

## Step 4: Calculating cumulative transaction amounts by origin year

The table rows show the cumulative amount by customer origin year

<img src="./Static/Step4.png" alt="drawing" width="550"/>

## Step 5: Calculating cumulative transaction amounts by new customers by origin year in each year

The table row shows the number of customers acquired in a origin year 

<img src="./Static/Step5.png" alt="drawing" width="550"/>

## Step 6: Calculating the historic CLV

This table essentially divides Step 4 by Step 5 to get the historic average CLV. The chart below shows the CLV for different origin years and their CLVs over the customer's lifetime.

<img src="./Static/CLV_Curve.png" alt="drawing" width="550"/>

## Step 7: Interpreting the results

Looking at the CLV chart curves, can expect new customers to have similar top line revenue into the future. Analysts can use historical trends to forecast into the future with reasonable accuracy, all else equal. 

One call-out is that for the 12 months category, there is a decrease in historic CLV, evidenced by the decrease for $12 to $10. 
