# Pizza Sales Analysis
## Table of contents
 - [Project Overview](#project-overview)
 - [Data Sources](#Data-Sources)
 - [Recomendations](#Recommendations)
### Project Overview

Welcome to the Pizza Sales Data Analytics Report repository. This project leverages SQL queries to analyze pizza sales data, focusing on key performance indicators (KPIs) to provide actionable insights into business performance.

### Data Sources

Sales Data: The primary dataset used for this analysis is the "pizza_sales.csv" file, containing detailed information about each sale made by the company.

### Tools

- Excel - Data cleaning
  - [Download Here](#pizza_sales.csv)
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
     ```
     select round(sum(total_price),2) as Total_Revenue from 
     pizza_sales;
     ```
       #### output:-
       ![image](https://github.com/muralikatta12/Pizza-Sales-Data-Analytics-Report/assets/124357793/54431c5b-cf2f-4df8-88de-9b229c05fed9)

   2. Average Order value:
     ```
     select round(sum(total_price) / count(DISTINCT order_id),2)
     as Avg_ord_value from pizza_sales;
     ```
     #### output:-
     ![image](https://github.com/muralikatta12/Pizza-Sales-Data-Analytics-Report/assets/124357793/05a5bd90-f8da-4d13-986d-3997d59d1bf8)

   3. Total Pizzas Sold:
     ```
     SELECT SUM(quantity) AS Total_Pizza_Sold
     from pizza_sales;
     ```
      #### output:-
      ![image](https://github.com/muralikatta12/Pizza-Sales-Data-Analytics-Report/assets/124357793/3b7aec78-0baa-4ae6-9669-6f4e3ca72aa7)

 
  5. Total_Orders:
    ```
    SELECT COUNT(DISTINCT order_id)  as Total_Orders
     from pizza_sales;
    ```
      #### output:-
      ![image](https://github.com/muralikatta12/Pizza-Sales-Data-Analytics-Report/assets/124357793/180f5833-12a0-46b8-895a-f7842883df6f)

 
  7. Average pizzas per order:
    ```
    SELECT CAST(
         CAST(SUM(quantity) AS DECIMAL(10,2)) / 
         CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2))
       AS DECIMAL(10,2)) AS Avg_pizza_per_order
    FROM pizza_sales;
    ```
      #### output:-
      ![image](https://github.com/muralikatta12/Pizza-Sales-Data-Analytics-Report/assets/124357793/8000cc88-d3c7-44d8-932a-11fce65fe64b)

 
  9. Daily Trend for Total orders:
   ```
   SELECT DATENAME(DW,order_date) AS order_day,COUNT (DISTINCT order_id) AS Total_orders
   from pizza_sales
   GROUP BY DATENAME(DW,order_date)
   ```
   #### output:-
   ![image](https://github.com/muralikatta12/Pizza-Sales-Data-Analytics-Report/assets/124357793/d73f6b98-e22c-438a-a484-607ceb0ba802)

  11. Monthly Trend for total orders:
   ```
     SELECT DATENAME(MONTH,order_date) as Month_Name , COUNT(DISTINCT order_id) as Total_orders
     from pizza_sales GROUP BY DATENAME(MONTH,order_date) ORDER BY Total_orders DESC

   ```
   #### output:-
   ![image](https://github.com/muralikatta12/Pizza-Sales-Data-Analytics-Report/assets/124357793/445038a8-1a04-462c-84d5-78f61acbf4eb)

  13. Percentage of sales by pizza category:
     ```
     SELECT pizza_category, sum(total_price) ,
     round(sum(total_price)*100 /(SELECT sum(total_price) from pizza_sales),2)as PCT
      from pizza_sales GROUP BY pizza_category
    ```
   #### output:-
  ![image](https://github.com/muralikatta12/Pizza-Sales-Data-Analytics-Report/assets/124357793/ba783a87-5d08-4b32-9a78-e15d23246e2b)

  15. Percentage of sales by pizza size:
    ```
    SELECT pizza_size, round(sum(total_price),2) as Total_sales,
   round(sum(total_price)*100 /(SELECT sum(total_price) from pizza_sales),2)as PCT
   from pizza_sales GROUP BY pizza_size 
   ORDER BY PCT DESC
    ```
   #### output:-
   ![image](https://github.com/muralikatta12/Pizza-Sales-Data-Analytics-Report/assets/124357793/b1fbb8e4-f532-43cb-87b3-862838d3eb1b)

  17. Top 5 Best sellers by revenue,Total quantity and Total_orders
    
   i) Total Revenue
   ```
   SELECT TOP 5 pizza_name, sum(total_price) as Total_revenue 
   from pizza_sales group by pizza_name  
   order  by Total_revenue DESC
   ```
   #### output:-
  ![image](https://github.com/muralikatta12/Pizza-Sales-Data-Analytics-Report/assets/124357793/a437da12-fe25-4f56-9cfb-b8c67f299e89)

 
  ii)Total quantity
   ```
   SELECT TOP 5 pizza_name, COUNT(quantity) as Total_Quantity
   from pizza_sales group by pizza_name  
   order  by Total_Quantity DESC
   ```
   #### output:-
  ![image](https://github.com/muralikatta12/Pizza-Sales-Data-Analytics-Report/assets/124357793/5fb3b1f5-6487-4111-a6ec-75fb1de7f986)

   iii)Total orders
  ```
  SELECT TOP 5 pizza_name, COUNT(DISTINCT order_id) as Total_orders
  from pizza_sales group by pizza_name  
  order  by Total_orders DESC
  ```
   #### output:-
   ![image](https://github.com/muralikatta12/Pizza-Sales-Data-Analytics-Report/assets/124357793/8660073f-f1be-4218-845d-28ddecbf2ad0)
   
### Findings from Pizza Sales Analysis

   1. Orders peak on weekends, particularly on Friday and Saturday evenings.

   2. Maximum orders are seen in July and January.

   3. The Classic category drives the highest sales and total orders.

   4. Large-size pizzas lead in terms of sales.

   5. The Thai Chicken Pizza contributes the most to overall revenue.
### Recommendations
  Based on the analysis I recommend the following actions
  
  - Since orders peak on weekends, particularly Friday and Saturday evenings, consider running special promotions or discounts during these times to maximize sales.
  - With maximum orders observed in July and January, plan targeted marketing campaigns for these months. This could include seasonal promotions, holiday-themed offers, 
    or special limited-time menu items.
  - Promote large-size pizzas through combo deals and special offers to boost sales.
  - Promote the Thai Chicken pizza prominently in your menu and advertisements.
  - Highlight the Brie Carre Pizza, as it significantly contributes to revenue, quantity sold, and total orders.

    

