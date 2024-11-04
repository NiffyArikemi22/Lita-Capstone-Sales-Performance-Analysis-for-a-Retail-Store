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

### Dataset File
data (folder containing the dataset([SalesData CSV.csv](https://github.com/user-attachments/files/17621528/SalesData.CSV.csv))

### Tool Used
* Excel Function
* SQL
* PowerBI

### Step-by-Step Dashboard Creation

#### Step 1: Load the Data

1. *Import Data:*
   - I loaded the dataset into Power BI via Excel.
   - i clicked on *Get Data*, choose your source, and load the data.

#### Step 2: Data Modeling

1. *Create Measures:*
   - *Total Sales*:
     DAX
     Total Sales = SUMX(SalesData, SalesData[UnitPrice] * SalesData[Quantity])
     
   - *Total Quantity Sold*:
     DAX
     Total Quantity = SUM(SalesData[Quantity])
 - *Total Orders*:
     DAX
     Total Orders = COUNT(SalesData[OrderID])
     
   - *Average Order Value*:
     DAX
     Average Order Value = DIVIDE([Total Sales], [Total Orders], 0)
     
   - *Sales Growth Percentage* (compared to previous month):
     DAX
     Sales Growth % = 
     VAR PreviousMonthSales = 
         CALCULATE(
             [Total Sales],
             PREVIOUSMONTH(SalesData[OrderDate])
         )
 RETURN
     DIVIDE([Total Sales] - PreviousMonthSales, PreviousMonthSales, 0)
     

2. *Create Date Hierarchy:*
   - By clicking on OrderDate column and create a hierarchy (Year, Month, Day) to allow for easy time-based filtering and analysis.

#### Step 3: Create Visualizations

1. *Sales Overview:*
   - *Total Sales Card:*
     - Visual: Card
     - Value: Total Sales

   - *Total Orders Card:*
     - Visual: Card
     - Value: Total Orders
   - *Average Order Value Card:*
     - Visual: Card
     - Value: Average Order Value

1. *Sales Trend Analysis:*
   - *Sales Trend Line Chart:*
     - Visual: Line Chart
     - Axis: Month-Year (created from OrderDate)
     - Values: Total Sales
   - *Sales Growth Percentage Card:*
     - Visual: Card
     - Value: Sales Growth %

2. *Customer Insights:*
   - *Top Customers Table:*
     - Visual: Table
     - Columns: CustomerId, Total Sales, Total Orders
       
   - *Customer Segmentation Pie Chart:*
     - Visual: Pie Chart
     - Legend: Region
     - Values: Total Sales

3. *Product Performance:*
   - *Top Products Table:*
     - Visual: Table
     - Columns: Product, Total Sales, Total Quantity Sold
       
   - *Sales by Product Bar Chart:*
     - Visual: Bar Chart
     - Axis: Product
     - Values: Total Sales

4. *Regional Breakdown:*
   - *Sales by Region Map:*
     - Visual: Map
     - Location: Region
     - Values: Total Sales

#### Step 4: Interactivity

- *Add Slicers:*
  - *Slicer for Region:* To filter all visuals based on selected region(s).
  - *Slicer for Product:* To filter visuals based on specific products.
  - *Date Slicer:* To allow users to filter data based on specific date ranges.

- *Enable Drill-Down:*
  - Enable drill-down on the sales trend line chart to analyze monthly or daily trends.

