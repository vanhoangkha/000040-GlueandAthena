---
title : "Xây dựng cơ sở dữ liệu"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---

Trong bài lab, khi đã có dữ liệu đầu vào với đường dẫn trên S3 như ở đầu bài lab, chúng ta sẽ cấu hình **AWS Glue** và **Crawler** để nó chạy theo lịch **mỗi ngày 1 lần**. **Crawler** sẽ quét đường dẫn chứa **file Parquet** đầu vào, lưu trên S3 rồi thực hiện tạo một database cùng các bảng đi kèm. Khi có một phiên bản mới của **report**, bảng dữ liệu sẽ được tự động cập nhật.

**Amazon Athena** giúp chúng ta truy cập và xem nội dung file parquet thông qua **mã lệnh SQL**. **Amazon Athena** là một giải pháp **phi máy chủ** hỗ trợ thực thi lệnh **truy vấn SQL** trên lượng lớn dữ liệu. **Athena** chỉ bị tính phi đối với dữ liệu được quét, không giống như giải pháp cơ sở dữ liệu truyền thống.

Các bước cấu hình chi tiết để **Amazon Athena** có thể truy cập file dữ liệu thông qua **AWS Glue** như sau:


1. Truy cập vào [AWS Management Console](https://aws.amazon.com/vi/console/)

- Tìm **AWS Glue**
- Chọn **AWS Glue**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/0001-builddatabase.png?featherlight=false&width=90pc)

2. Trong giao diện **AWS Glue**

- Chọn **Crawlers**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/0002-builddatabase.png?featherlight=false&width=90pc)

3. Trong giao diện **Crawler**

- Chọn **Add crawler**


![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/0003-builddatabase.png?featherlight=false&width=90pc)

4. Chúng ta thực hiện các bước cấu hình **crawler**

- Phần **Crawler info**, nhập **Crawler name** là ```Cost_MasterCrawler```


![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/0004-builddatabase.png?featherlight=false&width=90pc)

5. Bước cấu hình **Crawler source type**

- Chọn **Data stores**
- Chọn **Crawl new folders only**
- Chọn **Next**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/0005-builddatabase.png?featherlight=false&width=90pc)

6. Trong giao diện **Data store**

- **Chooose a data store**, nhập **S3**
- **Crawl data in**, chọn **Specified path in my account**
- **Include path**, Chọn **đường dẫn của S3**


![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/0006-builddatabase.png?featherlight=false&width=90pc)

7. Chỉ rõ những định dạng file sẽ không được crawl trong **phần exclude patterns**. Bao gồm những dạng file **.json**, **.yml**, **.sql**, **.csv**, **.gz**, **.zip**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/0007-builddatabase.png?featherlight=false&width=90pc)


8. Chọn **No** và chọn **Next**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/0008-builddatabase.png?featherlight=false&width=90pc)

9. Trong phần **IAM Role**

- Chọn **Create an IAM role**
- Nhập ```cost_MasterCrawler```
- Chọn **Next**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/0009-builddatabase.png?featherlight=false&width=90pc)

10. Trong phần **Schedule**

- **Frequency**, chọn **Run on demand**
- Chọn **Next**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/00010-builddatabase.png?featherlight=false&width=90pc)


11. Bước cấu hình **Output**

- Chọn **Add database**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/00011-builddatabase.png?featherlight=false&width=90pc)

12. Trong giao diện **Add database**

- **Database name**, nhập ```costmaster```
- Chọn **Create**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/00012-builddatabase.png?featherlight=false&width=90pc)

13. Chọn **Next**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/00013-builddatabase.png?featherlight=false&width=90pc)

14. Kiểm tra lại và chọn **Finish**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/00014-builddatabase.png?featherlight=false&width=90pc)

15. Hoàn thành tạo **Crawler**

- Chọn **Cost_MasterCrawler** vừa tạo
- Chọn **Run crawler**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/00015-builddatabase.png?featherlight=false&width=90pc)

16. Crawler chạy trong khoảng 5 phút sau, kết quả xuất hiện như hình có **1 Table** được thêm vào

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/00016-builddatabase.png?featherlight=false&width=90pc)

17. Trong giao diện **AWS Glue**

- Chọn **Databases**
- Chọn **costmaster** database
- Chọn **View tables**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/00017-builddatabase.png?featherlight=false&width=90pc)

18. Chọn **monthly_report** table


![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/00018-builddatabase.png?featherlight=false&width=90pc)

19. Dễ dàng nhận thấy, **giá trị recordCount khác 0**, điều này chứng tỏ **dữ liệu dạng parquet trên S3** đã được chuyển hóa thành dạng bảng thành công nhờ công cụ **Crawler của AWS Glue**.

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/00019-builddatabase.png?featherlight=false&width=90pc)


