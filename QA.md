Missing Data: As observed, there were instances of columns having NULL values, empty strings, or placeholders like "(not set)". 
These can potentially skew averages and other calculations if not handled correctly.

Duplicate Data: There could be duplicate entries in tables that could artificially inflate metrics.

Data Type Mismatches: Some columns may have mixed data types. For example, a column that is expected to contain only numeric values might have some text or other unexpected data.

Inconsistent Data: There could be inconsistencies in how data is recorded. For example, product names might be recorded differently in different rows (e.g., 'Product-A', 'product a', 'Product A').

Outliers: Outliers can significantly skew the average and other statistics. It's crucial to identify and understand them.


QA Process:
Describe your QA process and include the SQL queries used to execute it.

Handling Missing Data:

SELECT COUNT(*) 
FROM public.all_sessions 
WHERE city IS NULL OR city = '' OR city = '(not set)';

Checking for Duplicate Data:

SELECT "visitId", COUNT(*) 
FROM public.all_sessions 
GROUP BY "visitId" 
HAVING COUNT(*) > 1;

Data Type Validation:

SELECT "productPrice" 
FROM public.all_sessions 
WHERE "productPrice" !~ E'^\\d+$' LIMIT 10;

Data Consistency:

SELECT DISTINCT "v2ProductName" 
FROM public.all_sessions 
WHERE LOWER("v2ProductName") = 'product a';

Identify Outliers:

SELECT "timeOnSite" 
FROM public.all_sessions 
ORDER BY "timeOnSite" DESC LIMIT 5;
