---
title : "Data in the Table"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 3.1 </b> "
---

{{% notice tip %}}
Note: For the convenience of testing, you can copy the query commands. Replace our data table with your respective table name. For each command, we just need to copy it into the query window and then click the **Run** button.

{{% /notice %}}

#### Data in the Table

1. We perform the query **data 10 records do not overlap** located in the table **line_item_line_item_description**

```
SELECT distinct "line_item_line_item_description"
FROM "costmaster"."monthly_report"
LIMIT 10;
```

- Select **Run**

![Data in the table](/images/3-Costandusageanalysis/3.1-Datainthetable/0001-datainthetable.png?featherlight=false&width=90pc)

2. Result after query

![Data in the table](/images/3-Costandusageanalysis/3.1-Datainthetable/0002-datainthetable.png?featherlight=false&width=90pc)

3. Do a **query 10 records** where the column value **line_item_line_item_type** is **Usage**

```
SELECT * FROM "costmaster"."monthly_report"
WHERE "line_item_line_item_type" like '%Usage%'
LIMIT 10;
```

![Data in the table](/images/3-Costandusageanalysis/3.1-Datainthetable/0003-datainthetable.png?featherlight=false&width=90pc)

4. Query results returned

![Data in the table](/images/3-Costandusageanalysis/3.1-Datainthetable/0004-datainthetable.png?featherlight=false&width=90pc)

5. Show **duplicate payment times** in the datasheet

```
SELECT distinct bill_billing_period_start_date
FROM "costmaster"."monthly_report"
LIMIT 10;
```

![Data in the table](/images/3-Costandusageanalysis/3.1-Datainthetable/0005-datainthetable.png?featherlight=false&width=90pc)

6. Query results returned. Monthly payment results.

![Data in the table](/images/3-Costandusageanalysis/3.1-Datainthetable/0006-datainthetable.png?featherlight=false&width=90pc)