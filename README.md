# 🛒 Blinkit Sales Performance Analysis — Power BI Dashboard

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Excel](https://img.shields.io/badge/Microsoft%20Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)

A comprehensive, interactive Power BI dashboard analyzing Blinkit's (India's last-minute grocery delivery app by Zomato) sales performance, customer satisfaction, and inventory distribution across outlets.

---

## 📊 Dashboard Preview

![Blinkit Dashboard](./sales_performance_analysis/BlinkitData/dashboard_preview.png)

> **Key Highlights:** $1.20M Total Sales · $140.99 Avg Sales · 8,523 Items · 3.92 Avg Rating

---

## 📁 Project Structure

```
blinkit-powerbi-analysis/
│
├── BlinkitGroceryData.xlsx       # Raw dataset (8,523 rows × 12 columns)
├── BlinkitAnalysis.pbix          # Power BI report file
├── assets/                       # Icons and background images used in dashboard
│   ├── sales_icon.png
│   ├── items_icon.png
│   ├── rating_icon.png
│   └── avg_sales_icon.png
└── README.md
```

---

## 🎯 Business Objective

Conduct a comprehensive analysis of Blinkit's:
- **Sales performance** across product types and outlet categories
- **Customer satisfaction** through ratings data
- **Inventory distribution** across outlet sizes, locations, and types

The goal is to surface actionable insights for stakeholders using an interactive, filterable Power BI report.

---

## 📋 Dataset Overview

| Property | Details |
|---|---|
| Source | Excel file (`BlinkitGroceryData.xlsx`) |
| Rows | 8,523 |
| Columns | 12 |

### Columns

| Column | Description |
|---|---|
| `Item Fat Content` | Fat level of the product (Low Fat / Regular) |
| `Item Identifier` | Unique item code |
| `Item Type` | Category (Fruits, Snacks, Dairy, etc.) |
| `Outlet Establishment Year` | Year the outlet was established |
| `Outlet Identifier` | Unique outlet code |
| `Outlet Location Type` | Tier 1 / Tier 2 / Tier 3 city |
| `Outlet Size` | Small / Medium / High |
| `Outlet Type` | Grocery Store / Supermarket Type 1/2/3 |
| `Item Visibility` | How prominently the item appears in-app |
| `Item Weight` | Weight of the item |
| `Sales` | Revenue generated per order |
| `Rating` | Customer rating for the order |

---

## 🧹 Data Cleaning (Power Query)

Cleaning steps performed in Power Query Editor:

- Standardized **Item Fat Content** values:
  - `LF` → `Low Fat`
  - `low fat` → `Low Fat`
  - `reg` / `R` → `Regular`
- Verified **column quality** (Valid %, Error %, Empty %) for all fields
- `Item Weight` contains ~16% null values — retained as-is since it's not used in KPI calculations

---

## 📐 DAX Measures

```dax
Total Sales = SUM('BlinkitGroceryData'[Sales])

Average Sales = AVERAGE('BlinkitGroceryData'[Sales])

Number of Items = COUNTROWS('BlinkitGroceryData')

Average Rating = AVERAGE('BlinkitGroceryData'[Rating])
```

A **Field Parameter** (`Metrics`) was also created to allow dynamic switching between Total Sales, Average Sales, Number of Items, and Average Rating across charts.

---

## 📈 Dashboard Features

### KPI Cards
| KPI | Value |
|---|---|
| Total Sales | $1.20M |
| Average Sales | $140.99 |
| No. of Items | 8,523 |
| Average Rating | 3.92 |

### Charts & Visualizations

| Chart | Type | Insight |
|---|---|---|
| **Fat Content** | Donut Chart | Low Fat (64.6%) vs Regular (35.4%) of total sales |
| **Fat by Outlet** | Clustered Bar Chart | Sales breakdown by fat type across Tier 1/2/3 |
| **Item Type** | Horizontal Bar Chart | Fruits & Vegetables and Snack Foods are top sellers |
| **Outlet Establishment** | Line Chart | 2018 outlets are the highest performing |
| **Outlet Size** | Donut Chart | Medium outlets contribute the most (42.27%) |
| **Outlet Location** | Funnel Chart | Tier 3 leads at $472.13K |
| **Outlet Type** | Matrix Table | Supermarket Type 1 dominates with $787.55K in sales |

### Filters / Slicers
- **Outlet Location** (Tier 1 / Tier 2 / Tier 3)
- **Outlet Size** (Small / Medium / High)
- **Item Type** (multi-select dropdown)
- **Metric Selector** (Total Sales / Avg Sales / No. of Items / Avg Rating)
- **Reset / Clear All Filters** button

### Interactivity
- All chart slices and bars act as **cross-filters** (configured via Edit Interactions)
- Clicking any segment dynamically filters the entire dashboard

---

## 🛠️ Tools & Technologies

- **Power BI Desktop** — Report building and DAX calculations
- **Power Query Editor** — Data cleaning and transformation
- **Microsoft Excel** — Source data
- **DAX** — Custom measures and field parameters

---

## 🚀 How to Run

1. Download `BlinkitGroceryData.xlsx` and `BlinkitAnalysis.pbix`
2. Open `BlinkitAnalysis.pbix` in **Power BI Desktop**
3. If prompted, update the data source path to point to your local copy of the Excel file:
   - Go to **Home → Transform Data → Data Source Settings**
4. Click **Refresh** to load the data
5. Explore the dashboard using the filter panel on the left

---

## 💡 Key Insights

- **Low Fat products** account for ~65% of total sales, indicating strong health-conscious demand
- **Fruits & Vegetables** and **Snack Foods** are the highest-selling item categories
- **Tier 3 outlets** generate the most revenue despite being in smaller cities — likely due to higher outlet count
- **Supermarket Type 1** outlets outperform all other outlet types significantly
- **2018-established outlets** have the highest cumulative sales among all establishment years
- Average customer rating of **3.92/5** signals room for improvement in delivery quality and product satisfaction

---

## 📚 Reference

This project was built by following the tutorial:
**"Blinkit Sales Analysis Power BI Dashboard"** — available on YouTube.

---

## 🙋 Author

Built as a learning project to practice end-to-end Power BI development including data connection, cleaning, DAX, and interactive dashboard design.