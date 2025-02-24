# Credit_Card_Financial_Dashboard
## 📊 Credit Card Transaction & Customer Dashboard

## 📌 Overview
The **Credit Card Transaction and Customer Dashboard** is designed to analyze key metrics related to credit card transactions, customer spending behavior, and financial performance. This interactive dashboard provides actionable insights into revenue patterns, transaction trends, and customer demographics.

## 🚀 Features
✅ **Transaction Analysis**: Track total revenue, transaction count, and total interest earned.  
✅ **Customer Segmentation**: Identify trends based on age, income group, education, and occupation.  
✅ **Expenditure Insights**: Understand customer spending on various categories such as bills, travel, groceries, and entertainment.  
✅ **Card Category Performance**: Compare revenue contributions from different card categories—Blue, Gold, Silver, and Platinum.  
✅ **Time-Based Trends**: Monitor revenue fluctuations across weeks and quarters.  
✅ **Refund & Delayed Transactions**: Gain insights into refund patterns and delivery delays.

## 🛠️Dax Formulas Used are:
## 1. Current Week Revenue
```DAX
Current_Week_Revenue = CALCULATE(
    SUM('public cc_detail'[Revenue]),
    FILTER(
        ALL('public cc_detail'),
        'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])
    )
)
```

## 2. Previous Week Revenue
```DAX
Previous_Week_Revenue = CALCULATE(
    SUM('public cc_detail'[Revenue]),
    FILTER(
        ALL('public cc_detail'),
        'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2]) - 1
    )
)
```

## 3. Age Group Classification
```DAX
AgeGroup = SWITCH(TRUE(),
    'public cust_detail'[customer_age] < 30, "20-30",
    'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
    'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
    'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
    'public cust_detail'[customer_age] >= 60, "60+",
    "unknown"
)
```

## 4. Week-over-Week Revenue Change
```DAX
WOW_Revenue = DIVIDE(( [Current_Week_Revenue] - [Previous_Week_Revenue] ), [Previous_Week_Revenue])
```

## 5. Week Number Calculation
```DAX
week_num2 = WEEKNUM('public cc_detail'[week_start_date])
```

## 6. Revenue Calculation
```DAX
Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]
```

## 7. Income Group Classification
```DAX
IncomeGroup = SWITCH(
    TRUE(),
    'public cust_detail'[income] < 35000, "Low",
    'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] < 70000, "Medium",
    'public cust_detail'[income] >= 70000, "High",
    "unknown"
)
```
## 📈 Key Metrics
- **Total Revenue**: ₹57M
- **Total Interest Earned**: ₹8M
- **Total Transactions**: 667K
- **Average Order Value (AOV)**: ₹501.4
- **Return Rate**: 10% (mostly due to stale or damaged products)
- **Top-Selling Categories**: Dairy and Beverages (35% of total sales)

## 📊 Visual Breakdown
### 🔹 Transaction Report
- **Quarterly Revenue & Transaction Count**: Shows revenue trends across Q1 to Q4.
- **Revenue by Card Category**: Displays earnings from Blue, Gold, Silver, and Platinum cards.
- **Expenditure Analysis**: Breakdown of customer spending by categories (bills, travel, groceries, fuel, etc.).

### 🔹 Customer Report
- **Revenue by Age Group**: Helps identify which age segments contribute most to spending.
- **Revenue by Marital Status & Income Group**: Segments customer behavior based on financial background.
- **Top 5 States**: Geographical revenue distribution.

## 🎯 Business Impact
🔹 Enhanced customer insights for targeted marketing strategies.  
🔹 Improved transaction security by monitoring spending trends.  
🔹 Optimized financial forecasting for better decision-making.  
🔹 Increased customer engagement through tailored credit card offers.  

## 🛠️ Tools Used
- **Power BI**: For data visualization and dashboard creation.
- **SQL**: For data extraction and transformation.
- **Excel**: For pre-processing and analysis.

## 📥 How to Use
1. Open the Power BI dashboard.
2. Use filters to explore trends by quarter, card type, and customer demographics.
3. Gain valuable insights to drive business decisions.

📌 *Stay ahead in financial analytics with data-driven insights!* 🚀

