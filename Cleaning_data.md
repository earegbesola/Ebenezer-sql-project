In cleaning the data ,the following issues were addressed.
Reduntant data,data with inconsistent format,Duplicate data ,missing values ,outliers,Null records

Considering the products table:
-I checked for Null record , duplicate record  and standadized  data in the "sku" colunm as this was the primary key column

1. checking Null
select sku from products where sku is null

2.Assigning PK to SKU column
Alter Table Products
Add Primary Key(Sku)

2. checking for duplicate record in 'sku' by comparing distinct records with all records (both Querries have 1092 records meaning no duplicates in 'sku')
select * from products
select distinct sku from products

3.Renaming the "name" colunm  in the product table as "product_name".This was done considering best practice  since name is a keyword in SQL.
Alter table products
rename column name to product_name

4.Duplicate records in the product_name  were identified and i noticed there are 240 records with duplicate and 313 distinct product_name from the products table
select product_name ,count(* )as duplicate_products_count 
from products 
group by product_name having  count(* )>1 order by count(*)desc 

select distinct product_name from products 

5.The format for the data in the SKU column was like "GGOEGDHJ082599" but there ar e records formated like "9184681" which needed to be changed
select sku,product_name from products where sku not like 'GG%' order by product_name.

6. I updated the null values in sentimentscore and sentimentmagnitude with their  average values.
update products
set sentimentscore =(select avg(sentimentscore)from products)
where sentimentscore is null

update products
set sentimentmagnitude =(select avg(sentimentmagnitude)from products)
where sentimentmagnitude is null

7. currencycode in the all_sessions table is redundant so it was deleted.
select distinct currencycode from all_sessions
alter table all_sessions
drop column currencycode

8.Replacing city column with country data in the all_sessions table

select city,country,
case
when city like '%not%' or city like '(not set)'then country
when country like '%not%' or country like '(not set)' then 'Not available'
else city
end as city_new
from all_sessions
9 changing data type of integer to date in date column of all_sessions table.

ALTER COLUMN column_name datatype;

