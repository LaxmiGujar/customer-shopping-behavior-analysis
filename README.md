# Customer Shopping Behavior Analysis

End-to-end analysis of **3,900 retail customers** using **Python, SQL (PostgreSQL) and Power BI**. The project cleans the data, builds customer segments, answers business questions on revenue, discounts, subscriptions, shipping and product ratings, and presents the results in an interactive dashboard.

![Dashboard preview](dashboard/<img <img width="332" height="194" alt="Dashbord1" src="https://github.com/user-attachments/assets/3c3e0047-0eee-48a4-a61c-101186d4a77b" />
width="344" height="200" alt="Dashbord" src="https://github.com/user-attachments/assets/8eb98637-4609-415d-bd93-5a2a5f060c0f" />.png)

## Dataset

- **Rows:** 3,900 customers (one row per customer)
- **Columns (18):** customer_id, age, gender, item_purchased, category, purchase_amount_usd, location, size, color, season, review_rating, subscription_status, shipping_type, discount_applied, promo_code_used, previous_purchases, payment_method, frequency_of_purchases
- **Missing values:** 37 review ratings (about 1%)
- **Source:** *add the source link here, for example Kaggle, or write "sample dataset"*

> Note: each row is one purchase per customer, so "revenue" here means one purchase per customer, not lifetime value.

## Tools Used

| Tool | Purpose |
|---|---|
| **Python** (pandas, matplotlib, seaborn) | Data cleaning, feature engineering, exploratory analysis |
| **SQL** (PostgreSQL) | Table design with constraints, analytical queries |
| **Power BI** | Interactive dashboard |
| **Excel / CSV** | Cleaned dataset formats |

## Project Workflow

1. **Load and inspect** the data (shape, data types, summary statistics, duplicates, missing values).
2. **Clean:** filled the 37 missing review ratings with the **median rating of each product category**, and converted Yes/No columns to True/False.
3. **Feature engineering (Python):**
   - `age_group`: 18-25, 26-35, 36-45, 46-55, 56-65, 66+
   - `customer_segment`: New (1 previous purchase), Returning (2-10), Loyal (11+)
4. **Analyse** business questions in Python and SQL.
5. **Visualise** the results in Power BI.

## Business Questions Answered

**Python notebook (10 questions)**
1. Revenue by gender
2. Discount users who spent at or above the average purchase
3. Top 5 products by average review rating
4. Average purchase: Standard vs Express shipping
5. Subscribers vs non-subscribers (customers, average spend, total revenue)
6. Top 5 products by discount rate
7. Customer segment counts
8. Top 3 products within each category
9. Whether repeat buyers (more than 5 purchases) subscribe
10. Revenue by age group

**SQL (7 queries)**: row count, revenue by gender, discount users above average spend, top-rated products, Standard vs Express shipping, subscribers vs non-subscribers, and top discounted products.

## Key Findings

| Area | Finding |
|---|---|
| **Overall** | Total revenue $233,081 · average purchase $59.76 · average rating 3.75 |
| **Category** | Clothing generates about 45% of revenue ($104,264), followed by Accessories ($74,200), Footwear ($36,093) and Outerwear ($18,524) |
| **Gender** | Men $157,890 vs women $75,191. Average spend per purchase is nearly identical ($59.54 vs $60.25), so the gap comes from customer count, not spending |
| **Subscription** | Subscribers (1,053) spend about the same as non-subscribers (2,847): $59.49 vs $59.87 |
| **Repeat buyers** | Of 3,476 customers with more than 5 previous purchases, 2,518 (about 72%) are not subscribed, which suggests a loyalty-program opportunity |
| **Shipping** | Express averages $60.48 vs Standard $58.46 |
| **Discounts** | 43% of purchases used a discount. Hat (50%), Sneakers (49.7%) and Coat (49.1%) are discounted most often |
| **Ratings** | Top rated: Gloves 3.86, Sandals 3.84, Boots 3.82, Hat 3.80, Handbag 3.78 (a narrow range) |
| **Age** | The 46-55 group contributes the most revenue ($45.6K); 66+ the least ($20.9K) |
| **Segments** | Loyal 3,116 · Returning 701 · New 83 |

## Dashboard

The Power BI dashboard (`dashboard/customer_shopping_behaviour_analysis.pbix`) includes:
- KPI cards: Average Purchase Amount, Average Review Rating, Number of Customers
- Revenue and customer count by category
- Review rating distribution
- Subscription breakdown by season
- Slicers for subscription status, color and category

Open the `.pbix` file with Power BI Desktop (free for Windows).

## Repository Structure

```
customer-shopping-behavior-analysis/
├── data/
│   ├── customer_shopping_behavior_clean.csv
│   └── customer_shopping_behavior_clean.xlsx
├── notebooks/
│   └── shoppingData.ipynb
├── sql/
│   └── sql_que.sql
├── dashboard/
│   ├── customer_shopping_behaviour_analysis.pbix
│   └── dashboard_preview.png
└── README.md
```

## How to Run

**Python notebook**
```bash
pip install pandas matplotlib seaborn jupyter
jupyter notebook notebooks/shoppingData.ipynb
```
The notebook reads the dataset with a relative path. If you keep the folder layout above, change the load line to:
```python
df = pd.read_csv("../data/customer_shopping_behavior_clean.csv")
```

**SQL**
1. Create a PostgreSQL database.
2. Run `sql/sql_que.sql`. It creates the table, loads all 3,900 rows and runs the queries.

## Limitations

- The SQL queries use the raw ratings, so the 37 missing values stay NULL, while the Python analysis fills them with category medians. Rating results may differ slightly.
- Customer segmentation and the repeat-buyer analysis are done in Python only.
- The data has one purchase per customer, so trends over time and lifetime value cannot be measured.

## Author

**Laxmi Gujar** · [LinkedIn](https://www.linkedin.com/in/laxmi-g-gujar-287076245/) · [GitHub](https://github.com/LaxmiGujar)
