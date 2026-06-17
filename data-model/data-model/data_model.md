# Data Model – Denis Summary Report

## Overview
The data model for the Denis Summary Report is designed using a simple and efficient star-schema layout.  
It consists of one fact table (`Denis_TB`) and two dimension tables (`DateMaster` and `Access_TB`).  
This structure supports time intelligence, regional analysis, and KPI calculations used in the Power BI dashboard.

---

## Tables

### **1. Denis_TB (Fact Table)**
Contains the core transactional data including:
- Revenue
- Cost
- Profit
- Country
- Date
- Other sales-related fields

This is the central table used for all KPI and trend calculations.

### **2. DateMaster (Date Dimension)**
A full calendar table used for:
- Month-over-month (MoM) calculations
- Previous month comparisons
- Time intelligence functions

### **3. Access_TB (Region Dimension)**
Contains location and access information:
- Country / Region mapping
- Used to categorize sales by geography

---

## Relationships

### **1. Denis_TB[Date] → DateMaster[Date]**
- Type: One-to-many  
- Purpose: Enables all time-based calculations (MoM, Previous Month, YTD, etc.)

### **2. Denis_TB[Country] → Access_TB[Location]**
- Type: One-to-many  
- Purpose: Links each sale to its corresponding region for geographic analysis

These two relationships form a clean star schema with `Denis_TB` at the center.

---

## Measures Summary
The model includes six DAX measures used in the dashboard:

- **%Contribution** – Shows each category or region’s contribution to total revenue  
- **MoM** – Month-over-month growth  
- **PreviousMonth Rec** – Revenue from the previous month  
- **Profit** – Revenue minus cost  
- **Revenue All** – Total revenue across all filters  
- **Total REv** – Main revenue measure used in KPI cards  

Full DAX formulas are available in `dax_measures.md`.

---

## Data Model Diagram
Below is the visual representation of the model, showing tables, relationships, and measures:

![Data Model](data-model/data_model.png)

---

## Notes
- The model uses a semantic layer with culture `en-US`.  
- Relationships are single-direction to maintain performance and avoid ambiguity.  
- Measures are optimized for Power BI visuals and time intelligence.
