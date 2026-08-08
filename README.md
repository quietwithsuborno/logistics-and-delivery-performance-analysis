# 📦 Logistics & Delivery Performance Analysis
### Shohoz Express Ltd. | Excel Analytics Project

---

## 📌 Project Overview

This project is an end-to-end logistics analytics case study built entirely in **Microsoft Excel**, designed to showcase advanced Excel skills including Power Pivot, DAX, PivotTables, and dashboard design.

**Company:** Shohoz Express Ltd. *(fictional)*

**Domain:** Supply Chain & Logistics

**Analysis Period:** July 2025 – June 2026

**Dataset:** 5,000 shipments across 5 regions, 10 routes, and 6 carriers

---

## 📝 Executive Summary

Shohoz Express Ltd. is experiencing a sustained decline in delivery performance, with an overall On-Time Delivery (OTD) rate of just **54.52%** — far below the industry benchmark of 85%+. This project analyzes 12 months of shipment data to identify the root causes of delay across carriers, regions, routes, and operational timing. The analysis reveals that the problem is **structural rather than seasonal**, driven by specific underperforming carriers and route-level inefficiencies. Three targeted, actionable recommendations are provided to guide management's immediate intervention.

---

## ❓ Business Problem

> Shohoz Express Ltd. has seen a rise in customer complaints and a decline in On-Time Delivery (OTD) rate over the past 12 months. Management needs to identify **where, why, and when** delivery performance is failing — and which specific carriers, regions, or routes should be targeted for immediate improvement.

---

## 🎯 Analysis Scope

| # | Analysis | Key Question |
|---|---|---|
| 1 | OTD Rate Trend | How has on-time delivery changed month over month? |
| 2 | Carrier Performance | Which carrier has the worst delivery reliability? |
| 3 | Region & Route Analysis | Which regions and routes experience the most delays? |
| 4 | Delay vs Cost | Does a late delivery cost more? |
| 5 | Day-of-Week Pattern | Are delays concentrated on specific days of the week? |
| 6 | Delay Root Cause | What are the most common reasons for delays? |

---

## 🗂️ Repository Structure

```
excel-logistics-performance-analysis/
│
├── data/
│   ├── raw/                        # Intentionally messy raw datasets
│   └── clean/                      # Cleaned datasets
│
├── docs/
│   ├── 01_project_brief.md         # Business problem & scope
│   ├── 02_dataset_structure.md     # Table design & relationships
│   ├── 03_data_issue_log.md        # Pre-cleaning data quality audit
│   ├── 04_data_cleaning_log.md     # Step-by-step cleaning documentation
│   └── 05_insight_report.md        # Key findings & recommendations
│
├── dashboard.png               # Dashboard screenshot
└──
```

---

## 🔬 Methodology

This project follows a structured end-to-end analytics workflow:

1. **Data Collection & Design** — Defined the business problem, designed a 3-table relational dataset structure (Shipments, Carriers, Routes), and generated a realistic raw dataset with intentional data quality issues to simulate real-world operational data.

2. **Data Quality Audit** — Manually inspected all 3 raw tables and documented 21 data quality issues before any cleaning began (see [`03_data_issue_log.md`](docs/03_data_issue_log.md)).

3. **Data Cleaning** — Resolved all 21 issues using Excel formulas and built-in tools. Each fix was documented with the problem, logic, formula used, and outcome (see [`04_data_cleaning_log.md`](docs/04_data_cleaning_log.md)).

4. **Data Modeling** — Loaded the 3 cleaned tables into Power Pivot and created a star schema with relationships (Shipments as the fact table, Carriers and Routes as dimension tables). Added calculated columns (Delay_Days, OTD_Flag, Cost_per_KM) and a reusable DAX measure (Late %).

5. **Analysis** — Conducted 6 PivotTable-based analyses covering OTD trend, carrier performance, region/route breakdown, delay vs cost correlation, and day-of-week patterns.

6. **Dashboard** — Built a single-page executive dashboard with 4 KPI cards and 5 charts to present findings visually.

