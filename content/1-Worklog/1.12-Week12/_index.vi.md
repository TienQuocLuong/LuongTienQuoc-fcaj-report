---
title: "Worklog Tuần 12"
date: 2026-07-03
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Mục tiêu tuần:
Triển khai hạ tầng và các tài nguyên phụ trách; phối hợp cùng nhóm chạy thử nghiệm toàn hệ thống.

### Công việc thực hiện trong tuần:
| Thứ | Ngày | Công việc | Nguồn tài liệu |
|---|---|---|---|
| Thứ Sáu | 03/07/2026 | Cùng nhóm lập kế hoạch triển khai chi tiết và cấu hình hạ tầng mạng VPC (Subnet, Route Table, NAT Gateway, các Security Group) | |
| Thứ Bảy | 04/07/2026 | Cùng nhóm cập nhật, hoàn thiện kế hoạch triển khai và chuẩn bị tài nguyên (mã nguồn, file cấu hình hệ thống) | |
| Chủ Nhật | 05/07/2026 | Trực tiếp tạo hai bảng DynamoDB (playwright-test-history, playwright-error-log) theo schema đã thiết kế; phối hợp cùng nhóm tạo hai S3 bucket và hai SQS queue (task queue và Dead Letter Queue) | |
| Thứ Hai | 06/07/2026 | Tạo VPC Endpoint cho S3 (Gateway type) và cho ECR (Interface type); verify email trên SES và gửi thử một email để kiểm tra; hỗ trợ nhóm cấu hình các Lambda function và thiết lập EventBridge Scheduler | |
| Thứ Ba | 07/07/2026 | *(cập nhật sau – kiểm thử phần DynamoDB và SES trong luồng chạy end-to-end)* | |
| Thứ Tư | 08/07/2026 | *(cập nhật sau – chạy thử toàn hệ thống, sửa lỗi cấu hình, viết phần Tự đánh giá)* | |
| Thứ Năm | 09/07/2026 | *(cập nhật sau – hoàn thiện và nộp báo cáo thực tập)* | |

### Kết quả đạt được tuần 12:
* Cùng nhóm thống nhất kế hoạch triển khai và cấu hình thành công hạ tầng mạng VPC.
* Trực tiếp tạo và cấu hình hai bảng DynamoDB đúng theo schema đã thiết kế.
* Tạo thành công VPC Endpoint cho S3 (Gateway) và ECR (Interface) để các dịch vụ giao tiếp nội bộ an toàn.
* Verify và kiểm tra thành công email gửi qua Amazon SES.
* Phối hợp cùng nhóm tạo các tài nguyên lưu trữ và hàng đợi (2 S3 bucket, 2 SQS queue gồm DLQ), hỗ trợ triển khai Lambda và EventBridge Scheduler.