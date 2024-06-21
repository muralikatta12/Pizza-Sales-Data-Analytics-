# Pizza Sales Analysis
### Project Overview

Welcome to the Pizza Sales Data Analytics Report repository. This project leverages SQL queries to analyze pizza sales data, focusing on key performance indicators (KPIs) to provide actionable insights into business performance.

### Data Sources

Sales Data: The primary dataset used for this analysis is the "pizza_sales.csv" file, containing detailed information about each sale made by the company.

###Tools

- Excel - Data cleaning
- SQL Server - Data analysis
- Power BI - creating a reports

  ### Data Cleaning/Preparation
  In this initial data preparation phase, we performed following tasks:

  1. Dataloading and inspection.
  2. Handling missing values.
  3. Data cleaning and formatting.

  ### KPI's




  ### Data Analysis



  
1. Total Revenue:
```select round(sum(total_price),2) as Total_Revenue from ```
``` pizza_sales; ```
 

2. Average Order value:
   ```select round(sum(total_price) / count(DISTINCT order_id),2) ```
```   as Avg_ord_value from pizza_sales; ```
 
### 3. Total Pizzas Sold:
SELECT SUM(quantity) AS Total_Pizza_Sold
from pizza_sales;
 
4. Total_Orders:
SELECT COUNT(DISTINCT order_id)  as Total_Orders
from pizza_sales;
 
5. Average pizzas per order:
SELECT CAST(
         CAST(SUM(quantity) AS DECIMAL(10,2)) / 
         CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2))
       AS DECIMAL(10,2)) AS Avg_pizza_per_order
FROM pizza_sales;
 
6. Daily Trend for Total orders:
SELECT DATENAME(DW,order_date) AS order_day,COUNT (DISTINCT order_id) AS Total_orders
from pizza_sales
GROUP BY DATENAME(DW,order_date)
 
7. Monthly Trend for total orders:
SELECT DATENAME(MONTH,order_date) as Month_Name , COUNT(DISTINCT order_id) as Total_orders
from pizza_sales GROUP BY DATENAME(MONTH,order_date) ORDER BY Total_orders DESC

  
8. Percentage of sales by pizza category:
SELECT pizza_category, sum(total_price) ,
round(sum(total_price)*100 /(SELECT sum(total_price) from pizza_sales),2)as PCT
from pizza_sales GROUP BY pizza_category
 
9. Percentage of sales by pizza size:
SELECT pizza_size, round(sum(total_price),2) as Total_sales,
round(sum(total_price)*100 /(SELECT sum(total_price) from pizza_sales),2)as PCT
from pizza_sales GROUP BY pizza_size 
ORDER BY PCT DESC
 
10. Top 5 Best sellers by revenue,Total quantity and Total_orders:
SELECT TOP 5 pizza_name, sum(total_price) as Total_revenue 
from pizza_sales group by pizza_name  
order  by Total_revenue DESC
 
 ii)Total quantity
SELECT TOP 5 pizza_name, COUNT(quantity) as Total_Quantity
from pizza_sales group by pizza_name  
order  by Total_Quantity DESC
 `
 iii)Total orders
SELECT TOP 5 pizza_name, COUNT(DISTINCT order_id) as Total_orders
from pizza_sales group by pizza_name  
order  by Total_orders DESC
 