7. **Insights & Recommendations** — Synthesized findings into 3 targeted, data-backed recommendations for management action.

---

## 🛠️ Tools & Techniques

| Tool / Feature | Purpose |
|---|---|
| **Excel Formulas & Built-in Tools** | Data cleaning — date standardization, duplicate removal, missing value handling, type conversion (TEXT, DATE, IF, ABS, TRIM, PROPER, Find & Replace) |
| **Power Pivot / Data Model** | Relational modeling — 3-table star schema (Shipments ↔ Carriers ↔ Routes) |
| **DAX Measures** | Calculated KPIs — Late %, used across all PivotTables |
| **Calculated Columns** | Delay_Days, OTD_Flag, Cost_per_KM |
| **PivotTables** | Multi-dimensional analysis across carrier, region, route, and time |
| **Excel Charts** | Bar charts, line charts — custom color gradients for visual ranking |
| **Dashboard** | Single-page executive dashboard with 4 KPI cards and 5 charts |

---

## 📊 Dashboard Preview

<p align="center">
  <img src="dashboard.PNG" alt="dashboard_image" width="1000">
</p>

📄 **Full dashboard insights, business interpretation, and recommendations:** [`Dashboard Insight Report`](docs/05_insight_report.md)

---

## 🧹 Data Cleaning Highlights

The raw dataset was intentionally messy to simulate real-world operational data. **21 data quality issues** were identified and resolved across 3 tables.

Key issues handled:
- **5 mixed date formats** in the same column → standardized to `YYYY-MM-DD`
- **Logical vs. true missing values** in `Delay_Reason` → classified as `None`, `Missing Reason`, or `Review Required`
- **3 inconsistent Carrier_ID formats** → standardized to `C-0X`
- **Negative Shipment_Cost values** → corrected using `ABS()` function
- **Typos in categorical values** → corrected via Find & Replace

Full cleaning documentation: [`data_cleaning`](docs/04_data_cleaning_log.md)

---

## 📊 Key Findings

- 📉 Overall OTD Rate: **54.52%** — critically below the 85%+ industry benchmark
- 🚨 Worst carrier: **Padma Freight Co.** — 41.17% late rate + highest cost penalty on delays
- 🗺️ Worst region: **Chittagong** (36.00%) | Worst route: **Rajshahi Rural Belt** (37.64%)
- 📅 Worst days: **Tuesday (43.15%)** and **Monday (41.01%)** — week-start backlog effect
- 💰 Delay and cost are **weakly correlated** — delay is a service quality issue, not a cost driver

---

## ✅ Recommendations

1. **Review Padma Freight Co. contract** — SLA renegotiation or partial route reallocation to Karatoa Express
2. **Strengthen rural route coverage** — dedicated carriers and route-specific SLAs for top 3 worst routes
3. **Redistribute Monday–Tuesday shipment load** — increase Friday/Saturday processing to reduce week-start backlog

Full findings: [`details_report`](docs/05_dashboard_insight.md)

---

## ⚠️ Limitations & Future Improvements

**Limitations:**
- The dataset is **synthetically generated** — findings reflect simulated patterns, not real operational data
- **No product category or order value data** — cost analysis is limited to shipment-level cost only; revenue impact of delays could not be quantified
- **Delay_Reason has data gaps** — 76 delayed shipments had no recorded reason (`Missing Reason`), limiting root-cause analysis depth
- **Dashboard is static** — charts are not connected to slicers due to the mix of PivotCharts and manual charts; filtering requires going to individual analysis sheets

**Future Improvements:**
- Integrate actual delivery GPS/route data for more precise delay root-cause analysis
- Add a **Supplier Performance** dimension to track upstream delays
- Rebuild the dashboard in **Power BI** for full interactivity and slicer connectivity
- Expand the dataset to include **order value and revenue** to quantify the financial impact of delays

---

## 👩‍💻 Author

**Maksuda Akter**

Junior Data Analyst | Supply Chain & Logistics Domain

[GitHub](https://github.com/quietwithsuborno) · [LinkedIn](https://www.linkedin.com/in/maksuda-akter-suborno-9957573ab/)
