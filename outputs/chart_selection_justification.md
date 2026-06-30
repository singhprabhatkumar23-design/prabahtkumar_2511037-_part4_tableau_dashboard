# Chart Selection Justification

**Dashboard:** Executive Sales Dashboard
**Dataset:** dashboard_sales_data.xlsx | 4,200 orders | Jan 2024 – Dec 2025

---

## Chart 1: Sales Trend View — Line Chart

**Question answered:** How has monthly sales revenue trended over time, and is the business growing?

**Why this chart type is appropriate:** A line chart is the correct choice for time-series data because it shows continuity — the eye naturally tracks the line to perceive direction, rate of change, and anomalies over time. A bar chart of monthly sales would work, but would make it harder to perceive trend acceleration or deceleration. A scatter plot would lose the temporal sequence entirely.

**Field usage:**
- X-axis: Order Date (truncated to Month)
- Y-axis: SUM(Sales)
- Secondary axis: SUM(Profit) — dual axis to show both metrics without requiring two separate charts
- Color: Region (optional filter interaction to show regional trend breakdown)

**Design principle applied:** Dual-axis design with clearly labelled axes for Sales (left) and Profit (right). Both lines start from zero to prevent distorted perception of magnitude. A reference line at the average monthly sales value provides context for performance above/below trend.

**Mistake avoided:** Avoided truncating the Y-axis above zero, which would exaggerate the apparent growth rate and mislead leadership about the actual magnitude of change. Also avoided using area charts, which would double-count if regions were overlaid.

---

## Chart 2: Regional Performance View — Horizontal Bar Chart

**Question answered:** Which regions generate the most revenue and profit, and how do their margins compare?

**Why this chart type is appropriate:** A horizontal bar chart is ideal for comparing discrete categorical values (four regions) on a quantitative measure (sales or profit). Bars make magnitude differences immediately readable through length comparison. A map was considered but rejected because the dataset uses regional groupings (North/South/East/West), not precise state-level coordinates that would make a geographic map accurate and informative.

**Field usage:**
- Rows: Region (sorted by SUM(Sales) descending)
- Columns: SUM(Sales), SUM(Profit) — side-by-side bars
- Color: Region (consistent color coding matching other dashboard views)
- Label: SUM(Sales) displayed on bar ends

**Design principle applied:** Sorted in descending order so the highest-performing region appears at the top — this is the most natural reading order for a ranking chart and avoids random ordering that forces viewers to search for meaning. Color is used for category identity, not to encode an additional variable, avoiding double-encoding confusion.

**Mistake avoided:** Avoided using a pie chart, which would make it difficult to compare four regions of similar size (South 29.8% vs North 25.1% vs West 22.5% vs East 22.5% — too similar to distinguish as pie slices). Avoided a 3D bar chart, which creates false depth perception and distorts bar heights.

---

## Chart 3: Category Profitability View — Horizontal Bar Chart (Grouped by Category and Sub-category)

**Question answered:** Which categories and sub-categories are most and least profitable, and where should the business focus investment?

**Why this chart type is appropriate:** A grouped/nested horizontal bar chart allows simultaneous comparison at two levels of hierarchy — category and sub-category — without requiring the viewer to switch between charts. A treemap was considered for its space efficiency, but bar charts are more precise for exact value comparisons, which is critical for a profitability decision chart.

**Field usage:**
- Rows: Category → Sub-category (nested hierarchy)
- Columns: SUM(Profit)
- Color: Profit value (diverging red-green color scale: red = low or negative profit, green = high profit)
- Size: Not used (avoided size encoding in bar charts as it conflicts with bar length)

**Design principle applied:** Diverging color scale centred at zero highlights immediately which sub-categories are loss-making or low-profit in red and which are strong in green, without requiring numerical reading. Sorted within each category by descending profit so the best and worst performers are immediately visible.

**Mistake avoided:** Avoided using sales volume as the primary metric (which would make Office Supplies appear weaker than it is). Avoided using a single flat list of 13 sub-categories without category grouping, which would force viewers to mentally group categories themselves.

---

## Chart 4: Customer Segment View — Bar Chart

**Question answered:** Which customer segment drives the most revenue and profit, and are there margin differences between segments?

**Why this chart type is appropriate:** With only three customer segments, a bar chart clearly communicates magnitude differences. A pie chart could work for three categories but makes margin comparison (requiring a second chart) much harder. Using a single bar chart with dual measures (sales and profit) allows segment comparison on both dimensions simultaneously.

**Field usage:**
- Rows: Customer Segment
- Columns: SUM(Sales) and SUM(Profit) — dual measures
- Color: Customer Segment (consistent palette)
- Label: Profit margin % displayed as annotation

**Design principle applied:** Margin percentage labels are overlaid directly on bars rather than requiring a separate reference table. This gives executives the key interpretive insight (margin equivalence across segments) without needing to do mental arithmetic. Segments are sorted alphabetically for easy reference (Consumer → Corporate → Home Office).

**Mistake avoided:** Avoided stacking sales and profit in a single stacked bar, which would make it impossible to read the profit component accurately. Avoided using line charts for a three-category non-time comparison, which would falsely imply a sequential trend between categories.

---

