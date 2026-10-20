# Power BI Assignment 1: Data Transformation & Data Modeling

## Project Overview
This project documents the end-to-end data preparation, cleaning, transformation, aggregation, and relational data modeling for an E-commerce sales dataset using **Power BI Desktop** and **Power Query Editor**.

---

## Datasets Handled
1. **List of Orders**: Contains order-level metadata including Order ID, Order Date, Customer Name, City, State, Category, Amount, and Profit.
2. **Order Details**: Contains line-item transaction records including Order ID, Category, Sub-Category, Quantity, Amount, and Profit.
3. **Sales Target**: Contains monthly category-wise sales targets.

---

## Step-by-Step Implementation Summary

### 1. Data Import & Transformation (Power Query)
- Imported `List of Orders.csv`, `Order Details.csv`, and `Sales Target.csv` into Power Query Editor [cite: 16].
- Restricted the `List of Orders` table to the first 500 rows as per project requirements [cite: 17].
- Configured correct data types: set `Order Date` to **Date**, and `Amount` & `Target` to **Fixed Decimal Number** [cite: 17].

### 2. Text Formatting & Custom Columns
- Formatted `CustomerName` to **Proper Case** for consistent capitalization [cite: 17].
- Created a custom **Location** column by merging `City` and `State` in the format: `City, State` [cite: 17].
- Created a custom calculated column **Profit Margin** (`Profit / Amount`, expressed as a percentage) [cite: 17].

### 3. Conditional Column (`Profit Status`)
- Added a conditional column evaluating profitability:
  - If `Profit < 0` $
ightarrow$ **Loss** [cite: 17]
  - If `Profit = 0` $
ightarrow$ **Break-Even** [cite: 17]
  - If `Profit > 0` $
ightarrow$ **Profit** [cite: 17]

### 4. Merging Data (Joins)
- Performed a **Left Outer Join** between `List of Orders` and `Order Details` using **Order ID** as the matching key [cite: 17].
- Named the resulting combined table **`Orders Data`** [cite: 17].

### 5. Handling Missing Data & Duplicates
- **Missing Data Strategy:** Inspected all tables for null values; removed blank/incomplete rows where essential transaction keys were missing to prevent metric skew.
- **Duplicate Strategy:** Identified and removed duplicate transaction records using `Order ID` as the unique key to ensure data integrity.

### 6. Sorting, Filtering & Aggregations
- Sorted the `Orders Data` table by `Order Date` in **Descending** order [cite: 18].
- Applied state-level filters (e.g., *Tamil Nadu*) for regional exploration [cite: 18].
- Duplicated `Order Details` and generated summary tables for:
  - Count of Order ID by Category [cite: 18]
  - Average Profit by Category [cite: 18]
  - Total Amount by Sub-Category [cite: 18]
- Duplicated `Sales Target` and aggregated total **Target by Month of Order Date** [cite: 18].

### 7. Data Modeling & Star Schema Design
- Established an active **One-to-Many ($1: st$)** relationship between `List of Orders` and `Order Details` using **Order ID** [cite: 18].
- Resolved Many-to-Many constraints between `Order Details` and `Sales Target` by utilizing a clean **Category Lookup Dimension (`Category_Dim`)**, establishing active One-to-Many relationships on **Category** [cite: 18].
- Verified all relationships and cross-filter directions via **Manage Relationships** [cite: 18].

---

## Deliverables Checklist
- **Power BI Workbook (`.pbix`)**: Fully structured with queries, transformations, custom columns, merged tables, and relational data model [cite: 19].
- **Documentation / PDF Report**: Includes step-by-step workflow explanations and data model schema views [cite: 19].
