# Final-Project-Transforming-and-Analyzing-Data-with-SQL

## Project/Goals
The primary objective of this project was to harness the power of SQL to analyze an e-commerce dataset. The dataset, consisting of user sessions, product details, sales reports, and more, offers a rich tapestry of information. Our goals included:

Understand the key traffic sources to the website.
Identify top-performing products based on sentiment and sales.
Analyze the relationship between stock levels and ordered quantities.
Gauge user engagement and behavior based on session metrics.

## Process
### Step 1: Data Cleaning
Before diving into the analysis, we first ensured data cleanliness and consistency.
This involved addressing missing values, potential errors, and inconsistencies within the dataset.

### Step 2: Crafting and Executing SQL Queries
To answer business-centric questions and derive insights, we crafted and executed a series of SQL queries.
These ranged from basic SELECT operations to complex JOINs that combined data from multiple tables.

## Results
The dominant channels that drive the most traffic to the site.
Products that are not only popular in terms of sales but also have high sentiment scores, indicating customer satisfaction.
Cities that contribute significantly to the overall transaction revenue.
Patterns in user engagement, helping understand areas of potential optimization.

## Challenges 
## Handling Null Values:
One of the most pervasive challenges faced during the analysis was handling null values across different datasets.
Columns like sentimentScore had missing values, which posed questions about data integrity and required careful consideration.
Deciding whether to impute these values, remove them, or simply acknowledge them during analysis was a pivotal decision.

## productSKU Confusion:
Initially, there was a misunderstanding regarding whether productSKU was a column name or a table name.
This resulted in errors during query execution and necessitated revisions to the SQL code.
Ensuring that table and column names were accurately referenced was crucial to obtaining valid results.

## Data Consistency Across Tables:
With data spread across multiple tables like products, sales_report, and others, ensuring consistent joins and avoiding duplication was vital.
The relationship between tables, especially when dealing with sku from the products table and corresponding columns in other tables, required meticulous attention.

## Interpreting Ambiguous Results:
At times, the results from certain queries presented ambiguous interpretations.
For instance, understanding the significance of a high sentiment score in the context of sales required a blend of data analysis and business understanding.

## Future Goals
Dive deeper into user segmentation to understand distinct customer behaviors and preferences.
Perform a time-series analysis to identify sales trends and seasonality effects.
Cross refrence all revunue data and compile into one column 
