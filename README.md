# 📊 Churn Analysis Power BI Dashboard

This project focuses on a full-stack data workflow to analyze and predict customer churn. It combines **SQL Server** for robust data handling, **Power BI** for dynamic visualizations, and **Machine Learning** (Random Forest Classifier) for predictive insights. The goal is to uncover churn patterns, create a detailed dashboard, and build a model that helps identify and predict potential churners.

---

### 🛠️ Tools & Technologies

* **SQL Server:** ETL (Extract, Transform, Load), data cleansing, and view creation.
* **Power BI:** Data cleaning, modeling, DAX measures, and interactive visualization.
* **Machine Learning (Python):** Random Forest Classifier for churn prediction.

---

### 🚀 Project Workflow

#### 📍 STEP 1: ETL in SQL Server

The initial phase involved preparing the raw data within SQL Server.

* **Data Loading & Exploration:** Imported raw CSV data into a staging table (`stg_Churn`) and performed initial SQL queries to understand gender distribution, contract types, revenue by churn status, and state-wise breakdowns.
* **Null Handling:** Checked for and handled null values to ensure data quality. Cleaned data was then loaded into a production table (`prod_Churn`).
* **Views Creation:** Created reusable SQL views (`vw_ChurnData`, `vw_JoinData`) to serve as a clean, reliable data source for both Power BI reporting and machine learning modeling.

#### 📊 STEP 2: Power BI Data Transformation

Data was further refined in Power BI to enhance analytical capabilities.

* **Added New Columns:**
    * **Churn Status:** A binary flag (`1` for "Churned", `0` otherwise).
    * **Monthly Charge Range:** Categorized monthly charges into logical bins (e.g., `<20`, `20–50`, `>50`).
* **Reference Tables for Grouping:** Created separate tables to map `Age` and `Tenure` into predefined groups (e.g., `20–35`, `36–50` and `6–12 months`, `12–18 months`) for consistent sorting and filtering.

#### 📐 STEP 3: Power BI DAX Measures

Custom DAX measures were created to derive meaningful business insights and key metrics.

* `Total Customers = COUNT(prod_Churn[Customer_ID])`
* `Total Churn = SUM(prod_Churn[Churn Status])`
* `Churn Rate = [Total Churn] / [Total Customers]`
* `New Joiners = CALCULATE(COUNT(Customer_ID), Customer_Status = "Joined")`

---

### 📈 STEP 4: Dashboard & Visualization

An interactive Power BI dashboard was built to visualize churn trends and key metrics.

**Dashboard View:**
![Dashboard View](https://github.com/BhartiGangwar/Churn-Analysis-Power-BI-Dashboard/blob/main/DemoScreenshot.png?raw=true)

---

### 🤖 STEP 5: Churn Prediction using Machine Learning

A predictive model was developed to forecast which customers are at risk of churning.

* **Data Preparation:** Exported SQL views to a CSV file (`Prediction_Data.csv`) to use as the input for the machine learning model.
* **Model Building:** Used a **Random Forest Classifier** to train a predictive model based on various customer attributes.

---

### 📊 STEP 6: Visualization of Predicted Data

The model's predictions were integrated back into Power BI to create a second, forward-looking dashboard.

**Prediction Dashboard View:**
![Prediction Dashboard View](https://github.com/BhartiGangwar/Churn-Analysis-Power-BI-Dashboard/blob/main/ChurnAnalysis_prediction.png?raw=true)

* **Predicted Churners:** A new measure, `Count Predicted Churner`, was created to count the customers identified as likely to churn by the model.

---

### 📌 Key Takeaways

* **Comprehensive Approach:** This project effectively combines descriptive analytics (the dashboard) with predictive analytics (the ML model) for a holistic understanding of customer churn.
* **Clear Workflow:** It demonstrates a clear, end-to-end data workflow from raw data to actionable business insights.
* **Scalable Solution:** The integrated model provides a scalable and interpretable solution for proactive customer retention strategies.






    












