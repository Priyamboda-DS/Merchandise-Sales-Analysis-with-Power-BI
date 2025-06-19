# Merchandise Sales Analysis with Power BI and Python


Lee Chatmen is a popular influencer from the United States with over 7 million TikTok followers. He became famous for his entertaining videos, where he plays popular songs on miniature guitars. In 2023, Lee launched his own line of merchandise. 

This analysis looks at how his merchandise sales are going and what we can learn from the data.


## Data Description:


The data is in excel format with the following columns. There are 7394 rows of records. The data is pretty clean without any value error or any missing values.

![image](https://github.com/user-attachments/assets/f4307a19-1554-4668-ace0-d898339e5a04)

Data Source: Enterprise DNA


## Key Findings:


1. Total revenue is 856K in one year, mostly driven by product category 'Clothing' which consists of 75% of total revenue.
2. Owing to the steep shipping charges, on average, the overseas consumers pay almost double the price as compared to domestic cunsumers. This difference in price brings down the order volume in overseas locations.
3. Despite this high price, almost 45% of revenue comes from overseas sales. This can be attributed to the popularity and fan base of Mr. Lee Chatmen as well as the unique design and quality of the products. The proprieters may consider local procurement maintaining the quality and design of the products to beat low order volume in overseas locations. 
4. The buyers are primarily youngsters in 20 to 35 age range.
5. Ratings and reviews do not have much impact on sales. Consumers have praised the quality and design of products but complained about delays in delivery and lack of care in handling. Overall sentiment of customer reviews are positive but not very optimistic.


### Analysis:


I had broken down the analysis into finding answers to certain questions. Such questions and related analysis will unfold below.
The visualizations to support the analysis and key DAX functions used to develop such visualizations in Power BI are also given there.


#### Initial Steps:


1. Loaded the data to Power BI.
2. Verified the data for any possible data type error or missing values. There were none.
3. Changed the data type of 'Order Id' to text.
4. Created a new calendar table comprising all dates between the earliest and latest 'Order Date'.
5. Created measures and columns using Power query or DAX functions as and when required.


#### Q1. What is the trend of sales?


![image](https://github.com/user-attachments/assets/3cd1cb6d-b7d8-4df7-9295-6244dc588a94)

*DAX used:*

*1. Sales last Month = CALCULATE([Total],DATEADD('Calendar'[Month],-1,MONTH))*

*2. Total = SUM(Data[Total Sales])*

*3. % Change over Last Month = if ([Sales last Month]<>0, ([Total] - [Sales last Month]) / [Sales last Month] , 0)*

Findings:

1. Product category 'Clothing' is the main contributor to total revenue.
2. Sales are consistent over weekdays or weekends and over months. 


### Q2. How are the performance of each product categories?


![image](https://github.com/user-attachments/assets/49016491-8d3e-41be-bd43-5a24f59eadfa)

*DAX used:*

*1. % Change in Clothing Sales over last month = IF([Sales last Month]<>0, CALCULATE(([Total] - [Sales last Month]) / [Sales last Month],Data[Product Category]="Clothing"),0)*

    *- Same as above for Ornaments and Other.*
    
*2. % Change over Last Month = if ([Sales last Month]<>0, ([Total] - [Sales last Month]) / [Sales last Month] , 0)*

Findings:

1. The sales trend is almost flat over months for each product category.
2. Total sales follows the trend of sales in Clothing.


### What is the impact of price on sales?


![image](https://github.com/user-attachments/assets/5ce724d1-7346-43ab-a29f-3460ad96cea8)

Findings:

1. Both sales volume and revenue go down with the increase in prices. The consumers are price sensitive. 


### What is the most popular product?


![image](https://github.com/user-attachments/assets/df4b7b0f-4b4a-4109-9699-26b0f16b9a17)

*DAX used:*

*1. % Good Rating = CALCULATE(DISTINCTCOUNT(Data[Order ID]),Data[Rating]>3)/DISTINCTCOUNT(Data[Order ID])*

*2. % Neutral Rating = CALCULATE(DISTINCTCOUNT(Data[Order ID]),Data[Rating]=3)/DISTINCTCOUNT(Data[Order ID])*

*3. % Bad Rating = CALCULATE(DISTINCTCOUNT(Data[Order ID]),Data[Rating]<3)/DISTINCTCOUNT(Data[Order ID])*

Findings:

1. The product Clothing-BF1548 provides highest revenue with medium price in 'Clothing' category.
2. The average ratings are around 3.5 across all product categories; ratings do not impact popularity.
3. The product category 'Other' has obtained the highest average rating and the maximum percentage of 'Good' ratings.


### What is the total sales by order location?


![image](https://github.com/user-attachments/assets/810f81fe-8e00-4210-9fdf-52ea8352f56a)

![image](https://github.com/user-attachments/assets/8ee68e2b-cc9e-4314-a740-81216a030779)

Findings:

1. Revenue from overseas locations are comparable to that from inland locations despite order volume being half of the same from within country.
2. Consider net sales (deducting shipping charges from revenue) and the sales volume from international locations goes down to half the same from inland locations.


### What is the impact of Shipping Charges on Sales?


![image](https://github.com/user-attachments/assets/ba25c4f3-4d8b-46e3-a3e9-479a8a375718)

![image](https://github.com/user-attachments/assets/ee0b322c-d244-46a5-b368-b78cb5545d13)

Findings:

1. The price and consequently revenue are hugely inflated by Shipping Charges. The international customers pay almost double the price for same product.
2. The product catogory 'Other' has the stippest Shipping Charges, between 90% to 70% of the sales price depending on the overseas distance. This is followed by 'Ornaments'- almost 80% to 50% and 'Clothing'- 53% to 22% of sales prices.


### What is the demographic profile of the buyers?


![image](https://github.com/user-attachments/assets/98acb7f6-d45d-4867-89a8-449f3a7ea384)

Findings:

1. The buyers are all youths, mostly falling in 20-34 age groups. Men are the primary buyers across all age groups and locations.


### How do ratings and reviews correlate with sales?


![8  Ratings and Reviews vs  Sales](https://github.com/user-attachments/assets/e55cd6b3-3df7-4f0e-bd10-3f10fea319a9)

![8a  Clothing_Ratings and Reviews vs  Sales](https://github.com/user-attachments/assets/7b51532a-11c3-4695-a04d-6e7f1cf96ac8)

![8b  Ornaments_Ratings and Reviews vs  Sales](https://github.com/user-attachments/assets/636d2a13-48c3-44d3-b4f3-5e3ea248605a)

![8c  Other_Ratings and Reviews vs  Sales](https://github.com/user-attachments/assets/c3ea77cd-3d89-4387-844a-b11c5e43b7b1)

*The WordCloud images and sentiment analysis are done using Python. The Python file is attached with this analysis.*

Findings:

1. The average sales is almost same across ratings.
2. I have drawn a line chart of the average sales each month and the average ratings received till that month. However, as we see there is not much impact of ratings received on sales and this is true for all product categories.

![WordCloudImage_removing delivery team and greatly appreciated](https://github.com/user-attachments/assets/d69f0157-7b86-4530-a85c-eff3dc39330b)

3. Product category 'Clothing' and 'Ornaments' feature more negative words like 'delay' and 'lack'. Whereas, product category 'Other' shows some good words like 'major positives','excellent quality','great design', 'delivered quickly' etc. This also corroborates with the highest %age of 'Good' rating product category 'Other' received over other product categories.

![image](https://github.com/user-attachments/assets/e7e6711d-e299-42a2-9ae1-b5af833d63b7)

4. The sentiment analysis of the review comments reveal the mean polarity values of all product categories range between 0.15 to 0.2, which indicates sentiments being slightly positive, however not very optimistic. 


### What are the trends in shipping charges?


![9  Trend in Shipping Charges](https://github.com/user-attachments/assets/f85e4de5-485f-470e-b35e-e545965227e8)

*DAX used:*

*1. International Sales = CALCULATE(sum(Data[Total Sales]),Data[International Shipping]="Yes")*

Findings:

1. Shipping Charges are same for all product categories for a particular overseas location.
2. Total shipping charges across locations remained flat over months.


### Are there any patterns in repeat purchases?


![10  Repeat Purchase](https://github.com/user-attachments/assets/617c71e5-9fcd-4470-98aa-d2a34b7908ee)

*DAX used:*

*1. Order frequency per week = (DISTINCTCOUNT(Data[Order ID])/(MAX(Data[Order Date]) - MIN(Data[Order Date])))*7*


### Key Influencers:


![image](https://github.com/user-attachments/assets/de55139f-c801-4e57-9004-9e4033147d62)
![image](https://github.com/user-attachments/assets/52a7c7fe-fd15-4d4c-a1e3-70d25d219ac0)
![image](https://github.com/user-attachments/assets/9807023f-9199-4966-bfd4-a26270e4573e)


### Decomposition Tree:


![image](https://github.com/user-attachments/assets/0d06ab55-ee45-403d-b79b-a70ecd6cbc17)




