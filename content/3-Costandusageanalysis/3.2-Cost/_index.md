---
title : "Cost"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 3.2 </b> "
---

For effective optimization, it would be nice to be able to look at the top costs by various categories such as **services, descriptions and tags.**

1. Show **Top 10 Most Expensive Account ID**

```
SELECT "line_item_usage_account_id",
round(sum("line_item_unblended_cost"), 2) as cost
FROM "costmaster"."monthly_report"
GROUP BY "line_item_usage_account_id"
ORDER BY cost desc
LIMIT 10;
```

![Cost](/images/3-Costandusageanalysis/3.2-Cost/0001-cost.png?featherlight=false&width=90pc)

2. Query results returned

![Cost](/images/3-Costandusageanalysis/3.2-Cost/0002-cost.png?featherlight=false&width=90pc)

3. Show **Top10 Most Expensive Services**

```
SELECT "line_item_product_code",
round(sum("line_item_unblended_cost"), 2) as cost
FROM "costmaster"."monthly_report"
GROUP BY "line_item_product_code"
ORDER BY cost desc
LIMIT 10;
```

![Cost](/images/3-Costandusageanalysis/3.2-Cost/0003-cost.png?featherlight=false&width=90pc)

4. Query results returned

![Cost](/images/3-Costandusageanalysis/3.2-Cost/0004-cost.png?featherlight=false&width=90pc)

5. Show **Top10 Most Expensive Services and Descriptions**

```
SELECT "line_item_product_code",
"line_item_line_item_description",
round(sum("line_item_unblended_cost"), 2) as cost
FROM "costmaster"."monthly_report"
WHERE "line_item_product_code" like '%AmazonEC2%'
GROUP BY "line_item_product_code",
"line_item_line_item_description"
ORDER BY cost desc
LIMIT 10;
```

![Cost](/images/3-Costandusageanalysis/3.2-Cost/0005-cost.png?featherlight=false&width=90pc)

6. Query results returned

![Cost](/images/3-Costandusageanalysis/3.2-Cost/0006-cost.png?featherlight=false&width=90pc)

7. Show **Top 10 Most Expensive On Demand EC2 Uses**

```
SELECT "line_item_product_code",
"line_item_line_item_description",
round(sum("line_item_unblended_cost"), 2) as cost
FROM "costmaster"."monthly_report"
WHERE "line_item_product_code" like '%AmazonEC2%'
and "line_item_usage_type" like '%BoxUsage%'
GROUP BY "line_item_product_code",
"line_item_line_item_description"
ORDER BY cost desc
LIMIT 10;
```

![Cost](/images/3-Costandusageanalysis/3.2-Cost/0007-cost.png?featherlight=false&width=90pc)

8. Query results returned

![Cost](/images/3-Costandusageanalysis/3.2-Cost/0008-cost.png?featherlight=false&width=90pc)