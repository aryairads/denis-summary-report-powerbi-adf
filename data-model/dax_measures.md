# DAX Measures – Denis Summary Report

## Overview
This file documents all DAX measures used in the Denis Summary Report Power BI model.  
These measures support KPI cards, trend visuals, and time‑based analysis.

---

## Total REv
```DAX
Total REv = SUM(Denis_TB[Revenue])
Total Cost
DAX
Total Cost = SUM(Denis_TB[Cost])
Profit
DAX
Profit = [Total REv] - [Total Cost]
PreviousMonth Rec
DAX
PreviousMonth Rec =
    CALCULATE(
        [Total REv],
        DATEADD(DateMaster[Date], -1, MONTH)
    )
MoM
DAX
MoM =
    DIVIDE(
        [Total REv] - [PreviousMonth Rec],
        [PreviousMonth Rec]
    )
%Contribution
DAX
%Contribution =
    DIVIDE(
        [Total REv],
        CALCULATE([Total REv], ALL(Denis_TB))
    )
Revenue All
DAX
Revenue All = CALCULATE([Total REv], ALL(Denis_TB))
Notes
All time‑based measures use the DateMaster table.

Denis_TB is the main fact table for all calculations.

Total Cost = SUM(Denis_TB[Cost])


Measures are optimized for KPI cards, trend charts, and comparison visuals.
