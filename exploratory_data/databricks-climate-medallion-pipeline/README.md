# Climate & Energy Data Pipeline - Medallion Architecture 🌍🔋

This project implements a complete Data Engineering pipeline using the **Medallion Architecture (Bronze, Silver, and Gold)** in **Databricks** with **Apache Spark / PySpark**. The main goal is to ingest, clean, and consolidate complex data regarding global CO2 emissions, energy mixes, temperature anomalies, and extreme climate events for downstream analytical insights.

---

## 📁 Pipeline Structure (Notebooks)

The data processing is divided into three logical layers to ensure robust data governance and quality:

1. **`01_bronze_layer.ipynb` (Raw Ingestion)**:
   * Reads raw CSV files from the local source data directory (`raw-data`).
   * Preserves the original state of the source data while appending crucial metadata for audit trails (`ingestion_timestamp`).
   * Writes the resulting datasets into the Delta catalog using the layer's native naming conventions: `bronze.co2_raw`, `bronze.energy_raw`, `bronze.temperature_raw`, and `bronze.climate_raw`.

2. **`02_silver_layer.ipynb` (Cleaning & Standardization)**:
   * Handles explicit data type casting (converting string formats into native `date`, `timestamp`, `double`, and `integer` types).
   * Standardizes column headers across all tables to match the *snake_case* naming convention.
   * Performs basic data enrichment and maintains processing timelines via a custom `silver_timestamp` tracking column.
   * Persists clean, validated tables to the catalog: `silver.co2_emissions`, `silver.energy_mix`, `silver.temperature_anomaly`, and `silver.climate_events`.

3. **`03_gold_layer.ipynb` (Analytical / Business Layer)**:
   * Builds high-performance analytical aggregates ready to be consumed by BI tools (Power BI, Tableau) or business dashboards.
   * Joins and correlates energy mix evolutions with global temperature anomalies to answer critical environmental impact queries.

---

## 🛠️ Tech Stack & Architecture Patterns

* **Platform**: Databricks Lakehouse.
* **Processing Engine**: Apache Spark (PySpark DataFrame API & Spark SQL).
* **Storage Format**: Delta Lake (Supporting ACID transactions, Schema Enforcement, and Time Travel versioning).
* **Architecture Pattern**: Medallion Framework (Ensuring structured maturity steps for raw data assets).

---

## 🧠 Architectural FAQ

### Why split the pipeline into Bronze, Silver, and Gold layers?
This pattern guarantees idempotency and data recovery safety. If business logic rules change at the Gold tier, you do not need to re-ingest raw data from the external source system; you simply replay your calculations starting directly from your Silver or Bronze tables, saving valuable cluster computation time and cost.

### What is the advantage of storing data as Delta tables?
The Delta Lake storage layer fixes historical pain points associated with raw Parquet or CSV flat files. It provides true ACID transactions (guaranteeing that data writes either complete successfully or fail gracefully without causing data corruption), unlocks data version histories (Time Travel), and leverages native indexing engines built directly into Databricks to speed up complex query executions.

### Do Spark SQL and PySpark run differently on the underlying cluster?
No. Under the hood, both APIs compile down to the exact same execution instructions via Spark's Catalyst Optimizer. The choice between PySpark and Spark SQL in this project boils down to code readability: PySpark was chosen to handle structured, program
