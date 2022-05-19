---
title : "Nghiên cứu về Chi phí"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 3.2 </b> "
---

Để tối ưu hóa được hiệu quả, sẽ rất tốt nếu ta có thể xem xét những chi phí hàng đầu theo nhiều danh mục khác nhau như **dịch vụ, mô tả và tag.**

1. Hiển thị **Top10 Account ID tốn chi phí nhất**

```
SELECT "line_item_usage_account_id",
	round(sum("line_item_unblended_cost"), 2) as cost
FROM "costmaster"."monthly_report"
GROUP BY "line_item_usage_account_id"
ORDER BY cost desc
LIMIT 10;
```

![Cost](/images/3-Costandusageanalysis/3.2-Cost/0001-cost.png?featherlight=false&width=90pc)

2. Kết quả truy vấn trả về

![Cost](/images/3-Costandusageanalysis/3.2-Cost/0002-cost.png?featherlight=false&width=90pc)

3. Hiển thị **Top10 Dịch vụ tốn chi phí nhất**

```
SELECT "line_item_product_code",
	round(sum("line_item_unblended_cost"), 2) as cost
FROM "costmaster"."monthly_report"
GROUP BY "line_item_product_code"
ORDER BY cost desc
LIMIT 10;
```

![Cost](/images/3-Costandusageanalysis/3.2-Cost/0003-cost.png?featherlight=false&width=90pc)

4. Kết quả truy vấn trả về

![Cost](/images/3-Costandusageanalysis/3.2-Cost/0004-cost.png?featherlight=false&width=90pc)

5. Hiển thị **Top10 Dịch vụ và Mô tả chi tiết có chi phí tốn kém nhất**

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

6. Kết quả truy vấn trả về

![Cost](/images/3-Costandusageanalysis/3.2-Cost/0006-cost.png?featherlight=false&width=90pc)

7. Hiển thị **Top10 tình huống sử dụng EC2 kiểu On Demand tốn nhiều chi phí nhất**

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

8. Kết quả truy vấn trả về

![Cost](/images/3-Costandusageanalysis/3.2-Cost/0008-cost.png?featherlight=false&width=90pc)