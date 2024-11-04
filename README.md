# Project1_Documentation

### Project Title: Sales Performance Analysis

[Project Overview](#project-overview)

[Data Sources](#data-sources)

[Tools Used](#tools-used)

[Data Cleaning and Preparations](#data-cleaning-preparations)

[Exploratory Data Analysis](#exploratory-data-analysis)

[Data Analysis](#data-analysis)

[Data Visualization](#data-visualization)

[Key Findings](#key-findings)

[Recommendations](#recommendations)

[Conclusion](#conclusion)

[Appendix](#appendix)

### Project Overview
---
This project aims to explore and analyze sales data to generate key insights about a retail store performance.The analysis is designed to produce an interactive dashboard that highlights key findings, thereby enabling stakeholders to make data-driven decisions and to improve overall business performance.

### Data Sources
---
The data used for this analysis is LITA Capstone Dataset.xlsx and this is an open source data that can be downloaded from anyrepository site.

### Tools Used
---
- Microsoft Excel
  1. For Data Cleaning
  2. For Analysis
  3. For Data Visualization
     
-Structured Query Language for Querying of the Data

-Power BI 
  1. To build interactive dashboard
  2. For Data Visualization

### Data Cleaning and Preparations
---
This phase includes cleaning and preparing the data before visualizing it. The following steps was adopted:
  1. Data loading and Inspection
  2. Removal of Duplicate entries
  3. Data Cleaning and formatting

### Exploratory Data Analysis
---
This involves the initial exploration of the data to answer some basic questions about the data such as;
- What are the top selling products?
- What are the sales trend in days, month, and years?
- What are the sales performance across the regions?

### Data Analysis
---
```Excel
=SUMIF(D2:D9922,D2,H2:H9922)
```
```
=AVERAGEIF(C2:C9922,C2,H2:H9922)
```
  1. Pivot tables was used to summarize total sales by product, region, and month;top selling products
  2. Formulas was used to calculate metrics like average sales per product and total revenue by region


```SQL
Select top 1 product,SUM(revenue)as HighestsellingProduct from [dbo].[PROJECT1]
group by Product
The xlsx file was converted to a csv file and  imported to SQL server environment before creating a databasea and validating the following queries;
  - Retrieving total sales for each product category
  - Finding the top 5 customers by total purchase amount
  - Calculating total revenue per product
  - Finding the number of sales transactions in each region
  - Finding the highest selling product by total sales value
  - Identifying products with no sales in the last quarter
  - Calculating the percentage of total sales contributed by each region
```

- Power BI
  Here, a dashboard was created to visualize the insights found in Excel and SQL which includes the following;
  - Sales overview
  - Top performing products
  - Regional breakdowns
  - Slicers to filter sales data to quickly analyze performance in specific areas and identify sales trends
  - Bar charts, line chart, scatter plot, cards was also used to visualize trends in the data

  ### Data Visualization
  ---
![Excel_Sales](https://github.com/user-attachments/assets/7d947475-1862-4fa3-859a-34e9dcc3afce)

![Power BI_Sales](https://github.com/user-attachments/assets/feb14efc-be98-4680-a900-2c612e3e9714)

![SQL_Sales](https://github.com/user-attachments/assets/ad981625-3aaf-4c75-80e7-34953f7c0492)

### Key Findings
---
- Total Sales reached ₦2.1 million, with an impressive average order value of ₦105,000.

Regional Income:
- The South dominated revenue generation, accounting for 44.2% of total sales, followed by the East at 23.1%, the North at 18%, and the West at 14.3%.

Top Products:
- Hats led in quantity sold with 15,929 units, while shoes emerged with the highest revenue, generating ₦613,380. In contrast, jackets lagged with only 5,452 units sold, indicating opportunities for promotional strategies.

Daily and Yearly Trends:
- The highest daily sales peaked at ₦1,121,655 on the 31st of the month, while 2023 recorded ₦1,105,330 in total sales. However, 2024 had a decline to ₦995,760, indicating that there are some market challenges that occured in 2024.

Monthly Sales:
- February stood out with the highest sales at ₦546,300, while December was the lowest, showing that the products were purchased based on the seasons evolving.

Interactive Analysis:
- The use of slicers for key insights helps to explore revenue changes and sales trends, enhancing data-driven decision-making.

### Recommendations
---
- The store can come up with special offer/promotions during the months where sales is low, to boost the Sales in those seasons.
- Investigate the reasons for decline in the sales in certain regions and identify areas for improvement.
- The overall sales performance in the South is strong, there could be targetted offers to boost the sales in the region.
- There could be emails or messages sent to customers from time to time to get feedback on product satisfaction and understand market trend.

### Conclusion
---
The sales performance analysis revealed key insights into regional revenue distribution and the performance of the products, indicating opportunities for growth. By implementing the recommended suggestions, the retail store can improve sales, have better customer engagement, and above all align its offers with market demands.

### Appendix
---
- Excel	metrics used to calculate Average Sales and Aggregate
![image](https://github.com/user-attachments/assets/0933170a-7552-4d3f-ab6d-c6ef30875fd0)

- For Pivot table in Excel       
![image](https://github.com/user-attachments/assets/76e2b4d8-b1d3-4784-a3a1-c13ab9b8802c)

- SQL Queries
Create database money_db
Select *from [dbo].[PROJECT1]

----Retrieve total sales for each product category---

Select product,SUM(revenue) as TotalSales from [dbo].[PROJECT1]
group by product

----Highest selling product by Total Sales value----
Select top 1 product,SUM(revenue)as HighestsellingProduct from [dbo].[PROJECT1]
group by Product

---find the number of sales transactions in each region---
Select region, count(*) AS NumberOfSalesTransaction from [dbo].[PROJECT1]
group by region

---To calculate the total revenue per product-----
Select product, SUM(revenue) as TotalRevenue from [dbo].[PROJECT1]
group by Product

----Calculate the monthly sales total for the current year---
SELECT
	FORMAT(ORDERDATE, 'yyyy-MM') AS sales_month,
	SUM(Revenue) AS monthly_sales_total
FROM
	[dbo].[PROJECT1]
WHERE
	YEAR(OrderDate) = 2024
GROUP BY
	FORMAT(OrderDate, 'yyyy-MM')
ORDER BY
	FORMAT(OrderDate, 'yyyy-MM')

--TOP 5 CUSTOMERS BY TOTAL PURCHASE AMOUNT---
SELECT TOP 5 
    CUSTOMER_ID, 
    SUM(revenue) AS TotalPurchase
FROM 
    [dbo].[PROJECT1]
GROUP BY 
    CUSTOMER_ID
ORDER BY 
    TotalPurchase DESC

---Calculate the percentage of total sales contributed by each region----
SELECT
	region,
	SUM(Revenue) AS region_sales_total,
	(SUM(Revenue) * 100) / (SELECT SUM(Revenue) FROM [dbo].[PROJECT1])
	AS sales_percentage
FROM
	[dbo].[PROJECT1]
GROUP BY
	region

---Identify the products with no sales in the last quarter---
SELECT
    Product
FROM 
    [dbo].[PROJECT1]
GROUP BY 
    Product
HAVING
    SUM(CASE WHEN OrderDate >= '2024-01-01' AND OrderDate < '2024-04-01' THEN 1 ELSE 0 END) > 0

