
# Sales-Analysis-using-Power-BI

Refer link - https://app.powerbi.com/groups/me/reports/02b4cda0-820e-41c1-9c09-78014b8d9f88/ReportSection

We will create effective dashboard using Power BI with SQL integration, SQL helps to extraction of data from the data-warehouse which data engineers does there queries to manupulate the data in effective format. In SQL we can do analysis and proper data cleaning. Power BI is great tool to visualize our data in effective ways and its very easy to understand various sales trends per regions in india.


Problem statement:
  
The scenario of the project is business owner of hardware company wants to determine and evaluate the sales trends all over the Indian branches situated in different zones.
sales of hardware products are decreases per year from 2017. so, he wanted predict and describe the sales trends. They gather the data from owners of different branches.
They have the data in excel speadsheet and thats not efficient and easy to understand for that data analysis should be beneficial.
 
Power BI Dashboard:

![Uploading sales trends.jpg…]()

Data Analysis Using SQL
  
1) Show all customer records

SELECT * FROM customers;

2) Show total number of customers

SELECT count(*) FROM customers;

3) Show transactions for Chennai market (market code for chennai is Mark001

SELECT * FROM transactions where market_code='Mark001';

4) Show distrinct product codes that were sold in chennai

SELECT distinct product_code FROM transactions where market_code='Mark001';

5) Show transactions where currency is US dollars

SELECT * from transactions where currency="USD"

6) Show transactions in 2020 join by date table

SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;

7) Show total revenue in year 2020,

SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";

8) Show total revenue in year 2020, January Month,

SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");

9) Show total revenue in year 2020 in Chennai

SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.market_code="Mark001";

Data Analysis Using Power BI
 The company also provide there hardware products to out-off country have foreign customers.so, at some rows the sales amount are in USD. we should convert all USD currency into INR.
  
Formula to create norm_amount column
= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)
