# Excel Data Analytics Project: Bike Sales Dashboard

## Project Overview
This project demonstrates an end-to-end data analytics workflow using Microsoft Excel. The objective is to take raw demographic and consumer data of potential bike buyers, clean and structure it, and build an interactive, executive-facing dashboard to uncover patterns driving bike purchases. 

This project covers key data analyst competencies: **Data Cleaning, Feature Engineering (Nested IFs), Data Modeling (Pivot Tables), Data Visualization, and Interactive Dashboard Design.**

## Dataset Description
The source dataset contains demographic tracking details for 1,000 customers. Key features include:
* `ID`: Unique customer identifier.
* `Marital Status`: Relationship status (originally abbreviated).
* `Gender`: Customer gender (originally abbreviated).
* `Income`: Annual income.
* `Children`: Number of children.
* `Education` & `Occupation`: Socioeconomic metrics.
* `Home Owner`: Binary indicator (`Yes` / `No`).
* `Cars`: Count of vehicles owned.
* `Commute Distance`: Range of distance to the workplace.
* `Region`: Geographic location (`North America`, `Europe`, `Pacific`).
* `Age`: Continuous numerical age.
* `Purchased Bike`: The target variable (`Yes` / `No`).

---

## Workflow & Implementation Steps

### 1. Data Cleaning & Staging
To protect data integrity, the raw data was staged into a dedicated `Working Sheet` before starting any transformations. The following operations were applied:
* **Duplicate Removal:** Identified and eliminated duplicate rows based on the unique customer IDs to prevent skewed analytical results.
* **Standardizing Categorical Values:** Used **Find and Replace** (`Ctrl + H`) to expand ambiguous single-letter abbreviations into descriptive strings:
    * `M` / `S` $\rightarrow$ `Married` / `Single` (Marital Status)
    * `M` / `F` $\rightarrow$ `Male` / `Female` (Gender)
* **Formatting Data Types:** Formatted the `Income` column explicitly as currency with removed decimal places for presentation clarity.
* **Fixing Non-Standard Sorting:** Addressed an Excel sorting anomaly where string ranges (e.g., `"10 Miles"`) sorted incorrectly by modifying categorical text strings to sort cleanly in standard charts.

### 2. Feature Engineering (Age Buckets)
Using continuous age variables in charts causes massive visual clutter. To group consumers into logical target demographic segments, a new column called `Age Brackets` was engineered using a **Nested IF statement**:

$$=IF(L2 > 54, "Old", IF(L2 >= 31, "Middle Age", IF(L2 < 31, "Adolescent", "Invalid")))$$

* **Adolescent:** Under 31
* **Middle Age:** 31 to 54
* **Old:** 55 and older

### 3. Data Modeling via Pivot Tables
Three individual pivot tables were built to isolate specific operational questions:
1.  **Income Analysis:** Looks at the average income of customers broken down by `Gender`, intersecting whether they did or did not buy a bike.
2.  **Commute Analysis:** Counts customer purchasing frequency (`Yes`/`No`) relative to their daily `Commute Distance`.
3.  **Age Demographic Analysis:** Isolates customer purchasing patterns across the newly engineered `Age Brackets`.

### 4. Interactive Dashboard Layout & Visualization
A dedicated `Dashboard` sheet was established with a minimalist, clean aesthetic:
* **Gridlines Removed:** Cleared standard cell grids (`View -> Gridlines`) to make the interface feel like native analytics software.
* **Visual Elements Built:**
    * *Clustered Column Chart:* Displays Average Income per Purchase by Gender.
    * *Clustered Column Chart (Commute):* Highlights bike purchase counts relative to commute distances.
    * *Line Chart with Markers:* Illustrates purchase trends across age categories, making it visually apparent that **Middle-Aged (31-54)** individuals are the primary buyers.
* **Cross-Functional Slicers:** Embedded interactive dashboard filters (`Marital Status`, `Region`, and `Education`). Utilizing **Report Connections**, these slicers were bound globally across all backend pivot tables, allowing stakeholders to dynamically slice and dice the metrics in real time.

---

## Key Business Insights Uncovered
* **The Income Gap:** Across both genders, individuals who ultimately purchased a bike had a higher average income threshold than those who did not. 
* **The Sweet Spot Demographic:** The core buying demographic peaks heavily with middle-aged consumers (ages 31–54). Adolescents and senior citizens buy significantly fewer bikes.
* **Commute Correlation:** Short-distance commuters (specifically those traveling 0–1 miles) represent the highest density of bike purchasers.

## Tools & Functions Utilized
* **Software:** Microsoft Excel
* **Formulas:** Nested `IF` statements
* **Features:** Pivot Tables, Pivot Charts, Slicers (Global Report Connections), Find & Replace, Data Type Formatting, and Gridline Toggling.

---

*Note: This repository/project folder contains the original dataset, the processing scratchpad sheet, and the finalized interactive dashboard interface.*
