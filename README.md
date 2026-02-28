# BMW Global End-to-End Sales Analytics
Comprehensive end-to-end analysis of BMW global sales performance, customer segmentation, and regional revenue trends across 6 markets using Python, SQL, and Power BI.
This project details the development and analysis of an interactive Power BI dashboard focusing on sales performance, product strategy, and regional customer segmentation data across six global markets. The dataset, covering 2010 to 2024, was cleaned, preprocessed, and visualized. The dashboard tracks key performance indicators such as total revenue, total units sold, year-over-year growth, and average selling price. It aims to provide sales strategists, regional managers, and product teams with comprehensive insights to optimise market strategy, identify high-performing regions and models, and understand customer segmentation patterns globally.

Insights and recommendations are provided on the following key areas:

* **Category 1:** Revenue & Sales Performance
* **Category 2:** Product & Vehicle Strategy
* **Category 3:** Regional Analysis
* **Category 4:** Customer Segmentation

---

## Tools & Technologies

| Tool | Purpose |
|------|---------|
| Python (Pandas) | Data cleaning and preprocessing |
| MySQL | Data storage and exploratory analysis |
| Power BI | Interactive multi-page dashboard |
| CSV | Source data format |

**Pipeline:**  `Raw Data → Python (Cleaning) → MySQL (Analysis) → Power BI (Visualization)`

---

## Data Cleaning (Python)

The raw dataset was cleaned and preprocessed using **Pandas** prior to loading into MySQL. Steps included:

- Inspecting for null values and duplicates
- Validating data types across all columns
- Ensuring consistency in categorical fields (e.g. `Fuel_Type`, `Region`, `Sales_Classification`)
- Confirming `Total_Sales` alignment with `Price_USD` and `Unite_Sold`

---

## SQL Queries

The cleaned data was loaded into MySQL for analysis. Queries range from basic aggregations to advanced window functions and CTEs.

**Topics covered:**
- Total revenue and units sold by region
- Top 5 models by revenue
- Average selling price by fuel type and classification
- YoY revenue growth by region *(CTE + LAG window function)*
- Model revenue ranking within each region *(RANK + PARTITION BY)*
- Regions exceeding global average Electric vehicle sales *(Subquery)*
- Running total of revenue by year *(SUM OVER window function)*
- High value customer % by region *(Multi-CTE)*

> See [`BMW_Sales_SQL_Queries.txt`](SQL/BMW_Sales_SQL_Queries.txt) for all queries.

---

## Power BI Dashboard

The dashboard is built across three pages — Overview, Product & Vehicle Strategy, and Regional & Customer Segmentation — creating a clean, modern, and fully navigable interface.

📊 **Power BI Dashboard Link**

---
## Executive Summary

### Overview of Findings
Across the 2010–2024 period, BMW's global sales network generated **$19.0T in total revenue** from **253M units sold** across six regions and eleven models, reflecting a year-over-year growth rate of **14.53%**. Revenue performance was broadly consistent across all regions and models, with no single market or vehicle dominating the portfolio — a pattern that points to a globally standardised pricing and product strategy.

- Total revenue reached **$19.0T**, with prior year revenue of **$1.22T** and a YoY growth rate of **14.53%**
- **Asia** was the top performing region by total revenue at **$3.25T**, followed by Europe ($3.19T) and North America ($3.18T)
- The **7 Series** was the top model by revenue at **$1.79T**, followed closely by the 3 Series ($1.77T) and i8 ($1.76T)
- **Hybrid** vehicles led all fuel types in both revenue (**$4.82T, 25.4%**) and units sold (**65M**)
- Revenue peaked in **2022 at $1.34T**, the highest single year across the full 14-year period
- High value transactions account for **30.5%** of all records (**15,246 transactions**), with the remaining 69.5% classified as Low
- Average selling price across all markets was **$75.03K**, with average engine size of **3.25L**

Got it! Here's the full Insights Deep Dive, Recommendations, and Assumptions sections written out with the `**text**` syntax so you can copy and paste directly:

