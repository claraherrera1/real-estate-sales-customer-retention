# Methodology & Analytical Findings

**Project:** Real Estate Sales & Customer Retention Analysis  
**Primary Visualization Tool:** Tableau Public  
**Analysis Period:** January 2023 – December 2024  
**Geographic Coverage:** Mexico City, Mexico, and Bogotá, Colombia

## 1. Project Objective

The objective of this project was to evaluate real estate sales performance, identify key revenue drivers, and examine repeat purchasing behavior through customer cohort analysis.

The analysis addressed four main business areas:

- **Commercial performance:** Revenue, transaction volume, average sale value, and commissions.
- **Sales composition:** Revenue distribution by property type, sales channel, customer segment, and city.
- **Time-based performance:** Monthly sales trends and year-over-year (YoY) growth.
- **Customer retention:** Repeat purchases following each customer's first recorded transaction.

The final deliverable was a three-page interactive dashboard published on Tableau Public.

## 2. Data Sources

The project used three CSV datasets organized into a transactional fact table and two dimension tables.

| Dataset | Records | Description |
|---|---:|---|
| `hecho_ventas_propiedades.csv` | 8,500 | Property sales transactions, dates, prices, customer and property identifiers, sales channels, and commission information |
| `dim_clientes.csv` | 3,500 | Customer identifiers, geographic information, and buyer segmentation |
| `dim_propiedades.csv` | 8,000 | Property identifiers and characteristics, including property type, location, size, and listed price |

The transactional dataset covers sales recorded between January 2023 and December 2024.

### Data Model

The analytical structure follows a star-schema approach:

- **Fact table:** `hecho_ventas_propiedades`
- **Customer dimension:** `dim_clientes`
- **Property dimension:** `dim_propiedades`

The fact table connects to the dimension tables through `id_cliente` and `id_propiedad`.

These relationships support the analysis of sales transactions by customer and property attributes.

Tableau's date functionality was used for time-based analysis without requiring a separate calendar CSV.

## 3. Data Preparation & Validation

Before developing the dashboard, the datasets were reviewed for data-type consistency, missing values, and identifier uniqueness.

### Data-Type Validation

The preparation process included:

- Reviewing `fecha_venta` as a date field.
- Checking numeric fields associated with property prices, commissions, size, and room counts.
- Reviewing the percentage formatting of `porcentaje_comision`.

### Missing Values & Data Quality

The project documentation reports that the reviewed data contained no missing values or errors requiring record removal or imputation.

### Primary-Key Validation

The dimension tables were checked for duplicate identifiers:

- `dim_clientes`: 3,500 records and 3,500 distinct customer IDs.
- `dim_propiedades`: 8,000 records and 8,000 distinct property IDs.

No duplicate primary keys were identified in either dimension.

**Result:** The available datasets were considered suitable for the analytical model without deleting or imputing records.

## 4. KPI Definitions & Analytical Measures

### Core Business KPIs

| KPI | Definition | Result |
|---|---|---:|
| Total Revenue | Sum of recorded property sale prices | $6.01B |
| Sales Count | Number of recorded sales transactions | 8,500 |
| Average Sale Value | Total revenue divided by sales count | $707.35K |
| Total Commissions | Total reported sales commissions | $200.63M |

*All financial values are presented in USD.*

Total commissions are reported separately from sales revenue and should not be interpreted as net profit.

### Revenue Contribution

Revenue participation was evaluated across three dimensions:

- Property type
- Sales channel
- Customer segment

For each category, revenue participation represents its share of total recorded sales revenue.

### Time-Based Analysis

Monthly revenue trends were compared across 2023 and 2024.

Year-over-year growth was used to assess the percentage change in monthly revenue relative to the corresponding month of the previous year.

### Customer Cohort Analysis

Customers were grouped according to the month of their first recorded purchase.

Subsequent transactions were analyzed relative to that initial purchase to evaluate repeat purchasing behavior over time.

The dashboard presents:

