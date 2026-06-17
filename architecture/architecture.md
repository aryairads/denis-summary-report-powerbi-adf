# Pipeline Architecture – Denis Summary Report

![Azure Pipeline Architecture](architecture_diagram.png)

---

## Description

### 1. **On‑Premises Source**
- Product data originates from internal systems.
- Connected to Azure Data Factory through **Self‑Hosted Integration Runtime (SHIR)**.

### 2. **Storage Layer**
- **Blob Storage** holds structured and semi‑structured files (Excel, JSON).
- **ADLS** stores raw sales folders for scalable data ingestion.

### 3. **Processing Layer**
- **Azure Data Factory (ADF)** orchestrates data movement and transformation.
- Data Flows perform joins, derived columns, and aggregations.
- Linked Services (LS1–LS4) manage secure connections between components.

### 4. **Storage Layer (Gold)**
- Processed data is loaded into **Azure SQL Database (asqldb)**.
- Serves as the curated data source for Power BI.

### 5. **Visualization Layer**
- **Power BI (pbi)** connects directly to Azure SQL Database.
- Provides interactive dashboards and KPIs for business insights.

---

## Key Notes
- Architecture follows the **Medallion pattern** (Bronze → Silver → Gold).  
- Secure data transfer via **Azure Integration Runtime (AIR)** and **SHIR**.  
- Supports **Row‑Level Security (RLS)** and **scheduled refreshes** in Power BI Service.  
- Designed for scalability, automation, and enterprise‑grade analytics.

---

## Tags
`Azure Data Factory` • `Azure SQL Database` • `Power BI` • `Blob Storage` • `ADLS` • `ETL` • `Medallion Architecture`
