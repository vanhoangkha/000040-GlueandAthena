+++
title = "Tham khảo: SQL Query"
date = 2020
weight = 4
chapter = false
pre = "<b>4. </b>"
+++
---
{{% notice tip %}}
Với mỗi câu lệnh, ta chỉ cần sao chép vào đặt vào cửa sổ truy vấn rồi bấm nút **Run Query**.
{{% /notice %}}

```sql
SELECT * from "costmaster"."asg_costworkshop_hourly_billing"
LIMIT 10;

---

SELECT distinct "line_item_line_item_description" from "costmaster"."asg_costworkshop_hourly_billing"
LIMIT 10;

---

SELECT * from "costmaster"."asg_costworkshop_hourly_billing"
WHERE "line_item_line_item_type" like '%Usage%'
LIMIT 10;

---

SELECT distinct bill_billing_period_start_date FROM "costmaster"."asg_costworkshop_hourly_billing"
LIMIT 10;

---

SELECT "line_item_usage_account_id", round(sum("line_item_unblended_cost"),2) as cost from "costmaster"."asg_costworkshop_hourly_billing"
GROUP BY "line_item_usage_account_id"
ORDER BY cost desc
LIMIT 10;

---

SELECT "line_item_product_code", round(sum("line_item_unblended_cost"),2) as cost from "costmaster"."asg_costworkshop_hourly_billing"
GROUP BY "line_item_product_code"
ORDER BY cost desc
LIMIT 10;

---

SELECT "line_item_product_code", "line_item_line_item_description", round(sum("line_item_unblended_cost"),2) as cost from "costmaster"."asg_costworkshop_hourly_billing"
GROUP BY "line_item_product_code", "line_item_line_item_description"
ORDER BY cost desc
LIMIT 10;

---

SELECT "line_item_product_code", "line_item_line_item_description", round(sum("line_item_unblended_cost"),2) as cost from "costmaster"."asg_costworkshop_hourly_billing"
WHERE "line_item_product_code" like '%AmazonEC2%'
GROUP BY "line_item_product_code", "line_item_line_item_description"
ORDER BY cost desc
LIMIT 10;

---

SELECT "line_item_product_code", "line_item_line_item_description", round(sum("line_item_unblended_cost"),2) as cost from "costmaster"."asg_costworkshop_hourly_billing"
WHERE "line_item_product_code" like '%AmazonEC2%' and "line_item_usage_type" like '%BoxUsage%'
GROUP BY "line_item_product_code", "line_item_line_item_description"
ORDER BY cost desc
LIMIT 10;

---

SELECT "bill_payer_account_id", "product_product_name", "line_item_usage_type", "line_item_line_item_description", resource_tags_user_cost_center, round(sum(line_item_unblended_cost),2) as cost FROM "costmaster"."asg_costworkshop_hourly_billing"
WHERE length("resource_tags_user_cost_center") >0
GROUP BY "resource_tags_user_cost_center", "bill_payer_account_id", "product_product_name", "line_item_usage_type", "line_item_line_item_description"
ORDER BY cost desc
LIMIT 20

---

SELECT "bill_payer_account_id", "product_product_name", "line_item_usage_type", "line_item_line_item_description", round(sum(line_item_unblended_cost),2) as cost FROM "costmaster"."asg_costworkshop_hourly_billing"
WHERE length("resource_tags_user_cost_center") = 0
GROUP BY "bill_payer_account_id", "product_product_name", "line_item_usage_type", "line_item_line_item_description"
ORDER BY cost desc
LIMIT 20

---

SELECT "bill_payer_account_id", "bill_billing_period_start_date", "line_item_usage_account_id", "reservation_reservation_a_r_n", "line_item_product_code", "line_item_usage_type", sum("line_item_usage_amount") as Usage, "line_item_unblended_rate", sum("line_item_unblended_cost") as Cost, "line_item_line_item_description", "pricing_public_on_demand_rate", sum("pricing_public_on_demand_cost") as PublicCost from "costmaster"."asg_costworkshop_hourly_billing"
WHERE "line_item_line_item_Type" like '%DiscountedUsage%'
GROUP BY "bill_payer_account_id", "bill_billing_period_start_date", "line_item_usage_account_id", "reservation_reservation_a_r_n", "line_item_product_code", "line_item_usage_type", "line_item_unblended_rate", "line_item_line_item_description", "pricing_public_on_demand_rate"
LIMIT 20

---

SELECT "bill_payer_account_id", "bill_billing_period_start_date", "line_item_usage_account_id", "reservation_reservation_a_r_n", "line_item_product_code", "line_item_usage_type", sum("line_item_usage_amount") as Usage, "line_item_unblended_rate", sum("line_item_unblended_cost") as Cost, "line_item_line_item_description", "pricing_public_on_demand_rate", sum("pricing_public_on_demand_cost") as PublicCost from "costmaster"."asg_costworkshop_hourly_billing"
WHERE "line_item_line_item_Type" like '%DiscountedUsage%'
GROUP BY "bill_payer_account_id", "bill_billing_period_start_date", "line_item_usage_account_id", "reservation_reservation_a_r_n", "line_item_product_code", "line_item_usage_type", "line_item_unblended_rate", "line_item_line_item_description", "pricing_public_on_demand_rate"
LIMIT 20

---

SELECT "line_item_usage_type", sum("line_item_usage_amount") as usage, round(sum("line_item_unblended_cost"),2) as cost from "costmaster"."asg_costworkshop_hourly_billing"
WHERE "line_item_usage_type" like '%t2.%'
GROUP BY "line_item_usage_type"
ORDER BY "line_item_usage_type"
LIMIT 20

---

SELECT "line_item_usage_type", round(sum("line_item_usage_amount"),2) as usage, round(sum("line_item_unblended_cost"),2) as cost, round(avg("line_item_unblended_cost"/"line_item_usage_amount"),4) as hourly_rate from "costmaster"."asg_costworkshop_hourly_billing"
WHERE "line_item_product_code" like '%AmazonEC2%' and "line_item_usage_type" like '%Usage%'
GROUP BY "line_item_usage_type"
ORDER BY "line_item_usage_type"
LIMIT 20

---

SELECT bill_billing_period_start_date, product_region, line_item_usage_type, reservation_reservation_a_r_n, reservation_unused_quantity, reservation_unused_recurring_fee from "costmaster"."asg_costworkshop_hourly_billing"
WHERE length(reservation_reservation_a_r_n) > 0 and reservation_unused_quantity > 0
ORDER BY bill_billing_period_start_date, reservation_unused_recurring_fee desc
LIMIT 20

```