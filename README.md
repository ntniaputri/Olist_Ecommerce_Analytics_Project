# 📈 Olist E-commerce Data Analysis 📊

---

## ✨ Project Overview ✨

This project analyzes Olist Store’s sales and customer data from **January 2017 to August 2018**, aiming to uncover performance trends and buyer behavior that can inform business growth strategies.

The dataset contains detailed records of orders, products, customers, reviews, and transaction values. By integrating these tables, we created a unified dataset of around 99,000 records after filtering for the analysis period. A general product category field was also introduced to group similar items for clearer insights. This analysis focuses on four key areas:
* **Sales Trends**: Identify growth patterns, seasonality, and promotional impact (e.g., Black Friday) using temporal metrics like average order value, transaction volume, and total sales.
* **Product Performance**: Assess contributions of top categories and products, detect underperformers, and identify unique or seasonal trends.
* **Customer Behavior & Retention**: Analyzes customer purchasing patterns by segmenting new vs. repeat buyers, identifying order frequency, and comparing spending levels. Assess satisfaction through review scores and explore retention trends using cohort analysis to uncover loyalty patterns, repeat purchase rates, and the long-term value of returning customers.

* Data was initially inspected and prepared using Microsoft Excel.
* Interactive dashboards and analyses are available in Tableau: 🔗 https://public.tableau.com/views/OlistE-commerceDashboardFinal/CustomerDashboard2?:language=en-GB&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link

---

## 🔍 Data Structure & Initial Checks 📋