---

## Insights Deep Dive

### Category 1: Revenue & Sales Performance

**Total Revenue & Units:** The dashboard recorded **$19.0T** in total revenue and **253M units** sold across the full period, with a YoY growth rate of **14.53%**. Prior year revenue of **$1.22T** provides a useful benchmark for evaluating current performance.

**Revenue by Year:** Annual revenue fluctuated between **$1.22T (2023)** and **$1.34T (2022)**, showing no sustained upward or downward trend across the 14-year window. Revenue was relatively stable from 2010 through 2021 before a notable peak in 2022 followed by a dip in 2023 and recovery in 2024 (**$1.31T**).

**Revenue by Fuel Type:** **Hybrid** vehicles led total revenue at **$4.82T (25.4%)**, followed by Petrol (**$4.76T, 25.0%**), Electric (**$4.75T, 25.0%**), and Diesel (**$4.68T, 24.6%**). The near-equal split across all four fuel types suggests BMW's global revenue is not dependent on any single powertrain — an indicator of a well-diversified product portfolio.

**Top 5 Models by Revenue:** The **7 Series** led all models at **$1.79T**, followed by the 3 Series (**$1.77T**), i8 (**$1.76T**), X1 (**$1.75T**), and 5 Series (**$1.74T**). The gap between first and fifth place is less than **$50B**, highlighting the competitiveness of BMW's model lineup.

**Sales & Units by Color:** **Red** and **Silver** vehicles marginally outperformed other colours at **43M units each** (16.9% and 16.8% respectively), with White, Grey, Blue, and Black all recording **42M units**. Revenue followed a similar pattern, with no colour significantly outperforming others.

---

### Category 2: Product & Vehicle Strategy

**Average Selling Price:** The global average selling price across all models and regions was **$75.03K**, sitting at the midpoint of the **$0–$150.07K** pricing range. This reflects a balanced mix of entry-level and premium models in the overall sales composition.

**Sales Volume by Fuel Type:** **Hybrid** led unit sales at **65M**, followed by Petrol (**63M**), Electric (**63M**), and Diesel (**62M**). All four fuel types collectively account for **96.6%** of total volume. The Eco Share % (Hybrid + Electric combined) stands at **0.50**, indicating that eco-friendly vehicles account for half of all revenue generated.

**Price vs. Mileage Strategy:** **High** classification vehicles cluster at lower mileage and higher price points (up to **$0.4M**), while **Low** classification vehicles concentrate at higher mileage and lower price ranges — consistent with standard vehicle depreciation patterns. This confirms that Sales_Classification is strongly correlated with both price and mileage.

**Transmission Preference by Region:** Automatic and Manual transmission preference is split almost exactly **50/50** across all six regions, with no region showing a meaningful preference for either type. This suggests transmission type is not a regionally driven purchasing factor for BMW customers globally.

**Average Engine Size:** The global average engine size is **3.25L**, consistent across all four fuel types. Regional engine size fluctuated between **3.1L and 3.3L** from 2010 to 2024, with the **Middle East** declining from **3.32L in 2010** to **3.14L in 2024** — the sharpest regional decline, suggesting a shift toward smaller engines in that market.

---

### Category 3: Regional Analysis

**Revenue by Region:** **Asia** led all regions with **$3.25T** in total revenue and **42.97M units** sold, recording a YoY growth rate of **15.02%**. Europe followed at **$3.19T** (42.56M units, 14.79% YoY), North America at **$3.18T** (42.40M units, 13.66% YoY), Middle East at **$3.17T** (42.33M units), South America at **$3.11T** (41.55M units, 15.07% YoY), and Africa at **$3.11T** (41.57M units, 14.32% YoY). The narrow revenue range across all six regions (**$3.11T–$3.25T**) reflects a globally balanced sales distribution.

**Average Price by Region:** **Africa** and **North America** recorded the highest average selling prices at **$76K**, while Asia, Middle East, Europe, and South America each averaged **$75K**. The minimal variation confirms a globally standardised pricing strategy with limited regional price differentiation.

