+++
title = "Chuẩn bị Cơ sở dữ liệu"
date = 2020
weight = 3
chapter = false
pre = "<b>2. </b>"
+++
---
### Chuẩn bị Dữ liệu Đầu vào

Bước đầu tiên, để xây dựng cơ sở dữ liệu phục vụ cho mục đích truy vấn từ **Amazon Athena** thông qua **AWS Glue** thì ta cần phải có dữ liệu dựa trên **AWS Cost & Usage Report**. Tuy nhiên để có được bản báo cáo này sẽ mất ít nhất 24h, do vậy chúng tôi đã chuẩn bị sẵn các file report như bên dưới dây.  
Các bạn có thể download và đặt chúng vào các đường dẫn trên S3 tương tự như hình bên dưới:

![Security Hub](../../../images/1/27.png?width=90pc) 

[October 2018 Usage](https://www.wellarchitectedlabs.com/Cost/200_4_Cost_and_Usage_Analysis/Code/Oct2018-WorkshopCUR-00001.snappy.parquet)  
[November 2018 Usage](https://www.wellarchitectedlabs.com/Cost/200_4_Cost_and_Usage_Analysis/Code/Nov2018-WorkshopCUR-00001.snappy.parquet)  
[December 2018 Usage](https://www.wellarchitectedlabs.com/Cost/200_4_Cost_and_Usage_Analysis/Code/Dec2018-WorkshopCUR-00001.snappy.parquet)  

Trường hợp bạn có nhiều thời gian hơn, thì có thể tự tạo dữ liệu report theo các bước sau đây:
1. Bấm vào *Accout Name* ở góc phải trên màn hình >> chọn **My Billing Dashboard**

2. Bấm **Create Report** để bắt đầu tạo report theo dõi chi phí và hiệu năng sử dụng
![Security Hub](../../../images/1/2.png?width=65pc)  

3. Trong mục **Report Content**, nhập tên Report, rồi click **Next** 
![Security Hub](../../../images/1/3.png?width=65pc)  

4. Tại bước **Delivery Option**, bấm **Configure** để bắt đầu cấu hình **S3** >> nhập tên S3 bucket rồi bấm **Next**.  
Phần **path prefix** >> nhập **cur**.  
Phần **Compression type** >> chọn **Parquet**
![Security Hub](../../../images/1/4.png?width=65pc)  

5. Review lại thông tin cấu hình rồi bấm **Review and Complete**
![Security Hub](../../../images/1/5.png?width=65pc)   

6. Sau ít nhất khoảng 24h thì **AWS Cost and Usage Reports** sẽ xuất ra báo cáo đầu tiên hiển thị như bên dưới
![Security Hub](../../../images/1/6.png?width=90pc)   

AWS sẽ generate report theo giờ và file nằm trong đường dẫn mà ta đã định nghĩa ở các bước phía trên.  

***
### Xây dựng Cơ sở dữ liệu

Trở về nội dung chính của bài lab, khi đã có dữ liệu đầu vào với đường dẫn trên S3 như ở đầu bài lab, chúng ta sẽ đi cấu hình **AWS Glue** và **Crawler** để nó chạy theo lịch mỗi ngày 1 lần. **Crawler** sẽ quét đường dẫn chứa file **Parquet** đầu vào, lưu trên S3 rồi thực hiện tạo một database cùng các bảng đi kèm. Khi có một phiên bản mới của report, bảng dữ liệu sẽ được tự động cập nhật.  

**Amazon Athena** giúp chúng ta truy cập và xem nội dung file **parquet** thông qua mã lệnh **SQL**. **Amazon Athena** là một giải pháp phi máy chủ hỗ trợ thực thi lệnh truy vấn SQL trên lượng lớn dữ liệu. **Athena** chỉ bị tính phi đối với dữ liệu được quét, không giống như giải pháp cơ sở dữ liệu truyền thống.  

Các bước cấu hình chi tiết để **Amazon Athena** có thể truy cập file dữ liệu thông qua **AWS Glue** như sau:  

1. Truy cập **AWS Glue console** qua địa chỉ https://us-west-1.console.aws.amazon.com/glue/home?region=us-west-1#
   
2. Ở khung điều hướng bên trái, bấm **Crawlers** >> **Add Crawler**
![Security Hub](../../../images/1/7.png?width=90pc)  

3. Phần **Crawler info**,  nhập crawler name ***Cost_MasterCrawler***
![Security Hub](../../../images/1/8.png?width=90pc)   

4. Phần **Crawler Source type**, chọn **Data stores** rồi bấm **Next**
![Security Hub](../../../images/1/9.png?width=90pc)   

5. Phần cấu hình **Data store**, lựa chọn **S3**, dữ liệu crawl sẽ được lưu tại đường dẫn chứa file report ***s3://asg-costworkshop-hourly-billing***.  
{{% notice tip %}}
Lưu ý: chỉ rõ những định dạng file sẽ không được crawl trong phần exclude patterns. Bao gồm những dạng file **.json, **.yml, **.sql, **.csv, **.gz, **.zip 
{{% /notice %}}
![Security Hub](../../../images/1/10.png?width=90pc)   

6. Thực hiện tạo mới **IAM Role**, đặt tên ***AWSGlueServiceRole-cost_MasterCrawler***, rồi bấm **Next**
![Security Hub](../../../images/1/11.png?width=90pc)   

7. Nôi dung schedule, tạm thời ta để lịch trình chạy **Run on demand**
![Security Hub](../../../images/1/12.png?width=90pc)   

8. Tạo Database mới để lưu Output của task Crawler. Bấm **Add Database**
![Security Hub](../../../images/1/13.png?width=90pc)   

9. Nhập tên database ***costmaster*** >> bấm **Create** >> tiếp tục bấm **Next**
![Security Hub](../../../images/1/14.png?width=35pc)   

10. Kiểm tra lại thông tin lần cuối, rồi bấm **Finish** để kết thúc quy trình thiết lập **Crawler**
![Security Hub](../../../images/1/15.png?width=55pc)  

11. Chạy Crawler mới tạo bằng cách tích chọn rồi bấm **Run crawler** 
![Security Hub](../../../images/1/16.png?width=90pc)  

12. Kết quả sau khi thực thi là một table mới được tạo ra. Bấm vào Database để bắt đầu kiểm tra bảng dữ liệu
![Security Hub](../../../images/1/17.png?width=90pc)  

13. Tại trang Database, bấm vào tên của database **costmaster**
![Security Hub](../../../images/1/18.png?width=50pc)  

14. Tiếp tục bấm vào **Tables in costmaster**
![Security Hub](../../../images/1/19.png?width=40pc)  

15. Bấm vào tên của table ***asg_costworkshop_hourly_billing***
![Security Hub](../../../images/1/20.png?width=90pc)  

16. Dễ dàng nhận thấy, giá trị **recordCount** khác 0, điều này chứng tỏ dữ liệu dạng *parquet* trên S3 đã được chuyển hóa thành dạng bảng thành công nhờ công cụ **Crawler** của **AWS Glue**. 
![Security Hub](../../../images/1/21.png?width=90pc)  

17. Thực hiện truy cập dịch vụ **Amazon Athena** >> chọn database ***costmaster***. Để thao tác với bảng dữ liệu, ta cần cấu hình nơi lưu kết quả truy vấn trên S3. Bấm vào **Settings** >> nhập đường dẫn S3
![Security Hub](../../../images/1/22.png?width=90pc)  

18. Bấm vào **dấu 3 chấm** bên cạnh tên bảng, rồi chọn **Load Partition** để dữ liệu bảng được lưu vào *metastore* của **Amazon Athena**. 
![Security Hub](../../../images/1/23.png?width=70pc)  

19. Thực hiện preview hệ thống để kiểm tra khả năng truy vấn bảng dữ liệu trên **AWS Glue**
![Security Hub](../../../images/1/24.png?width=90pc)  
