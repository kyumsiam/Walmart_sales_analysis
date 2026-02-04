# Walmart_sales_analysis

Walmart_Sales_Analysis
Walmart Sales & Business Performance Analysis using SQL

# Overview

This project analyzes Walmart sales transaction data using SQL to uncover key business insights related to payment behavior, product performance, customer ratings, branch-wise activity, time-based sales patterns, and year-over-year revenue trends.

The analysis focuses on solving real-world retail business problems that support data-driven decision-making for operations, marketing, and revenue optimization.

# Objectives

-Analyze payment methods and quantity sold

-Identify top-rated product categories per branch

-Determine busiest days for each branch

-Evaluate rating performance across cities and categories

-Calculate revenue and profit by category

-Understand customer behavior across time shifts

-Identify preferred payment methods by branch

-Detect branches with declining revenue year-over-year

Dataset

The dataset represents transactional-level sales data from Walmart stores.
Each record corresponds to a single customer transaction.

Key attributes include:

Branch and city information

Product category and quantity

Payment method

Customer rating

Transaction date and time

Revenue and profit margin
``` sql
Schema
CREATE TABLE walmart (
    branch VARCHAR(10),
    city VARCHAR(50),
    category VARCHAR(50),
    payment_method VARCHAR(20),
    quantity INT,
    unit_price NUMERIC,
    total NUMERIC,
    profit_margin NUMERIC,
    rating NUMERIC,
    date VARCHAR(20),
    time VARCHAR(20)
);
```

Business Problems and Solutions
Objective: Analyze payment methods and total quantity sold.

What are the different payment methods, number of transactions, and quantity sold?
``` sql 
SELECT 
    payment_method,
    COUNT(*) AS no_payments,
    SUM(quantity) AS no_qty_sold
FROM walmart
GROUP BY payment_method;
```
Objective: Identify the highest-rated category in each branch.

Which product category has the highest average rating in each branch?
``` sql
SELECT *
FROM (
    SELECT 
        branch,
        category,
        AVG(rating) AS avg_rating,
        RANK() OVER(PARTITION BY branch ORDER BY AVG(rating) DESC) AS rank
    FROM walmart
    GROUP BY branch, category
)
WHERE rank = 1;
```
Objective: Determine the busiest day for each branch.

Which day has the highest number of transactions per branch?
``` sql
SELECT *
FROM (
    SELECT 
        branch,
        TO_CHAR(TO_DATE(date, 'DD/MM/YY'), 'Day') AS day_name,
        COUNT(*) AS no_transactions,
        RANK() OVER(PARTITION BY branch ORDER BY COUNT(*) DESC) AS rank
    FROM walmart
    GROUP BY branch, day_name
)
WHERE rank = 1;
```
Objective: Calculate total quantity sold per payment method.

How many items are sold using each payment method?
``` sql
SELECT 
    payment_method,
    SUM(quantity) AS no_qty_sold
FROM walmart
GROUP BY payment_method;
```
Objective: Analyze customer ratings by city and category.

What are the average, minimum, and maximum ratings for each category in every city?
``` sql
SELECT 
    city,
    category,
    MIN(rating) AS min_rating,
    MAX(rating) AS max_rating,
    AVG(rating) AS avg_rating
FROM walmart
GROUP BY city, category;
```
Objective: Evaluate revenue and profit by category.

Which categories generate the highest revenue and profit?
``` sql
SELECT 
    category,
    SUM(total) AS total_revenue,
    SUM(total * profit_margin) AS profit
FROM walmart
GROUP BY category
ORDER BY profit DESC;
```
Objective: Identify preferred payment methods by branch.

What is the most commonly used payment method in each branch?
``` sql
WITH cte AS (
    SELECT 
        branch,
        payment_method,
        COUNT(*) AS total_trans,
        RANK() OVER(PARTITION BY branch ORDER BY COUNT(*) DESC) AS rank
    FROM walmart
    GROUP BY branch, payment_method
)
SELECT *
FROM cte
WHERE rank = 1;
```
Objective: Analyze sales distribution across time shifts.

How do sales vary by time of day (Morning, Afternoon, Evening)?
``` sql
SELECT
    branch,
    CASE 
        WHEN EXTRACT(HOUR FROM (time::time)) < 12 THEN 'Morning'
        WHEN EXTRACT(HOUR FROM (time::time)) BETWEEN 12 AND 17 THEN 'Afternoon'
        ELSE 'Evening'
    END AS day_time,
    COUNT(*) AS total_invoices
FROM walmart
GROUP BY branch, day_time
ORDER BY branch, total_invoices DESC;
```
Objective: Identify branches with declining revenue year-over-year.

Which 5 branches have the highest revenue decrease from 2022 to 2023?
``` sql
WITH revenue_2022 AS (
    SELECT 
        branch,
        SUM(total) AS revenue
    FROM walmart
    WHERE EXTRACT(YEAR FROM TO_DATE(date, 'DD/MM/YY')) = 2022
    GROUP BY branch
),
revenue_2023 AS (
    SELECT 
        branch,
        SUM(total) AS revenue
    FROM walmart
    WHERE EXTRACT(YEAR FROM TO_DATE(date, 'DD/MM/YY')) = 2023
    GROUP BY branch
)
SELECT 
    ls.branch,
    ls.revenue AS last_year_revenue,
    cs.revenue AS current_year_revenue,
    ROUND(
        (ls.revenue - cs.revenue)::NUMERIC / ls.revenue::NUMERIC * 100,
        2
    ) AS revenue_decrease_ratio
FROM revenue_2022 ls
JOIN revenue_2023 cs
ON ls.branch = cs.branch
WHERE ls.revenue > cs.revenue
ORDER BY revenue_decrease_ratio DESC
LIMIT 5;
```

# Findings and Conclusion

Payment preferences differ significantly across branches

Certain product categories consistently receive higher customer ratings

Branch activity varies strongly by day of the week

Time-of-day analysis helps optimize staffing and inventory planning

Some branches experienced notable revenue decline year-over-year

Category-level profit analysis highlights high-margin product groups

This project demonstrates practical SQL skills including aggregations, window functions, CTEs, and time-based analysis, making it suitable for data analyst and business intelligence portfolios.