- **M1:** Repeat purchasing at the first monthly checkpoint.
- **M3:** Repeat purchasing at the third monthly checkpoint.
- **M6:** Repeat purchasing at the sixth monthly checkpoint.
- **M1–M12 cohort matrix:** Monthly repeat-purchase patterns by first-purchase cohort.

These indicators describe repeat purchasing behavior, not general customer activity or cumulative customer lifetime retention.

## 5. Tableau Dashboard Development

The final Tableau report contains three analytical pages.

### 5.1 Executive Overview | Real Estate Performance

**Original Tableau title:** Overview Ejecutivo | Desempeño Inmobiliario

This dashboard provides a consolidated view of commercial performance.

It includes:

- Total revenue
- Number of sales
- Average sale value
- Total commissions
- Monthly revenue trends
- Revenue by city
- Monthly year-over-year growth

**Analytical Purpose:** Help stakeholders monitor overall performance, compare geographic markets, and identify periods of growth or decline.

### 5.2 Commercial Analysis | Composition & Performance

**Original Tableau title:** Análisis Comercial | Composición y Desempeño

This dashboard explores commercial performance across business dimensions.

It includes:

- Revenue participation by property type
- Revenue participation by sales channel
- Revenue participation by customer segment
- Revenue by property type
- Sales volume by property type
- Average sale value by property type

**Analytical Purpose:** Identify which properties, channels, and customer segments contribute most to revenue and transaction volume.

### 5.3 Customer Retention | Cohort Analysis

**Original Tableau title:** Retención de Clientes | Análisis de Cohortes

This dashboard examines repeat purchases after customers' first recorded transactions.

It includes:

- M1 retention: 9.35%
- M3 retention: 9.47%
- M6 retention: 10.21%
- Monthly cohort heatmap covering available M1–M12 observations

**Analytical Purpose:** Compare repeat-purchase patterns across acquisition cohorts and identify opportunities for post-sale engagement.

