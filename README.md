# 📊 Customer Churn Analysis Dashboard

<div align="center">

**SQL Server | Power BI | Machine Learning**

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![SQL Server](https://img.shields.io/badge/SQL_Server-CC2927?style=for-the-badge&logo=microsoft-sql-server&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)

</div>

---

## 🎯 Project Overview

This project analyzes customer churn patterns using **SQL Server** for data processing, **Power BI** for visualization, and **Machine Learning** (Random Forest) for prediction. The goal is to identify churned customers and predict future churners to support retention strategies.

---

## 🛠️ Tools Used

- **SQL Server** - Data cleaning and transformation
- **Power BI** - Dashboard creation and DAX measures
- **Python** - Random Forest Classifier for predictions

---

## 📋 Workflow

### **Step 1: SQL Server - Data Preparation**

- Loaded raw data into staging table `stg_Churn`
- Cleaned data and handled null values
- Created production table `prod_Churn`
- Built SQL views `vw_ChurnData` and `vw_JoinData`

### **Step 2: Power BI - Data Transformation**

**New Columns Added:**
- **Churn Status** - Binary flag (1 = Churned, 0 = Active)
- **Monthly Charge Range** - Categorized as <20, 20-50, 50-100, >100

**Reference Tables Created:**
- Age Groups: 20-35, 36-50, 51-65, 66+
- Tenure Groups: <6 months, 6-12 months, 12-18 months, 24+ months

### **Step 3: Power BI - DAX Measures**

```dax
Total Customers = COUNT(prod_Churn[Customer_ID])

Total Churn = SUM(prod_Churn[Churn Status])

Churn Rate = DIVIDE([Total Churn], [Total Customers])

New Joiners = CALCULATE(COUNT(prod_Churn[Customer_ID]), 
              prod_Churn[Customer_Status] = "Joined")
```

### **Step 4: Dashboard Visualization**

<div align="center">

![Dashboard View](https://github.com/BhartiGangwar/Churn-Analysis-Power-BI-Dashboard/blob/main/DemoScreenshot.png?raw=true)

</div>

**Dashboard Features:**
- Total customers and churn rate
- Churn analysis by gender, contract type, and state
- Revenue breakdown by churn status
- Monthly charge distribution

### **Step 5: Machine Learning - Churn Prediction**

- Exported data from SQL views to CSV
- Built **Random Forest Classifier** model
- Trained model on customer attributes
- Generated predictions for at-risk customers

### **Step 6: Prediction Dashboard**

<div align="center">

![Prediction Dashboard](https://github.com/BhartiGangwar/Churn-Analysis-Power-BI-Dashboard/blob/main/ChurnAnalysis_prediction.png?raw=true)

</div>

**New Measure Created:**
```dax
Count Predicted Churner = CALCULATE(COUNT(prod_Churn[Customer_ID]), 
                          prod_Churn[Predicted_Churn] = 1)
```

---

## 🎯 Key Insights

| Insight | Description |
|---------|-------------|
| **Descriptive Analytics** | Historical dashboard showing actual churn patterns |
| **Predictive Analytics** | ML model identifying customers likely to churn |
| **Actionable Data** | Clear visualizations for retention strategies |
| **End-to-End Solution** | Complete workflow from raw data to predictions |

---

## 📌 Project Highlights

✅ Complete ETL process in SQL Server  
✅ Interactive Power BI dashboards with custom DAX  
✅ Machine Learning integration for predictions  
✅ Two dashboards: Historical analysis + Future predictions  
✅ Scalable solution for business use  

---


<div align="center">


</div>





