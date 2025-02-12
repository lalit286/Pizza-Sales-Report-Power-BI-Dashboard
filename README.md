# Pizza Sales Report #



**Problem Statement: Pizza Sales Analysis Dashboard Using Power BI & SQL**

**Background**

In the highly competitive pizza industry, understanding sales performance and customer preferences is crucial for strategic decision-making. The pizza sales data contains valuable insights that can help identify trends, optimize operations, and enhance marketing efforts. However, the current data is scattered and not easily accessible in a comprehensive, visual format.

**Objective**
The objective of this project is to create a Power BI dashboard that provides an intuitive and interactive visual representation of the pizza sales data. The dashboard will enable stakeholders to monitor key performance indicators (KPIs), analyze sales trends, and make data-driven decisions to improve business performance.

**Key Goals**
Centralize Data: Integrate and centralize all pizza sales data into a single Power BI dashboard.

Visualize KPIs: Display key performance indicators such as total revenue, average order value, total pizzas sold, and total orders.

Trend Analysis: Provide daily and monthly trend analyses to identify patterns and fluctuations in sales.

Sales Breakdown: Offer a detailed breakdown of sales by pizza category and pizza size.

Top and Bottom Performers: Highlight the top and bottom-performing pizzas based on revenue, quantity sold, and total orders.

Interactivity: Ensure the dashboard is interactive, allowing users to filter and drill down into specific data points for deeper insights.

**Scope**
The Power BI dashboard will include the following components:

* Revenue Overview

* Total Revenue

* Average Order Value

* Total Pizzas Sold

* Total Orders

* Average Pizzas Per Order

* Trend Analysis

* Daily Trend for Total Orders

* Monthly Trend for Orders

* Sales Breakdown

* Percentage of Sales by Pizza Category

* Percentage of Sales by Pizza Size

* Top and Bottom Performers

* Top 5 and Bottom 5 Pizzas by Revenue

* Top 5 and Bottom 5 Pizzas by Quantity

* Top 5 and Bottom 5 Pizzas by Total Orders


# Pizza Sales Dashboard


**Dashboard**
![Dashboard Image](https://github.com/lalit286/Pizza-Sales-Report-Power-BI-Dashboard/blob/main/Pizza_Sales_Report_Dashboard.png)

**BEST/WORST SELLERS**
![Dashboard Image](https://github.com/lalit286/Pizza-Sales-Report-Power-BI-Dashboard/blob/main/Pizza_Sales_Report_Dashboard2.png)


 **SQL QUERIES**
[VIEW SQL QUERIES](URL)

PIZZA SALES SQL QUERIES
* A. KPI’s
1. Total Revenue:
SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;
 
2. Average Order Value
SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value FROM pizza_sales
 
3. Total Pizzas Sold
SELECT SUM(quantity) AS Total_pizza_sold FROM pizza_sales
 
4. Total Orders
SELECT COUNT(DISTINCT order_id) AS Total_Orders FROM pizza_sales
 
5. Average Pizzas Per Order
SELECT CAST(CAST(SUM(quantity) AS DECIMAL(10,2)) / 
CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS DECIMAL(10,2))
AS Avg_Pizzas_per_order
FROM pizza_sales
 
* B. Daily Trend for Total Orders
SELECT DATENAME(DW, order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders 
FROM pizza_sales
GROUP BY DATENAME(DW, order_date)
Output:
 
* C. Monthly Trend for Orders
select DATENAME(MONTH, order_date) as Month_Name, COUNT(DISTINCT order_id) as Total_Orders
from pizza_sales
GROUP BY DATENAME(MONTH, order_date)Output
 


* D. % of Sales by Pizza Category
SELECT pizza_category, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_category
Output
 
* E. % of Sales by Pizza Size
SELECT pizza_size, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_size
ORDER BY pizza_size
Output
 

* F. Total Pizzas Sold by Pizza Category
SELECT pizza_category, SUM(quantity) as Total_Quantity_Sold
FROM pizza_sales
WHERE MONTH(order_date) = 2
GROUP BY pizza_category
ORDER BY Total_Quantity_Sold DESC
Output
 
* G. Top 5 Pizzas by Revenue
SELECT Top 5 pizza_name, SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue DESC
 
* H. Bottom 5 Pizzas by Revenue
SELECT Top 5 pizza_name, SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue ASC
 
* I. Top 5 Pizzas by Quantity
SELECT Top 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold DESC
Output
 
* J. Bottom 5 Pizzas by Quantity
SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold ASC

* K. Top 5 Pizzas by Total Orders
SELECT Top 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders DESC
 
* L. Borrom 5 Pizzas by Total Orders
SELECT Top 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders ASC
 






