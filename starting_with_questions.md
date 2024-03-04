Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:
```sql
SELECT city, country, SUM("totalTransactionRevenue") as total_revenue
FROM public.all_sessions
WHERE "totalTransactionRevenue" IS NOT NULL
GROUP BY city, country
ORDER BY total_revenue DESC
LIMIT 10;
```

Answer:
not available in demo dataset,United States,6092560000
San Francisco,United States,1564320000
Sunnyvale,United States,992230000
Atlanta,United States,854440000
Palo Alto,United States,608000000
Tel Aviv-Yafo,Israel,602000000
New York,United States,530360000
Mountain View,United States,483360000
Los Angeles,United States,479480000
Chicago,United States,449520000




**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:
```sql
SELECT city, country, AVG(CAST("productQuantity" AS FLOAT)) as average_ordered
FROM public.all_sessions
WHERE "productQuantity" IS NOT NULL AND "productQuantity" <> ''
GROUP BY city, country
ORDER BY average_ordered DESC;
```



Answer:
not available in demo dataset,United States,10.583333333333334
Madrid,Spain,10
Salem,United States,8
Atlanta,United States,4
Houston,United States,2
New York,United States,1.1666666666666667
Dallas,United States,1
Detroit,United States,1
Dublin,Ireland,1
Columbus,United States,1
Los Angeles,United States,1
Chicago,United States,1
Mountain View,United States,1
(not set),United States,1
Palo Alto,United States,1
Bengaluru,India,1
San Francisco,United States,1
San Jose,United States,1
Seattle,United States,1
Sunnyvale,United States,1
not available in demo dataset,Argentina,1
not available in demo dataset,Canada,1
not available in demo dataset,Colombia,1
not available in demo dataset,Finland,1
not available in demo dataset,France,1
not available in demo dataset,Mexico,1
Ann Arbor,United States,1





**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:
```sql
SELECT city, country, "v2ProductCategory", COUNT("v2ProductCategory") as category_count
FROM public.all_sessions
WHERE city <> '(not set)' AND country <> '(not set)'
GROUP BY city, country, "v2ProductCategory"
ORDER BY city, country, category_count DESC
LIMIT 10;
```

Answer:
Adelaide,Australia,Home/Apparel/Men's/Men's-Outerwear/,1
Ahmedabad,India,Home/Shop by Brand/YouTube/,5
Ahmedabad,India,Home/Shop by Brand/Google/,2
Ahmedabad,India,(not set),1
Ahmedabad,India,Home/Apparel/Men's/Men's-T-Shirts/,1
Ahmedabad,India,Home/Accessories/,1
Ahmedabad,India,Home/Bags/,1
Ahmedabad,India,Home/Apparel/Men's/Men's-Outerwear/,1
Akron,United States,Home/Apparel/Men's/,1
Alexandria,Egypt,Home/Apparel/Men's/Men's-T-Shirts/,1





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:
```sql
SELECT city, country, "v2ProductName", COUNT("v2ProductName") as product_count
FROM public.all_sessions
GROUP BY city, country, "v2ProductName"
ORDER BY product_count DESC
LIMIT 10;
```


Answer:

not available in demo dataset,United States,Google Men's 100% Cotton Short Sleeve Hero Tee White,84
not available in demo dataset,United States,22 oz YouTube Bottle Infuser,75
not available in demo dataset,United States,YouTube Twill Cap,56
not available in demo dataset,United States,YouTube Men's Short Sleeve Hero Tee Black,56
not available in demo dataset,United States,YouTube Leatherette Notebook Combo,55
not available in demo dataset,United States,YouTube Custom Decals,55
not available in demo dataset,United States,YouTube Men's Short Sleeve Hero Tee Charcoal,50
not available in demo dataset,United States,Google Men's 100% Cotton Short Sleeve Hero Tee Black,48
not available in demo dataset,United States,Google Men's 100% Cotton Short Sleeve Hero Tee Navy,44
not available in demo dataset,United States,Galaxy Screen Cleaning Cloth,42




**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:
```sql
SELECT city, country, SUM("totalTransactionRevenue")::FLOAT as total_revenue
FROM public.all_sessions
GROUP BY city, country
ORDER BY total_revenue DESC;
```

Answer:

not available in demo dataset,United States,6092560000
San Francisco,United States,1564320000
Sunnyvale,United States,992230000
Atlanta,United States,854440000
Palo Alto,United States,608000000
Tel Aviv-Yafo,Israel,602000000
New York,United States,530360000
Mountain View,United States,483360000
Los Angeles,United States,479480000
Chicago,United States,449520000