## Chart 5: Shipping Performance View — Bar Chart with Reference Line

**Question answered:** How do different shipping modes compare on delivery speed and revenue, and which modes should the business promote?

**Why this chart type is appropriate:** A horizontal bar chart ordered by average delivery days shows immediately which shipping modes are fastest and slowest. Overlaying revenue contribution as a secondary bar provides the business context needed for the "so what" — fast shipping modes need to be profitable to justify operational investment.

**Field usage:**
- Rows: Ship Mode (sorted by AVG(Delivery Days) ascending)
- Columns: AVG(Delivery Days) primary, SUM(Sales) secondary
- Color: Ship Mode
- Reference line: Company average delivery days (3.6 days)

**Design principle applied:** Ordering by delivery speed (fastest at top) rather than alphabetically makes the chart read as a natural ranking from best to worst delivery performance. The reference line allows immediate identification of above-average and below-average shipping modes without number reading.

**Mistake avoided:** Avoided using delivery days as a continuous axis on a scatter plot (which would plot individual orders rather than mode aggregates and create unreadable point density). Avoided omitting revenue from the shipping chart, which would make fast shipping appear universally desirable regardless of its revenue contribution.

---

## Chart 6: Discount vs Profit View — Scatter Plot

**Question answered:** Is there a relationship between discount level and profit, and at what discount threshold does the business start losing money?

**Why this chart type is appropriate:** A scatter plot is the only chart type that can reveal the relationship (correlation, clustering, or threshold) between two continuous variables across 4,200 individual data points. No other chart type (bar chart, line chart) can show both the direction of the relationship and the density of observations simultaneously. The scatter plot reveals outliers — high-discount, high-sales orders that are still loss-making — that would be invisible in aggregate views.

**Field usage:**
- X-axis: Discount (individual order level, 0 to 0.5)
- Y-axis: Profit (individual order level, can be negative)
- Color: Category (Technology/Furniture/Office Supplies)
- Reference line: Y = 0 (zero profit line) — critical visual anchor

**Design principle applied:** The zero-profit reference line (Y = 0) is the single most important design element in this chart. It separates profitable orders (above) from loss-making orders (below) without requiring the viewer to read any axis numbers. Color encoding by category reveals which category's orders cluster in the loss-making zone. Opacity set to 40% to handle overplotting at common discount values (0%, 0.1, 0.2, etc.).

**Mistake avoided:** Avoided aggregating this view into a summary bar chart (e.g., "average profit by discount bucket"), which would mask the variance and the individual outliers that tell the full story. Avoided using a 3D scatter plot, which makes depth perception unreliable and creates visual clutter. Did not use connecting lines between points, which would falsely imply sequence or trend between individual orders.

---

## Chart 7: Return Analysis View — Bar Chart

**Question answered:** Which categories have the highest return rates, and where is return-related revenue risk concentrated?

**Why this chart type is appropriate:** A bar chart directly shows return count or return rate per category, enabling immediate ranking of return risk. A heat map was considered for category × region × segment combinations but would be overly complex for an executive dashboard view. The bar chart provides the clear "which category is worst" answer executives need at a glance.

**Field usage:**
- Rows: Category, Sub-category
- Columns: SUM(Return Flag) for absolute returns, or Return Rate calculated field for proportional view
- Color: Return Rate (red gradient — higher rate = darker red, signalling risk)
- Label: Return count and return rate % shown together

**Design principle applied:** Using a risk-signalling color scheme (white to red) rather than the standard blue palette used elsewhere on the dashboard creates immediate visual contrast that draws executive attention to this chart as a "risk" view rather than a performance view. Consistent with dashboard convention where standard performance charts use blue/green and risk views use orange/red.

**Mistake avoided:** Avoided using return count alone without return rate, which would make high-volume categories (Office Supplies: 1,669 orders) appear riskier than low-volume categories (Furniture: 1,147 orders) even when the percentage is lower. Avoided including the return rate for categories with fewer than 50 orders in the dataset, which would create statistically unreliable rates that could mislead decision-making.

---

## Dashboard-Level Design Principles

**KPI Cards:** Three summary KPI tiles placed at the top of the dashboard show Total Sales (₹217.0M), Profit Margin (15.35%), and Return Rate (4.55%). These anchor the viewer with business context before they read individual charts.

**Filter placement:** Four interactive filters (Region, Category, Customer Segment, Ship Mode) are positioned as a vertical panel on the right side of the dashboard — the standard Tableau convention that executives are familiar with. All filters apply to all worksheets simultaneously via dashboard-level filter actions.

**Color consistency:** Each Region uses the same color across all charts (e.g., South = teal, North = blue, East = orange, West = green). Each Category uses the same color across all charts. This allows viewers to track a region or category across multiple views without re-reading legends.

**Title hierarchy:** Dashboard title (largest, dark navy), section subheadings (medium, dark grey), chart titles (small, descriptive). Avoids decorative elements like icons or gradient backgrounds that add visual noise without informational value.

**Avoided misleading scales:** All bar charts start at zero. No truncated axes. The scatter plot Y-axis includes negative values to show loss-making orders. Dual-axis charts use independent scales with clear axis labels so the reader understands they are comparing different units.
