# Nexora Connect CPaaS Pricing Analysis
**Tools:** Excel | SQL Server | Power BI | Word  
**Type:** End-to-End Pricing Analysis  
**Dataset:** Q1 2025 (January - March 2025)

## Project Overview
Conducted a comprehensive pricing performance 
analysis for Nexora Connect — Africa's leading 
CPaaS provider processing over 1 billion 
transactions annually across 20,000+ businesses.

The analysis covered four key areas:
- Margin analysis and leakage detection
- Revenue anomaly detection using SQL
- Interactive pricing dashboard
- Strategic pricing recommendation memo

## Business Context
Nexora Connect operates a margin-sensitive model — 
purchasing message delivery capacity from 
carriers at wholesale rates and selling to 
Enterprise, SME and Startup clients at retail 
rates across products including Bulk SMS, 
Transactional SMS, Voice OTP, USSD and 
WhatsApp API.

## Task 1 — Margin Analysis (Excel)
**Tools:** Excel, Power Query, Pivot Tables, DAX

**What I built:**
- Imported raw data using Power Query
- Calculated Gross Revenue, Total Cost, 
  Gross Profit and Gross Margin % per 
  product and route combination
- Aggregated figures by product across 
  Q1 2025 using SUMIF formulas
- Identified Top 3 and Bottom 3 margin 
  performers using LARGE, SMALL and 
  INDEX MATCH functions
- Applied conditional formatting — 
  Red below 30%, Green above 55%
- Built pivot summary showing Revenue, 
  Cost and Margin % by Product and 
  Client Tier with interactive slicer

**Key Findings:**
| Product | Route | Margin % |
|---------|-------|----------|
| Transactional SMS | MTN Nigeria | 65.2% ✅ |
| Voice OTP | MTN Nigeria | 50.0% ✅ |
| USSD | GLO Nigeria | 48.6% ✅ |
| Bulk SMS | Airtel Nigeria | 47.1% ✅ |
| Bulk SMS | MTN Nigeria | 43.3% ✅ |
| WhatsApp API | Meta Global | 33.3% ⚠️ |
| Bulk SMS | International | 30.0% 🔴 |

## Task 2 — Revenue Leakage Detection (SQL)
**Tool:** SQL Server (SSMS)

**4 Production Ready Queries:**

**Query 1 — Below Floor Pricing**
Identified records where effective price 
per unit charged to clients was below 
vendor rate — detecting revenue leakage.
Result: No below-floor pricing detected ✅

**Query 2 — Margin by Client Tier**
Calculated average gross margin % per 
client tier per product using RANK() 
window function partitioned by product.
Result: Transactional SMS Enterprise 
leads at 65.2%

**Query 3 — Month on Month Volume Change**
Used CTE and CASE WHEN to pivot monthly 
volumes and calculate % change between 
January, February and March.
Result: Data sparsity identified as 
critical gap — flagged for resolution

**Query 4 — Vendor Rate Expiry Risk**
Identified all vendor contracts expiring 
within 30 days using DATEDIFF and DATEADD.
Result: All 6 vendor contracts expired 
on 31-Mar-25 — URGENT renewal required

## Task 3 — Pricing Dashboard (Power BI)
**Tools:** Power BI Desktop, DAX

**DAX Measures:**
- Total Revenue = SUM(traffic_data[revenue])
- Total Cost = SUM(traffic_data[cost_ngn])
- Gross Profit = [Total Revenue] - [Total Cost]
- Margin % = DIVIDE([Gross Profit], [Total Revenue], 0)

**Dashboard Visuals:**
- 4 KPI Cards — Revenue, Cost, Profit, Margin %
- Bar Chart — Margin % by Product with 40% reference line
- Matrix Table — Revenue, Cost, Margin % by Product × Client Tier
- Line Chart — Monthly revenue trend filterable by Client Tier
- Scatter Plot — Volume vs Margin % by route
- Interactive Client Tier slicer
- Navigation buttons between pages

**Key Dashboard Insights:**
- Overall Q1 margin 45.79% exceeds 40% target ✅
- Transactional SMS leads at 65.22% 🟢
- WhatsApp API and Bulk SMS International below 40% 🔴
- MTN Nigeria dominates volume at 5.8M messages
- Enterprise tier drives 78% of Q1 revenue

## Task 4 — Pricing Recommendation Memo
**Tool:** Microsoft Word

**Key Recommendations:**

| Action | Product | Current Price | New Price | Margin Impact | Revenue Impact |
|--------|---------|---------------|-----------|---------------|----------------|
| Reprice | Bulk SMS International | ₦2.50 | ₦2.92 | 30% → 40.07% | +₦294,000/qtr |
| Reprice | WhatsApp API | ₦6.00 | ₦6.67 | 33.33% → 40.03% | +₦140,700/qtr |
| Remove Discount | Bulk SMS Intl Enterprise | 10% | 0% | 33.46% → 40.07% | Margin protected |
| Establish | Pricing Catalogue | Absent | Live document | Framework resolved | Long term |

**Combined Repricing Impact: +₦434,700 per quarter**

## Data Gap Identified
The pricing_catalogue was absent from the dataset. 
Reconstructed using:
- Cost floor — Cost_NGN ÷ Volume
- 40% margin target — Price = Cost ÷ (1 - 0.40)
- B2B tier discounts — Enterprise 10%, SME 5%, Startup 0%
- Nigerian CPaaS market benchmarking

## Skills Demonstrated
- Power Query data transformation
- SUMIF, LARGE, SMALL, INDEX MATCH
- Conditional formatting logic
- CTEs, Window Functions, JOINs in SQL
- DAX measures in Power BI
- Cost floor and margin markup calculations
- Executive level data storytelling

## Results
- Identified +₦434,700 quarterly revenue opportunity
- Detected 2 underperforming products below 40% target
- Flagged 6 vendor contracts requiring urgent renewal
- Reconstructed missing pricing catalogue
- Built executive ready interactive dashboard

*Analysis conducted as part of Nexora Connect Group 
Pricing Officer practical assessment.*

![Nexora Connect CPaaS Dashboard](Nexora_Connect_dashbaord.png)
