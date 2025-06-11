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

1. Total sales around 8.5K. sales value wise almost 74% consists of Clothing, 18% Ornaments and 7% Other. But quantity wise only 49% is Clothing, 31% Ornaments and 20% Other. Thus it is obvious that Clothings are highly prices compared to Ornaments and Other.
2. There is almost no diffrence in average sales volume over weekdays or weekends.
3. Top selling months were May and July followed by December and March. However, June has the deepest slump between two high grossing months.

DAX used:
1. Sales last Month = CALCULATE([Total],DATEADD('Calendar'[Month],-1,MONTH))
2. Total = SUM(Data[Total Sales])
3. % Change over Last Month = if ([Sales last Month]<>0, ([Total] - [Sales last Month]) / [Sales last Month] , 0)

