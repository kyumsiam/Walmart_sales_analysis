# 🛒 Walmart_Sales_Analysis

# Walmart Sales & Business Performance Analysis using SQL

![](data:image/png;base64,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)

---

## Overview

This project analyzes Walmart sales transaction data using **SQL** to uncover key business insights related to **payment behavior, product performance, customer ratings, branch-wise activity, time-based sales patterns, and year-over-year revenue trends**.

The project focuses on solving real-world retail business problems and demonstrates practical SQL skills used in **data analytics and business intelligence**.

---

## Objectives

- Analyze payment methods and total quantity sold  
- Identify highest-rated product categories per branch  
- Determine busiest days for each branch  
- Evaluate rating trends across cities and categories  
- Calculate revenue and profit by category  
- Understand sales distribution across time shifts  
- Identify preferred payment methods by branch  
- Detect branches with declining year-over-year revenue  

---

## Dataset

The dataset represents **transaction-level Walmart sales data**.  
Each record corresponds to a single customer transaction.

### Key Attributes

- Branch and city  
- Product category  
- Payment method  
- Quantity purchased  
- Unit price and total sales  
- Profit margin  
- Customer rating  
- Transaction date and time  

---

## Schema

```sql
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

# Business Problems and Solutions

## Objective: Analyze payment methods and total quantity sold.

1. What are the different payment methods, number of transactions, and quantity sold?
``` sql 
SELECT 
    payment_method,
    COUNT(*) AS no_payments,
    SUM(quantity) AS no_qty_sold
FROM walmart
GROUP BY payment_method;
```
## Objective: Identify the highest-rated category in each branch.

2. Which product category has the highest average rating in each branch?
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
## Objective: Determine the busiest day for each branch.

3. Which day has the highest number of transactions per branch?
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
## Objective: Calculate total quantity sold per payment method.

4. How many items are sold using each payment method?
``` sql
SELECT 
    payment_method,
    SUM(quantity) AS no_qty_sold
FROM walmart
GROUP BY payment_method;
```
## Objective: Analyze customer ratings by city and category.

5. What are the average, minimum, and maximum ratings for each category in every city?
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
## Objective: Evaluate revenue and profit by category.

6. Which categories generate the highest revenue and profit?
``` sql
SELECT 
    category,
    SUM(total) AS total_revenue,
    SUM(total * profit_margin) AS profit
FROM walmart
GROUP BY category
ORDER BY profit DESC;
```
## Objective: Identify preferred payment methods by branch.

7. What is the most commonly used payment method in each branch?
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
## Objective: Analyze sales distribution across time shifts.

8. How do sales vary by time of day (Morning, Afternoon, Evening)?
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
## Objective: Identify branches with declining revenue year-over-year.

9. Which 5 branches have the highest revenue decrease from 2022 to 2023?
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
