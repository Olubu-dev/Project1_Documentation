# Project1_Documentation

### Project Title: Sales Performance Analysis

### Project Overview
This project aims to explore and analyze sales data to generate key insights about the retail store performance.The analysis is designed to produce an interactive dashboard that highlights these key findings, thereby enabling stakeholders to make data-driven decisions and to improve overall business performance.

### Data Sources
The data used for this analysis is LITA Capstone Dataset.xlsx and this is an open source data that can be downloaded from anyrepository site.

### Tools Used
- Microsoft Excel
  1. For Data Cleaning
  2. For Analysis
  3. For Data Visualization
     
-Structured Query Language for Querying of the Data

-Power BI 
  1. To build interactive dashboard
  2. For Data Visualization

### Data Cleaning and Preparations
This phase includes cleaning and preparing the data before visualizing it. The following steps was adopted:
  1. Data loading and Inspection
  2. Removal of Duplicate entries
  3. Data Cleaning and formatting

### Exploratory Data Analysis
This involves the initial exploration of the data to answer some basic questions about the data such as;
- What are the top selling products?
- What are the sales trend in days, month, and years?
- What are the sales performance across the regions?

### Methodology
- Excel
  1. Pivot tables was used to summarize total sales by product, region, and month;top selling products
  2. Formulas was used to calculate metrics like average sales per product and total revenue by region

- SQL
The xlsx file was converted to a csv file and  imported to SQL server environment before creating a databasea and validating the following queries;
  - Retrieving total sales for each product category
  - Finding the top 5 customers by total purchase amount
  - Calculating total revenue per product
  - Finding the number of sales transactions in each region
  - Finding the highest selling product by total sales value
  - Identifying products with no sales in the last quarter
  - Calculating the percentage of total sales contributed by each region

- Power BI
  Here, a dashboard was created to visualize the insights found in Excel and SQL which includes the following;
  - Sales overview
  - Top performing products
  - Regional breakdowns
  - Slicers to filter sales data to quickly analyze performance in specific areas and identify sales trends
  - Bar charts, line chart, scatter plot, cards was also used to visualize trends in the data
  
### Data Analysis
This is where line of codes, metrics is imputed for  the calculation of the tools used 

```Excel
=SUMIF(D2:D9922,D2,H2:H9922)