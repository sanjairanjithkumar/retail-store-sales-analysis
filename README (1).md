# Retail Store Multi-Year Sales & Profitability Analysis

Order-level retail sales analysis covering **5,000 orders across 4 years (2022–2025)**, built as two parallel deliverables — a fully Excel-based dashboard and a Power BI star-schema dashboard — using the same underlying dataset.

---

## 📌 Overview

This project analyzes multi-year retail transaction data spanning 5 cities, 5 product categories, 5 stores, and two sales channels (Online/Store). It covers the full workflow from raw data to a decision-ready dashboard: cleaning, validation, modeling, and visualization — delivered in two forms so the same insights can be explored either in Excel or interactively in Power BI.

## 🎯 Objective

- Clean and validate the raw multi-year retail dataset.
- Analyze sales, revenue, and profit trends across years, months, cities/regions, categories, and channels.
- Compare Online vs Store channel performance and payment mode distribution.
- Identify the most and least profitable categories, cities, brands, and stores.
- Study the impact of discounting and product returns on overall profitability.
- Present these insights through an interactive dashboard for quick, data-driven decisions.

## 🗂️ Dataset

| | |
|---|---|
| **Rows × Columns** | 5,000 × 26 |
| **Time period** | January 2022 – December 2025 (4 full years) |
| **Cities / Regions** | Delhi (North), Mumbai (West), Chennai (South), Bangalore (South), Kolkata (East) |
| **Categories** | Grocery, Beauty, Electronics, Clothing, Home |
| **Stores** | 5 stores across 5 cities |
| **Channels** | Online (2,500 orders), Store (2,500 orders) |
| **Payment modes** | Card, Cash, UPI |
| **Unique customers / products / salespeople** | 500 / 200 / 60 |

**Key fields:** `OrderID`, `OrderDate`, `Month`, `Year`, `CustomerID`, `CustomerName`, `City`, `Region`, `ProductID`, `ProductName`, `Category`, `Brand`, `StoreID`, `StoreName`, `Channel`, `SalespersonID`, `PaymentMode`, `Quantity`, `UnitPrice`, `DiscountPct`, `CostPrice`, `Total Cost`, `Total Sales`, `Profit`, `Profit%`, `ReturnFlag`

## 🛠️ Tools & Tech Stack

| Deliverable | Tools |
|---|---|
| **Excel version** | Microsoft Excel — formulas (`COUNTBLANK`, `IFERROR`, `TRIM`), PivotTables & PivotCharts, conditional formatting, slicers |
| **Power BI version** | Power BI Desktop — Power Query Editor, star-schema data model, DAX measures, multi-page interactive report |

## 🧹 Data Cleaning

- Checked for duplicate records — **0 duplicate rows, 0 duplicate OrderIDs**.
- Verified all core transactional fields — fully populated, no missing values.
- Reviewed `ReturnFlag` — populated for only **~10% of orders** (500 of 5,000); the remaining 90% were treated as "not flagged / non-return" rather than errors.
- Standardized `OrderDate` and cross-checked it against `Month`/`Year`.
- Validated numeric fields for correct types and valid ranges (`Quantity` 1–8, `DiscountPct` 0–25%).
- Reviewed `Profit` for outliers — **351 orders (~7.0%)** have negative profit, kept as genuine loss-making transactions relevant to the profitability analysis.
- Confirmed consistent spelling/casing across `City`, `Region`, `Category`, `Brand`, `Channel`, and `PaymentMode`.

*(Power BI version additionally: split the flat table into a Fact Sales table plus `Dim_Customer`, `Dim_Product`, `Dim_Store`, and `Dim Calender` dimension tables, and built one-to-many relationships between each dimension and the fact table.)*

## 📊 Dashboards

### Excel Dashboard
- KPI cards: Total Orders, Total Sales, Total Profit, Average Profit%, Return Rate
- Year-over-year and month-over-month sales & profit trend charts
- City/Region, category/brand, and store-wise performance views
- Channel comparison (Online vs Store) and payment mode distribution
- Discount vs profit relationship view
- Slicers for year, month, city, category, channel, and payment mode

### Power BI Dashboard
Five interactive report pages:
1. **Overview** — KPI cards, Sales by Region, Profit by Brand, Top 10 Products, Sales by Brand treemap, Sales vs Profit by City
2. **Time Series Analysis** — Previous Year vs Current Year sales, sales by quarter across channel, sales by month, sales by month across region
3. **Sales & Profit Summary** — regional/brand/store breakdowns with KPI cards
4. **Category & City Deep-Dive** — brand/city cross-filtering
5. **Regional & Time-Intelligence Tables** — region-specific KPIs and YTD/QTD/MTD detail tables

Includes custom DAX measures for YTD, QTD, MTD, previous-year comparisons, and filtered KPIs (e.g. Online-channel average sales, South-region orders).

## 💡 Key Insights

- Average profit margin holds steady at **~22%** across all four years, with order volume fairly stable year over year (~1,200–1,280 orders/year).
- **~7% of orders are loss-making**, concentrated where discount rates run highest (up to 25%) relative to cost price — discount discipline matters more to profitability than order volume or channel mix.
- Category, city, and store performance vary enough that a single blended margin figure hides meaningful differences worth tracking separately.

## 📁 Repository Structure

```
├── data/
│   └── retail_store_multiyear_dataset.xlsx      # Raw dataset
├── excel-dashboard/
│   └── Retail_MultiYear_Dashboard.xlsx          # Excel dashboard + PivotTables
├── powerbi-dashboard/
│   └── Retail_Sales_Multi_year.pbix             # Power BI report
└── README.md
```

## 👤 Author

Sanjai — Data Analytics student (Python with Data Analytics, QSpiders, Bengaluru)