**Interactive Dashboard:** [View on Tableau Public](https://public.tableau.com/app/profile/clara.herrera5092/viz/RealEstateSalesCustomerRetentionAnalysis/Dashboard1-OverviewEjecutivo)

## 6. Key Analytical Findings

### 6.1 Overall Commercial Performance

Between January 2023 and December 2024, the business recorded:

- **$6.01B** in total sales revenue.
- **8,500** property sales.
- **$707.35K** in average sale value.
- **$200.63M** in total commissions.

**Business Interpretation:** The executive KPIs establish a baseline for monitoring transaction volume, sales value, and commission generation.

### 6.2 Geographic Revenue Distribution

Mexico City generated approximately **$3.24B**, compared with **$2.77B** in Bogotá.

**Business Interpretation:** Mexico City represented the larger revenue market during the analyzed period. Further market-level analysis would be needed to explain the difference.

### 6.3 Property-Type Performance

Houses contributed the largest share of revenue, representing **37.26%**, or approximately **$2.24B**.

Apartments accounted for the highest transaction volume, with **5,105 sales**, representing approximately **60.06%** of all transactions.

Commercial properties recorded the highest average sale value, approximately **$1.80M**.

**Business Interpretation:** Sales volume and revenue contribution reveal different aspects of performance. Apartments lead in transaction count, while houses generate the largest revenue share and commercial properties command higher average sale values.

### 6.4 Sales Channel Concentration

The broker channel (*Corredor*) generated **72.85%** of revenue, compared with **27.15%** from direct sales.

**Business Interpretation:** Brokers are a major contributor to revenue, but the distribution also indicates substantial reliance on one sales channel.

This concentration should be evaluated alongside channel costs, conversion efficiency, and customer acquisition performance before making resource-allocation decisions.

### 6.5 Customer Segment Contribution

First-time buyers (*Primera vez*) generated **62.93%** of revenue.

Investors (*Inversionista*) contributed **24.47%**, while high-net-worth buyers (*Alto patrimonio*) contributed **12.60%**.

**Business Interpretation:** First-time buyers represent the largest revenue segment and a relevant audience for evaluating post-purchase engagement opportunities.

### 6.6 Year-over-Year Growth

Monthly YoY growth was positive in most months analyzed.

The strongest increases were recorded in:

- **July:** +27.22%
- **May:** +25.40%

October recorded a **−0.84%** YoY change.

**Business Interpretation:** The variation in monthly growth suggests that commercial performance should be assessed over time rather than through aggregate revenue alone.

The available analysis identifies changes in performance but does not establish their underlying causes.

### 6.7 Customer Retention & Repeat Purchases

The dashboard reported the following retention indicators:

| Checkpoint | Retention |
|---|---:|
| M1 | 9.35% |
| M3 | 9.47% |
| M6 | 10.21% |

The cohort heatmap also revealed variation in repeat purchasing across monthly acquisition cohorts.

**Business Interpretation:** Repeat purchases were relatively limited at the analyzed checkpoints, suggesting opportunities to investigate customer engagement and post-sale relationship management.

However, real estate purchases are typically infrequent transactions. These percentages should be interpreted in the context of the industry's purchasing cycle.

## 7. Business Recommendations

### 7.1 Strengthen Post-Sale Customer Engagement

Develop follow-up strategies for first-time buyers, including relevant communications, referral initiatives, and opportunities to identify future purchasing needs.

**Suggested Measurement:** Repeat-purchase rates by cohort and customer segment.

### 7.2 Monitor Sales Channel Performance

Continue supporting the broker channel while evaluating opportunities to strengthen direct sales.

Before reallocating resources, compare channel-level revenue with associated costs and conversion performance.

**Suggested Measurement:** Revenue, sales volume, commission expense, and acquisition efficiency by channel.

### 7.3 Differentiate Strategies by Property Type

Use distinct commercial approaches based on property performance:

- Houses: Monitor their contribution to total revenue.
- Apartments: Optimize processes supporting high transaction volumes.
- Commercial properties: Evaluate strategies suited to higher-value transactions.

**Suggested Measurement:** Revenue share, transaction volume, and average sale value by property type.

### 7.4 Investigate Monthly Performance Changes

Review business conditions and commercial initiatives associated with strong YoY growth in May and July, as well as the decline observed in October.

**Suggested Measurement:** Monthly YoY revenue growth, sales count, and performance by city and property type.

### 7.5 Develop Cohort-Based Customer Monitoring

Continue tracking repeat purchases across acquisition cohorts and customer segments.

Evaluate whether post-sale engagement initiatives are associated with improved repeat-purchase behavior.

**Suggested Measurement:** Repeat-purchase rates at defined monthly checkpoints, cohort sizes, and subsequent transaction values.

## 8. Analytical Limitations

Several considerations should be kept in mind when interpreting the results.

**Sales revenue versus profitability:** The analysis focuses on transaction values and commissions. It does not establish net profitability or account for all business operating expenses.

**Cohort maturity:** More recent acquisition cohorts have fewer observable months. Comparisons across cohorts should account for differences in follow-up periods.

**Small-cohort variability:** High percentages in small cohorts may be driven by relatively few transactions and should be interpreted cautiously.

**Repeat-purchase frequency:** Real estate transactions generally have longer purchasing cycles than many retail or subscription businesses. Monthly repeat-purchase rates should not be interpreted as equivalent to recurring product usage.

**Causality:** Differences across cities, channels, property types, and time periods describe observed patterns. Additional analysis would be required to identify their causes.

## 9. Conclusion

This project demonstrates an end-to-end business intelligence workflow, from data validation and analytical modeling to KPI development, Tableau visualization, and business interpretation.

The analysis identified differences between transaction volume and revenue contribution, a high concentration of sales revenue in the broker channel, and opportunities to investigate repeat purchasing behavior.

The three-page Tableau dashboard provides an accessible way to explore commercial performance and supports further investigation into sales strategy and customer engagement.

---

**Project Type:** Educational business intelligence project developed through TripleTen.  
**Dashboard Platform:** Tableau Public.  
**Source Data:** Project CSV datasets available in the repository.
