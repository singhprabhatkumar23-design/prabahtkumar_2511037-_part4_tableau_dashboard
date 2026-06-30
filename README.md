# prabahtkumar_2511037-_part4_tableau_dashboard
# Part 4: Tableau Executive Sales Dashboard

## 1. Business Problem Summary

A retail leadership team needs a unified, interactive executive dashboard to understand sales performance across regions, product categories, customer segments, and shipping modes. The goal is to identify what is driving revenue, where profitability is being compressed, and which operational decisions — particularly around discounting, product mix, and shipping — require immediate management attention.

---

## 2. Dataset Description

**File:** `data/dashboard_sales_data.xlsx`
**Records:** 4,200 orders | India retail operations | January 2024 – December 2025

| Column | Type | Description |
|---|---|---|
| order_id | String (ID) | Unique order identifier |
| order_date | Date | Date order was placed |
| ship_date | Date | Date order was shipped |
| customer_id | String | Customer identifier |
| customer_segment | Categorical | Home Office, Corporate, Consumer |
| region | Categorical | North, South, East, West |
| state | String | Indian state |
| city | String | City |
| category | Categorical | Technology, Furniture, Office Supplies |
| sub_category | Categorical | 13 sub-categories |
| product_name | String | Individual product |
| ship_mode | Categorical | Same Day, First Class, Second Class, Standard Class |
| sales | Numeric | Order sales value (₹) |
| quantity | Integer | Units ordered |
| discount | Numeric | Discount applied (0–0.5) |
| profit | Numeric | Order profit (₹, can be negative) |
| return_flag | Binary | 1 = returned, 0 = not returned |
| delivery_days | Integer | Days from order to delivery (0–9) |
| customer_rating | Numeric | Customer satisfaction (1–5), 32 missing |
| campaign_channel | Categorical | Organic, Social, Referral, Paid, Email, 24 missing |

---

## 3. Tableau Workbook Description



**Worksheets included:**
1. Sales Trend View — Line chart of monthly Sales and Profit
2. Regional Performance View — Horizontal bar chart by Region
3. Category Profitability View — Nested bar chart Category > Sub-category
4. Customer Segment View — tree map by Customer Segment
5. Shipping Performance View — Bar chart by Ship Mode (avg delivery days + revenue)
6. Discount vs Profit View — Scatter plot (Discount % vs Profit ₹)
7. Return Analysis View — Bar chart of return rate by Category

---

## 4. Calculated Fields Created

| Field Name | Formula | Business Purpose |
|---|---|---|
| **Profit Margin** | Sum`[profit] / sum[sales]` | Measures what proportion of revenue converts to profit |
| **Cost** | `[sales] - [profit]` | Derives the cost base implicit in the data |
| **Average Order Value (AOV)** | `[sales] / [quantity]` | Revenue per unit — indicator of basket quality |
| **Return Rate** | `COUNTD(IF [Return Flag]= 1 THEN [Order Id] END) / COUNTD([Order Id])
| **Shipping Delay Bucket** | `IF DATEDIFF('day', [Order Date], [Ship Date]) <= 2 THEN "Fast"
ELSEIF DATEDIFF('day', [Order Date], [Ship Date]) <= 5 THEN "Standard"
ELSE " Delayed"
END

---

## 5. Dashboard Components



**Charts (7):**
- Monthly Sales & Profit Trend (Line chart, dual axis)
- Revenue by Region (Horizontal bar chart)
- Profit by Category & Sub-category (Grouped horizontal bar chart)
- Sales & Profit by Customer Segment (Bar chart)
- Average Delivery Days by Ship Mode (Horizontal bar + reference line)
- Discount vs Profit (Scatter plot)
- Return Rate by Category (Horizontal bar, risk-coded color)

---

## 6. Filters and Interactions Used

**Global Filters (4 — applied to all worksheets):**
1. **Region** — Filter by North, South, East, West (multi-select)

2. **Customer Segment** — Filter by Home Office, Corporate, Consumer


**Dashboard Action (1):**
- Click any bar in the Regional Performance View to filter all other sheets to that region (highlight action + filter action)



---

---


---

