Questions that the data can answer include:

1.The product with the highest  sales by volume.
"Ballpoint LED Light Pen" 

Answer: 456 

---select product_name,sum(total_ordered)total_orderd_byProduct,count(* )
from sales_report 
group by product_name 
order by sum(total_ordered) desc---

2.product sold with  the average least sentimentscore or negative perception/opinion by customers.

Answer :" Men's Vintage Henley"  with sentimentscore of -0.5

---select product_name,count(*),avg(sentimentscore) from sales_report 
group by product_name order by avg(sentimentscore)---

3.products not in stock/discontinued.

Answer: 171 unique products

---select  distinct product_name,stocklevel from products where stocklevel < 1---