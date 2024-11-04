## LITA_CAPSTONE_PROJECT_1

INCUBATOR HUB: This repository contains a comprehensive sales data analysis project. Using Excel, SQL, &amp; PowerBI for analysis, report & visualization.

### Project Title: Sales Data Analysis Project
---
### Project Overview
---
This project aims to analyze sales data to identify trends, patterns, and insights that can inform business decisions and drive growth.  It focuses on analyzing specific sales data that includes such as sales transactions, customer demographics, product categories, regional sales performance, time-based sales trends. The goal is to provide actionable recommendations to improve sales performance, optimize marketing strategies, and enhance customer engagement.

### Data Sources
---
The primary source of data used here is LITA Capstone Dataset.xlsx.

### Tools & Technologies
---
- Microsoft Excel: 
  1. For data analysis and visualization.
  2. For data summarization and pivot tables.
  3. To create charts and reports.

- Structured Query Language - SQL: 
  1. To retrieve and analyze data.
  2. To manage and manipulate the data
  3. To create, query, and modify the data.

- PowerBI:
  1. For data visualization and reporting.
  2. For data modeling and transformation.
  3. To create interactive dashboards.

### Data Cleaning & Preparation
---
It is crucial to clean and prepare our data for analysis. I, therefore, performed the following:

- Identified & removed duplicate records using [the 'remove duplicate tool' from the data tab]
- Normalized the dataset by;
    - Standardizing the date formats to [format, e.g., YYYY-MM-DD]
    - Converting each columns' data type
    - Filtering the columns
 
### Exploratory Data Analysis
---
This involves the exploration of data to answer the following questions:

- What is the total sales for each product?
- What is the number of sales transaction in each region?
- What is the monthly Sales for each product based on their region?

### Data Analysis
---
Line of queries/codes used during analysis.

```SQL
Select 
	Product,
	SUM(Revenue) AS TotalSales
FROM 
	[dbo].[SalesData]
GROUP BY 
	Product
ORDER BY 
	TotalSales Desc
```

```SQL
SELECT 
	MONTH(OrderDate) AS SalesMonth,
	SUM(Revenue) AS MonthlySalesTotal
FROM 
	SalesData
WHERE 
	YEAR(OrderDate) = YEAR(GETDATE())
GROUP BY 
	MONTH(OrderDate)
ORDER BY 
	SalesMonth
```

### Data Visualization

![SalesData Dashboard](https://github.com/user-attachments/assets/a914b248-371d-453a-892b-2d83973f5a11)
