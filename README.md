# 📊 Power BI Sales Performance Dashboard

## 🧾 Project Overview

This project focuses on designing a **Sales Performance Dashboard** using **Power BI** to analyze and visualize sales data across multiple years, states, and product categories.

The goal is to transform raw data into meaningful insights that enable better decision-making, improve sales tracking, and measure business performance through KPIs like **Total Sales, YoY Growth %, QTD, YTD, and MTD**.

---

## 💡 Objectives

* To analyze sales data and uncover trends across years and regions
* To monitor key performance metrics (KPIs) like Total Sales, Orders, and YoY Growth
* To create an interactive, dynamic Power BI dashboard for business insights
* To practice end-to-end data cleaning, modeling, and visualization workflow

---

## 🧹 Data Cleaning & Preparation

The dataset contained raw transactional-level data with inconsistencies in **date formats, missing values, and duplicate entries**.
The following steps were performed to clean and prepare the data before visualization:

### **1️⃣ Data Import**

* Imported raw CSV/Excel file into Power BI using the **Power Query Editor**.
* Previewed column data types (e.g., date, text, numbers) for correctness.

### **2️⃣ Removed Duplicates & Blanks**

* Removed duplicate rows using *Remove Duplicates* in Power Query.
* Replaced or removed blank/NA values in key columns (like State, Product, and Amount).

### **3️⃣ Date Standardization**

* The dataset had inconsistent date formats (`mm/dd/yyyy`, `dd-mm-yyyy`).
* Used Power Query transformations:

  ```m
  = Table.TransformColumnTypes(#"PreviousStep",{{"OrderDate", type date}})
  ```
* Converted all dates into **standard date format (dd-mmm-yyyy)** for time intelligence functions.

### **4️⃣ Created a Date Table**

* Built a custom date table using DAX:

  ```DAX
  Date = CALENDAR(MIN(Sales[OrderDate]), MAX(Sales[OrderDate]))
  ```
* Added columns for **Year, Quarter, Month, Month Name**, etc., to enable YTD, QTD, and MTD calculations.

### **5️⃣ Data Type Corrections**

* Ensured numeric columns (like Sales Amount and Order Count) were in *Decimal Number* format.
* Verified categorical columns (State, Product, Deal Size) were in *Text* format.

---

## 🧮 DAX Measures Used

| Measure                 | Formula                                                      | Description                      |
| ----------------------- | ------------------------------------------------------------ | -------------------------------- |
| **Total Sales**         | `SUM(Sales[SalesAmount])`                                    | Calculates total sales revenue   |
| **Total Orders**        | `COUNT(Sales[OrderID])`                                      | Counts total orders placed       |
| **Total Sales LY**      | `CALCULATE([Total Sales], SAMEPERIODLASTYEAR('Date'[Date]))` | Sales from the previous year     |
| **YoY Growth %**        | `DIVIDE([Total Sales] - [Total Sales LY], [Total Sales LY])` | Year-over-Year growth percentage |
| **Total Sales YTD**     | `TOTALYTD([Total Sales], 'Date'[Date])`                      | Year-to-Date sales               |
| **Total Sales QTD**     | `TOTALQTD([Total Sales], 'Date'[Date])`                      | Quarter-to-Date sales            |
| **Total Sales MTD**     | `TOTALMTD([Total Sales], 'Date'[Date])`                      | Month-to-Date sales              |
| **Avg Sales per Order** | `DIVIDE([Total Sales], [Total Orders])`                      | Average revenue per order        |

---

## 📈 Dashboard Features

* KPI cards for **Total Orders, Total Sales, States Covered, Product Count, YoY Growth %, and Avg Sales/Order**
* **Interactive slicers** for filtering by *Year, Quarter, and Deal Size*
* **Dynamic KPI comparison** using DAX (Current Year vs. Last Year)
* Visuals include:

  * Line and Area charts for trend analysis
  * Pie chart for deal size distribution
  * Table for monthly breakdown (MTD, QTD, YTD, YoY)
  * KPI visual comparing current vs last year’s sales

---

## 🎨 Design Highlights

* Consistent color palette with beige background for clarity
* Clean layout — balanced between KPIs, charts, and tables
* Minimal borders and grid alignment for professional look
* Used icons and KPI indicators for visual storytelling

---

## 📂 Folder Structure

```
📁 PowerBI-Sales-Dashboard
│
├── 📊 Sales_Dashboard.pbix           # Power BI project file
├── 📘 README.md                      # Project documentation
├── 📈 Sales_Dashboard_Screenshot.png # Dashboard preview
└── 📂 Data
    └── sales_data.csv                # Raw dataset (if allowed)
```

---

## 💻 Tools & Technologies Used

* **Power BI Desktop**
* **Power Query**
* **DAX (Data Analysis Expressions)**
* **Excel (for initial data check)**

---

## 🧠 Insights Gained

* Identified a **21.5% YoY growth** in total sales.
* Detected **seasonal trends** with peaks during mid-year months.
* Average sales per order stood at **₹4.59K**, helping measure efficiency.
* Top-performing years showed strong performance across 17 states and 60 products.

---

## 📤 How to Use

1. Download the `.pbix` file from this repository.
2. Open it using **Power BI Desktop**.
3. Interact with slicers and visuals to explore insights.

---

## 📸 Dashboard Preview

*(Add your image here)*
![Sales Dashboard Preview](./Sales_Dashboard_Screenshot.png)

---

## 🤝 Connect with Me

**Aniket Kumar**
📍 Gurugram, Haryana, India
📧 [aniketkumarsingh8743@gmail.com](mailto:aniketkumarsingh8743@gmail.com)
🔗 [LinkedIn](https://linkedin.com/in/aniket-kumar)
🔗 [GitHub](https://github.com/yourusername)


