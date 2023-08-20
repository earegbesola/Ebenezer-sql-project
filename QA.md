
Identify and describe your risk areas:

The Data QA process is to ensure that data meets certain specific data standards and quality as this impact the quality of decision or insight derived from the data. 

The process should throw-up Data QA risk areas reflecting data quality characteristcs and standards including the following:

a.completeness:

There is the risk of  data in the tables being incomplete.example include having null values

b.Data consistency:

 example include data stored in differentv and wrong  formats in a table

c.Data Uniqueness and Validity: 

Some of the data in the tables may not be valid like storing integers as a text format  or having duplicate entries.

d.We could also be faced with the risk of Data accuracy.


The  QA process  executed was to basicaly test for the data quality characteristics to ensure that we address data quality risk areas identified .

This process was implemented using  the following  SQL queries :

1 Anomaly detection: 

To ensure data validity,I checked  for outliers ,null values  or ambiguous data like the unit_price  in the analytics table and displaying all records to review the different data types.

---select * from sales_report---

checking to see if primary Key column contain duplicates or null values.

---select(select count(distinct sku) from products) = (select count(sku) from products)
select count(sku) from products where sku is  null---


cheking to see where orderedQuanity exceeded stockLevel in the products table and sales_report

---select * from products
where orderedQuantity > stockLevel---

---select * from sales_report where 
total_ordered >stockLevel order by product_name---

2.consistency testing was done like checking the count of the unique products in the products table and comparing this with the sales_report table. 

---select(select count (distinct product_name )from products)>=
(select count(distinct product_name)from  sales_report)---


---select(select count(distinct sku) from products) = (select count(sku) from products)
select count(sku) from products where sku is  null---


3.Referential integrity test to see if relationships between two tables are properly maintained example:

---select(select count (distinct product_name )from products)>=
(select count(distinct product_name)from  sales_report)---

There are also statistical analysis test (calculating mean,median and mode of data colums)that can be done to reveal outliers in a data set in other  to acertain the quality of the data.



