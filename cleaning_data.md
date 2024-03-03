What issues will you address by cleaning the data?

**1. Handling Null Transaction Revenues:** 
- To ensure accurate financial analysis, we filter out or adjust records with null transaction values, improving data integrity for revenue calculations.

**2. Standardizing Data Types for Financial Analysis:** 
- Converting textual representations of numbers to numeric data types ensures that calculations and aggregations on financial figures are accurate and performance-optimized.

**3. Analyzing Traffic Sources:** 
- Understanding which channels contribute most to user sessions helps identify effective marketing strategies.

**4. Identifying Highly Rated Products:** 
- Highlighting products with the highest sentiment scores provides insights into customer preferences and product performance.

### Refined Queries

**Filter Out Null Transaction Values**
```sql
SELECT COUNT(*) 
FROM public.all_sessions 
WHERE "totalTransactionRevenue" IS NOT NULL;
```
*Purpose:* Identify the number of sessions with recorded transaction revenue to ensure subsequent analyses are based on complete financial data.

**Breakdown of Sessions by Channel**
```sql
SELECT "channelGrouping", COUNT(*) AS num_sessions 
FROM public.all_sessions 
GROUP BY "channelGrouping" 
ORDER BY num_sessions DESC;
```
*Purpose:* Determine which channels are driving the most traffic, highlighting successful marketing efforts.

**Set Default Value for Null Transaction Revenue**
```sql
UPDATE public.all_sessions 
SET "totalTransactionRevenue" = COALESCE("totalTransactionRevenue", '0');
```
*Purpose:* Replace null values in the transaction revenue column with 0 to simplify financial analysis.

**Convert Transaction Revenue to Numeric Type**
```sql
ALTER TABLE public.all_sessions 
ALTER COLUMN "totalTransactionRevenue" TYPE numeric 
USING "totalTransactionRevenue"::numeric;
```
*Purpose:* Ensure that the transaction revenue column uses a numeric data type for accurate financial computations.

**Top 10 Products by Sentiment Score**
```sql
SELECT Name, "sentimentScore" 
FROM public.products 
WHERE "sentimentScore" IS NOT NULL 
ORDER BY "sentimentScore" DESC 
LIMIT 10;
```
*Purpose:* List the top 10 products based on sentiment scores, indicating customer satisfaction and product reception.

**Join Products and Sales Report by SKU**
```sql
SELECT p.Name, s."productSKU", s.total_ordered
FROM public.products p
JOIN public.sales_report s ON p.sku = s."productSKU"
ORDER BY s.total_ordered DESC;
```
*Purpose:* Combine product and sales data to rank products by the quantity ordered, identifying best-sellers.

**Note:** The redundant query for channel grouping was removed for conciseness, and the incorrect LIMIT clause in the sentiment score query was corrected. Additionally, the query to select "productSKU" from `public.sales_report` was streamlined into the join operation for clarity and direct relevance to product performance analysis..
