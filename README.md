# Customer Shopping Behavior Analysis

A full end-to-end data analytics project analyzing 3,900 customer transactions to uncover spending patterns, customer segments, discount dependencies, and subscription behavior — with actionable business recommendations.

**Tools used:** Python (Pandas) · PostgreSQL · Power BI

---

## Problem Statement

A retail business wants to understand how customers shop — who spends the most, which products drive revenue, whether discounts are hurting or helping, and how to convert more buyers into loyal subscribers.

---

## Project Workflow

```
Raw Data → Python EDA & Cleaning → PostgreSQL (SQL Analysis) → Power BI Dashboard → Business Recommendations
```

---

## 1. Python — Data Cleaning & EDA

**File:** `customer_behaviour_analysis.ipynb`

- Loaded 3,900-row dataset with 18 columns using Pandas
- Handled 37 missing values in `Review Rating` — imputed using **median rating per product category**
- Renamed all columns to snake_case for consistency
- Feature engineering:
  - Created `age_group` by binning customer ages (Young Adult / Adult / Middle-aged / Senior)
  - Created `purchase_frequency_days` from purchase frequency labels
- Identified and dropped `promo_code_used` as redundant with `discount_applied`
- Connected Python to PostgreSQL using `psycopg2` and loaded cleaned DataFrame into the database

---

## 2. SQL — Business Questions Answered

**File:** `analysis_queries.sql` | **Database:** PostgreSQL

| # | Question | Key Finding |
|---|----------|-------------|
| 1 | Revenue by Gender | Male customers generated $157,890 vs Female $75,191 |
| 2 | High-Spending Discount Users | 839 customers used discounts yet spent above average |
| 3 | Top 5 Products by Rating | Gloves (3.86), Sandals (3.84), Boots (3.82) |
| 4 | Shipping Type Comparison | Express avg $60.48 vs Standard $58.46 |
| 5 | Subscribers vs Non-Subscribers | Avg spend nearly equal (~$59.49 vs $59.87) — subscribers are not higher spenders |
| 6 | Discount-Dependent Products | Hat (50%), Sneakers (49.66%), Coat (49.07%) most discount-reliant |
| 7 | Customer Segmentation | Loyal: 3,116 · Returning: 701 · New: 83 |
| 8 | Top 3 Products per Category | Used `RANK()` window function — Jewelry, Blouse, Sandals, Jacket lead their categories |
| 9 | Repeat Buyers & Subscriptions | 2,518 repeat buyers are non-subscribers — a clear conversion opportunity |
| 10 | Revenue by Age Group | Young Adults contribute the most ($62,143), Seniors the least ($55,763) |

---

## 3. Power BI Dashboard

**File:** `Customer_behaviour_Dashboard.pbix`

Key KPIs displayed:
- **3.9K** Total Customers
- **$59.76** Average Purchase Amount
- **3.75** Average Review Rating

Visuals included:
- Subscription status breakdown (Yes 27% / No 73%)
- Revenue and Sales by Category (Clothing leads)
- Revenue and Sales by Age Group
- Slicers: Subscription Status, Gender, Category, Shipping Type

![Dashboard Preview](dashboard_screenshot.png)

---

## Key Insights

1. **Subscriptions are underutilized** — 73% of customers are non-subscribers, yet avg spend is nearly identical to subscribers. There's no incentive strong enough to convert.
2. **Discounts don't deter spending** — 839 customers used discounts AND spent above average, suggesting discounts attract genuine high-value buyers.
3. **Young Adults are the highest-revenue segment** — despite likely lower per-order spend, they transact more frequently.
4. **Repeat buyers resist subscribing** — 2,518 repeat buyers (>5 purchases) have not subscribed. Targeted conversion campaigns here would have the highest ROI.
5. **Half of Hat and Sneaker sales depend on discounts** — these products need pricing strategy review; full-price demand is weak.

---

## Business Recommendations

| Recommendation | Based On |
|----------------|----------|
| Launch a loyalty-to-subscription conversion campaign targeting the 2,518 repeat non-subscribers | SQL Query 9 |
| Re-evaluate discount strategy for Hat, Sneakers, Coat — test price sensitivity | SQL Query 6 |
| Focus marketing spend on Young Adults and Middle-aged segments | SQL Query 10 |
| Promote top-rated products (Gloves, Sandals, Boots) in email campaigns | SQL Query 3 |
| Offer Express Shipping incentives — these customers already spend more | SQL Query 4 |

---

## Dataset

- **Source:** [Kaggle — Customer Shopping Trends Dataset](https://www.kaggle.com/datasets/iamsouravbanerjee/customer-shopping-trends-dataset)
- **Rows:** 3,900 | **Columns:** 18
- **Key fields:** Age, Gender, Location, Item Purchased, Category, Purchase Amount (USD), Season, Subscription Status, Discount Applied, Review Rating, Previous Purchases, Frequency of Purchases

---

## How to Run

1. Clone the repo
2. Run `customer_behaviour_analysis.ipynb` to clean data and load to PostgreSQL
3. Run `analysis_queries.sql` in PostgreSQL (pgAdmin or psql)
4. Open `Customer_behaviour_Dashboard.pbix` in Power BI Desktop

---

## Author

**Wani Uzair** · [LinkedIn](https://linkedin.com/in/your-profile) · [GitHub](https://github.com/waniuzair17)

