---
title : "Chuẩn bị cơ sở dữ liệu"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 2.1 </b> "
---

Trong bài lab này, chúng ta sử dụng dữ liệu có sẵn về  **AWS Cost & Usage Report.**

Bước đầu tiên, để xây dựng cơ sở dữ liệu phục vụ cho mục đích truy vấn từ **Amazon Athena** thông qua **AWS Glue** thì ta cần phải có dữ liệu dựa trên **AWS Cost & Usage Report**. Tuy nhiên để có được bản báo cáo này sẽ **mất ít nhất 24h**, do vậy chúng tôi đã chuẩn bị sẵn các file report. 

{{% notice note %}}
Các bạn tải dữ liệu về tại [Cost and Usage Analysis](https://github.com/First-Cloud-Journey/000040-CUR). ![Prerequisite](/images/2-Prerequiste/2.1-Preparedatabase/00012-preparedatabase.png?featherlight=false&width=90pc)

{{% /notice %}}

1. Truy cập vào [AWS Management Console](https://aws.amazon.com/vi/console/)

- Tìm **S3**
- Chọn **S3**

![Prerequisite](/images/2-Prerequiste/2.1-Preparedatabase/0001-preparedatabase.png?featherlight=false&width=90pc)

1. Trong giao diện **S3**

- Chọn **Buckets**
- Chọn **Create bucket**

![Prerequisite](/images/2-Prerequiste/2.1-Preparedatabase/0002-preparedatabase.png?featherlight=false&width=90pc)

3. Trong giao diện **Create bucket**

- **Bucket name**, nhập ```cost-and-usage-analysis```

![Prerequisite](/images/2-Prerequiste/2.1-Preparedatabase/0003-preparedatabase.png?featherlight=false&width=90pc)

4. Chọn **Create bucket**

![Prerequisite](/images/2-Prerequiste/2.1-Preparedatabase/0004-preparedatabase.png?featherlight=false&width=90pc)

5. Hoàn thành tạo **S3 bucket**

- Chọn **cost-and-usage-analysis** bucket

![Prerequisite](/images/2-Prerequiste/2.1-Preparedatabase/0005-preparedatabase.png?featherlight=false&width=90pc)

6. Trong **cost-and-usage-analysis** bucket

- Tạo một folder để lưu trữ dữ liệu bằng cách chọn **Create folder**

![Prerequisite](/images/2-Prerequiste/2.1-Preparedatabase/0006-preparedatabase.png?featherlight=false&width=90pc)

7. Trong giao diện **Create folder**

- **Folder name**, nhập ```Monthly-Report```
- Chọn **Create folder**

![Prerequisite](/images/2-Prerequiste/2.1-Preparedatabase/0007-preparedatabase.png?featherlight=false&width=90pc)

8. Chúng ta thực hiện **Upload** các file dữ liệu 

![Prerequisite](/images/2-Prerequiste/2.1-Preparedatabase/0008-preparedatabase.png?featherlight=false&width=90pc)

9. Chọn các file dữ liệu đã tải về

- Chọn **Add files**
- Chọn các file dữ liệu

![Prerequisite](/images/2-Prerequiste/2.1-Preparedatabase/0009-preparedatabase.png?featherlight=false&width=90pc)

10. Chọn **Upload**

![Prerequisite](/images/2-Prerequiste/2.1-Preparedatabase/00010-preparedatabase.png?featherlight=false&width=90pc)

11. Khi trạng thái upload chuyển sang **Succeeded**

![Prerequisite](/images/2-Prerequiste/2.1-Preparedatabase/00011-preparedatabase.png?featherlight=false&width=90pc)