**Average Engine Size by Region Over Time:** From 2010 to 2024, regional average engine sizes fluctuated between **3.1L and 3.3L**. The **Middle East** showed the most notable shift, declining from **3.32L in 2010** to **3.14L in 2024**, while **Africa** and **South America** ended the period highest at **3.29L** each.

---

### Category 4: Customer Segmentation

**High vs. Low Classification:** Of the **50,000 transactions**, **15,246 (30.5%)** were classified as High value and **34,754 (69.5%)** as Low. High value transactions generated a disproportionate share of total revenue, reflected in the High Value % KPI of **0.51**.

**Customer Classification by Region:** **Asia** recorded the highest High classification share at **31.70%**, followed by North America (**31.40%**), Europe (**31.27%**), Africa (**30.53%**), Middle East (**29.98%**), and South America (**28.87%**). The narrow range across all regions confirms that customer classification is not geographically driven — High value customers are distributed evenly across all markets.

**High Class Transactions:** A total of **15,246** High classification transactions were recorded globally, distributed consistently across all six regions with no single market concentrating high value activity.

---

## Recommendations

**Invest in Hybrid and Electric Product Lines:** With Eco Share % at **0.50** and **Hybrid** leading both revenue and unit sales, continued investment in eco-friendly powertrains is well-supported by the data. Expanding the Hybrid and Electric lineup could capture additional market share as global demand for sustainable vehicles grows.

**Leverage Asia's Growth Momentum:** **Asia** leads all regions in total revenue (**$3.25T**) and YoY growth (**15.02%**). Targeted marketing campaigns, expanded dealership networks, and region-specific model offerings could further capitalise on this momentum.

**Address the Middle East Engine Size Trend:** The **Middle East's** average engine size declined from **3.32L in 2010** to **3.14L in 2024** — the sharpest regional decline observed. This may signal a shift in customer preference toward more fuel-efficient vehicles, warranting a review of the model mix offered in that market.

**Develop High Value Customer Retention Programmes:** With High classification customers accounting for **30.5%** of transactions and **51%** of revenue, developing loyalty programmes, priority service offerings, and personalised outreach strategies targeting this segment could meaningfully increase lifetime customer value.

**Standardise Global Pricing with Regional Incentives:** The near-uniform average selling price across all regions (**$75K–$76K**) confirms a globally standardised pricing strategy. While consistency supports brand positioning, introducing region-specific financing options or incentive programmes — particularly in **South America** and **Africa** where revenue lags — could stimulate growth in lower-performing markets.

**Monitor 2022 Revenue Peak for Sustainability:** **2022** recorded the highest annual revenue at **$1.34T**, followed by a dip to **$1.22T** in 2023. Identifying the factors that drove the 2022 peak and replicating those conditions would be valuable for sustaining growth momentum.

---

## Assumptions

- Data completeness and accuracy are assumed following the cleaning and transformation process in **Python (Pandas)**.
- All KPIs and DAX measures are calculated based solely on the provided dataset without external imputation.
- `Total_Sales` is assumed to be accurately derived from `Price_USD × Unite_Sold` for each transaction.
- `Sales_Classification` (High/Low) is assumed to be consistently applied across all regions and model types using a standardised internal classification methodology.
- The dataset is synthetic and intended for analytical and portfolio demonstration purposes only.
- All revenue figures are denominated in **USD** and no currency conversion adjustments have been applied.
- The average engine size of **3.24L–3.25L** across all fuel types, including Electric, reflects the synthetic nature of the dataset as real-world Electric vehicles do not have combustion engine displacements.

## Dataset

- **Rows:** 50,000
- **Columns:** 13
- **Source:** Synthetic BMW sales data
- **Key fields:** `Customer_ID`, `Model`, `Year`, `Region`, `Fuel_Type`, `Transmission`, `Engine_Size_L`, `Mileage_KM`, `Price_USD`, `Unite_Sold`, `Sales_Classification`, `Total_Sales`
