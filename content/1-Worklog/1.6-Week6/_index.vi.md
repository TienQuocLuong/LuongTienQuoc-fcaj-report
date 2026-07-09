---
title: "Worklog Tuần 6"
date: 2026-05-22
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần (Trọng tâm: Database):
Học sâu Module 06 về cơ sở dữ liệu (RDS, DynamoDB) — phần thế mạnh của bản thân, dành nhiều thời gian và thực hành kỹ nhất.

### Công việc thực hiện trong tuần:
| Thứ | Ngày | Công việc | Nguồn tài liệu |
|---|---|---|---|
| Thứ Sáu | 22/05/2026 | Xem bài giảng Module 06 và đọc tài liệu chi tiết về Amazon RDS và Aurora; ghi chú so sánh các engine (MySQL, PostgreSQL, Aurora) và các khái niệm Multi-AZ, Read Replica |  |
| Thứ Bảy | 23/05/2026 | Thực hành Lab 05 (Amazon RDS): tạo RDS MySQL, cấu hình Security Group cho EC2 kết nối tới RDS, cài Node.js và MySQL client, triển khai ứng dụng Node.js; xử lý lỗi file .env rỗng và lỗi package mysql không tương thích bằng cách đổi sang mysql2, cuối cùng app chạy thành công và kết nối được RDS | [awsstudygroup.com](https://000005.awsstudygroup.com/)  |
| Chủ Nhật | 24/05/2026 | Ôn lại truy vấn SQL từ cơ bản đến nâng cao (JOIN, GROUP BY, subquery, index) để phục vụ thao tác và tối ưu dữ liệu | |
| Thứ Hai | 25/05/2026 | Tìm hiểu sâu về Amazon DynamoDB: mô hình NoSQL, khái niệm Partition Key và Sort Key, cách thiết kế bảng để truy vấn hiệu quả và tránh hot partition |  |
| Thứ Ba | 26/05/2026 | Thực hành Lab 60 (DynamoDB): tạo bảng bằng AWS CLI, thực hiện đầy đủ các thao tác CRUD (thêm/đọc/sửa/xóa item), truy vấn dữ liệu bằng Query và Scan, phân biệt hai cách truy vấn này | [awsstudygroup.com](https://000005.awsstudygroup.com/1-introduce/)  |
| Thứ Tư | 27/05/2026 | Tiếp tục Lab 60: tạo và truy vấn Global Secondary Index (GSI) để truy vấn theo thuộc tính không phải khóa chính; sau đó thao tác lại toàn bộ bằng Python SDK Boto3 | [awsstudygroup.com](https://000005.awsstudygroup.com/1-introduce/)  |
| Thứ Năm | 28/05/2026 | Luyện thêm với Boto3: tự viết script tạo bảng, nạp dữ liệu mẫu, truy vấn và xóa item; đây là bước chuẩn bị nền tảng trực tiếp cho phần DynamoDB mình sẽ phụ trách trong dự án nhóm | |

### Kết quả đạt được tuần 6:
* Nắm vững kiến thức cơ sở dữ liệu trên AWS: phân biệt được cơ sở dữ liệu quan hệ (RDS/Aurora) và NoSQL (DynamoDB) cùng trường hợp sử dụng.
* Hoàn thành Lab 05: triển khai thành công ứng dụng Node.js kết nối RDS MySQL và tự xử lý được lỗi .env cùng lỗi tương thích package (chuyển sang mysql2).
* Hoàn thành Lab 60: thành thạo thiết kế bảng, thao tác CRUD, truy vấn Query/Scan và tạo Global Secondary Index trên DynamoDB.
* Thao tác thành thạo DynamoDB bằng cả AWS CLI và Python SDK Boto3.
* Củng cố lại kỹ năng SQL từ cơ bản đến nâng cao.
* Xây dựng được nền tảng vững chắc và trực tiếp cho vai trò phụ trách DynamoDB trong dự án nhóm.