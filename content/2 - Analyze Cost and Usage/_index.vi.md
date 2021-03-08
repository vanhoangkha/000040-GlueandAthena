+++
title = "Phân tích Chi phí và Hiệu năng Sử dụng"
date = 2020
weight = 3
chapter = false
pre = "<b>3. </b>"
+++
---
Ở phần này, chúng ta sẽ đi phân tích hiệu năng sử dụng của hệ thống bằng các lệnh truy vấn SQL. Việc sử dụng **Amazon Athena** sẽ bị tính phí khi ta truy vấn, dựa theo lượng dữ liệu được quét – là dữ liệu được ghi nhận theo tháng và file ở định dạng **parquet**. Dữ liệu này đã được nén và phân mảnh để giảm thiểu chi phí khi sử dụng **Amazon Athena**. Tuy nhiên khi truy vấn vẫn nên giới hạn số lượng bản ghi trả về với từ khóa **limits** ở cuối câu lệnh.  

Cụ thể, chúng ta sẽ cùng nhau đi qua 4 ví dụ đánh giá sau đây. 
{{% notice tip %}}
Lưu ý: Để thuận tiện cho việc thử nghiệm, các bạn có thể sao chép các lệnh truy vấn [ở đây](http://localhost:1313/3-sql-query-for-cur/). Thay thế bảng dữ liệu của chúng tôi bằng tên bảng tương ứng của các bạn.
Với mỗi câu lệnh, ta chỉ cần sao chép vào đặt vào cửa sổ truy vấn rồi bấm nút **Run Query**.
{{% /notice %}}


#### 1. Nghiên cứu Dữ liệu trong bảng
- Hiển thị 10 bản ghi không trùng lặp nhau nằm trong bảng ***line_item_line_item_description***
![Security Hub](../../../images/1/25.png?width=55pc)  

- Hiển thị 10 bản ghi mà có giá trị cột line_item_line_item_type là Usage
![Security Hub](../../../images/1/26.png?width=90pc)  

- Hiển thị thời gian thanh toán không trùng lặp trong bảng dữ liệu
![Security Hub](../../../images/1/28.png?width=55pc)  

#### 2. Nghiên cứu về Chi phí 
Để tối ưu hóa được hiệu quả, sẽ rất tốt nếu ta có thể xem xét những chi phí hàng đầu theo nhiều danh mục khác nhau như dịch vụ, mô tả và tag.  
Dưới đây là một số lệnh truy vấn có thể giúp ta đánh giá chi phí 

- Hiển thị Top10 Account ID tốn chi phí nhất
![Security Hub](../../../images/1/29.png?width=90pc)  

- Hiển thị Top10 Dịch vụ tốn chi phí nhất
![Security Hub](../../../images/1/30.png?width=90pc)  

- Hiển thị Top10 Dịch vụ và Mô tả chi tiết có chi phí tốn kém nhất
![Security Hub](../../../images/1/31.png?width=90pc)  

- Hiển thị Top10 tình huống sử dụng EC2 tốn nhiều chi phí nhất
![Security Hub](../../../images/1/32.png?width=90pc)  

- Hiển thị Top10 tình huống sử dụng EC2 kiểu On Demand tốn nhiều chi phí nhất
![Security Hub](../../../images/1/33.png?width=90pc)  

#### 3. Tagging và sự Phân bổ Chi phí
Việc đánh tag khá phổ biến trong các tổ chức lớn, nó đáp ứng yêu cầu phân bổ chi phí trở lại cho các đơn vị kinh doanh cụ thể. Nó cũng rất quan trọng đối với việc tối ưu hóa trong việc phân bổ chi phí theo khối lượng công việc, đồng thời giúp đo lường hiệu quả công việc.

- Hiển thị Top20 hạng mục có chi phí cao nhất được nhóm theo Mô tả chi tiết và dấu tag của CostCenter
![Security Hub](../../../images/1/34.png?width=90pc)  

- Hiển thị Top20 hạng mục có chi phí cao nhất được nhóm theo Mô tả chi tiết và bỏ qua dấu tag của CostCenter
![Security Hub](../../../images/1/35.png?width=90pc)  

#### 4. Savings Plans, Reserved Instance, On Demand và Spot Usage
Để cải thiện việc sử dụng các mô hình tính toán chi phí cho doanh nghiệp, chúng tôi có đưa ra ở đây một vài ví dụ giúp làm nổi bật các trường hợp sử dụng EC2 theo kiểu **Savings Plans** hoặc **Reserved Instance** một cách hiệu quả khi so sánh với kiểu tính phí **On Demand**. 

- Hiển thị những account sử dụng EC2 dạng **Reserved Instance** và chi phí họ phải trả nếu tính với giá công khai. Điều này vô cùng hữu ích cho tổ chức trong việc tính toán bồi hoàn. 
![Security Hub](../../../images/1/36.png?width=90pc)  

- Hiển thị chi phí cho từng loại usage type thuộc family **t2**
![Security Hub](../../../images/1/37.png?width=90pc)  

- Hiển thị chi phí tính theo giờ cho từng loại usage type
![Security Hub](../../../images/1/38.png?width=90pc)  

- Hiển thị số Reserved Instance chưa được sử dụng
![Security Hub](../../../images/1/39.png?width=90pc)


