What issues will you address by cleaning the data?





Queries:
SELECT COUNT(*)
FROM public.all_sessions
WHERE "totalTransactionRevenue" IS NOT NULL;
-- This filters out NULL transaction values.
SELECT "channelGrouping", COUNT(*) as num_sessions
FROM public.all_sessions
GROUP BY "channelGrouping"
ORDER BY num_sessions DESC;
--This query provides a breakdown of the number of sessions for each channel. Channels with higher session counts are driving more traffic to the site.
UPDATE public.all_sessions
SET "totalTransactionRevenue" = COALESCE("totalTransactionRevenue", '0');
--This query provides the average revenue generated per session, helping gauge the site's monetization effectiveness.
ALTER TABLE public.all_sessions
    ALTER COLUMN "totalTransactionRevenue" TYPE numeric USING "totalTransactionRevenue"::numeric;
--Converting textual numeric columns to appropriate numeric data types
SELECT "channelGrouping", COUNT(*) as num_sessions
FROM public.all_sessions
GROUP BY "channelGrouping"
ORDER BY num_sessions DESC;
--This query provides a breakdown of the number of sessions for each channel. Channels with higher session counts are driving more traffic to the site.
SELECT Name, "sentimentScore"
FROM public.products
WHERE "sentimentScore" IS NOT NULL
ORDER BY "sentimentScore" DESC
LIMIT 10
    FROM public.products
ORDER BY sentimentScore DESC
LIMIT 10;
--The result lists the top 10 products with the highest sentiment scores, indicating positive customer sentiment.

SELECT *
FROM information_schema.tables
WHERE table_name = 'productSKU';


SELECT *

FROM public.products p

         JOIN
     public.sales_report s
     ON p.sku = s."productSKU"

ORDER by s.total_ordered DESC;

SELECT "productSKU"
from public.sales_report
--This query joins the two tables based on the SKU and retrieves the SKU and total ordered quantity for each product, ordered by the quantity in descending order.
