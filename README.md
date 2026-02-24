# big D's Footwear Sales Intelligence Dashboard (Power BI)

## Project Overview

This project analyzes 4 months of transaction-level sales data from a direct-to-consumer footwear business operating through digital marketplaces and messaging platforms.

The objective was to transform manually reconstructed transaction records into a structured profitability monitoring system to support better pricing, channel allocation, and growth decisions.

---

## Business Context

The business operates through:

- Direct customer conversations
- Bank transfers
- Online marketplace platforms including Jiji

Before this project, there was no structured visibility into:

- Revenue performance
- Transaction-level profitability
- Channel effectiveness
- Cost leakage (shipping, discounts, gift items)
- Margin sustainability at low sales volumes

This dashboard introduces financial clarity at the unit economics level.

---

## Dataset Overview

- Time Period: 4 months  
- Total Transactions: 29  
- Data Source: Manual extraction from bank logs and customer confirmations  
- Granularity: Individual transaction level  

### Fields Captured

- product_id, size, discount, gift_items, total_cost, product_name, quantity, discount_amount, gifts_cost, profit, brand, selling_price, amount_paid, shipping_cost, channel, category, cost_price, gift_for_first_time_customer, shipping_cost_company, payment_method
  
The dataset includes both revenue and full cost breakdown, enabling complete transaction-level profitability analysis.

---

## Data Cleaning & Transformation

Data preparation was performed in Microsoft Excel and Power BI.

Key steps included:

- Standardizing financial calculations
- Verifying revenue consistency (price × quantity)
- Validating total cost composition
- Recomputing profitability where necessary
- Removing incomplete or inconsistent entries
- Creating calculated columns for:
  - Profit Margin %
  - Net Revenue
- Creating DAX measures for:
  - Total Revenue
  - Total Profit
  - Average Order Value
  - Margin %

Row-level logic was implemented using calculated columns, while aggregation logic was handled using DAX measures to preserve analytical flexibility.

---

## Data Modeling Notes

This project used a primarily flat transaction model due to the small dataset size.

Power BI auto-generated relationships where applicable.

During development, a structural refresh issue occurred when adding new transactions. Referenced queries required careful management of applied steps. Copying transformations without correctly referencing the working table led to refresh inconsistencies.

This highlighted the importance of:

- Query dependency management  
- Clean transformation pipelines  
- Scalable data modeling design  

Future versions will implement a formal dimensional model for improved scalability.

---

## Key KPIs

- Total Revenue, Revenue by Product, Revenue by Payment Method, Total Profit, Revenue by Brand, Shipping Cost Impact, Profit Margin %, Revenue by Category, Gift Campaign Cost Impact, Average Order Value, Revenue by Channel
  
---

## Key Insights

- Jiji generated the highest share of total revenue during the analysis period.
- Sales volume (29 transactions over 4 months) indicates growth is currently volume-constrained.
- Shipping contributions, gift costs, and discounting materially impact margin at low order volume.
- Increasing marketing efforts to drive order frequency represents the primary growth lever.
- Transaction-level profitability tracking improves pricing and cost control decisions.
  
---

## Dashboard Preview

<img width="1366" height="768" alt="Screenshot (55)" src="https://github.com/user-attachments/assets/07e54b1e-6fa0-4c90-9c36-e67a2a470381" />
<img width="1366" height="768" alt="Screenshot (56)" src="https://github.com/user-attachments/assets/0f1bcdff-553f-4693-819b-3da5b7d5574c" />
<img width="1366" height="768" alt="Screenshot (57)" src="https://github.com/user-attachments/assets/35c462e6-1026-4e4d-8fb7-850d6ec8f7d1" />
<img width="1366" height="768" alt="Screenshot (58)" src="https://github.com/user-attachments/assets/e15a8256-8e75-4ea4-aac5-c5fd23b76afd" />
<img width="1366" height="768" alt="Screenshot (59)" src="https://github.com/user-attachments/assets/a2a2da91-7e0c-4cd6-af1e-0083951c7433" />

---

## Project Files

Google drive link to all the files needed to view and work with this project are included in the repo:
- https://drive.google.com/drive/folders/19lIY65TwE7tu5JZQqLAdpM4G9zLZ88wx?usp=drive_link

You can open the Excel file to see the raw transaction data, and the PBIX file to explore the dashboard and measures directly in Power BI.

---

## Limitations

- Small sample size (29 transactions)
- Manual data entry
- Profit initially calculated in Excel
- No repeat customer tracking
- No automated ingestion pipeline

---

## Possible Future Improvements

- Implement star schema data model
- Automate data ingestion
- Add customer retention tracking
- Introduce sales forecasting
- Migrate to SQL-backed storage

  ## 💡 Extra Credit: Lessons Learned & Troubleshooting (full version on my X - formerly twitter)

During the dashboard development, I encountered a structural issue that taught me valuable lessons about data management and Power BI workflow:

- I accidentally uploaded my order records table **twice** and updated the wrong table. To fix this, I had to restructure my data by referencing the correct table.  
- I linked the new table reference to my dashboard and disabled the incorrect one.  
- I learned that I could **copy all applied steps** (the cleaning procedure) from one table to another, which I used to fix the updated table — thanks to ChatGPT.  

### What “Updated” Means in Practice:

1. I entered the footwear business transaction data into Excel.  
2. I cleaned, analyzed, and visualized it in Power BI.  
3. A few days later, a new order came in, and I wanted it to reflect on the dashboard. To do this, I updated the original Excel file.  
4. I noticed that the table powering the dashboard wasn’t updating.  
5. After investigation, I discovered the duplicate table upload. I fixed the structural problem, enabling all future orders to update automatically.  

✅ Key Takeaway: Managing query references and applied steps is critical for building scalable and maintainable Power BI dashboards.
