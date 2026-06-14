# Amazon-ecommerce-analysis

##📋 Project Overview
This project presents an end-to-end data analysis of Amazon sales data, covering the full pipeline from raw data collection to interactive dashboard creation. The goal is to uncover meaningful insights about customer behavior, product performance, revenue trends, and operational efficiency.

##🗂️ Project Workflow
Kaggle Dataset → Python (Data Cleaning) → MySQL (Querying) → Power BI (Dashboard)

##📁 Tech Stack

Tool --	Purpose
Kaggle	Data source
Python (Jupyter Notebook)	Data cleaning & preprocessing
MySQL 8.4	Data storage & SQL analysis
Power BI	Data visualization & dashboarding

##📥 1. Data Collection
Dataset sourced from Kaggle (Amazon Sales Dataset)
Contains 1,000,000 order records across multiple dimensions: customers, products, locations, payment methods, and delivery status

##🧹 2. Data Cleaning (Python / Jupyter Notebook)
Performed the following preprocessing steps using Pandas:

Removed duplicate records
Handled missing/null values
Standardized column data types (dates, numeric fields)
Filtered out inconsistent or invalid entries
Exported cleaned data for MySQL import

##3. Database Setup & SQL Analysis (MySQL)
Database: amazon_project
Table: orders

###Key Queries 
####1.Total Revenue
SELECT SUM(final_price) FROM orders;
result:
| SUM(final_price)  |
+-------------------+
| 9938876984.899958 |

####2.Revenue by Brand (Top 10)
SELECT brand, SUM(final_price) AS revenue
FROM orders
GROUP BY brand
ORDER BY revenue DESC
LIMIT 10;
result:
+---------+-------------------+
| brand   | revenue           |
+---------+-------------------+
| Lenovo  | 834698265.1300116 |
| Sony    | 832227170.8400061 |
| Samsung | 831559760.4099945 |
| LG      | 831268886.5099925 |
| Adidas  | 828076829.7799908 |
| Boat    | 827732261.8699986 |
| HP      | 826993652.6799951 |
| Nike    |  826645590.460006 |
| Zara    | 826028195.5200062 |
| Apple   |  826003980.430001 |
+---------+-------------------+

####3.Revenue by Category
SELECT category, SUM(final_price)
FROM orders
GROUP BY category;
result:
+-------------+--------------------+
| category    | SUM(final_price)   |
+-------------+--------------------+
| Electronics |  6579047983.299879 |
| Sports      | 1124849199.3300068 |
| Beauty      |  375951719.9100048 |
| Home        | 1529977638.3200028 |
| Clothing    |  329050444.0399974 |
+-------------+--------------------+

####4.Average Rating by Brand
SELECT brand, AVG(rating)
FROM orders
GROUP BY brand
ORDER BY AVG(rating) DESC;
result:
+---------+--------------------+
| brand   | AVG(rating)        |
+---------+--------------------+
| Sony    | 3.9300674421112123 |
| Samsung | 3.9298641288083314 |
| Lenovo  | 3.9283079169758555 |
| H&M     | 3.9278224045042065 |
| Zara    |  3.927728376072462 |
| Boat    |  3.927551289425784 |
| Apple   | 3.9272573057905187 |
| Adidas  |  3.927091023135743 |
| HP      | 3.9267109674329364 |
| LG      |  3.926013924322277 |
| Nike    | 3.9252508521772733 |
| Puma    |  3.923064321331621 |
+---------+--------------------+

####5.Orders by Payment Method
SELECT payment_method, COUNT(*)
FROM orders
GROUP BY payment_method;
result:
Payments are nearly evenly distributed across UPI (~25%), Credit Card (~25%), Debit Card (~24.9%), and Cash on Delivery (~25%).
+------------------+----------+
| payment_method   | COUNT(*) |
+------------------+----------+
| UPI              |   249951 |
| Credit Card      |   250324 |
| Debit Card       |   249337 |
| Cash on Delivery |   250388 |
+------------------+----------+

##📊 4. Power BI Dashboards
Three interactive dashboards were built in Power BI using the MySQL data.

###Dashboard 1 — Overview
1M total customers, 90K products, 1M orders, $9.90M total revenue, 3.93 avg rating
Orders by category (treemap): Home and Sports lead in volume
Monthly order trends show consistent performance year-round
Return rates broken down by category — Beauty has the highest return rate
Payment methods are evenly split across four channels

###Dashboard 2 — Products
5 categories, 12 brands, $9.94K avg revenue, 3.93 avg rating, Home is the top category
Orders by rating follow a near-normal distribution, peaking around the 3.5–4.0 range
Avg rating is consistent across all categories (Electronics, Home, Sports, Beauty, Clothing)
Delivery status breakdown: majority delivered, with a portion delayed, in transit, or returned
Brand-level table showing orders, revenue, stock, delivery count, and total orders

###Dashboard 3 — Customers
82K total customers, Delhi is the top city, 5 locations, $9.90M revenue, $9.93K AOV (Average Order Value)
Customer journey funnel: Orders → Rated → Delivered → 5-Star Rated (drop-off visible at each stage)
Customers and orders vary by location — relatively balanced across all 5 cities
Payment method distribution shown via donut chart
Orders by device type visible; one segment dominates

##5. Key Insights
Electronics dominates revenue — accounting for over 66% of total sales ($6.58B out of $9.94B), making it by far the most important category.
Revenue is city-agnostic — all 5 cities (Delhi, Bangalore, Mumbai, Chennai, Hyderabad) contribute almost equally (~$2B each), suggesting no single market dependency.
Return rate is ~11.6% — Beauty and Clothing categories show higher return rates, which may indicate sizing/expectation mismatches worth addressing.
Ratings are uniformly high across brands — all brands sit between 3.92–3.93, suggesting either strong product quality or potential rating inflation.
Payment methods are evenly distributed — no single payment method dominates, indicating a healthy, flexible checkout ecosystem.
March is peak revenue month — seasonal campaigns or promotions in Q1 appear effective; February is the weakest month and could benefit from targeted offers.
Lenovo leads in revenue despite not having the highest rating, suggesting high-volume or high-price-point sales over pure customer satisfaction scores.
Average Order Value (AOV) of $9.93K is high, likely skewed by Electronics; segmenting AOV by category would reveal more actionable pricing insights.

##📂 Repository Structure

amazon-ecommerce-analysis/
│
├── data/
│   └── amazon_raw.csv            # Original Kaggle dataset
│
├── notebooks/
│   └── data_cleaning.ipynb       # Python data cleaning steps
│
├── sql/
│   └── sql_queries.sql           # All MySQL queries used
│
├── dashboard/
│   └── amazon_analysis.pbix      # Power BI dashboard file
│
└── README.md

##👤 Author
Arpita Chaudhary
