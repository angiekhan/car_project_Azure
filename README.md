# car_project_Azure

Tools used:
Azure Data Factory (ADF) | Azure SQL Server | Azure Data Lake (ADLS Gen2) | Databricks | Unity Catalog | PySpark | Delta Lake | Medallion Architecture
✅ Azure Data Factory (ADF) for ETL Orchestration
✅ Incremental Loading with Lookup Activity
✅ Slowly Changing Dimensions (SCD Type 2) in Databricks
✅ Fact & Dimension Modeling using Star Schema

Workflow: 
1️⃣ Extract Data from API → ADF Ingests data into Azure Data Lake (Bronze)
2️⃣ Transform & Cleanse Data → Databricks processes raw data (Silver Layer)
3️⃣ Load into Data Warehouse → Azure SQL (Gold Layer) for reporting & analytics
4️⃣ Implement SCD Type 2 in Databricks for tracking historical changes

Data Pipeline Architecture - Medallion Architecture Implementation:

Bronze Layer → Stores raw data in ADLS Gen2
Silver Layer → Transforms data into cleaned format using PySpark
Gold Layer → Loads fact & dimension tables into Azure SQL for analytics

Step-by-Step Setup Implementation:
1️⃣ Azure Resource group Setup
Azure Data Lake (ADLS Gen2) → Store bronze, silver, gold layers
Azure SQL Server & Database → Data Warehouse
Azure Data Factory (ADF) → ETL Orchestration
2️⃣ Azure Data Factory (ADF) Pipelines
Ingestion Pipeline → Extract API Data & store in Bronze Layer
Incremental Load Pipeline → Lookup last processed data & load new records
3️⃣ Databricks Transformation
Read Bronze Layer data (abfss://bronze@carindiradatalake.dfs.core.windows.net/)
Transform in PySpark & store in Silver Layer
Apply SCD Type 2 logic in scd_type_2.py
Store results in Gold Layer (abfss://gold@carindiradatalake.dfs.core.windows.net/)
4️⃣ Unity Catalog & Delta Lake
Manage data governance using Unity Catalog
Store Delta Tables in ADLS Gen2 (external tables)

