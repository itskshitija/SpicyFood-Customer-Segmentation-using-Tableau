![25553c40-cf0a-43da-93d7-97eec0f8048c](https://github.com/user-attachments/assets/4c8aec06-e55c-466c-9d46-6c9dfa8cdbdd)

# 😋SpicyFood - Customer Segmentation: RFM Analysis using Tableau


## Checkout my medium article [Here](https://medium.com/@kshitijachilbule2/spicyfood-exploring-customer-segmentation-with-a-tableau-dashboard-1167eed99ca2)

## Overview
This project focuses on creating a Customer Segmentation Dashboard for SpicyFood Management using Tableau. The goal is to classify customers into meaningful segments based on their purchasing behavior and demographics, enabling the business to make informed, data-driven decisions.

Using the RFM (Recency, Frequency, Monetary) model, customers are grouped into categories such as Champions, Loyal Customers, Potential Loyalists, Promising, and At Risk, among others. These segments provide insights into customer value, engagement, and retention opportunities.

The analysis incorporates factors like age, customer tiers, and average bill per customer to better understand customer patterns. The provided dataset includes essential details like Customer ID, Purchase Frequency, Bill Amount, Recency, and other relevant attributes.

The final Tableau dashboard delivers an interactive and visually appealing representation of these insights, helping SpicyFood Management to:
- Identify high-value customers.
- Re-engage at-risk customers.
- Enhance retention strategies.
- Optimize marketing campaigns.

## 📌Introduction
This project involves **RFM Analysis (Recency, Frequency, and Monetary)** to segment customers based on their purchase behavior and provide actionable insights for better business decisions. The analysis is visualized using an interactive **Tableau Dashboard**.

## [View My Tableau Dashboard](https://public.tableau.com/views/Kshitija_SpicyFood_Dashboard1_6/Dashboard?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)

### 📊Dashboard Preview
![Dashboard](https://github.com/user-attachments/assets/b7eed9cd-73c2-463e-a880-4ca653fdc91a)

## 🔠Dataset Description
The dataset used for this analysis includes the following fields:
- **Customer ID**: Unique identifier for each customer.
- **Purchase Frequency**: The number of purchases a customer makes.
- **Bill Amount**: Total monetary value spent by the customer.
- **Recent Purchase Date**: The customer’s latest purchase date.
- **Rank_Recency**: Ranking based on the recency of purchases.
- **Rank_Frequency**: Ranking based on purchase frequency.
- **Rank_Spending**: Ranking based on the total spending amount.
- **Average of Rank**: Average rank across recency, frequency, and spending.
- **Overall Rank**: Combined rank for RFM segmentation.
- **Customer Tiers**: Segmented customer groups based on RFM scores.
- **Gender**: Gender of the customer.
- **Age**: Age of the customer.
  
## 📍Project Objectives
- Perform RFM segmentation to categorize customers into groups such as **Champions, Loyal Customers, Potential Loyalist, Promising, At Risk**.
- Visualize customer segmentation using an interactive Tableau dashboard.
- Provide insights to help businesses understand customer behavior and improve decision-making.

## 🚀Features of the Tableau Dashboard
1. **Customer Segmentation Overview**:
   - Visual representation of customer tiers.
   - Insights on high-value vs. low-value customers.
2. **Key Metrics**:
   - Analysis of recency, frequency, and monetary values.
   - Drill-down options for specific customer segments.
3. **Demographics Insights**:
   - Breakdown by gender and age groups.
 
## 📊🍜Insights

### Customer Segmentation Breakdown
- #### Champions
  - These customers make up 22% of the customer base and contribute to the majority of revenue.
  - They are frequent buyers with high spending and recent purchases, making them ideal for loyalty programs or exclusive offers.

- #### Loyal Customers
  - This group consistently makes repeat purchases and represents a significant portion of long-term revenue.
  - Retaining them through rewards or early access to products can strengthen their loyalty even further.

### Growth Opportunities
- #### Potential Loyalist
  - Customers in this group show high potential to become Champions.
  - Strategies such as personalized marketing or small incentives (e.g., free shipping or discounts) could encourage them to purchase more frequently.

- #### Promising Customers
  - These are new or occasional buyers with medium spending levels.
  - Engaging them through follow-ups, product recommendations, or introductory offers can drive higher retention.

### At-Risk Customers
- This segment includes customers with low recent activity but medium or high spending in the past.
- Re-engagement campaigns, such as email reminders, exclusive discounts, or personalized offers, could win them back.

### Demographics and Spending Patterns
- Champions, Potential Loyal Customers, and Promising are predominantly Teenagers, indicating a strong purchasing power in this demographic.
- #### Gender Insights
  - Male customers slightly dominate the Champion segment, while females are more prevalent in the Potential Loyalist and Promising groups.

### Behavioural Insights
- Loyal Customers and Champions have the highest spending levels, and their purchase frequency shows consistent growth.

### Retention Strategies
- For **Champions**: Strengthen their loyalty through VIP programs, exclusive offers, or early product launches.
- For **At-Risk Customers**: Focus on reactivation campaigns, leveraging discounts, or reminding them of past positive experiences.
- For **Promising Customers**: Engage them with welcome campaigns or personalized product recommendations to build trust.

## MySQL Queries for validation 
```
`USE spicyfood;

SELECT * FROM spicyfood_data;

-- Total Unique Customers count
SELECT DISTINCT(COUNT(*)) AS Total_Customers FROM spicyfood_data;

-- Total bill amount
SELECT SUM(`Bill Amount`) AS Total_Purchase FROM spicyfood_data;

-- Total Number of Orders
SELECT SUM(`Purchase Frequency`) AS Number_of_Orders FROM spicyfood_data;

-- Average Purchase Amount
SELECT ROUND(AVG(`Bill Amount`)) AS Avg_Purchase_Amount FROM spicyfood_data;

-- Unique Customer Tiers
SELECT DISTINCT `Customer Tiers` FROM spicyfood_data;

-- Select Customer ID, Purchase Frequency, Bill Amount and Recent Purchase Date with a Customer Tier "Champions"
SELECT `Customer ID`, `Purchase Frequency`, `Bill Amount`, `Recent Purchase Date`
FROM spicyfood_data 
WHERE `Customer Tiers` = 'Champions';

-- Select Customer ID, Purchase Frequency, Bill Amount and Recent Purchase Date with a Customer Tier "Loyal Customer"
SELECT `Customer ID`, `Purchase Frequency`, `Bill Amount`, `Recent Purchase Date`
FROM spicyfood_data 
WHERE `Customer Tiers` = 'Loyal Customer';

-- find the percentage of customers in each Customer Tier
SELECT 
    `Customer Tiers`, 
    COUNT(*) AS Customer_Count,
    ROUND((COUNT(*) * 100.0 / (SELECT COUNT(DISTINCT `Customer ID`) FROM spicyfood_data)), 2) AS Percentage
FROM spicyfood_data
GROUP BY `Customer Tiers`
ORDER BY Percentage DESC;

--  retrieve customers sorted by their overall rank
SELECT `Customer ID`, `Overall Rank`
FROM spicyfood_data
ORDER BY `Overall Rank`;

-- Select customers who have recently purchased and their total spend
SELECT `Customer ID`, SUM(`Rank_Spending`) AS Total_Spend
FROM spicyfood_data
WHERE `Recent Purchase Date` = (SELECT MAX(`Recent Purchase Date`) FROM spicyfood_data)
GROUP BY `Customer ID`;


-- Gender distribution by Customer Tiers
SELECT 
    `Customer Tiers`, 
    Gender, 
    COUNT(*) AS Customer_Count, 
    ROUND((COUNT(*) * 100.0 / SUM(COUNT(*)) OVER (PARTITION BY `Customer Tiers`)), 2) AS Percentage
FROM spicyfood_data
GROUP BY `Customer Tiers`, Gender
ORDER BY `Customer Tiers`, Percentage DESC;
```

# Connect🤝
- 📩 <b>Email:</b> kshitijachilbule5@gmail.com
- 📶 <b>LinkedIn:</b> https://www.linkedin.com/in/kshitija-chilbule-b98515309/
- 📜 <b>Medium:</b> https://medium.com/@kshitijachilbule2
- 👩‍💻 <b>HackerRank:</b> https://www.hackerrank.com/profile/kshitijachilbul7
