**OmniSphere Global** 

2025 Retail Sales & Profitability Analysis 

*A Full-Stack Data Analysis: Excel → SQL (BigQuery) → Power BI* 

***What truly drove profit in 2025 — volume, pricing strategy, or promotional  discounts?*** 

This repository documents a complete analytical pipeline applied to OmniSphere Global's 2025 global  sales data. Starting from six raw regional Excel files and culminating in a Power BI executive dashboard,  the project uncovers the true drivers of profitability across six international markets, six product  categories, nine demographic segments, and 18 store locations. 

**1\. Project Overview** 

| Attribute  | Details |
| :---- | :---- |
| **Organization**  | OmniSphere Global — Diversified Mass-Market Retailer |
| **Fiscal Year**  | 2025 |
| **Markets Analyzed**  | United States · United Kingdom · Canada · China · India · Nigeria |
| **Total Stores Covered**  | 18 locations across 4 continents |
| **Data Pipeline**  | Excel → Google BigQuery → Power BI |
| **Analysis Type**  | Revenue, Profitability, Demographics, Sales Force Performance |

OmniSphere Global is a diversified mass-market retailer modelled on high-volume, B2C operations  spanning North America, Europe, Asia, and Africa. This case study moves beyond surface-level revenue  reporting to uncover where margins are healthy, where they are eroding, and what strategic actions can  drive stronger growth in 2026\. 

**2\. The Business Problem** 

*Despite stable top-line revenue in 2025, OmniSphere’s executive leadership raised a critical concern:  “Are we generating sustainable profit, or simply driving high sales volume at dangerously thin — or  even negative — margins?”*

**The analysis was structured around four strategic pillars:** 

• Geographic Efficiency — Which markets truly convert revenue into profit? 

• Product & Category Intelligence — Which products are heroes, and which are anchors? • Customer & Demographic Behavior — Who is our most valuable customer segment? • Sales Force & Operational Performance — Are we rewarding quality sales or just volume? 

**3\. Technical Stack** 

| Tool  | Role  | Key Tasks |
| :---- | :---- | :---- |
| Microsoft Excel  | Data Cleaning & Prep  | Formatting, deduplication, type validation across 6  regional files |
| Google BigQuery (SQL)  | Data Engineering & Analysis  | UNION ALL merge, feature engineering, all analytical  queries |
| Power BI  | Visualization & Reporting  | Scorecards, Geo-maps, Gauge charts, Waterfall, KPI  tables |

**4\. Data Methodology** 

**Phase 1 — Data Cleaning (Excel)** 

The raw dataset comprised six regional Excel sheets, each representing a separate country’s sales  records for 2025\. Before any analysis could begin, the data required thorough preparation: 

• Converted each raw sheet into a structured, formatted Excel Table 

• Standardized all column headers to ensure consistent naming across all six files • Validated and corrected data types — dates, currency values, integers, and categorical fields • Identified and removed duplicate records, documenting all rows dropped 

• Resolved null values and corrected categorical misspellings in the Category column *Key principle: Establish a Single Source of Truth before any data leaves Excel.* 

**Phase 2 — Data Engineering (BigQuery SQL)** 

With clean source files uploaded, the SQL layer handled consolidation and feature creation. All SQL  queries are attached in a separate document. 

**Step 1 — Table Consolidation** 

\-- All six tables shared identical column headers   
CREATE TABLE retail\_sales AS   
 SELECT \* FROM retail\_us   
 UNION ALL SELECT \* FROM retail\_uk

 UNION ALL SELECT \* FROM retail\_canada   
 UNION ALL SELECT \* FROM retail\_china   
 UNION ALL SELECT \* FROM retail\_india   
 UNION ALL SELECT \* FROM retail\_nigeria; 

**Step 2 — Feature Engineering** 

\-- Derived columns, rounded to 2 decimal places for financial accuracy UPDATE retail\_sales 

SET Total\_Amount \= ROUND(Final\_Selling\_Price \* Quantity, 2),   
 Profit \= ROUND((Final\_Selling\_Price \- Cost\_Price) \* Quantity, 2); 

*Production best practice: Raw source tables were kept unchanged. All analysis was performed on a  separate retail\_sales\_cleaned view to ensure full reproducibility and auditability.* 

**Phase 3 — Visualization (Power BI)** 

• Scorecards — Total Revenue, Total Profit, Average Transaction Value, Global Profit Margin • Geo Map — Country-level profit and revenue with store-level drill-down capability • Gauge Chart — Highest and lowest profit margin countries displayed side-by-side • Category Bar Chart — Total profit by product category, sorted descending 

• Waterfall Chart — Baseline margin → discount impact → actual margin, broken down by country • KPI / Drill-Through Table — Flagged negative-profit transactions with rep and store attribution 

**5\. Key Findings** 

