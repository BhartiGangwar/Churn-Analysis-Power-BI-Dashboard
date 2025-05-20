# Churn-Analysis-Power-BI-Dashboard
what i did 
STEP 1 – ETL Process in SQL Server
Creating Database
Import csv into SQL server 
Apply sql query
Data Exploration – Check Distinct Values
1.SELECT Gender, Count(Gender) as TotalCount,
Count(Gender)  1.0 / (Select Count() from stg_Churn)  as Percentage
from stg_Churn
Group by Gender

2.SELECT Contract, Count(Contract) as TotalCount,
Count(Contract)  1.0 / (Select Count() from stg_Churn)  as Percentage
from stg_Churn
Group by Contract

3.SELECT Customer_Status, Count(Customer_Status) as TotalCount, Sum(Total_Revenue) as TotalRev,
Sum(Total_Revenue) / (Select sum(Total_Revenue) from stg_Churn) * 100  as RevPercentage
from stg_Churn
Group by Customer_Status

4.SELECT State, Count(State) as TotalCount,
Count(State)  1.0 / (Select Count() from stg_Churn)  as Percentage
from stg_Churn
Group by State
Order by Percentage desc

Check Nulls
Remove null and insert the new data into Prod table


 Create View for Power BI
 STEP 2 – Power BI Transform

1. Add a new column in prod_Churn
   
      Churn Status = if [Customer_Status] = “Churned” then 1 else 0
      Change Churn Status data type to numbers
      Monthly Charge Range = if [Monthly_Charge] < 20 then “< 20” else if [Monthly_Charge] < 50 
      then “20-50” else if [Monthly_Charge] < 100 then “50-100” else “> 100”
   
2.Create a New Table Reference for mapping_AgeGrp
      Keep only Age column and remove duplicates
      Age Group = if [Age] < 20 then “< 20” else if [Age] < 36 then “20 – 35” else if [Age] < 
      51 then “36 – 50” else “> 50”
     AgeGrpSorting = if [Age Group] = “< 20” then 1 else if [Age Group] = “20 – 35” then 2 else 
     if [Age Group] = “36 – 50” then 3 else 4
     Change data type of AgeGrpSorting to Numbers
     
3.Create a new table reference for mapping_TenureGrp
     Keep only Tenure_in_Months and remove duplicates
    Tenure Group = if [Tenure_in_Months] < 6 then “< 6 Months” else if [Tenure_in_Months] < 12 
    then “6-12 Months” else if [Tenure_in_Months] < 18 then “12-18 Months” else if 
    [Tenure_in_Months] < 24 then “18-24 Months” else “>= 24 Months”
    TenureGrpSorting = if [Tenure_in_Months] = “< 6 Months” then 1 else if [Tenure_in_Months] =  
    “6-12 Months” then 2 else if [Tenure_in_Months] = “12-18 Months” then 3 else if 
    [Tenure_in_Months] = “18-24 Months ” then 4 else 5
    Change data type of TenureGrpSorting  to Numbers

4.Create a new table reference for prod_Services

  Unpivot services columns
   Rename Column – Attribute >> Services & Value >> Status

STEP 3 – Power BI Measure
  Total Customers = Count(prod_Churn[Customer_ID])

  New Joiners = CALCULATE(COUNT(prod_Churn[Customer_ID]), prod_Churn[Customer_Status] = “Joined”)

 

  Total Churn = SUM(prod_Churn[Churn Status])

  Churn Rate = [Total Churn] / [Total Customers]
  
  STEP 4 – Power BI Visualization

STEP 5 – Predict Customer Churn
 

Data Preparation for ML model

Let us first import views in an Excel file.

o   Go to Data >> Get Data >> SQL Server Database

o   Enter the Server Name & Database name to connect to SQL Server

o   Import both vw_ChurnData & vw_JoinData

o   Save the file as Prediction_Data
Create Churn Prediction Model – Random Forest








    












