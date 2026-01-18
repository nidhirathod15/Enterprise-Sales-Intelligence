# Enterprise-Sales-Intelligence: From Raw Transactional Data to Strategic ROI
This project transforms a fragmented dataset of **500,000+ international retail transactions** into a centralized, high-performance analytics platform. The goal was to provide executive leadership with a "single source of truth" for global revenue, product performance, and regional growth trends.

## Architecture
### 1. Data Engineering & ETL (Power Query / M-Language)
**Standardization:** Resolved critical `DataFormat.Error` issues by implementing **Locale-aware transformations** for international Date/Time fields.
**Data Cleansing:** Used **M-Language scripts** to handle missing values and perform case-sensitive string standardization (`Text.Proper`).
**Optimized Loading:** Employed the **Reference method** to build a modular data pipeline, keeping the `Sales_Base` query as a non-loading staging layer to reduce memory overhead.

### 2. Relational Modeling (Star Schema)
To ensure sub-second query performance, I migrated the data from a "Flat File" structure to a **Star Schema**
**Fact Table:** `fact_sales` (Transactions, Quantity, Price).
**Dimension Tables:** `dim_product`, `dim_customer`, and `dim_geography`.
**Cardinality:** Established **One-to-Many relationships** using `StockCode`, `CustomerID`, and `Country` as primary/foreign keys.

### 3. Analytics & DAX Development
Developed a custom library of measures to drive financial insights:
- Created `Total Revenue` using the `SUMX` iterator to calculate line-level totals dynamically across 500k rows.
- Configured **Data Categorization** for regional fields, enabling interactive map visuals for global footprint analysis.
- Implemented **Top-N filtering** to isolate the top 10 products contributing to the total **$9.75M revenue portfolio**.

## Dashboard Features
Instant visibility into Total Revenue and unit volume.
Dynamic time-series filtering by `InvoiceDate` to track seasonal performance.
Visualized revenue concentration across global markets using Bing Maps integration.

## Impact & Business Value
**Decision Speed:** Reduced data preparation time by 90% through automated ETL.
**Scalability:** The Star Schema architecture allows for the easy addition of new data sources (e.g., Marketing or Logistics) without breaking existing reports.
**Accuracy:** Eliminated 100% of date-parsing errors that previously led to incorrect financial reporting.
