# Business Insights — Executive Sales Dashboard

**Dataset:** dashboard_sales_data.xlsx | 4,200 orders | Jan 2024 – Dec 2025 | India retail operations

---

## Calculated Fields Used in This Dashboard

| Field Name | Formula | Purpose |
|---|---|---|
| **Profit Margin** | `[profit] / [sales]` | Measures profitability efficiency as a percentage |
| **Cost** | `[sales] - [profit]` | Derives cost of goods and operations |
| **Average Order Value (AOV)** | `[sales] / [quantity]` | Measures revenue per unit sold |
| **Return Rate** | `SUM([return_flag]) / COUNT([order_id])` | Measures proportion of orders returned |
| **Shipping Delay Bucket** | `IF [delivery_days] = 0 THEN "Same Day" ELSEIF [delivery_days] <= 2 THEN "Fast (1-2 days)" ELSEIF [delivery_days] <= 4 THEN "Standard (3-4 days)" ELSEIF [delivery_days] <= 6 THEN "Slow (5-6 days)" ELSE "Very Slow (7+ days)" END` | Categorises delivery speed for shipping performance analysis |

---

## Insight 1 — Sales Trend: Healthy Year-on-Year Growth with Consistent Revenue Base

**Observation:** Total revenue grew from ₹106.2M in 2024 to ₹110.8M in 2025, representing a 4.3% year-on-year increase.

**Data evidence:** 2024 sales = ₹106,241,022 | 2025 sales = ₹110,776,629 | Profit grew from ₹16.47M to ₹16.83M.

**Business interpretation:** The business is growing steadily, but profit growth (2.2%) is trailing revenue growth (4.3%), indicating that costs or discounting levels are compressing margins as the business scales. The monthly trend shows no sharp dips or revenue cliff, suggesting stable demand rather than spike-driven performance.

**Recommended action:** Investigate why profit growth is lagging revenue growth. Review whether increased marketing or discounting spend in 2025 is eating into margins. Set a target for profit growth to match or exceed revenue growth in 2026.

---

## Insight 2 — Regional Performance: South Leads Revenue, but All Regions Are Margin-Equivalent

**Observation:** The South region generates the highest revenue (₹64.7M, 29.8% of total), followed by North (₹54.6M), West (₹48.9M), and East (₹48.9M). However, all four regions have nearly identical profit margins (15.1%–15.6%).

**Data evidence:** South = ₹64.7M revenue, 15.44% margin | North = ₹54.6M, 15.24% | East = ₹48.9M, 15.55% | West = ₹48.9M, 15.14%.

**Business interpretation:** The South region's revenue leadership does not translate into a profitability advantage — all regions operate at structurally similar margins. This suggests that regional pricing, product mix, and cost structures are uniform across the country, which is efficient for standardisation but may mean the business is not capturing regional premium pricing opportunities.

**Recommended action:** Test premium pricing strategies in South and North regions where demand is clearly higher. Investigate whether West and East can grow revenue with targeted regional marketing without compromising the consistent margin structure.

---

## Insight 3 — Category Profitability: Technology Dominates; Furniture Is a Drag

**Observation:** Technology accounts for 70.9% of total profit (₹28.0M) on 70.9% of sales (₹153.9M). Furniture generates only 10.7% of total profit (₹3.6M) on 23.8% of sales (₹51.6M) — a margin of just 6.9%.

**Data evidence:** Technology margin = 18.22% | Office Supplies margin = 14.85% | Furniture margin = 6.89%.

**Business interpretation:** Technology is the profit engine of the business. Furniture is consuming significant sales volume and operational resources (shipping, warehousing, returns) while generating very thin margins. Within Furniture, Tables (5.67%) and Bookcases (5.71%) are the worst performers. Within Technology, all four sub-categories achieve margins above 18%.

**Recommended action:** Evaluate whether Furniture, particularly Tables and Bookcases, justifies its shelf space and logistics cost. Consider reducing Furniture SKUs and reallocating inventory investment to Technology. Review whether Furniture pricing can be improved or whether supplier costs need renegotiation.

---

## Insight 4 — Customer Segment: Home Office Leads Profit, Corporate Needs Attention

**Observation:** Home Office is the highest-revenue segment (₹74.5M, 34.3%) with the strongest margin (15.51%). Corporate is the second-largest revenue segment (₹70.6M) but has the weakest margin (15.18%). Consumer sits in the middle (₹71.9M, 15.34% margin).

**Data evidence:** Home Office = ₹74.5M sales, ₹11.56M profit, 15.51% margin | Corporate = ₹70.6M, ₹10.72M, 15.18% | Consumer = ₹71.9M, ₹11.03M, 15.34%.

**Business interpretation:** All three segments are performing within a tight margin band (15.2%–15.5%), suggesting the business has not differentiated its commercial terms significantly by segment. Home Office outperforming Corporate slightly may indicate that Corporate buyers are negotiating larger discounts or receiving more favourable shipping terms that compress margin.

