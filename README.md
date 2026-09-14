# E-Commerce_Business_Performance_Analysis

An end-to-end Power BI analytics project analyzing transaction orders from 2021–2025 in an E-Commerce business to uncover trends in sales, profitability, customer behaviour, product performance, and operational efficiency, translating findings into actionable business recommendations.

---

📦 Table of Contents

- [Project Overview](#-project-overview)
- [Business Objectives](#-business-objectives)
- [Tools & Technologies](#-tools--technologies)
- [Dataset & Data Model](#-dataset--data-model)
- [Data Preparation & Transformation](#-data-preparation--transformation)
- [Exploratory Data Analysis (EDA)](#-exploratory-data-analysis-eda)
- [Dashboard Structure](#-dashboard-structure)
- [Key Business Insights](#-key-business-insights)
- [Dashboard](#-dashboard)
- [Business Recommendations](#-business-recommendations)

---
 
## 📝 Project Overview
This project analyses the performance of a fictitious E-commerce business using data covering 2021–2025. The dashboard provides a comprehensive view of Sales Performance, Products & Profitability, Customer & Marketing, and Logistics & Returns, supported by a concise yet insightful Executive Overview.

The goal is to understand the company's overall performance, identify key trends and patterns, and uncover the factors driving business growth, profitability, customer behaviour, and operational performance.


---

## 🎯 Business Objectives

The analysis aims to:

- Evaluate overall sales and profitability performance by identifying trends in revenue, realized net profit, profit margins, order activity, and product performance over 2021–2025.
- Identify profitable products and categories by comparing sales, quantities sold, profit, profit margins, and return activity to distinguish high-demand products from those that generate stronger financial value.
- Assess the impact of discounting on sales and profitability to understand whether higher discounts drive additional demand at the expense of profit margins.
- Understand customer behaviour and value by analysing customer segments, customer types, repeat purchasing, order behaviour, and customer value across different markets.
- Evaluate marketing and acquisition performance by comparing channels based on customer acquisition, sales, profitability, and the value of customers they attract.
- Analyse regional and market performance to identify differences in sales, customer behaviour, and purchasing patterns across countries and regions.
- Assess logistics and returns performance by examining delivery outcomes, return rates, return sales, and return reasons to identify potential operational challenges.
- Identify key trends, patterns, and relationships across customers, products, sales, marketing, and operations that may explain the factors contributing to business growth or declining performance.

---

## 🧰 Tools & Technologies


* Microsoft Excel - Data Preparation
  
  * Reviewed multi-year datasets covering sales, customers, products, and operational information from 2021–2025.

* Power Query - Data Transformation & ETL
  
  * Cleaned, transformed, and structured data from multiple related tables, including handling missing values and preparing fields for analysis.

* Power BI - Data Modeling, Analytics & Visualization
  
  * Designed the data model and relationships across Sales, Customers, Order Items, and Products, with supporting Calendar and Measures tables.
  * Developed interactive 5-page dashboards with slicers, drill-downs, cross-filtering, and custom visual formatting.

* DAX (Data Analysis Expressions) — Analytical Calculations
  
  * Developed dynamic measures for time-based analysis, YoY growth, profitability, return rates, customer metrics, and other business KPIs.

---

## 📂 Dataset & Data Model

### Data Source

The dataset was sourced from Kaggle and covers E-commerce activity from 2021–2025.

### Source Tables

The analysis was built from four related source tables:

|**Table** | **Records** | **Description overview**|
|---|---|---|
|Customers | 25,000 | Customer attributes and customer value-related information|
|Sales | 138,116 | Order-level transactions, sales values, discounts, status, and delivery information|
|Order Items | 387,569 | Individual products and quantities, cost, revenue and profit associated with each order|
|Products | 1,175 | Product categories, subcategories, brands, costs, ratings, suppliers, and review sentiment|

### Supporting Tables

Two additional tables were created in Power BI to support the analysis:

- **Calendar** - A dedicated date table used for time intelligence, date filtering, and analysis of trends across 2021–2025.
- **Measures** - A dedicated table used to organize and manage DAX measures separately from the source data tables.

### Data Model

The tables are connected through key fields including Order ID, Product ID, and Customer ID. The model uses Sales as the central transaction table, with Order Items providing the link between sales transactions and product-level information.

The model is a relational data model rather than a conventional star schema, reflecting the structure of the source data and the analytical requirements of the project.

### Data model schema:

"Data Model Schema" (images/data-model.png)

---

## 🧹 Data Preparation & Transformation

The source data was reviewed and prepared to improve data quality, reduce redundancy, and ensure that calculations were based on the appropriate level of detail.

**Data Cleaning & Structuring**

- Removed the Order Time field from the Sales table as it was not required for the analysis.
- Removed customer attributes from the Sales table — including customer name, age, gender, segment, city, state, country, region, and postal code — because these attributes were already maintained in the Customer Master table. This reduced redundancy and kept customer information centralized.
- Preserved null values for Delivery Days and Estimated Delivery Days for cancelled orders, ensuring that cancelled orders were not incorrectly included in delivery-time calculations such as averages.
- Standardized and corrected column data types across the Order Items, Customer Master, and Products tables.
- Created discount bands from discount percentages to support analysis of discount levels and their relationship with sales, quantity, and profitability.

**Data Quality & Validation**

- Reviewed column quality and distribution to identify missing, invalid, or inconsistent values.
- Examined distinct and unique values to identify potential duplicates and validate the underlying data.
- Reviewed relationships and fields across the source tables to ensure that data was structured appropriately for analysis.

**Time Intelligence** 

- Created a dedicated Calendar table and configured it as the model's date table to support time-intelligence calculations and consistent date-based analysis across the dashboard.

**Data consideration:**

The dataset contains financial values for some cancelled orders with failed payments. Therefore, both order status and payment status were considered when defining recognized/realized sales and profit to avoid overstating them.

---

## 🔎 Exploratory Data Analysis (EDA)

Prior to building the data model and Power BI reporting suite, exploratory data analysis was conducted across the dataset records to assess data quality, understand field distributions, and identify relationships and patterns relevant to the business.
The analysis focused on:
- Sales & profitability: Multi-year sales trends, order activity, AOV, realized profit, and profit margins.
- Discount impact: Relationships between discount levels, quantities sold, sales, and profitability.
- Product performance: Category and subcategory differences in sales, quantity, profit, margins, and returns.
- Customer behaviour: Customer types, segments, order frequency, repeat purchasing, and customer value.
- Marketing performance: Customer acquisition, sales, and profit across marketing channels.
- Logistics & returns: Delivery outcomes, cancellation patterns, return rates, return reasons, and shipping methods.
- Geographic performance: Sales and customer activity across countries and regions.
- 
---

## 💻 Dashboard Structure

**1. Executive Overview**

**Focus:** High-level view of overall business performance and key trends.

**Key Visuals:**
* KPI cards: Order Completion %, Realized Net Sales, Realized Net Profit, Profit Margin, Sales YoY, and Order Return Rate
* Realized Net Sales by Month
* Order Status Distribution
* Realized Net Sales by Country
* Realized Net Sales by Customer Segment

**2. Sales Performance**

**Focus:** Analysis of sales activity, order performance, customer purchasing, and the impact of discounts.

**Key Visuals:**
* KPI cards: Total Orders, Completed Orders, Quantities Sold, and Average Order Value
* Realized Net Sales by Period with drill-down
* Realized Net Sales by Location with geographic drill-down
* Discount Impact on Sales Volume and Profitability
* Realized Net Sales by Sales Channel
* Quantity Sold by Month
* Realized Net Sales by Customer Type

**3. Customer & Marketing Analysis**

**Focus:** Understanding customer behaviour, customer value, segmentation, and marketing performance.

**Key Visuals:**
* KPI cards: Total Customers, Purchasing Customers, Repeat Customer Rate, and Average Customer Revenue
* Marketing Channel Performance
* Realized Net Sales & Profit by Marketing Channel
* Realized Net Sales by Gender
* Customer Order Size Distribution
* Customer Segment Value and Acquisition
* Profit Margin by Customer Type

**4. Products & Profitability**
   
**Focus:** Evaluating product demand, profitability, margins, and return performance across product categories.

**Key Visuals:**
* Realized Net Sales & Profit by Product Category and Subcategory
* Realized Net Profit by Month
* Profit Margin by Month
* Product Category Performance Table: Return Rate, Profit Margin, Profit per Unit, and Quantity Sold

**5. Logistics & Returns**

**Focus:** Assessing delivery performance, returns, return-related revenue impact, and operational efficiency.
**Key Visuals:**
* Order Delivery Status Breakdown
* Return Sales & Order Return Rate by Month
* Return Reasons
* Country-level Return Performance
* Shipping Method Performance

---

## 🔍 Key Business Insights


**1. Stable Sales Base with a Gradual Downward Trend**

Realized net sales remained relatively stable at around $31M annually from 2021–2025, but showed a gradual decline over the period. The U.S., the dominant market, contributes significantly to this downward trend, with Germany also showing a decline, while smaller markets have not generated enough sales volume to fully offset the reduction.

**2. Sales Volume Does Not Always Translate to Higher Profitability**

November and December recorded the highest realized net sales and quantities sold, but they also recorded the lowest profit margins across the months. In contrast, August, October and December are generally among the stronger months for realized net profit. This highlights that higher sales volume does not necessarily result in stronger profitability. Differences in product mix, pricing, discounts, and costs play an important role in monthly profit performance.

**3. Higher Discounts Increase Volume but Pressure Profitability**

Higher discount levels are associated with lower realized net sales and profitability. November and December recorded a greater concentration of quantities sold at 30%–60% discount levels, which may help explain why their higher sales volumes did not translate into the highest profit margin. This highlights the importance of balancing sales volume with margin preservation when using discounts.

**4. Product Mix and Profitability**

Electronics, Jewelry, and Home Appliances consistently rank among the top-performing product categories by realized net sales and realized net profit across the five-year period. Grocery consistently records the highest profit margin year over year, generating a relatively higher proportion of profit from its realized sales. Overall profitability also varies across months, showing that volume of sales alone does not determine how much profit the business generates.

**5. Customer Loyalty Drives Profit Contribution** 

Profit margins remained relatively stable across customer types over 2021–2025, ranging from 41.43% to 42.67%. New customers recorded the highest margin at 42.67%, while Loyal customers generated the highest total realized net profit due to their greater purchasing volume. This demonstrates the difference between profitability rate and absolute profit contribution.

**6. Customer Segments Show Different Purchasing and Discount Behaviours**

The Consumer segment contributes 55.02% of total sales, making it the largest revenue contributor with the highest LifeTimevalue. Business and Consumer customers are also major contributors to realized net profit, particularly during November and December. In contrast, Premium and VIP segments show a higher concentration of purchases at 50%–60% discounts, while Consumer and Business purchases are concentrated primarily within the 0%–20% discount range. Premium also shows relatively steady year-on-year sales growth compared with the other segments.

**7. Repeat Purchasing Is Highly Concentrated**

Although almost all purchasing customers are classified as repeat customers, purchasing frequency is uneven. Most customers make relatively few repeat purchases, while a smaller group accounts for much more frequent purchasing, including customers who have placed up to 10–20 orders. This suggests that customer retention is strong, but high purchase frequency is concentrated among a smaller group of customers.

**8. Order Cancellations Represent a Significant Operational Issue**

Approximately 17.78% of orders were cancelled. The recorded cancellation reasons include wrong product, other, changed mind, size issue, defective product, late delivery, product not as expected, and damaged product. The presence of product-related and fulfilment-related cancellation reasons highlights opportunities to improve product information, order accuracy, quality control, and delivery processes to reduce avoidable cancellations.

---

## 📊 Dashboard

The Power BI dashboard consists of five interactive pages designed to provide a comprehensive view of business performance across sales, customers and marketing, products and profitability and logistics and returns
  
### Dashboard 1 - Executive Overview
![Dashboard 1]()

### Dashboard 2 - Sales Performance
![Dashboard 2]()

### Dashboard 3 - Customer & Marketing Analysis
![Dashboard 3]()

### Dashboard 4 - Products & Profitability
![Dashboard 4]()

### Dashboard 5 - Logistics & Returns
![Dashboard 5]()

## 💡 Business Recommendations

Based on the analysis, the following actions could help improve profitability, customer value, revenue growth, and operational performance:

**1. Review High-Discount Strategies**

Higher discount levels are associated with increased quantities sold but lower profit margins. The business should evaluate whether discounts above 30% generate sufficient sales volume to justify the reduction in margins, particularly during high-volume periods such as November and December.

**2. Optimize the Product Mix**

Electronics, Jewelry, and Home Appliances consistently contribute strongly to realized net profit, while Grocery records the highest profit margin. The business should prioritize high-performing and high-margin categories while reviewing pricing, costs, and product assortment for lower-margin categories.

**3. Increase Customer Purchase Frequency**

The customer order-count distribution shows that while many customers make repeat purchases, frequent purchasing is concentrated among a smaller group of customers. The business should use targeted retention, personalized offers, cross-selling, and reactivation campaigns to encourage lower-frequency customers especially those that have purchased once to purchase more often.

**4. Evaluate Discount Strategies by Customer Segment**

Premium and VIP customers show a higher concentration of purchases at 50%–60% discounts, while Consumer and Business customers are more concentrated at 0%–20% discounts. The business should evaluate discount performance within each segment to determine where higher discounts generate sufficient additional sales and where lower discounts may be sufficient to maintain demand and protect profit margins.

**5. Reduce Preventable Order Cancellations**

With approximately 17.78% of orders cancelled, the business should investigate the main cancellation reasons, particularly wrong product, product quality issues, and fulfilment-related problems. Improving product information and order accuracy, strengthening quality checks, and addressing delivery issues could help reduce avoidable cancellations and improve the customer experience.

**6. Protect Major Markets and Develop Growth Opportunities**

The U.S. remains the dominant market, but its declining realized net sales contributes significantly to the overall downward sales trend. The business should investigate the causes of this decline while developing the smaller markets with growth potential to reduce dependence on its largest market.

**7. Focus on Sustainable Revenue Growth**

Realized net sales remained relatively stable at around $31M annually but showed a gradual decline from 2021 to 2025. Growth strategies should focus not only on increasing sales volume, but also on increasing customer purchase frequency, improving customer value, reducing avoidable cancellations, and protecting profit margins.
