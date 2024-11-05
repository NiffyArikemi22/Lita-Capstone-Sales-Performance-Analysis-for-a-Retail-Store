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
* Excel Function
* SQL
* PowerBI


### Dataset File
Excel File (folder containing the dataset([SalesData CSV.csv](https://github.com/user-attachments/files/17621528/SalesData.CSV.csv))

Excel:
o PerformED an initial exploration of the sales data by pivot tables to summarize
total sales by product, region, and month


SQL queries

```
[Uploacreate database LITAPROJECT_DB

-----1ST PROJECT(Sales Performance Analysis for a Retail Store)

 Select * from [dbo].[SalesData CSV]

------(question 1) Total sales for each product------

Select product, sum(Total_Sales)
as Sales_by_Product 
from [dbo].[SalesData CSV]
group by product

-------(question 2) Number of sales transactions in each Region------

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

---------Monthly sales totals for the current year
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


