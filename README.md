# Capstone of an Online Sales Retailer

### An Analysis of Overall Retail Performance and Sales Patterns of an Online Sales Retailer 

![Screenshot of Intro](https://i.imgur.com/iMgQaNl.png)
![Screenshot of dashboard](https://i.imgur.com/k8jHib2.png)

[Link to dataset](https://www.kaggle.com/datasets/yusufdelikkaya/online-sales-dataset/data?select=online_sales_dataset.csv)

### Description of dataset
This online sales dataset used in this capstone is extracted from kaggle.com. it consists of past sales performance over the last 5 years from 2018 to 2023 with information on its total orders, sales, shipping costs, returns from over 12 countries across Europe, including US and Australia. The dataset comprise of close to 50,000 records.

The initial discoveries of the dataset were observed:

1. Size of the dataset is 49,782 rows by 17 features
2. InvoiceDate feature was not stored in the correct data type
3. Discount feature has too many decimal points and,
4. some discount values recorded were over 1 which means is more than 100% discount which is highly likely to be recorded   wrongly.
5. negative values were also observed in about 10% of the records in Quantity and UnitPrice features and,
6. Typo error was observed in one distinct repetitive record in PaymentMethod. Paypall
7. CustomerID has null values which I believe is resulted from purchases by customers who are guests and did not sign up any account with us.
8. There are improper recordings in ShippingCost as well as WarehouseLocation which has resulted in some null values in them.
9. The recorded sales were registered for the time period between 2020 to 2025 which is probably an error as it is not possible to store 2024 and 2025 records when the period is not over or even started yet.

*Description of Dashboard*
The dashboard mainly focuses on the overall sales performances over amount sales orders that were placed during the time period visialized by the breakdown by Countries and Product Categories. The dataset lacks more information on the total actual costs such as the product purchase/manufacturing costs to reflect actual net profits from the overall gross sales.

### Insights
1. Lowest sales recorded was in Feb 2020 at $812k
2. Highest sales recorded was in Nov 2018 at $956k
3. Best performing country is Belgium with overall sales at $5.35m with UK close behind at $5.33m.
4. Sales distribution seemed very evenly distributed over time period, by location country, by products and almost any other features which is quite unusual in a real-life situation, suggesting that this dataset is most likely synthetic.

### Data Transformation in Jupyter
1. InvoiceDate datatype was corrected to date dtype
2. Negative and over 1 values in Discount feature were corrected to positive and capped at 1. (dilemma to handle over 1 values) remove records or to cap them? 
3. Discount values were also rounded up to 2 decimal places for better readability.
4. Paypall was changed to PayPal in PaymentMethod feature.
5. Changed null values in CustomerID to 0 to retain guest purchase records. CustomerID datatype was also changed to Int after removing all .0 values in all the records as it was redundant.
6. Missing values in ShippingCost was replaced with a median value as the next best closest fit.
7. Missing values in WarehouseLocation is replaced with Unknown.
8. All sales records timeline was shifted 2 years backwards to display the correct timeline. 2018 to 2023
9. Created additional features Sales and Sales_Discounted that is derived from:
  a)	Quantity x UnitPrice
  b)	Quantity x UnitPrice less discount
10. Created Year, Quarter and Month column from InvoiceDate column

### Further Data Transformation in Power BI using Power Query
1. Datatypes for Sales, Sales_Discounted, UnitPrice, ShippingCost, Discount were changed to currency and % dtype for better readability and understanding.
2. Category column is not being categorized properly against Description which labels the products that was sold online. To fix this, a new column was created to realign the correct Category that the products should be under using conditional formatting
3. With this, a product category hierarchy can be created.
4. An additional MonthNum column need to be created to correctly display the months correctly in calendar order instead of alphabetical asc or desc order.
5. A Timeline hierarchy was also created.
6. I wanted to compare % change of Sales YOY, therefore new measurement using DAX formula. 
7. For this DAX formula, I needed a calendar time column. So I created a new Calendar Table that will help me with this. From the model view, a many-to-one relationship need to be established in a single direction from CalendarDate Table to Online Sales Table.
8. InvoiceDate column needs to be reformulated so that all invoice dates are correctly captured against the calendar date slicer which has been adjusted to 2018 to 2023. And so a new Corrected_InvoiceDate column was created to fix this issue.

### Dataset Preparation Tools
To prepare for this analysis, 2 main tools were used:
1. Jupyter Notebook: provided a quick overview and understanding of the raw extracted dataset and perform the initial steps of data cleansing and transformation
2. Power BI: further data cleansing and transformation using power query was performed as more normalisation of the data were required and new measures & a calendar table were created to provide more meaningful insights discoveries.


[Link to my LinkedIn](https://www.linkedin.com/in/stephen-loh-8baa3068/)
