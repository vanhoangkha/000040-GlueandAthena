---
title : "Phân tích chi phí và hiệu năng sử dụng"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 3. </b> "
---

#### Phân tích chi phí và hiệu năng sử dụng

Ở phần này, chúng ta sẽ đi phân tích hiệu năng sử dụng của hệ thống bằng các lệnh truy vấn **SQL**. Việc sử dụng **Amazon Athena** sẽ bị tính phí khi ta truy vấn, dựa theo lượng dữ liệu được quét ( **scan** ) là dữ liệu được ghi nhận theo tháng và file ở **định dạng parquet**. Dữ liệu này đã được nén và phân mảnh để giảm thiểu chi phí khi sử dụng **Amazon Athena**. Tuy nhiên khi truy vấn vẫn nên giới hạn số lượng bản ghi trả về với **từ khóa limits** ở cuối câu lệnh.

#### Một số câu lệnh SQL cơ bản

- **Câu lệnh SQL SELECT** : SELECT được sử dụng để chọn dữ liệu từ cơ sở dữ liệu. Dữ liệu trả về được lưu trữ trong một bảng kết quả.

- **Câu lệnh SQL SELECT DISTINCT**: SELECT DISTINCT được sử dụng để trả về các giá trị riêng biệt (khác nhau). Bên trong một bảng, một cột thường chứa nhiều giá trị trùng lặp; và đôi khi bạn chỉ muốn liệt kê các giá trị khác nhau (riêng biệt).

- **Mệnh đề WHERE trong SQL**: Mệnh đề WHERE được sử dụng để lọc các bản ghi. Nó chỉ được sử dụng để trích xuất những bản ghi đáp ứng một điều kiện cụ thể.

- **Câu lệnh SQL GROUP BY**: GROUP BY dùng để nhóm các hàng có cùng giá trị thành các hàng tóm tắt. 

- **Câu lệnh SQL ORDER BY**: ORDER BY được sử dụng để sắp xếp tập hợp kết quả theo thứ tự tăng dần hoặc giảm dần.

- **Toán tử SQL LIKE**: Toán tử LIKE được sử dụng trong một mệnh đề WHERE để tìm kiếm một mẫu xác định trong một cột.

- **Từ khóa LIMIT**: giới hạn số lượng bản ghi trả về

#### Nội dung

1. [Nghiên cứu dữ liệu trong bảng](3.1-datainthetable)
2. [Nghiên cứu về chi phí](3.2-cost)
3. [Tagging và sự Phân bổ Chi phí](3.3-taggingandcost)
4. [Savings Plans, Reserved Instance, On Demand và Spot Usage](3.4-usage)

