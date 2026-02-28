# BMW Global End-to-End Sales Analytics

Comprehensive analysis of BMW global sales performance, customer segmentation, and regional revenue trends across 6 markets.

---

## Project Overview

This end-to-end data analytics project explores 50,000 BMW sales transactions spanning multiple regions, models, and years. The goal was to uncover revenue trends, identify top-performing markets and models, and segment customers by classification — moving the data through a full analytics pipeline from raw CSV to interactive dashboard.

**Pipeline:**  `Raw Data → Python (Cleaning) → MySQL (Analysis) → Power BI (Visualization)`

---

## Tools & Technologies

| Tool | Purpose |
|------|---------|
| Python (Pandas) | Data cleaning and preprocessing |
| MySQL | Data storage and exploratory analysis |
| Power BI | Interactive multi-page dashboard |
| CSV | Source data format |

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

### Page 1: Overview

**KPI Cards:** Total Revenue (19.0T), Total Units (253M), PY Revenue (1.22T), YoY Growth % (14.53), High Value % (0.51)

**Revenue by Fuel Type:** Fuel type revenue is evenly distributed across all four types — Hybrid leads at 4.82T (25.4%), followed by Petrol at 4.76T (25.0%), Electric at 4.75T (25.0%), and Diesel at 4.68T (24.6%). This near-equal split suggests no single powertrain dominates BMW's global revenue.

**Sales & Units by Color:** Sales revenue and units sold are tracked across six vehicle colours — Red, Silver, White, Blue, Grey, and Black. Red and Silver lead slightly in both sales (~4T each) and units (~43M each), though colour performance is broadly consistent across all options, ranging between 42M–43M units.

**Top 5 Models by Revenue:** The 7 Series leads all models at 1.79T in total revenue, followed closely by the 3 Series (1.77T), i8 (1.76T), X1 (1.75T), and 5 Series (1.74T). Revenue is highly competitive across the top five, with less than 50B separating first and fifth place.

**Total Revenue and PY Revenue by Year:** Both Total Revenue and Prior Year Revenue are tracked from 2010 to 2024, with values oscillating between 1.2T and 1.3T annually. Revenue peaked around 2020–2022 before a slight decline toward 2024.

**Revenue by Geography:** Bubble map visualising total revenue and units by region. Asia leads with $3.25T in revenue and 42.97M units (YoY Growth: 15.02%), followed by Europe at $3.19T and 42.56M units (YoY Growth: 14.79%), North America at $3.18T and 42.40M units (YoY Growth: 13.66%), South America at $3.11T and 41.55M units (YoY Growth: 15.07%), and Africa at $3.11T and 41.57M units (YoY Growth: 14.32%).

---

### Page 2: Product & Vehicle Strategy

**KPI Cards:** Avg Selling Price (75.03K), Eco Share % (0.50), Avg Engine Size (3.25L), Top Model (7 Series), Diesel Share % (0.25)

**Average Selling Price:** The gauge tracks average selling price against a maximum of 150.07K, currently sitting at 75.03K — representing the midpoint of the pricing range, suggesting a balanced mix of entry-level and premium models in the sales mix.

**Sales Volume by Fuel Type:** Hybrid leads sales volume at 65M units, followed by Petrol (63M), Electric (63M), and Diesel (62M). All four fuel types account for 96.6% of total volume collectively, with Hybrid holding a slight edge.

**Price vs. Mileage Strategy:** Plots individual transactions by price (up to 0.4M) against mileage (up to 0.2M KM), segmented by High and Low classification. High classification vehicles are concentrated at lower mileage and higher price points, while Low classification vehicles cluster at higher mileage and lower price ranges — consistent with expected depreciation patterns.

**Units Sold by Color:** Units are evenly distributed across all six colours, each accounting for approximately 16.5%–16.9% of total units sold. White and Silver lead marginally at 43M each (16.87% and 16.8% respectively).

**Transmission Preference by Region:** Automatic and Manual transmission preference is split almost exactly 50/50 across all six regions, with no region showing a meaningful preference for either transmission type.

---

### Page 3: Regional & Customer Segmentation

**KPI Cards:** NA Revenue (3T), EU Revenue (3T), Asia Revenue (3T), High Class Txns (15K), Avg Units/Deal (5.07K)

**Revenue by Region:** Cumulative revenue builds from Asia (lowest individual contribution) through Europe, North America, Middle East, South America, and Africa, totalling approximately 19T globally. Each region contributes roughly 3T, reflecting a well-balanced global sales distribution.

**Customer Classification by Region:** High vs Low classification is broken down by region. Asia has the highest High classification share at 31.70%, followed by North America (31.40%), Europe (31.27%), Africa (30.53%), Middle East (29.98%), and South America (28.87%). The narrow range across all regions (28.87%–31.70%) indicates that customer classification is not strongly influenced by geography.

**Average Price by Region:** Africa and North America lead with an average selling price of 76K, while Asia, Middle East, Europe, and South America all record 75K. Pricing is consistent across markets, suggesting a globally standardised pricing strategy with minimal regional variation.

**Average Engine Size by Year and Region:** Average engine size across all six regions is tracked from 2010 to 2024, fluctuating between 3.1L and 3.3L throughout the period. In 2010, the Middle East recorded the largest average engine size at 3.32L, followed by North America (3.30L) and South America (3.27L). By 2024, Africa and South America lead at 3.29L, while the Middle East has declined the most sharply to 3.14L — suggesting a regional shift toward smaller, more fuel-efficient engines over the 14-year period.

---

## Key Insights

- **Africa** generated the highest total revenue among all regions
- **7 Series** was the top performing model by total revenue globally
- **Hybrid** vehicles were the most frequently sold fuel type
- **2022** was the highest revenue year in the dataset
- Customer classification (High vs Low) is evenly distributed across all regions (~30/70 split), suggesting classification is driven by factors other than geography
- Top models vary by region — Asia leads with the X1, Europe with the i8, and the Middle East with the 7 Series

---

## Dataset

- **Rows:** 50,000
- **Columns:** 13
- **Source:** Synthetic BMW sales data
- **Key fields:** `Customer_ID`, `Model`, `Year`, `Region`, `Fuel_Type`, `Transmission`, `Engine_Size_L`, `Mileage_KM`, `Price_USD`, `Unite_Sold`, `Sales_Classification`, `Total_Sales`
