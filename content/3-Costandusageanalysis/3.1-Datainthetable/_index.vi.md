---
title : "Nghiên cứu Dữ liệu trong bảng"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 3.1 </b> "
---

{{% notice tip %}}
Lưu ý: Để thuận tiện cho việc thử nghiệm, các bạn có thể sao chép các lệnh truy vấn. Thay thế bảng dữ liệu của chúng tôi bằng tên bảng tương ứng của các bạn. Với mỗi câu lệnh, ta chỉ cần sao chép vào đặt vào cửa sổ truy vấn rồi bấm nút **Run**.

{{% /notice %}}

#### Nghiên cứu Dữ liệu trong bảng

1. Chúng ta thực hiện truy vấn **dữ liệu 10 bản ghi không trùng lặp nhau** nằm trong bảng **line_item_line_item_description**

```
SELECT distinct "line_item_line_item_description"
FROM "costmaster"."monthly_report"
LIMIT 10;
```

- Chọn **Run**

![Data in the table](/images/3-Costandusageanalysis/3.1-Datainthetable/0001-datainthetable.png?featherlight=false&width=90pc)

2. Kết quả sau khi truy vấn 

![Data in the table](/images/3-Costandusageanalysis/3.1-Datainthetable/0002-datainthetable.png?featherlight=false&width=90pc)

3. Thực hiện **truy vấn 10 bản ghi** mà có giá trị cột **line_item_line_item_type** là **Usage**

```
SELECT * FROM "costmaster"."monthly_report"
WHERE "line_item_line_item_type" like '%Usage%'
LIMIT 10;
```

![Data in the table](/images/3-Costandusageanalysis/3.1-Datainthetable/0003-datainthetable.png?featherlight=false&width=90pc)

4. Kết quả truy vấn trả về 

![Data in the table](/images/3-Costandusageanalysis/3.1-Datainthetable/0004-datainthetable.png?featherlight=false&width=90pc)

5. Hiển thị **thời gian thanh toán không trùng lặp** trong bảng dữ liệu

```
SELECT distinct bill_billing_period_start_date 
FROM "costmaster"."monthly_report"
LIMIT 10;
```

![Data in the table](/images/3-Costandusageanalysis/3.1-Datainthetable/0005-datainthetable.png?featherlight=false&width=90pc)

6. Kết quả truy vấn trả về. Kết quả thanh toán theo từng tháng. 

![Data in the table](/images/3-Costandusageanalysis/3.1-Datainthetable/0006-datainthetable.png?featherlight=false&width=90pc)