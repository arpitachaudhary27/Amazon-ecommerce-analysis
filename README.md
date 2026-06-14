# 🛒 Amazon E-commerce Analysis

## 📋 Project Overview

This project presents an **end-to-end data analysis** of Amazon sales data, covering the complete pipeline from raw data collection to interactive dashboard creation.

The objective is to uncover meaningful insights into:

- Customer behavior
- Product performance
- Revenue trends
- Operational efficiency
- Business decision-making

---

# 🔄 Project Workflow

```
Kaggle Dataset
        │
        ▼
Python (Jupyter Notebook)
Data Cleaning & Preprocessing
        │
        ▼
MySQL 8.4
Data Storage & SQL Analysis
        │
        ▼
Power BI
Interactive Dashboard
```

---

# 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| Kaggle | Dataset Source |
| Python (Pandas, NumPy) | Data Cleaning & Preprocessing |
| Jupyter Notebook | Data Exploration |
| MySQL 8.4 | Data Storage & SQL Analysis |
| Power BI | Dashboard & Visualization |

---

# 📥 Data Collection

**Dataset Source:** Kaggle

### Dataset Details

- 1,000,000 Order Records
- Customer Information
- Product Details
- Brand Information
- Location Data
- Payment Methods
- Delivery Status
- Ratings

---

# 🧹 Data Cleaning (Python)

Performed the following preprocessing steps using **Pandas**:

- ✅ Removed duplicate records
- ✅ Handled missing/null values
- ✅ Standardized data types
- ✅ Removed invalid/inconsistent records
- ✅ Exported cleaned data for MySQL

---

# 🗄️ Database Setup

**Database:** `amazon_project`

**Table:** `orders`

---

# 📊 SQL Analysis

## 1. Total Revenue

```sql
SELECT SUM(final_price) AS Total_Revenue
FROM orders;
```

**Result**

| Total Revenue |
|--------------:|
| 9,938,876,984.90 |

---

## 2. Top 10 Brands by Revenue

```sql
SELECT brand,
       SUM(final_price) AS revenue
FROM orders
GROUP BY brand
ORDER BY revenue DESC
LIMIT 10;
```

| Brand | Revenue |
|--------|-------------:|
| Lenovo | 834,698,265.13 |
| Sony | 832,227,170.84 |
| Samsung | 831,559,760.41 |
| LG | 831,268,886.51 |
| Adidas | 828,076,829.78 |
| Boat | 827,732,261.87 |
| HP | 826,993,652.68 |
| Nike | 826,645,590.46 |
| Zara | 826,028,195.52 |
| Apple | 826,003,980.43 |

---

## 3. Revenue by Category

```sql
SELECT category,
       SUM(final_price)
FROM orders
GROUP BY category;
```

| Category | Revenue |
|-----------|---------------:|
| Electronics | 6,579,047,983.30 |
| Home | 1,529,977,638.32 |
| Sports | 1,124,849,199.33 |
| Beauty | 375,951,719.91 |
| Clothing | 329,050,444.04 |

---

## 4. Average Rating by Brand

```sql
SELECT brand,
       AVG(rating)
FROM orders
GROUP BY brand
ORDER BY AVG(rating) DESC;
```

### Top Brands

| Brand | Average Rating |
|--------|--------------:|
| Sony | 3.93 |
| Samsung | 3.93 |
| Lenovo | 3.93 |
| H&M | 3.93 |
| Zara | 3.93 |

---

## 5. Orders by Payment Method

```sql
SELECT payment_method,
       COUNT(*)
FROM orders
GROUP BY payment_method;
```

| Payment Method | Orders |
|----------------|-------:|
| Cash on Delivery | 250,388 |
| Credit Card | 250,324 |
| UPI | 249,951 |
| Debit Card | 249,337 |

**Insight**

Payment methods are almost evenly distributed across all four payment options.

---

# 📈 Power BI Dashboard

Three interactive dashboards were created using Power BI.

---

## 📊 Dashboard 1 — Overview

### KPIs

- Total Customers: **1M**
- Products: **90K**
- Orders: **1M**
- Revenue: **$9.90B**
- Average Rating: **3.93**

### Visuals

- Revenue KPI Cards
- Category Treemap
- Monthly Order Trend
- Return Rate by Category
- Payment Method Distribution

---

## 📦 Dashboard 2 — Products

### KPIs

- 5 Categories
- 12 Brands
- Average Revenue
- Average Rating
- Top Category

### Visuals

- Rating Distribution
- Revenue by Category
- Delivery Status
- Brand Performance Table

---

## 👥 Dashboard 3 — Customers

### KPIs

- Total Customers: **82K**
- Top City: **Delhi**
- Revenue: **$9.90B**
- Average Order Value: **$9.93K**

### Visuals

- Customer Journey Funnel
- Orders by Location
- Device Type Analysis
- Payment Method Distribution

---

# 📊 Dashboard Screenshots

> Since the Power BI (.pbix) file exceeds GitHub's upload limit, dashboard screenshots are provided in the repository.

### Dashboard Overview

![Overview](https://raw.githubusercontent.com/arpitachaudhary27/Amazon-ecommerce-analysis/main/Power%20BI%20visualization/overview_page.png)


### Product Dashboard

![Products](https://raw.githubusercontent.com/arpitachaudhary27/Amazon-ecommerce-analysis/main/Power%20BI%20visualization/Products.png)


### Customer Dashboard

![Customers](https://raw.githubusercontent.com/arpitachaudhary27/Amazon-ecommerce-analysis/main/Power%20BI%20visualization/Customers.png)

---

# 💡 Key Business Insights

- Electronics contributes **66%** of total revenue.
- Revenue is evenly distributed across all five cities.
- Beauty and Clothing categories have the highest return rates.
- Customer ratings remain consistently high across brands.
- Payment methods are evenly distributed.
- March generated the highest revenue.
- Lenovo generated the highest revenue among all brands.
- Average Order Value (AOV) is approximately **₹9.93K**.

---

# 📂 Repository Structure

```
amazon-ecommerce-analysis/
│
├── Data/
│
├── Data cleaning/
│   └── data_cleaning.ipynb
│
├── SQL Queries/
│   └── sql_queries.sql
│
├── Power BI visualization/
│   ├── overview.png
│   ├── products.png
│   ├── customers.png
│
└── README.md
```

---


# 👤 Author

**Arpita Chaudhary**

**Aspiring Data Analyst**

