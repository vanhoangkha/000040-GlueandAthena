---
title : "Tagging và sự Phân bổ Chi phí"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 3.3 </b> "
---

Việc đánh tag khá phổ biến trong các tổ chức lớn, nó đáp ứng yêu cầu phân bổ chi phí trở lại cho các đơn vị kinh doanh cụ thể. Nó cũng rất quan trọng đối với việc tối ưu hóa trong việc phân bổ chi phí theo khối lượng công việc, đồng thời giúp đo lường hiệu quả công việc.

1. Hiển thị **Top20 hạng mục có chi phí cao nhất được nhóm theo Mô tả chi tiết và dấu tag của CostCenter**

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

2. Kết quả truy vấn trả về

![Cost](/images/3-Costandusageanalysis/3.3-Taggingandcost/0002-taggingandcost.png?featherlight=false&width=90pc)

3. Hiển thị **Top20 hạng mục có chi phí cao nhất được nhóm theo Mô tả chi tiết và bỏ qua dấu tag của CostCenter**

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

4. Kết quả truy vấn trả về


![Cost](/images/3-Costandusageanalysis/3.3-Taggingandcost/0004-taggingandcost.png?featherlight=false&width=90pc)