# 🛒 Calwest E-Commerce Tableau Dashboard  
**Business Intelligence Case Study | BIDA® Certified**  

![Tableau](https://img.shields.io/badge/Tableau-Public-<COLOR>.svg?logo=tableau)
![SQL](https://img.shields.io/badge/SQL-Data_Modeling-blue)
![Dashboarding](https://img.shields.io/badge/Tableau-Interactive_Dashboards-orange)

---

## 🌟 **Project Overview**  
This Tableau dashboarding project analyzes **health-conscious product sales** for Calwest E-Commerce, focusing on **human and pet products**. It provides actionable insights through two interactive dashboards:  
1. **High-Level E-Commerce Performance**  
2. **Regional Performance Summary**  

Built with **Tableau relationships**, **LOD calculations**, and **dynamic interactivity**, the dashboards empower stakeholders to track revenue trends, promotions, geographic performance, and product profitability.

**Live Dashboard**: [Explore on Tableau Public](https://public.tableau.com/shared/DPYFXZNXP?:display_count=n&:origin=viz_share_link)  


---

## 🎯 **Objectives**  
1. Model a star schema using **7 CSV files** and Tableau relationships.  
2. Visualize KPIs like **Gross Revenue ($81.27M)**, **Profit Margin (54.35%)**, and **Order Count (184,375)**.  
3. Enable dynamic filtering by date, region, and product categories.  
4. Implement cross-dashboard interactivity (e.g., map selections filter other visuals).  

---

## 📂 Data Model & ERD

📍 **ERD Diagram**  
--- <img src="https://github.com/user-attachments/assets/80897ef8-166f-440d-826b-6c8da1dde349" width = "450"> 

📍 **Relationship Diagram**  
--- <img src="https://github.com/user-attachments/assets/4c7db6c5-05fc-4ba4-b184-f44f5081e535" width = "450">

📍 **CSV Files Overview**  
--- <img src="https://github.com/user-attachments/assets/8a1a6778-55a8-4979-ad82-639505f3c9e9" width = "450">

**Fact Table**:  
- `FactOrders` : Connects to all dimensions via foreign keys (`CustomerId`, `ProductId`, etc.).  

**Dimension Tables**:  
- `dimCustomer`, `dimProduct`, `dimPromo`, `dimShipping`, `dimLocation`, `dimPayment`  

**Key Relationships**:  
- **All dimensions ↔ FactOrders**: Many-to-one (fact-to-dimension) with **referential integrity** (all records match).  
- **Exception**: `dimPromo` uses **"Some records match"** due to nullable promo IDs.  

---

## 📊 **Dashboard 1: E-Commerce Performance**  
### **Preview**  
<img src="https://github.com/user-attachments/assets/89200daf-65dd-4b51-b521-d17c8332704e"> 
### ✅ KPIs Included

- **SUM of Gross Revenue**
- **SUM of Profit**
- **Profit Margin % (Aggregated & Row-level)**
- **SUM of Discount**
- **SUM of Quantity** / **SUM of Units**
- **DISTINCT COUNT of Order ID & Customers**
- **AVERAGE Order Value**

### 📊 Visuals

- 🔹 **BANS** (Big Ass Numbers – KPI summary excluding Customer Count and Row-level margin)
- 📈 **Line Chart** – Gross Revenue over Order Month (one line per Category)
- 📊 **Bar Chart** – Gross Revenue by Category > Sub-Category (colors matched)
- ⚪ **Scatter Plot** – Product-level Gross Revenue vs Profit Margin %
  
### 🧩 Dashboard Interactivity

- A **parameter** allows the user to toggle between “Gross Revenue” and “Profit”.
- The **line** and **bar charts** dynamically adjust based on parameter selection.
  
---

## 🌍 Dashboard 2 – Regional Performance Summary
### **Preview**  
<img src="https://github.com/user-attachments/assets/00dba506-f9ee-4f9e-8449-5fcc77bb0383">

### 📌 Visuals

- 🗺️ **Map** – Gross Revenue by U.S. state with Region overlay
- 📊 **Bar Chart** – Monthly % of revenue from Promo vs Non-Promo
- 🌳 **Tree Map** – Category > Subcategory showing Gross Revenue and Profit Margin %
- 🍭 **Lollipop Chart** – Top 10 products by Gross Revenue

### 🧩 Dashboard Interactivity

- A **map click action** filters other visuals by selected U.S. state.
- A **floating container** allows toggling of the **Top 10 Products Lollipop chart**.

---

## 📐 Key Calculated Fields

| Metric                         | Formula                                                                 |
|-------------------------------|-------------------------------------------------------------------------|
| **Profit**                    | `SUM([Revenue]) - SUM([Cost])`                                          |
| **Profit Margin %**           | `[Profit] / [Gross Revenue]`                                            |
| **Profit Margin % (Row-level)** | `([Revenue] - [Cost]) / [Revenue]`                                     |
| **Discount**                  | `SUM([Base Revenue]) - [Gross Revenue]`                                 |
| **Order Value Avg**           | `[Gross Revenue] / [Order Count]`                                       |
| **Is Promo**                  | `IF NOT ISNULL([Promo Code]) THEN 'Promo' ELSE 'Non Promo' END`        |

---

## 💡 Insights You Can Derive

- 💰 Identify best-selling products by revenue and margin
- 📍 Discover revenue-heavy U.S. states and regions
- 🧪 Measure effectiveness of promotions by time and region
- 🧬 Uncover product-level profitability anomalies via scatter analysis

---

## 🙌 Acknowledgements
Thanks to Corporate Finance Institute® (CFI) for designing this comprehensive case study as part of the BIDA – Business Intelligence & Data Analysis course.
