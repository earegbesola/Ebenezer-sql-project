### 1.find all duplicate records:

`select product_name,count(*)as duplicate_record from  products group by product_name having count(*) >1`

There are no duplicate in the sales_by_sku Table (same number of record for both queries)

`select * from sales_by_sku`

`select distinct productsku from sales_by_sku`

### 2.find the total number of unique visitors (fullVisitorID)

Answer - 120018

` select count(distinct fullvisitorid) from analytics `

### 3.find the total number of unique visitors by referring sites 

Answer-18382

```select count(distinct fullvisitorid) from analytics where channelGrouping ='Referral'```


### 4.find each unique product viewed by each visitor 

Answer -471

```select distinct v2productname from all_sessions```

 ### 5.compute the percentage of visitors to the site that actually makes a purchase

 Answer-11 percent

```select(select count(distinct fullvisitorid ) from all_sessions)/(select count (distinct fullvisitorid) from analytics)*100 ```
