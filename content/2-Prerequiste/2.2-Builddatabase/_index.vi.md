---
title : "Xây dựng cơ sở dữ liệu"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---

Trong bài lab, khi đã có dữ liệu đầu vào với đường dẫn trên   như ở đầu bài lab, chúng ta sẽ cấu hình **AWS Glue** và **Crawler** để nó chạy theo lịch **mỗi ngày 1 lần**. **Crawler** sẽ quét đường dẫn chứa **file Parquet** đầu vào, lưu trên S3 rồi thực hiện tạo một database cùng các bảng đi kèm. Khi có một phiên bản mới của **report**, bảng dữ liệu sẽ được tự động cập nhật.

**Amazon Athena** giúp chúng ta truy cập và xem nội dung file parquet thông qua **mã lệnh SQL**. **Amazon Athena** là một giải pháp **phi máy chủ** hỗ trợ thực thi lệnh **truy vấn SQL** trên lượng lớn dữ liệu. **Athena** chỉ bị tính phi đối với dữ liệu được quét, không giống như giải pháp cơ sở dữ liệu truyền thống.

Các bước cấu hình chi tiết để **Amazon Athena** có thể truy cập file dữ liệu thông qua **AWS Glue** như sau:


1. Truy cập vào [AWS Management Console](https://aws.amazon.com/vi/console/)

   - Tìm **AWS Glue**
   - Chọn **AWS Glue**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/0001-builddatabase.png?featherlight=false&width=90pc)

2. Trong giao diện **AWS Glue**

   - Chọn **Crawlers**
   - Chọn **Create crawler**

![Prerequisite](/images/2/0001.png?featherlight=false&width=90pc)

3. Cấu hình **Crawler**, nhập **Name** là **```Cost_MasterCrawler```**. Sau đó, chọn **Next**

![Prerequisite](/images/2/0002.png?featherlight=false&width=90pc)

4. Chọn  **Add a data source**

![Prerequisite](/images/2/0003.png?featherlight=false&width=90pc)

5. Cấu hình data source 

![Prerequisite](/images/2/0004.png?featherlight=false&width=90pc)

6. Chọn **S3 path**

![Prerequisite](/images/2/0005.png?featherlight=false&width=90pc)

7. Hoàn tất cấu hình data source.

![Prerequisite](/images/2/0006.png?featherlight=false&width=90pc)

8. Sau khi cấu hình data source, chọn **Next**

![Prerequisite](/images/2/0007.png?featherlight=false&width=90pc)

9. Đối với security, bạn chọn **Create new IAM role**

![Prerequisite](/images/2/0008.png?featherlight=false&width=90pc)

10. Nhập tên role và chọn **Create**

![Prerequisite](/images/2/0009.png?featherlight=false&width=90pc)

11. Sau khi tạo role, chọn **Next**

![Prerequisite](/images/2/00010.png?featherlight=false&width=90pc)

12. Thực hiện thêm database

- Chọn **Add database**

![Prerequisite](/images/2/00011.png?featherlight=false&width=90pc)

13. Nhập tên database là **```costmaster```**. Chọn **Create database**

![Prerequisite](/images/2/00012.png?featherlight=false&width=90pc)

14. Hoàn thành tạo database.

![Prerequisite](/images/2/00013.png?featherlight=false&width=90pc)

15. Thêm database thành công và chọn **Next**

![Prerequisite](/images/2/00014.png?featherlight=false&width=90pc)

14. Kiểm tra và chọn **Create crawler**

![Prerequisite](/images/2/00015.png?featherlight=false&width=90pc)

15. Hoàn thành tạo crawler.

![Prerequisite](/images/2/00016.png?featherlight=false&width=90pc)

16. Chọn **Run crawler**

![Prerequisite](/images/2/00017.png?featherlight=false&width=90pc)

17. Mất khoảng 1 phút để khởi tạo run crawler. 

![Prerequisite](/images/2/00018.png?featherlight=false&width=90pc)

18. Khởi tạo **run crawler**

![Prerequisite](/images/2/00019.png?featherlight=false&width=90pc)

19. **Run crawler** thành công. 

![Prerequisite](/images/2/00020.png?featherlight=false&width=90pc)

20. Kiểm tra **Table** của AWS Glue. Ta thấy có bảng dữ liệu **monthly_report**

![Prerequisite](/images/2/00021.png?featherlight=false&width=90pc)

21. Xem chi tiết thông tin bảng dữ liệu.

![Prerequisite](/images/2/00022.png?featherlight=false&width=90pc)


