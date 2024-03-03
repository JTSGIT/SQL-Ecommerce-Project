Question 1: What are the top channels driving traffic to the site?

SQL Queries:

SELECT "channelGrouping", COUNT(*) as number_of_sessions
FROM public.all_sessions
GROUP BY "channelGrouping"
ORDER BY number_of_sessions DESC;

Answer: The results will list the channels driving traffic to the site in descending order, indicating which channels are the most effective in bringing users to the site.

Question 2: Which products have the highest sentiment scores?

SQL Queries:

SELECT Name, "sentimentScore"
FROM public.products
WHERE "sentimentScore" IS NOT NULL
ORDER BY "sentimentScore" DESC
LIMIT 10;


Answer: 

USB wired soundbar - in store only
Men's Watershed Full Zip Hoodie Grey
 Stylus Pen w/ LED Light
 Mood Ninja Window Decal
 Onesie Heather
 G Noise-reducing Bluetooth Headphones
 Men's Watershed Full Zip Hoodie Grey
Metal Texture Roller Pen
 Women's Fleece Hoodie
 Toddler Short Sleeve Tee Red


Question 3: How does the stock level relate to the total ordered quantity for products?

SQL Queries:

SELECT p.sku, s.total_ordered
FROM public.products p
JOIN public.sales_report s
ON p.sku = s."productSKU"
ORDER BY s.total_ordered DESC;

Answer: The results will show the relationship between each product's SKU and its ordered quantity, offering insights into which products are ordered the most.



Question 4: Which cities contribute the most to the total transaction revenue?

SQL Queries: SELECT city, SUM("totalTransactionRevenue") as total_revenue
FROM public.all_sessions
WHERE "totalTransactionRevenue" IS NOT NULL
GROUP BY city
ORDER BY total_revenue DESC;

Answer: The results will list the cities in descending order of their total transaction revenue, highlighting which cities are the most lucrative markets for the business.



Question 5: Are there any patterns in user engagement metrics like pageviews, time on site, and bounces?

SQL Queries: 

SELECT 
    AVG(pageviews) as average_pageviews, 
    AVG("timeOnSite") as average_time_on_site
FROM public.all_sessions;


Answer:

Upon analyzing the all_sessions dataset, the following patterns in user engagement emerge:

Pageviews: Users, on average, view approximately 4.52 pages during a session. This indicates that users tend to explore multiple pages on the website, suggesting a certain depth to their browsing behavior.
Time on Site: The average time a user spends on the site is about 3.75 minutes (or 224.71 seconds). This suggests a moderate level of engagement with the site's content, possibly involving activities such as reading product details, comparing items, or interacting with site features.
