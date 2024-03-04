QA Process:
Describe your QA process and include the SQL queries used to execute it.

Missing Data:

 I checked for missing or placeholder data in the city field. It's important because missing info here could really skew location-based insights. Here's how I spotted these gaps. I realized that without handling these, any analysis on geographical distribution would be off. So, planning to replace "(not set)" with something more analysis-friendly or maybe exclude them. 
 
```sql
SELECT COUNT(*) 
FROM public.all_sessions 
WHERE city IS NULL OR city = '' OR city = '(not set)';
```


Duplicate Data:

This helped me see how many sessions were counted more than once. I'm thinking of removing the extras to keep things accurate.

```sql
SELECT "visitId", COUNT(*) 
FROM public.all_sessions 
GROUP BY "visitId" 
HAVING COUNT(*) > 1;
```

Data Type Mismatches:

I found that some fields expected to be numeric had other stuff mixed in, like the productPrice. This is a big deal for any sort of pricing analysis or summing up sales.

```sql
SELECT "productPrice" 
FROM public.all_sessions 
WHERE "productPrice" !~ E'^\\d+$' LIMIT 10;
```
Inconsistent Data:

Noticed that product names weren't consistent — some had different capitalizations or extra spaces. This could really mess with trying to aggregate data by product. I'll need to standardize these names so that 'Product-A', 'product a', and 'Product A' are all recognized as the same product. I'll need to standardize these names so that 'Product-A', 'product a', and 'Product A' are all recognized as the same product.

```sql
SELECT DISTINCT "v2ProductName" 
FROM public.all_sessions 
WHERE LOWER("v2ProductName") = 'product a';
```
Outliers:

I looked into outliers in the timeOnSite data because they can dramatically skew averages and give a misleading picture of user engagement. Identifying these outliers helps me decide whether they represent genuine user behavior or if they're anomalies that should be excluded from certain analyses.

```sql
SELECT "timeOnSite" 
FROM public.all_sessions 
ORDER BY "timeOnSite" DESC LIMIT 5;
```
