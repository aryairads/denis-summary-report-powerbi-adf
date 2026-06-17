# ADF Pipeline Steps – Denis Summary Report

## Overview
This document explains the Azure Data Factory (ADF) pipeline used to build the Denis Summary Report dataset.  
The pipeline follows a **Medallion Architecture** (Bronze → Silver → Gold) for structured data transformation and loading.

---

## 1. Bronze Layer – Raw Data Ingestion
**Purpose:** Collect raw source data from multiple systems.

**Steps:**
1. Create a **Linked Service** to connect to the source (SQL Server / Blob Storage).  
2. Use a **Copy Data activity** to extract raw tables:
   - `Denis_TB` (transaction data)
   - `Access_TB` (region mapping)
   - `DateMaster` (calendar data)
3. Store all raw files in the **Bronze container** in Azure Data Lake.

---

## 2. Silver Layer – Data Cleaning and Transformation
**Purpose:** Standardize and clean the ingested data.

**Steps:**
1. Add a **Data Flow activity** to perform transformations:
   - Remove nulls and duplicates.  
   - Rename columns for consistency.  
   - Apply data type conversions.
2. Output the cleaned tables to the **Silver container**.

---

## 3. Gold Layer – Aggregation and Modeling
**Purpose:** Prepare analytical data for Power BI consumption.

**Steps:**
1. Use a **Mapping Data Flow** to join tables:
   - Join `Denis_TB` with `Access_TB` on `Country`.  
   - Join with `DateMaster` on `Date`.
2. Create calculated columns for:
   - `Profit = Revenue - Cost`
   - `MonthName`, `Year`, `Quarter`
3. Store the final dataset in the **Gold container**.

---

## 4. Pipeline Orchestration
**Purpose:** Automate and schedule the workflow.

**Steps:**
1. Add **Sequential activities** for Bronze → Silver → Gold execution.  
2. Configure **triggers**:
   - Daily refresh at 6 AM.  
   - On-demand manual trigger for testing.
3. Add **Error handling** using “On Failure” paths and email alerts.

---

## 5. Integration with Power BI
**Purpose:** Connect the Gold dataset to Power BI.

**Steps:**
1. Create a **Power BI dataset** using the Gold layer output.  
2. Publish the `.pbix` file to Power BI Service.  
3. Set up **scheduled refresh** using the same ADF trigger logic.

---

## Notes
- The pipeline uses **parameterized datasets** for flexibility.  
- Each layer is stored in separate folders for clarity.  
- The design ensures scalability and easy maintenance.

