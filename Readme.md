# Adventure Works Power BI Data Analysis Project  
**By Shubham Pawar**

---

## 📌 Project Overview
This guided Power BI project analyzes sales and order data for **AdventureWorks**, a global retail company.  
The dashboard provides actionable insights into **revenue trends, order performance, and product categories**, showcasing my ability to design interactive dashboards and highlight key business drivers.  

---

## 📋 Project Link (PowerBi File (pbix)):
[Adventure Works Power BI Project](https://github.com/mjshubham21/AdventureWorks_PowerBi_Project/blob/main/GuidedProjectAdventureWorksDA.pbix)

## 📊 Key Insights (Based on Narrative)

- **Revenue Growth**
  - Revenue increased by **212.14%** between **January 2020 and June 2022**.  
  - Revenue started trending up in **August 2021**, rising by **127.18% ($1,022,793.75)** within **10 months**.  
  - The steepest incline was from **$804,193.39 to $1,826,987.14** between **August 2021 and June 2022**.  

- **Category-wise Orders**
  - **Accessories** had the highest total orders (**16,983**), **143.45% higher** than **Clothing** (**6,976**).  
  - **Bikes** ranked second with **13,929 total orders**.  
  - Order distribution: **Accessories (16,983) > Bikes (13,929) > Clothing (6,976)**.  

---

## 🛠️ Skills and Tools Demonstrated

### 🔹 Data Preparation & Cleaning (Power Query)
In Power BI Power Query:  
1. **Appended Sales Tables**  
   - Combined sales data from **2020, 2021, and 2022** into a single fact table called **SALES_FINAL**.  
2. **Product & Customer Tables**  
   - Cleaned data and added **conditional columns** such as:  
     - `isParent` (flag for parent products)  
     - `incomeLevel` (based on customer income brackets)  
     - `ageGroup` (derived from customer birthdate)  
   - Fixed incorrect **data types** across columns.  
3. **Calendar Table**  
   - Derived **Month Name, Day Name, and Quarter** from the Date column for time intelligence.  

---

### 🔹 Data Modeling
- Built a **star schema** with **SALES_FINAL** as the central fact table, connected to dimension tables like Product Lookup, Customer Lookup, Territory, Calendar, and Categories.  
- Ensured proper **one-to-many (1:* ) relationships** between fact and dimension tables.  
- Created a **Measure Table** to store KPIs and calculated measures.  

📸 **Data Model Screenshot:**  
![Data Model](https://raw.githubusercontent.com/mjshubham21/AdventureWorks_PowerBi_Project/main/images/Schema.png)  

---

### 🔹 DAX (Data Analysis Expressions)  
Defined key business measures using DAX:  

```
DAX
Revenue = SUMX(
    SALES_FINAL,
    SALES_FINAL[OrderQuantity] * RELATED('Product Lookup'[ProductPrice])
)

TotalCost = SUMX(
    SALES_FINAL,
    SALES_FINAL[OrderQuantity] * RELATED('Product Lookup'[ProductCost])
)

ProfitMargin = [Revenue] - [TotalCost]
```
- **Data Visualization**: Interactive charts, KPIs, slicers, drill-throughs.  
- **Business Intelligence Reporting**: Revenue tracking, order distribution, trend analysis.  

---

**Functions Used in Measures**:

- **SUMX** → For row-by-row calculations of Revenue and Cost.  
- **RELATED** → To fetch product details like price and cost from dimension tables.  
- **COUNTROWS** → To calculate total number of orders.  
- **DIVIDE** → For safe division while avoiding divide-by-zero errors.  
- **IF** (used in conditional KPIs) → For logic-based calculations (e.g., flagging performance trends).  

---

### 🔹 Row-Level Security (RLS)

To ensure **restricted access**, I implemented **Row-Level Security** in Power BI based on **regional managers**:

- Created **3 roles**:  
  - Europe Manager  
  - North America Manager  
  - Pacific Manager  

- Each role is restricted to view **only their own region’s data**.  

- Managers cannot access:  
  - Data/visuals from other regions.  
  - The underlying **data tables** or **model view** of unrelated regions.  
  - **Power BI Security** provides **fine-grained control** over **data access** and **dashboard permissions**.
 ---

## 🎯 Key Learnings
- How to structure a BI dashboard to tell a **data story**.  
- Techniques for highlighting **growth trends and product performance**.  
- Effective use of Power BI visuals to support **decision-making**.
- Hands-on experience with data modeling and DAX calculations.
- How to create interactive dashboards and drill-throughs.

---

## 📸 Screenshots

![Dashboard](https://raw.githubusercontent.com/mjshubham21/AdventureWorks_PowerBi_Project/main/images/Dashboard.png)  
![Map](https://raw.githubusercontent.com/mjshubham21/AdventureWorks_PowerBi_Project/main/images/map.png)   

