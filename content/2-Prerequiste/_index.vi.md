---
title : "Các bước chuẩn bị"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2. </b> "
---

#### Các bước chuẩn bị

Chúng ta bỏ qua các bước biến đổi dữ liệu ban đầu và chỉ làm việc trực tiếp trên file **Parquet** có sẵn.
Cụ thể chúng ta sẽ đi xây dựng một nền tảng để phân tích chi phí và hiệu năng sử dụng, từ đó ta có thể cân bằng giữa chi phí với hiệu quả của các thành phần trong hệ thống, nhưng vẫn tuân thủ kiến trúc tối ưu của AWS **(AWS Well-Architected Framework)**. Chúng ta bắt đầu thực hiện các bước xây dựng dữ liệu sau:

1. [Chuẩn bị cơ sở dữ liệu](2.1-preparedatabase)
2. [Xây dựng cơ sở dữ liệu](2.2-builddatabase)
3. [Kiểm tra cơ sở dữ liệu](2.3-testdatabase)