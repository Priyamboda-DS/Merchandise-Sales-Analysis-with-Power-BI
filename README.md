# Merchandise-Sales-Analysis-with-Power-BI

Lee Chatmen is a popular influencer from the United States with over 7 million TikTok followers. He became famous for his entertaining videos, where he plays popular songs on miniature guitars. In 2023, Lee launched his own line of merchandise. 

This analysis looks at how his merchandise sales are going and what we can learn from the data.

## Data Description:

The data is in excel format with the following columns. There are 7394 rows of records. The data is pretty clean without any value error or any missing values.

![image](https://github.com/user-attachments/assets/f4307a19-1554-4668-ace0-d898339e5a04)

Data Source: Enterprise DNA

## Analysis, Steps followed and Codes used:

### Initial Steps:

1. Loaded the data to Power BI.
2. Verified the data for any possible data type error or missing values. There were none.
3. Changed the data type of 'Order Id' to text.
4. Created a new calendar table comprising all dates between the earliest and latest 'Order Date'.

### Progression of Analysis:

I had broken down the analysis into finding answers to certain questions. Such questions and related analysis will unfold below.
I have also given the steps followed or codes used to develop the related visualizations in Power BI.

### Q1. What is the trend of sales?

![1  Sales Trend](https://github.com/user-attachments/assets/f84cb91f-72fc-4385-b0a9-2e6c2dfbda78)

Findings:

1. Total sales is around 8.5K. Value wise almost 74% consists of Clothing, 18% Ornaments and 7% Other. But quantity wise only 49% is Clothing, 31% Ornaments and 20% Other. Obviously, that Clothings are highly priced compared to Ornaments and Other.
2. There is almost no diffrence in average sales volume over weekdays or weekends.
3. Top selling months were May and July followed by December and March. However, June has the deepest slump between two high grossing months.

*DAX used:*

*1. Sales last Month = CALCULATE([Total],DATEADD('Calendar'[Month],-1,MONTH))*

*2. Total = SUM(Data[Total Sales])*

*3. % Change over Last Month = if ([Sales last Month]<>0, ([Total] - [Sales last Month]) / [Sales last Month] , 0)*

### Q2. How are the performance of each product categories?

![2  Product Category Performance](https://github.com/user-attachments/assets/c1416926-d2a7-4de9-bf3f-89fa906c5465)

Findings:

1. The sales trend is almost flat over months for each product category.
2. Total sales follows the trend of sales as Clothing.

*DAX used:*

*1. % Change in Clothing Sales over last month = IF([Sales last Month]<>0, CALCULATE(([Total] - [Sales last Month]) / [Sales last Month],Data[Product Category]="Clothing"),0)*

    *- Same as above for Ornaments and Other.*
    
*2. % Change over Last Month = if ([Sales last Month]<>0, ([Total] - [Sales last Month]) / [Sales last Month] , 0)*

### What is the impact of price on sales?

![3  Price vs  Sales](https://github.com/user-attachments/assets/1c0a95a8-4c3b-4e0b-8f0a-7a36c2b01d8f)

Findings:

1. In this Price vs. Sales graph, the quantity sold and sales volumn- both have a downward trend with the increase in prices. The consumers seem to be quite price sensitive. 

### What is the most popular product?

![4  Product Popularity](https://github.com/user-attachments/assets/28ec02fb-bf86-4042-8424-6436668a95db)

Findings:

1. The product Clothing-BF1548 has highest amount of sales with medium price in the Clothing product category. It also has a medium average rating within its product category!
2. The product category Other has obtained the highest average rating and the maximum percentage of 'Good' ratings, although, there is no significant difference in the ratings received across all categories.

*DAX used:*

*1. % Good Rating = CALCULATE(DISTINCTCOUNT(Data[Order ID]),Data[Rating]>3)/DISTINCTCOUNT(Data[Order ID])*

*2. % Neutral Rating = CALCULATE(DISTINCTCOUNT(Data[Order ID]),Data[Rating]=3)/DISTINCTCOUNT(Data[Order ID])*

*3. % Bad Rating = CALCULATE(DISTINCTCOUNT(Data[Order ID]),Data[Rating]<3)/DISTINCTCOUNT(Data[Order ID])*

### What is the total sales by order location?

![5  Gross Sales by Order Location](https://github.com/user-attachments/assets/c05a9b68-9b59-49fb-bb95-8d85cbe2abdb)

Findings:

1. The city 'Sydney' provides the maximum revenue from sales in all product categories.
   However, Sydney is an overseas location, hence steep amount of shipping charges is applicable, which actually contributes to this high revenue.
   If we consider the net sales, which is the total revenue - Shipping Charges, the picture entirely changes. The inland cities now come out as leaders.

![5  Net Sales by Order Location](https://github.com/user-attachments/assets/e6f6abb1-1dbb-4f71-8d41-059cbc623b0d)

### What is the impact of Shipping Charges on Sales?

![6  Shipping Charges vs  Sales](https://github.com/user-attachments/assets/42dc2b52-c1ec-4486-b575-c1d58871001d)

Findings:

1. The basket value, which is the average sales per order, is higher in all product categories for overseas locations. This can be attributed to two things: i> high shipping charges which inflates the gross sales value by inflating the sales prices and ii> comparatively low number of orders from overseas locations.
2. The impact of shipping charges on sales is evidently clear from the Proportion of Gross and Net Sale w.r.t. International Shipping visual. We see the proportion of Gross Sales for inland and overseas sales is 55%:45%. Whereas, this proportion changes to 70%:30% when considered the net sales only.
3. From the last visual of Sales and Shipping Charges across international Locations, we find the 'Other' product catogory has the stippest Shipping Charges, as high as 90% to minimum 70% of the sales price depending on the overseas distance.
   This is followed by 'Ornaments'- almost 80% to 50% of sales prices and 'Clothing'- 53% to 22%.
   However, despite this humongous shipping charges, Sydney provides the highest revenue from sales. Sydney seems to hold quite a significant fan base for our Mr. Lee Chatmen!

### What is the demographic profile of the buyers?

![7  Demographic Profile of Buyers](https://github.com/user-attachments/assets/5e64bdd2-a21e-417a-b236-24032b34b408)

Findings:

1. The buyers are all youths, mostly falling in 20-34 age groups. Men are the primary buyers across all age groups.

### How do ratings and reviews correlate with sales?

![8  Ratings and Reviews vs  Sales](https://github.com/user-attachments/assets/e55cd6b3-3df7-4f0e-bd10-3f10fea319a9)

Findings:

1. The average sales is more or less same across ratings.
2. I have drawn a line chart of the average sales each month and the average ratings received till that month. However, as we see there is not much impact of ratings received on sales and this is trus for all product categories.

![8a  Clothing_Ratings and Reviews vs  Sales](https://github.com/user-attachments/assets/7b51532a-11c3-4695-a04d-6e7f1cf96ac8)
![8b  Ornaments_Ratings and Reviews vs  Sales](https://github.com/user-attachments/assets/636d2a13-48c3-44d3-b4f3-5e3ea248605a)
![8c  Other_Ratings and Reviews vs  Sales](https://github.com/user-attachments/assets/c3ea77cd-3d89-4387-844a-b11c5e43b7b1)
