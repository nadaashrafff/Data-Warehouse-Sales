# BikeStores Data Warehousing and Analytics Project

## Project Overview

This project is a Data Warehousing and Analytics project based on the **BikeStores** sample database. The project focuses on designing and implementing a complete data warehouse solution to analyze sales performance and support business decision-making.

The project follows the full data warehousing lifecycle, starting from the operational source database, then building a dimensional data warehouse, developing an ETL process, creating an OLAP cube, writing MDX queries, and finally building a Power BI dashboard for business insights.

---

## Project Title

**Data Warehousing Design and Analytics Project**

---

## Business Domain

The project focuses on a fictional bicycle retail company called **BikeStores**.

The main business area analyzed is:

- Sales performance
- Store performance
- Product performance
- Customer geographic analysis
- Staff sales performance
- Brand and category performance

---

## Project Objectives

The main objectives of this project are to:

- Design and implement a data warehouse for BikeStores sales analysis.
- Extract, transform, and load data from the transactional database into the data warehouse.
- Build an OLAP cube for multidimensional analysis.
- Use MDX queries to extract business insights.
- Visualize the final insights using Power BI.
- Support strategic business decision-making through dashboards and reports.

---

## Source Database

The project uses the **BikeStores Sample Database** as the source operational database.

The source database includes two main areas:

- Sales
- Production

### Main Source Tables

- Orders
- Order Items
- Products
- Categories
- Brands
- Customers
- Staff
- Stores

---

## Data Warehouse Design

The data warehouse is designed using dimensional modeling concepts.

### 4-Step Data Warehouse Design

| Step | Description |
|---|---|
| Subject | BikeStores Retail Sales |
| Grain | One row per product sold in a transaction per day per customer per staff per store |
| Dimensions | Product, Customer, Store, Staff, Date, Category, Brand |
| Measures | Sales Amount, Quantity Sold, Gross Amount, Discount |

---

## Grain

The grain of the fact table is:

> One row per product sold in a transaction, on a specific day, by a specific staff member, to a specific customer, in a specific store.

This means each row in the fact table represents a detailed sales transaction at the product level.

---

## Data Warehouse Schema

The project uses a star schema with some snowflake structure for product-related dimensions.

### Fact Table

- `Sales_Fact`

### Dimension Tables

- `Product_Dimension`
- `Category_Dimension`
- `Brand_Dimension`
- `Customer_Dimension`
- `Store_Dimension`
- `Staff_Dimension`
- `Date_Dimension`

### Measures in the Fact Table

- Quantity Sold
- Sales Amount
- Gross Amount
- Discount

---

## Snowflake Design

The **Category** and **Brand** dimensions are snowflaked from the Product Dimension.

This design helps reduce redundancy because category and brand values are repeated across many products.

---

## Date Dimension Role Playing

The Date Dimension is implemented using a role-playing design.

The project uses one physical Date Dimension and creates three role-playing views:

- Order Date
- Required Date
- Shipped Date

Each date role appears in the fact table as a separate foreign key:

- `order_date_key`
- `required_date_key`
- `shipped_date_key`

This allows analysis based on different date perspectives.

---

## Methodology

The project follows a structured data warehousing methodology:

1. Design the data warehouse schema using SQL DDL.
2. Build ETL pipelines using SQL Server Integration Services.
3. Load dimensions and fact tables into the data warehouse.
4. Develop an OLAP cube using SQL Server Analysis Services.
5. Write MDX queries for business analysis.
6. Build Power BI dashboards for visual analytics.

---

## Tools and Technologies Used

- SQL Server
- SQL Server Management Studio
- Visual Studio 2019
- SQL Server Integration Services
- SQL Server Analysis Services
- MDX
- Power BI
- Data Warehouse Design
- Dimensional Modeling
- Star Schema
- Snowflake Schema
- OLAP Cube

---

## ETL Process

The ETL process was implemented using **SQL Server Integration Services (SSIS)**.

The ETL process extracts data from the BikeStores operational database and loads it into the BikeStores data warehouse.

### ETL Packages

The ETL process includes loading:

- Product Dimension
- Category Dimension
- Brand Dimension
- Customer Dimension
- Store Dimension
- Staff Dimension
- Date Dimension
- Sales Fact Table

### ETL Features

- Source-to-destination data flow
- Derived column transformations
- Lookup transformations
- Foreign key mapping
- Fact table loading
- Dimension loading
- Role-playing date mapping
- ETL validation and verification

---

## OLAP Cube

The OLAP cube was developed using **SQL Server Analysis Services (SSAS)**.

The cube enables fast multidimensional analysis of BikeStores sales data.

### Cube Features

- Sales measures
- Product analysis
- Store analysis
- Staff analysis
- Customer analysis
- Date hierarchy
- Brand and category analysis
- Drill-down and roll-up capabilities
- MDX query support
- Power BI live connection support

---

## Date Hierarchy

The Date Dimension includes a hierarchy that supports drill-down analysis:

```text
Year → Month → Day
```

This helps analyze sales trends at different time levels.

---

## MDX Query Analysis

MDX queries were used to extract insights from the OLAP cube.

### Business Questions Answered

