+++
title = "COST AND USAGE ANALYSIS"
date = 2020
weight = 1
chapter = false
+++

# PHÂN TÍCH CHI PHÍ VÀ HIỆU NĂNG SỬ DỤNG VỚI AWS GLUE VÀ AMAZON ATHENA
---
Bài lab sẽ hướng dẫn bạn từng bước để thiết lập một nền tảng để phân tích các báo cáo chi phí và hiệu năng sử dụng của bất kì hệ thống nào. Các kiến thức có được sau bài lab sẽ giúp bạn thực hiện phân tích về chi phí và về hiệu năng sử dụng hệ thống mà bạn đang làm việc trên đó. 

#### Tài liệu

1. Tài liệu nguồn [Cost and Usage Analysis](https://www.wellarchitectedlabs.com/cost/200_labs/200_4_cost_and_usage_analysis/)
2. Tài liệu tham khảo [What is Amazon Athena?](https://aws.amazon.com/vi/athena) 
3. Tài liệu tham khảo [What is AWS Glue](https://aws.amazon.com/vi/glue)


#### Nội dung

Nội dung bài lab gồm 3 phần:

1. [Giới thiệu AWS Glue & Amazon Athena](0-introduce-glue-and-athena/)
2. [Chuẩn bị Cơ sở dữ liệu](1-setup-database/)
3. [Phân tích Chi phí và Hiệu năng Sử dụng](2-analyze-cost-and-usage/)


#### Chuẩn bị  

1. Quyền đăng nhập và sử dụng 1 AWS account thuộc nhóm người dùng có khả năng Tối ưu hóa Chi phí (Cost Optimization)
2. User phải đủ quyền tạo Tạo/Sửa đổi Roles trong IAM
3. User phải có quyền sử dụng AWS Glue & Amazon Athena

#### Lưu ý

1. S3 chứa dữ liệu đầu vào không yêu cầu phải được cấu hình public access và cũng không cần phải cùng region với dịch vụ AWS Glue
2. S3 chứa kết quả truy vấn từ Athena phải cùng Region với Amazon Athena
3. AWS Glue cần được cấp quyền GetObject and PutObject S3, nhằm cho phép Glue được truy cập vào S3 (đọc và ghi file Parquet trên S3)
