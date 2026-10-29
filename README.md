# 🛒 Brazilian E-Commerce Customer Behavior & Profitability Analysis
*An end-to-end data analytics project modeling the Google Data Analytics Capstone framework.*

[![Python](https://img.shields.io/badge/Python-3.11+-blue.svg)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data%20Wrangling-orange.svg)](https://pandas.pydata.org/)
[![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-green.svg)](https://seaborn.pydata.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## 📌 Executive Summary
This project analyzes **100,000+ real commercial orders** (2016–2018) from Olist, the largest department store marketplace in Brazil. By connecting disparate data tables—including customer locations, order items, product attributes, payment logs, and review scores—this analysis uncovers critical supply chain bottlenecks, regional fulfillment variances, and top-performing product categories to provide actionable strategic recommendations for marketplace operators.

---

## 🔍 The 6-Phase Google Data Analytics Framework

### 1. Ask (Business Problem & Objectives)
Olist connects small-to-medium merchants across Brazil to major digital sales channels. Operating at scale introduces logistical friction and margin pressures. This project answers four core business questions:
* **Logistics:** Which Brazilian states experience the highest frequency of delivery delays and longest fulfillment cycles?
* **Profitability:** Which product categories generate the highest Gross Merchandise Value (GMV) vs. those facing high freight-to-price ratios?
* **Customer Value:** Where is the primary customer base geographically concentrated?
* **Operational Efficiency:** How do estimated delivery dates compare against actual customer delivery dates?

---

### 2. Prepare (Data Architecture & Credibility)
* **Dataset Source:** Publicly available Brazilian E-Commerce Dataset by Olist hosted on [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce).
* **Data Structure:** Relational schema spanning 9 tables (`customers`, `orders`, `order_items`, `payments`, `reviews`, `products`, `sellers`, `geolocation`, and `category_name_translation`).
* **ROCC Evaluation:** 
  * **Reliable:** Sourced directly from real commercial transactional logs with anonymized user data.
  * **Original:** First-party data published directly by Olist.
  * **Comprehensive:** Captures the complete lifecycle from order placement and payment to carrier dispatch and final review.
  * **Current:** Historical multi-year longitudinal window (2016–2018) ideal for macro-level trend analysis.

---

### 3. Process (Data Cleaning & Transformation)
Data cleaning and manipulation were performed using **Python (Pandas)** in Jupyter Notebooks:
* Converted raw date-string columns into native datetime objects (`order_purchase_timestamp`, `order_delivered_customer_date`, `order_estimated_delivery_date`, etc.).
* Handled missing values in unfulfilled/canceled order records (`order_status` tracking).
* Engineered new calculated metrics:
  * `delivery_days`: Total time elapsed from purchase to customer delivery.
  * `shipping_delay_days`: Variance between actual delivery and estimated delivery dates.
  * `is_late`: Binary indicator flag for delayed shipments.
* Performed multi-table relational joins to combine customers, order items, products, and English category translations into a master analytical dataframe ($112,650 \text{ rows} \times 30 \text{ columns}$).

---

### 4. Analyze (Exploratory Data Analysis)
* **Logistics Bottlenecks:** States like **Alagoas (AL)** and **Maranhão (MA)** experience average delivery windows exceeding 21–24 days, with late delivery rates climbing between **20% and 23%**.
* **Revenue Leaders:** **`health_beauty`** leads total gross revenue at over **R$ 1.25M**, followed closely by **`watches_gifts`** (commanding a high average price point of ~R$ 201) and **`bed_bath_table`** (leading in sales volume with over 11,100 items sold).
* **Delivery Buffer:** On average, Olist orders arrived **11.1 days earlier** than estimated delivery dates, showing overall conservative estimation buffers offset by extreme long-tail transit outliers.

---

### 5. Share (Data Visualization)
Key insights are visualized below using Python (`Seaborn` & `Matplotlib`):

![Key Insights](images/olist_key_insights.png)

[![Tableau](https://img.shields.io/badge/Tableau-Interactive%20Dashboard-E97627.svg)](https://public.tableau.com/views/OlistBrazilianE-CommerceAnalytics_17933049791000/Dashboard1?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link))

### 6. Act (Strategic Recommendations)
1. **Targeted Carrier SLAs in North/Northeast Regions:** Because states like Alagoas and Maranhão suffer from disproportionately high delay rates (~20%–23%), Olist should renegotiate regional carrier contracts or incentivize local merchants to utilize regional fulfillment hubs.
2. **Freight & Margin Bundling:** Protect margins on high-volume, lower-priced categories (such as `bed_bath_table`) by introducing optimized freight bundling to prevent shipping costs from eroding customer satisfaction and repeat purchase intent.

---

## 🗂️ Repository Structure
```text
olist-ecommerce-analytics/
│
├── data/                      # Raw and processed CSV datasets
├── notebooks/                 # Jupyter notebooks containing full code pipeline
├── images/                    # Exported portfolio visualizations (.png)
├── README.md                  # Project Documentation
└── requirements.txt           # Python library dependencies
