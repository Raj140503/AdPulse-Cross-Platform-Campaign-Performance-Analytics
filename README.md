# AdPulse — Cross-Platform Campaign Performance Analytics

A marketing analytics project that unifies Facebook Ads, Google Ads, and TikTok Ads data using SQL and Google BigQuery, then visualizes campaign performance in Tableau to support data-driven marketing decisions.

## Project Overview

Marketing teams often struggle to compare advertising performance across platforms because each platform uses different column names, data structures, and available metrics.

**AdPulse** addresses this challenge by consolidating advertising data into a unified analytical dataset and presenting key performance indicators through an executive Tableau dashboard.

The project demonstrates an end-to-end analytics workflow, from raw data validation and SQL-based transformation to KPI development, visualization, and business-oriented performance analysis.

## Project Objectives

- Consolidate advertising data from three digital marketing platforms into a standardized dataset.
- Resolve differences in column names and platform-specific schemas using SQL.
- Validate record counts, reporting dates, and aggregate metrics before visualization.
- Analyze campaign efficiency using consistent KPI definitions.
- Build an interactive dashboard to compare platform and campaign performance.
- Support marketing decisions through clear performance reporting and analytical insights.

## Technology Stack

| Category | Tools |
|---|---|
| Data Analysis & Transformation | SQL |
| Cloud Data Warehouse | Google BigQuery |
| Business Intelligence | Tableau Desktop |
| Data Visualization | Tableau Public |
| Data Sources | CSV files |
| Version Control | Git, GitHub |

## Data Overview

The project uses advertising data from three platforms over January 1–30, 2024.

| Platform | Source File | Records |
|---|---|---:|
| Facebook Ads | `01_facebook_ads.csv` | 110 |
| Google Ads | `02_google_ads.csv` | 110 |
| TikTok Ads | `03_tiktok_ads.csv` | 110 |
| **Total** | **3 CSV files** | **330** |

The source data contains advertising performance measures such as impressions, clicks, spend, conversions, and platform-specific engagement metrics.

The available fields differ across platforms. For example, cost is represented by different column names, and conversion value is available only in the Google Ads dataset.

## Data Engineering & SQL Workflow

### 1. Source Data Validation

Inspected the source tables to understand their schemas, date ranges, metric availability, and aggregate values.

### 2. Schema Standardization

Used SQL to standardize common fields, including advertising cost and ad group identifiers, into a consistent naming structure.

### 3. Data Unification

Combined the three source datasets using `UNION ALL` to create a consolidated `unified_ads` table in BigQuery.

The transformation preserves platform-specific fields and uses typed `NULL` values where a metric is not available for a particular platform.

### 4. Data Quality Validation

Validated the unified dataset against the original source tables by checking record counts, reporting dates, platform-level totals, and metric consistency.

The resulting analytical dataset contains 330 records and 24 columns.

### 5. Tableau Integration

Connected Tableau to the unified BigQuery dataset and developed calculated fields and visualizations for campaign performance analysis.

## Key Performance Indicators

The dashboard covers six core digital advertising metrics.

| KPI | Formula | Business Purpose |
|---|---|---|
| Click-Through Rate (CTR) | Clicks / Impressions × 100 | Measures the proportion of impressions that generate clicks |
| Cost Per Click (CPC) | Spend / Clicks | Measures the average cost of a click |
| Cost Per Acquisition (CPA) | Spend / Conversions | Measures advertising cost per reported conversion |
| Cost Per Mille (CPM) | Spend / Impressions × 1,000 | Measures cost per 1,000 impressions |
| Conversion Rate (CVR) | Conversions / Clicks × 100 | Measures the proportion of clicks resulting in conversions |
| Return on Ad Spend (ROAS) | Conversion Value / Spend | Measures reported conversion value relative to advertising spend |

Aggregate ratios are calculated using summed numerators and denominators rather than averaging individual row-level ratios.

**Metric limitation:** ROAS is available only for Google Ads because conversion value is not provided for Facebook Ads or TikTok Ads in the source data. It should not be interpreted as a directly comparable cross-platform KPI.

## Dashboard & Deliverables

- **Interactive Tableau Dashboard:** [Add your Tableau Public dashboard link]
- **SQL Transformation Scripts:** Available in this repository.
- **Source Datasets:** Facebook Ads, Google Ads, and TikTok Ads CSV files.
- **Tableau Workbook:** `marketing-analyst-assignment.twbx`

The dashboard is designed to help users explore advertising performance, compare platform-level results, identify campaign efficiency patterns, and investigate areas that may warrant optimization.

## Repository Structure

```text
AdPulse-Cross-Platform-Campaign-Performance-Analytics/
│
├── README.md
├── 00_validation_source_tables.sql
├── 01_create_unified_ads.sql
├── 01_facebook_ads.csv
├── 02_google_ads.csv
├── 02_validate_unified_ads.sql
├── 03_tiktok_ads.csv
└── marketing-analyst-assignment.twbx
```

## How to Reproduce the Project

### Prerequisites

- Access to Google BigQuery
- Tableau Desktop or a compatible Tableau environment
- The CSV files included in this repository

### Steps

1. Clone or download this repository.
2. Create a BigQuery project and a dataset for the advertising data.
3. Upload the three CSV files as separate source tables, ensuring that headers and data types are handled correctly.
4. Review and execute `00_validation_source_tables.sql` to inspect the source data.
5. Execute `01_create_unified_ads.sql` to create the consolidated analytical table.
6. Run `02_validate_unified_ads.sql` to validate the transformed data against the source tables.
7. Connect Tableau to the resulting BigQuery dataset.
8. Open the Tableau workbook or recreate the calculated fields and dashboard using the unified dataset.

**Note:** Review the table references in the SQL scripts and update them to match your own BigQuery project and dataset.

## Key Analytical Considerations

- Standardizing schemas makes cross-platform reporting more consistent.
- Data validation helps identify discrepancies introduced during transformation.
- Platform-specific metrics should be retained where useful but not compared as if they were universally available.
- Aggregate KPIs must use consistent definitions and appropriate denominators.
- Reported conversions and conversion value may reflect platform-specific attribution methods.
- Campaign performance metrics alone do not establish profitability or prove that a particular optimization caused an improvement.

## Future Enhancements

- Automate data ingestion through advertising platform APIs.
- Add scheduled refreshes and a more scalable transformation pipeline.
- Incorporate revenue and conversion-value data across platforms for more comprehensive efficiency comparisons.
- Introduce campaign-level performance alerts and configurable reporting periods.
- Extend the analysis with budget allocation scenarios and additional marketing performance dimensions.

## Skills Demonstrated

**SQL · Google BigQuery · Data Cleaning · Data Validation · Data Modeling · KPI Development · Tableau · Marketing Analytics · Data Visualization · Business Intelligence**

---

Developed by **Raj Patil**.
