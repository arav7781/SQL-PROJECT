# E-commerce SQL dashboard

A Flask + MySQL dashboard over an e-commerce schema (customers, orders, ordered items, products, categories),
built for a database course. The whole project is in [`final_dcdsl.zip`](final_dcdsl.zip): `app9.py` (Flask API)
and `index9999.html` (sign-in page and dashboard).

## What the queries cover

The API exposes a fixed set of named queries at `GET /execute_query/<query_id>`:

- multi-table joins (customers ⋈ orders, products ⋈ categories, orders ⋈ ordered items)
- aggregates with `GROUP BY` / `ORDER BY` / `LIMIT`: order value, sales per item, top-5 products, products per category
- date filtering (`DATE_SUB(CURDATE(), INTERVAL 1 MONTH)`) for recently active customers
- shipping performance: average real vs scheduled shipping days per state
- views (`active_customers`, `CustomerOrders`, `CategorySalesOverview`) and a stored function for average order value
- parameterised deletes (`%s` placeholders, no string-built SQL)

## Run

```bash
unzip final_dcdsl.zip && cd final_dcdsl
pip install flask flask-cors mysql-connector-python
# set DB_HOST, DB_USER, DB_DATABASE in app9.py to your MySQL instance
python app9.py
```

## Tech

Python · Flask · MySQL · HTML/CSS/JS
