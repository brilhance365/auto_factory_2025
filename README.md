# Auto Factory 2025: Industrial Data Pipeline 🏭⚙️
### Medallion Architecture on Databricks | From Shop Floor to Actionable Insights

This project demonstrates an end-to-end industrial data pipeline built on **Azure Databricks**, transforming raw manufacturing silos into structured, analysis-ready datasets. 

As a professional with **14+ years of experience in Industrial Operations, Quality, and Continuous Improvement**, I developed this project to bridge the gap between "physical" shop floor reality and modern data engineering practices.

---

## 🎯 Project Motivation
Coming from a background in **Lean Manufacturing, RCA, and Quality Management (PSA Groupe)**, I understand that data is only valuable if it drives operational intervention. This pipeline was designed to answer:
- Which production teams have the best performance-to-quality ratio?
- Where are the biggest daily "improvement opportunities" by shift?
- How do maintenance logs (SAP style) correlate with real-time downtime?

## 🛠️ The Medallion Pipeline
The architecture follows the **"ETL Understood"** principles, focusing on **Idempotency, Data Contracts, and Observability**.

### 1. Bronze (Raw Ingestion)
- **Ingestion:** Automated ingestion of Excel (Factory tables), CSV (Maintenance/HR), and JSONL (Quality/Safety).
- **Metadata:** Injection of `_input_file_name` and `_ingestion_timestamp` for full lineage.
- **Organization:** Normalization of source names and automatic file archiving post-processing.

### 2. Silver (Cleansing & Standardization)
- **Data Contracts:** Implementation of schema enforcement and type casting (PySpark).
- **Quality Logic:** Separation of valid records from rejections (Quarantine pattern).
- **Reliability:** Deduplication using business keys and `MERGE` (Upsert) logic to ensure idempotency.

### 3. Gold (Business Insights)
- **Focus:** Team-by-team performance ranking and shift-level operational loss analysis.
- **Value:** Aggregated tables ready for **Power BI** or **Direct SQL Analysis** to support Gemba walks and daily meetings.

---

## 📂 Repository Structure
```text
├── 01_ingestion_orders.ipynb   # Multi-source raw ingestion
├── 02_bronze_orders.ipynb      # Bronze layer management
├── 03_silver_orders.ipynb      # Data cleaning, Contracts & Quality rules
├── 04_gold_orders.ipynb        # KPI Aggregations & Team Insights
├── run_pipeline.ipynb          # End-to-end Orchestrator
├── utils.ipynb                 # Shared helper functions
└── README.md                   # Documentation
