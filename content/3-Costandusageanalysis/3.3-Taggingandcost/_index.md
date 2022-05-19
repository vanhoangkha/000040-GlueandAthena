---
title : "Tagging and Cost Allocation"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 3.3 </b> "
---

Tagging is quite common in large organizations, it fulfills the requirement of allocating costs back to specific business units. It is also important for optimizing workload allocation and for measuring performance.

1. Display **Top20 Highest Costing Items grouped by CostCenter Detail Description and tags**

```
SELECT "bill_payer_account_id",
"product_product_name",
"line_item_usage_type",
"line_item_line_item_description",
resource_tags_user_cost_center,
round(sum(line_item_unblended_cost), 2) as cost
FROM "costmaster"."monthly_report"
WHERE length("resource_tags_user_cost_center") > 0
GROUP BY "resource_tags_user_cost_center",
"bill_payer_account_id",
"product_product_name",
"line_item_usage_type",
"line_item_line_item_description"
ORDER BY cost desc
LIMIT 20
```

![Cost](/images/3-Costandusageanalysis/3.3-Taggingandcost/0001-taggingandcost.png?featherlight=false&width=90pc)

2. Query results returned

![Cost](/images/3-Costandusageanalysis/3.3-Taggingandcost/0002-taggingandcost.png?featherlight=false&width=90pc)

3. Display **Top20 Highest Costing Items grouped by Detailed Description and omit the CostCenter tag**

```
SELECT "bill_payer_account_id",
"product_product_name",
"line_item_usage_type",
"line_item_line_item_description",
round(sum(line_item_unblended_cost), 2) as cost
FROM "costmaster"."monthly_report"
WHERE length("resource_tags_user_cost_center") = 0
GROUP BY "bill_payer_account_id",
"product_product_name",
"line_item_usage_type",
"line_item_line_item_description"
ORDER BY cost desc
LIMIT 20
```

![Cost](/images/3-Costandusageanalysis/3.3-Taggingandcost/0003-taggingandcost.png?featherlight=false&width=90pc)

4. Query results returned


![Cost](/images/3-Costandusageanalysis/3.3-Taggingandcost/0004-taggingandcost.png?featherlight=false&width=90pc)