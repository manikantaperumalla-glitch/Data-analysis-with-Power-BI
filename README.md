# 📊 E-Commerce Sales Analysis – Power BI

![Power BI](https://img.shields.io/badge/Power%20BI-Data%20Analytics-yellow)
![DAX](https://img.shields.io/badge/DAX-Data%20Analysis-blue)
![Data Visualization](https://img.shields.io/badge/Data%20Visualization-Power%20BI-orange)
![Project Type](https://img.shields.io/badge/Project-E--Commerce%20Analytics-green)

## 📌 Project Overview

**E-Commerce Sales Analysis** is a Power BI data analytics project focused on analyzing e-commerce sales data to understand **sales trends, profitability, order performance, sales targets, product performance, and geographic sales patterns**.

The project uses **DAX (Data Analysis Expressions)** to create calculated columns and measures, followed by interactive Power BI visualizations to communicate key business metrics and performance indicators.

The project follows the required analytical workflow:

**Data → Data Modeling → DAX Calculations → Visualization → Analysis → Business Insights**

The source assignment specifically requires data modeling to be completed before visualization, including establishing relationships between the required tables and creating the calculations needed for analysis.

---

# 🎯 Business Problem

E-commerce businesses generate large volumes of transactional data across orders, products, categories, locations, and sales targets.

However, raw transactional data alone does not provide management with an easy way to understand:

* Actual sales performance
* Sales target achievement
* Profitability
* Product and sub-category performance
* Monthly sales trends
* Order volumes
* Geographic sales patterns
* Quantity versus profit relationships

This project uses Power BI and DAX to transform e-commerce data into an interactive analytical solution that helps users evaluate sales and performance metrics.

---

# 🎯 Business Objectives

The key objectives of this project are:

1. Analyze e-commerce sales performance.
2. Compare actual sales against sales targets.
3. Measure order volume and sales performance.
4. Analyze profitability by product sub-category.
5. Identify monthly sales trends.
6. Compare profit and quantity sold.
7. Analyze sales performance by category and month.
8. Identify geographic sales patterns.
9. Understand sales distribution across sub-categories.
10. Analyze order counts across different states.
11. Create reusable DAX calculations for business analysis.
12. Build interactive Power BI visualizations for decision-making.

---

# 📂 Dataset Information

The project uses three source datasets:

### 1. List of Orders

Contains order-level information used to analyze orders and geographic/order-related performance.

### 2. Order Details

Contains detailed sales information used for:

* Category
* Sub-Category
* Amount
* Quantity
* Profit
* Profit Margin
* Sales analysis

### 3. Sales Target

Contains sales target information used to compare target performance against actual sales.

The assignment identifies these three files as the source data for the project.

# 🧮 DAX – Calculated Columns

The project includes three major calculated columns.

## 1. Category Type

A calculated column named **Category Type** combines the `Category` and `Sub-Category` fields into a single analytical field.

### Purpose

This provides a combined product classification that can be used for filtering and analysis.

```DAX
Category Type =
'Order Details'[Category] & " - " & 'Order Details'[Sub-Category]
```

---

## 2. Revenue per Order

A calculated column is created to calculate revenue per order using:

**Amount × Quantity**

```DAX
Revenue per Order =
'Order Details'[Amount] * 'Order Details'[Quantity]
```

### Purpose

This provides an order-level revenue calculation for further analysis.

---

## 3. Sales Category

A calculated column named **Sales Category** categorizes sales as:

* Above Average
* Below Average

based on the `Amount` value.

Example implementation:

```DAX
Sales Category =
IF(
    'Order Details'[Amount] >=
    AVERAGE('Order Details'[Amount]),
    "Above Average",
    "Below Average"
)
```

The assignment specifically requires the Sales Category classification to be based on the Amount value.

---

# 📐 DAX – Calculated Measures

## 1. Order Count

Measures the total number of orders in the Order Details table.

```DAX
Order Count =
COUNTROWS('Order Details')
```

### Business Purpose

Helps monitor overall order volume.

---

## 2. Average Profit in Delhi

Calculates the average profit for orders placed in Delhi.

```DAX
Average Profit in Delhi =
CALCULATE(
    AVERAGE('Order Details'[Profit]),
    'List of Orders'[City] = "Delhi"
)
```

### Business Purpose

Helps evaluate profitability for the Delhi market.

---

## 3. Year-to-Date Sales

Calculates cumulative sales from the beginning of the available period through the current order date.

```DAX
YTD Sales =
TOTALYTD(
    SUM('Order Details'[Amount]),
    'List of Orders'[Order Date]
)
```

### Business Purpose

Helps monitor cumulative sales performance throughout the year.

The assignment specifically requires an Order Count measure, an average-profit measure for Delhi, and a YTD Sales measure.

---

# 📊 Data Visualization

The dashboard uses multiple visualization types to answer different business questions.

---

## 📈 1. Sales Target Achievement by Category

**Visualization:** Clustered Column Chart

### Purpose

Compares:

* Actual Sales
* Sales Target

across different categories.

### Business Question

> Which categories are achieving or falling short of their sales targets?

---

# 🍩 2. Maximum Profit Margin by Sub-Category

**Visualization:** Donut Chart

### Purpose

Analyzes the maximum profit margin across product sub-categories.

### Business Question

> Which sub-categories demonstrate the highest profit margins?

---

# 📅 3. Monthly Sales Trend

**Visualization:** Line Chart

### Purpose

Displays monthly sales performance over time.

### Business Question

> How are sales changing from month to month?

This visualization helps identify sales trends and changes over time.

---

# 🔵 4. Profit vs Quantity by Sub-Category

**Visualization:** Scatter Chart

### Purpose

Compares:

* Profit
* Quantity Sold

across different sub-categories.

### Business Question

> Is there a relationship between quantity sold and profit across sub-categories?

---

# 🎯 5. Total Sales Amount vs Sales Target

**Visualization:** Cards

The dashboard uses cards to display:

* Total Sales Amount
* Sales Target

A **multi-row card** is also used to display the minimum target for each segment.

### Business Question

> How does actual sales performance compare with the overall target?

---

# 📋 6. Sales Performance Matrix

**Visualization:** Matrix

### Purpose

Analyzes actual sales against sales targets across:

* Categories
* Months

### Business Question

> How does sales performance change across categories and months?

---

# 🗺️ 7. Geographic Sales Analysis

**Visualization:** Map

### Purpose

Displays total sales by city.

### Business Question

> Which geographic locations contribute the most to total sales?

This visualization helps identify regional sales patterns.

---

# 🌳 8. Sales Distribution by Sub-Category

**Visualization:** Treemap

### Purpose

Shows the distribution of sales across product sub-categories.

### Business Question

> Which sub-categories contribute the largest share of sales?

---

# 🔻 9. Order Count Analysis by State

**Visualization:** Funnel Chart

### Purpose

Visualizes order counts across different states.

### Business Question

> How are order volumes distributed across states?



# 🔍 Key Business Questions

This project answers important e-commerce business questions such as:

1. What is the total sales amount?
2. What is the total sales target?
3. How many orders were placed?
4. Which categories generate the highest sales?
5. Which categories meet their sales targets?
6. Which categories fall below their targets?
7. Which sub-categories have the highest profit margins?
8. How do sales change month over month?
9. What is the relationship between profit and quantity?
10. Which cities generate the highest sales?
11. Which sub-categories contribute most to sales?
12. Which states have the highest order counts?
13. What is the average profit generated in Delhi?
14. How does sales performance vary by category and month?
15. What is the cumulative YTD sales performance?

---

# 💡 Key Insights

The dashboard is designed to identify insights related to:

### Sales Performance

* Actual sales versus target
* Category-level performance
* Monthly sales movement
* YTD sales progression

### Profitability

* Profit by sub-category
* Maximum profit margin
* Average profit in Delhi
* Relationship between quantity and profit

### Product Performance

* Sales distribution by sub-category
* Category Type performance
* Above-Average versus Below-Average sales

### Geographic Performance

* City-level sales
* State-level order counts
* Regional sales patterns

> **Important:** The uploaded assignment specifies the analyses and visualizations to be created, but it does not provide the final numerical results. Therefore, specific values and findings should be added to this section after the Power BI dashboard is completed.

---

# 💼 Business Recommendations

After completing the analysis, management can use the dashboard to:

1. Focus on categories that consistently underperform against targets.
2. Identify high-profit sub-categories for strategic focus.
3. Monitor monthly sales trends to identify performance changes.
4. Investigate locations with strong or weak sales performance.
5. Evaluate the relationship between quantity sold and profitability.
6. Monitor cumulative YTD sales performance.
7. Use sales-target comparisons to improve category-level planning.
8. Analyze state-level order volumes to support regional strategies.

These recommendations should be finalized based on the actual numerical findings from the completed Power BI report.

---

# 📈 Business Impact

This Power BI project can help an e-commerce organization:

* Improve sales performance monitoring.
* Track target achievement.
* Identify profitable product segments.
* Understand sales trends.
* Compare regional performance.
* Monitor order volumes.
* Support data-driven business decisions.
* Improve visibility into sales and profitability metrics.

---

# 🛠️ Tools & Technologies

| Tool / Technology    | Purpose                         |
| -------------------- | ------------------------------- |
| **Power BI**         | Dashboard and visualization     |
| **DAX**              | Calculated columns and measures |
| **Power Query**      | Data preparation                |
| **CSV**              | Source datasets                 |
| **Data Modeling**    | Table relationships             |
| **Charts & Visuals** | Business analysis               |

---

# 🧠 Skills Demonstrated

### Technical Skills

* Power BI
* DAX
* Data Modeling
* Data Visualization
* Data Analysis
* Calculated Columns
* Calculated Measures
* KPI Development
* Dashboard Design

### Analytical Skills

* Business Problem Solving
* Sales Analysis
* Profitability Analysis
* Target Analysis
* Trend Analysis
* Geographic Analysis
* Product Performance Analysis
* Business Insight Generation

---

# 📁 Project Structure

```text
E-Commerce-Sales-Analysis/
│
├── Dataset/
│   ├── List of Orders.csv
│   ├── Order Details.csv
│   └── Sales target.csv
│
├── PowerBI/
│   └── E-Commerce Sales Analysis.pbix
│
├── Screenshots/
│   └── Dashboard.png
│
├── Documentation/
│   └── Project Report.pdf
│
└── README.md
```

---

# 📷 Dashboard Preview

Add your final Power BI dashboard screenshot here:https://drive.google.com/file/d/1Ai0bSbttMSCzn-CzR-R6OoC-qxsb5NpN/view?usp=sharing

```markdown
![E-Commerce Sales Dashboard](Screenshots/Dashboard.png)
```

---

# 🚀 Future Scope

The project can be further enhanced by adding:

* Advanced time-intelligence analysis.
* Sales growth percentage.
* Year-over-Year sales comparison.
* Target achievement percentage.
* Profit margin KPIs.
* Dynamic ranking of products.
* Advanced drill-through pages.
* Additional interactive slicers.
* Customer-level analysis.
* Automated Power BI data refresh.
* Predictive sales analysis.
* Advanced geographic analysis.

---

# ⚠️ Limitations

* The analysis depends on the quality and completeness of the source CSV files.
* The project scope is limited to the fields available in the provided datasets.
* The assignment does not provide final numerical findings.
* Specific business recommendations should be validated against actual dashboard results.
* The project focuses primarily on descriptive and diagnostic analysis.

---

# 🎓 Project Learning Outcome

Through this project, I developed practical experience in building an end-to-end Power BI analytics solution.

The project strengthened my understanding of:

**Data Modeling → DAX → KPI Development → Visualization → Business Analysis → Dashboard Storytelling**

It demonstrates how Power BI can transform raw e-commerce transaction data into an interactive business intelligence solution.

---

# 👨‍💻 Author

## Manikanta

**Aspiring Data Analyst | Power BI | SQL | Excel | Python**

I am developing my career in **Data Analytics and Business Intelligence**, with a focus on transforming raw data into meaningful insights and interactive dashboards.

### Core Skills

* Microsoft Excel
* SQL
* Power BI
* DAX
* Python
* Data Visualization
* Data Cleaning
* Data Analysis
* Business Intelligence

---

# 📌 Final Project Statement

> **E-Commerce Sales Analysis** is a Power BI project that demonstrates the complete process of transforming e-commerce data into actionable business intelligence using data modeling, DAX calculations, and interactive visualizations.

The project provides a structured approach to analyzing **sales, targets, profitability, products, trends, orders, and geographic performance**, enabling stakeholders to better understand business performance and make data-driven decisions.



🔗 LinkedIn: www.linkedin.com/in/manikantaa1999


📧 Email : manikantaperumalla143@gmail.com
