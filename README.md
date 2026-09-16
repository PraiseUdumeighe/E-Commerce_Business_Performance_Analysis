# E-Commerce Business Performance Analysis

An end-to-end Power BI analytics project analyzing e-commerce transaction data from 2021–2025 to uncover trends in sales, profitability, customer behaviour, product performance, and operational efficiency, translating findings into actionable business recommendations.

---

## 📦 Table of Contents

- [Project Overview](#-project-overview)
- [Business Objectives](#-business-objectives)
- [Tools & Technologies](#-tools--technologies)
- [Dataset & Data Model](#-dataset--data-model)
- [Data Preparation & Transformation](#-data-preparation--transformation)
- [Business Metrics & Logic](#-business-metrics--logic)
- [Exploratory Data Analysis (EDA)](#-exploratory-data-analysis-eda)
- [Dashboard Structure](#-dashboard-structure)
- [Dashboard](#-dashboard)
- [Key Business Insights](#-key-business-insights)
- [Business Recommendations](#-business-recommendations)
- [Limitations](#limitations)

---
 
## 📝 Project Overview
This project analyses the performance of an e-commerce business using data covering 2021–2025. The dashboard provides a comprehensive view of Sales Performance, Products & Profitability, Customer & Marketing, and Logistics & Returns, supported by a concise yet insightful Executive Overview.

The goal is to understand the company's overall performance, identify key trends and patterns, and uncover the factors driving business growth, profitability, customer behaviour, and operational performance.

---

## 🎯 Business Objectives

The analysis aims to:

- Evaluate overall sales, profitability and order performance from 2021-2025.
- Identify high-performing and profitable products and categories.
- Assess the relationship of discounting, sales and profitability.
- Analyze customer behaviour, segmentation, retention and customer value.
- Evaluate realized net sales and profit across marketing channels to identify growth opportunities.
- Analyse regional and market performance to identify differences in sales, customer behaviour, and purchasing patterns across countries and regions.
- Assess logistics, cancellations and returns performance to identify operational improvement areas.

---

## 🧰 Tools & Technologies

* Microsoft Excel - Data Preparation
  
  * Data Exploration and Validation

* Power Query - Data Transformation & ETL
  
  * Cleaned, transformed, and structured data from multiple related tables, including handling missing values and preparing fields for analysis.

* Power BI - Data Modeling, Analytics & Visualization
  
  * Designed the data model and relationships across Sales, Customers, Order Items, and Products, with supporting Calendar and Measures tables.
  * Developed a 5-page interactive dashboard with slicers, drill-downs, cross-filtering, and custom visual formatting.

* DAX (Data Analysis Expressions) — Analytical Calculations
  
  * Developed dynamic measures for time-based analysis, YoY growth, profitability, return rates, customer metrics, and other business KPIs.

---

## 📂 Dataset & Data Model

### Data Source

The dataset was sourced from Kaggle and covers E-commerce activity from 2021–2025.

🔗 [View the original dataset on Kaggle](https://www.kaggle.com/datasets/datascikhan/e-commerce-sales-and-customer-analytics)

### Source Tables

The analysis was built from four related source tables:

|**Table** | **Records** | **Description overview**|
|---|---|---|
|Customers | 25,000 | Customer attributes and customer value-related information|
|Sales | 138,116 | Order-level transactions, sales values, discounts, status, and delivery information|
|Order Items | 397,569 | Individual products and quantities, cost, revenue and profit associated with each order|
|Products | 1,175 | Product categories, subcategories, brands, costs, ratings, suppliers, and review sentiment|

### Supporting Tables

Two additional tables were created in Power BI to support the analysis:

- **Calendar** - A dedicated date table used for time intelligence, date filtering, and analysis of trends across 2021–2025.
- **Measures** - A dedicated table used to organize and manage DAX measures separately from the source data tables.

### Data Model

The model combines two transaction tables at different levels of detail:

* **Sales** - An order-level table, with one row representing an order.
* **Order Items** - A product-level transaction table, with multiple rows possible per order.

Sales is connected to the Customer table through Customer ID, while Order Items is connected to the Product Catalog through Product ID. Sales and Order Items are related through Order ID, and the Calendar table is connected to Sales for time-based analysis.

### Data model schema:

![Data Model Schema](Project%20Images/Data%20Model.png)

---

## 🧹 Data Preparation & Transformation

The source data was reviewed and prepared to improve data quality, reduce redundancy, and ensure that calculations were based on the appropriate level of detail.

**Data Cleaning & Structuring**

* Removed the `order_time` field from the Sales table as it was not required for the analysis.
* Removed customer attributes from the Sales table (including customer name, age, gender, segment, city, state, country, region, and postal code) because these attributes were already maintained in the Customer Master table. This reduced redundancy and kept customer information centralized.
* Preserved null values for `delivery_days` and `estimated_delivery_days` for orders that were not completed, since delivery did not occur for these orders. This prevented non-delivered orders from being incorrectly included in delivery-time calculations such as averages.
* Standardized and corrected column data types across the Order Items, Customer Master, and Products tables.
* Created discount bands from discount percentages to support analysis of discount levels and their relationship with sales, quantity, and profitability.

**Data Quality & Validation**

* No duplicate records were identified during duplicate and uniqueness checks.
* Reviewed column quality and distributions to identify missing, invalid, or inconsistent values.
* Blank values were assessed based on their business context. For example, `return_status` was blank for orders without a recorded return, while delivery fields were blank for orders that were not completed.
* Examined distinct and unique values and reviewed relationships across the source tables to validate the underlying data structure and appropriate level of detail.

**Time Intelligence**

* Created a dedicated Calendar table and configured it as the model's date table to support time-intelligence calculations and consistent date-based analysis across the dashboard.

---

## 📏 Business Metrics & Logic

To ensure that the analysis reflects realized business performance rather than all recorded transactions, key metrics were calculated using consistent business rules:

| Metric                        | Definition & Business Logic|
|-----------------------------|-----------------------------|
| **Realized Net Sales**        | Revenue from orders classified as Completed and therefore delivered.|
| **Realized Net Profit**       | Profit value provided in the dataset for the applicable transactions.|
| **Profit Margin**             | Realized Net Profit relative to Realized Net Sales.|
| **Completed Orders**          | Orders with a **Completed** order status.|
| **Quantity Sold**             | Quantity from the Order Items table associated with Completed orders.|
| **Average Order Value (AOV)** | Average realized sales value per Completed order.|
| **Order Return Rate**         | Proportion of orders recorded with a **Returned** return status. No Completed orders in the dataset were recorded as returned. |
| **Repeat Customer Rate**      | Proportion of purchasing customers identified as repeat customers.|
| **Average Customer Revenue**  | Average realized revenue generated per purchasing customer.|

**Sales Recognition and Business Logic**

The dataset includes orders with statuses of Completed, Returned, Cancelled, and Pending. Realized sales and profit are based on orders marked as completed with successful payment. Realized Net Sales uses the dataset's `net_sales` field under these sales-recognition criteria. Cancelled and pending orders are excluded from realized performance metrics, while returns are analyzed separately through return status and return-related metrics.

---

## 🔎 Exploratory Data Analysis (EDA)

Exploratory data analysis was conducted across the dataset during data preparation and modeling to assess data quality, understand field distributions, and identify relationships and patterns relevant to the business.

The analysis focused on:

* **Sales & profitability:** Multi-year sales trends, order activity, AOV, realized gross profit, and gross profit margins.
* **Discounts:** Relationships between discount levels, quantities sold, sales, and profitability.
* **Product performance:** Category and subcategory differences in sales, quantity, gross profit, margins, and returns.
* **Customer behavior:** Customer types, segments, customer order counts, repeat purchasing, and customer value.
* **Marketing channels:** Customer counts, sales, and gross profit across marketing channels.
* **Logistics & returns:** Delivery outcomes, cancellation patterns, return rates, return reasons, and shipping methods.
* **Geographic performance:** Sales and customer activity across countries and regions.
  
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

## 📊 Dashboard

The Power BI dashboard consists of five interactive pages designed to provide a comprehensive view of business performance across sales, customers and marketing, products and profitability, and logistics and returns
  
### Dashboard 1 - Executive Overview
![Dashboard 1](Project%20Images/Executive_Overview.png)

### Dashboard 2 - Sales Performance
![Dashboard 2](Project%20Images/Sales_Performance.png)

### Dashboard 3 - Customer & Marketing Analysis
![Dashboard 3](Project%20Images/Customer_&_Marketing_Analysis.png)

### Dashboard 4 - Products & Profitability
![Dashboard 4](Project%20Images/Products_&_Profitability.png)

### Dashboard 5 - Logistics & Returns
![Dashboard 5](Project%20Images/Logistics_&_Returns.png)

---

## 🔍 Key Business Insights


**1. Relatively Stable Sales with Decline Over the Period**

Realized net sales averaged approximately $31.36M annually from 2021–2025 but declined by 2.48%, from $31.85M in 2021 to $31.06M in 2025. The U.S. market, the largest contributor to realized net sales, declined from $18.33M in 2021 to $17.88M in 2025, a 2.45% decrease. This represented approximately 57% of the overall $0.79M decline in realized net sales over the period.


**2. Sales Volume Does Not Always Translate to Higher Profitability**

November and December recorded the highest realized net sales and quantities sold, but they also recorded the lowest profit margins across the months. This highlights that higher sales volume does not necessarily result in stronger profitability. Differences in product mix, pricing, discounts, and costs play an important role in monthly profit performance.

**3. Higher Discounts Are Associated with Lower Profitability and Sales Volume**

Profitability declines as discount levels increase, while quantity sold peaks at 10% discount and falls substantially across the higher discount bands.
November and December recorded a higher combined share of quantities sold within the 30%–60% discount range, coinciding with their high overall sales volumes.

**4. Product Mix and Profitability**

Electronics, Jewelry, and Home Appliances consistently rank among the top-performing product categories by realized net sales and realized net profit across the five-year period. Grocery consistently records the highest profit margin year over year, generating a relatively higher proportion of profit from its realized sales. 

**5. Customer Loyalty and Profit Contribution**

Customers classified as New recorded the highest profit margin at 42.67%, while Loyal customers generated the highest total realized net profit alongside greater purchasing volume. This highlights the difference between profitability rate and absolute profit contribution.

**6. Customer Segments Show Different Purchasing and Discount Behaviours**

The Consumer segment contributes 55.02% of total sales, making it the largest revenue contributor. Premium and VIP segments show a higher concentration of purchases at 50%–60% discounts, while Consumer and Business purchases are concentrated primarily within the 0%–20% discount range. Premium also shows relatively steady year-on-year sales growth compared with the other segments.

**7. Sales Channel and Marketing Channel**

Mobile Apps sales channel drives the highest realized net sales followed by Website use.

Organic Search was associated with the highest number of customers and recorded the highest realized net sales and realized net profit among marketing channels, while YouTube recorded the lowest realized net sales.

**8. Repeat Purchasing And Order Count**

Repeat customers account for 98.66% of Purchasing Customers indicating that most customers made more than one purchase. However order counts are unevenly distributed: while customer order count ranges from 1 to 20, only 8.26% of purchasing customers have placed 10-20 orders.

**9. Delivery Order Cancellations Represent a Significant Operational Issue**

Approximately 17.78% of delivery orders were cancelled. The recorded cancellation reasons include wrong product, other, changed mind, size issue, defective product, late delivery, product not as expected, and damaged product. The presence of product-related and fulfilment-related cancellation reasons highlights opportunities to improve product information, order accuracy, quality control, and delivery processes to reduce avoidable cancellations.

---

## 💡 Business Recommendations

Based on the analysis, the following actions could support profitability, customer value, revenue growth, and operational performance:

**1. Evaluate High-Discount Strategies**

Higher discount bands are associated with lower profitability, while quantity sold peaks at the 10% discount band and declines at higher discount levels. The business should evaluate discount levels alongside sales volume, gross profit, and gross profit margin to determine whether additional volume compensates for reduced margins.

**2. Optimize the Product Mix**

Electronics, Jewelry, and Home Appliances contribute strongly to realized gross profit, while Grocery records the highest gross profit margin. The business should evaluate product mix, pricing, costs, and assortment across categories to identify opportunities to strengthen both profit contribution and margins.

**3. Increase Customer Purchase Frequency**

The business should use targeted retention, personalized offers, cross-selling, and reactivation strategies to encourage lower-frequency customers, particularly those with only one purchase, to purchase more frequently.

**4. Evaluate Discount Strategies by Customer Segment**

The business should evaluate how discount levels relate to sales volume and profitability across customer segments, such as Consumer, Premium, VIP, and Business. This can help identify whether different segments respond differently to discounts and where discounting may be adjusted to support sales while protecting profit margins.

**5. Reduce Preventable Delivery Cancellations**

Approximately 17.78% of orders had a **Cancelled delivery status**. The business should investigate the reasons associated with these delivery cancellations, particularly product, quality, and fulfilment-related issues where applicable. Improving product information, order accuracy, quality checks, and fulfilment processes could help reduce avoidable delivery cancellations and improve the customer experience.


**6. Protect Major Markets and Develop Growth Opportunities**

The U.S. remains the largest contributor to realized net sales, but its 2.45% decline from 2021 to 2025 accounted for approximately 57% of the overall decline in realized net sales over the period. The business should investigate the factors associated with this decline while evaluating opportunities in smaller markets to diversify revenue sources.

**7. Focus on Sustainable Revenue Growth**

Growth strategies should focus not only on increasing sales volume, but also on increasing customer purchase frequency, improving customer value, reducing avoidable cancellations, and protecting profit margins.

---

## Limitations

The analysis is subject to the following dataset limitations:

* **Dataset Scope:** The analysis covers the available data for 2021–2025. Findings therefore reflect patterns within this dataset and should not automatically be generalized beyond the period or population represented.

* **Synthetic/Simulated Data:** The dataset is designed for analytical purposes rather than representing a verified real-world company's complete operational records. Findings should therefore be interpreted as analytical results rather than actual company performance.

* **Profit Scope:** The dataset includes product and shipping costs but does not provide a complete set of operating expenses, such as marketing, payroll, warehousing, or administrative costs. Therefore, profit and margin measures reflect the costs captured in the dataset rather than full business net income.

* **Incomplete Marketing Data:** Some campaign-name records are blank, limiting campaign-level analysis. Coupon codes are also blank in the available data and could not be used for coupon-level analysis.

* **Customer Review Data:** Some customer review fields are blank, limiting the completeness of review-based analysis and the ability to incorporate customer feedback across all transactions.