The Olist e-commerce dataset is structured into multiple relational tables capturing different aspects of the business process including orders, order items, customers, reviews, and geolocations. For the purpose of this analysis, key tables were joined and aggregated into a single, analysis-ready table to simplify tracking sales trends and customer behavior.
![image](https://github.com/user-attachments/assets/8aa2551b-d973-4daf-9602-1881825ae8e4)
Key fields used in this dataset include:

* `order_id`: Unique ID for each order, used to link across tables.
* `order_status`: Indicates the current state of the order (e.g., delivered, shipped, canceled).
* `order_approved_at`, `order_delivered_carrier_date`, `order_delivered_customer_date`: Key timestamps capturing order lifecycle events.
* `product_id`: Unique identifier of each product included in the order.
* `order_item_id`: Identifies individual items within a multi-item order.
* `price` and `freight_value`: Represent the product price and its shipping cost.
* `customer_id`: Internal ID linking orders to customers.
* `customer_unique_id`: A persistent ID that uniquely identifies customers across all their orders (useful for retention or cohort analysis).
* `customer_city` and `customer_state`: Geographic attributes for customer segmentation.
* `review_id` and `review_score`: Link each order to its customer review and satisfaction level.

Before beginning the analysis, initial data checks showed ~100,000 records. After cleaning, filtering for January 2017 to August 2018, and combining key tables, the final dataset contained ~99,000 records. Review data was cleaned in Excel, and SQL was used to aggregate order, product, customer, and review data into a single table. A product_category_general field was added to group detailed categories into broader ones for easier analysis. All visualizations were done in Tableau. SQL queries used can be found here.

---

## 🌟 Executive Summary 🌟

* Olist's sales are heavily driven by seasonal promotions, generating high transaction volumes despite fluctuating Average Order Value.
* Product performance relies significantly on event-driven demand, with top categories leading but many items showing only temporary spikes.
* Strong new customer acquisition contrasts with poor long-term retention, as repeat rates are minimal despite high customer satisfaction.
* Few but high-value repeat customers and a highly concentrated urban market like São Paulo present key targets for focused growth strategies.

---

## 📈 Sales Trends 📈
![image](https://github.com/user-attachments/assets/383c3187-4e16-44c7-963d-b0c0473f2323)
* **Average Transaction Value (ATV):** ATV peaked at $143.13 in January 2017, subsequently declining to $119.10 by July 2017 and ending the period at $127.27 in August 2018. The W-shaped trend observed throughout 2017 included November (Black Friday), where an ATV of $128.96, amidst record-high transaction volume and total sales, strongly suggests a surge driven by promotional pricing. In 2018, ATV showed a peak of $138.68 in May before a gradual decline.
* **Transaction Volume:** Transaction volume reached its highest point with 7,319 orders in November 2017. After maintaining robust figures, it saw a decline to 6,162 orders by July 2018. The period began with a consistent growth throughout 2017 from an initial 747 orders in January, demonstrating sustained order activity into early 2018.
* **Total Sales Value:** Total sales value reached a peak of $943,878.71 in November 2017 and a 2018 peak of $986,181.57 in May. By August 2018, it tapered to $850,774.15. Overall, sales climbed significantly from $106,921.27 in January 2017, showing strong foundational growth before a moderate decline towards the end of the analyzed period.
* **Sales Performance by Time Granularity:**
    * Monthly Peaks: November 2017 ($943,878.71) and May 2018 ($986,181.57).
    * Weekly Spike: A sharp increase to $343,714.09 during the week of October 29, 2017.
    * Daily Trends: Tuesdays consistently generated the highest daily sales $2,438,741.67), while Sundays recorded the lowest ($1,168,868.78).

---

## 📦 Product Insights 📦
![image](https://github.com/user-attachments/assets/0f1cd55e-26b7-492f-b1fe-9ce52d39dfa1)
* **Hobbies, Arts & Party Supplies:** Led with $2.25M (17.45%), peaking at $188.4K (Nov 2017), due to diverse offerings.
* **Home & Living Goods:** Second highest in sales at $2.20M (17.09%). This category peaked at $187.5K in May 2018, largely driven by its bed, bath, and table products and typical seasonal demand.
* **Electronics & Gadgets:** Generated $1.81M (14.02%), peaking at $149.5K (Feb 2018), possibly tied to tech cycles.
* **Health & Beauty** ($1.61M) and **Fashion & Personal Accessories** ($1.49M) showed consistent growth with late-period peaks.
* **Top Sellers:** Health, beauty ($1.22M), watches, gifts ($1.16M), and bed, bath, and table ($1.02M) were top sellers, each exceeding averages.
* **Lower Performers:** Garden tools ($466K) and cool stuff ($603K) showed lower sales and flatter trends, indicating limited demand.
* **Widespread Seasonal Surges:** Most categories saw significant sales spikes in November 2017 (Black Friday) and recurring seasonal peaks between January and August 2018, indicating a strong response to retail promotion cycles.

---

## 🤝 Customer Behavior 🧑‍🤝‍🧑
![image](https://github.com/user-attachments/assets/fd519516-34c9-4e30-9146-2f7b138f71d0)
![image](https://github.com/user-attachments/assets/16bf883b-03d1-47ad-8c1c-7510d91f06d6)
* **New Customer Dominance:** New customers overwhelmingly dominate the monthly active base (e.g., Aug 2018: 6,481 new vs. 204 repeat).
* **Repeat Customer Value:** Despite low volume, repeat customers generate 2.13% of total revenue ($275K), indicating a higher average spend.
* **Low Repeat Activity & Poor Retention:** Repeat customers constitute a minimal portion of the monthly active base (1-3%). This is reflected in cohort analysis, which shows poor long-term retention, with most cohorts dropping to 0.3-0.4% by Month 4.
* **High Customer Satisfaction:** Customer satisfaction is high: 77.47% positive reviews (58.15% are 5-star).
* **Geographic Concentration:** The customer base is highly concentrated, with São Paulo accounting for 41.5% of customers.
* **Urban-Centric Market:** The top 5 states comprise nearly 70% of the customer base, highlighting an urban-centric market.

---

## 💡 Recommendations 💡

* Maximize key sales periods (Nov, May) and Tuesday daily peaks, optimizing AOV during promotions.
* Prioritize top product categories (Hobbies & Arts, Home & Living) and leading items like health and beauty, re-evaluate underperformers to shift from event-driven sales.
* Tackle low repeat rates and poor retention with immediate, personalized re-engagement for new customers, leveraging high satisfaction.
* Focus growth efforts on high-value repeat customers and the dense São Paulo market, while exploring other top states.