**5.1 Global Financial Summary** 

| Metric  | Value |
| :---- | :---- |
| Total Revenue (2025)  | $4,137,375.58 |
| Total Profit (2025)  | $959,345.14 |
| Average Transaction Value  | $1,378.21 |
| Min Transaction Value  | $9.97 |
| Max Transaction Value  | $4,906.26 |
| Average Profit per Transaction  | $319.57 |
| Global Profit Margin  | \~23.2% |

*Analyst's Note: A global profit margin of approximately 23.2% is a strong indicator of pricing  discipline. Most mass-market retailers operate between 18–25%, placing OmniSphere firmly in the  healthy range.* 

**5.2 Geographic Performance**  
**OmniSphere Global — 2025 Retail Sales & Profitability Analysis**Page 4 

**Country-Level Profit and Margin Rankings** 

| Rank  | Country  | Total Profit  | Profit Margin % |
| :---- | :---- | :---- | :---- |
| �� 1  | United States  | $166,544.53  | 23.89% |
| �� 2  | China  | $161,686.50  | 23.73% |
| �� 3  | Canada  | $160,802.09  | 23.04% |
| 4  | United Kingdom  | $159,447.43  | 22.63% |
| 5  | India  | $159,017.24  | 23.20% |
| 6  | Nigeria  | $151,847.35  | 22.63% |

**Discount Impact Analysis — Are lower margins driven by cost pressure or excessive  discounting?** 

| Country  | Discount %  | Discount Profit Impact  | Actual Margin %  | Baseline Margin % |
| :---- | :---- | :---- | :---- | :---- |
| Nigeria  | 1.78%  | $12,169.32  | 22.63%  | 24.01% |
| UK  | 1.85%  | $13,305.55  | 22.63%  | 24.06% |
| Canada  | 1.81%  | $12,891.53  | 23.04%  | 24.43% |
| India  | 1.86%  | $13,003.45  | 23.20%  | 24.63% |
| China  | 1.91%  | $13,295.65  | 23.73%  | 25.19% |
| US  | 1.70%  | $12,026.63  | 23.89%  | 25.18% |

*Insight: The margin gap between countries is tight — only \~1.3 percentage points from top to bottom.  In lower-performing markets like Nigeria and the UK, discounting accounts for roughly 1.4–1.5  percentage points of margin erosion. This is moderate and fully controllable with pricing policy  adjustments.* 

**5.3 Product & Category Intelligence** 

**All six categories are independently profitable — no loss leaders detected.** 

| Rank  | Category  | Units Sold  | Total Profit  | Profit/Unit  | Margin % |
| ----- | :---- | :---- | :---- | :---- | :---- |
| 1  | Home & Kitchen  | 2,911  | $164,297.14  | $56.44  | 22.43% |
| 2  | Clothing  | 2,855  | $163,596.20  | $57.30  | 23.18% |
| 3  | Sports  | 2,701  | $162,119.45  | $60.02  | 23.81% |
| 4  | Electronics  | 2,670  | $161,766.71  | $60.59  | 23.67% |
| 5  | Toys  | 2,692  | $154,969.52  | $57.57  | 23.27% |
| 6  | Beauty  | 2,571  | $152,596.12  | $59.35  | 22.81% |

**Discounting by Category**

| Category  | Total Discount Value  | Discount Intensity %  | Total Profit |
| :---- | :---- | :---- | :---- |
| Home & Kitchen  | $14,226.02  | 1.91%  | $164,297.14 |
| Toys  | $12,651.58  | 1.86%  | $154,969.52 |

**OmniSphere Global — 2025 Retail Sales & Profitability Analysis**Page 5 

| Category  | Total Discount Value  | Discount Intensity %  | Total Profit |
| :---- | :---- | :---- | :---- |
| Clothing  | $13,239.27  | 1.84%  | $163,596.20 |
| Beauty  | $12,408.35  | 1.82%  | $152,596.12 |
| Sports  | $12,223.51  | 1.76%  | $162,119.45 |
| Electronics  | $11,943.40  | 1.72%  | $161,766.71 |

*Insight: The spread between the most discounted category (Home & Kitchen, 1.91%) and the least  (Electronics, 1.72%) is only 0.19 percentage points. This extremely low volatility strongly indicates  centralized, controlled discounting policies are working exactly as intended. In many retail sectors,*  

*discount intensities of 10–15% are routine — staying under 2% across all categories is a genuine  competitive advantage.* 

**5.4 Customer Demographics** 

**Profit Contribution by Demographic Segment** 

