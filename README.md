# Call Centre Performance Dashboard
<img width="1429" height="655" alt="Screenshot 2025-09-17 210248" src="https://github.com/user-attachments/assets/0e22b004-a7da-4e6b-8a9f-4130e3db5b9d" />



An Excel-based interactive dashboard to monitor call centre KPIs: call volume, average handle time, customer satisfaction, agent performance, and trends by time and category.

## What’s inside
- Power Pivot data model joining **Calls** and **Customers** on `Customer ID`.
- Slicers for **Representative**, **Day of week**, **FY**, and other categories.
- Interactive charts and KPI cards with conditional formatting.
- Pivot Tables powered by DAX measures.

## Data model
**Tables**
- **Calls**: `Call number`, `Customer ID`, `Duration`, `Representative`, `Date of Call`, `Purchase Amount`, `Satisfaction Rating`, `FY`, `Day of week`, `Duration Bucket`, `Rating rounded`
- **Customers**: `Customer ID`, `Gender`, `Age`, `City`

**Relationship**
- `Calls[Customer ID]` → `Customers[Customer ID]` (Many-to-One)

## Measures (DAX)


```DAX
Call Count  = COUNTROWS(Calls)
```

```DAX
Distinct Customers = DISTINCTCOUNT(Calls[Customer ID])
```
```DAX
Total Amount = SUM(Calls[Purchase Amount])
```
```DAX
Total Duration (mins) = SUM(Calls[Duration])
```
```DAX
Avg Rating = AVERAGE(Calls[Satisfaction Rating])
```
```DAX
5 Star Calls =
    CALCULATE(
        [Call Count],
        Calls[Rating rounded] = 5
    )
```
```DAX
% 5 Star Calls := DIVIDE([5 Star Calls], [Call Count])
```

## How to use

1. Open `CallCentre_Performance_Dashboard.xlsx`.  
2. On the **Customer Centre Report** sheet, use the slicers (Representative, Day of week, FY, etc.) to filter the view.  
3. Hover over visuals to read exact values — KPI cards update automatically with your selections.  

---

## How it works

1. The **Data** sheet holds raw records for Calls and Customers (side-by-side).  
2. In **Power Pivot**, both tables were added to the Data Model and related via `Customer ID`.  
3. In the **Pivot Table** sheet, a pivot was created from the Data Model and DAX measures were added.  
4. Slicers were connected to the pivot to control all visuals.  
5. Interactive charts were built from the pivots, and conditional formatting was applied to highlight KPIs.  
6. Stock images from Excel were used for the visual header — these are placeholders, not real customer photos.  



