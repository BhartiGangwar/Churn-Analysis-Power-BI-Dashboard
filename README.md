# Churn-Analysis-Power-BI-Dashboard
Tools Used
SQL Server (ETL & Data Transformation)
Power BI (Data Cleaning, Modeling, and Visualization)
ML (Random Forest Classifier)



🚀 Project Workflow
🧩 STEP 1 – ETL in SQL Server
1. Data Loading & Exploration:
Created database and imported CSV file into SQL Server.
Checked distinct values and performed exploratory SQL queries:
-- Gender Distribution
SELECT Gender, COUNT(Gender) AS TotalCount,
       COUNT(Gender) * 1.0 / (SELECT COUNT(*) FROM stg_Churn) AS Percentage
FROM stg_Churn
GROUP BY Gender;

-- Contract Type
SELECT Contract, COUNT(Contract) AS TotalCount,
       COUNT(Contract) * 1.0 / (SELECT COUNT(*) FROM stg_Churn) AS Percentage
FROM stg_Churn
GROUP BY Contract;

-- Customer Revenue by Status
SELECT Customer_Status, COUNT(Customer_Status) AS TotalCount,
       SUM(Total_Revenue) AS TotalRev,
       SUM(Total_Revenue) * 1.0 / (SELECT SUM(Total_Revenue) FROM stg_Churn) * 100 AS RevPercentage
FROM stg_Churn
GROUP BY Customer_Status;

-- State-wise Distribution
SELECT State, COUNT(State) AS TotalCount,
       COUNT(State) * 1.0 / (SELECT COUNT(*) FROM stg_Churn) AS Percentage
FROM stg_Churn
GROUP BY State
ORDER BY Percentage DESC;

2. Null Handling:
Checked for null values, removed or replaced where necessary.
Inserted cleaned data into production table prod_Churn.

3. Created Views for Power BI Reporting.

🛠️ STEP 2 – Power BI Transformation
Added Columns:
Churn Status: 1 if Customer_Status = "Churned" else 0
Monthly Charge Range: Categorized charge into bins like <20, 20–50, etc.
Created Reference Tables:
Age Group Mapping:
< 20, 20–35, 36–50, > 50
Added custom sorting column.
Tenure Group Mapping:
<6, 6–12, 12–18, 18–24, >=24 Months
Added custom sorting column.
Services Table:
Used Unpivot to reshape services columns into Service and Status.


📏 STEP 3 – Power BI Measures
Total Customers = COUNT(prod_Churn[Customer_ID])
New Joiners = CALCULATE(COUNT(Customer_ID), Customer_Status = "Joined")
Total Churn = SUM(prod_Churn[Churn Status])
Churn Rate = [Total Churn] / [Total Customers]

📊 STEP 4 – Visualization
Created interactive Power BI visuals including:
Gender & State-wise churn
Tenure and Monthly Charges
Revenue contribution
Churn rate KPIs


STEP 5 – Predict Customer Churn
 Data Preparation for ML model
 Let us first import views in an Excel file.
o   Go to Data >> Get Data >> SQL Server Database
o   Enter the Server Name & Database name to connect to SQL Server
o   Import both vw_ChurnData & vw_JoinData
o   Save the file as Prediction_Data
Create Churn Prediction Model – Random Forest








    












