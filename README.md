## LITA_CAPSTONE_PROJECTS_

INCUBATOR HUB: This repository contains two comprehensive analysis of the Sales Data of a retail store and Customer Segmentation for a subscription service. Using Excel, SQL, &amp; PowerBI for analysis, report & visualization.

### Project Title: Sales Data & Customer Segmentation Analysis
---
### Project Overview
---
This project aims to analyze sales data to identify trends, patterns, and insights that can inform business decisions and drive growth.  It focuses on analyzing specific sales data that includes such as sales transactions, customer demographics, product categories, regional sales performance, time-based sales trends. The goal is to provide actionable recommendations to improve sales performance, optimize marketing strategies, and enhance customer engagement.

### Data Sources
---
The primary source of data used here is LITA Capstone Dataset.xlsx. which contains two worksheets; the sales data and the customer data.

### Tools & Technologies
---
For both projects, I made use of the same tools and technologies to carry out me cleaning, analysis and down to visualization.
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
For both projects, I cleaned and prepared my dataset alike; in a ready-for-exploration manner. I, therefore, performed the following:

- Identified & removed duplicate records using [the 'remove duplicate tool' from the data tab]
- Normalized the dataset by;
    - Standardizing the date formats to [format, e.g., YYYY-MM-DD].
    - Converting each columns' data type.
    - Filtering the columns.
    - Adding columns I deemed fit.

#### For Sales Data, I added a revenue column in order to run my exploratory data.
![Cleaned SalesData](https://github.com/user-attachments/assets/48b9284a-a3aa-4a58-87a1-181fa2e5ff36)

#### For Customer Data, I added the subscription duration column in order to run my exploratory data.
![Cleaned CustData](https://github.com/user-attachments/assets/770c6f00-2565-44ef-84a0-d8f0003da2b8)

### Exploratory Data Analysis
---
This involves the exploration of data to answer the following questions:

#### For Sales Data

- What is the total sales for each product?

![EDA-Tot_Sales_By_Prod](https://github.com/user-attachments/assets/dad5ea1a-0518-42d4-ab14-6d5c00ff57d5)

- What is the number of sales transaction in each region?

![EDA-No_Of_Sales_Tran_By_Reg](https://github.com/user-attachments/assets/d4e40a0e-e228-4aa9-9d18-fd124d29f786)

- What is the monthly Sales for each product based on their region?


#### For Customer Data
- What is the average subscription duration?

![EDA-Avr_Sub_Duration](https://github.com/user-attachments/assets/48fa04f0-817f-4b00-afff-c9177fdc3853)

- What is the most popular subscription type?
  
![EDA-Most_pop_sub_type](https://github.com/user-attachments/assets/2fc61889-0091-4c82-ab70-c236b24253c4)

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

![SalesData Dashboard](https://github.com/user-attachments/assets/ff552317-d222-4dc1-995c-95fbbc27aecd)

![CustomerData Dashboard](https://github.com/user-attachments/assets/3b692215-6f93-43fd-9260-414148320f75)
