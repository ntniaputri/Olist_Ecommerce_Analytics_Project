# Project Background

Olist is Brazil’s largest department store across marketplaces, enabling small businesses to sell through major e-commerce platforms. This project analyzes Olist Store’s sales and customer data from January 2017 to August 2018, aiming to uncover performance trends and buyer behavior that can inform business growth strategies.

The dataset contains detailed records of orders, products, customers, reviews, and transaction values. By integrating these tables, we created a unified dataset of around 99,000 records after filtering for the analysis period. A general product category field was also introduced to group similar items for clearer insights. This analysis focuses on four key areas:

- **Sales Trends**: Identify growth patterns, seasonality, and promotional impact (e.g., Black Friday) using temporal metrics like average order value, transaction volume, and total sales.
- **Product Performance**: Assess contributions of top categories and products, detect underperformers, and identify unique or seasonal trends.
- **Customer Behavior & Retention**: Analyzes customer purchasing patterns by segmenting new vs. repeat buyers, identifying order frequency, and comparing spending levels. Assess satisfaction through review scores and explore retention trends using cohort analysis to uncover loyalty patterns, repeat purchase rates, and the long-term value of returning customers.

---

# Data Structure & Initial Checks

The Olist e-commerce dataset is structured into multiple relational tables capturing different aspects of the business process including orders, order items, customers, reviews, and geolocations. For the purpose of this analysis, key tables were joined and aggregated into a single, analysis-ready table to simplify tracking sales trends and customer behavior.

**Key fields used in this dataset include:**

- `order_id`: Unique ID for each order, used to link across tables.
- `order_status`: Indicates the current state of the order (e.g., delivered, shipped, canceled).
- `order_approved_at`, `order_delivered_carrier_date`, `order_delivered_customer_date`: Key timestamps capturing order lifecycle events.
- `product_id`: Unique identifier of each product included in the order.
- `order_item_id`: Identifies individual items within a multi-item order.
- `price` and `freight_value`: Represent the product price and its shipping cost.
- `customer_id`: Internal ID linking orders to customers.
- `customer_unique_id`: A persistent ID that uniquely identifies customers across all their orders (useful for retention or cohort analysis).
- `customer_city` and `customer_state`: Geographic attributes for customer segmentation.
- `review_id` and `review_score`: Link each order to its customer review and satisfaction level.

This consolidation enables efficient analysis of product performance, delivery timelines, and customer satisfaction.

Before beginning the analysis, initial data checks showed ~100,000 records. After cleaning, filtering for January 2017 to August 2018, and combining key tables, the final dataset contained ~99,000 records. Review data was cleaned in Excel, and SQL was used to aggregate order, product, customer, and review data into a single table. A `product_category_general` field was added to group detailed categories into broader ones for easier analysis. All visualizations were done in Tableau. SQL queries used can be found here.

---

# Executive Summary

- Olist’s sales performance is heavily driven by seasonal promotions, revealing strong short-term gains but limited year-round consistency.
- While a few top product categories deliver steady revenue, many items rely on temporary hype or discounts, signaling a need for a more balanced product mix.
- The platform excels at acquiring new customers, but the vast majority do not return—despite high satisfaction—highlighting a major retention challenge.
- Repeat customers, though few, are high-value; targeting them more effectively could unlock meaningful growth, especially in key urban markets like São Paulo.

---

# Sales Trends

- **AOV** peaked at **$154.95 (Jan 2017)** and **$151.99 (Apr 2017)** before dropping to **$126.46 (Jul 2017)**. After a short rebound in Oct (**$145.97**), it declined again by Dec (**$132.60**). During Black Friday (**Nov 2017**), AOV was **$136.22**, indicating discount-driven purchases. A similar W-shaped pattern appeared in 2018, rising to **$144.78 (Apr)** then falling to **$133.04 (Aug)**.
- **Transaction volume** grew steadily from **726 (Jan 2017)** to **7,039 (Nov 2017)**, with the highest weekly spike reaching **$348K (Oct 29, 2017)**. Volumes stayed high in early 2018 (**6,818 in Jan**, **6,970 in Mar**) but dropped to **5,982 (Jul)**, reflecting seasonal promo cycles and a mid-year slowdown.
- **Total sales value** climbed from **$112K (Jan 2017)** to **$1.03M (Nov 2017)**, remaining strong in early 2018 (**$954K in Jan**, **$996K in May**) before tapering to **$859K (Aug)**.

**Time trends:**
- **Monthly**: Peaks in **Nov 2017 ($958K)** and **May 2018 ($996K)**
- **Weekly**: Sharp spike in **late Oct 2017 ($348K)**
- **Daily**: Highest on **Tuesdays ($2.47M)**, lowest on **Sundays ($1.19M)**

---

# Product Insights

- **Hobbies, Arts & Part Supplies** led all categories with **$2.3M (17.5%)**, peaking in **Nov 2017 ($191K)**, driven by its wide product base.
- **Home & Kitchen Goods** followed at **$2.2M (17%)**, mostly from **bed_bath_table ($1.02M)**, which peaked in **May 2018 ($188K)**—likely reflecting seasonal demand.
- **Electronics & Gadget** generated **$1.85M (14.1%)**, peaking in **Feb 2018 ($152K)**—possibly tied to tech product cycles.
- **Health & Beauty ($1.62M)** and **Fashion & Personal Accessories ($1.51M)** showed steady growth and late-2018 peaks.
- **Top-performing products** include **health_beauty ($1.23M)**, **watches_gifts ($1.18M)**, and **bed_bath_table ($1.02M)**—each surpassing their category averages.
- **Underperformers** like **garden_tools ($476K)** and **cool_stuff ($620K)** had lower peaks and flatter curves.
- Some categories (e.g., **Toys, Sports**) spiked around **Black Friday**, highlighting promo-driven surges.
- Others (e.g., **telephony, audio**) peaked early in 2017, then plateaued—suggesting one-time demand or early hype.
- Seasonal peaks were common from **May to Nov 2018**, aligning with retail promotion cycles.

---

# Customer Behavior

- New customers dominate, showing strong acquisition. **Repeat customers account for just 6.6%** of total transactions.
- The **repeat purchase rate holds steady at ~6–7%**, with most returning within 2–3 months.
- **Cohort analysis confirms poor long-term retention**—top cohorts from **Sep–Oct 2017 drop below 0.3% by Month 4**.
- Despite their low volume, **repeat customers generate 22.8% of total revenue**, indicating higher spend per user.
- **Customer satisfaction is high** (avg. rating **4.1**), with **88% positive reviews** (including **57.8% 5-star ratings**). However, high satisfaction doesn’t translate to loyalty.
- Geographically, **41.5% of customers are from São Paulo**, with the **top 5 states making up nearly 70%** of the base—highlighting a dense, urban market.

---

# Recommendations

- Capitalize on strong sales months like **May and November** with well-timed promotions and inventory planning. Use bundled or value-added offers during discount-heavy events to protect margins.
- Invest more in **top-performing categories** such as **Hobbies & Arts** and **Home & Kitchen**, while reconsidering or optimizing underperformers like **garden_tools** and **cool_stuff**.
- Introduce **loyalty programs** and **personalized re-engagement strategies** to improve low repeat rates, especially within the first **30–60 days** after a purchase.
- Focus acquisition efforts on **dense urban areas like São Paulo** while testing regional campaigns to unlock growth in less saturated markets.
