---
title: "Worklog Tuần 10"
date: 2026-06-19
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu tuần:
Hoàn thiện bản mô tả chi tiết và sơ đồ kiến trúc; tập trung thiết kế phần dữ liệu (DynamoDB) và tìm hiểu VPC Endpoint.

### Công việc thực hiện trong tuần:
| Thứ | Ngày | Công việc | Nguồn tài liệu |
|---|---|---|---|
| Thứ Sáu | 19/06/2026 | Ôn lại các module và luyện vẽ thử một vài phương án sơ đồ kiến trúc cho hệ thống | |
| Thứ Bảy | 20/06/2026 | Cùng nhóm soạn bản mô tả chi tiết đề tài; đóng góp phần thiết kế hai bảng DynamoDB dùng để lưu lịch sử test và log lỗi | |
| Chủ Nhật | 21/06/2026 | Thiết kế schema chi tiết cho bảng playwright-test-history (Partition Key: task_id) và playwright-error-log (Partition Key: error_id), xác định rõ các trường và kiểu dữ liệu | |
| Thứ Hai | 22/06/2026 | Cùng nhóm vẽ sơ đồ kiến trúc, xác định vị trí của DynamoDB trong hệ thống và các luồng đọc/ghi dữ liệu từ Lambda | |
| Thứ Ba | 23/06/2026 | Rà soát lại các luồng kết nối dữ liệu, phát hiện và điều chỉnh những chỗ chưa hợp lý; bổ sung các dịch vụ liên quan đến phần mình phụ trách | |
| Thứ Tư | 24/06/2026 | Cùng nhóm trình bày sơ đồ kiến trúc với mentor để được review; ghi nhận các điểm cần chỉnh sửa và thảo luận hướng khắc phục | |
| Thứ Năm | 25/06/2026 | Nghiên cứu kỹ về VPC Endpoint: phân biệt Gateway Endpoint (cho S3, DynamoDB) và Interface Endpoint (cho ECR), chuẩn bị cho phần triển khai của mình | |

### Kết quả đạt được tuần 10:
* Cùng nhóm hoàn thiện bản mô tả chi tiết và sơ đồ kiến trúc của hệ thống (gồm CloudFront, S3, Cognito, API Gateway, SQS, ECS Fargate, ECR, DynamoDB, Lambda, CloudWatch, Secrets Manager, VPC, SES).
* Hoàn thành thiết kế schema chi tiết cho hai bảng DynamoDB thuộc phần việc của mình.
* Tham gia rà soát và điều chỉnh các luồng dữ liệu trong kiến trúc.
* Tìm hiểu kỹ và phân biệt được hai loại VPC Endpoint (Gateway và Interface), sẵn sàng cho giai đoạn triển khai.