| Segment  | Transactions  | Total Revenue  | Total Profit  | Avg Order Value |
| :---- | :---- | :---- | :---- | :---- |
| Young Male  | 359  | $537,391.39  | $124,708.27  | $1,496.91 |
| Adult Female  | 369  | $508,741.36  | $114,102.53  | $1,378.70 |
| Senior Other  | 336  | $472,414.66  | $109,670.00  | $1,406.00 |
| Senior Female  | 328  | $459,227.66  | $109,287.03  | $1,400.08 |
| Adult Other  | 319  | $465,689.80  | $107,032.92  | $1,459.84 |
| Adult Male  | 346  | $454,939.85  | $103,517.93  | $1,314.86 |
| Senior Male  | 341  | $446,059.34  | $102,857.14  | $1,308.09 |
| Young Female  | 314  | $412,378.03  | $99,459.58  | $1,313.31 |
| Young Other  | 290  | $380,533.49  | $88,709.74  | $1,312.18 |

**Discount Sensitivity by Segment** 

| Segment  | Avg Discount Intensity %  | Total Units Bought  | Total Profit |
| :---- | :---- | :---- | :---- |
| Senior Male  | 3.09%  | 1,788  | $102,857.14 |
| Adult Male  | 3.02%  | 1,876  | $103,517.93 |
| Senior Female  | 2.93%  | 1,822  | $109,287.03 |
| Young Male  | 2.91%  | 2,000  | $124,708.27 |
| Adult Other  | 2.66%  | 1,725  | $107,032.92 |

*Insight: Young Males drive the highest total profit ($124,708) AND the highest average transaction  value ($1,496.91), making them the single most commercially valuable segment. Senior and Adult  Males respond to discounts but still maintain strong profit contribution — targeted promotions for  these groups remain viable when discount ceilings are enforced.* 

**5.5 Sales Force & Store Performance**  
**OmniSphere Global — 2025 Retail Sales & Profitability Analysis**Page 6 

**Top 6 Store Locations by Profit** 

| Store  | Country  | Revenue  | Profit  | Margin % |
| :---- | :---- | :---- | :---- | :---- |
| New York  | US  | $273,746.93  | $66,247.10  | 24.20% |
| Birmingham  | UK  | $266,500.83  | $57,878.10  | 21.72% |
| Toronto  | Canada  | $248,312.34  | $57,130.42  | 23.01% |
| Shanghai  | China  | $234,110.00  | $56,568.25  | 24.16% |
| Montreal  | Canada  | $233,246.41  | $55,646.54  | 23.86% |
| Delhi  | India  | $229,358.08  | $54,733.73  | 23.86% |

**Top Sales Representatives** 

| Sales Rep  | Total Amount Sold  | Avg Profit/Transaction  | Total Profit |
| :---- | :---- | :---- | :---- |
| Jennifer Miller  | $6,944.49  | $779.39  | $1,558.79 |
| Rebecca Reyes  | $6,031.61  | $901.22  | $1,802.45 |
| Michael Parker  | $5,842.94  | $826.37  | $1,652.74 |
| Justin McDonald  | $5,615.50  | $657.69  | $1,315.39 |
| Deborah Thomas  | $5,370.39  | $415.79  | $831.59 |
| Kyle Hughes  | $5,068.12  | $802.69  | $1,605.37 |

**Underperforming Reps — Flagged for Immediate Intervention** 

| Store  | Sales Rep  | Revenue  | Profit  | Margin %  | Discount % |
| :---- | :---- | :---- | :---- | :---- | :---- |
| Vancouver  | Jennifer Ortega  | $389.44  | \-$40.71  | \-10.45%  | 19.32% |
| Birmingham  | Misty Gibson  | $395.59  | \-$34.73  | \-8.78%  | 18.34% |
| Montreal  | Ryan Wolf  | $86.51  | \-$6.76  | \-7.81%  | 17.53% |
| Beijing  | William Hall  | $139.02  | \-$9.35  | \-6.73%  | 18.74% |
| Los Angeles  | Jessica Davis MD  | $27.68  | \-$1.69  | \-6.11%  | 16.75% |
| Los Angeles  | Melissa Blake  | $355.80  | \-$20.39  | \-5.73%  | 19.78% |

*Insight: These negative-margin transactions share a common thread — discount rates of 16–19%,  approximately 10x the company’s global average of \~1.8%. These are almost certainly unauthorized  discounts, data-entry errors, or unlogged refunds. Each case warrants individual investigation before  systemic conclusions are drawn.* 

**6\. Actionable Recommendations** 

**Immediate (0–30 Days)** 

• Audit & resolve all flagged negative-profit transactions. Cross-reference with POS and CRM logs.  Raise incident tickets for each store \+ transaction ID identified.  
**OmniSphere Global — 2025 Retail Sales & Profitability Analysis**Page 7 

• Create a production-ready retail\_sales\_cleaned view in BigQuery, leaving raw tables unchanged.  Enforce this as the single source of truth for all future reporting. 

