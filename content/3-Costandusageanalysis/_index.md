---
title : "Analysis of cost and usage performance"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 3. </b> "
---

#### Cost and performance analysis

In this part, we will analyze the system's performance using **SQL** queries. Use of **Amazon Athena** will be charged when you query, based on the amount of scanned data ( **scan** ) which is monthly recorded data and the file is in **parquet format**. This data has been compressed and fragmented to reduce costs when using **Amazon Athena**. However, the query should still limit the number of records returned with the **limit keyword** at the end of the statement.

#### Some basic SQL statements

- **SQL SELECT statement**: SELECT is used to select data from the database. The returned data is stored in a result table.

- **SQL SELECT DISTINCT statement**: SELECT DISTINCT is used to return distinct (different) values. Inside a table, a column often contains many duplicate values; and sometimes you just want to list different (separate) values.

- **WHERE clause in SQL**: WHERE clause is used to filter records. It is only used to extract those records that meet a specific condition.

- **SQL statement GROUP BY**: GROUP BY is used to group rows with the same value into summary rows.

- **SQL statement ORDER BY**: ORDER BY is used to sort the result set in ascending or descending order.

- **SQL LIKE operator**: The LIKE operator is used in a WHERE clause to search for a specific pattern in a column.

- **LIMIT keyword**: limit the number of records returned

#### Content

1. [Study the data in the table](3.1-datainthetable)
2. [Cost Study](3.2-cost)
3. [Tagging and Cost Allocation](3.3-taggingandcost)
4. [Savings Plans, Reserved Instance, On-Demand and Spot Usage](3.4-usage)