- What are the monthly sales trends?
- What are the yearly sales trends?
- Which products sold the most?
- Which categories generated the highest revenue?
- Which brands generated the highest sales?
- Which stores generated the highest revenue?
- Which salespersons generated the highest revenue?
- Which customer states contributed the most sales?
- What are the top products per brand?

---

## Power BI Dashboard

Power BI was used to visualize the final insights from the OLAP cube.

The dashboard includes charts and KPIs for:

- Total Sales Amount
- Total Gross Amount
- Quantity Sold
- Sales Amount by Year and Month
- Sales Amount by Category
- Quantity Sold by Brand
- Quantity Sold by Product
- Sales Amount by Store
- Sales Amount by Year and Store
- Quantity Sold by State
- Sales Amount by Salesperson

---

## Dashboard KPIs

The final Power BI dashboard shows the following key indicators:

| KPI | Value |
|---|---|
| Sales Amount | 7.69M |
| Gross Amount | 8.58M |
| Quantity Sold | 7078 |

---

## Main Insights

### Sales Trends

Sales were generally consistent until a significant peak around April 2018, followed by a sharp drop.

### Top Product Categories

The highest revenue-generating categories are:

1. Mountain Bikes
2. Road Bikes
3. Cruisers Bicycles

### Top Brands

The highest-selling brands are:

1. Electra
2. Trek
3. Surly

### Top Products

Top-selling products include:

- Electra Cruiser 1 (24-Inch) - 2016
- Electra Townie Original 7D EQ - 2016
- Electra Townie Original 21D - 2016

### Store Performance

Baldwin Bikes generated the highest sales amount, contributing around 67.83% of total sales.

### State Performance

NY contributed the highest quantity sold, followed by CA and TX.

### Salesperson Performance

Top-performing salespersons include:

- Marcelene Boyer
- Venita Daniel

---

## Repository Contents

```text
BikeStore_OLAP_Cube.sln
BikeStores_ETLProcess.sln
Dashboard_BikeStores.pdf
Data warehouse PPT.pptx
Technical Report Data warehousing Project.docx
```

---

## File Descriptions

### `BikeStore_OLAP_Cube.sln`

Visual Studio solution file for the OLAP cube project developed using SQL Server Analysis Services.

### `BikeStores_ETLProcess.sln`

Visual Studio solution file for the ETL process developed using SQL Server Integration Services.

### `Dashboard_BikeStores.pdf`

Final Power BI dashboard export showing BikeStores sales analysis visuals and KPIs.

### `Data warehouse PPT.pptx`

Presentation slides explaining the project overview, data warehouse design, ETL process, OLAP cube, MDX queries, Power BI visualizations, and final insights.

### `Technical Report Data warehousing Project.docx`

Full technical report documenting the project, including the source database, data warehouse schema, ETL process, OLAP cube development, MDX queries, Power BI dashboard, and insights.

---

## How to Use This Project

### 1. Open the ETL Project

Open the following solution in Visual Studio:

```text
BikeStores_ETLProcess.sln
```

Use this project to review or run the SSIS ETL packages.

---

### 2. Open the OLAP Cube Project

Open the following solution in Visual Studio:

```text
BikeStore_OLAP_Cube.sln
```

Use this project to review, deploy, and process the SSAS OLAP cube.

---

### 3. Review the Dashboard

Open the dashboard file:

```text
Dashboard_BikeStores.pdf
```

This file contains the final Power BI dashboard with visual insights.

---

### 4. Review the Documentation

Open the technical report:

```text
Technical Report Data warehousing Project.docx
```

This file contains the full explanation of the project implementation and analysis.

---

## Project Workflow

The project follows this workflow:

```text
BikeStores Source Database
        ↓
Data Warehouse Schema Design
        ↓
SSIS ETL Process
        ↓
BikeStores Data Warehouse
        ↓
SSAS OLAP Cube
        ↓
MDX Queries
        ↓
Power BI Dashboard
        ↓
Business Insights
```

---

## Key Learning Outcomes

This project demonstrates practical knowledge of:

- Data warehouse design
- Dimensional modeling
- Star schema design
- Snowflake schema design
- ETL development using SSIS
- OLAP cube development using SSAS
- MDX querying
- Power BI dashboard creation
- Business intelligence reporting
- Sales analytics and decision support

---

## Business Value

The project helps business users and managers:

- Identify top-performing stores.
- Understand seasonal sales trends.
- Evaluate product category performance.
- Track top-selling products and brands.
- Analyze customer geographic behavior.
- Identify high-performing sales staff.
- Make better strategic decisions based on historical sales data.

---

## Conclusion

This project successfully implements a complete data warehousing and analytics solution for the BikeStores retail sales database.

The solution transforms transactional data into meaningful business insights through a structured data warehouse, ETL pipelines, OLAP cube analysis, MDX queries, and Power BI visualizations.

By using this system, decision-makers can better understand sales performance, identify growth opportunities, and make data-driven strategic decisions.

---

## Team Members

- Nada Ashraf
- Aly Zaki
- Ahmed Waleed
- Omar Bayoumi

---

## Course Information

**University:** Egypt University of Informatics  
**Faculty:** Computer and Information Systems  
**Course:** Big Data Engineering  
**Project:** Data Warehousing Design and Analytics  
**Submission Date:** 19 April 2025
