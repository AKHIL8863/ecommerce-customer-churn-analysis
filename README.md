# 📊 Customer Churn Analysis using SQL

## 📌 Project Overview
This project focuses on analyzing customer churn behavior using SQL. It includes data cleaning, transformation, and exploratory data analysis to extract meaningful business insights.

## 🎯 Objectives
- Identify churned customers
- Understand factors influencing churn
- Analyze customer behavior patterns

## 🛠 Tools Used
- MySQL
- SQL (Joins, Aggregations, Subqueries)

---

## 🧹 Data Cleaning
- Handled NULL values using AVG and MODE
- Removed outliers (WarehouseToHome > 100)
- Standardized inconsistent values (COD → Cash on Delivery)

---

## 🔄 Data Transformation
- Renamed columns for clarity
- Created new columns:
  - ComplaintReceived (Yes/No)
  - ChurnStatus (Churned/Active)
- Dropped unnecessary columns

---

## 📊 Key Analysis Performed

### 1. Customer Distribution
- Count of churned vs active customers

### 2. Complaint Impact
- % of churned customers who raised complaints

### 3. Payment Behavior
- Most used payment method by active users

### 4. Distance Impact
- Categorized customers based on distance:
  - Very Close
  - Close
  - Moderate
  - Far

### 5. Customer Segmentation
- Based on City Tier, Gender, Marital Status

### 6. Advanced Analysis
- Subqueries
- Aggregations
- INNER JOIN with returns table

---

## 🔍 Sample Query

```sql
SELECT 
    CASE 
        WHEN WarehouseToHome <= 5 THEN 'Very Close Distance'
        WHEN WarehouseToHome <= 10 THEN 'Close Distance'
        WHEN WarehouseToHome <= 15 THEN 'Moderate Distance'
        ELSE 'Far Distance'
    END AS DistanceCategory,
    ChurnStatus,
    COUNT(*) AS Customer_Count
FROM customer_churn
GROUP BY DistanceCategory, ChurnStatus;
