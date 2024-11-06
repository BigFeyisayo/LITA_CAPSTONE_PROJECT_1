## LITA_CAPSTONE_PROJECT_1

INCUBATOR HUB: This repository contains a comprehensive analysis of the Sales Performance of a retail store. Using Excel, SQL, &amp; PowerBI for analysis, report & visualization.

### Project Title: Sales Performance Analysis

[Project Overview](#project-overview)

[Data Sources](#data-sources)

[Tools And Technologies](#tools-and-technologies)

[Data Cleaning And Preparation](#data-cleaning-and-preparation)

[Exploratory Data Analysis](#exploratory-data-analysis)

[Data Analysis](#data-analysis)

[Data Visualization](#data-visualization)

### Project Overview
---
This project aims to analyze sales data to identify trends, patterns, and insights that can inform business decisions and drive growth.  It focuses on analyzing specific sales data that includes such as sales transactions, customer demographics, product categories, regional sales performance, time-based sales trends. The goal is to provide actionable recommendations to improve sales performance, optimize marketing strategies, and enhance customer engagement.

### Data Sources
---
The primary source of data used here is LITA Capstone Dataset.xlsx. 

### Tools And Technologies
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

### Data Cleaning And Preparation
---
- Identified & removed duplicate records using [the 'remove duplicate tool' from the data tab]
- Normalized the dataset by;
    - Standardizing the date formats to [format, e.g., YYYY-MM-DD].
    - Converting each columns' data type.
    - Filtering the columns.
    - Adding columns I deemed fit.

- For Sales Data, I added a revenue column in order to run my exploratory data.
![Cleaned SalesData](https://github.com/user-attachments/assets/48b9284a-a3aa-4a58-87a1-181fa2e5ff36)

### Exploratory Data Analysis
---
This involves the exploration of data to answer the following questions:

- What is the total sales for each product?

![EDA-Tot_Sales_By_Prod](https://github.com/user-attachments/assets/dad5ea1a-0518-42d4-ab14-6d5c00ff57d5)

- What is the number of sales transaction in each region?

![EDA-No_Of_Sales_Tran_By_Reg](https://github.com/user-attachments/assets/d4e40a0e-e228-4aa9-9d18-fd124d29f786)

- What is the monthly Sales for each product based on their region?

![EDA-RegionalSales_By_Prod](https://github.com/user-attachments/assets/e649397e-d05c-448e-8d8d-95e4e627b479)

- Average sales per product

![EDA-Avr_Sales_Per_Prod](https://github.com/user-attachments/assets/5f47da9e-9d5e-4b27-85a9-bf27bfa1c58f)

- Total revenue by region

![EDA-Total_Rev_By_Region](https://github.com/user-attachments/assets/a3d57d9f-882c-4da6-be02-482aad3f3507)

### Data Analysis
---
Line of queries/codes used during analysis.

- Retrieve the total sales for each product category.
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

- Find the number of sales transactions in each region.
```SQL
SELECT
	Region,
	COUNT(*) AS NoOfSalesTransactions
FROM
	[dbo].[SalesData]
GROUP BY 
	Region
ORDER BY 
	NoOfSalesTransactions Desc
```

- Find the highest-selling product by total sales value.
```SQL
SELECT Top 1
	Product,
	SUM(Revenue) AS TotalSalesValue
FROM 
	SalesData
GROUP BY 
	Product
ORDER BY 
	TotalSalesValue Desc
```

- Calculate total revenue per product.
```SQL
SELECT 
	Product, 
	SUM(Revenue) AS TotalRevenuePerProduct
FROM 
	SalesData
GROUP BY 
	Product
ORDER BY 
	TotalRevenuePerProduct DESC
```

- Calculate monthly sales totals for the current year.
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

- Find the top 5 customers by total purchase amount.
```SQL
SELECT TOP 5 
	Customer_Id, 
	SUM(Revenue) AS TotalPurchaseAmount
FROM 
	SalesData
GROUP BY 
	Customer_Id
ORDER BY 
	TotalPurchaseAmount DESC
```

- Calculate the percentage of total sales contributed by each region.
```SQL
SELECT 
	Region,
	SUM(Revenue) AS RegionalSales,
	CONCAT(ROUND(SUM(Revenue) / (Select SUM(Revenue) FROM SalesData) * 100, 2), '%') AS SalesPercentage
FROM
	SalesData 
GROUP BY
	Region
ORDER BY
	RegionalSales Desc
```
- Identify products with no sales in the last quarter.
```SQL
SELECT 
	Product,
	SUM(Quantity) AS ProdWtNoSale
FROM 
	SalesData
WHERE 
	Product NOT IN (
					SELECT 
					Product
					FROM 
					SalesData
					WHERE 
					OrderDate >= DATEADD(quarter, -1, GETDATE())
					)
	GROUP BY Product
```

### Data Visualization

![SalesReport Dashboard](https://github.com/user-attachments/assets/300492d6-94ff-42ac-a5f3-5eb8e98a2bd7)

