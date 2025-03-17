# **Customer Retention & Churn Analysis Using SQL & Power BI **  

## **Overview**  
This project focuses on **customer retention and churn analysis**, leveraging **SQL & Power BI** to model data, optimize **Lifetime Value (LTV), Customer Acquisition Cost (CAC), and maximize Marketing ROI**.  

Understanding retention trends and churn patterns helps businesses improve revenue forecasting, refine marketing strategies, and enhance customer loyalty.  

## **Key Topics Covered**  
- **Retention vs. Churn**: Understanding retention rates and early churn indicators.  
- **LTV, CAC & Marketing ROI**: Analyzing customer value and optimizing acquisition costs.  
- **Data Modeling for Retention Analysis**: Structuring SQL tables to track customer activity.  
- **SQL Transformations**: Creating cohort-based retention analysis.  
- **Retention Calculation in Power BI**: Using DAX to derive percentage retention metrics.  
- **Data Visualization**: Implementing heatmaps and retention curves for insights.  

## **Dataset Structure**  
The dataset includes:  
- **User transactions** (purchase date, spend, product category).  
- **Customer signup data** (first transaction, acquisition source).  
- **Aggregated monthly retention & spend patterns**.  

Each user’s **6-month spending pattern** is analyzed, assigning `nth_month` labels (M0, M1, etc.) to track engagement over time.  

## **Approach**  
1. Extract first transaction dates and assign signup months.  
2. Identify the highest-spent product in the signup month.  
3. Create a structured retention dataset by tracking monthly spending patterns.  
4. Calculate percentage retention using SQL transformations and Power BI.  
5. Visualize results with heatmaps and retention curves to gain actionable insights.  

## **Retention Calculation in Power BI**  
Retention metrics are calculated using **DAX measures** to determine the percentage of users who continue spending over time. This enables tracking of customer engagement and churn trends effectively.  

## **Visualizations**  
- **Heatmap**: Highlights user engagement drop-offs over time.  
- **Retention Curve (Line Chart)**: Compares retention trends across products.  

These visualizations help in understanding **customer stickiness, churn patterns, and upsell opportunities**.  

## **Further Developments**  
- **12-Month Lapse Rule**: Differentiating reactivated users from loyal customers.  
- **Predictive Churn Analysis**: Using Machine Learning (Logistic Regression, Random Forest) to flag at-risk users before they churn.  
- **Marketing Optimization**: Aligning retention, LTV, and CAC for smarter budget allocation.  

## **Let’s Connect!**  
Interested in more insights on **customer retention, SQL analytics, and Power BI visualizations**? Feel free to **⭐ Star** this repository or connect with me on **LinkedIn**!  

🔗 https://www.linkedin.com/in/rajkumarshenigaram/
