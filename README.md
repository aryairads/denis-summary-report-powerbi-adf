# Denis Summary Report – Power BI + Azure Data Factory

## Overview
This project showcases the Denis Summary Report built in Power BI, using data processed through an Azure Data Factory pipeline following the Medallion Architecture (Bronze → Silver → Gold). The dashboard provides insights into revenue, cost, profit, and product/state-level performance.

## Dashboard Preview
![Denis Summary Dashboard](screenshots/denis_summary_dashboard.png)

## PBIX File
`Dennis_Summary_Report.pbix` contains the complete Power BI dashboard with:
- Revenue, cost, and profit KPIs
- Product-wise and state-wise performance
- Monthly trends and gross profit analysis
- Clean layout designed for management insights

## Repository Structure
- `Dennis_Summary_Report.pbix`  
- `/screenshots` – Dashboard images  
- `/ADF-Pipeline-Design` – Pipeline documentation  
- `/data-model` – DAX, relationships, and model screenshots  

## Tech Stack
Power BI | Azure Data Factory | SQL Server | DAX | Power Query

## Note
The original ADF pipeline was created in a trial Azure account that has since expired. This repository includes a reconstructed pipeline design for portfolio demonstration.
