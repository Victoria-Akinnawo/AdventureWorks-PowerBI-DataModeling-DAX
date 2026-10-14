# AdventureWorks Sales Analytics & Data Modeling (Power BI)

## 📌 Project Overview
This project showcases end-to-end data preparation, Star-Schema modeling, customer segmentation, and business intelligence DAX calculations using the **AdventureWorks** dataset in Power BI.

---

## 🏗️ Data Architecture & Modeling
Built a clean **Star-Schema** relational data model connecting fact and dimension tables:
- **Fact Table:** `FactInternetSales`
- **Dimension Tables:** `DimCustomer`, `DimDate`, `DimProduct`, `DimSalesTerritory`, `DimGeography`
- **Relationships:** Established 1-to-Many (`1:*`) single-direction relationships across dimensions.

---

## 🧹 Data Cleaning & Calculated Columns
Created custom DAX calculated columns to segment customer demographics and enhance analytics:

### 1. Customer Age Segmentation (`Age Bracket`)
```dax
Age Bracket = 
IF(DimCustomer[AGE] < 20, "Adolescent",
    IF(DimCustomer[AGE] < 35, "Youth",
        IF(DimCustomer[AGE] < 50, "Adult", "Old Adult")
2. Customer Income Band Segmentation (income_band)
income_band = 
SWITCH(
    TRUE(),
    DimCustomer[YearlyIncome] < 50000, "Low income",
    DimCustomer[YearlyIncome] < 90000, "Medium income",
    DimCustomer[YearlyIncome] < 150000, "High income",
    "Extremely high income")
3. Purchase Month Extraction (month)
month = FORMAT(DimCustomer[DateFirstPurchase], "mm")

    📐 Key DAX Measures Created
Core Financial & Operational KPIs
Total Revenue: $29.36M

Total Customers: 18,484

Total Orders: 27,659

Products Sold: 158

Total Product Catalog: 606
Advanced DAX Logic
-- High-Value Segment Analysis
revenue_cost_ABOVE_150K = [DAX Measure for high-income cohort revenue]

-- Order Counts for High-Income Tier
orders_extremelyhighincome_customers = [DAX Measure for extremely high income orders]
📊 Key Insights & Customer Segments
Medium & Low Income segments contribute the largest share of total revenue ($11.91M and $10.55M respectively across 11,000+ orders each).

High & Extremely High Income segments represent premium customer cohorts with high average order values ($6.11M and $777.88K).

📁 Files Included
AdventureWorks.pbix — Complete Power BI workbook containing models, calculated columns, and measures.
