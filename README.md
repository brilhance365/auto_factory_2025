# auto_factory_2025
# Industrial Data Pipeline: Medallion Architecture with Databricks 🏭⚙️

This repository contains the implementation of an end-to-end data pipeline using the **Medallion Architecture** on Azure Databricks. The project focuses on transforming industrial data silos (Production, Maintenance, Quality and HR) into actionable insights for shop floor management.

## Project Overview
The aim is to consolidate fragmented data from various manufacturing systems to enable analysis of overall efficiency (OEE), root causes of downtime, and the correlation between team performance and quality.

The project follows the principles of **Idempotence, Data Contracts and Observability** based on the *ETL Understood* framework.

---

## Pipeline Architecture

### 1. Bronze Layer (Raw Ingestion)
Responsible for capturing data ‘as-is’.
- **Data Sources:** Excel (Factory Tables), CSV (Maintenance, HR, Engineering), JSON/JSONL (Safety, Quality) and Downtime Events.
- **Processing:** Parameterised ingestion via PySpark.
- **Highlights:** 
  - Automatic normalisation of table names.
  - Injection of technical metadata (`_input_file_name`, `_ingestion_timestamp`).
  - Automatic movement to the archive folder post-processing.

### 2. Silver Layer (Refinement and Quality) - *Under Development*
Where data gains operational reliability.
- **Standardisation:** Application of data types (casting) and standard column names.
- **Quality (Data Contracts):** Separation of valid and rejected records (`quarantine`).
- **Deduplication:** Record retention logic based on business keys.
- **Idempotence:** Use of `MERGE` (Upsert) to ensure repeatability without duplication.

---

## 📂 Repository Structure

```text
├── notebooks/
│   ├── 00_utils/             # Auxiliary functions (Log, IO, normalisation)
│   ├── 01_ingestion_orders/  # Initial load pipeline
│   └── 02_silver_orders/     # Cleaning and application of business rules
|   
├── samples/                  # Sample files (CSV, JSON, XLSX)
└── README.md                 # Project documentation