• Implement POS-level discount ceilings — system hard cap at 10% (soft cap at 5%) to prevent  recurrence of the 16–19% unauthorized discounts observed. 

**Tactical (1–3 Months)** 

• Shift sales rep incentives to margin-based KPIs. Reward Average Profit per Transaction  alongside total revenue. Rebecca Reyes ($901.22 avg profit/transaction) sets the benchmark. • Increase marketing investment in Electronics — the highest-efficiency category (1.72% discount  intensity, $60.59 profit per unit) with proven demand at full price. 

• Launch value bundles in the UK and Nigeria to replace blanket discounts. A curated Home \+  Kitchen \+ Beauty bundle approach could lift average order value while protecting unit margins. 

**Strategic (3–12 Months)** 

• Implement margin-aware inventory allocation — prioritize high-margin SKUs (Electronics, Sports)  in high-value stores like New York (24.20% margin) and Shanghai (24.16%). 

• Formalize a Global Discount Playbook that documents discount authority levels by rep tier, store  type, and product category, with structured clearance event rules. 

• Deploy the Power BI dashboard with live automated alerts for: negative-profit transactions,  discount intensity above 5%, and margin anomalies by store or rep. 

**7\. Repository Structure** 

omnisphere-2025-analysis/   
|   
├── data/   
| ├── raw/ \# Original Excel files (6 regional sheets) | └── processed/ \# Cleaned CSVs exported from BigQuery | 

├── sql/   
| ├── 01\_merge\_tables.sql \# UNION ALL consolidation script | ├── 02\_cleaning\_nulls.sql \# Null audit and remediation   
| ├── 03\_feature\_engineering.sql \# Total\_Amount and Profit column creation | ├── 04\_geographic\_analysis.sql \# Country-level profit and margin queries | ├── 05\_category\_analysis.sql \# Product category performance | ├── 06\_demographic\_analysis.sql \# Age x Gender x Country segmentation | └── 07\_salesforce\_analysis.sql \# Rep and store performance queries | 

├── reports/   
| ├── country\_summary.csv   
| ├── category\_summary.csv   
| ├── demographic\_summary.csv   
| └── underperforming\_transactions.csv   
|   
├── powerbi/   
| ├── OmniSphere\_2025\_Dashboard.pbix   
| └── dashboard\_notes.md \# Visual reproduction guide   
|   
└── README.md  
**OmniSphere Global — 2025 Retail Sales & Profitability Analysis**Page 8 

**8\. Limitations & Data Quality Notes** 

• Currency Normalization: This analysis assumes all monetary values were normalized to a single  currency (USD equivalent) prior to upload. If regional tables contain local currency values, cross country aggregate comparisons will be skewed. A currency conversion step using 2025 average  exchange rates should be applied before re-running the analysis. 

• Negative Profit Outliers: A small set of transactions recorded negative profit. These may  represent refunds processed alongside forward sales, unauthorized discounts applied at point-of sale, or cost-price data entry errors. They are localized anomalies and require reconciliation with  POS or CRM records before exclusion or correction. 

• Cost Price Accuracy: All baseline margin calculations depend on the accuracy of the Cost\_Price  column. If cost prices are stale, estimated, or inconsistently recorded across regions, margin  estimates will be directionally biased. 

• Sample Representativeness: With approximately 3,000 transactions across 18 stores and 6  countries, this dataset is analytically rich but should be validated against full ERP and POS  transaction logs before informing major capital allocation decisions. 

**9\. Conclusion** 

The 2025 analysis paints a clear and encouraging picture: OmniSphere Global is a healthy, margin disciplined retailer with genuine pricing power across all six markets and all six product categories. 

The headline numbers tell a compelling story — $4.1M in revenue, $959K in profit, and a global margin of  approximately 23.2% — but the real value of this analysis lies in the granular intelligence beneath the  surface: 

• Every product category is independently profitable. No loss leaders, no structural margin erosion. • Discounting is tightly controlled globally at under 2% intensity — a significant competitive  advantage in mass-market retail. 

• A small but fully actionable set of negative-margin transactions points to operational exceptions,  not systemic failure. 

• Young Male and Adult Female customers represent the highest-value segments and should  anchor the 2026 marketing investment strategy. 

• Electronics is the efficiency engine: high margin, low discounting, strong profit per unit — it  deserves a larger share of the promotional budget. 

*The path to a stronger 2026 is not a dramatic strategic overhaul. It is a series of targeted, data-driven  optimizations: tightening discount controls at the rep level, reallocating marketing spend toward high efficiency segments and categories, and implementing the operational data hygiene fixes that will  make future analyses even more reliable.* 

***OmniSphere Global has built a strong foundation. Now it is time to build on it with  precision.***

*Analysis conducted using Excel, Google BigQuery (SQL), and Power BI.* 

*Joy Lorna*  

*Feb 2026*
