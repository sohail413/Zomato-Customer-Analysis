# Zomato-Customer-Analysis
 Zomato Customer Analysis  A comprehensive end-to-end data analysis project on a simulated Zomato food delivery dataset, covering customer behaviour, order trends, restaurant performance, and delivery operations — using Python (EDA), PostgreSQL (SQL Analytics), and Power BI (Dashboard).

---

## 📌 Project Overview

This project analyses 4 interconnected datasets simulating the Zomato platform ecosystem across 5 Indian cities: **Bangalore, Mumbai, New Delhi, Pune, and Hyderabad**.

The goal is to extract actionable business insights around:
- Customer demographics and loyalty behaviour
- Order patterns, revenue, and payment preferences
- Restaurant performance and cuisine popularity
- Delivery partner efficiency and ratings

---

## 🗂️ Repository Structure

```
zomato-customer-analysis/
│
├── data/                        # Raw CSV datasets
│   ├── customers.csv
│   ├── orders.csv
│   ├── restaurants.csv
│   └── deliveries.csv
│
├── notebooks/                   # Python EDA notebooks
│   └── zomato_eda.ipynb
│
├── sql/                         # PostgreSQL analytical queries
│   └── zomato_queries.sql
│
├── dashboard/                   # Power BI dashboard screenshots
│   ├── dashboard_overview.png
│   └── dashboard_filtered.png
│
└── README.md
```

---

## 📊 Datasets

| Dataset | Rows | Columns | Description |
|---|---|---|---|
| `customers.csv` | 2,000 | 11 | Customer profile, city, loyalty points, cuisine preference |
| `orders.csv` | 3,000 | 12 | Order amount, discount, payment method, status, rating |
| `restaurants.csv` | 1,200 | 11 | Restaurant name, cuisine, city, rating, cost-for-two |
| `deliveries.csv` | 2,544 | 12 | Delivery partner, distance, pickup/drop times, tip, rating |

### Schema & Relationships

```
customers ──< orders >── restaurants
                │
           deliveries
```

**Key join columns:**
- `customers.customer_id` → `orders.customer_id`
- `restaurants.restaurant_id` → `orders.restaurant_id`
- `orders.order_id` → `deliveries.order_id`

---

## 🐍 Exploratory Data Analysis (Python)

The EDA notebook (`notebooks/zomato_eda.ipynb`) covers:

### 1. Customer Analysis
- Age distribution across cities
- Gender split and active vs. inactive customers
- Loyalty points segmentation
- Cuisine preference breakdown

### 2. Order Analysis
- Revenue distribution and top spenders
- Order status breakdown (Delivered / Cancelled / Processing)
- Payment method popularity
- Discount usage patterns
- Food prep time and delivery fee analysis

### 3. Restaurant Analysis
- Top cuisines by count and rating
- City-wise restaurant density
- Average cost-for-two by cuisine
- Open vs. closed restaurant ratio

### 4. Delivery Analysis
- Partner-wise delivery volume and average rating
- Average delivery speed (km/h) per partner
- Tip amount distribution
- Distance distribution by delivery region

---

## 🛢️ SQL Analysis (PostgreSQL)

The `sql/zomato_queries.sql` file contains **20 carefully selected queries** ranging from basic SELECT/WHERE to advanced window functions and CTEs.

### Query Highlights

