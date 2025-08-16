# Amazon-Clothing-Sales-2025-Data-Analysis-using-Colab-and-Python
An analysis, cleaning and visualization of Amazon's 2025 clothing sales data in google colab as an exploratory Data Analysis exercise
Project: Amazon Clothing Sales 2024–2025 (DS12) Overview
Goal: Analyze Amazon clothing orders to understand revenue trends, customer behavior, and product performance, and provide actionable insights.
Data: Amazon_Clothing_Sales_2025 DS12 - Amazon_Clothing_Sales_2025.csv
Key fields: order_id, customer_id, product_id, product_name, main_category, sub_category, brand, price, quantity, discount_percent, final_price, payment_method, review_rating, order_date, delivery_days, is_returned, region, customer_age_group, device_type.

Methodology
Load data and parse dates; validate numerics (price, quantity, discount_percent, final_price).
Exploratory analysis: revenue by month, category, brand; return rates; ratings distribution; device and payment mix; delivery performance.
Data quality review: missingness, anomalies, and cleaning steps.
Hypothesis testing: proportion and mean tests across segments (region, category, device, discount).
Visualization: labeled plots embedded in the notebook.

Key Findings (high level)
Revenue is broadly steady with a noticeable dip around Feb 2025 and spike in Mar 2025.
Discounts strongly correlate with sales volume and revenue in several categories.
Return rates are concentrated in a few sub-categories; some brands show higher-than-average returns.
Mobile dominates device usage; some payment methods skew to higher order values.
Delivery delays associate with lower ratings.

Reproducibility
Environment: Python 3, pandas, seaborn, matplotlib.
Steps:
Place the CSV in project root.
Run the notebook cells in order.
Plots render inline; export artifacts are created in the files pane if you request exports.

Data Quality Report Missingness
region: some rows missing (NULL detected).
order_date: coerced to datetime; any unparsable entries set to NaT.
review_rating: present in sample; validate full dataset in notebook.
final_price, price, quantity: present; verify non-null across all rows in notebook.

Anomalies
Casing inconsistency in main_category (e.g., baby vs Baby).
discount_percent and final_price need consistency checks: final_price should approximate price × quantity × (1 − discount%).
delivery_days: verify non-negative; check long tails/outliers.
is_returned: binary; confirm only 0/1.
ratings range: ensure between 1–5.
Duplicate order_id: ensure uniqueness..
Recalculate expected_final_price = price × quantity × (1 − discount_percent/100) and flag rows where relative error > 2–3%.
Clip impossible values: negative prices, quantities, discounts < 0 or > 100, delivery_days < 0.
Impute region with Unknown or drop if 
analysis requires geographic integrity.
Convert booleans to ints; ensure dtypes for numerics.
Remove duplicate order_id or resolve by latest timestamp where needed.
