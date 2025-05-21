📊 Churn Analysis Power BI Dashboard

This project focuses on analyzing and predicting customer churn using a full-stack data workflow including SQL Server, Power BI, and Machine Learning (Random 

Forest Classifier). The goal is to uncover churn patterns, create an insightful dashboard, and build a model that helps predict churners.

🛠️ Tools & Technologies

SQL Server – ETL (Extract, Transform, Load), data cleansing, and view creation

Power BI – Data cleaning, modeling, DAX measures, and visualization

Machine Learning – Random Forest Classifier for churn prediction

🚀 Project Workflow

📍 STEP 1 – ETL in SQL Server

Data Loading & Exploration

Imported raw CSV data into a SQL Server staging table (stg_Churn)

Performed SQL queries for initial analysis:

Gender Distribution

Contract Type Breakdown

Customer Revenue by Churn Status

State-wise Distribution

Null Handling

Checked and handled nulls

Cleaned data was inserted into a production table (prod_Churn)

Views Creation

Created SQL views (vw_ChurnData, vw_JoinData) for Power BI reporting and ML modeling

📊 STEP 2 – Power BI Data Transformation

Added New Columns

Churn Status: 1 if Customer_Status = "Churned", else 0

Monthly Charge Range: Binned into categories like <20, 20–50, >50, etc.

Reference Tables for Grouping

Age Group Mapping: <20, 20–35, 36–50, >50

Tenure Group Mapping: <6, 6–12, 12–18, 18–24, >=24 months

Used custom sorting columns for correct ordering

Services Table

Used Unpivot to convert service columns into a normalized Service-Status format

📐 STEP 3 – Power BI DAX Measures

Defined custom DAX measures for meaningful insights:

Total Customers = COUNT(prod_Churn[Customer_ID])

New Joiners = CALCULATE(COUNT(Customer_ID), Customer_Status = "Joined")

Total Churn = SUM(prod_Churn[Churn Status])

Churn Rate = [Total Churn] / [Total Customers]

📈 STEP 4 – Dashboard & Visualization

Built an interactive Power BI dashboard with:

Gender-wise and State-wise Churn Breakdown

Monthly Charges & Tenure Distribution

Revenue Contribution by Customer Status

Key Metrics and KPIs on Churn Rate, Total Customers, etc.

📸 Add a screenshot of the main Power BI dashboard here
![Dashboard View](screenshots/powerbi_dashboard.png)

🤖 STEP 5 – Churn Prediction using ML (Random Forest)

Data Preparation

Exported SQL views (vw_ChurnData, vw_JoinData) to Excel using Power BI's SQL Server connection

Saved data as Prediction_Data.xlsx

Model Building

Used Random Forest Classifier to predict churn based on customer attributes

Evaluated accuracy and feature importance

![ML Model](screenshots/ml_model_metrics.png)

📂 Project Structure

Churn-Analysis-Power-BI-Dashboard/

├── SQL_Scripts/

│   └── ETL_and_Queries.sql

├── PowerBI_Dashboard/

│   └── Churn_Analysis.pbix

├── ML_Model/

│   └── churn_prediction_random_forest.ipynb

├── Prediction_Data.xlsx

├── README.md

└── Screenshots

📌 Key Takeaways

Combines descriptive (dashboard) and predictive (ML model) analytics

Clear workflow from raw data to business insights

Scalable and interpretable model for customer churn prediction











    












