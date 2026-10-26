# BlueMart Retail Analytics

Python analysis of **640K+ retail transactions** across **50 stores** and **200 products** (Jan 2021 – Oct 2025), with an interactive executive dashboard for management.

![Dashboard preview](images/dashboard_preview.png)

## Business Problem

BlueMart is a UAE retail chain selling through stores, its website, a mobile app and online marketplaces. Management wanted to know:

1. How are sales changing over time?
2. Which categories generate the most sales and profit?
3. Which products are the most profitable?
4. Which cities and stores perform best?
5. Which sales channel brings the most revenue?

Three extra questions came from the inventory data:

6. Which high-selling products are at risk of running out of stock?
7. Which products are below their reorder point?
8. Which products have high sales but low profit?

## Key Findings

| Area | Finding |
|---|---|
| Overall | 73.21M in sales and 21.10M in profit (28.8% margin), from 1.68M units sold in 641,798 transactions |
| Category | Electronics brings 55.7% of sales (40.79M) and 11.85M of profit. Personal Care has the lowest margin (about 26%) |
| Products | Batteries (3.96M), Cables (3.39M), Chargers (2.31M) and Mobile Accessories (2.18M) earn the most profit |
| Cities | Dubai 56.1% of sales, Abu Dhabi 28.0%, Sharjah 15.9% |
| Stores | Store sales are close: the top store (Store 41, 1.50M) is only about 5% above the lowest (Store 03, 1.43M) |
| Channels | In-store 41.3%, Website 27.7%, Mobile App 17.9%, Amazon.ae 8.8%, Noon 4.3% |
| Store types | Mall 44.1%, High Street 35.9%, Community 19.9% |
| Stock risk | No product is below its reorder point. 2,098 store-product records (99 products) have high sales with lower stock |
| Margin watch | 8 products sell well but earn less profit than most, such as Grocery_Rice_1121 (14.4% margin) |

## Dashboard

`BlueMart_Executive_Dashboard.html` is a single file. Open it in any browser, no setup needed.

- KPI cards, executive summary and management takeaways
- Interactive charts with hover tooltips
- Filters: Year, City, Store Type, Category, Channel, with a Reset button
- Product, store, location and inventory views

## Data

| File | Rows | Content |
|---|---|---|
| `bm_sales.csv` | 641,843 | Date, store, product, customer, quantity, price, total value, channel, discount |
| `bm_skus.csv` | 200 | Product name, category, subcategory, brand, unit price, cost price |
| `bm_stores.csv` | 50 | Store name, city, store type, opening date |
| `bm_inventory.csv` | 8,735 | Stock on hand, reorder point, safety stock, last restock, snapshot date |

## Method

1. Loaded and checked the four datasets (shape, types, missing values, duplicates).
2. Removed 45 duplicate sales rows and converted date columns.
3. Joined sales with products on `sku_id` and with stores on `store_id`.
4. Calculated profit as `total_value - quantity * cost_price`.
5. Grouped by month, category, subcategory, store, city and channel, and plotted the results.
6. Kept inventory separate from sales. Only total units sold per product were linked to stock.

**Stock risk rule:** a store-product record is flagged when its product's total units sold is above the median and its stock on hand is below the median.

## Notes

- About 25% of sales rows have no customer ID, so customer-level analysis was not done.
- Profit uses the product cost price, so it is a gross margin figure.
- Inventory is a single snapshot (31 Oct 2025), not a history.
- The data has no currency, so amounts are shown without a symbol.

## Tools

Python, pandas, NumPy, Matplotlib, Jupyter Notebook, HTML/JavaScript (dashboard)

## Files

```
├── Blue_mart_retail_analysis.ipynb
├── BlueMart_Executive_Dashboard.html
├── data/        (the four CSV files)
├── images/      (dashboard preview)
└── README.md
```

## Author

**Syed Auliya Mohiddin** · [LinkedIn](https://linkedin.com/in/syed-auliya) · [GitHub](https://github.com/Syed-Auliya)
