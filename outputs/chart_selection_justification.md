# Chart Selection Justification

**Dashboard:** Executive Sales Dashboard
**Dataset:** dashboard_sales_data.xlsx | 4,200 orders | Jan 2024 – Dec 2025

---

## Chart 1: Sales Trend View — Line Chart

**Question answered:** How has monthly sales revenue trended over time, and is the business growing?

**Why this chart type is appropriate:** A line chart is the correct choice for time-series data because it shows continuity — the eye naturally tracks the line to perceive direction, rate of change, and anomalies over time.



---

## Chart 2: Regional Performance View — Horizontal Bar Chart

**Question answered:** Which regions generate the most revenue and profit, and how do their margins compare?

**Why this chart type is appropriate:** A horizontal bar chart is ideal for comparing discrete categorical values (four regions) on a quantitative measure (sales or profit). Bars make magnitude differences immediately readable through length comparison. A map was considered but rejected because the dataset uses regional groupings (North/South/East/West), not precise state-level coordinates that would make a geographic map accurate and informative.



---

## Chart 3: Category Profitability View — Horizontal Bar Chart (Grouped by Category and Sub-category)

**Question answered:** Which categories and sub-categories are most and least profitable, and where should the business focus investment?

**Why this chart type is appropriate:** A grouped/nested horizontal bar chart allows simultaneous comparison at two levels of hierarchy — category and sub-category — without requiring the viewer to switch between charts. A treemap was considered for its space efficiency, but bar charts are more precise for exact value comparisons, which is critical for a profitability decision chart.


---

## Chart 4: Customer Segment View — treemap

**Question answered:** Which customer segment drives the most revenue and profit, and are there margin differences between segments?

**Why this chart type is appropriate:** With only three customer segments, a treemap clearly communicates magnitude sales differences



---

## Chart 5: Shipping Performance View — Bar Chart with Reference Line

**Question answered:** How do different shipping modes compare on delivery speed and revenue, and which modes should the business promote?

**Why this chart type is appropriate:** A horizontal bar chart ordered by average delivery days shows immediately which shipping modes are fastest and slowest. Overlaying revenue contribution as a secondary bar provides the business context needed for the "so what" — fast shipping modes need to be profitable to justify operational investment.


---

## Chart 6: Discount vs Profit View — Scatter Plot

**Question answered:** Is there a relationship between discount level and profit, and at what discount threshold does the business start losing money?

**Why this chart type is appropriate:** A scatter plot is the only chart type that can reveal the relationship (correlation, clustering, or threshold) between two continuous variables across 4,200 individual data points. No other chart type (bar chart, line chart) can show both the direction of the relationship and the density of observations simultaneously. The scatter plot reveals outliers — high-discount, high-sales orders that are still loss-making — that would be invisible in aggregate views.



---

## Chart 7: Return Analysis View — Bar Chart

**Question answered:** Which categories have the highest return rates, and where is return-related revenue risk concentrated?

**Why this chart type is appropriate:** A bar chart directly shows return count or return rate per category, enabling immediate ranking of return risk. A heat map was considered for category × region × segment combinations but would be overly complex for an executive dashboard view. The bar chart provides the clear "which category is worst" answer executives need at a glance.

*

---

## Dashboard-Level Design Principles


**Filter placement:** two interactive filters (Region,  Customer Segment, ) are positioned as a vertical panel on the right side of the dashboard — the standard Tableau convention that executives are familiar with. All filters apply to all worksheets simultaneously via dashboard-level filter actions.

**Color consistency:** Each Region uses the same color across all charts (e.g., South = teal, North = blue, East = orange, West = green). Each Category uses the same color across all charts. This allows viewers to track a region or category across multiple views without re-reading legends.

**Title hierarchy:** Dashboard title (largest, dark navy), section subheadings (medium, dark grey), chart titles (small, descriptive). Avoids decorative elements like icons or gradient backgrounds that add visual noise without informational value.

**Avoided misleading scales:** All bar charts start at zero. No truncated axes. The scatter plot Y-axis includes negative values to show loss-making orders. Dual-axis charts use independent scales with clear axis labels so the reader understands they are comparing different units.
