# Lita-Capstone-Sales-Performance-Analysis-for-a-Retail-Store

### Capstone SalesData Project

## Project Overview/Objectives

This project analyzes the sales performance of a retail store by exploring sales data to uncover key insights such as top-selling products, regional
performance, and monthly sales trends. The goal is to produce an interactive Power BI
dashboard that highlights these findings. Furthermore, this repository give a detailed example of Excel, SQL and  Power BI dashboard for the sales dataset, providing more in-depth guidance on visualizations, DAX calculations, and insights. This project include specific visuals, potential data analysis questions, and how to implement them in Power BI.

### Dataset Structure

*Columns:*
- OrderID: Unique identifier for each order
- CustomerId: Unique identifier for each customer
- Product: Name of the product sold
- Region: Region where the sale occurred
- OrderDate: Date of the order
- UnitPrice: Price per unit of the product
- Quantity: Number of units sold

### Tool Used
* Excel Function: Used for data cleaning (removing duplicates) and summarizing the data using pivot tables
* SQL: Performed data analysis and created views for generationg insoghts
* PowerBI: Used to visualize the finding through interactive dashboards.


### Dataset File
Excel File (folder containing the dataset([SalesData CSV.csv](https://github.com/user-attachments/files/17621528/SalesData.CSV.csv))

### Key Objectives:

1. Clean and preprocess sales data for analysis
2. Analyze sales trends and patterns using SQL Server queries
3. Visualize critical sales performance metrics using Power BI dashboards
4. Identify top products, regions with highest sales, and top customers

### Methodology:

1. Data Cleaning: Excel data manipulation and Pivot Tables
2. Data Analysis: SQL Server queries for data modeling and insights
3. Data Visualization: Power BI dashboards for interactive and dynamic visualization


### Exploratory Data Analysis (EDA)
* Total Sales per Product Category
* Sales Transactions in Each Region
* Top Selling Product
* Revenue per Product
* Monthly Sales for current year
* Percentage of Sales Contributed by Region
* Products with no sales in the last Quarter

Excel:
Performed an initial exploration of the sales data by pivot tables to summarize
total sales by product, region, and month using Pivot Table

![image](https://github.com/user-attachments/assets/d2e4be1e-ee49-4a4a-9ed8-6abc4a03e10e)

![image](https://github.com/user-attachments/assets/7c9cf525-8158-414b-b542-4f57bbed6fd8)

![image](https://github.com/user-attachments/assets/17653d5b-3842-41c8-a12b-c3a45b7ebda9)

### Line Chart visualizing MoM Change in Revenue comparing 2023-2024

![image](https://github.com/user-attachments/assets/93383850-c367-4430-b2b1-ec8e8d67e866)

### Product	Average Sales

![image](https://github.com/user-attachments/assets/362ae9be-d21e-4d44-803d-12f7621a7c9b)

 ### 2023-2024 Total Revenue %
 
![image](https://github.com/user-attachments/assets/b4ce1f45-c791-4b46-89ec-b79335a37ffd)

### Product by Total Sales and Total Quantity Sold

![image](https://github.com/user-attachments/assets/f355b171-3893-406b-a543-c8ba3d620d57)
						
![image](https://github.com/user-attachments/assets/348b049e-c2a5-4be5-ae18-e19e28df92c2)



### SQL queries:

```
[Uploacreate database LITAPROJECT_DB

-----1ST PROJECT(Sales Performance Analysis for a Retail Store)

 Select * from [dbo].[SalesData CSV]

 ------(question 1) Total sales for each product------

Select product, sum(Total_Sales)
as Sales_by_Product 
from [dbo].[SalesData CSV]
group by product

------(question 2) Number of sales transactions in each Region------

Select Region, sum(Total_sales)
as sales_per_region
from [dbo].[SalesData CSV]
group by Region

----------(question 3) Highest-selling product by total sales value

Select Product, Sum(Total_sales)
as Highest_Selling_product 
from [SalesData CSV]
group by Product

-------(question 4) Total revenue per product-----

Select Product, sum(Revenue) 
as Total_Revenue 
from [SalesData CSV] 
group by Product
--------Monthly sales totals for the current year
----Create	OrderMonth Column

Alter table [dbo].[SalesData CSV]
Add OrderMonth nvarchar(50)
Update [dbo].[SalesData CSV]
set OrderMonth = DateName(Month,OrderDate)

 ----to create OrderYearColumn
Alter Table [dbo].[SalesData CSV]
Add OrderYear int
update [dbo].[SalesData CSV]
set OrderYear=Year(OrderDate)

 ------(question 5) Monthly sales totals for the current year
Select OrderMonth, sum(Quantity)
as TotalSales
from [dbo].[SalesData CSV]
where OrderYear=2024
group by OrderMonth


-----------(Question 6)Top 5 customers by total purchase amount
Select Top 5 Customer_Id, 
sum(Total_sales) as TotalPurchase
from [dbo].[SalesData CSV]
group by Customer_Id
Order by TotalPurchase DESC

 -----------(question 7) Percentage of total sales contributed by each region

Select Region,
sum(Revenue) / sum(quantity * UnitPrice) * 0.1
as Percentage_of_Total_sales
from [SalesData CSV]
group by Region
Order by Percentage_of_Total_sales

-------(Question 8) Products with no sales in the last quarter

select Product, sum(Total_Sales) as Sales
from [SalesData CSV]
where Month(Orderdate) between 10 and 12
group by Product
Having sum(quantity * UnitPrice) = 0 
```

### PowerBI Dashboard

![WhatsApp Image 2024-11-08 at 16 33 10_c2ffb417](https://github.com/user-attachments/assets/7236e855-b7c4-4fe0-9ae4-a56c3e16a65f)

### Conclusion
This project presents a comprehensive methodology for cleaning, analyzing, and visualizing sales performance data for a retail store, employing Excel for data manipulation, SQL Server for querying, and Power BI for interactive dashboard creation, yielding key insights on top products, regions, and customers to support strategic business decision-making.
