# Retail Analytics Data Warehouse & Business Intelligence Solution

A complete Business Intelligence solution developed to transform retail transaction data into actionable insights using **Data Warehousing, SSIS ETL, SSAS OLAP Cube, and Power BI Analytics**.

---

# Project Overview

Organizations generate large volumes of data from different operational systems such as sales, customers, and products. However, analyzing this data becomes difficult when it is stored across multiple sources and formats.

This project implements a complete **Retail Analytics Data Warehouse** solution by integrating heterogeneous data sources, performing ETL operations, designing a dimensional data warehouse, developing an OLAP cube, and creating interactive Power BI reports.

The solution enables business users to analyze:

- Sales performance
- Profitability
- Customer behaviour
- Product performance
- Store performance
- Time-based sales trends

---

# Business Intelligence Workflow

```
Source Systems
      |
      ↓
Staging Area
      |
      ↓
SSIS ETL Process
      |
      ↓
Data Warehouse (Star Schema)
      |
      ↓
SSAS OLAP Cube
      |
      ↓
Power BI Reports
```

---

# Technologies Used

| Technology | Purpose |
|------------|---------|
| Microsoft SQL Server | Source database and Data Warehouse implementation |
| SQL Server Integration Services (SSIS) | ETL development |
| SQL Server Analysis Services (SSAS) | OLAP Cube development |
| Power BI | Dashboard and reporting |
| Excel | External data source |
| CSV Files | External data source |

---

# Dataset

## Dataset Information

**Dataset Name:** Indian Store Data

**Source:**  
https://www.kaggle.com/datasets/abuhumzakhan/store-data

**Records:** Approximately 100,000 retail sales transactions

**Data Period:** Multiple years of sales transactions

The dataset represents a retail business scenario containing:

- Customer information
- Product information
- Sales transactions
- Product categories
- Sales amount
- Quantity
- Discount
- Profit

---

# Source Systems

The dataset was separated into multiple heterogeneous sources to simulate a real-world enterprise environment.

## SQL Server Database

Contains transactional sales data:

**Orders Table**

Includes:

- Order ID
- Customer ID
- Product ID
- Order Date
- Ship Date
- Sales
- Quantity
- Discount
- Profit

---

## CSV Source

### Customer Data

File:

```
customer.csv
```

Contains:

- Customer ID
- Customer Name
- Last Name
- Date of Birth
- Segment

---

## Excel Source

### Product Data

File:

```
product.xlsx
```

Contains:

- Product ID
- Product Name
- Category
- Sub Category

---

# Data Warehouse Design

## Star Schema Architecture

The data warehouse was designed using a star schema model.

![Star Schema](Documentation/star-schema.png)

---

## Fact Table

### FactSales

Contains business measures:

- Sales Amount
- Quantity
- Discount
- Profit

---

## Dimension Tables

### DimCustomer

Stores customer attributes:

- Customer Name
- Last Name
- Segment

---

### DimProduct

Stores product information:

- Product Name
- Category
- Sub Category

---

### DimDate

Stores time-related attributes:

- Date
- Year
- Month
- Day

---

# ETL Development using SSIS

Three main ETL packages were developed.

---

## Package 1: as_Load_Staging.dtsx

Purpose:

Extract raw data from multiple sources and load into staging tables.

Sources:

- SQL Server
- CSV files
- Excel files

Process:

```
Source
 ↓
Data Conversion
 ↓
OLE DB Destination
```

Staging tables:

- StgCustomer
- StgProduct
- StgOrders

---

## Package 2: as_Load_DW.dtsx

Purpose:

Transform staging data and load into warehouse tables.

Transformations applied:

- Data Conversion
- Lookup Transformation
- Conditional Split
- Derived Column
- Surrogate Key Generation

Loaded tables:

- DimCustomer
- DimProduct
- FactSales

---

## Package 3: Update_FactSales.dtsx

Purpose:

Update accumulating fact table information.

Implemented:

- Transaction completion tracking
- Processing time calculation

---

# SSAS OLAP Cube

A multidimensional OLAP cube was created using SQL Server Analysis Services.

The cube contains:

## Measures

- Sales
- Quantity
- Discount
- Profit


## Dimensions

- Customer
- Product
- Date


## Hierarchies

Example:

```
Year
 |
Month
 |
Day
```

---

# OLAP Operations Demonstrated

The cube was tested using Excel PivotTable connected to SSAS.

Implemented operations:

## Roll-up

Aggregates data to a higher level.

Example:

```
Month → Year
```

---

## Drill-down

Explores detailed information.

Example:

```
Year → Month → Day
```

---

## Slice

Filters data using a single dimension.

Example:

```
Customer Segment = Consumer
```

---

## Dice

Filters data using multiple conditions.

Example:

```
Segment = Consumer
+
Category = Electronics
```

---

## Pivot

Changes the perspective of data analysis.

---

# Power BI Reports

Power BI was connected with the SSAS cube to create interactive reports.

Implemented reports:

---

## Matrix Report

Displays:

- Product categories
- Customer segments
- Sales values

---

## Interactive Slicer Report

Includes:

- Cascading filters
- Multiple visuals
- Sales charts

---

## Drill-down Report

Allows users to explore:

```
Year → Month → Day
```

---

## Drill-through Report

Allows users to navigate from summary information to detailed analysis.

Includes:

- Product details
- Sales information
- Profit analysis

---

# Project Outcomes

✔ Designed a complete retail data warehouse using star schema architecture.

✔ Integrated multiple heterogeneous data sources using SSIS.

✔ Developed automated ETL workflows.

✔ Created SSAS OLAP cube for multidimensional analysis.

✔ Implemented OLAP operations including drill-down, roll-up, slice, dice, and pivot.

✔ Developed Power BI reports for business intelligence and decision support.

✔ Gained practical experience in data modelling, ETL, OLAP, and visualization.

---

# Author

**Ishoda Moderage**

BSc (Hons) Information Technology  
Specializing in Data Science  
Sri Lanka Institute of Information Technology (SLIIT)
