# LITA-Capstone-Project-Sales-Data
---
## PROJECT TITLE: SALES DATA
---
## DATA SOURCE
- This data was provided by The Incubator Hub
---
## PROJECT OVERVIEW
- This project contains the Sales trend of a company within a year. The aim of this project is to get insights into the sales trends of the company, to see the Top performing Product , the Region that generated the most revenue etc and to profer solutions to when needed. This Project contains both Qualitative and Quantitative data.
---
## KEY VARIABLES
This segment explains the key variables that were used in the analysis;

**Qualitative Data** 
-  **Product:** this includes the goods that were up for sale.
-  **Region:** this expalains the geographical area that sales were made.
-  **Months:** this includes the months that sales were made.
-  **Order Id**: this is the Identification number for each customers whenever an order is placed.

  **Quantitative Data**
-  **Sales/Revenue**: this explains the total value of goods sold by a business within a specific period. Its calculated by multiplying you Price and Quantity.
- **Price:** this explains the worth of each goods to be sold.
-  **Quantity:** this explains the number of goods sold or produced in a specific trading period.
-  **Order Date**: this represents the day,month and year an order was carried out.
---
## TOOLS USED FOR ANALYSIS
For this project, i had to make use of Three(3) analytical tool. They are;
-  Microsoft Excel [Download Here](https://www.microsoft.com/en-us/microsoft-365) 
-  SQL Server [Download here](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
-  Microsoft Power BI [Download Here](https://www.microsoft.com/en-us/power-bi) 
--- 
## DATA PREPARATIONS
My first take on this dataset when i accessed it was to check for duplicates using Excel. I removed all the duplicates then also checked for any empty cells which there was none. After cleaning i carried out my analysis and also transferred the cleaned data to Sql and Power BI for further analysis
### EXCEL ANALYSIS
I used Excel Functions and Pivot Tables to carry out some of the following;
- Pivot tables was used to summarize total sales by product, region, and month.
- To know which goods was more dominant in the regions.
- To also Sum the Price for each products and to Know the Quantity of products sold in each regions.

![SD1](https://github.com/user-attachments/assets/828525d3-557e-4a35-9a4c-2a41bd35917e)

-  Excel Functions was carried out to know  average sales per product and total revenue by region.
-  I also wanted to know the Maximum and Minimum sales made.
-  I also used the MONTH function to extracts all the months orders were made in the Order date.

  ![Project Lita - Excel 03-Nov-24 11_19_17 PM](https://github.com/user-attachments/assets/07961e5c-91f1-448d-a97a-b2b8d17a525c)

### SQL QUERIES
i used Sql to run some queries to extract key insights to answer the following questions;
-  To retrieve the total sales for each product category
``` 
select sum (Sales) as TotalSalesperProduct, Product
from [dbo].[Sales Data]
group by Product
```
- To find the number of sales transactions in each region.
```
select count (Sales) as SalesCountbyRegion, Region
from [dbo].[Sales Data]
group by Region
```
- To find the highest-selling product by total sales value.
```
select Product, sum(Sales) as HighestSellingProducts
from [dbo].[Sales Data]
Group by Product
Order by 2 desc
```
- To calculate total revenue per product.
```
select sum (sales) as TotalRevenueperProduct, Product
from [dbo].[Sales Data]
group by Product
```
- To calculate monthly sales totals for the current year.
```
select Months_Text, sum(Sales) as MonthlySalesTotal
from [dbo].[Sales Data]
Where Years='2024'
Group by Months_Text 
Order by 2 desc
```
- To find the top 5 customers by total purchase amount.
```
select top 5 OrderID,
Sum(Sales) as Top5CustomersTotalpurchaseamount
from [dbo].[Sales Data]
Group by OrderID
Order by 2 desc
```
- To calculate the percentage of total sales contributed by each region.
  ```

  ```
- To identify products with no sales in the last quarter.
```

```
---
### DATA VISUALIZATION WITH POWER BI
I visualized the data by showing key trends in the company and to also derive insights from it.

![Project LITA 02-Nov-24 5_46_16 PM](https://github.com/user-attachments/assets/3180056d-3382-4c7e-97b7-9e08b703f633)

#### Insights Drawn
1. 


