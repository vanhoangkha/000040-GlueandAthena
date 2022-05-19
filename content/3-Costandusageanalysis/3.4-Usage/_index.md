---
title : "Usage"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 3.4 </b> "
---

#### Savings Plans, Reserved Instance, On Demand and Spot Usage

To improve the use of costing models for businesses, here are a few examples that highlight EC2 use cases in **Savings Plans or Reserved Instance** styles. efficient way when compared to **On Demand.**

1. Show **accounts that use EC2 as Reserved Instance and how much they pay if charged at public rates**. This is extremely useful to the organization in calculating reimbursement.

```
SELECT "bill_payer_account_id",
"bill_billing_period_start_date",
"line_item_usage_account_id",
"reservation_reservation_a_r_n",
"line_item_product_code",
"line_item_usage_type",
sum("line_item_usage_amount") as Usage,
"line_item_unblended_rate",
sum("line_item_unblended_cost") as Cost,
"line_item_line_item_description",
"pricing_public_on_demand_rate",
sum("pricing_public_on_demand_cost") as PublicCost
FROM "costmaster"."monthly_report"
WHERE "line_item_line_item_Type" like '%DiscountedUsage%'
GROUP BY "bill_payer_account_id",
"bill_billing_period_start_date",
"line_item_usage_account_id",
"reservation_reservation_a_r_n",
"line_item_product_code",
"line_item_usage_type",
"line_item_unblended_rate",
"line_item_line_item_description",
"pricing_public_on_demand_rate"
LIMIT 20
```

![Uasge](/images/3-Costandusageanalysis/3.4-Usage/0001-usage.png?featherlight=false&width=90pc)

2. Query results returned

![Uasge](/images/3-Costandusageanalysis/3.4-Usage/0002-usage.png?featherlight=false&width=90pc)

3. Display **cost for each usage type of family t2**

```
SELECT "line_item_usage_type",
sum("line_item_usage_amount") as usage,
round(sum("line_item_unblended_cost"), 2) as cost
FROM "costmaster"."monthly_report"
WHERE "line_item_usage_type" like '%t2.%'
GROUP BY "line_item_usage_type"
ORDER BY "line_item_usage_type"
LIMIT 20
```

![Uasge](/images/3-Costandusageanalysis/3.4-Usage/0003-usage.png?featherlight=false&width=90pc)

4. Query results returned

![Uasge](/images/3-Costandusageanalysis/3.4-Usage/0004-usage.png?featherlight=false&width=90pc)

5. Display **hourly cost for each usage type**

```
SELECT "line_item_usage_type",
round(sum("line_item_usage_amount"), 2) as usage,
round(sum("line_item_unblended_cost"), 2) as cost,
round(
avg(
"line_item_unblended_cost" / "line_item_usage_amount"
),
4
) as hourly_rate
FROM "costmaster"."monthly_report"
WHERE "line_item_product_code" like '%AmazonEC2%'
and "line_item_usage_type" like '%Usage%'
GROUP BY "line_item_usage_type"
ORDER BY "line_item_usage_type"
LIMIT 20
```

![Uasge](/images/3-Costandusageanalysis/3.4-Usage/0005-usage.png?featherlight=false&width=90pc)

6. Query results returned

![Uasge](/images/3-Costandusageanalysis/3.4-Usage/0006-usage.png?featherlight=false&width=90pc)

7. Display **Number of Reserved Instances that have not been used**

```
SELECT bill_billing_period_start_date,
product_region,
line_item_usage_type,
reservation_reservation_a_r_n,
reservation_unused_quantity,
reservation_unused_recurring_fee
FROM "costmaster"."monthly_report"
WHERE length(reservation_reservation_a_r_n) > 0
and reservation_unused_quantity > 0
ORDER BY bill_billing_period_start_date,
reservation_unused_recurring_fee desc
LIMIT 20
```

![Uasge](/images/3-Costandusageanalysis/3.4-Usage/0007-usage.png?featherlight=false&width=90pc)

8. Query results returned

![Uasge](/images/3-Costandusageanalysis/3.4-Usage/0008-usage.png?featherlight=false&width=90pc)