---
title : "Kiểm tra cơ sở dữ liệu"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 2.3 </b> "
---

Chúng ta thực hiện tạo **S3 bucket** để lưu trữ kết quả truy vấn.

1. Truy cập vào **S3**

- Chọn **Bucket**
- Chọn **Create bucket**

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/0001-testdatabase.png?featherlight=false&width=90pc)

2. Trong giao diện **Create bucket**

- **Bucket name**, nhập ```cost-and-usage-query-results```

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/0002-testdatabase.png?featherlight=false&width=90pc)

3. Chọn **Create bucket**

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/0003-testdatabase.png?featherlight=false&width=90pc)

4. Chọn **cost-and-usage-query-results** bucket vừa tạo

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/0004-testdatabase.png?featherlight=false&width=90pc)

5. Tạo một folder để lưu trữ dữ liệu truy vấn

- Chọn **Create folder**

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/0005-testdatabase.png?featherlight=false&width=90pc)

6. Tạo folder

- **Folder name**, nhập ```Athena-Query-Results```
- Chọn **Create folder**

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/0006-testdatabase.png?featherlight=false&width=90pc)

7. Hoàn thành tạo folder 

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/0007-testdatabase.png?featherlight=false&width=90pc)

8. Truy cập **AWS Console Management**

- Tìm **Athena**
- Chọn **Athena**

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/0008-testdatabase.png?featherlight=false&width=90pc)

9. Để thao tác với bảng dữ liệu, ta cần cấu hình nơi lưu kết quả truy vấn trên S3. 

- Chọn **Settings**

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/0009-testdatabase.png?featherlight=false&width=90pc)

10. Chọn **Manage**

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/00010-testdatabase.png?featherlight=false&width=90pc)

11. Chọn đường dẫn S3 để lưu trữ 

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/00011-testdatabase.png?featherlight=false&width=90pc)

12. Sau đó, chọn **Edit**

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/00012-testdatabase.png?featherlight=false&width=90pc)

13. Kiểm tra lại và thực hiện query

- **Data Source**, chọn **AwsDataCatalog**
- **Database**, chọn **costmaster**
- **Table**, chọn **monthly_report**
- Thực hiện truy vấn  bằng lệnh sau: dữ liệu bảng được lưu vào **metastore của Amazon Athena**.

```
MSCK REPAIR TABLE monthly_report;
```
- Chọn **Run**
- Hoàn thành truy vấn **Query successful**

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/00013-testdatabase.png?featherlight=false&width=90pc)

14. Thực hiện preview hệ thống để kiểm tra khả năng truy vấn bảng dữ liệu trên AWS Glue

- Chọn **monthly_report** table
- Chọn **Preview Table**

```
SELECT * FROM "costmaster"."monthly_report"
LIMIT 10;
```

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/00014-testdatabase.png?featherlight=false&width=90pc)
