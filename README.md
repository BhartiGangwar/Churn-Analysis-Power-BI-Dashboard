# 🎯 Customer Churn Analysis & Prediction

<div align="center">

**End-to-End Analytics Solution: SQL Server + Power BI + Machine Learning**

[![SQL Server](https://img.shields.io/badge/SQL%20Server-CC2927?style=flat-square&logo=microsoft-sql-server&logoColor=white)](https://www.microsoft.com/sql-server)
[![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat-square&logo=power-bi&logoColor=black)](https://powerbi.microsoft.com/)
[![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![ML](https://img.shields.io/badge/Random%20Forest-00979D?style=flat-square)](https://scikit-learn.org/)

</div>

---

## 📖 Overview

A comprehensive churn analysis system combining **descriptive analytics** (historical trends) and **predictive analytics** (ML-based forecasting) to identify at-risk customers and enable proactive retention strategies.

---

## 🛠️ Tech Stack

| Component | Purpose |
|-----------|---------|
| **SQL Server** | ETL pipeline, data cleansing, view creation |
| **Power BI** | Interactive dashboards, DAX measures, data modeling |
| **Python ML** | Random Forest Classifier for churn prediction |

---

## 🚀 Project Workflow

### **1️⃣ SQL Server: Data Engineering**
- Loaded raw data into staging table (`stg_Churn`)
- Performed data quality checks and null handling
- Created production table (`prod_Churn`) and reusable views (`vw_ChurnData`, `vw_JoinData`)

### **2️⃣ Power BI: Data Modeling**
**Added Calculated Columns:**
- `Churn Status`: Binary flag (1 = Churned, 0 = Active)
- `Monthly Charge Range`: Categorized billing (<20, 20-50, 50-100, >100)

**Created Reference Tables:**
- Age Groups (20-35, 36-50, 51-65, 66+)
- Tenure Buckets (<6m, 6-12m, 12-18m, 18-24m, 24m+)

### **3️⃣ Key DAX Measures**

```dax
Total Customers = COUNT(prod_Churn[Customer_ID])
Total Churn = SUM(prod_Churn[Churn Status])
Churn Rate = DIVIDE([Total Churn], [Total Customers], 0)
New Joiners = CALCULATE(COUNT(prod_Churn[Customer_ID]), prod_Churn[Customer_Status] = "Joined")
```

### **4️⃣ Historical Analytics Dashboard**

<div align="center">

![Dashboard](https://github.com/BhartiGangwar/Churn-Analysis-Power-BI-Dashboard/blob/main/DemoScreenshot.png?raw=true)

</div>

**Key Features:**
- 📊 KPIs: Total customers, churn rate, revenue metrics
- 🔍 Dimensional analysis: Demographics, contract types, geography
- 💰 Financial impact tracking
- 🎛️ Interactive filters and slicers

### **5️⃣ Machine Learning Pipeline**

**Model:** Random Forest Classifier

**Process:**
1. Exported SQL views for model training
2. Feature engineering and selection
3. Model training with hyperparameter tuning
4. Generated predictions on customer base

**Top Churn Drivers:**
- Contract type
- Tenure duration
- Monthly charges
- Service usage patterns

### **6️⃣ Predictive Analytics Dashboard**

<div align="center">

![Prediction Dashboard](https://github.com/BhartiGangwar/Churn-Analysis-Power-BI-Dashboard/blob/main/ChurnAnalysis_prediction.png?raw=true)

</div>

**Features:**
- 🎯 Count of predicted churners
- 📈 Risk segmentation (High/Medium/Low)
- 💼 Targeted retention recommendations
- 📊 Model performance tracking

---

## 💡 Key Outcomes

<table>
<tr>
<td align="center" width="33%">
<h3>🔍</h3>
<b>Early Detection</b>
<br>Identify at-risk customers before they churn
</td>
<td align="center" width="33%">
<h3>📊</h3>
<b>Data-Driven Insights</b>
<br>Interactive dashboards for strategic decisions
</td>
<td align="center" width="33%">
<h3>💰</h3>
<b>Revenue Protection</b>
<br>Proactive retention strategies
</td>
</tr>
</table>

---

## 🎓 Project Highlights

✅ **End-to-end pipeline** from raw data to actionable insights  
✅ **Dual analytics approach:** Historical + Predictive  
✅ **Scalable architecture** ready for production deployment  
✅ **Business impact:** Quantifiable ROI on customer retention  

---

## 📧 Connect

**Bharti Gangwar** | [GitHub](https://github.com/BhartiGangwar) | [LinkedIn](https://www.linkedin.com/in/bhartigangwar)

---

<div align="center">

⭐ **Star this repo if you find it helpful!** ⭐

![Visitors](https://visitor-badge.laobi.icu/badge?page_id=BhartiGangwar.Churn-Analysis)

</div>