**Recommended action:** Audit discount and pricing structures for Corporate accounts. If Corporate customers receive preferential pricing, ensure volume commitments justify the margin concession. Explore upselling higher-margin Technology products to Corporate clients.

---

## Insight 5 — Discount Impact: Discounts Above 20% Destroy Profitability

**Observation:** Orders with no discount achieve a 20.56% profit margin. Orders with discounts of 31–50% produce a negative margin of –4.95%. The margin degradation is steep and consistent as discount levels rise.

**Data evidence:** 0% discount = 20.56% margin | 1-10% = 17.01% | 11-20% = 13.63% | 21-30% = 8.05% | 31-50% = –4.95% (loss-making).

**Business interpretation:** Discounting is eroding profitability in a structured, predictable way. Orders in the 31–50% discount bracket collectively generate a net loss of ₹102,494 — meaning the business is paying customers to take products. No discount tier generates better margin than undiscounted orders. Discounting is not creating incremental profit through volume; it is simply subsidising sales.

**Recommended action:** Set a hard maximum discount policy of 20% for all sales channels. Review all outstanding contracts or promotions offering discounts above 20% and renegotiate or sunset them. Use the Discount vs Profit scatter plot as a standing management report to monitor discount discipline.

---

## Insight 6 — Shipping Performance: Standard Class Dominates but Same Day Is Underutilised

**Observation:** Standard Class handles 58.3% of orders (₹122.8M revenue) with an average delivery time of 4.71 days. Same Day shipping handles only 6.9% of orders (₹14.6M) but delivers in 0.40 days with a competitive margin.

**Data evidence:** Standard Class = ₹122.8M sales, ₹19.09M profit, 4.71 avg days | Same Day = ₹14.6M, ₹2.19M profit, 0.40 days | First Class = ₹31.9M, ₹4.64M, 1.77 days | Second Class = ₹47.7M, ₹7.39M, 2.68 days.

**Business interpretation:** The business is heavily concentrated in Standard Class shipping, which may be creating customer experience issues for time-sensitive orders. Same Day and First Class both generate healthy profit contributions despite their operational premium cost, suggesting customers value speed and may be willing to pay for it. No shipping mode produces a loss.

**Recommended action:** Analyse whether Standard Class customers are churning at higher rates than faster-ship customers. Test promotional messaging around First Class shipping for Technology products where order values are high and customer satisfaction is critical.

---

## Insight 7 — Return Patterns: Furniture Returns at 2x the Rate of Technology

**Observation:** Furniture has a return rate of 7.67% — more than double Technology (3.03%) and significantly above Office Supplies (3.65%). In absolute numbers, Furniture generated 88 returns versus Technology's 42, despite Technology having far higher revenue.

**Data evidence:** Furniture = 88 returns / 1,147 orders = 7.67% return rate | Office Supplies = 61 / 1,669 = 3.65% | Technology = 42 / 1,384 = 3.03%.

**Business interpretation:** Furniture's high return rate compounds its already thin margins. Returns carry hidden costs — reverse logistics, restocking, potential write-offs — that are not visible in the margin figures alone. A 7.67% return rate on Furniture, combined with a 6.89% average margin, likely means a significant portion of Furniture sales are loss-making once return costs are factored in.

**Recommended action:** Investigate root causes of Furniture returns — are they driven by damage in shipping, product quality issues, or expectation mismatch? Consider improving product descriptions and images online to reduce expectation-gap returns. Apply a restocking fee for Furniture returns to partially offset reverse logistics costs.

---

## Insight 8 — Business Risk / Opportunity: Discount Creep and Furniture Combine to Create a Structural Profitability Threat

**Observation:** Two separate issues — high discount rates and Furniture's poor performance — are compounding each other. Furniture is the most discounted category, and the category generating the most returns. If discount rates continue to rise and Furniture's share of the product mix grows, overall company margins will compress further.

**Data evidence:** Furniture margin = 6.89% (vs 18.22% for Technology) | Orders with 31-50% discount = net margin of –4.95% | Furniture return rate = 7.67% vs company average of 4.55% | Profit growth (2.2%) is already trailing revenue growth (4.3%) across 2024–2025.

**Business interpretation:** The business currently earns its overall 15.35% margin largely because of Technology's strong performance. If Technology growth stalls or Furniture's share grows unchecked, the overall margin position becomes structurally vulnerable. The combination of thin margins, high returns, and aggressive discounting in one category is a significant risk that individual metric reviews would miss.

**Recommended action:** Commission a full category profitability review that includes return costs, shipping costs, and discount rates by category. Set category-level minimum margin targets. Create a dashboard alert that flags any month where Furniture margin falls below 5% or company-wide discount rate exceeds 20% of total revenue. Prioritise Technology sales growth as the primary margin protection strategy.
