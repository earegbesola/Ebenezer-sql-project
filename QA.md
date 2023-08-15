
Identify and describe your risk areas:

The following Data QA risk areas are identified and these can ultimately result in bad decisions  or insights derived from the data.
incomplete data in the tables : checking tables for empty values
Duplicate data: Identifying dublicate records
inconsistency in the data format : looking for inconsistencies in data types eg integer for time/date
Wrong and ambigous data: 


The  QA process  executed was to address the risk areas identified with the following  SQL queries used to implement
the QA process :

1. Anomaly detection: checking for outliers  or ambiguos data like the unit_price  in the analytics table and displaying all records to review the different data types



2.consistency testing was done like checking the count of the unique products in the products table and comparing this with the sales_report table.

select(select count (distinct product_name )from products)>=
(select count(distinct product_name)from  sales_report)

cheking to see where orderedQuanity exceeded stockLevel in the products table and sales_report
select * from products
where orderedQuantity > stockLevel

select * from sales_report where 
total_ordered >stockLevel order by product_name

checking to see if primary Key column contain duplicate or null values.

select(select count(distinct sku) from products) = (select count(sku) from products)
select count(sku) from products where sku is  null