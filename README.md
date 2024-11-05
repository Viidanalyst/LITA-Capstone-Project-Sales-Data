# LITA-Capstone-Project-Sales-Data
---
## PROJECT TITLE: SALES DATA
---
## DATA SOURCE
- This data was provided by The Incubator Hub
---
## PROJECT OVERVIEW
This project contains the Sales trend of a company within a year. The aim of this project is to get insights into the sales trends of the company, to see the Top performing Product , the Region that generated the most revenue etc and to profer solutions to when needed. This Project contains both Qualitative and Quantitative data.

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
  Select Region, Sum(Sales)/Sum(quantity*UnitPrice)*0.1 As PercentageOfTotalSales
  From [dbo].[Sales Data]
  Group by Region
  Order by PercentageOfTotalSales
  ```
- To identify products with no sales in the last quarter.
```
Select Product, Sum(Quantity) As Sales
from [dbo].[Sales Data]
Where Month(OrderDate) Between 10 and 12
Group by Product
Having Sum(Quantity)=0
```
---
### DATA VISUALIZATION WITH POWER BI
I visualized the data by showing key trends in the company and to also derive insights from it.

![Project LITA 02-Nov-24 6_02_47 PM](https://github.com/user-attachments/assets/6fab23e6-8b31-4ee8-ad52-e965a991d6ba)


#### Insights Drawn
1. The total sales generated for the trading year is 2,102,035, with a count of 7 products. The total quantity of products sold sums up to 68,497.
2. The Shoes product generated the most sales with a total of 613,440, followed by the Shirt product with a total of 486,080. The Socks product made the lowest sales with a total of 180,800. This divulges that more quantity of shoes should be produced, since it is the most sought after.
3. The Southern region generated the highest sales with a total of 928,020, the West region generated the least sales with a total of 300,420. It should be looked into on why sales is not booming in the Western region.
4. In the Product category, Hats has the most quantity of goods purchased with a total of 15,963. This implies that the hat product is the most sought after, even if it did not generated the most revenue due to its price.
5. The Southern Region has the highest quantity of goods purchased with a total of 24,306 and a 35% total. This explains why they have the most revenue generated.
6. The Price of Shoes in the product category tops the chart when summed up with a total of 69,555. This explains why Shoes generated the most revenue even though it did not have the most quantity purchased.
7. The Month of Febraury generated the most sales with a total of 546,300, followed by the Month of July with a total of 275,280. The least sales was generated in the Month of September with a toal of 34,790.
---
#### DASHBOARD WITH APPLIED SLICER
I applied a slicer which contains the Months order were made. I decided to show the Month with the Highest Revenue and the Month with the Lowest Revenue. 
##### DASHBOARD FOR THE MONTH OF FEBRUARY

![Project LITA 05-Nov-24 12_18_30 PM](https://github.com/user-attachments/assets/0ff6b66b-3d01-498d-9d13-6c6be05680e9)

##### Insights
The Month of February is shown in the applied slicer above. It shows that The Most Sales were made in February with a total of 546,300. The Revenue was generated through the Sales of Shoes all of the sales were made in the Southern Region with a quantity of 9,930 goods sold. The highest quantity of shoes purchased is 10.

##### DASHBOARD FOR THE MONTH OF SEPTEMBER

![Project LITA 05-Nov-24 12_11_29 PM](https://github.com/user-attachments/assets/0fd8c8d8-27f5-403e-9dfe-f8040fcbcd23)

##### Insights
The Month of September is shown in the applied slicer above. It shows that the Least Sales were made in September with a total of 34,790. The Revenue was generated through the sales of Hat and all the sales were made in the Northern Region with a quantity of 3,479. The highest quantity of hat purchased is 7.

---
## GENERAL CONCLUSIONS
The analysis of this dataset has shown the various trends and pattern of sales in this company as it was the aim. In order to generate more sales in the coming year some solutions will be profered;

- There should be a customer awareness to know what the customers want to see in the market. For Instance, we can see that the sales of shooes generated the most revenue so, shoes should be produced in higher quantity whilst maintaining its price an quality.
- A proper research should be conducted in the Western Region where low sales were made to know why i was so. Initiate customers in a conversation to know what products they would love to see in their region, that way the company will know what to send to that region.
- Since Socks made the lowest sales, the quantity to be produced in the coming year should be minmal so as to not run into a loss if it is not purchased by customers.
- The goal is to always make more Sales, so the company should look into more PR and advertising that will get to their target audience. Also look into giving discount and promos that will enhance publicity, because if customer see a product with discount they are most likely to purchase such product in more quantity.
- Finally, Sales should be made in all Regions and in all Months, so the company should make sure their goods are well distributed in all regions every month.