| # | Topic | Technique |
|---|---|---|
| Q1 | Unique cuisines across restaurants | `DISTINCT` |
| Q2 | Active customers aged 20–30 | `WHERE`, `BETWEEN` |
| Q3 | Top 5 highest-spending orders | `ORDER BY`, `LIMIT` |
| Q4 | Cancelled orders or low-rated orders | `WHERE`, `OR` |
| Q5 | Open restaurants with 'Biryani' in name | `ILIKE`, `AND` |
| Q6 | Orders with missing feedback rating | `IS NULL` |
| Q7 | Total revenue from delivered orders | `SUM`, `WHERE` |
| Q8 | Orders count by payment method | `GROUP BY`, `COUNT` |
| Q9 | Cities with more than 10 restaurants | `HAVING` |
| Q10 | Total tips per delivery partner | `SUM`, `GROUP BY` |
| Q11 | Orders above average order value | Scalar Subquery |
| Q12 | Orders delivered by Bike | `JOIN`, `WHERE` |
| Q13 | Customers who ordered outside their city | Multi-table `JOIN` |
| Q14 | Top 3 spenders per city | `CTE`, `ROW_NUMBER()` |
| Q15 | Running total of orders per customer | `SUM() OVER()` |
| Q16 | Top-rated restaurant per city (with ties) | `RANK() OVER()` |
| Q17 | Each order's % contribution to restaurant revenue | `PARTITION BY` |
| Q18 | Customers categorised by age tier with avg spend | `CASE`, `CTE` |
| Q19 | Average delivery speed per partner (km/h) | `EXTRACT EPOCH`, `CTE` |
| Q20 | Churned customers: loyal but inactive in 2026 | Subquery, Date filter |

---

## 📈 Power BI Dashboard

An interactive dashboard was built in Power BI with filters for **Status**, **Gender**, **Preferred Cuisine**, and **City**.

### Dashboard – Full View
![Dashboard Overview](dashboard/dashboard_overview.png)

### Dashboard – Filtered: Male, Biryani preference, Hyderabad
![Dashboard Filtered](dashboard/dashboard_filtered.png)

### Visuals Included
- **Loyalty Points Treemap** — by city
- **Active Customer Status by City** — horizontal bar chart
- **Delivery Partner Rating** — bar chart (Swiggy Partner, Shadowfax, Dunzo, Zomato Valet)
- **Sales by City** — vertical bar chart (New Delhi leads at ₹744K)
- **Payment Method Table** — sum of discounts and final amounts

### Key Dashboard Insights
| Metric | Value |
|---|---|
| Total Revenue | ₹34,56,880 |
| Total Discount Applied | 38,860 |
| Highest Sales City | New Delhi (₹744K) |
| Top Delivery Partner (Rating) | Swiggy Partner & Shadowfax (2.8K) |
| Most Used Payment Method | UPI (773 orders) |

---

## 🔍 Key Business Insights

1. **New Delhi** leads in total sales (₹744K), followed by Bangalore (₹732K) — indicating a stronger urban ordering base in North India.
2. **66.35%** of customers are active, with a mean loyalty score of **2,471 points** — a strong retention signal.
3. **UPI** is the most popular payment method, reflecting India's digital payment adoption.
4. **Swiggy Partner and Shadowfax** lead delivery ratings, while **Zomato Valet** has the lowest average rating (2.6K).
5. **84.8%** of orders are successfully delivered; a 9.9% cancellation rate warrants further root cause analysis.
6. **Asian and South Indian** are the most preferred cuisines among customers, while **Desserts** dominate the restaurant supply.
7. Customers who joined before 2025 with high loyalty points but no 2026 orders represent a **churn risk segment** worth targeting with re-engagement campaigns.

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| Python (pandas, matplotlib, seaborn) | Exploratory Data Analysis |
| PostgreSQL | SQL-based business queries |
| Power BI | Interactive dashboard |
| Jupyter Notebook | EDA documentation |

---

## 🚀 Getting Started

### Run the EDA Notebook
```bash
pip install pandas matplotlib seaborn jupyter
jupyter notebook notebooks/zomato_eda.ipynb
```

### Run SQL Queries
```sql
-- Connect to your PostgreSQL instance and import the CSVs as tables:
-- customers, orders, restaurants, deliveries
-- Then execute queries from sql/zomato_queries.sql
```

---

## 👤 Author

**[Your Name]**  
Data Analyst | Python • SQL • Power BI  
[LinkedIn](#) · [GitHub](#)

---

## 📄 License

This project uses a simulated dataset for educational and portfolio purposes only. Not affiliated with Zomato.
