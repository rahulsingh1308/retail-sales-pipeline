# Retail Sales Intelligence Pipeline

An end-to-end data engineering project built on **Azure** and **PySpark** using the **Medallion Architecture** (Bronze → Silver → Gold).

## Architecture
## Tech Stack

| Tool | Purpose |
|---|---|
| Azure Data Factory | Pipeline orchestration and ingestion |
| ADLS Gen2 | Data lake storage (Bronze/Silver/Gold) |
| Apache PySpark 3.4 | Data transformation and aggregation |
| Delta Lake | ACID-compliant Gold layer storage |
| Python 3.12 | Development environment |

## Project Structure
## Pipeline Stages

### Bronze Layer
Raw CSV data ingested from source and landed as-is into ADLS Gen2 Bronze container via ADF Copy Activity.

### Silver Layer
ADF pipeline converts raw CSV to Parquet format with column name sanitization to meet Parquet schema requirements.

### Gold Layer
PySpark transformations produce three business-ready Delta tables:
- **monthly_revenue** — Total revenue, orders, and unique customers by country and month
- **top_products** — Products ranked by total revenue and quantity sold
- **customer_rfm** — Recency, Frequency, Monetary scoring for each customer

## Dataset
[Online Retail II Dataset](https://archive.ics.uci.edu/dataset/502/online+retail+ii) — UCI Machine Learning Repository (~1M transactions)

## Key Transformations
- Null handling and deduplication
- Removal of cancelled orders and invalid records
- Derived column creation (TotalAmount, Year, Month)
- Window-based aggregations for business metrics
- RFM customer segmentation
