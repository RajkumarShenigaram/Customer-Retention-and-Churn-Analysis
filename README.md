# Customer Retention & Churn Analysis Using SQL & Power BI  

## 📌 Overview  
This project focuses on **customer retention and churn analysis**, leveraging **SQL & Power BI** to model data, optimize Lifetime Value (**LTV**), Customer Acquisition Cost (**CAC**), and maximize **Marketing ROI**.  

Understanding retention trends and churn patterns helps businesses improve revenue forecasting, refine marketing strategies, and enhance customer loyalty.  

---

## 🔍 Key Topics Covered  
- **Retention vs. Churn**: Understanding retention rates and early churn indicators.  
- **LTV, CAC & Marketing ROI**: Analyzing customer value and optimizing acquisition costs.  
- **Data Modeling for Retention Analysis**: Structuring SQL tables to track customer activity.  
- **SQL Transformations**: Creating cohort-based retention analysis.  
- **Retention Calculation in Power BI**: Using **DAX** to derive percentage retention metrics.  
- **Data Visualization**: Implementing heatmaps and retention curves for insights.  

---

## 📊 Dataset Structure  
The dataset contains:  
- **User transactions** (purchase date, spend, product category).  
- **Customer signup data** (first transaction, acquisition source).  
- **Aggregated monthly retention & spend patterns**.  

Each user’s **6-month spending pattern** is analyzed, assigning `nth_month` labels (M0, M1, etc.) to track engagement over time.  

---

## 🛠️ SQL Implementation Steps  
### 1️⃣ Cohort Creation  
Extracting first sale dates and assigning `signup_month`:  
```sql
WITH users_signup_month AS (
  SELECT 
   user_id, 
   MIN(sale_date) AS first_sale_date, 
   DATE_TRUNC('month', MIN(sale_date)) AS signup_month
  FROM sales_data
  GROUP BY user_id
)
SELECT * FROM users_signup_month;
